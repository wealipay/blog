---
date: 2025-08-16 08:09 
abbrlink: 'any'
categories: 开发记录
tags: 辅助文章
title: 3解决any类型错误的问题
---
{% folding, eslint.config.mjs： %}
在文件中增加rules规则
```ts
const eslintConfig = [
  ...compat.extends("next/core-web-vitals", "next/typescript"),
  rules: {
      'react/no-unescaped-entities': 'off',
      '@next/next/no-page-custom-font': 'off',
    },
];
```
{% endfolding %}
<hr>
