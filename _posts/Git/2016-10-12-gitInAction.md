---
layout: post
title: "Git实用指南"
categories: git
excerpt: 
tags: git
---

* content
{:toc}

git基本使用的memo和注意点



### 基本问题

- 如何使用git？如何优雅地使用git？

### Git的基本使用

#### 基本配置 : git config

- 配置用户名和基本信息

```
git config --global user.name "name"
git config --global user.email email@email.com
```

- 配置命令别名

	可以使用 git st 来指代 git status

```
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.co checkout 
git config --global alias.br branch
```

- 删除对应的key配置

```
git config --unset --global KEY

git config --unset --global alias.st
```
	
#### 创建初始化版本库 : git init

- 创建git仓库，可以直接创建初始化，会自动建好文件夹

```
git init gitdemo
```

#### 创建分支branch

- 

