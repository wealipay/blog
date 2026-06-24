---
title: Brainwave教程
abbrlink: "brainwave"
swiper: false
swiperImg: ""
img: ""
excerpt: "知识点汇集"
top: false
toc: false
tocOpen: false
onlyTitle: false
comments: false
share: false
copyright: true
donate: false
bgImg: ""
bgImgTransition: translate-fade
bgImgDelay: 180000
categories: Next.js16教程
tags: next.js16
imgTop: true
date: 2026-06-11 19:33:09
swiperDesc:
---

{% folding Button组件: %}

```tsx
import ButtonSvg from "@/assets/svg/ButtonSvg";

type ButtonProps = {
  className?: string;
  href?: string;
  onClick?: () => void;
  children: React.ReactNode;
  px?: string;
  white?: boolean;
};

export default function Button({
  className,
  href,
  onClick,
  children,
  px,
  white
}: ButtonProps) {
  const classes = `
     button 
     relative inline-flex items-center justify-center 
     h-11 
     transition-colors 
     hover:text-color-1 
     ${px || "px-7"} 
     ${white ? "text-n-8" : "text-n-1"}
     ${className || ""}
   `;
  const spanClasses = "relative z-10";
  const Tag = href ? "a" : "button";
  return (
    <Tag className={classes} href={href} onClick={onClick}>
      <span className={spanClasses}>{children}</span>
      {ButtonSvg(white)}
    </Tag>
  );
}
```

<hr />
{% folding 知识点: %}

- 类型定义

```ts
type ButtonProps = {}
//无返回值的函数
onClick?: () => void;
```

<hr />

- h-11
  11 = 对应间距刻度，1 单位 = 0.25rem,h-11就是2.75rem,44px
- 模板字符串
  模板字符串是 JavaScript 里一种升级版字符串写法，专门用来解决「普通字符串拼接麻烦、换行不方便」的问题，写法是用反引号 `
  嵌入变量 ${}：在模板字符串里用  ${变量/计算/函数} ，可以直接把动态内容插进去，替代繁琐的  +  拼接。
- ${ }
  模板字符串的插值语法，里面可以写 JS 表达式，最终把结果拼成字符串。
- {ButtonSvg(white)}
  是一个专门返回 SVG 图形的函数（不是 React 组件，所以写法是  ButtonSvg(white)  调用，而非  <ButtonSvg /> ）。
  按钮的自定义外观、背景、边框、异形轮廓、装饰图形
  视觉层级：做底层背景，不遮挡文字
- @theme 定义自定义颜色
  CSS文件中用  @theme  定义  --color-\*  变量，自动生成工具类（如  bg-brand-500 、 text-primary ）
- color-scheme: dark详解
  这是 CSS 原生配色模式属性，用于适配系统/浏览器的深色/浅色模式。
  自动改变浏览器原生控件样式：滚动条、表单、按钮、输入框、下拉框、系统弹窗等
  /_ 放在根元素，全局生效 _/

```ts
:root{
  color-scheme: dark;
}
```

<hr />

- @media (prefers-color-scheme)
  这是 CSS 媒体查询，用来读取用户系统/浏览器当前的主题模式（深色/浅色），自动匹配样式。
  纯 CSS 实现无感自动换肤，不用 JS
  prefers-color-scheme: light
  系统开启浅色/白天模式时生效

```ts
@media (prefers-color-scheme: light) {
  /* 浅色样式写这里 */
}
```

- prefers-color-scheme: dark
- 系统开启深色/夜间模式时生效

```ts
@media (prefers-color-scheme: dark) {
  /* 深色样式写这里 */
}

```

<hr />

- @utility 
  是 Tailwind CSS v4 新增的核心指令，专门用来创建自定义工具类（Utilities），让你可以像使用内置类（比如  text-center 、 backdrop-blur-sm ）一样，定义自己的样式工具类，同时获得完整的变体支持（hover、focus、响应式等）
  定义新的原子工具类用  @utility ，组合现有类写组件用  @apply
  动态值工具类（支持任意值）

```ts
@utility my-* {
  margin-top: --value(--spacing);
  margin-bottom: --value(--spacing);
}

```

<hr />

{% endfolding %}

{% endfolding %}

<hr >

{% folding Header组件: %}

{% folding 知识点: %}

- Link组件
  . <Link> 是 Next.js 官方推荐的客户端导航组件，基于 <a>标签封装，核心优势是客户端无刷新跳转 + 自动预取（prefetch），大幅提升SPA体验 。
  prefetch（预取，默认 true）
  true（默认）：视口内自动预取静态页面（SSG），鼠标悬停更快 。
  false：关闭预取（如频繁隐藏的弹窗链接）。

```ts
<Link href="/heavy-page" prefetch={false}>
  不预取的页面
</Link>

```

3.   replace （替换历史，默认  false ）

-  false ：正常添加历史记录（可返回）。
  ​
-  true ：替换当前历史（返回跳过此页，适合登录后跳转） 。

```
<Link href="/login" replace>
  登录（替换历史）
</Link>

```

4.   scroll （滚动复位，默认  true ）

-  true ：跳转后滚动到顶部。
  ​
-  false ：保持滚动位置（适合列表页跳详情再返回） 。

5.   onNavigate （跳转回调，16+ 新增）

```ts
<Link
  href="/checkout"
  onNavigate={(e) => {
    console.log('跳转前', e)
    // e.preventDefault() // 取消跳转
  }}
>
  去结算

</Link>
```

跳转前触发，可用于埋点、拦截、取消导航 。

- Image组件
  Next.js 16 的  <Image>  是内置图片优化组件，扩展原生  <img> ，提供自动格式转换（WebP/AVIF）、响应式尺寸、懒加载、布局偏移防护等能力，显著提升性能与用户体验 。
   preload  替代  priority ：语义更清晰，用于首屏关键图预加载
   loading  行为优化：默认  lazy ，可设  eager  强制立即加载
   sizes  建议必配：提升响应式加载精度，优化带宽
  模糊占位增强：本地图自动生成  blurDataURL ，远程图需手动提供

```ts
import Image from 'next/image'
import productImg from '@/public/product.jpg' // 静态导入

export default function Product() {
  return (
    <Image
      preload={true}
      src={productImg}       // 直接使用导入对象
      alt="产品详情图"
      placeholder="blur"     // 模糊占位
    />
  )
}

```

3. 远程图片（需配置）

在  next.config.js  声明信任域名：

```ts
/** @type {import('next').NextConfig} */
const nextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: "https",
        hostname: "images.unsplash.com", // 允许的域名
        port: "",
        pathname: "/photo-**" // 路径匹配规则
      }
    ]
  }
};

module.exports = nextConfig;
```
- static使用场景
  覆盖掉父级继承的定位（比如父  relative ，子要恢复默认流）
- global.d.ts
  定义全局类型，不用导入，直接使用
```ts
declare interface NavItem {
  id: string;
  title: string;
  url: string;
  onlyMobile?: boolean;
}

```
- usePathname
  usePathname  是 App Router 专用客户端钩子，从  next/navigation  导入，仅在客户端组件可用（文件顶部必须写  'use client' ） 。
  2. 无入参： const pathname = usePathname() ，不接受任何参数；
  3. 返回纯字符串：只提取 URL 路径，自动忽略 search 参数、hash；
  4. 路由切换自动响应更新，搭配  useEffect  可监听路由变化；

{% endfolding %}

{% endfolding %}
