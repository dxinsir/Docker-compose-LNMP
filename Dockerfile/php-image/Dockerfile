#基础镜像
FROM centos:centos7
#作者
MAINTAINER Dx dxinsir@163.com

#更新yum源，安装PHP依赖包
RUN yum -y update && \
    yum install -y gcc \
	 gcc-c++ \
	 curl \ 
	 curl-devel \
	 libxml2 \
	 libxml2-devel \
	 openssl \
	 openssl-devel \
	 libcurl \
	libcurl-devel \
	libjpeg \
	libjpeg-devel \
	libpng \
	libpng-devel \
	freetype \
	freetype-devel \
	epel-release \
	wget \
	&& yum install -y libmcrypt libmcrypt-devel \
	&& yum clean all

#下载PHP、编译
RUN  cd /tmp \
	&& wget http://cn2.php.net/get/php-7.1.16.tar.gz/from/this/mirror \
	&& mv mirror php-7.1.16.tar.gz \
	&& tar -xzf php-7.1.16.tar.gz \
	&& cd php-7.1.16 \
	&& ./configure --prefix=/usr/local/php --with-mysqli --with-pdo-mysql --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir --enable-simplexml --enable-xml --disable-rpath --enable-bcmath --enable-soap --enable-zip --with-curl --enable-fpm --with-fpm-user=nobody --with-fpm-group=nobody --enable-mbstring --enable-sockets --with-mcrypt --with-gd --enable-gd-native-ttf --with-openssl --with-mhash --enable-opcache \
	&& make \
	&& make install \
	&& cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf \
	&& cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
#指定端口
EXPOSE 9000
CMD ["/usr/local/php/sbin/php-fpm"]
