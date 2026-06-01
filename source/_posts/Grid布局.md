---
title: Grid布局
abbrlink: 'grid'
swiper: false
swiperImg: ''
img: ''
excerpt: 'grid布局详解'
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
date: 2026-05-29 23:14:16
swiperDesc:
---

{% folding grid布局详解: %}
+ Grid 是二维布局（同时控制行+列），适合整体页面、卡片、宫格布局，是目前最强的网页布局方案。默认是肉按行排列
+ grid-template-columns 定义列

```ts
        .containner{
          display: grid;
          border: 1px solid red;
          gap:1px;
          grid-template-columns: minmax(150px,1fr) 1fr 1fr;
        }
```

+ grid-template-rows 定义行
#### gap:
+ gap 专门设置网格/弹性布局元素之间的间距，不包含容器内外边距，是  grid-gap  新标准写法。
```ts
/* 第一个值：行间距  第二个值：列间距 */
gap: 10px 20px;
```
+ 只作用于元素之间
+ 容器最外侧不会产生间距，区别于  margin 。
+ 3列网格，只会在第1&2、2&3列中间产生间隙。
```css
    .item-1{
      grid-row-start: 1;
      grid-row-end: 3;
      grid-column-start: 2;
      grid-column-end: 4;
    }
    
 .item-1{
      grid-row: 1/3;
      grid-column: 4/6;
    }
 
    
```

#### grid-template-areas 详解
+ grid-template-areas  是 CSS Grid 布局 用来给网格区域命名，直观划分页面布局，搭配  grid-area  使用。
+ 配套属性：grid-area
 给子元素绑定区域名：

```ts
.container {
  display: grid;
  /* 格式：每行写一组区域名，引号包裹，空格分隔 */
  grid-template-areas:
    "头部 头部"
    "侧边 主体"
    "底部 底部";
  /* 配合行列尺寸 */
  grid-template-columns: 200px 1fr;
  grid-template-rows: 60px 1fr 50px;
}

```

{% endfolding %}
