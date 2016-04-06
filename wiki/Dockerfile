FROM		ubuntu:16.04
MAINTAINER	Juergen Doenitz

RUN		apt-get update
RUN		apt-get install -y wget unzip apache2 make git php5 php5-mysql curl

RUN		wget https://github.com/AKSW/OntoWiki/archive/develop.zip
RUN		unzip develop.zip

RUN		ls -l /var/www/

RUN		mkdir /var/www/html/ontowiki
RUN		mv OntoWiki-develop/* /var/www/html/ontowiki/
#RUN		rmdir OntoWiki-develop
RUN		a2enmod rewrite

RUN		cd /var/www/html/ontowiki && make getcomposer
RUN		cd /var/www/html/ontowiki && make install

ADD		config.ini /var/www/html/ontowiki/

EXPOSE		80 
EXPOSE		443 

RUN		apt-get remove -y wget unzip make git
RUN		apt-get clean

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

