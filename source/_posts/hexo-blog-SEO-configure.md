---
title: hexo blog SEO configure
date: 2021-05-09 16:50:26
tags: 
	- hexo
	- next
	- SEO
	- next-plugin
categories: tool
---



# SEO

SEO(Search Engine Optimization) 针对搜索引擎的优化。  
意义是让我们的博客能被通过搜索引擎查询相关问题的人更容易看到浏览。(换句话说，没有这方面需求的人可以忽略)  

我没有相关的需求，玩的就是一个收藏。毕竟写博客主要目的是技术积累，以及和朋友的谈资  : )  
至于博客里面甚至留了bitcoin的打赏二维码，相信我，那只是为了好玩。 : )  

出于对技术的热爱角度，也来学习一下，万一以后能用到呢。所以没有和hexo博客搭建写在一起，而是单独另起一篇细细的看下，有用的记录下。  
如果你有缘看到了，那就一起学习下有哪些方式吧。

## 添加搜索引擎的认证

## sitemap

## 优化目录结构

修改站点配置文件`_config.yml--> permalink`
```
permalink: :year:month:day/:title/
```
or
```
permalink: :title.html
```
从而改变博客的目录结构
## 代码压缩
网页的代码存在大量空白符，压缩代码可以提高网站被访问速度。

安装插件： `npm install hexo-neat --save`  

修改*站点配置文件*：
```
# 开启压缩
neat_enable: true
neat_html:
  enable: true
  exclude:
neat_css:
  enable: true
  exclude:
    - '**/*.min.css'
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/index.js'
```

# **reference**

- 知乎： [hexo博客高级优化](https://zhuanlan.zhihu.com/p/344927945)  
- NexT： [SEO|NexT](https://theme-next.js.org/docs/theme-settings/seo)


{% cq %}永远拥抱开放，拥抱自由，where we stands as who we are{% endcq %}