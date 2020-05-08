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