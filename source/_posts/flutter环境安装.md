---
title: flutter环境安装
date: 2018-08-03 19:38:22
tags: ['js', '移动开发', '混合APP']
---

## 今天小试一把Flutter环境搭建

### <!--more-->

前面的安装步骤就不说了，太多的资料，可综合自行百度....

说说我自己遇到的问题：

### 安装步骤 - - -

1. 安装flutter SDK; 

2. flutter create <new Project Name>

3. flutter doctor ( 中间会提示 flutter update-packages 更新依赖包 )

4. flutter run


### 遇到的问题： 

   1. github仓库 ssh key 过期

      `重新替换仓库的ssh key` 

   2. 提示android SDK 未安装 （一定要安装，不然会无法执行）

      `X Unable to locate Android SDK. `

      方法：

        找到SDK路径

        AS -> file -> settings -> System Settings -> Andriod SDK 里面的 `Android SDK Location`

        设置环境变量： 
         
        `ANDROID_HOME` = `上面的Android SDK Location路径`

   3. Andriod SDK 版本错误

      解决方式： 在 `build.gradle` 配置里面设置电脑上已经安装的Andriod SDK版本

                andriod: {
                    ` buildToolsVersion "24.0.1" `
                }

        

