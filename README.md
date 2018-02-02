# SmartCloud_WiKi
wiki for SmartCloud porject

# Laravel PHP framework
[Laravel](https://github.com/laravel/laravel)

# web 工程准备

## php web 环境

```
1. sudo apt-get install php7.0 php7.0-* -y
2. sudo apt-get install apache2 -y
3. sudo apt-get install libapache2-mod-php7.0 -y

```

## laravel 安装

### composer

```
1. curl -sS https://getcomposer.org/installer | php
2. sudo mv composer.phar /usr/local/bin/composer
3. sudo apt-get install snmp-mibs-downloader
```

### laravel

```
1. composer global require "laravel/installer"
```

``` 添加composer环境变量
2. vim ~/.profile
3. export PATH=$PATH:$HOME/.config/composer/vendor/bin

```

## web 工程部署

### clone 代码并安装依赖库
```
1. cd ~
2. mkdir Project
3. cd Project
4. git clone git@github.com:ejngnng/SmartCloud.git
5. cd SmartCloud
6. composer install 或者composer update
```

### 配置Application Key

```
1. cd SmartCloud
2. cp -a .env.example .env
3. php artisan key:generate
```

### 配置storage 读写权限

```
1. chmod -R 777 SmartCloud/storage
```

### 配置apache

```
1. cd /var/www/
2. sudo ln -s ~/Project/SmartCloud .
3. sudo vim /etc/apache2/sites-available/000-default.conf
4. 改 DocumentRoot /var/www/SmartCloud/public
5. sudo systemctl restart apache2
```
