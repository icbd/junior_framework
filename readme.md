# 基本配置

## Hosts
127.0.0.1 junior.mbp

## PHP with php-fpm
PHP 7.0.6

## Server
nginx version: nginx/1.8.1

## nginx vhost conf
/usr/local/etc/nginx/servers/junior_framework.conf
 
 ```
  
 server {
    
    server_name junior.mbp;
    root /Users/cbd/vm/learn/app_framework/junior_framework/root;
    access_log /Users/cbd/vm/learn/app_framework/junior_framework/temp/access.log;
    

    listen 80;
    index index.php;

    location / {
        rewrite ".+" "/index.php" last;
    }

    location ~ \.php$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include        fastcgi_params;
        }
    location ~ .*\.(map|html|woff|ttf|ico|css|js|gif|jpg|jpeg|png|bmp|swf)$ {
        expires 90d;
    }
}


 ```
 
# 概览

## 目录结构
|   目录| 用途|
|---|---|
|   root|   根目录,入口|
|   app|    MVC应用目录|
|   focus|  框架核心组件|
|   doc|    说明文档|
|   temp|   临时文件,log等|
|   unitest|    测试文件|

     
```
.
├── app
│   ├── auto_include
│   │   ├── app.conf.php
│   │   ├── databases
│   │   │   └── redis_conf.php
│   │   ├── helpers
│   │   └── methods
│   │       └── user_methods.php
│   ├── controller
│   │   └── Hello.php
│   ├── model
│   │   └── HelloDao.php
│   └── view
│       └── index.html
├── define.php
├── doc
│   └── introduce.md
├── focus
│   ├── FocusCore.php
│   ├── FocusMethods.php
│   ├── FocusRouter.php
│   └── Twig(下级目录略)
├── readme.md
├── root
│   ├── favicon.ico
│   └── index.php
├── temp
│   └── access.log
└── unitest
    └── phpunit-5.3.4.phar

```