---
date: 2025-08-19 23:13
abbrlink: 'gradienttext'
categories: 开发记录
tags: 辅助文章
title: 6GradientText组件使用
excerpt: GradientText组件使用
---

{% folding, GradientText组件定义 %}
```ts
import React, { ReactNode } from 'react';

interface GradientTextProps {
    children: ReactNode;
    className?: string;
    colors?: string[];
    animationSpeed?: number;
    showBorder?: boolean;
}

export default function GradientText({
    children,
    className = "",
    colors = ["#ffaa40", "#9c40ff", "#ffaa40"],
    animationSpeed = 8,
    showBorder = false,
}: GradientTextProps) {
    const gradientStyle = {
        backgroundImage: `linear-gradient(to right, ${colors.join(", ")})`,
        animationDuration: `${animationSpeed}s`,
    };

    return (
        <div
            className={`relative mx-auto flex max-w-fit flex-row items-center justify-center rounded-[1.25rem] font-medium backdrop-blur transition-shadow duration-500 overflow-hidden cursor-pointer ${className}`}
        >
            {showBorder && (
                <div
                    className="absolute inset-0 bg-cover z-0 pointer-events-none animate-gradient"
                    style={{
                        ...gradientStyle,
                        backgroundSize: "300% 100%",
                    }}
                >
                    <div
                        className="absolute inset-0 bg-black rounded-[1.25rem] z-[-1]"
                        style={{
                            width: "calc(100% - 2px)",
                            height: "calc(100% - 2px)",
                            left: "50%",
                            top: "50%",
                            transform: "translate(-50%, -50%)",
                        }}
                    ></div>
                </div>
            )}
            <div
                className="inline-block relative z-2 text-transparent bg-cover animate-gradient"
                style={{
                    ...gradientStyle,
                    backgroundClip: "text",
                    WebkitBackgroundClip: "text",
                    backgroundSize: "300% 100%",
                }}
            >
                {children}
            </div>
        </div>
    );
}

```
{% endfolding %}
<hr>
{% folding, GradientText组件的使用： %}
```ts
<GradientText
  colors={["red", "#4079ff", "white", "#4079ff", "red"]}
  animationSpeed={3}
  showBorder={false}
  className="absolute font-bold text-center animate-gradient  top-10 transform translate-x-1/2 text-2xl"
  >
    在支付宝首页搜索
    <br />
    <br />
    853688884
    <br />
    <br />
    即可领红包
</GradientText>
```
{% endfolding %}
<hr>
{% folding, @keyframe： %}
```ts
/*GradientText*/
@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
.animate-gradient {
  animation: gradient 3s ease infinite; /* 应用动画 */
}
```
{% endfolding %}
<hr>