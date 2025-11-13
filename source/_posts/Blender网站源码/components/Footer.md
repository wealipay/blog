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

{% endfolding %}
