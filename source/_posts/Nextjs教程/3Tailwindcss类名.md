---
date: 2025-10-31 13:02
abbrlink: "class"
categories: nextjs教程
tags: Nextjs
title: 3Tailwindcss类名
---

{% folding mx-auto: %}

- mx-auto 是 Tailwind CSS 的一个间距类，作用是给元素的左右（水平方向）设置自动外边距，从而实现元素在其父容器中水平居中对齐。
- 通常需要配合设置了宽度的块级元素使用才会生效。
  {% endfolding %}

{% folding sm:max-w-xl: %}

- sm:max-w-xl 是 Tailwind CSS 的响应式类，意思是当屏幕宽度达到  sm （小屏幕，默认断点为 640px）及以上时，元素的最大宽度被限制为  xl  对应的尺寸（默认是 36rem，即 576px）。
- 简单说就是“小屏幕起，元素最大宽固定为 576px”，能防止宽屏时元素过宽影响阅读
- md:max-w-2xl：屏幕宽度达到  md  断点（默认768px）及以上时，元素最大宽度为  2xl （默认42rem，即672px）。
- lg:max-w-3xl：屏幕宽度达到  lg  断点（默认1024px）及以上时，元素最大宽度为  3xl （默认48rem，即768px）。
- xl:max-w-6xl：屏幕宽度达到  xl  断点（默认1280px）及以上时，元素最大宽度为  6xl （默认72rem，即1152px）。
  {% endfolding %}

{% folding p-4: %}

- p-4 是 Tailwind CSS 的内边距类，意思是给元素的四个方向（上、右、下、左）都设置相等的内边距，其中  4  对应 Tailwind 的间距单位（默认 1 单位 = 0.25rem，所以  p-4  即 1rem，也就是 16px）。
  {% endfolding %}

{% folding 配置@: %}

```
    "baseUrl": ".",
    "paths": {
      "@/*": ["./app/*"]
    }
```

{% endfolding %}
{% folding text-md: %}

- 在 Tailwind CSS 中， text-md  是一个文本字号工具类，对应的字体大小为 16px（1rem），行高为 24px（1.5rem），是日常排版中常用的中等字号样式。
  {% endfolding %}

{% folding tracking-wider: %}

- 在 Tailwind CSS 中， tracking-wider  是文本字间距工具类，作用是增大字符之间的间距，对应的 CSS 实际值为  letter-spacing: 0.05em ，能让文字看起来更舒展。
  {% endfolding %}

{% folding ring-1: %}

- “ring-1” 通常是 Tailwind CSS（一个流行的 CSS 框架）中的阴影类，表示给元素添加一层非常淡的、贴近元素的内阴影或外阴影（具体效果由框架预设），属于最浅的阴影层级之一。
- 它常和其他阴影类（如 ring-2、ring-4 等）搭配使用，数字越大阴影越明显。
  {% endfolding %}

{% folding ring-gray-200: %}
- “ring-gray-200” 是 Tailwind CSS 中用于设置 阴影颜色 的类，需和  ring （或  ring-1 / ring-2  等控制阴影粗细的类）配合使用。
- 其中 “gray-200” 指 Tailwind 预设的一种浅灰色调，所以 “ring-gray-200” 就是将元素的阴影颜色设置为浅灰色。
{% endfolding %}
