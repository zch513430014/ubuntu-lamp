ARG UBUNTU_VERSION=${UBUNTU_VERSION}
FROM ubuntu:${UBUNTU_VERSION}
LABEL maintainer="Grant Zuo <513430014@qq.com>"
LABEL version="1.0.0"
COPY ./aliyunsource.list /etc/apt/aliyunsource.list
RUN mv /etc/apt/sources.list /etc/apt/sources.list.cp \
&& mv /etc/apt/aliyunsource.list /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y openssl
RUN apt-get install -y wget
RUN apt-get install -y libssl-dev
#去下面这个网站选择一个php版本，下载速度要快一点国内
#http://mirrors.sohu.com/php/
ARG PHP_VERSION=${PHP_VERSION}
RUN wget http://mirrors.sohu.com/php/php-${PHP_VERSION}.tar.gz -O /tmp/php-${PHP_VERSION}.tar.gz
#COPY ./php.tar.gz /usr/local/src/php.tar.gz
RUN tar -zxvf /tmp/php-${PHP_VERSION}.tar.gz -C /tmp
RUN apt-get install -y gcc
RUN apt-get install -y libxml2-dev
RUN apt-get install -y libsqlite3-dev
RUN apt-get install -y libcurl4-openssl-dev
RUN apt-get install -y alien
RUN apt-get install -y libbz2-dev
RUN apt-get install -y libgmp-dev
RUN apt-get install -y libsasl2-dev
RUN apt-get install -y libldap-dev
RUN apt-get install -y libonig-dev
RUN apt-get install -y libxslt1-dev
#指定编译到的文件夹
RUN mkdir -p /usr/local/php
RUN cd /tmp/php-${PHP_VERSION} && ./configure --prefix=/usr \
 --enable-fpm \
 --exec-prefix=/usr \
 --bindir=/usr/bin \
 --sbindir=/usr/sbin \
 --sysconfdir=/etc \
 --datadir=/usr/share \
 --includedir=/usr/include \
 --libdir=/usr/lib \
 --libexecdir=/usr/libexec \
 --localstatedir=/var \
 --sharedstatedir=/var/lib \
 --mandir=/usr/share/man \
 --infodir=/usr/share/info \
 --cache-file=../config.cache \
 --with-libdir=lib \
 --with-config-file-path=/etc/php \
 --with-config-file-scan-dir=/etc/php/php.d \
 --disable-debug \
 --with-pic \
 --disable-rpath \
 --without-pear \
 --with-bz2 \
 --with-exec-dir=/usr/bin \
 --with-freetype-dir=/usr \
 --with-png-dir=/usr \
 --with-xpm-dir=/usr \
 --enable-gd-native-ttf \
 --with-t1lib=/usr \
 --with-gettext \
 --with-gmp \
 --with-iconv \
 --with-jpeg-dir=/usr \
 --with-openssl \
 --with-pcre-regex=/usr \
 --with-zlib \
 --with-layout=GNU \
 --enable-exif \
 --enable-ftp \
 --enable-sockets \
 --enable-shmop \
 --enable-calendar \
 --with-libxml-dir=/usr \
 --enable-xml \
 --with-system-tzdata \
 --with-mhash \
 --enable-pcntl \
 --enable-mbstring=shared \
 --enable-mbregex \
 --with-gd=shared \
 --enable-bcmath=shared \
 --with-xmlrpc=shared \
 --with-ldap=shared \
 --with-ldap-sasl \
 --enable-mysqlnd=shared \
 --with-mysql=shared,mysqlnd \
 --with-mysqli=shared,mysqlnd \
 --with-mysql-sock=/var/lib/mysql/mysql.sock \
 --enable-dom=shared \
 --enable-wddx=shared \
# --with-snmp=shared,/usr \
 --enable-soap=shared \
 --with-xsl=shared,/usr \
 --enable-xmlreader=shared \
 --enable-xmlwriter=shared \
 --with-curl=shared,/usr \
 --enable-pdo=shared \
 --with-pdo-mysql=shared,mysqlnd \
 --with-pdo-sqlite=shared,/usr \
 --with-sqlite3=shared,/usr \
 --enable-json=shared \
 --enable-zip=shared \
 --with-libzip \
 --without-readline \
 --enable-phar=shared \
 --enable-sysvmsg=shared \
 --enable-sysvshm=shared \
 --enable-sysvsem=shared \
 --enable-posix=shared \
 --enable-fileinfo=shared \
 --enable-intl=shared \
 --with-icu-dir=/usr \
 --with-recode=shared,/usr
RUN cd /tmp/php-${PHP_VERSION} && make && make install
#添加环境变量
#RUN ln -s /usr/local/php/bin/phpize /usr/bin/phpize \
#    && ln -s /usr/local/php/bin/php-config /usr/bin/php-config \
#    && ln -s /usr/local/php/bin/php-cgi /usr/bin/php-cgi \
#    && ln -s /usr/local/php/bin/php /usr/bin/php \
#    && ln -s /usr/local/php/bin/pecl /usr/bin/pecl
#新添加扩展需要
RUN apt-get install -y m4
RUN apt-get install -y autoconf
#添加常用扩展
RUN apt-get install -y vim
#安装yaf yar yaconf sealog 环境

