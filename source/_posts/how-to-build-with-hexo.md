---
title: how to build with hexo
date: 2021-05-05 17:48:39
tags: hexo
categories: tool
---



采用hexo这种静态页面的博客是无奈之举，因为云服务器+jupyter方式确实方便，最终云服务器到期了。
看了教程也是头疼，做下来感觉就是”难不会，会不难“。
简单来说就是hexo+ github pages，hexo需要用到nodejs+npm，github pages需要用到git。
先无脑跟着教程做一遍，再去体会
# hexo + github pages

## hexo
博客框架

## nodejs + npm + git
nodejs： [网址下载](https://nodejs.org/en)
> note ： 从官网安装的版本自带npm，无需额外安装。但是通过shell apt安装则需要单独安装nodejs+npm

```shell
sudo apt install nodejs
sudo apt install npm
```

## git 
git : `apt install git` 
安装好git后，还需要设置：
```
git config --global user.name xxx
git config --global user.email xxx@gmail.com
```
因为我们需要把生成的博客页面上传到github仓库里面。还需要获取仓库的访问权限，也就是将本地密钥放到ssh key里面  
生成密钥（rsa）： 
``` ssh-keygen -t rsa -C email@gmail.com ```
> windows： C:/user/[username]/.ssh/id_rsa.pub
> linux : ~/.ssh/id_rsa.pub 

## github repo
创建github 新的 repo，repo的名字一定是 ***[your_name].github.io***
> note： 名字不是上述形式的话，会出现本地渲染正常，但是上传到github pages里面后打开没有任何样式。

> note: 创建好之后，我们不必根据github的提示在本地初始化一个github仓库。后面设置好之后hexo-deployer-git工具会自动提交到这个仓库。  

## npm + hexo 
安装hexo ， 以下是常用的hexo命令：
```
hexo clean  
hexo generate # hexo g  
hexo server   # hexo s  
hexo deploy   # hexo d  将本地的hexo generate之后文件部署到github仓库，一般是通过hexo-deployer-git工具自动部署
```

这里分为两种情况：
### 新创建的仓库
```shell
npm install hexo-cli -g	  #安装hexo
hexo init your_blog_name  #hexo 新建一个blog项目框架
cd your_blog_name         # 进入blog项目文件夹下
npm install               # 初始化安装必要的文件
hexo server               # 也可以写为hexo s , 意思是开启本地一个服务，可以直接访问 localhost:4000 查看初始化好的hexo页面。
```

### 已经存在github上面的hexo仓库
```shell
npm install hexo-cli -g		  #安装hexo
git clone your_repo_addr.git
cd your_repo_addr
npm install
``` 
## _config.yml
在Hexo中有两份主要的配置文件，其名称都是 *_config.yml*。其中，一份位于 Hexo 根目录下，主要包含 Hexo本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。  前者称为 **站点配置文件** ， 后者称为 **主题配置文件** 。

- 站点配置文件
下面是站点配置文件需要修改的地方：
```
title ： 网页的名称
url ： https://your_name.github.io/your_name.github.io  #github repo的setting --> pages 
root: /  #root在url下面，没有可以加上

theme：file_name_in_themes  # theme名字就是 themes目录下，主题文件夹名称。文件夹名称可以自己更改

deploy:
  type: git
  repo: https://github.com/your_name/your_name.github.io
  branch: gh-pages
```
deploy配置主要是用作hexo d，也就是 hexo-deployer-git插件会用到的地方。
主要是用作指定github创建的仓库位置及上传到哪个分支。这里分支名为gh-pages，也可以自己指定。

- 主题配置文件
主题配置文件大部分不需要配置，对页面功能有要求的可以自行了解。

安装hexo-deployer-git： `npm install hexo-deployer-git --save`  
当我们配置好之后就可以执行`hexo clean && hexo g -d`进行部署到github，然后通过url查看效果
当然部署之前可以本地localhost:4000查看：
```
hexo clean
hexo g && hexo s
```

## 编写markdown
hexo配置好了，默认主题就是landscape，不考虑换的话，就应该做该做的写博客了。
1. 创建新的文章： ` hexo new "post title" `

2. source\_posts 目录下的xxx.md就是刚刚创建的博客内容，格式是markdown

## push
我个人建议最好做一份本地文件的存档，真正做到“云博客”，换个场景之后，可以把文件从分支上clone下来，配置好本地环境即可接着编辑博客。

我选择上传文件到main分支，main分支远程仓库暂时没有
```shell
git init       #初始化本地git仓库
hexo clean     # 清楚多余的生成文件，保留原始文件
git checkout -b main  #创建并切换到本地新分支
git add * 				 #将改动提交到本地新分支
git commit -m "upload hexo files"
git remote add origin url       #关联远程分支
git push -u origin main
```

# 更换合适的主题

theme 主题一直是hexo的亮点。找到适合自己的主题，体面，酷炫，一直是bloger最浪费时间的工作。
主题才是真的需要熟悉的地方。我觉得这才是hexo的门槛所在。  
我自从搭建了hexo以来，感觉一直在花费时间换各种各样的主题，尝试每个主题不同的功能。  

在没找到好看的主题之前，这里就保存一下自己换过的主题用了哪些功能吧
因为LiveForCode 简单试用过之后就放弃了，主要是因为感觉还是要注重内容本身，不能搞的花里胡哨（虽然好的页面也可以令人心情愉悦，提升阅读体验）

所以还是从万人敬仰的NexT开始记录吧。

## NexT
- 修改字体大小到0.9：我觉得默认的hexo博客标题字体都偏大，看着很不舒服.0.9我觉得正好。故调整了global字段
```
font:
  #enable: false
  enable: true   #改为true应用修改
...
  global:
    external: true
    family: Lato
    size: 0.9  # 改变值
```
- `scheme` ：　
Gemini， NexT还提供四种页面布局可选，比较中意的是第四种，Gemini。
或许后面页面功能玩的熟练了，搭配其他的也可以。
- `menu`
添加了 Home ，tags， Categories ， Archives
其余的about，schedule， sitemap， comonweal，还没定义。就不放上去了。但是tags 和categories还是不能用。

- `social link` : github + email
- `categories`和`tag`，/tags/ & /categories/ 里面的index.md内 type 字段值要和 _config.yml设置的保持一致。 
- 首页内容折叠`excerpt`： hexo7.8版本以上支持自动截图摘要功能，需要以下安装` npm install hexo-excerpt --save `
> `--save`的作用主要是将安装的插件记录到 package-lock.json & package.json中
> 在新的仓库中执行npm install 其实就是读取或生成package-lock.json& package.json 安装仓库的原有的环境里面的插件。
然后更改站点配置：
```
excerpt:
  depth: 10
  excerpt_excludes: []
  more_excludes: []
  hideWholePostExcerpts: true
 ```

- `local_search` : blog内容搜索，感觉这个功能主要给博客主自己用 安装：`npm install hexo-generator-searchdb --save`  
然后更改站点配置：
```
search:
  path: search.xml
  field: post
  content: true
  format: html
```
在主题配置中启用：
```
local_search:
  enable: true
```

- `tag-plugins` : 意思是通过给文本、图片等打上一些标签从而实现一些特殊的效果  
For more info: [Tag Plugins introduc](https://theme-next.js.org/docs/tag-plugins/)
注意： 这不属于markdown的语法，而是hexo在渲染时候的功能

- `emoji`:  通过shortcode使用表情， hexo默认的markdown渲染器hexo-render-marked不支持渲染emoji  
可以通过更改支持的渲染器来解决。但是我不想大动干戈，本着emoji能用就行的心态，装个插件:   ` npm install hexo-filter-github-emojis --save `
修改站点配置文件：
```
githubEmojis:
  enable: true
  className: github-emoji
  inject: true
  styles:
  customEmojis:
```
- `flowchart/mermaid` ： 在next主题配置文件中找到mermaid 字段，enable 改为true
尽量使用mermaid ，似乎flowchart语法，在手机上浏览网页会让页面错误。

- 插入图片： 站点配置文件中post_assert_floder改为true， 这样hexo new post时就会创建对应的文件夹。
注意： 插入图片时应该使用 post_floder_name/image_name.type 路径来引用图片。 插入图片不需要安装其他任何插件，不显示就是路径设置错误  

- 文章置顶：:point_right: [reference](https://github.com/im0o/hexo-generator-index-custom/blob/master/README_zh.md)
```
npm uninstall hexo-generator-index
npm install hexo-generator-index-custom --save
```
站点配置文件中的index_generator部分不需要改，完全兼容！
在文章开头添加 sticky 或 top 参数， 其值可以是 true（置顶） 或者 数字，数据越大，越排在前面。
hide参数可以隐藏文章
```
---
title: Ideas
date: 2020-05-06 09:59:10
tags: ideas
categories: daily_note
top: true
---
```
----------
(end)


# **reference**
在使用NexT中参考了很多前辈的配置过程，在此感谢！
hexo官方文档： [主要是选择主题](https://hexo.io/themes/)
NexT官方参考文档： [Getting Started](https://theme-next.js.org/docs/getting-started/)  
比较全的主题功能配置： [点此前往查看](https://www.meijindong.com/posts/3688165485.html)
hexo提供的plugins： [插件一览，要啥找啥](https://hexo.io/plugins/)


{% cq %}集中力量办大事无法调动积极性，只会滋生投机份子{% endcq %}