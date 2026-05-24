---
title: InfiniteMenu组件
abbrlink: "infiniteMenu"
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
date: 2026-05-21 02:28:19
swiperDesc:
---

{% folding 安装: %}
```shell
pnpm dlx jsrepo@latest add https://reactbits.dev/r/InfiniteMenu-TS-TW
```
{% endfolding %}

{% folding 配置: %}
+ 需要在文件的开头标识"use client";
+ 全屏固定定位：
```html
<div className='relative w-full min-h-dvh h-dvh h-screen '>
```

+ 垂直居中：

```css
absolute
font-black
[font-size:4rem]
left-1/2
top-1/2
transform
-translate-y-1/2
-translate-x-1/2
```

{% endfolding %}

{% folding 导入StarBorder组件: %}
```tsx
<StarBorder
	as='button'
	className=' text-4xl'
	color='red'
	thickness='1'
	speed='3s'>
	<span className='text-3xl  text-white'>
		&nbsp; ✨ 点击跳转 &nbsp;&nbsp;
	</span>
</StarBorder>
```
{% endfolding %}

{% folding 使用: %}
```
<div className='absolute w-full min-h-dvh h-dvh h-screen opacity-50'>
	<InfiniteMenu items={navs} scale={0.3} />
</div>
```
{% endfolding %}
