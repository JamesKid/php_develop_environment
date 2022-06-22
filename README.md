## PHP 开发环境 docker 一键生成脚手架
## Author: 
    Jameskid
    VimKid

### 首次使用


### 环境版本
    php:  8.1.3
    mysql: 5.6 
    swoole: 4.8.8
    nodejs:  12.22.5 
    redis: 5.0.8
    docker-desktop: 4.8.2

注意事项： windows, docker-desktop 软件 需要4.8.2 以上，如果版本较低请自行到官网下载更新，更新安装覆盖即可（不用卸载原来，
以免原有容器丢失 ） 。 

### 修改docker 配置
在docker desktop的setting中的 Docker Engine中配置
```shell
"features": {
    "buildkit": false
}
```
### 

### 拉取项目
```
# 根目录执行
# 命令行 进入app 目录下载新项目
cd app 


# 拉取需要部署的项目代码 
git clone git@gitee.com:xianrenhui/new-crm.git ./app/easyswoole-crm

```
### 启动命令
在 php_development_environment  根目录进行以下命令启动并安装环境容器
```
docker-compose -f docker-compose-dev.yml up -d
```
### 停止
```
docker-compose -f docker-compose-dev.yml down
```
### 重新构建命令
如有修改config 下的  Dockerfile 文件， 需要 重新构建则使用以下命令 
```
docker-compose -f docker-compose-dev.yml build
```
###

### 
访问`127.0.0.1:1215` 或 访问 ` ，如果能出现正常首页，则表示部署成功

### 本地数据库连接信息
mysql
```
host: localhost  或 127.0.0.1
port: 3306 
user : root
password : 123456
```
redis
```
host: localhost  或 127.0.0.1
port: 3680
user : 无
password : 无
```
### 教程


### 常见问题
#### 1. 如何添加 php 扩展或容器软件或配置
在 config/php-swoole/Dockerfile 文件下，添加相应的官方包，然后 执行
```
docker-compose -f docker-compose-dev.yml build
docker-compose -f docker-compose-dev.yml up -d
```
命令重新构建并重启容器即可

#### 2.

