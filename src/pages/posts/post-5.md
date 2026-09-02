---
layout: ../../layouts/MarkdownPostLayout.astro
title: '动态网页搭建过程'
pubDate: 2026-9-3
description: ' 详细的整理一下动态网页的搭建 '
author: 'HikiLin'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
---

# 动态网页搭建过程
我们先记住三个角色的分工：

1. 动态路由：相当于一个“页面模具”。它决定了所有动态页面的长相（HTML结构、CSS样式）。

2. `getStaticPaths`：相当于“生产计划员”。它负责在盖房子（构建项目）之前，列出一份清单：“我们要盖哪些页面？每个页面的代号（params）是什么？每个页面需要什么专属材料（props）？”

3. Astro 对象：相当于“传送带”。当计划员开始生产时，传送带会把当前这个页面专属的“代号”和“材料”送到模具里。
   
## Step1动态路由
在`src/pages`目录下，创建一个带方括号的文件，如：`[MyRoute].astro`<br />
`[MyRoute]`就相当于一个占位符

## Step2编写`getStaticPaths`函数
```JavaScript
// 模拟数据源(通常来自数据库或CMS)
const allPosts = [
    { id: 1, title: 'Page1', content: "内容1" },
    { id: 2, title: 'Page2', content: "内容2" },
];

// 编写getStaticPaths函数!!!
export function getStaticPaths(){
    return allPosts.map((post) =>{return {params: {MyRoute: post.title}, props: {post: post}}})
}
```
函数会返回一个形如👇的数组：
```JavaScript
[{params: {MyRoute: "Page1"}, props: {post: { id: 1, title: 'Page1', content: "内容1" }}},
 {params: {MyRoute: "Page2"}, props: {post: { id: 2, title: 'Page2', content: "内容2" }}},
]
```
其中的每一项都是一个静态页面的"图纸"

## Step3`Astro`对象
当 Astro 编译器循环遍历数组的每一项时，会把当前项的 params 和 props 挂在 Astro 对象上。
在frontmatter中打印`Astro.params`和`Astro.props`即可看到它们。