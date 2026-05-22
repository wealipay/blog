---
title: StarBorder组件
abbrlink: "starborder"
swiper: false
swiperImg: ''
img: ''
excerpt: 'StarBorder组件的使用'
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
date: 2026-05-21 05:10:16
swiperDesc:
---

{% folding 安装: %}
```shell
pnpm dlx jsrepo@latest add https://reactbits.dev/r/StarBorder-TS-TW
```
{% endfolding %}

{% folding 配置: %}
+ 由于组件使用了动画，需要全局globall.css中配置
```css
//globall.css
@keyframes star-movement-bottom {
   0% {
     transform: translate(0%, 0%);
     opacity: 1;
   }
   100% {
     transform: translate(-100%, 0%);
     opacity: 0;
   }
 }
 @keyframes star-movement-top {
   0% {
     transform: translate(0%, 0%);
     opacity: 1;
   }
   100% {
     transform: translate(100%, 0%);
     opacity: 0;
   }
 }
 @theme inline {
   --animate-star-movement-bottom: star-movement-bottom linear infinite alternate;
   --animate-star-movement-top: star-movement-top linear infinite alternate;
 }
```

{% endfolding %}

{% folding 使用: %}
+ 在InfiniteMenu组件中使用
{% endfolding %}

