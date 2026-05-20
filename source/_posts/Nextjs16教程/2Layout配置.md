---
title: 2Layout配置
abbrlink: "layout"
swiper: false
swiperImg: ''
img: ''
excerpt: '网站全局配置'
top: true
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
date: 2026-05-20 20:40:49
swiperDesc: 
---

{% folding Metadata: %}
```ts
import type { Metadata } from "next";
import { siteConfig } from "../siteConfig"; //网站全局配置文件

export const metadata: Metadata = {
	title: {
		default: siteConfig.title,
		template: `%s | ${siteConfig.title}`
	},
	keywords: siteConfig.keywords,
	authors: siteConfig.authors,
	viewport:
		"width=device-width, initial-scale=1, maximum-scale=1,user-scalable=no",
	description: siteConfig.desc,
	icons: {
		icon: siteConfig.faviconUrl,
		apple: siteConfig.faviconUrl
	},
	alternates: {
		canonical: "https://wealipay.top/"
	},
	robots: {
		index: true,
		follow: true,
		googleBot: {
			index: true,
			follow: true
		}
	},
	locale: "zh-CN"
};
```


```ts
//siteConfig.ts
export const siteConfig = {
	title: "wealipay",
	desc: "记录学习Nextjs16历程",
	keywords: ["wealipay", "Next.js16", "Tailwind V4"],
	authors: [{ name: "wealipay" }],
	faviconUrl: "./favicon.ico"
};
```


- 作用：从 Next.js 中导入 Metadata 类型（用于定义页面的 SEO 元数据，如标题、描述等）。
- 注意：import type 表示仅导入类型（TypeScript 特性），不会增加运行时的体积
- 定义网站全局配置文件siteConfig.ts

{% endfolding %}

{% folding 加载马善政字体: %}
{% folding 初始化字体: %}
```ts
import { Ma_Shan_Zheng } from "next/font/google";
  const maShan = Ma_Shan_Zheng({
	weight: ["400"],
	subsets: ["latin"],
	display: "swap",
	variable: "--font-mashan",
	preload: true
});
```

####  subsets: ["latin"]： 
- 只加载拉丁字母字符集（英文、数字），减小字体文件体积。 
- 如果要支持中文，一般要加  ["latin", "chinese"] 。
<hr/>

####  display: "swap"： 
字体加载策略：
- 网页先用默认字体显示
- 等 Ma_Shan_Zheng 下载完自动替换
避免文字长时间空白、闪烁。
<hr/>

####  variable: "--font-mashan"： 
把这个字体绑定到 CSS 变量  --font-mashan 。
后面你在 CSS 里可以直接用：
```css
font-family: var(--font-mashan);
```
或者在tailwind中使用font-mashan

<hr/>

####  preload: true： 
 
开启预加载，浏览器优先提前加载这个字体，页面渲染更快。

{% endfolding %}
	
{% folding 使用字体: %}

```ts
<html lang='zh-CN' className={`${maShan.className}  antialiased`} suppressHydrationWarning>
</html>
```
+ JSX 里 { }：插 JS 变量/代码
+ 反引号`：方便拼接字符串，支持 ${} 插值
+ 把拼接的类名注入到html标签上供全局使用
+ suppressHydrationWarning 是 Next.js / React 原生属性，作用：关闭当前标签的「服务端渲染 和 客户端渲染 内容不一致」的 Hydration 水合报错。

#### h-full（Tailwind）：
 
+ 给 html标签设置高度 100%
作用：
- 让页面高度铺满整个屏幕
- 解决页面高度塌陷、滚动条、底部留白等常见布局问题

<hr/>

#### antialiased：
+ 抗锯齿；平滑边缘

<hr/>

#### suppressHydrationWarning：
+ 前后端内容不一致抑制水合警告

<hr/>

{% folding 为什么必须这样用: %}
##### 性能优化：
+ Next.js 会通过这个className自动：
+ 预加载字体文件
+ 托管字体到你的域名（避免第三方请求）
+ 实施font-display策略
##### SSR支持：
+ 服务端渲染时就能注入正确的字体CSS
+ 避免客户端闪烁（FOUC） 
{% endfolding %}

{% endfolding %}


{% folding 关闭TS检查: %}

```ts
typescript: {
    ignoreBuildErrors: true, // 临时关闭 TS 检查
  },
```
{% endfolding %}

{% endfolding %}

{% folding 2026-05-20完整代码: %}
```tsx
import type { Metadata } from "next";
import { Ma_Shan_Zheng } from "next/font/google";
import "./globals.css";
import { siteConfig } from "../siteConfig";

const maShan = Ma_Shan_Zheng({
	weight: ["400"],
	subsets: ["latin"],
	display: "swap",
	variable: "--font-mashan",
	preload: true
});

export const metadata: Metadata = {
	title: {
		default: siteConfig.title,
		template: `%s | ${siteConfig.title}`
	},
	keywords: siteConfig.keywords,
	authors: siteConfig.authors,
	viewport:
		"width=device-width, initial-scale=1, maximum-scale=1,user-scalable=no",
	description: siteConfig.desc,
	icons: {
		icon: siteConfig.faviconUrl,
		apple: siteConfig.faviconUrl
	},
	alternates: {
		canonical: "https://wealipay.top/"
	},
	robots: {
		index: true,
		follow: true,
		googleBot: {
			index: true,
			follow: true
		}
	},
	locale: "zh-CN"
};

export default function RootLayout({
	children
}: Readonly<{
	children: React.ReactNode;
}>) {
	return (
		<html
			lang='zh-CN'
			className={`${maShan.className} antialiased`}
			suppressHydrationWarning>
			<body>{children}</body>
		</html>
	);
}

```
{% endfolding %}
