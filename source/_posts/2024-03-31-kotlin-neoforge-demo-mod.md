---
title: 使用 Kotlin 语言开发 NeoForge 模组
date: 2024-03-31 14:18:34
tags: [Kotlin, NeoForge]
---

# 前言

Kotlin 是由 JetBrains 推出的一门基于 JVM 平台的编程语言，引入了许多不同于 Java 的先进概念以及语法糖，极大地提高了开发人员的编程效率，广受各路 Java 开发者推崇。但由于 NeoForge 官方并未就使用 Kotlin 开发模组提供支持，使得精通 Kotlin 的开发者未能使用所擅长的语言编写模组而被迫改用 Java 。幸运的是借助 [thedarkcolour](https://github.com/thedarkcolour/) 开发的 [KotlinForForge](https://github.com/thedarkcolour/KotlinForForge/) 前置模组，完全使用 Kotlin 语言开发 NeoForge 模组成为了可能。下面简要地就借助该前置模组开发 Kotlin 语言模组的步骤进行说明。

# NeoForge MDK 的搭建

前往 NeoForge 的 [示例 MDK 仓库](https://github.com/neoforged/MDK/) 下载示例 NeoForge 模组源码。切换到所下载的源码目录中，先运行 `./gradlew runClient` 尝试启动游戏客户端程序， Gradle 会自动下载完成所需的依赖文件，成功启动游戏后关闭。接下来根据自己的 IDE 情况运行 `./gradlew eclipse` 或 `./gradlew idea` 进行 IDE 相关配置，完成后用 IDE 打开项目。至此 MDK 搭建完毕。

# 配置项目 Kotlin 相关依赖

接下来需要对项目进行设置以引入 Kotlin 与前置模组 KotlinForForge 的支持。打开 `build.gradle` 文件，对 `plugins` 、 `repositories` 与 `dependencies` 代码块进行修改：

```groovy
plugins {
    id 'java-library'
    id 'eclipse'
    id 'idea'
    id 'maven-publish'
    id 'net.neoforged.gradle.userdev' version '7.0.80'
    // Adds the Kotlin Gradle plugin
    id 'org.jetbrains.kotlin.jvm' version '1.9.22'
    // OPTIONAL Kotlin Serialization plugin
    id 'org.jetbrains.kotlin.plugin.serialization' version '1.9.22'
}

repositories {
    mavenLocal()
    // Add KFF Maven repository
    maven {
        name = 'Kotlin for Forge'
        url = 'https://thedarkcolour.github.io/KotlinForForge/'
    }
}

dependencies {
    // Specify the version of Minecraft to use.
    // Depending on the plugin applied there are several options. We will assume you applied the userdev plugin as shown above.
    // The group for userdev is net.neoforged, the module name is neoforge, and the version is the same as the neoforge version.
    // You can however also use the vanilla plugin (net.neoforged.gradle.vanilla) to use a version of Minecraft without the neoforge loader.
    // And its provides the option to then use net.minecraft as the group, and one of; client, server or joined as the module name, plus the game version as version.
    // For all intends and purposes: You can treat this dependency as if it is a normal library you would use.
    implementation "net.neoforged:neoforge:${neo_version}"

    // Example mod dependency with JEI
    // The JEI API is declared for compile time use, while the full JEI artifact is used at runtime
    // compileOnly "mezz.jei:jei-${mc_version}-common-api:${jei_version}"
    // compileOnly "mezz.jei:jei-${mc_version}-forge-api:${jei_version}"
    // runtimeOnly "mezz.jei:jei-${mc_version}-forge:${jei_version}"

    // Example mod dependency using a mod jar from ./libs with a flat dir repository
    // This maps to ./libs/coolmod-${mc_version}-${coolmod_version}.jar
    // The group id is ignored when searching -- in this case, it is "blank"
    // implementation "blank:coolmod-${mc_version}:${coolmod_version}"

    // Example mod dependency using a file as dependency
    // implementation files("libs/coolmod-${mc_version}-${coolmod_version}.jar")

    // Example project dependency using a sister or child project:
    // implementation project(":myproject")

    // For more info:
    // http://www.gradle.org/docs/current/userguide/artifact_dependencies_tutorial.html
    // http://www.gradle.org/docs/current/userguide/dependency_management.html

    // Adds KFF as dependency and Kotlin libs (use the variant matching your mod loader)
    // NEOFORGE
    implementation 'thedarkcolour:kotlinforforge-neoforge:4.10.0'
}
```

接下来修改 `gradle.properties` 文件：
```properties
# Sets default memory used for gradle commands. Can be overridden by user or command line properties.
#org.gradle.jvmargs=
org.gradle.daemon=false
org.gradle.debug=false

#read more on this at https://github.com/neoforged/NeoGradle/blob/NG_7.0/README.md#apply-parchment-mappings
# you can also find the latest versions at: https://parchmentmc.org/docs/getting-started
neogradle.subsystems.parchment.minecraftVersion=1.20.3
neogradle.subsystems.parchment.mappingsVersion=2023.12.31
# Environment Properties
# You can find the latest versions here: https://projects.neoforged.net/neoforged/neoforge
# The Minecraft version must agree with the Neo version to get a valid artifact
minecraft_version=1.20.4
# The Minecraft version range can use any release version of Minecraft as bounds.
# Snapshots, pre-releases, and release candidates are not guaranteed to sort properly
# as they do not follow standard versioning conventions.
minecraft_version_range=[1.20.4,1.21)
# The Neo version must agree with the Minecraft version to get a valid artifact
neo_version=20.4.215
# The Neo version range can use any version of Neo as bounds
neo_version_range=[20.4,)
# The loader version range can only use the major version of FML as bounds
loader_version_range=[4.10,)

## Mod Properties

# The unique mod identifier for the mod. Must be lowercase in English locale. Must fit the regex [a-z][a-z0-9_]{1,63}
# Must match the String constant located in the main mod class annotated with @Mod.
mod_id=kotlindemo
# The human-readable display name for the mod.
mod_name=Kotlin NeoForge Demo Mod
# The license of the mod. Review your options at https://choosealicense.com/. All Rights Reserved is the default.
mod_license=All Rights Reserved
# The mod version. See https://semver.org/
mod_version=1.0.0
# The group ID for the mod. It is only important when publishing as an artifact to a Maven repository.
# This should match the base package used for the mod sources.
# See https://maven.apache.org/guides/mini/guide-naming-conventions.html
mod_group_id=top.srcres.mods.kotlindemo
# The authors of the mod. This is a simple text string that is used for display purposes in the mod list.
mod_authors=src_resources
# The description of the mod. This is a simple multiline text string that is used for display purposes in the mod list.
mod_description=Example mod description.\nNewline characters can be used and will be replaced properly.
```

然后打开 `src` 目录内的 `mods.toml` 文件，修改 `modLoader` 为 `kotlinforforge` ：

```toml
modLoader="kotlinforforge" #mandatory
```

接下来删除 `java` 目录，新建 `kotlin` 目录，即可在其中使用 Kotlin 语言编写代码了。笔者的示例代码如下：

```kotlin
package top.srcres.mods.kotlindemo

import com.mojang.logging.LogUtils
import net.neoforged.fml.common.Mod

@Mod(KotlinDemo.MODID)
object KotlinDemo {
    const val MODID = "kotlindemo"

    val logger = LogUtils.getLogger();

    init {
        logger.info("$MODID is initialized.")
    }
}
```

全部工作完成后，回到项目根目录，运行 `./gradlew runClient` 启动游戏。可以看到我们的示例模组已被正常加载：

{% asset_img ss.png Screenshot %}

# 项目源码

本文示例项目源码已上传 [GitHub](https://github.com/srcres258/kotlin-neoforge-demo-mod) 供读者参考，使用 [MIT](https://spdx.org/licenses/MIT.html) 协议开源。
