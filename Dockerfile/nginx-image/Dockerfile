# 指定基础镜像
FROM centos:centos7
# 作者
MAINTAINER Dx dxinsir@163.com
# 更新yum源，安装Nginx依赖包
  RUN yum -y update && \
     yum install -y gcc make gcc-c++ openssl-devel  libmcrypt-devel libmcrypt mcrypt libxml2 libxml2-devel bzip2 bzip2-devel curl curl-devel wget  && \
     yum clean all
# 安装Nginx
RUN cd /tmp \
  && wget http://nginx.org/download/nginx-1.13.10.tar.gz \
  && tar -xzf nginx-1.13.10.tar.gz \
  && cd /tmp/nginx-1.13.10 \
  && ./configure \
    --prefix=/usr/local/nginx \
    --with-http_ssl_module --with-http_sub_module --with-http_dav_module --with-http_flv_module \
    --with-http_gzip_static_module --with-http_stub_status_module --with-debug \
  && make \
  && make install
# 指定对外开放端口
EXPOSE 80 443
#前台挂起Nginx
CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
