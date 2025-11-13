---
date: 2025-11-01 10:57
abbrlink: "layout"
categories: Blender网站源码
tags: Nextjs
title: Layout.tsx文件
excerpt: Layout代码
toc: false
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

{% endfolding %}
