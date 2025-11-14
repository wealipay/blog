---
date: 2025-11-02 21:52
abbrlink: "searchbar"
categories: Blender网站源码
tags: Nextjs
title: SearchBar.tsx文件
excerpt: SearchBar代码
hidden: true
---

{% folding 01-04新增代码: %}

```ts
import { Search } from "lucide-react";
const SearchBar = () => {
  return (
    <div className="hidden sm:flex items-center gap-2 rounded-md ring-1 ring-gray-200 px-2 py-1 shadow-md">
      <Search className="w-4 h-4 text-gray-500" />
      <input
        id="search"
        placeholder="请输入搜索内容"
        className="text-sm outline-0"
      />
    </div>
  );
};
export default SearchBar;
{
  /*npm install lucide-react 安装lucide图标*/
}

```

- text-md：是一个文本字号工具类，对应的字体大小为 16px（1rem），行高为 24px（1.5rem），是日常排版中常用的中等字号样式。
- tracking-wider是文本字间距工具类，作用是增大字符之间的间距，对应的 CSS 实际值为  letter-spacing: 0.05em ，能让文字看起来更舒展。
- ring-1” 通常是 Tailwind CSS（一个流行的 CSS 框架）中的阴影类，表示给元素添加一层非常淡的、贴近元素的内阴影或外阴影（具体效果由框架预设），属于最浅的阴影层级之一。它常和其他阴影类（如 ring-2、ring-4 等）搭配使用，数字越大阴影越明显。
- “ring-gray-200” 是 Tailwind CSS 中用于设置 阴影颜色 的类，需和  ring （或  ring-1 / ring-2  等控制阴影粗细的类）配合使用。其中 “gray-200” 指 Tailwind 预设的一种浅灰色调，所以 “ring-gray-200” 就是将元素的阴影颜色设置为浅灰色。

{% endfolding %}
