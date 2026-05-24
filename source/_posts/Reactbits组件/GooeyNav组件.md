---
title: GooeyNav组件
abbrlink: 'gooeynav'
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
tags: reactbits
imgTop: true
date: 2026-05-22 23:02:16
swiperDesc:
---

{% folding 安装: %}
```shell
pnpm dlx jsrepo@latest add https://reactbits.dev/r/GooeyNav-TS-TW
```
{% endfolding %}

{% folding 配置: %}
+ 需要在文件的开头标识"use client";
#### 为特效配置指定颜色：
```css
<style>
{`
:root {
--color-1: rgb(141,23,23);
--color-2: rgb(11,59,206);
--color-3: rgb(234,235,238);
--color-4: rgb(207,30,199);
`
 </style>
}
```
#### 定义导航数组：
```json
//types/navs.tsx
export const runningNavs = [
	{ label: "首页", href: "/" },
	{ label: "跑步", href: "#" },
	{ label: "轨迹", href: "#" }
];
```
{% endfolding %}

{% folding 使用: %}
```
//running/layout.tsx
import { runningNavs } from "../type/navs";
<div className='fixed left-0 bottom-1 text-2xl w-full h-[3rem] flex justify-around items-center'>
	<GooeyNav
		items={runningNavs}
		particleCount={20}
		particleDistances={[90, 10]}
		particleR={600}
		initialActiveIndex={1}
		animationTime={300}
		timeVariance={300}
		colors={[1, 2, 3, 4, 1, 2, 3, 4]}
	/>
</div>
```
{% endfolding %}
