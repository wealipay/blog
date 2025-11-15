---
date: 2025-11-01 20:06
abbrlink: "page"
categories: Blender网站源码
tags: Nextjs
title: Page.tsx文件
excerpt: page代码
hidden: true
---

{% folding 01-04新增代码: %}

```ts
import ProductList from "./components/ProductList";
import Image from "next/image";

export default function Home() {
  return (
    <div className="">
      <div className="relative aspect-[3/1] mb-12">
        <Image src="/featured.png" alt="featured" fill />
      </div>
      <ProductList />
    </div>
  );
}


```

{% note, 轮播图： %}

- 父容器需显式声明  position: relative （或其他定位），否则  fill  会让图片以  absolute  定位全屏覆盖页面。
  典型使用场景:
- 卡片背景图：让图片填充卡片容器，文字叠加在上方。
- 响应式轮播图：轮播容器尺寸随屏幕变化，图片自动适配填充。
- 动态尺寸容器：如用户上传图片后，按容器比例自动适配显示。
- 在 Tailwind CSS 中， aspect-[]  是 控制元素宽高比 的工具类，通过  aspect-[width/height]  语法快速定义固定宽高比，无需手动计算宽高，适配响应式布局（尤其适合图片、视频、卡片等容器）。

{% endfolding %}
