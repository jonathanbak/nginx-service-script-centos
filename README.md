# nginx-service-script-centos


Amazon Linux 1, 2, CentOS7 에서 nginx 소스 컴파일 방법

### 의존성 라이브러리 설치

```bash
# yum groupinstall -y "Development Tools"

# yum install -y pcre pcre-devel libxml2 libxml2-devel curl curl-devel openssl openssl-devel

```

### nginx 소스 컴파일
```bash
# groupadd -r nginx
# useradd -r -g nginx -s /sbin/nologin -M nginx

# mkdir /usr/src
# cd /usr/src/
# wget https://nginx.org/download/nginx-1.14.0.tar.gz
# tar zxvf nginx-1.14.0.tar.gz
# cd nginx-1.14.0
# ./configure --user=nginx --group=nginx --with-http_ssl_module
# make
# make install
# sed -i "s/#user  nobody;/user nginx nginx;/" /usr/local/nginx/conf/nginx.conf
# /usr/local/nginx/sbin/nginx -t

```

### nginx service 등록
```
# wget https://raw.githubusercontent.com/jonathanbak/nginx-service-script-centos/master/nginx-script

# mv nginx-script /etc/init.d/nginx && chmod 755 /etc/init.d/nginx

# service nginx start
```
 