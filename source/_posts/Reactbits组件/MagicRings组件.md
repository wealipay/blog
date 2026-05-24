---
title: MagicRings
abbrlink: "magicRings"
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
date: 2026-05-20 23:09:48
swiperDesc:
---

{% folding 安装: %}
```shell
pnpm dlx jsrepo@latest add https://reactbits.dev/r/MagicRings-TS-TW
```
{% endfolding %}

{% folding 配置: %}
+ 需要在文件的开头标识"use client";
+ 全屏固定定位
```html
<div ref={mountRef} className='w-full min-h-dvh h-dvh h-screen'
style={blur > 0 ? { filter: `blur(${blur}px)` } : undefined}
		/>
```
{% endfolding %}

{% folding 使用: %}
```html
//page.tsx
<div className='absolute w-full min-h-dvh h-dvh h-screen'>
<MagicRings
	color='#A855F7'
	colorTwo='#6366F1'
	ringCount={8}
	speed={2}
	attenuation={10}
	lineThickness={1}
	baseRadius={0.1}
	radiusStep={0.1}
	scaleRate={0.01}
	opacity={0.9}
	blur={1}
	noiseAmount={0.41}
	rotation={0}
	ringGap={1.5}
	fadeIn={0.7}
	fadeOut={0.5}
	followMouse={false}
	mouseInfluence={0.2}
	hoverScale={1.2}
	parallax={0.05}
	clickBurst={false}
	/>
</div>
```
{% endfolding %}
