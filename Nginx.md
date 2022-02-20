# Nginx
### 作用：
反向代理：将用户的请求分到不同服务器（相对的，正向代理指代理客户端，比如vpn）
负载均衡：将请求按照配置的权重分到不同服务器，有的性能好多分点
动静分离：一些静态文件不需要经过后台，直接用ngix处理

### 常用命令：
cd _usr_local_nginx_sbin
./nginx 启动
./nginx -s reload 重新加载
./nginx -s stop 停止
./nginx -s  quit  安全退出
ps aux|grep nginx 查看nginx进程

### 常用配置文件路径：
```
1. /usr/local/etc/nginx/nginx.conf （nginx配置文件路径）
2. /usr/local/var/www （nginx服务器默认的根目录）
3. /usr/local/Cellar/nginx/1.17.9 （nginx的安装路径）
4. /usr/local/var/log/nginx/error.log (nginx默认的日志路径)
```

### 配置文件
Server{ } 其实是包含在 http{ } 内部的。每一个 server{ } 是一个虚拟主机（站点）。
上面代码块的意思是：当一个请求叫做localhost:8080请求nginx服务器时，该请求就会被匹配进该代码块的 server{ } 中执行。
```
# 首尾配置暂时忽略
server {  
        # 当nginx接到请求后，会匹配其配置中的service模块
        # 匹配方法就是将请求携带的host和port去跟配置中的server_name和listen相匹配
        listen       8080;        
        server_name  localhost; # 定义当前虚拟主机（站点）匹配请求的主机名

        location / {
            root   html; # Nginx默认值
            # 设定Nginx服务器返回的文档名
            index  index.html index.htm; # 先找根目录下的index.html，如果没有再找index.htm
        }
}
# 首尾配置暂时忽略
```


