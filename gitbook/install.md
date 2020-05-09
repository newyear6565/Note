http://nginx.org/download/

https://sourceforge.net/projects/pcre/files/pcre/

http://www.zlib.net/zlib-1.2.11.tar.gz

### 安装方法

```bash
tar zxf zlib-1.2.11.tar.gz 
cd zlib-1.2.11/ 
./configure 
make 
sudo make install

# 指定目录的make install

make DESTDIR=/install/directory install
```

### NGINX的配置
```conf
worker_processes  1;  

events {
    worker_connections  1024;
}

http {
    include            mime.types;
    default_type       application/octet-stream;
    sendfile           on; 
    keepalive_timeout  65; 
    charset utf-8;                # 设置编码格式
    

    server {
    	listen 8081;              # 端口号
    	#server_name _;           # 配置域名信息
    	root /home/zgy/webbook;   # 静态页面根目录
    	index index.html;
    }
}
```

启动nginx，-c指定配置文件路径，-p指定目录名
```bash
./nginx -c /home/zgy/tool/nginx/nginx/usr/local/nginx/conf/nginx.conf -p /home/zgy/tool/nginx/tmp
```

### 插件的使用

添加book.js

```json
{
        "plugins":["toggle-chapters"]
}
```

```bash
gitbook install
```

### Build
```bash
OutputDir的路径与Nginx配置文件中root的路径一致
gitbook build originDir OutputDir
```

