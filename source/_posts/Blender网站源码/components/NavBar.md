---
date: 2025-11-02 21:46
abbrlink: "navbar"
categories: Blender网站源码
tags: Nextjs
title: NavBar.tsx文件
excerpt: NavBar代码
---

{% folding 01-04新增代码: %}

```ts
import SearchBar from "./SearchBar";
import Image from "next/image";
import Link from "next/link";
import {Home} from "lucide-react"

const NavBar = () => {
  return (
    <nav className="w-full flex items-center justify-between border-b border-gray-200 pb-4">
      {/*Left*/}
      <Link href="/" className="flex items-center">
        <Image
          src="/logo.png"
          width={36}
          height={36}
          alt="logo"
          className="w-6 h-6 md:w-9 md:h-9"
        />
        <p className="hidden md:block text-md font-medium tracking-wider">
          Wealipay
        </p>
      </Link>
      {/*Right*/}
      <div className="">
        <SearchBar />
        <Link href="/">
          <Home />
        </Link>
      </div>
    </nav>
  );
};
export default NavBar;

```

{% endfolding %}

{% folding 05-08新增代码: %}

```ts
import { Home, Bell, ShoppingCart } from "lucide-react";
<div className="flex items-center gap-6">
  <Bell className="w-4 h-4 text-gray-600" />
  <ShoppingCart className="w-4 h-4 text-gray-600" />
  <Link href="/login">登陆</Link>
</div>

```

{% endfolding %}
