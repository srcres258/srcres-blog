---
title: 高等数学随记 - 利用双元法求不定积分
date: 2024-03-19 15:51:35
tags: [高等数学随记, 考研]
mathjax: true
---

# 前言
双元法是近些年来网络上流传出的一种求解不定积分的新方式，其既有准确得值、计算简便的快捷性，又在传统的第一类、第二类换元积分法的基础上有所创新，给我们提供了另一个视角看待不定积分求解的思维历程. 尤其用在考研时该方法的正确使用亦可在作答试卷时起到事半功倍的效果，特此深入研究了一下该方法，以个人见解对其总结汇集于此.

# 例题引入

例1. 求$\int\sqrt{x^2+a^2}\mathrm{d}x$.

解1. \[第二类换元积分法\]

$$\int\sqrt{x^2+a^2}\mathrm{d}x = a\int\sqrt{(\frac{x}{a})^2+1}\mathrm{d}x = a^2\int\sqrt{(\frac{x}{a})^2+1}\mathrm{d}(\frac{x}{a}).$$

利用三角换元，$\mathrm{tan}\theta = \frac{x}{a}$，则$\mathrm{sec}\theta = \sqrt{\mathrm{tan}^2\theta+1} = \frac{\sqrt{x^2+a^2}}{a}$.

则

$$\int\sqrt{x^2+a^2}\mathrm{d}x = a^2\int\mathrm{sec}\theta\mathrm{d}\mathrm{tan}\theta$$

$$= a^2\mathrm{sec}\theta\mathrm{tan}\theta-a^2\int\mathrm{tan}\theta\mathrm{d}\mathrm{sec}\theta$$

$$= a^2\mathrm{sec}\theta\mathrm{tan}\theta-a^2\int\mathrm{tan}^2\theta\mathrm{sec}\theta\mathrm{d}\theta$$

$$= a^2\mathrm{sec}\theta\mathrm{tan}\theta-a^2\int(\mathrm{sec}^2\theta-1)\mathrm{sec}\theta\mathrm{d}\theta$$

$$= a^2\mathrm{sec}\theta\mathrm{tan}\theta-a^2\int\mathrm{sec}^3\theta\mathrm{d}\theta+a^2\int\mathrm{sec}\theta\mathrm{d}\theta.$$

注意到

$$\int\sqrt{x^2+a^2}\mathrm{d}x = a^2\int\mathrm{sec}\theta\mathrm{d}\mathrm{tan}\theta$$

$$= a^2\int\mathrm{sec}^3\theta\mathrm{d}\theta，$$

故移项得

$$2a^2\int\mathrm{sec}\theta\mathrm{d}\mathrm{tan}\theta = a^2\mathrm{sec}\theta\mathrm{tan}\theta+a^2\int\mathrm{sec}\theta\mathrm{d}\theta，$$

从而

$$\int\sqrt{x^2+a^2}\mathrm{d}x = a^2\int\mathrm{sec}\theta\mathrm{d}\mathrm{tan}\theta = \frac{a^2}{2}\mathrm{sec}\theta\mathrm{tan}\theta+\frac{a^2}{2}\int\mathrm{sec}\theta\mathrm{d}\theta$$

$$= \frac{a^2}{2}\mathrm{sec}\theta\mathrm{tan}\theta+\frac{a^2}{2}\mathrm{ln}\left|\mathrm{tan}\theta+\mathrm{sec}\theta\right|+C$$

$$= \frac{a^2}{2}\cdot\frac{x}{a}\cdot\frac{\sqrt{x^2+a^2}}{a}+\frac{a^2}{2}\mathrm{ln}\left|\frac{x}{a}+\frac{\sqrt{x^2+a^2}}{a}\right|+C$$

$$= \frac{x\sqrt{x^2+a^2}}{2}+\frac{a^2}{2}\mathrm{ln}(x+\sqrt{x^2+a^2})+C.$$

（注意$-\frac{a^2}{2}\mathrm{ln}\left|a\right|$已并入常数项$C$中；由于$\sqrt{x^2+a^2}+x$恒为正，故去掉绝对值符号. ）

解2. \[双元虚圆换元法\] 令$y = \sqrt{x^2+a^2}$，易得$y^2-x^2 = a^2$，从而$y\mathrm{d}y=x\mathrm{d}x$.

故

$$\int\sqrt{x^2+a^2}\mathrm{d}x = \int y\mathrm{d}x$$

$$= xy-\int x\mathrm{d}y$$

$$= xy-\int\frac{x^2\mathrm{d}x}{y}$$

$$= xy-\int\frac{(y^2-a^2)\mathrm{d}x}{y}$$

$$= xy-\int y\mathrm{d}x+a^2\int\frac{\mathrm{d}x}{y}，$$

移项得

$$2\int y\mathrm{d}x = xy+a^2\int\frac{\mathrm{d}x}{y}，$$

$$\int y\mathrm{d}x = \frac{xy}{2}+\frac{a^2}{2}\int\frac{\mathrm{d}x}{y}.$$

因$y\mathrm{d}y=x\mathrm{d}x$，故$\frac{\mathrm{d}x}{y}=\frac{\mathrm{d}y}{x}$，由合比定理有$\frac{\mathrm{d}x}{y}=\frac{\mathrm{d}y}{x}=\frac{\mathrm{d}x+\mathrm{d}y}{x+y}=\frac{\mathrm{d}(x+y)}{x+y}=\mathrm{d}\mathrm{ln}(x+y)$（此处绝对值符号可去，原因同解1）.

故

$$\int\sqrt{x^2+a^2}\mathrm{d}x = \frac{xy}{2}+\frac{a^2}{2}\int\frac{\mathrm{d}x}{y}$$

$$= \frac{xy}{2}+\frac{a^2}{2}\mathrm{ln}(x+y)+C.$$

将$y = \sqrt{x^2+a^2}$代入得

$$\int\sqrt{x^2+a^2}\mathrm{d}x = \frac{x\sqrt{x^2+a^2}}{2}+\frac{a^2}{2}\mathrm{ln}(x+\sqrt{x^2+a^2})+C.$$

# 方法总结：不定积分的双元换元法

一般地，我们将解不定积分的双元换元法分为两种类型：

- 类型1. 实圆双元：$x^2+y^2=C \Leftrightarrow x\mathrm{d}x=-y\mathrm{d}y$.
- 类型2. 虚圆双元：$x^2-y^2=C \Leftrightarrow x\mathrm{d}x=y\mathrm{d}y$.

对于以上两类型双元换元，我们有以下公式（由于常数$C$已在上两式中使用，故接下来积分常数用$C_0$表示）：

## 1. 双元第一公式

- \(1\) 对于实圆双元，$\int\frac{\mathrm{d}x}{y} = \mathrm{arctan}\frac{y}{x}+C_0$；
- \(2\) 对于虚圆双元，$\int\frac{\mathrm{d}x}{y} = \mathrm{ln}\left|x+y\right|+C_0$.

证明. \(1\) 由于$y\mathrm{d}y=-x\mathrm{d}x$，故

$$y\mathrm{d}x-x\mathrm{d}y=y\mathrm{d}x-x\cdot\frac{x\mathrm{d}x}{y}=\frac{(y^2+x^2)\mathrm{d}x}{y}$$

故

$$\mathrm{d}x = \frac{y(y\mathrm{d}x-x\mathrm{d}y)}{x^2+y^2}$$

故

$$\int\frac{\mathrm{d}x}{y} = \int\frac{1}{y}\cdot\frac{y(y\mathrm{d}x-x\mathrm{d}y)}{x^2+y^2}$$

$$= \int\frac{y\mathrm{d}x-x\mathrm{d}y}{x^2+y^2}，$$

又由于

$$\mathrm{d}(\frac{x}{y}) = \frac{y\mathrm{d}x-x\mathrm{d}y}{y^2}，$$

故

$$\int\frac{\mathrm{d}x}{y} = \int\frac{y^2}{y^2+x^2}\cdot\mathrm{d}(\frac{x}{y})$$

$$= \int\frac{1}{(\frac{x}{y})^2+1}\cdot\mathrm{d}(\frac{x}{y})$$

$$= \mathrm{arctan}\frac{x}{y}+C_0.$$

\(2\) 因$y\mathrm{d}y=x\mathrm{d}x$，故$\frac{\mathrm{d}x}{y}=\frac{\mathrm{d}y}{x}$，由合比定理有$\frac{\mathrm{d}x}{y}=\frac{\mathrm{d}y}{x}=\frac{\mathrm{d}x+\mathrm{d}y}{x+y}=\frac{\mathrm{d}(x+y)}{x+y}=\mathrm{d}\mathrm{ln}\left|x+y\right|$.

故

$$\int\frac{\mathrm{d}x}{y} = \int\mathrm{d}\mathrm{ln}\left|x+y\right|$$

$$= \mathrm{ln}\left|x+y\right|+C_0.$$

## 2. 双元第三公式

- \(1\) 对于实圆双元，$\int\frac{\mathrm{d}x}{y^3} = \frac{1}{y^2+x^2}\cdot\frac{x}{y}+C_0 = \frac{x}{Cy}+C_0$；
- \(2\) 对于虚圆双元，$\int\frac{\mathrm{d}x}{y^3} = \frac{1}{y^2-x^2}\cdot\frac{x}{y}+C_0 = -\frac{x}{Cy}+C_0$.

证明. \(1\) 类似双元第一公式的证法，

$$\int\frac{\mathrm{d}x}{y^3} = \int\frac{1}{y^2}\cdot\frac{\mathrm{d}x}{y}$$

$$= \int\frac{1}{y^2}\cdot\frac{y\mathrm{d}x-x\mathrm{d}y}{x^2+y^2}$$

$$= \int\frac{1}{x^2+y^2}\cdot\frac{y\mathrm{d}x-x\mathrm{d}y}{y^2}$$

$$= \int\frac{1}{x^2+y^2}\cdot\mathrm{d}(\frac{x}{y})$$

$$= \frac{1}{x^2+y^2}\cdot\frac{x}{y}+C_0$$

$$= \frac{x}{Cy}+C_0.$$

\(2\) 由于

$$x\mathrm{d}x=y\mathrm{d}y，$$

故

$$\mathrm{d}y=\frac{x\mathrm{d}x}{y}，$$

故

$$y\mathrm{d}x-x\mathrm{d}y = y\mathrm{d}x-x\cdot\frac{x\mathrm{d}x}{y}$$

$$= \frac{(y^2-x^2)\mathrm{d}x}{y}，$$

故

$$\mathrm{d}x = \frac{y(y\mathrm{d}x-x\mathrm{d}y)}{y^2-x^2}，$$

故

$$\int\frac{\mathrm{d}x}{y^3} = \int\frac{1}{y^3}\cdot\frac{y(y\mathrm{d}x-x\mathrm{d}y)}{y^2-x^2}$$

$$= \int\frac{y\mathrm{d}x-x\mathrm{d}y}{y^2(y^2-x^2)}$$

$$= \int\frac{1}{y^2-x^2}\mathrm{d}(\frac{x}{y})$$

$$= \frac{1}{y^2-x^2}\cdot\frac{x}{y}+C_0$$

$$= -\frac{x}{Cy}+C_0.$$

## 3. 双元第二公式

注：此公式的形式已在例1中解2的过程中给出，此处总结一般情形.

- \(1\) 对于实圆双元，$\int y\mathrm{d}x = \frac{xy}{2}+\frac{x^2+y^2}{2}\int\frac{\mathrm{d}x}{y} = \frac{xy}{2}+\frac{C}{2}\int\frac{\mathrm{d}x}{y}$；
- \(2\) 对于虚圆双元，$\int y\mathrm{d}x = \frac{xy}{2}-\frac{x^2-y^2}{2}\int\frac{\mathrm{d}x}{y} = \frac{xy}{2}-\frac{C}{2}\int\frac{\mathrm{d}x}{y}$.

这里每一个结论均有两种证法，其中分部积分法即为例1中解2的过程所用形式.

证明. \(1\) \[证法一 - 分部积分法\] 由于

$$\int y\mathrm{d}x = xy-\int x\mathrm{d}y$$

$$= xy-\int x\cdot(-\frac{x\mathrm{d}x}{y})$$

$$= xy+\int \frac{x^2\mathrm{d}x}{y}$$

$$= xy+\int \frac{C-y^2}{y}\mathrm{d}x$$

$$= xy+C\int \frac{\mathrm{d}x}{y}-\int y\mathrm{d}x，$$

故移项得

$$2\int y\mathrm{d}x = xy+C\int \frac{\mathrm{d}x}{y}，$$

$$\int y\mathrm{d}x = \frac{xy}{2}+\frac{C}{2}\int \frac{\mathrm{d}x}{y}$$

$$= \frac{xy}{2}+\frac{x^2+y^2}{2}\int \frac{\mathrm{d}x}{y}.$$

\[证法二 - 二分裂项法\]

$$\int y\mathrm{d}x = \frac{1}{2}\int y\mathrm{d}x-\frac{1}{2}\int(-y\mathrm{d}x)$$

$$= \frac{1}{2}\int(x\mathrm{d}y+y\mathrm{d}x)-\frac{1}{2}\int(x\mathrm{d}y-y\mathrm{d}x)$$

$$= \frac{1}{2}\int\mathrm{d}(xy)+\frac{1}{2}\int(y\mathrm{d}x-x\mathrm{d}y)$$

$$= \frac{1}{2}xy+\frac{1}{2}\int(y\mathrm{d}x-x(-\frac{x\mathrm{d}y}{y}))$$

$$= \frac{1}{2}xy+\frac{1}{2}\int\frac{x^2+y^2}{y}\mathrm{d}x$$

$$= \frac{xy}{2}+\frac{x^2+y^2}{2}\int\frac{\mathrm{d}x}{y}$$

$$= \frac{xy}{2}+\frac{C}{2}\int\frac{\mathrm{d}x}{y}.$$
