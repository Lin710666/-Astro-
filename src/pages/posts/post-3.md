---
title: 我的第三篇博客文章
author: HikiLin
description: "我遇到了一些问题，但是在社区里面提问真的很有帮助！"
image:
    url: "https://docs.astro.build/assets/rays.webp"
    alt: "The Astro logo on a dark background with rainbow rays."
pubDate: 2026-8-31
tags: ["astro", "learning in public", "setbacks", "community"]
---

# 搭建过程中学到的新东西
### 动态变量
`{var}`
```astro
    ---
    const pageTitle = "关于我" // js/ts变量
    ---
    <h1>{pageTitle}</h1>
```

### JavaScript数组的map方法
`arr.map(f)` 基本等同于 Python 的列表推导式 `[f(x) for x in arr]`
“不改变原数组，对每个元素执行指定操作，并组成一个新数组返回”

### 条件渲染元素
```astro
    ---
    const happy = true;
    ---
    {happy && <p>我很乐意学习Astro!</p>}
    {happy === true ? <p>我很高兴！</p> : <p>我不高兴! </p>}
```