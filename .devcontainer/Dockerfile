#-------------------------------------------------------------------------------------------------------------
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License. See https://go.microsoft.com/fwlink/?linkid=2090316 for license information.
#-------------------------------------------------------------------------------------------------------------

FROM php:7-apache-stretch

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# Configure apt and install packages
RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils zip unzip nano ncdu 2>&1 \
	#
	# Webgrind prereqs
	&& apt-get -y install --no-install-recommends python graphviz 2>&1 \
    #
    # Install git, procps, lsb-release (useful for CLI installs)
    && apt-get -y install git iproute2 procps lsb-release \
    #
    # Install xdebug
    && yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.profiler_enable_trigger=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
	#
	# Install extensions (optional)
	&& apt-get -y install libicu-dev \
	&& docker-php-ext-install intl pdo_mysql opcache \
	&& pecl install apcu && docker-php-ext-enable apcu \
	&& echo "apc.enable_cli=1" > /usr/local/etc/php/php.ini \
	&& echo "apc.enable=1" > /usr/local/etc/php/php.ini \
	&& a2enmod rewrite \
	#
	# Install composer
	&& curl -s https://getcomposer.org/installer | php \
	&& mv composer.phar /usr/local/bin/composer \
	&& composer global require hirak/prestissimo \
    #
    # Clean up
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
	#
	# Link our site config to the devcontainer
RUN rm -rf /etc/apache2/sites-enabled \
	&& ln -s /var/www/html/.devcontainer/sites-enabled /etc/apache2/sites-enabled

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog


