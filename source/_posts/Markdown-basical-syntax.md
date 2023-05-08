---
title: Markdown basical syntax
date: 2023-05-06 10:12:19
tags: markdown
categories: tool
---

**<center> 中国人很擅长抽象， 化繁为简是好事，但总会丢了灵魂 </center>**
说到底，还是把握不住精髓。  
都是知道了该怎么做就开始抽象。而不是知道了为什么这么做再开始抽象。浮躁。 


# Markdown

## 换行、段落
> 换行：两个空格
> 段落： 一行空行

## 粗体、斜体
``` 
 ** text ** 
  * text * 
```
> **note** : *注意markdown中的符号后面的空格*

## 列表
```
1. xxx
2. xxx
3. xxx
```

## 链接、图片

```
链接[source](link "description")
图片 ![](path "title")
```

## 转义字符 '\\'

## 表格
```
---|---|---
---|---|---
```

### 代码

> 行内插入代码 ： \` code \`
> 多行代码：
> - \`\`\` code  \`\`\`
> - 四个空格或者tab缩进

代码进行语法高亮
>\`\`\` python  
> python code
>\`\`\`  

即在\`\`\`后标明 code的语言  

## Emoji


` :joy: ` 

示例： 这是开心的表情 :joy:    (这里不知道为啥不能显示)

更多表情简码列表，[点击这里](https://gist.github.com/rxaviers/7360908)

## 改变字体颜色

markdown不支持改变字体颜色，但是支持html语法  
通过`<font color=green size=7 face="黑体"> font </font>`