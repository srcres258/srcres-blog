---
title: 模组简介 - CreativeTabSearch
date: 2024-02-29 20:25:53
tags: 模组简介
categories: 模组简介
---

# 创造物品栏检索 CreativeTabSearch

现已支持**Fabric**，但需安装前置模组[**Fabric API**](https://www.mcmod.cn/class/3124.html)。

## 概述
在创造模式物品栏上方添加搜索框用以快速筛选某一创造物品标签页。

## 相关链接
名称 | 链接
:---: | :---
GitHub | https://github.com/srcres258/CreativeTabSearch/
MC百科 | https://www.mcmod.cn/class/13913.html
CurseForge | https://legacy.curseforge.com/minecraft/mc-mods/creativetabsearch
Modrinth | https://modrinth.com/mod/creativetabsearch

# 简介
该模组在创造模式物品栏添加了一个搜索栏，以便检索指定的创造物品栏页。<br>
**该模组只能在客户端上使用。** 尝试在专用服务端上加载此模组将会导致崩溃。

# 用法
加载此模组后，你可以在创造模式物品栏上方看到一个输入框：
{% asset_img ss1.png Screenshot 1 %}

在此输入框中输入任意内容后，只有与输入相匹配的物品栏页被显示出来：
{% asset_img ss2.png Screenshot 2 %}
{% asset_img ss3.png Screenshot 3 %}

可以点击旁边的“X”按钮以快速清除所输入的内容。
{% asset_img ss4.png Screenshot 4 %}
{% asset_img ss5.png Screenshot 5 %}

其他语言也受支持，例如简体中文：
{% asset_img ss6.png Screenshot 6 %}

0.1.2 版本开始新增高级搜索选项，需带前缀“@”。

@modid：搜索指定modid的模组标签页，可指定多个（图中仅指定了1个）：
{% asset_img ss7.png Screenshot 7 %}

@itemid：搜索包含指定物品id的标签页，可指定多个（图中仅指定了1个）：
{% asset_img ss8.png Screenshot 8 %}

# 协议
本项目使用 [GNU Lesser General Public License v3.0 only](https://spdx.org/licenses/LGPL-3.0-only.html) 授权。

