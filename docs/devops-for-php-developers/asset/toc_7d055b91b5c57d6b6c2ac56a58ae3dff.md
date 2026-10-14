## 手动服务器设置
### 寻找合适的服务器
### 创建 Droplet
### 服务器更新
### apt update
### apt upgrade -y
### 无人值守升级
### 安装构建工具
### apt install -y build-essential g++ gcc unzip
### 设置 MySQL 服务器
### wget https://repo.percona.com/apt/percona-release_latest.$(lsb_release -sc)_all.deb
### dpkg -i percona-release_latest.$(lsb_release -sc)_all.deb
### percona-release setup ps80
### 安装 Percona Server
### apt install -y percona-server-server
### echo -e "[mysqld]\ndefault-authentication-plugin = mysql_native_password" > /etc/mysql/mysql.conf.d/default-auth-override.cnf
### service mysql restart
### systemctl enable mysql
### mysql_secure_installation
### rm percona-release_latest.$(lsb_release -sc)_all.deb
### 设置 PHP 7.4
### add-apt-repository ppa:ondrej/php
### apt install -y php-pear php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-dev php7.4-gd php7.4-json php7.4-mysql php7.4-opcache php7.4-readline php7.4-sqlite3 php7.4-tidy php7.4-xml php7.4-bcmath php7.4-bz2 php7.4-fpm php7.4-imap php7.4-zip php7.4-mbstring php7.4-soap php7.4-xsl php7.4-intl imagemagick php7.4-imagick
### systemctl enable php7.4-fpm
### php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
### php -r "if (hash_file('sha384', 'composer-setup.php') === 'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353fde0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
### php composer-setup.php
### php -r "unlink('composer-setup.php');"
### mv composer.phar /usr/local/bin/composer
### which composer
### 设置 Redis 服务器
### apt install -y redis-server
### systemctl enable redis-server
### 设置 Nginx
### apt remove apache2
### add-apt-repository ppa:nginx/stable
### apt install -y nginx
### systemctl enable nginx
### cat /etc/php/7.4/fpm/pool.d/www.conf | grep 'listen ='
### 使用 Ansible 实现服务器自动化设置
#### Nginx 的 PHP-FPM 配置
#### vi /etc/nginx/sites-available/default
#### nginx -t
#### service nginx restart
#### echo -e "<?php\nphpinfo();" > /var/www/html/info.php
## 什么是 Ansible？
## 设置 Ansible
### Fedora
### CentOS
### Ubuntu
### macOS 或其他系统上的本地单用户安装
### macOS 或其他系统上的系统级安装
## Ansible 清单
### your server ip addresses
### your server ip addresses
## YAML 基础
### Literal
### same as:
### this is\nthe\nwrapped\nhello world template
### Folded
### same as:
### this is the wrapped\nhello world template
## Ansible Playbooks
### Ansible Playbooks 和 Roles
## 初始设置
## 角色结构
## Common 角色
### tasks file for common role
## Pre-Setup 子任务
### 预设置与优化
## common 的 defaults 文件
## pre_setup 任务
## 无人值守升级
## 完整的 pre_setup 任务
## 优化子任务
## 优化连接限制
## 添加重启处理程序
### handlers file for common
## 完整的优化任务文件
## 用户子任务
### tasks for users.yml
## 安全子任务
### tasks for security
### 使用别名
### 使用 ssh config
## MySQL 角色
### Percona 子任务
### mysql/handlers/main.yml
### 配置子任务
### 创建 MySQL 配置文件
### `templates/my.cnf.j2`
### 禁用符号链接以防止各种安全风险
### 内存设置。
### InnoDB 设置。
### `defaults/main.yml`
### mysql 的默认文件
### caching_sha2_password 是默认值，但大多数客户端不支持它
### `mysql/tasks/configure.yml`
### mysql/tasks/configure.yml
### `templates/root-my.cnf.j2`
### `mysql/tasks/main.yml`
### tasks file for mysql
## PHP 角色
### 安装子任务
### `php/defaults/main.yml`
### defaults file for php
### `php/tasks/installs.yml`
### 安装 PHP 包
### 更新 PECL 协议
### 安装 PECL 包
### 配置子任务
### php/tasks/configure.yml
### handlers file for php
### tasks file for php
## Nginx 角色
### tasks file for nginx
### 安装子任务
### 配置子任务
### defaults file for nginx
## Nginx 配置与 SSL 安全加固
### 生成 Diffie-Hellman 参数
### defaults/main.yml
### 配置 SSL 参数模板
### Use per block. ssl-params
### SSL 配置说明
### 部署 SSL 片段
### 默认 Server 块模板
### 默认变量
### 默认 Server 块模板文件 `nginx/templates/default.j2`
### 部署默认 Server 块
### nginx 的处理器文件
## ACL 角色
### acl 的任务文件
## 测试与部署
### 测试用例
### 本地测试
#### 测试 Laravel
### 测试文章更新与删除功能
### 更新文章测试
### 删除文章测试
### 完整文件
### Post Controller
### Post Test
## 使用 GitLab CI/CD 进行自动化测试
### 开始使用 Docker
### 构建与发布 Docker 镜像
## Docker 镜像构建与 GitLab CI/CD 配置
### Docker 镜像构建
### 生成 `.gitlab-ci.yml`
## GitLab CI/CD 配置与自动化部署
### GitLab CI/CD 配置文件
### 仓库初始化与推送
### 使用 GitLab CI/CD 实现自动化部署
#### SSH 配置
#### 目录结构
#### Laravel Envoy
## Laravel Envoy 部署脚本与 CI/CD 配置
### 生产环境配置
### paste the content
### update the variables
### 部署流程配置
### 手动部署
## 还有更多！
## 文档大纲