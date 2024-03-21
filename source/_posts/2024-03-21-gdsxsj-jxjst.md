---
title: 高等数学随记 - 一道极限计算题的简化求解
date: 2024-03-21 11:16:46
tags: [高等数学随记, 考研]
mathjax: true
---

# 题目

例1. 求$\lim_{x \to 0} \frac{e(x-2)+2e^{\frac{\ln(x+1)}{x}}}{2x^2}$.

# 解法一：常规解法，洛必达法则（繁琐，暂略）

# 解法二：简化解法，利用麦克劳林公式（注意适用条件）

解. 取以下麦克劳林公式：（$\ln(x+1)$展开到3次项，$e^x$展开到2次项）

$$\ln(x+1) = x-\frac{x^2}{2}+\frac{x^3}{3}+\mathrm{o}(x^3)，$$

$$e^x = 1+x+\frac{x^2}{2}+\mathrm{o}(x^2)，$$

对原式有：

$$\lim_{x \to 0} \frac{e(x-2)+2e^{\frac{\ln(x+1)}{x}}}{2x^2} = \lim_{x \to 0} \frac{e(x-2)+2e^{\frac{x-\frac{x^2}{2}+\frac{x^3}{3}+\mathrm{o}(x^3)}{x}}}{2x^2}$$

$$= \lim_{x \to 0} \frac{e(x-2)+2e^{1-\frac{x}{2}+\frac{x^2}{3}+\mathrm{o}(x^2)}}{2x^2}$$

$$= \lim_{x \to 0} \frac{e(x-2)+2e\cdot e^{-\frac{x}{2}+\frac{x^2}{3}+\mathrm{o}(x^2)}}{2x^2}$$

$$= \lim_{x \to 0} \frac{e(x-2)+2e(1-\frac{x}{2}+\frac{x^2}{3}+\mathrm{o}(x^2)+\frac{(-\frac{x}{2}+\frac{x^2}{3}+\mathrm{o}(x^2))^2}{2}+\mathrm{o}((-\frac{x}{2}+\frac{x^2}{3}+\mathrm{o}(x^2))^2))}{2x^2}$$

$$= \lim_{x \to 0} \frac{2e(\frac{x^2}{3}+\frac{x^2}{8})+\mathrm{o}(x^2)}{2x^2}$$

$$= \lim_{x \to 0} \frac{2e\cdot\frac{11}{24}x^2}{2x^2}$$

$$= \frac{11}{24}e.$$
