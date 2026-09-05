---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Neural Network'
pubDate: 2026-9-5
description: ' 跟做LLMs from Scratch过程中的笔记 '
author: 'HikiLin'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ["astro"]
---

## Python的`zip()`方法
```python
weights = [[1, 10, 5, 6],
           [2, 3, 4, 5],
           [3, 2, 1, 4]]

biases = [1.6, 2.3, 0.7]

neuron_pair = zip(weights, biases)
for _ in neuron_pair:
    print(_)
```

打印得到：
```
([1, 10, 5, 6], 1.6)
([2, 3, 4, 5], 2.3)
([3, 2, 1, 4], 0.7)
```

也就是说
```python
数组1 = [元素11, 元素12, 元素13, 元素14]
数组2 = [元素21, 元素22, 元素23, 元素24]

pairs = zip(数组1,数组2)
//则paris = [(元素11,元素21), (元素12,元素22),(元素13,元素23),(元素14,元素24)]
```