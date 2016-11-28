---
title: react-router笔记
date: 2015/10/20 11:54:00
tags: react-router
categories: 随笔
---

# react-router笔记

### 路径语法
路由路径是匹配一个（或一部分）URL 的 [一个字符串模式](/docs/Glossary.md#routepattern)。大部分的路由路径都可以直接按照字面量理解，除了以下几个特殊的符号：

  - `:paramName` – 匹配一段位于 `/`、`?` 或 `#` 之后的 URL。 命中的部分将被作为一个[参数](/docs/Glossary.md#params) 
  - `()` – 在它内部的内容被认为是可选的
  - `*` – 匹配任意字符（非贪婪的）直到命中下一个字符或者整个 URL 的末尾，并创建一个 `splat` [参数](/docs/Glossary.md#params)

```js
<Route path="/hello/:name">         // 匹配 /hello/michael 和 /hello/ryan
<Route path="/hello(/:name)">       // 匹配 /hello, /hello/michael 和 /hello/ryan
<Route path="/files/*.*">           // 匹配 /files/hello.jpg 和 /files/path/to/hello.jpg
```

如果一个路由使用了相对`路径`，那么完整的路径将由它的所有祖先节点的`路径`和自身指定的相对`路径`拼接而成。[使用绝对`路径`](RouteConfiguration.md#decoupling-the-ui-from-the-url)可以使路由匹配行为忽略嵌套关系。

### 优先级
最后，路由算法会根据定义的顺序自顶向下匹配路由。因此，当你拥有两个兄弟路由节点配置时，你必须确认前一个路由不会匹配后一个路由中的`路径`。例如，千万**不要**这么做：

```js
<Route path="/comments" ... />
<Redirect from="/comments" ... />
```



