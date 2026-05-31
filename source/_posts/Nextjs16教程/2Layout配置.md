---
title: 2Layout配置
abbrlink: "layout"
swiper: false
swiperImg: ''
img: ''
excerpt: '网站全局配置'
top: true
toc: false
tocOpen: false
onlyTitle: false
comments: false
share: false
copyright: true
donate: false
bgImg: ''
bgImgTransition: translate-fade
bgImgDelay: 180000
categories: Next.js16教程
tags: next.js16
imgTop: true
date: 2026-05-20 20:40:49
swiperDesc: 
---

{% folding Metadata: %}
```ts
import type { Metadata } from "next";
import { siteConfig } from "../siteConfig"; //网站全局配置文件

export const metadata: Metadata = {
	title: {
		default: siteConfig.title,
		template: `%s | ${siteConfig.title}`
	},
	keywords: siteConfig.keywords,
	authors: siteConfig.authors,
	description: siteConfig.desc,
	icons: {
		icon: siteConfig.faviconUrl,
		apple: siteConfig.faviconUrl
	},
	export const viewport = {
	width: "device-width",
	initialScale: 1,
	maximumScale: 1,
	userscalable: false
};
	alternates: {
		canonical: "https://wealipay.top/"
	},
	robots: {
		index: true,
		follow: true,
		googleBot: {
			index: true,
			follow: true
		}
	},
	locale: "zh-CN"
};
```


```ts
//siteConfig.ts
export const siteConfig = {
	title: "wealipay",
	desc: "记录学习Nextjs16历程",
	keywords: ["wealipay", "Next.js16", "Tailwind V4"],
	authors: [{ name: "wealipay" }],
	faviconUrl: "./favicon.ico"
};
```


- 作用：从 Next.js 中导入 Metadata 类型（用于定义页面的 SEO 元数据，如标题、描述等）。
- 注意：import type 表示仅导入类型（TypeScript 特性），不会增加运行时的体积
- 定义网站全局配置文件siteConfig.ts

{% endfolding %}

{% folding 加载马善政字体: %}
{% folding 初始化字体: %}
```ts
import { Ma_Shan_Zheng } from "next/font/google";
  const maShan = Ma_Shan_Zheng({
	weight: ["400"],
	subsets: ["latin"],
	display: "swap",
	variable: "--font-mashan",
	preload: true
});
```

####  subsets: ["latin"]： 
- 只加载拉丁字母字符集（英文、数字），减小字体文件体积。 
- 如果要支持中文，一般要加  ["latin", "chinese"] 。
<hr/>

####  display: "swap"： 
字体加载策略：
- 网页先用默认字体显示
- 等 Ma_Shan_Zheng 下载完自动替换
避免文字长时间空白、闪烁。
<hr/>

####  variable: "--font-mashan"： 
把这个字体绑定到 CSS 变量  --font-mashan 。
后面你在 CSS 里可以直接用：
```css
font-family: var(--font-mashan);
```
或者在tailwind中使用font-mashan

<hr/>

####  preload: true： 
 
开启预加载，浏览器优先提前加载这个字体，页面渲染更快。

{% endfolding %}
	
{% folding 使用字体: %}

```ts
<html lang='zh-CN' className={`${maShan.className}  antialiased`} suppressHydrationWarning>
</html>
```
+ JSX 里 { }：插 JS 变量/代码
+ 反引号`：方便拼接字符串，支持 ${} 插值
+ 把拼接的类名注入到html标签上供全局使用
+ suppressHydrationWarning 是 Next.js / React 原生属性，作用：关闭当前标签的「服务端渲染 和 客户端渲染 内容不一致」的 Hydration 水合报错。

#### h-full（Tailwind）：
 
+ 给 html标签设置高度 100%
作用：
- 让页面高度铺满整个屏幕
- 解决页面高度塌陷、滚动条、底部留白等常见布局问题

<hr/>

#### antialiased：
+ 抗锯齿；平滑边缘

<hr/>

#### suppressHydrationWarning：
+ 前后端内容不一致抑制水合警告

<hr/>

{% folding 为什么必须这样用: %}
##### 性能优化：
+ Next.js 会通过这个className自动：
+ 预加载字体文件
+ 托管字体到你的域名（避免第三方请求）
+ 实施font-display策略
##### SSR支持：
+ 服务端渲染时就能注入正确的字体CSS
+ 避免客户端闪烁（FOUC） 
{% endfolding %}

{% endfolding %}


{% folding 关闭TS检查: %}

```ts
typescript: {
    ignoreBuildErrors: true, // 临时关闭 TS 检查
  },
```
{% endfolding %}

{% endfolding %}

{% folding 2026-05-20完整代码: %}
```tsx
import type { Metadata } from "next";
import { Ma_Shan_Zheng } from "next/font/google";
import "./globals.css";
import { siteConfig } from "../siteConfig";

const maShan = Ma_Shan_Zheng({
	weight: ["400"],
	subsets: ["latin"],
	display: "swap",
	variable: "--font-mashan",
	preload: true
});

export const metadata: Metadata = {
	title: {
		default: siteConfig.title,
		template: `%s | ${siteConfig.title}`
	},
	keywords: siteConfig.keywords,
	authors: siteConfig.authors,
	viewport:
		"width=device-width, initial-scale=1, maximum-scale=1,user-scalable=no",
	description: siteConfig.desc,
	icons: {
		icon: siteConfig.faviconUrl,
		apple: siteConfig.faviconUrl
	},
	alternates: {
		canonical: "https://wealipay.top/"
	},
	robots: {
		index: true,
		follow: true,
		googleBot: {
			index: true,
			follow: true
		}
	},
	locale: "zh-CN"
};

export default function RootLayout({
	children
}: Readonly<{
	children: React.ReactNode;
}>) {
	return (
		<html
			lang='zh-CN'
			className={`${maShan.className} antialiased`}
			suppressHydrationWarning>
			<body>{children}</body>
		</html>
	);
}

```
{% endfolding %}

{% folding useState: %}
+ useState 是React/NextJs 内置钩子函数
+ 作用：定义页面变量、保存数据、实现页面动态更新
+ 普通变量改了页面不会刷新，useState定义的变量修改，页面立刻自动刷新
```
const [变量名, 修改变量的方法] = useState(默认值)

import { useState } from 'react'

export default function Home(){
    // 定义count 默认值0
    const [count,setCount] = useState(0)

    return(
        <div>
            当前数字：{count}
            <button onClick={()=>setCount(count+1)}>加1</button>
        </div>
    )
}

```

#### 常用类型
```ts
//数字
const [num,setNum] = useState(0)
//字符串
const [text,setText] = useState('')
//布尔值 开关
const [open,setOpen] = useState(false)
//数组
const [list,setList] = useState([])

```

{% endfolding %}

{% folding useEffect: %}
+ useEffect 是 React 副作用钩子，用来处理函数组件副作用
+ 副作用：请求接口、定时器、监听事件、修改DOM、本地存储、页面挂载/销毁逻辑，全都放 useEffect
```
useEffect(回调函数, 依赖数组)
```

#### 依赖项为空数组 []
+ 组件只挂载执行一次，页面进来只跑一遍
+ 常用于：首次页面请求接口
```ts
useEffect(()=>{
  console.log("组件挂载，只执行一次")
},[])

```

#### 不写依赖数组（直接省略）
+ 组件每次渲染、数据一变就重复执行
```ts
useEffect(()=>{
  console.log("每次渲染都执行")
})

```

#### 传入指定依赖 [a,b]
+ 只有依赖变量发生变化，才会触发执行
```ts
useEffect(()=>{
  console.log("count变了就执行")
},[count])

```

#### 清除副作用（return 销毁函数）
+ 定时器、监听事件必须清除，防止内存泄漏
```ts
useEffect(()=>{
    // 开启定时器
    let timer = setInterval(()=>{},1000)

    // 组件销毁 / 重新执行前 自动执行
    return ()=>{
        clearInterval(timer) //清除定时器
    }
},[])

```

#### 执行顺序
 
+ 组件渲染页面DOM
+ 再执行 useEffect

#### 核心规则
 
1 useEffect 异步执行，不会阻塞页面渲染

2 依赖数组里面的值，只能放state、props

3 依赖少写会报错、漏监听会数据不更新

4 多个 useEffect 按代码顺序依次执行
{% endfolding %}

{% folding loading.tsx: %}
+ loading.js/loading.tsx 是一个特殊约定文件，用来在路由切换时自动显示“加载中”界面
+ 当访问  /dashboard ，且  page.tsx  里有异步数据请求时，自动先显示 loading，数据回来后替换成页面内容 。
```tsx
// app/blog/loading.tsx
export default function Loading() {
  return (
    <div className="space-y-4 p-4 animate-pulse">
      {/* 标题骨架 */}
      <div className="h-8 w-1/2 bg-gray-200 rounded" />
      {/* 内容骨架列表 */}
      <div className="space-y-3">
        {Array.from({ length: 3 }).map((_, i) => (
          <div key={i} className="h-24 bg-gray-100 rounded" />
        ))}
      </div>
    </div>
  );
}

```
{% endfolding %}

{% folding 配置别名@: %}
```
//tsconfig.json
    "baseUrl":".",
    "paths": {
      "@/*": ["./app/*"]
    }
```
{% endfolding %}

#### Promise:
+ Promise 是JS专门用来处理【异步任务】的对象
+ 用来处理网络请求、文件读取、延时等待等操作
+ async、await 只能搭配Promise使用，不能单独用
+ 自带三种状态：
 - pending 等待中
 - resolve 成功
 - reject 失败
+ async
 - 放在函数前面，把普通函数强制变成Promise函数
 - 不管你函数内部有没有return，返回值永远是Promise对象
+ await
 - 只能等待Promise
 - 作用：暂停代码、原地等待Promise执行完毕，拿到结果再往下走
 - await不能等定时器、不能等普通变量，只等Promise
+ await 必须写在 async 函数里面，外面直接报错
+ async函数里面可以没有await，但await一定要有async
+ await后面必须是Promise对象
+ 所有网络请求axios、fetch，底层全部都是Promise
```ts
// 标准接口模拟模板 完整版
const getData = async () => {
    return new Promise( (resolve,reject) => {
        setTimeout(() => {
            let flag = true
            if(flag){
                resolve("请求成功，返回数据") //成功
            }else{
                reject("请求失败") //失败
            }
        }, 1000);
    });
};

// 使用
async function fn(){
  try{
    let res = await getData()
    console.log(res)
  }catch(err){
    //捕获错误
    console.log(err)
  }
}
fn()

```
