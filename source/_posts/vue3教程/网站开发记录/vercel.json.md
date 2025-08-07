---
date: 2025-08-4 18:05
abbrlink: 'verceljson'
categories: vue3教程
tags: vercel
title:
---
{% folding, vercel.json: %}
```ts
{
  "rewrites": [{
    "source":"/:path*",
    "destination":"/index.html"
  }]
}

```
这段代码是一个 URL 重写规则配置（常见于 Next.js、Vercel 等平台），它的含义是：

将所有不匹配其他具体路由的请求都重定向到 `/index.html` 文件。

具体解释：
1. `"source": "/:path*"`：
   - `:path*` 是一个通配符，匹配任何路径（包括多级路径）
   - 例如：`/about`、`/products/123` 等都会匹配这个规则

2. `"destination": "/index.html"`：
   - 将所有匹配的请求都指向 `/index.html`

这种配置通常用于：
- 单页应用（SPA）：确保所有路由都由前端 JavaScript 处理
- 前端路由：当用户直接访问或刷新非根路由时，仍然返回首页
- 静态网站部署：让服务器对所有路由返回同一个 HTML 文件

例如：
- 用户访问 `/about` → 实际返回 `/index.html`
- 用户访问 `/contact/us` → 实际返回 `/index.html`

注意：这种配置意味着后端不会处理 404 错误，所有未知路径都会返回首页，前端路由需要自己处理不存在的路径。
{% endfolding %}