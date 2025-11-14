---
date: 2025-11-01 20:10
abbrlink: "footer"
categories: Blender网站源码
tags: Nextjs
title: Footer.tsx文件
excerpt: Footer代码
hidden: true
---

{% folding 05-08新增代码: %}

```ts
import Image from "next/image";
import Link from "next/link";

const Footer = () => {
  return (
    <div className="mt-16 flex flex-col items-center gap-8 md:flex-row md:items-start md:justify-between md:gap-0 bg-gray-800 p-8 rounded-lg">
      <div className="flex flex-col gap-4 items-center md:items-start">
        <Link href="/" className="flex items-center">
          <Image src="/logo.png" width={36} height={36} alt="logo" />
          <p className="hidden md:block text-md font-medium tracking-wider text-white">
            Wealipay
          </p>
        </Link>
        <p className="text-sm text-gray-400">© 2025 Wealipay</p>
        <p className="text-sm text-gray-400">版权所有</p>
      </div>
      <div className="flex flex-col gap-4 text-sm text-gray-400 items-center md:items-start">
        <p className="text-sm text-amber-50">相关链接</p>
        <Link href="/">首页</Link>
        <Link href="/">服务</Link>
        <Link href="/">关于</Link>
        <Link href="/">领红包</Link>
      </div>
      <div className="flex flex-col gap-4 text-sm text-gray-400 items-center md:items-start">
        <p className="text-sm text-amber-50">相关链接</p>
        <Link href="/">首页</Link>
        <Link href="/">服务</Link>
        <Link href="/">关于</Link>
        <Link href="/">领红包</Link>
      </div>
      <div className="flex flex-col gap-4 text-sm text-gray-400 items-center md:items-start">
        <p className="text-sm text-amber-50">相关链接</p>
        <Link href="/">首页</Link>
        <Link href="/">服务</Link>
        <Link href="/">关于</Link>
        <Link href="/">领红包</Link>
      </div>
      <div className="flex flex-col gap-4 text-sm text-gray-400 items-center md:items-start">
        <p className="text-sm text-amber-50">相关链接</p>
        <Link href="/">首页</Link>
        <Link href="/">服务</Link>
        <Link href="/">关于</Link>
        <Link href="/">领红包</Link>
      </div>
    </div>
  );
};
export default Footer;

```

- md:flex-row md:items-start md:justify-between:中等屏幕及以上，子元素“水平排、往上靠、两端拉满”；小屏幕则按默认布局（比如可能是垂直排列、居中对齐等）。
Fill:
- 父容器需显式声明  position: relative （或其他定位），否则  fill  会让图片以  absolute  定位全屏覆盖页面。
  典型使用场景:
- 卡片背景图：让图片填充卡片容器，文字叠加在上方。
  ​
- 响应式轮播图：轮播容器尺寸随屏幕变化，图片自动适配填充。
  ​
- 动态尺寸容器：如用户上传图片后，按容器比例自动适配显示。
  {% endfolding %}
- 在 Tailwind CSS 中， aspect-[]  是 控制元素宽高比 的工具类，通过  aspect-[width/height]  语法快速定义固定宽高比，无需手动计算宽高，适配响应式布局（尤其适合图片、视频、卡片等容器）。
  {% endfolding %}
