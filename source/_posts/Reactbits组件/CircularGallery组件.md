---
title: CircularGallery组件
abbrlink: "circullarygallery"
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
date: 2026-05-28 19:44:06
swiperDesc:
---

{% folding 安装: %}
+ 环形画廊
```
pnpm dlx jsrepo@latest add https://reactbits.dev/r/CircularGallery-TS-TW
```
{% endfolding %}

{% folding 配置: %}
#### Props 属性说明区：
这是给开发者看的组件 API 文档，解释每个属性的类型、默认值和作用：
- items：画廊要展示的内容数组，每个元素包含  image （图片地址）和  text （标题文本），默认  undefined （需要自己传入）
- bend：和  Bend Level  对应，控制弯曲曲率，默认值是 3（和预览区当前值不同，是默认配置），正负值会改变弯曲方向
- textColor：标题文字的颜色，默认白色  #ffffff 
- borderRadius：图片圆角，默认 0.05
- scrollSpeed：滚动速度，默认 2
- scrollEase：滚动平滑度，默认 0.05
{% endfolding %}

{% folding 使用: %}
```
<div
    className="
    w-11/12
    absolute left-1/2 top-1/2
    transform
    -translate-y-1/2
    -translate-x-1/2 "
>
    <CircularGallery
        bend={3}
        textColor="#ffffff"
        borderRadius={0.05}
        bend={2}
        borderRadius={0.05}
        scrollSpeed={1.5}
        scrollEase={0.08}
    />
</div>
```
{% endfolding %}

