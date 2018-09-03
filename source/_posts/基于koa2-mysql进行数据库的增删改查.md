---
title: '基于koa2+mysql进行数据库的增删改查'
date: 2018-09-01 17:53:17
tags: ['koa2', 'mysql', '服务端']
---

学了一段时间的数据库操作，做一个demo练手，网上似乎也找不到这么基础的demo了。

### <!--more-->

 ui界面： jquery

 server:  koa2 + koa-router + koa-bodyparse + mysql

 主要功能： 对数据进行 增 、删、改、查。

## Action (服务端篇)

    ## 引入必要模块

        const Koa = require('koa2'); 
        const router = require('koa-router')(); //用于设计接口
        var mysql = require('mysql'); 
        var bodyParser = require('koa-bodyparser'); // 对客户端数据进行解析
        const app = new Koa(); // 实例化
        app.use(bodyParser()); //使用中间件

    ## 连接数据库

        var connection = mysql.createConnection({
            host: 'localhost',
            user: 'root', // sql账号
            password: '123456', // sql密码
            database: 'test'
        });
    
    ## 接口设计

        router.get('/', async (ctx, next) => { ctx.response.body = '<h1>欢迎查询</h1>' })
        router.get('/get_user_list', async (ctx, next) => {...})
        router.put('/update_user', async (ctx, next) => {...})
        router.delete('/delete_user', async (ctx, next) => {...})
        router.post('/add_user', async (ctx, next) => {...})
    
    ## 静态托管一个界面

        app.use(require('koa-static')(__dirname));
    
    ## 使用路由中间件

        app.use(router.routes())
    
    ## 启动服务
        app.listen(3000, () => {
            console.log('server is running at http://localhost:3000')
        })


app.js： https://github.com/crazyTedy/koa2-mysql/blob/master/app.js

   ### 服务端脚本-踩坑之123事

    1. post请求参数的获取和序列化

        // 对客户端数据进行【解析】 正确获取post参数

        var bodyParser = require('koa-bodyparser'); 

        // 获取参数 

        ctx.request.body
        

## Action (ajax篇)

   1.简单的ajax请求 就不赘述了
   2.实现了增删改查

index.html： https://github.com/crazyTedy/koa2-mysql/blob/master/index.html


### 心历路程和收获

   1.加深理解了后端查询数据库和设计接口的流程
   2.学习mysql的阶段性总结。
    
### 认知和不足：

   1.数据库查询熟练度，和http知识的补充。
   2.寻找大一点的数据库，写一些测试性脚本，深入了解后端知识。
   3.数据库安全方面的知识。