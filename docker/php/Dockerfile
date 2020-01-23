FROM ubuntu:18.04
RUN apt update
RUN apt install -y wget gcc htop nano less
RUN apt install -y libxml2-dev libjpeg-dev libpng-dev libfreetype6-dev libbz2-dev libmcrypt-dev libxslt1-dev
RUN wget http://de2.php.net/get/php-5.4.45.tar.gz/from/this/mirror  --output-document=/usr/local/src/php-5.4.45.tar.gz
RUN tar -C "/usr/local/src" -xzvf /usr/local/src/php-5.4.45.tar.gz
WORKDIR "/usr/local/src/php-5.4.45"
RUN ./configure --prefix=/opt/php-5.4.45 --enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data --with-pdo-mysql --enable-mbstring --enable-sockets \
    --enable-exif --enable-bcmath --enable-calendar --enable-zip --enable-ftp --enable-gd-native-ttf --with-gd --with-freetype-dir -with-zlib --with-bz2 \
    --with-mcrypt -with-mhash --with-pcre-regex --with-xmlrpc --with-xsl -with-mysql --enable-intl --with-gettext
RUN make
RUN make install
COPY php-fpm.conf /opt/php-5.4.45/etc/

EXPOSE 9000
CMD ["/opt/php-5.4.45/sbin/php-fpm", "--nodaemonize"]