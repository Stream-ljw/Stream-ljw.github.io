---
title: git-note
date: 2023-06-26 16:30:34
tags: 
	- git

categories: git
---

记录一些在使用git过程中常用的操作。  
从操作中理解git思想。  

# 提PR时当前分支落后于主分支

基本上企业应用开发中难以避免的就是当你需要pull-request时发现还需要rebase或者存在confliction。
这种情况是因为多人同时开发，从master主分支上拉取分支A，B，C...总会先有人先完成，进行提PR merge。
后提交的分支自然是落后于master一个或多个提交。  

**解决思路：**
	假设需要提交的的分支是A。 本地将master分支pull下来，然后merge到自己的分支A里。有冲突就解冲突。
	再提交PR。

**操作如下：**
```
$ git pull origin master
$ git checkout A && git pull
$ git merge master
$ git push
```

其实该思路反过来也是可以的，即将分支A merge到本地master，然后git push到远程主分支。
但问题是：
- 直接操作master主分支实际上在商业软件代码管理上是不合理的。肯定需要master的权限； 
- 会跳过代码review，让系统代码存在不稳定性。

另外，如果不想体验，小技巧：需要提交代码的时候再去拉一个分支，然后快速整理提交，保证自己快人一步。哈哈。
（分支维护人少的情况下，确实可行。:smirk:）