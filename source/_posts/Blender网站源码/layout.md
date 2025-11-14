---
date: 2025-11-01 10:56
abbrlink: "layout"
categories: Blender网站源码
tags: Nextjs
title: Layout.tsx文件
excerpt: Layout代码
hidden: true
---

{% folding 01-04新增代码: %}

```ts
import Footer from "@/components/Footer";
import NavBar from "@/components/NavBar";

<div className="mx-auto p-4 sm:max-w-xl md:max-w-2xl lg:max-w-3xl xl:max-w-6xl">
  <NavBar />
    {children}
  <Footer />
</div>
```

- mx-auto 是 Tailwind CSS 的一个间距类，作用是给元素的左右（水平方向）设置自动外边距，从而实现元素在其父容器中水平居中对齐。
- 通常需要配合设置了宽度的块级元素使用才会生效。
- p-4 是 Tailwind CSS 的内边距类，意思是给元素的四个方向（上、右、下、左）都设置相等的内边距，其中  4  对应 Tailwind 的间距单位（默认 1 单位 = 0.25rem，所以  p-4  即 1rem，也就是 16px）。
- sm:max-w-xl 是 Tailwind CSS 的响应式类，意思是当屏幕宽度达到  sm （小屏幕，默认断点为 640px）及以上时，元素的最大宽度被限制为  xl  对应的尺寸（默认是 36rem，即 576px）。简单说就是“小屏幕起，元素最大宽固定为 576px”，能防止宽屏时元素过宽影响阅读
- md:max-w-2xl：屏幕宽度达到  md  断点（默认768px）及以上时，元素最大宽度为  2xl （默认42rem，即672px）。
- lg:max-w-3xl：屏幕宽度达到  lg  断点（默认1024px）及以上时，元素最大宽度为  3xl （默认48rem，即768px）。
- xl:max-w-6xl：屏幕宽度达到  xl  断点（默认1280px）及以上时，元素最大宽度为  6xl （默认72rem，即1152px）。

```ts
//tsconfig.json配置@别名：
"baseUrl": ".",
"paths": {
"@/*": ["./app/*"]
}
```

{% endfolding %}
