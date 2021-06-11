## 说明
- nginx：1.21.0
- nginx-sticky-module-ng: 1.2.6

本镜像时区、仓库都已进行本地化优化处理。

## 配置说明
- 主配置文件 `/etc/nginx/nginx.conf`
- 服务全局配置目录`/etc/nginx/conf.d/`
- 应用配置目录`/etc/nginx/web.d/`

镜像中默认配置了一个web站点，配置文件为`/etc/nginx/web.d/default.conf`，可通过配置覆盖程自己的应用。

## 启动示例
### 1. 默认配置启用
`sudo docker run -tid --name nginx -p 8080:80 ottc/nginx:1.21.0`
### 2. 自定义配置应用
`docker run -tid --name nginx -v /home/parallels/Desktop/demo.conf:/etc/nginx/web.d/default.conf -p 8080:80 ottc/nginx:1.21.0
`

## 配置示例
### 反向代理配置示例
```
upstream demo {
    server 192.168.8.132:7070;
    server 192.168.8.132:7010;
    sticky name=srv_id domain=10.211.55.4 expires=1h path=/ hash=md5 httponly;
}

server {
    listen       80 default_server;
    listen       [::]:80;
    location /api/ {
        proxy_pass http://demo/;
    }
}
```
注意sticky中domain的配置，根据访问入口来决定domain具体参数值，防止session保持没有生效。


## 参考
- https://github.com/metowolf/docker-nginx
- https://bitbucket.org/nginx-goodies/nginx-sticky-module-ng/
