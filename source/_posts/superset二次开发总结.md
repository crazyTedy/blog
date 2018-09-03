---
title: superset二次开发总结
date: 2018-06-28 20:31:20
tags: ['js', 'superset', 'python', 'flask']
---
## superset二次开发总结：未完待续....

### <!--more-->

开发心得：
    superset是基于flask开发的一套可视化模板，好处：1.快速生成图表，2.集成了多种数据库环境，相对于复杂的图表展示来说可谓是利器,刚开始接到这个superset的时候一脸懵逼，都**的python文件？喂，我不会啊！抱怨可以有，但毛用没有，做还是得做的。哭.... superset中有很多文件相互调用，缕清相互的关系是需要费相当的精力和时间。我太菜了，我硬是看了三四天才在第五天完全看明白。哇，真的菜~~~~ 我总结一下我踩的坑 ，希望可以给你们一些帮助


掘金： <https://juejin.im/post/5b399a4ee51d455898532b65>
    

##  python服务器启动

    路径:
        cd F:\Anaconda\Lib\site-packages\superset\bin>
    命令：
        python superset runserver -d 

###  修改文案 汉化

    执行路径： 
        /superset/transitions
    作用： 
        .po文件转.json文件
    命令：
        pybabel compile -d translations


### 本地静态目录
    
    /static
        ---src                          //业务组件
        ---stylesheets                  //样式文件（需要注意的两个文件）
            --less
                --cosmo
                    --bootswatch.less   // 修改样式的地方
            --superset.less             //  修改全局样式的地方


    注意： 本地安装开发环境的时候，react版本最好不要升级,坑也挺多,就按照他的版本来.
           如果你非要升级的话，有几点需要提醒你：

            1. prop-types 会提示相关报错, 问题在于react版本。@15和@16版本中prop-types的差异,升级的react版本到@16.**的注意一下

            2.会提示Cannot find module 'react/lib/*****'等未知模块,想要好办法？二话不说丢给你一个网站  https://www.jianshu.com/p/43b7db635f8c 按步骤运行！

            3.想找react-router? 找不到的，他压根就不是spa, 虽然在react写的 （此时劝诫自己要压住怒火）提示： superset/views/core.py   // 模块注册和页面跳转

###  模板引擎

    superset/templates

    flash_appbuilder/templates

    注：如果这里模板调用找不到的话 在和superset同级的flash_appbuilder/templates里面找，
        这两个文件夹是可以相互调用的.（千万注意，这是一个坑~坑死我了~~~） 
        两个模板有很多不起作用的模板，不知道为什么要留在里面，增加了很多不必要的难度

###  路由

    /views
        ---core.py  
            class    // 创建视图对象，
            appbuilder.add_view(   // 注册路由文件    
                        视图对象，
                        mtrid, 
                        msgstr, 
                        图标，...  
                    )  
            appbuilder.add_link(    //添加子路由
                        mtrid       //字符串id 
                        label       //名称
                        href        // 跳转路径
                        category    // 属于哪个类目
                        category_label  // 类目名称
            )
