---
title: Markdown 语法
description: Markdown 语法
categories:
 - 教程
tags: Markdown
---

> Markdown语法

<!-- more -->

## 标题
使用 # 号可表示 1-6 级标题，一级标题对应一个 # 号，二级标题对应两个 # 号，以此类推。

\# 一级标题  
\#\# 二级标题  
\#\#\# 三级标题  
\#\#\#\# 四级标题  
\#\#\#\#\# 五级标题  
\#\#\#\#\#\# 六级标题  

显示效果如下：
# 一级标题  
## 二级标题  
### 三级标题  
#### 四级标题  
##### 五级标题  
###### 六级标题  

## 代码
如果是段落上的一个函数或片段的代码可以用反引号把它包起来（\`），例如：  
\`printf()\` 函数，显示效果如右`printf()` 

你也可以用 \`\`\` 包裹一段代码，并指定一种语言（也可以不指定）：  


\`\`\`sh  
sudo apt update  
sudo apt install shadowsocks-libev  
\`\`\`

显示效果如下：

```sh
sudo apt update
sudo apt install shadowsocks-libev
```