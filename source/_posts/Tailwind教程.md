---
title: Tailwind教程
abbrlink: 'tailwind'
swiper: false
swiperImg: ''
img: ''
excerpt: ''
top: false
toc: false
tocOpen: false
onlyTitle: false
comments: false
share: false
copyright: true
donate: false
bgImg: ''
bgImgTransition: translate-fade
bgImgDelay: 180000
categories: Next.js16教程
tags: next.js16
imgTop: true
date: 2026-06-05 12:44:07
swiperDesc:
---

{% folding 颜色: %}
+ 在 Tailwind CSS 项目中使用和定制颜色调色板。
+ 默认色板中的每种颜色都包含 11 个级别，50 为最浅色，950 为最深色：
+ 调整不透明度:
   您可以使用类似于 bg-black/75 的语法来调整颜色的不透明度，其中 75 将颜色的 alpha 通道设置为 75%
+ 针对深色模式
   使用 dark 变体编写类似 dark:bg-gray-800 的类，仅在深色模式激活时应用颜
+ space-y-*
  是 Tailwind 最常用的布局工具类之一，用于在容器的直接子元素之间添加统一的垂直间距，space-y-5  会给容器中除最后一个子元素外的所有直接子元素添加  1.25rem （20px）的底部外边距，从而在子元素之间创建均匀的垂直间距。
+ 子元素的  margin-bottom  会与  space-y  叠加
+ 小于md=2xl，≥md=3xl，≥lg=4xl，移动端缩小字号防溢出
+ transition-colors  是 Tailwind 内置过渡工具类，只对颜色属性开启过渡动画，不处理宽高、位移、透明度。
  生效属性
  只过渡这些颜色类：
  color （文字颜色:text-*）
  background-color （bg-*）
  border-color （border-*）
  outline-color
  fill 、 stroke
{% endfolding %}
