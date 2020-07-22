FROM centos:7
RUN yum install epel-release wget -y \
    && yum clean all  \
    && yum makecache \
    && rpm -ivh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm \
    && yum install -y php72w php72w-cli php72w-fpm php72w-mbstring php72w-xml php72w-bcmath php72w-gd php72w-mysql php72w-opcache php72w-process php72w-devel \
    && wget -O composer-setup.php https://getcomposer.org/installer \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer


COPY www.conf /etc/php-fpm.d/www.conf
RUN mkdir -p /app
COPY laravel-blog /app
WORKDIR /app
RUN composer config repo.packagist composer https://mirrors.aliyun.com/composer/ \
    && composer install
EXPOSE 9000
# Run PHP-FPM on container start.
CMD ["/usr/sbin/php-fpm", "-F", "-R"]