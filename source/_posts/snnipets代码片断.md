---
title: snnipets代码片断
abbrlink: 'snnipets'
swiper: false
swiperImg: ''
img: ''
excerpt: '自定义代码片断'
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
categories: Snnipets
tags: snnipets
imgTop: true
date: 2026-05-26 07:14:25
swiperDesc:
---

### 自定义代码片断
+ 在Acode中安装插件*React and React Router v7 Snippet and Auto Importer*
{% folding tsx格式代码片断: %}
#### 路径：
```path
内部存储/Android/data/com.foxdebug.acode/files/plugins/acode.plugin.react.snippet/snippets/tsx.snippets
```
{% folding iccn: %}
```snippets
snippet iccn
	import ${1} from '@/components/${1}';
```
{% endfolding %}

{% folding edf: %}
```snippets
export default function {fileName}() { return ( <div>$1</div> ) }
```
{% endfolding %}

{% folding ilk: %}
```
snippet ilk
	import Link from "next/link"
```
{% endfolding %}

{% endfolding %}

<hr/>




{% folding Tailwind代码片断: %}
#### 路径：
```path
内部存储/Android/data/com.foxdebug.acode/files/plugins/acode.plugin.react.snippet/snippets/reactTag.snippets
```
{% folding hdvh: %}
```
snippet hdvh
	<div className="w-full h-dvh h-min-dvh h-screen">
		${1}
	</div>
```
{% endfolding %}

{% endfolding %}
