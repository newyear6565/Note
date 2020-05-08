http://nginx.org/download/

https://sourceforge.net/projects/pcre/files/pcre/

http://www.zlib.net/zlib-1.2.11.tar.gz

### 安装方法
tar zxf zlib-1.2.11.tar.gz 
cd zlib-1.2.11/ 
./configure 
make 
sudo make install

指定目录的make install
make DESTDIR=/install/directory install

### NGINX的配置
worker_processes  1;  

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on; 
    keepalive_timeout  65; 
    charset utf-8;        # 设置编码格式
    
    server {
    listen 8081;             # 端口号
    #server_name _;           # 配置域名信息
    root /home/zgy/webbook;               # 静态页面根目录
    index index.html;
    }   
}

### 插件的使用
添加book.js
{
        "plugins":["toggle-chapters"]
}

gitbook install

### Build
OutputDir的路径与Nginx配置文件中root的路径一致
gitbook build originDir OutputDir

