FROM	debian:buster-slim

RUN	apt-get update -y
RUN	apt-get upgrade -y
RUN	apt-get install wget -y
RUN	apt-get install -y php7.3\
	php7.3-fpm\
	php7.3-mysql\
	php7.3-phar\
	mariadb-client

RUN	wget https://wordpress.org/wordpress-6.0.tar.gz -P /var/www
RUN	cd /var/www && tar -xzf wordpress-6.0.tar.gz  && rm wordpress-6.0.tar.gz

COPY	./conf/php.conf		/etc/php/7.3/fpm/pool.d/www.conf



RUN	chown -R root:root /var/www/wordpress

RUN	wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

RUN	chmod +x wp-cli.phar
RUN	mv wp-cli.phar /usr/local/bin/wp-cli.phar

COPY 	conf/my_conf.sh my_conf.sh

ENTRYPOINT ["bash", "my_conf.sh"]
