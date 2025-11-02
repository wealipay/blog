---
date: 2025-11-02 21:52
abbrlink: "searchbar"
categories: Blender网站源码
tags: Nextjs
title: SearchBar.tsx文件
excerpt: SearchBar代码

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

{% endfolding %}
