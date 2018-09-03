---
title: 项目中必会的git操作
date: 2018-09-03 11:38:23
tags: ['git', '团队协作']
---

不管是大项目还是小项目，项目托管已经是必要的掌握技能。现在总结一下平时遇到的那些git命令

### <!--more-->


## 介绍:

    1. 初始化仓库

        个人仓库
        
        fork的仓库


    2. 代码更新、提交、合并

        个人代码更新

        团队代码合并，更新， 提交
    

    3. 仓库分支（branch）的使用

        创建分支

        切换分支

        删除分支

        合并分支


# 初始化仓库

  一般我们创建一个项目的时候，首先要在自己的gitLab或者github上面 New repositories 一个新的仓库名字 Name

    # 个人仓库（最高权限）

        初始化操作三连 唰~唰~唰~

        // 创建一个.git 配置文件夹

            git init 

        // 添加仓库地址信息，你就理解成登录要设置账号密码

            git remote add origin '仓库地址.git'

        // 获取本地更新并上传

            git status 
            
            git add .
            
            git commit -m '提交信息'
            
            git push origin master


    # fork的仓库

        点击`fork`复制别人的项目到自己的仓库，此时你的项目属于别人项目的`分支`


# 代码更新、提交、合并

  ### 个人代码更新

        git pull origin '分支名'

### 团队代码合并、 更新

#### 假设：

        团队主仓库主分支 `upstream`

        个人仓库主分支 `master`

#### 环境： 

        此时你本地仓库的`master`分支由`upstream`仓库fork出来的。

#### 注册主仓库地址：    需要注册`upstream`的仓库地址到.git/config中，和注册个人仓库操作类似。

    git remote add `upstream` 分支地址.git 


#### .git/config配置

                    .git/config配置：

                        [core]
                            repositoryformatversion = 0
                            filemode = false
                            bare = false
                            logallrefupdates = true
                            symlinks = false
                            ignorecase = true

                        [remote "origin"]
                            url = '本地仓库地址'
                            fetch = +refs/heads/*:refs/remotes/origin/*

                        [branch "master"]
                            remote = origin
                            merge = refs/heads/master
                            
                        [remote "upstream"]
                            url = '团队仓库地址'
                            fetch = +refs/heads/*:refs/remotes/upstream/*

#### 获取`upstream`更新

    1. 先在本地仓库创建一个分支，并且换到创建的分支上. 原因是先获取远程更新，然后合并到`master`上
    
        git branch dev-upstream

        git checkout dev-upstream

    2. 获取远程`upstream`更新, 此时的分支正在 `dev-upstream`上，：

        git remote update `upstream`

#### 合并分支

    3. 合并 `dev-upstream` 更新到 `master` 上 , 此时的 `dev-upstream` 已经获取 `upstream` 更新的内容，：

        git merge dev-upstream/master  或者  git rebase dev-upstream/master
    
#### 提交到主仓库

    4. 切换到主分支，提交更新至本地仓库

        git branch master

        git status

        git add .

        git commit -m '合并分支'

        git push origin master

#### Merge给管理员

    5. New Merger 提交到项目管理员


# 仓库分支（branch）的使用

    创建分支

        git branch '分支名'

    切换分支

        git checkout '分支名'

    删除分支

        git branch -d '分支名'

    合并分支

        git merge(rebase) 分支/目标分支

 ## 完结 ##

这些基本涵盖了常规的git操作， 和团队合作方式的操作。

当然还有一些仓库的权限操作，生成ssh key 和 更新 ssh的方式。网上有很多就不单独介绍。

我发现写博客可以让自己的思路更清晰，激发自己的学习积极性。。





    


    

    


                        
            




        




        

        

        

