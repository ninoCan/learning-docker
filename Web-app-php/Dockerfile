############################################################
# Dockerfile to build Linux Apache PHP server with WordPress
# Based on the official php:7.2-apache
############################################################

    #load the php image with apache2 preinstalled
    FROM php:7.2-apache

    #specify the mainteiner of this image (me=Antonino Cangialosi)
    MAINTAINER nino <ninocangialosi@yahoo.it>

    # add the mysql needed extensions for php
    RUN docker-php-ext-install mysqli pdo_mysql

    # change into this directory on the run
    WORKDIR /var/www/html/

    #copy the content of an hello php file from the locale to that path
    COPY ./index.php /var/www/html/

#version 1.0 starts here
    #attach the latest (at time of image building) WordPress installation
    COPY ./latest.tar.gz /var/www/
    #move the starting directory to /var/www/
    WORKDIR /var/www/
    #expand the package
<<<<<<< HEAD
<<<<<<< HEAD
    RUN tar -xzvf latest.tar.gz -C /var/www/
=======
=======
>>>>>>> cba00818728bd59c2b5ccc99d4419bb7e5e8b877
    RUN rm latest.tar.gz
    #remove the taz.gz package from the container. Version 1.1
    RUN mv /var/www/wordpress/wp-config-sample.php /var/www/wordpress/wp-config.php
>>>>>>> cba00818728bd59c2b5ccc99d4419bb7e5e8b877
    #create the WordPress configuration file out of the available sample
    RUN mv /var/www/wordpress/wp-config-sample.php /var/www/wordpress/wp-config.php

    # define and put in place the variables needed to be inputed at time of the container initialization
    RUN sed -i "s/'database_name_here'/getenv('DB_NAME')/" /var/www/wordpress/wp-config.php
    RUN sed -i "s/'username_here'/getenv('DB_USER')/" /var/www/wordpress/wp-config.php
    RUN sed -i "s/'password_here'/getenv('DB_PASSWORD')/" /var/www/wordpress/wp-config.php
    RUN sed -i "s/'localhost'/getenv('DB_HOST')/" wordpress/wp-config.php

    #tells apache to load the wordpress page instead of the simple php file
    RUN cd /etc/apache2/sites-enabled/
    RUN sed -i 's/\/var\/www\/html/\/var\/www\/wordpress/' /etc/apache2/sites-enabled/000-default.conf
    #version 1.0 stops here

    EXPOSE 80
    #opens port 80 for external comunication

    CMD ["apache2-foreground"]
    #run the final apache2 config
