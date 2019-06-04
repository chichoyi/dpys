## 背景

- 现在都9102年了，搞事必须docker化
- 本包是以python:3.5为镜像，集成了scrapy框架，其他内容看后续需要再继续加
- 爬虫讲究的是策略，比如IP代理，抓包前加载渲染等，欢迎讨论

## 前言
  使用前，默认你已经安装了 [docker](https://www.jianshu.com/search?q=docker%E5%AE%89%E8%A3%85&page=1&type=note) 和 [docker-compose](https://www.jianshu.com/p/f323aa0416da)

## 阿里云镜像加速器
 
 [阿里云镜像加速器](https://dev.aliyun.com)
 
 进入之后登录，然后进到 [ 管理中心 ]，找到镜像加速器，里面有教你怎么配置本地的加速器，不再赘述
 
  ##  克隆此包
   
      git clone  https://github.com/chichoyi/dpys.git
      
      
### 修改docker-compose.yml

~~~
services:
     python:
       build: ./python
       container_name: python
       hostname: python
       volumes:
         - ./items:/www  # ./items 可以切换为你代码目录
       tty: true
       networks:
         - dpys
   
   
   networks:
     dpys:
       driver: bridge

~~~

 ## 修改完之后执行命令
  
    cd dpys
    
    docker-compose build
    
- 第一次执行需要花点时间下载镜像


## 更新日志

- scrapy框架安装

## 命令参考

    # 你自己修改了docker-compose文件或Dockerfile文件的话，请执行
    docker-compose build
    
    # 开启 dnmp 服务
    docker-compose up -d
    
    # 重启 dnmp 服务
    docker-compose restart
    
    # 关闭 dnmp 服务
    docker-compose down
    
    # 生成框架
    docker exec -w /www python scrapy startproject CrawlImages
    
 ## contact me
 
 email: chichoyi@163.com
 