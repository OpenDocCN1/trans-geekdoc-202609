
# PHP 开发者的 DevOps 指南

## 前言

### 本书的设计理念

虽然本书专注于 PHP，但此处描述的技术可应用于任何其他语言或部署，包括但不限于容器发布、Node.js 应用程序、Ruby 等。

我们将主要关注完整的 LEMP（Linux Nginx MySQL PHP）服务器，即所有二进制文件均运行在同一台服务器上。根据您的需求，您可以使用专用的 MySQL 实例，以及一个作为网关的独立 Nginx 实例，您只需修改脚本以匹配您的设置即可。

您可以按任何您喜欢的顺序阅读本书。参考资源均可随时获取，其中部分为开源资源。

所有待执行的 Shell 命令均以前缀 `$` 或 `#` 加一串字符的形式书写，输出将紧随其后，例如：

```
$ echo 'hello world'
hello world
```

### 谁应该阅读本书？

任何软件开发人员或管理员均可阅读本书。本书非常适合自由职业者、初创企业、企业家以及所有从事服务器工作并编写少量代码的人员。

由于本书主要涉及 PHP，您应了解该语言并理解您正在使用的技术栈；无论是 LAMP 还是 LEMP；并对服务器设置、SSH 和终端的使用有少许了解。

### 责任声明

我已竭尽全力确保书中信息的准确性。

然而，本书所含信息不提供任何担保，无论明示或暗示。作者、经销商或分销商均不对因本书中的说明，或因书中所述软件或服务提供商而直接或间接造成的任何损害承担责任。

## 手动服务器设置

### 寻找合适的服务器

有几家提供商（[DigitalOcean](https://www.digitalocean.com/?refcode=9724e049fc4d)、[Linode Cloud](https://www.linode.com/products/standard-linodes/)、[AWS](https://aws.amazon.com/ec2/)、[Vultr](https://www.vultr.com/?ref=7275395) 等）提供极具竞争力的价格，从 [Vultr](https://www.vultr.com/?ref=7275395) 的 10GB SSD、1 vCPU 和 512 MB RAM 每月 2.5 美元，到 [DigitalOcean](https://www.digitalocean.com/?refcode=9724e049fc4d) 的 3,840GB SSD、32 vCPU 和 192GB RAM 每月 960 美元不等。

在我们的案例中，我们将使用 [每月 40 美元的 DigitalOcean Droplet（160GB SSD，4 vCPUs and 8GB of RAM) running the latest version of Ubuntu, 20.04 LTS.](https://cloud.digitalocean.com/droplets/new?size=s-4vcpu-8gb)

### 创建 Droplet

如果您想要分离服务并拥有 Redis、MySQL、Nginx 和 PHP 服务器，请在“Select additional options”下启用私有网络。这将为 Droplet 分配私有 IP 地址，用于同一数据中心区域内的服务器间通信。

根据您的需求，增加要创建的 Droplet 数量。在本例中我们仅使用一个。最后，添加您的 SSH 密钥（[或创建一个](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)），选择所需的主机名并创建 Droplet。

Droplet 创建完成后，复制公共 IP 地址，打开终端并通过 SSH 登录服务器：

```
$ ssh root@123.45.6.78
```

```
The authenticity of host '123.45.6.78 (123.45.6.78)' can't be established.
ECDSA key fingerprint is SHA256:shashashasahashashashasaha.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '123.45.6.78' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-51-generic x86_64)
* Documentation: https://help.ubuntu.com
* Management: https://landscape.canonical.com
* Support: https://ubuntu.com/advantage
System information as of Wed Oct 28 05:26:58 UTC 2020
System load: 0.47  Users logged in: 0
Usage of /: 0.7% of 24.06GB  IPv4 address for eth0: 123.45.6.78
Memory usage: 4%  IPv4 address for eth0: 10.10.0.5
Swap usage: 0%  IPv4 address for eth1: 10.116.0.2
Processes: 97
1 update can be installed immediately.
0 of these updates are security updates.
To see these additional updates run: `apt list --upgradable`
The list of available updates is more than a week old.
To check for new updates run: `sudo apt update`
The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in `/usr/share/doc/*/copyright`.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
root@ubuntu-s-1vcpu-1gb-nyc1-01:~#
```

太棒了！我们已成功启动！

### 服务器更新

默认情况下，我们的 Ubuntu 20.04 LTS 服务器有一些过时的二进制文件，因此让我们先更新它们：

```
$ apt update
```

```
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
Get:2 http://mirrors.digitalocean.com/ubuntu focal InRelease [265 kB]
...
...
Building dependency tree
Reading state information... Done
53 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

```
$ apt upgrade -y
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
linux-headers-5.4.0-53 linux-headers-5.4.0-53-generic linux-image-5.4.0-53-generic linux-modules-5.4.0-53-generic
The following packages will be upgraded:
...
...
53 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 88.0 MB of archives.
After this operation, 174 MB of additional disk space will be used.
Get:1 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 libperl5.30 amd64 5.30.0-9ubuntu0.2 [3,952 kB]
Get:2 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 perl amd64 5.30.0-9ubuntu0.2 [224 kB]
Get:3 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 perl-base amd64 5.30.0-9ubuntu0.2 [1,513 kB]
...
...
done
```

### 无人值守升级

Debian/Ubuntu 提供的 [Unattended Upgrades 包](https://help.ubuntu.com/community/AutomaticSecurityUpdates) 可用于自动更新系统，可将其视为 Debian 或 Ubuntu 版的 Windows Update。让我们设置它来处理安全更新。该包通常默认已安装，如果缺失，请使用以下命令安装：`apt install unattended-upgrades`。

我们现在需要找到并修改 `/etc/apt/apt.conf.d/50unattended-upgrades` 以满足我们的要求。目前，我们将仅启用安全更新，但您可以随意调整该文件以满足您的需求。确认 `Unattended-Upgrade::Allowed-Origins` 部分具有以下活动配置：

```
Unattended-Upgrade::Allowed-Origins {
"${distro_id}:${distro_codename}";
"${distro_id}:${distro_codename}-security";
"${distro_id}ESMApps:${distro_codename}-apps-security";
"${distro_id}ESM:${distro_codename}-infra-security";
// "${distro_id}:${distro_codename}-updates";
// "${distro_id}:${distro_codename}-proposed";
// "${distro_id}:${distro_codename}-backports";
};
```

Extended Security Maintenance (ESM) 源并非在所有版本中都存在，但如果可用将会被使用，因此保留它无妨。

您希望手动更新的所有包都应添加到 `Unattended-Upgrade::Package-Blacklist` 部分。每当运行自动更新时，这些包将被排除在更新之外。这对于有问题的包特别有用。

某些包需要系统重启才能完成安装。您可以允许自动重启，也可以手动重启服务器。

在本例中，我们将允许在 UTC 02:00 左右自动重启。

```
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-Time "02:00";
```

剩下的就是通过编辑（或创建）apt 配置文件 `/etc/apt/apt.conf.d/20auto-upgrades` 来启用无人值守更新，并设置我们希望多久下载一次可升级的包以及多久运行一次自动清理。

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

搞定！我们已完成自动更新的设置。

### 安装构建工具

我们现在将安装一些稍后从源代码编译其他包所需的包。

```
$ apt install -y build-essential g++ gcc unzip
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-9
...
...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
```

现在我们可以开始设置我们的 LEMP 服务器了。

> **注意**：大部分手动步骤将被跳过，但将在自动化部分中得到充分解释。

### 设置 MySQL 服务器

[我个人更倾向于使用 Percona Server](https://www.percona.com/software/mysql-database/percona-server) [而非 MySQL Community](https://www.mysql.com/products/community)，因为它是任何 MySQL 数据库的免费、完全兼容、增强且开源的直接替代品。它提供了卓越的性能、可扩展性和检测能力。

由于 Percona Server 不在标准 Ubuntu 仓库中，我们需要添加其源并启用 `ps80` 仓库以使用 MySQL 8。

```
$ wget https://repo.percona.com/apt/percona-release_latest.$(lsb_release -sc)_all.deb
```

```
--2020-10-28 06:51:13-- https://repo.percona.com/apt/percona-release_latest.focal_all.deb
Resolving repo.percona.com (repo.percona.com)... 167.99.233.229, 157.245.119.64, 167.71.118.3
Connecting to repo.percona.com (repo.percona.com)|167.99.233.229|:443...
connected.
...
...
```

```
$ dpkg -i percona-release_latest.$(lsb_release -sc)_all.deb
```

```
(Reading database ... 100078 files and directories currently installed.)
Preparing to unpack percona-release_latest.focal_all.deb ...
...
...
```

```
$ percona-release setup ps80
```

```
* Disabling all Percona Repositories
* Enabling the Percona Server 8.0 repository
* Enabling the Percona Tools repository
Get:1 http://mirrors.digitalocean.com/ubuntu focal InRelease [265 kB]
...
Reading package lists... Done
```

### 安装 Percona Server

现在我们可以安装 Percona Server。由于大多数应用程序尚未使用新的 MySQL 认证插件，我们将指示 Percona 使用传统的 MySQL 5.x 认证。按照提示操作，为 `root` 用户输入一个安全密码，然后选择原生认证插件。

```
$ apt install -y percona-server-server
```

```
...
...

Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
```

**注意：** 如果你未启用原生认证插件，但现在需要启用，请创建一个新的 MySQL 配置文件以便在 MySQL 启动时设置它，然后重启 MySQL。我们还将确保 MySQL 在系统启动时自动运行。



```bash
### echo -e "[mysqld]
default-authentication-plugin = mysql_native_password" > /etc/mysql/mysql.conf.d/default-auth-override.cnf
### service mysql restart
### systemctl enable mysql
```

接下来，让我们运行 MySQL 提供的脚本以提高安装的安全性。

```bash
### mysql_secure_installation
```

最后，我们可以清理并删除下载的文件：

```bash
### rm percona-release_latest.$(lsb_release -sc)_all.deb
```

大功告成！

## 设置 PHP 7.4

编写本文时，PHP 的最新版本是 7.4。请根据你感兴趣的版本进行调整。让我们使用 [Ondrej's PPA](https://launchpad.net/~ondrej/+archive/ubuntu/php) 来设置我们的 PHP 7.4 实例。

```bash
### add-apt-repository ppa:ondrej/php
```

```
Co-installable PHP versions: PHP 5.6, PHP 7.x and most requested extensions are included. Only Supported Versions of
PHP (http://php.net/supported-versions.php) for Supported Ubuntu Releases (https://wiki.ubuntu.com/Releases) are
provided. Don't ask for end-of-life PHP versions or Ubuntu release, they won't be provided.
```

...

...

```
Get:14 http://ppa.launchpad.net/ondrej/php/ubuntu focal/main Translation-en [28.2 kB]
Fetched 1,030 kB in 2s (564 kB/s)
Reading package lists... Done
```

我们现在可以选择运行应用程序所需的 PHP 模块集合。提供的这些模块对于大多数应用程序来说是一个很好的起点。

```bash
### apt install -y php-pear php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-dev php7.4-gd php7.4-json php7.4-mysql php7.4-opcache php7.4-readline php7.4-sqlite3 php7.4-tidy php7.4-xml php7.4-bcmath php7.4-bz2 php7.4-fpm php7.4-imap php7.4-zip php7.4-mbstring php7.4-soap php7.4-xsl php7.4-intl imagemagick php7.4-imagick
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
autoconf automake autopoint autotools-dev debhelper
```

...

...

```
Processing triggers for php7.4-cli (7.4.12-3+ubuntu20.04.1+deb.sury.org+1) ...
Processing triggers for php7.4-fpm (7.4.12-3+ubuntu20.04.1+deb.sury.org+1) ...
```

然后启用 PHP-FPM 以便在启动时运行。

```bash
### systemctl enable php7.4-fpm
```

```
Synchronizing state of php7.4-fpm.service with SysV service script with
/lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable php7.4-fpm
```

既然我们使用他人的软件包，我们肯定需要 [Composer 来管理依赖。请遵循 Composer 安装指南](https://getcomposer.org/doc/00-intro.md)，该指南位于 [下载 Composer 页面，然后移动 composer 使其](https://getcomposer.org/download/) 全局可访问。

**警告：** 由于每当安装文件更改时哈希值都会变化，因此以下代码片段会随着时间的推移而过时。

```bash
### php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
### php -r "if (hash_file('sha384', 'composer-setup.php') === 'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353fde0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```

```
Installer verified
```

```bash
### php composer-setup.php
```

```
All settings correct for using Composer
Downloading...
Composer (version 2.0.4) successfully installed to: /root/composer.phar
Use it: php composer.phar
```

```bash
### php -r "unlink('composer-setup.php');"
### mv composer.phar /usr/local/bin/composer
### which composer
```

```
/usr/local/bin/composer
```

我们已经准备好 PHP 实例了！太棒了！

## 设置 Redis 服务器

[Redis](https://redis.io) 是一个很棒的内存键值存储。它可用作数据库、缓存，甚至使用 [Pub/Sub 作为消息代理。设置它并启用](https://redis.io/topics/pubsub) 开机自启非常简单：

```bash
### apt install -y redis-server
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
```

...

...

```
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
```

```bash
### systemctl enable redis-server
```

```
Synchronizing state of redis-server.service with SysV service script with
/lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable redis-server
```

## 设置 Nginx

[Nginx 是一个开源 Web 服务器，正如其官网所述，它](https://www.nginx.com/) 为超过 4 亿个网站提供支持。Nginx 非常健壮，也可以充当负载均衡器。要开始使用，我们必须确认未安装 `apache2`。

```bash
### apt remove apache2
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'apache2' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

接下来，我们将添加官方 Nginx PPA，以便始终获得最新更新。

```bash
### add-apt-repository ppa:nginx/stable
```

```
This PPA contains the latest Stable Release version of the nginx web server software.
**Only Non-End-of-Life Ubuntu Releases are supported in this PPA**
**Development releases of Ubuntu are not officially supported by this PPA, and uploads for those will not be available until actual final releases for those versions**
More info: https://launchpad.net/~nginx/+archive/ubuntu/stable
Press [ENTER] to continue or Ctrl-c to cancel adding it.
```

```
Hit:1 http://repo.percona.com/prel/apt focal InRelease
...
...
Reading package lists... Done
```

我们现在可以安装并启用 Nginx 以便在启动时运行。

```bash
### apt install -y nginx
```

```
Reading package lists... Done
Building dependency tree
...
...
Processing triggers for nginx-core (1.18.0-3ubuntu1+focal2) ...
Triggering nginx reload ..
```

```bash
### systemctl enable nginx
```

```
Synchronizing state of nginx.service with SysV service script with
/lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable nginx
```

太棒了！我们现在可以设置默认服务器块来处理 PHP 文件，并创建一个示例 PHP 文件来测试我们的安装。我们需要从配置文件中找到 php-fpm 套接字（TCP 或 Unix 套接字）。

**注意：** 你可以更改池定义中的 `listen` 选项以使用你首选的配置，默认为 Unix 套接字。

```bash
### cat /etc/php/7.4/fpm/pool.d/www.conf | grep 'listen ='
```

```
listen = /run/php/php7.4-fpm.sock
```

从上面的输出中，我们看到 PHP-FPM 正在通过位于 `/run/php/php7.4-fpm.sock` 的套接字进行监听。我们将在默认 Nginx 配置中使用此套接字作为 `fastcgi_pass` 参数。打开 `/etc/nginx/sites-available/default` 并更新它，以便允许处理 PHP 文件。

[我们要更改的第一件事是 index 指令](http://nginx.org/en/docs/http/ngx_http_index_module.html)。该指令决定了当 URL 以斜杠 (/) 结尾时加载的默认文件。

**警告：** 你设置参数的顺序很重要。如果你有一个 `index.php` 和一个 `index.html` 文件，且 `index` 指令设置为 `index index.html index.php`，则 `index.html` 文件将优先于 `index.php` 文件。

## 使用 Ansible 实现服务器自动化设置

### Nginx 的 PHP-FPM 配置

我们还将添加一个新的 location 块，并使用正则表达式匹配所有以 `.php` 结尾的文件，将它们发送给正在运行的 PHP-FPM 进程。

```bash
#### vi /etc/nginx/sites-available/default

root /var/www/html;

index index.php index.html index.htm index.nginx-debian.html;
server_name _;

location / {
    try_files $uri $uri/ =404;
}

location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php7.4-fpm.sock;
}
```

完成后，保存文件，测试确认其正确且无错误，然后重启 nginx 以使新配置生效。

```bash
#### nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

#### service nginx restart
```

我们现在可以添加一个 php info 脚本，用于检查我们的安装。

```bash
#### echo -e "<?php
phpinfo();" > /var/www/html/info.php
```

这太繁琐了！想象一下要对十台服务器执行所有这些步骤！

好消息是我们有 Ansible 来帮助我们实现自动化！打开你喜欢的浏览器，访问 `http://your.ip.over.here/info.php` 并确认 php info 页面已加载。

## 什么是 Ansible？

[Ansible](https://www.ansible.com/) 是红帽公司的一个平台，具有无限的自动化用例，允许同时在多台服务器上执行操作。Ansible 使用 YAML 语言编写文件，并依赖 SSH 协议来管理机器。

Ansible 安装后，不会添加数据库，也无需启动或保持任何守护进程运行。你只需在一台机器上安装它（可以轻松是一台笔记本电脑），即可从该中心点管理整个远程机器群。当 Ansible 管理远程机器时，不会在这些机器上留下已安装或正在运行的软件，因此升级到新版本时，完全不存在如何升级 Ansible 的问题。如果你想为项目做贡献，可以查看 [GitHub](https://github.com/ansible/ansible)。

## 设置 Ansible

要运行 Ansible，你需要一台运行任意版本 Unix 的机器，无论是 Red Hat、Debian、CentOS、macOS、Ubuntu 及其衍生版等。

目前不支持 Microsoft Windows。根据你的本地发行版，使用包管理器安装 ansible。Ansible 也可通过 Python pip 获取。

### Fedora

```bash
$ sudo dnf install ansible
```

### CentOS

```bash
$ sudo yum install ansible
```

### Ubuntu

```bash
$ sudo apt update && sudo apt install -y software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

### macOS 或其他系统上的本地单用户安装

```bash
$ pip install --user ansible
```

### macOS 或其他系统上的系统级安装

```bash
$ sudo pip install ansible
```

我们准备好了！当 Ansible 进行远程连接时，它将使用原生 SSH 服务，并假设你正在使用 SSH 密钥。始终建议使用 SSH 密钥而非纯密码认证。如果你已经有一台正在运行的服务器，但尚未设置免密认证，可以在本地机器上使用 `ssh-copy-id` 轻松复制你的公钥。

在下面的命令中替换服务器 IP 地址（如果你想为不同用户设置免密认证，也替换用户名）。

```bash
$ ssh-copy-id root@123.45.6.78
```



现在我们已经安装了 Ansible。我们需要一台全新的、未安装任何软件的服务器，以便自动化完成上一节中的手动流程。一旦我们从 Digital Ocean（或任何其他提供商，或本地服务器）启动一个新的 Droplet，就可以开始使用 Ansible 了。在本地机器上某个很酷的地方创建一个 ansible 目录。在我们的例子中，我们将使用 `~/devops`。

## Ansible 清单

Ansible 允许我们以[不同格式](https://docs.ansible.com/ansible/latest/plugins/inventory.html#inventory-plugins)列出服务器 IP 地址。让我们同时使用 INI 和 YAML 格式来解释它们的区别。在新目录中，创建两个新文件：`hosts` 和 `hosts.yml`；以保存所有服务器 IP 地址的[清单](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)。由于我们尚未为服务器设置其他用户，我们将使用 root 用户。我们还可以为每台服务器命名，并根据需要对它们进行分组。

```
$ cat hosts
### your server ip addresses
1.x.x.x
2.x.x.x

[databases]
3.y.y.y
4.y.y.y

[php]
server ansible_host=5.z.z.z
worker ansible_host=6.z.z.z ansible_port=8888
```

在上述 INI 文件中：

*   `x.x.x` 地址仅在 `all` 和 `ungrouped` 组中，
*   `y.y.y` 在 `databases` 组中，
*   `z.z.z` 在 `php` 组中。

这两个 PHP 服务器组有别名（`server` 和 `worker`），当你想明确针对这两台服务器中的任意一台时可以使用。`worker` 服务器还有一个自定义 SSH 端口 `8888`，必须使用 `ansible_port` 变量定义。

上述 INI 文件的 YAML 等效形式为：

```
$ cat hosts.yml
### your server ip addresses
all:
  hosts:
    1.x.x.x:
    2.x.x.x:
  children:
    databases:
      hosts:
        3.y.y.y:
        4.y.y.y:
    php:
      hosts:
        server:
          ansible_host: 5.z.z.z
        worker:
          ansible_host: 6.z.z.z
          ansible_port: 8888
```

对于 Ansible 主机，当主机不止一个时，每个列表项末尾的冒号是必需的，因此建议始终保留冒号，无论是否有多个主机。要测试我们的清单，请使用 ansible [ping 模块](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/ping_module.html) ping 任一列出的服务器：

```
$ ansible all -i hosts -m ping
$ ansible all -i hosts.yml -m ping
$ ansible databases -i hosts -m ping
$ ansible databases -i hosts.yml -m ping
$ ansible worker -i hosts -m ping
$ ansible worker -i hosts.yml -m ping
```

```
...
6.z.z.z | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

## YAML 基础

YAML 语法非常直观。在查看 playbook 之前，我们将先了解一些基础知识。

按照通用约定，Ansible 文件可以以 `---` 开头，以 `...` 结尾，表示文档的开始和结束。大多数文件只包含开始标记。注释由 `#` 字符定义。

列表在 Ansible 中非常常见，定义方式是使用 `-`（连字符）后跟一个空格。

```
---
- php
- vue
- react
```

字典是键值对，冒号后必须始终跟一个空格。

```
php:
  latest: 7.3
  Installed: 7.3
```

如果某行太长，可以使用字面块标量字符 `|`（管道符）或折叠块标量字符 `>`（大于号）进行换行。字面块标量字符将按输入原样渲染，包括换行符和任何额外空格；而折叠块标量字符会将换行符转换为空格。可以通过缩进行或添加额外空行来强制换行。

```
### Literal
exact_hello_world_template: |
  this is
  the
  hello world template

### same as:
### this is
the
wrapped
hello world template

### Folded
wrapped_hello_world_template: >
  this is
  the
  wrapped
  hello world template

### same as:
### this is the wrapped
hello world template
```

注意：如果你的字符串包含冒号或 `#`，你需要给它们加引号，因为当冒号后跟一个空格时（即 `John Doe: Look for him`），YAML 会期望一个映射。`#` 之后的任何内容都将被视为注释。

## Ansible Playbooks

Playbook 是 Ansible 的配置、部署和编排语言。它们可以描述你希望远程系统强制执行的策略，或通用 IT 流程中的一组步骤，在我们的例子中，就是我们希望如何设置服务器。

### Ansible Playbooks 和 Roles

每个 playbook 由 tasks（任务）组成，任务是在你选择的主机上执行的一组步骤。任务按照编写顺序针对选定的主机执行，一次执行一个任务。为了使我们的 playbook 可配置，我们必须在任务中使用变量。

这些变量可以在 Ansible Inventory 文件、play 中，甚至在 task 中定义。

当任务执行时，任务的名称会作为输出的一部分显示。因此，play 中的每个任务都应该有一个名称，即任务的简单易读描述。

我们可以按照任何喜欢的结构对任务进行分组。既然我们要设置 LEMP 服务器，我们可以有 php、mysql、nginx、common 和 acl 组。在 Ansible 中，这些组被称为 **roles（角色）**。**角色** 的优点在于它们是自包含的，因此可以在 playbook 之间轻松共享。

## 初始设置

万事俱备！在 `~/devops` 目录下，添加一个新的 `site.yml` 文件。这将是我们的 play 定义文件。接下来我们需要一个目录来存放所有的角色；创建 `roles` 目录。然后我们将使用 `ansible-galaxy` 来创建 5 个角色。

```
$ touch site.yml
$ mkdir roles
$ cd roles
$ ansible-galaxy init php
$ ansible-galaxy init mysql
$ ansible-galaxy init nginx
$ ansible-galaxy init common
$ ansible-galaxy init acl
```

首先，让我们给 Ansible 提供要使用的主机列表。按你喜欢的格式定义 Ansible Inventory。我倾向于使用 INI 格式：

```
123.45.6.78 ansible_user=root
```

> **注意：** 既然我们在服务器上使用 `root` 账户，就必须通过添加 `ansible_user=root` 参数显式指示 Ansible；否则，它将尝试使用本地用户账户连接并失败。

接下来，使用你喜欢的编辑器打开 `site.yml`。我倾向于使用安装了 YAML 和 Ansible 扩展的 Visual Studio Code。

> **注意：** 每个 playbook 由一个 plays 列表组成，每个 play 针对一个服务器列表（主机）执行。

我们要给出的第一个指令是 play 应该在其上执行的主机列表；目前用 `all` 即可。

```
---
- hosts: all
```

接下来我们将定义一个部分来保存 play 将要使用的变量。该部分由键 `vars` 定义，并且由于它是一个字典，其属性应从边距处缩进。

```
---
- hosts: all
  vars:
    KEY: sample value
```

我们现在可以通过添加一个 `ping` 任务来测试 playbook 是否设置正确，该任务的作用与运行 `ansible all -i hosts -m ping` 相同。

```
---
- hosts: all
  vars:
    KEY: sample value
  tasks:
    - name: Ping our awesome server
      ping:
        data: pong
```

打开终端并导航到 `~/devops` 目录，然后执行 playbook：

```
$ cd ~/devops
$ ansible-playbook -i ./hosts site.yml
```

```
PLAY [all] *************************************************************
TASK [Gathering Facts] *************************************************
ok: [123.45.6.78]
TASK [Ping our awesome server] *****************************************
ok: [123.45.6.78]
PLAY RECAP *************************************************************
123.45.6.78 : ok=2 changed=0 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
```

恭喜！你已经运行了第一个 playbook。回顾一下，playbook 的语法与 YAML hosts 文件相似。我们将对所有 playbook 信息（包括角色）使用 YAML。

移除刚才添加的 tasks，并用我们的 roles 替换它们。

根据你的设置，你可能需要在 playbook 中包含多个 play，每个 play 都有自己的主机集合。在我们的例子中，我们对所有服务使用一台通用服务器。

运行 play 时，我们将首先执行 `common` 角色，以便进行基本的服务器设置并执行系统升级。我们计划通过 unix socket 使用 PHP-FPM。unix socket 的路径取决于我们运行的 PHP 版本。如果我们选择 PHP 7.3，socket 将是 `unix:/run/php/php7.3-fpm.sock`，而 PHP 7.4 将给我们 `unix:/run/php/php7.4-fpm.sock`。socket 位置同时被 Nginx 和 PHP 使用。PHP 版本也决定了要安装的 PHP 模块。如果我们使用 PHP 7.3，就必须安装 `php7.3-*` 模块。鉴于所有这些原因，将 PHP 版本保存为变量非常合理。所以让我们把它作为第一个变量添加进去。

```
---
- name: Spinning up our LEMP server.
  hosts: all
  vars:
    php_version: "7.3"
  roles:
    - common
    - mysql
    - php
    - nginx
    - acl
```

当使用不同的主机时，你可以使用：

```
---
- name: Common Setup
  hosts: all
  roles:
    - common
    - security
    - ...
    - ...
- name: Spin up php
  hosts:
    - php
  vars:
    php_version: "7.3"
  roles:
    - php
```

## 角色结构

使用 `ansible-galaxy init role` 创建的每个角色都附带一组文件夹。并非所有文件夹都是必需的，但至少应存在 `tasks` 文件夹。以下是默认获得的文件夹：

*   **Defaults（默认值）** => 存储角色中使用的默认变量，以防变量未定义。
*   **Files（文件）** => 存放角色中使用的可部署文件。
*   **Handlers（处理器）** => 存放可在角色内部或外部使用的 handlers（事件监听器）。
*   **Meta（元数据）** => 定义角色将使用的一些元数据。
*   **Tasks（任务）** => 存放角色将执行的任务列表。
*   **Templates（模板）** => 包含可由角色编辑和部署的模板。
*   **Vars（变量）** => 包含角色使用的变量。

你可以在 Ansible 中触发事件，这些事件将由 `handlers` 目录中定义的监听器处理。我们所有的任务都将在 `tasks` 目录中定义和存储。

## Common 角色

打开位于 `common/tasks` 下的 `main.yml`。我们将使用此文件定义在 `site.yml` 中定义的每个主机上执行的所有通用任务。我们将添加一些“手动服务器设置”章节中没有的内容。我们将采取的步骤是：

1.  更新服务器
2.  设置无人值守升级
3.  安装额外软件包
4.  执行一些系统优化
5.  创建新用户；`deploy` 以处理我们的 CI/CD 部署
6.  设置防火墙。

我们将创建将被导入到 `main.yml` 文件中的子任务。拥有子任务使过程非常原子化，因此更易于管理。我们将创建子任务文件，然后将它们添加到 common 任务中。

```
$ cd ~/devops/roles/common/tasks
$ touch pre_setup.yml optimisations.yml users.yml security.yml
```

然后将创建的子任务导入主任务文件：

```
---
### tasks file for common role
- name: Pre-setup tasks
  import_tasks: pre_setup.yml
- name: Optimise system
  import_tasks: optimisations.yml
- name: Create additional users
  import_tasks: users.yml
- name: Boot firewall and configure SSH
  import_tasks: security.yml
```

## Pre-Setup 子任务

打开 `pre_setup.yml` 并使用 `apt` 模块来更新服务器、安装软件包和设置无人值守升级。对于无人值守升级，我们将使用模板、完整文件或 `lineinfile` 模块。`lineinfile` 模块可用于在文件中添加、编辑和删除行，如果文件不存在，它也可以创建文件。

首先，让我们更新 apt 缓存和任何过时的软件包。我们将 apt 缓存过期时间设置为 24 小时。由于 `apt` 模块以秒为单位接受 TTL，我们将使用 `86400`。

```
---
- name: Update the system
  apt:
    update_cache: yes
    cache_valid_time: 86400
    upgrade: 'dist'
```

萝卜青菜，各有所爱，因此需要变量！每台服务器都不同，有不同的软件包需求，无人值守升级软件包需要有不同的表现等。我们将为角色设置默认变量并将它们存储在 `defaults` 目录中。这些变量可以通过在 play 定义或 `vars` 目录中拥有同名变量来覆盖。

### 预设置与优化

我们肯定需要一些基础软件包已安装，且某些软件包可能使用 snap。因此，我们可以创建三个变量：一个用于存放 apt 软件包（`pre_setup_packages`），最后两个用于存放 snap 软件包（`pre_setup_snap` 和 `pre_setup_snap_classic`）。

[假设我们将使用 Let’s Encrypt](https://letsencrypt.org/) 和 Ubuntu 18.04，我们将需要添加 `ppa:certbot/certbot` 仓库。在我们的案例中，使用的是 Ubuntu 20.04，我们将使用 snap 来安装 certbot。

---

## common 的 defaults 文件



```yaml
pre_setup_snap:
pre_setup_snap_classic:
  - certbot
pre_setup_packages:
  - wget
  - curl
  - zsh
  - software-properties-common
  - build-essential
  - g++
  - gcc
  - git
  - vim
  - nscd
  - supervisor
  - unzip
  - acl
  - unattended-upgrades
  - ufw
```

切回到 `pre_setup` 子任务，并添加安装所需软件包的任务。

---

## pre_setup 任务

```yaml
- name: Update the system
  apt:
    update_cache: yes
    cache_valid_time: 86400
    upgrade: 'dist'

- name: Install packages
  apt:
    name: "{{ pre_setup_packages | default([], true) | list }}"
    state: latest

- name: Install Snap Packages
  snap:
    name: "{{ pre_setup_snap | default([], true) | list }}"
    state: present

- name: Install Classic Snap Packages
  snap:
    name: "{{ pre_setup_snap_classic | default([], true) | list }}"
    classic: true
    state: present
```

## 无人值守升级

无人值守升级仅使用已启用的来源运行。我们可以创建一个文件并将其存放在 `files` 目录下，或者使用变量来启用我们需要的来源。我们将采用后者。让我们在 `common/default/main.yml` 文件中添加一些默认变量。

```yaml
unattended_upgrades_security: true
unattended_upgrades_esm: true
unattended_upgrades_updates: true
unattended_upgrades_proposed: false
unattended_upgrades_backports: false
unattended_upgrades_blacklisted: []
unattended_upgrades_remove_dependencies: false
unattended_upgrades_auto_reboot: true,
unattended_upgrades_auto_reboot_time: "00:00"
unattended_upgrades_update_period: 1
unattended_upgrades_upgrade_period: 1
unattended_upgrades_auto_clean_period: 7
unattended_upgrades_unattended_upgrade_period: 1
```

请随意根据需要添加更多变量。复制 `/etc/apt/apt.conf.d/50unattended-upgrades` 并将其用作模板，保存为 `common/templates/50unattended-upgrades.j2`，然后将值替换为变量。

[Ansible 使用 Jinja 作为模板引擎。您可以在](https://jinja.palletsprojects.com) [文档站点](https://jinja.palletsprojects.com)上阅读更多相关信息。

```jinja
Unattended-Upgrade::Allowed-Origins {
  "${distro_id}:${distro_codename}";

  {% if unattended_upgrades_security %}
  "${distro_id}:${distro_codename}-security";
  {% endif %}

  {% if unattended_upgrades_esm %}
  "${distro_id}ESMApps:${distro_codename}-apps-security";
  "${distro_id}ESM:${distro_codename}-infra-security";
  {% endif %}

  {% if unattended_upgrades_updates %}
  "${distro_id}:${distro_codename}-updates";
  {% endif %}

  {% if unattended_upgrades_proposed %}
  "${distro_id}:${distro_codename}-proposed";
  {% endif %}

  {% if unattended_upgrades_backports %}
  "${distro_id}:${distro_codename}-backports";
  {% endif %}
};

Unattended-Upgrade::Package-Blacklist {
  {% for item in unattended_upgrades_blacklisted %}
  "{{ item }}";
  {% endfor %}
};

Unattended-Upgrade::MinimalSteps "true";
Unattended-Upgrade::InstallOnShutdown "false";
Unattended-Upgrade::Remove-Unused-Dependencies "{% if unattended_upgrades_remove_dependencies %}true{% else %}false{% endif %}";
Unattended-Upgrade::Automatic-Reboot "{% if unattended_upgrades_auto_reboot %}true{% else %}false{% endif %}";
Unattended-Upgrade::Automatic-Reboot-Time "{{ unattended_upgrades_auto_reboot_time }}";
```

在 `pre_setup.yml` 下创建一个任务，用于替换变量并将模板部署到服务器。如果 Ansible 任务编写得当，在已设置好的系统上重新运行它们不会破坏任何东西，只会简单地更新需要更改的内容。

```yaml
- name: Configure Unattended Upgrades
  template:
    dest: /etc/apt/apt.conf.d/50unattended-upgrades
    src: 50unattended-upgrades.j2
```

添加第二个模板：`common/templates/20auto-upgrades.j2`；内容如下。此文件决定自动升级的执行频率。

```jinja
APT::Periodic::Update-Package-Lists "{{ unattended_upgrades_update_period }}";
APT::Periodic::Download-Upgradeable-Packages "{{ unattended_upgrades_upgrade_period }}";
APT::Periodic::AutocleanInterval "{{ unattended_upgrades_auto_clean_period }}";
APT::Periodic::Unattended-Upgrade "{{ unattended_upgrades_unattended_upgrade_period }}";
```

剩下的就是设置将复制模板的任务：

```yaml
- name: Configure Unattended Upgrades Frequency
  template:
    dest: /etc/apt/apt.conf.d/20auto-upgrades
    src: 20auto-upgrades.j2
    owner: root
    group: root
    mode: 0644
```

完成了！我们成功创建了两个模板文件，添加了一些变量，并创建了将渲染模板并将其部署到服务器的任务。要运行 playbook，我们将使用与之前相同的命令：`$ ansible-playbook -i ./hosts site.yml`

以下是我们完整的预设置文件：

---

## 完整的 pre_setup 任务

```yaml
- name: Update the system
  apt:
    update_cache: yes
    cache_valid_time: 86400
    upgrade: 'dist'

- name: Install packages
  apt:
    name: "{{ pre_setup_packages | default([], true) | list }}"
    state: latest

- name: Install Snap Packages
  snap:
    name: "{{ pre_setup_snap | default([], true) | list }}"
    state: present

- name: Install Classic Snap Packages
  snap:
    name: "{{ pre_setup_snap_classic | default([], true) | list }}"
    classic: true
    state: present

- name: Configure Unattended Upgrades
  template:
    dest: /etc/apt/apt.conf.d/50unattended-upgrades
    src: 50unattended-upgrades.j2
    owner: root
    group: root
    mode: 0644

- name: Configure Unattended Upgrades Frequency
  template:
    dest: /etc/apt/apt.conf.d/20auto-upgrades
    src: 20auto-upgrades.j2
    owner: root
    group: root
    mode: 0644
```

## 优化子任务

根据我们的 `main.yml` 任务文件，队列中的下一项是优化（`optimisations.yml`）。为了充分发挥服务器的性能，我们需要增加一些默认值。`Somaxconn` 定义了接受新连接的内核队列大小。该值越低，最大并发用户数越低。

默认情况下，该值设置为 128，最大并发用户数为 128。我们将把该值设置为 100000。打开 `optimisations.yml` 并添加第一个任务：

```yaml
---
- name: Update the maximum concurrent connections
  sysctl:
    name: net.core.somaxconn
    value: "100000"
    state: present
```

`ip_local_port_range` 定义了可用和可用的端口，默认通常设置为 32768 - 61000。我们将扩大此范围，提供从端口 10000 到端口 65535。

```yaml
- name: Update available port range
  sysctl:
    name: net.ipv4.ip_local_port_range
    value: "1024 65535"
    state: present
```

TCP 协议提供了一种等待状态，它在连接关闭后保持套接字打开长达 4 分钟。这在繁忙的服务器上可能会有问题，因为它会耗尽套接字和端口。我们可以指示系统在安全时重用套接字，而无需等待 4 分钟过去。

```yaml
- name: Allow socket reuse
  sysctl:
    name: net.ipv4.tcp_tw_reuse
    value: 1
    reload: yes
    state: present
```

大多数开发者都遇到过每个进程允许的最大打开文件数的问题。默认值通常非常低；设置为 1024，这会导致问题，因为在任何 unix 系统上套接字本质上都是文件（例如

## 优化连接限制

由于 `/run/php/php7.4-fpm.sock` 的限制，最大并发连接数受到限制。经过计算，网关仅允许最大 512 个连接。这是因为每个客户端连接算作一个入站连接，随后会被转发到上游服务器，这又需要一个出站连接，因此每个客户端占用 2 个打开连接。我们必须调大该值，将软限制和硬限制均设置为 `999999`。

```yaml
- name: Set the soft and hard open file limits
  pam_limits:
    domain: "{{ item.domain }}"
    value: "999999"
    limit_item: nofile
    limit_type: "{{ item.type }}"
  with_items:
    - type: soft
      domain: "*"
    - type: hard
      domain: "*"
    - type: soft
      domain: root
    - type: hard
      domain: root
```

## 添加重启处理程序

添加第一个处理程序，用于监听需要系统重启的事件。在修改软硬文件限制后触发该事件。打开 `common/handlers/main.yml`：

```yaml
---
### handlers file for common
- name: reboot server
  reboot:
```

## 完整的优化任务文件

以下是完整的 `common/tasks/optimisations.yml` 文件：

```yaml
---
- name: Update the maximum concurrent connections
  sysctl:
    name: net.core.somaxconn
    value: "100000"
    state: present

- name: Update available port range
  sysctl:
    name: net.ipv4.ip_local_port_range
    value: "1024 65535"
    state: present

- name: Allow socket reuse
  sysctl:
    name: net.ipv4.tcp_tw_reuse
    value: 1
    reload: yes
    state: present

- name: Set the soft and hard open file limits
  pam_limits:
    domain: "{{ item.domain }}"
    value: "999999"
    limit_item: nofile
    limit_type: "{{ item.type }}"
  with_items:
    - type: soft
      domain: "*"
    - type: hard
      domain: "*"
    - type: soft
      domain: root
    - type: hard
      domain: root
  notify:
    - reboot server
```

## 用户子任务

为了克隆 Git 仓库，我们需要一个用户（当然不是 root）。我倾向于将用户命名为 `deploy`，但你可以创建任何喜欢的用户名。让我们在 `common/defaults/main.yml` 下添加一些默认变量，然后在 `common/tasks/users.yml` 中编写用户创建任务。

```yaml
deploy_user: "deploy"
deploy_user_generate_ssh_key: true
deploy_user_shell: "/bin/bash"
deploy_user_local_ssh_keys:
  - ~/.ssh/id_rsa.pub
deploy_user_groups:
  - www-data
```

> **注意**：由于该用户需要处理 Web 服务器文件，我们将其添加到 `www-data` 组。我们未实施用户隔离。如果你打算实施，请修改附加到 `deploy` 用户的组。

使用 Ansible `user` 模块创建新用户，并生成将被 CI/CD 流水线使用的 SSH 密钥对。我们还将使用 `authorized_key` 模块复制本地公钥以实现无密码登录。同时，我们希望允许 `deploy` 用户在从 GitLab 使用 CI/CD 流水线时以自己的身份登录。



```yaml
---
### tasks for users.yml
- name: Create the deploy user groups
  group:
    name: "{{ item }}"
    state: present
  loop: "{{ deploy_user_groups | default([], true) }}"

- name: Create the deploy user
  user:
    name: "{{ deploy_user }}"
    groups: "{{ (deploy_user_groups | default([], true) | join(',')) }}"
    generate_ssh_key: "{{ deploy_user_generate_ssh_key }}"
    shell: "{{ deploy_user_shell }}"
  register: created_user

- name: Add GitLab to known hosts
  lineinfile:
    dest: "/home/{{ deploy_user }}/.ssh/known_hosts"
    create: yes
    state: present
    line: "{{ lookup('pipe', 'ssh-keyscan -t rsa gitlab.com') }}"
    regexp: "^gitlab\\.com"
    mode: 0600

- name: Allow SSH key based logins
  authorized_key:
    user: "{{ deploy_user }}"
    key: "{{ lookup('file', item) }}"
    state: present
  loop: "{{ deploy_user_local_ssh_keys | default([], true) }}"

- name: Allow Deploy User to Login
  authorized_key:
    user: "{{ deploy_user }}"
    key: "{{ created_user['ssh_public_key'] }}"
    state: present
```

运行 Playbook 查看更改是否按预期应用。Playbook 运行后，尝试以创建的用户身份登录（在本例中为 `deploy` 用户）：`ssh deploy@123.45.6.78`。你应该能够成功无密码登录。

## 安全子任务

让我们加强服务器安全！首先我喜欢修改默认 SSH 端口。我们还安装了 UFW（简单防火墙）来过滤允许接受和丢弃的连接。

添加一些新的默认变量。`ufw_allow` 变量将包含要使用的端口和协议（tcp/udp），可包含任意数量的端口。

```yaml
ssh_port: "4033"
ufw_allow:
  - port: 80
    proto: tcp
  - port: 443
    proto: tcp
```

然后在 `common/tasks/security.yml` 中添加任务：

```yaml
---
### tasks for security
- name: Update the SSH port
  lineinfile:
    path: /etc/ssh/sshd_config
    regexp: "^#?Port "
    line: "Port {{ ssh_port }}"

- name: Allow SSH traffic through firewall
  ufw:
    rule: allow
    port: "{{ ssh_port }}"
    proto: tcp

- name: Allow traffic through firewall
  ufw:
    rule: allow
    port: "{{ item.port }}"
    proto: "{{ item.proto }}"
  loop: "{{ ufw_allow | default([], true) | list }}"

- name: Restart SSH
  service:
    name: ssh
    state: restarted

- name: Ensure we use the configured SSH port for the remainder of the role
  set_fact:
    ansible_port: "{{ ssh_port }}"

- name: Start UFW
  ufw:
    direction: incoming
    state: enabled
    policy: deny
```

你会注意到，我们在 `Ensure we use the configured SSH port for the remainder of the role` 任务下更新了 `ansible_port` 事实。这使得 Ansible 在我们将默认 SSH 端口更改为 `4033` 后，能继续执行该角色的其余部分。如果使用其他防火墙，请确保在更改端口前该端口已开放，否则任务将失败。

如果尝试使用默认 SSH 命令连接，除非指定端口，否则将失败。要以之前创建的 `deploy` 用户身份连接，请在 SSH 命令中添加 `-p 4033`。你也可以为此连接创建别名，或在本地 SSH 配置 `~/.ssh/config` 中添加主机：

```bash
$ ssh -p 4033 deploy@123.45.6.78

### 使用别名
$ echo 'alias devops="ssh -p 4033 deploy@123.45.6.78"' >> ~/.bashrc
$ source ~/.bashrc
$ devops # 这将调用上述别名

### 使用 ssh config
$ vi ~/.ssh/config
Host devops
  Hostname 123.45.6.78
  Port 4033
  User deploy
$ ssh devops # 这将使用 devops 配置
```

> **注意**：如果你在每次更改后运行 Playbook，需要将 `ansible_port` 变量添加到 Ansible 清单主机文件中，待整个 Playbook 完成后再将其移除，以便新服务器获得正确配置。

使用 INI 格式：

```ini
123.45.6.78 ansible_user=root ansible_port=4033
```

`common` 角色完成！

## MySQL 角色

### Percona 子任务

在 `mysql` 角色目录下，创建一个新的 `percona.yml` 文件并放入 `tasks` 目录，用于存放 Percona 的准备和安装任务。我们还将添加一些 Python 库，以便 Ansible 能连接到数据库。

```yaml
---
- name: Setup Percona Repository
  apt:
    deb: "https://repo.percona.com/apt/percona-release_latest.{{ ansible_distribution_release }}_all.deb"

- name: Enable Percona 8 Repository
  command: percona-release setup ps80

- name: Install Percona Server
  apt:
    name: percona-server-server
    state: latest
    update_cache: yes

- name: Determine required MySQL Python libraries
  set_fact:
    mysql_python_package: "{% if ansible_python.version.major == 3 %}python3-pymysql{% else %}python-pymysql{% endif %}"

- name: Ensure MySQL Python libraries are installed
  apt:
    name: "{{ mysql_python_package }}"
    state: latest
```

我们还将添加一个处理程序（`mysql/handlers/main.yml`），用于重启 MySQL 服务器。

```yaml
---
### mysql/handlers/main.yml
- name: restart mysql
  service:
    name: mysql
    state: restarted
```

### 配置子任务

### 创建 MySQL 配置文件

在 `mysql/tasks` 下创建一个新的任务文件 `configure.yml`，在 `mysql/templates` 下创建一个新的模板文件 `my.cnf.j2`。该模板将用于修改 Percona 自带的默认 `my.cnf` 文件。

### `templates/my.cnf.j2`

```
[mysqld]
default-authentication-plugin={{ default_authentication_plugin }}

### 禁用符号链接以防止各种安全风险
symbolic-links = 0

### 内存设置。
max_allowed_packet = {{ mysql_max_allowed_packet }}
sort_buffer_size = {{ mysql_sort_buffer_size }}
read_buffer_size = {{ mysql_read_buffer_size }}
key_buffer_size = {{ mysql_key_buffer_size }}
myisam_sort_buffer_size = {{ mysql_myisam_sort_buffer_size }}
read_rnd_buffer_size = {{ mysql_read_rnd_buffer_size }}
table_open_cache = {{ mysql_table_open_cache }}
max_connections = {{ mysql_max_connections }}
group_concat_max_len = {{ mysql_group_concat_max_len }}
thread_cache_size = {{ mysql_thread_cache_size }}
join_buffer_size = {{ mysql_join_buffer_size }}
tmp_table_size = {{ mysql_tmp_table_size }}
max_heap_table_size = {{ mysql_max_heap_table_size }}

### InnoDB 设置。
innodb_file_per_table = {{ mysql_innodb_file_per_table }}
innodb_buffer_pool_size = {{ mysql_innodb_buffer_pool_size }}
innodb_log_file_size = {{ mysql_innodb_log_file_size }}
innodb_log_buffer_size = {{ mysql_innodb_log_buffer_size }}
innodb_flush_log_at_trx_commit = {{ mysql_innodb_flush_log_at_trx_commit }}
innodb_lock_wait_timeout = {{ mysql_innodb_lock_wait_timeout }}

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/
```

我们还将为约 512MB 内存的服务器添加一些默认值。

编辑 `mysql/defaults/main.yml` 并添加以下变量。

### `defaults/main.yml`

```yaml
---
### mysql 的默认文件
### caching_sha2_password 是默认值，但大多数客户端不支持它
default_authentication_plugin: "mysql_native_password"

mysql_max_allowed_packet: "64M"
mysql_sort_buffer_size: "1M"
mysql_read_buffer_size: "1M"
mysql_key_buffer_size: "256M"
mysql_myisam_sort_buffer_size: "64M"
mysql_read_rnd_buffer_size: "4M"
mysql_table_open_cache: "256"
mysql_max_connections: "151"
mysql_group_concat_max_len: "1024"
mysql_thread_cache_size: "8"
mysql_join_buffer_size: "262144"
mysql_tmp_table_size: "16M"
mysql_max_heap_table_size: "16M"
mysql_innodb_file_per_table: "1"
mysql_innodb_buffer_pool_size: "256M"
mysql_innodb_log_file_size: "64M"
mysql_innodb_log_buffer_size: "8M"
mysql_innodb_flush_log_at_trx_commit: "1"
mysql_innodb_lock_wait_timeout: "50"
mysql_root_password: "t00r"
mysql_grant_users:
  - name: "devops"
    password: "devops"
    host: "localhost"
    privileges: "*.*:All" # '*.*:ALL,GRANT' 会生成一个 "root" 用户
```

现在我们可以将模板文件复制到服务器上并替换现有文件。配置完成后，我们将使用之前创建的处理程序重启 MySQL 服务器。我们还将确保 MySQL 在系统启动时自动启动。

我们还将创建额外的 MySQL 用户，并赋予他们所需的权限。根据需要在 `mysql_grant_users` 变量下添加任意数量的用户。同时通过角色变量为 root 设置一个合理的密码。最后，我们将执行安全安装，并移除测试数据库和匿名用户。

### `mysql/tasks/configure.yml`



## MySQL 角色

### 配置子任务

#### `mysql/tasks/configure.yml`

```yaml
---
- name: Update MySQL Configuration
  template:
    src: my.cnf.j2
    dest: /etc/mysql/my.cnf
    owner: root
    group: root
    mode: "0644"
    force: true
  notify: restart mysql

- name: Enable MySQL on boot
  service:
    name: mysql
    state: started
    enabled: true

- name: Disallow remote root login
  command: 'mysql -NBe "{{ item }}"'
  with_items:
    - DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost', '127.0.0.1', '::1')
  changed_when: false

- name: Get defined hosts for root
  command: mysql -NBe "SELECT Host FROM mysql.user WHERE User = 'root' ORDER BY (Host='localhost') ASC"
  register: mysql_hosts
  changed_when: false
  check_mode: false

- name: Update MySQL root password
  shell: mysql -u root -NBe 'ALTER USER "root"@"{{ item }}" IDENTIFIED WITH mysql_native_password BY "{{ mysql_root_password }}";'
  with_items: "{{ mysql_hosts.stdout_lines | default([]) }}"

- name: Set MySQL root configuration
  template:
    src: "root-my.cnf.j2"
    dest: "/root/.my.cnf"
    owner: root
    group: root
    mode: "0600"
    force: true

- name: Create additional users
  mysql_user:
    name: "{{ item.name }}"
    host: "{{ item.host }}"
    password: "{{ item.password }}"
    priv: "{{ item.privileges }}"
    state: present
  loop: "{{ mysql_grant_users | default([]) }}"
  no_log: true

- name: Get defined hosts for the anonymous user
  command: mysql -NBe 'SELECT Host FROM mysql.user WHERE User = ""'
  register: mysql_anonymous_hosts
  changed_when: false
  check_mode: false

- name: Remove anonymous MySQL users
  mysql_user:
    name: ""
    host: "{{ item }}"
    state: absent
  with_items: "{{ mysql_anonymous_hosts.stdout_lines | default([]) }}"

- name: Remove MySQL test database
  mysql_db:
    name: test
    state: absent
  notify: restart mysql
```

上述任务引用了一个 `root-my.cnf.j2` 模板文件，用于存储 root MySQL 用户的凭据。请在 `templates` 下创建该文件，并使用以下内容。

#### `templates/root-my.cnf.j2`

```ini
[client]
user="root"
password="{{ mysql_root_password }}"
```

### 主任务文件

剩下的就是将这两个子任务包含到 `mysql/tasks/main.yml` 中。

#### `mysql/tasks/main.yml`

```yaml
---
### tasks file for mysql
- name: Handle Percona Installation
  import_tasks: percona.yml

- name: Configure the database engine
  import_tasks: configure.yml
```

这应该能搞定我们的 MySQL 服务器。你应该能够使用设置的密码登录 MySQL，其他创建的用户也应该能够登录。

## PHP 角色

设置 PHP 通常很简单。由于我们使用的是 PHP 7.4，我们可以选择使用 Debian 维护的版本或 Ondrej 的 PPA，但既然很多人喜欢拥有灵活性，我们就使用后者。我们将设置 PHP、[Composer](https://getcomposer.org/) 并配置诸如 `opcache` 之类的模块。

### 安装子任务

添加一个新的子任务 `installs.yml`，用于存放 PHP 和其他所需二进制文件的安装。我们将从源码编译一些模块，如 `redis`。要安装的包列表将在 `php/defaults/main.yml` 中定义。

#### `php/defaults/main.yml`

```yaml
---
### defaults file for php
php_version: "7.4"
php_packages:
  - php-pear
  - "php{{ php_version }}"
  - "php{{ php_version }}-cli"
  - "php{{ php_version }}-common"
  - "php{{ php_version }}-curl"
  - "php{{ php_version }}-dev"
  - "php{{ php_version }}-gd"
  - "php{{ php_version }}-json"
  - "php{{ php_version }}-mysql"
  - "php{{ php_version }}-opcache"
  - "php{{ php_version }}-readline"
  - "php{{ php_version }}-sqlite3"
  - "php{{ php_version }}-xml"
  - "php{{ php_version }}-bcmath"
  - "php{{ php_version }}-bz2"
  - "php{{ php_version }}-fpm"
  - "php{{ php_version }}-intl"
  - "php{{ php_version }}-mbstring"
  - "php{{ php_version }}-soap"
  - "php{{ php_version }}-xsl"
  - "php{{ php_version }}-zip"
  - "php{{ php_version }}-imagick"
  - imagemagick
  - libmcrypt-dev
php_pecl_install:
  - mcrypt
  - redis
```

更改 playbook 中的 `php_version`（在 `site.yml` 中定义）也将改变将要安装的模块，因为我们在所有模块中都使用该变量作为引用。你可以根据需要添加任意数量的包。每个项目都有其自身所需的扩展规格。如果不需要图像处理，可以移除 `imagick` 等图像处理扩展。

有两个额外的包来自 PECL。在我们的例子中是 `mcrypt` 和 `redis`。更新 `php/tasks/installs.yml` 子任务并添加：

#### `php/tasks/installs.yml`

```yaml
---
- name: Add Ondrej PPA
  apt_repository:
    repo: ppa:ondrej/php
    state: present
    update_cache: yes
    mode: "0666"
```

#### 安装 PHP 包

```yaml
- name: Install PHP packages
  apt:
    name: "{{ php_packages | default([]) }}"
    state: latest
```

#### 更新 PECL 协议

```yaml
- name: Update PECL protocols
  shell: pecl channel-update pecl.php.net
```

#### 安装 PECL 包

```yaml
- name: Install PECL Packages
  shell: yes '' | pecl install -s --force {{ item }}
  loop: "{{ php_pecl_install }}"
```

按照 [Composer 官方文档](https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md) 中的程序化安装方法，创建一个新脚本并保存为 `files/install_composer.sh`。我们将执行该脚本并注册输出，以此判断安装是否成功。若成功，则将生成的 `composer.phar` 文件移动至 `/usr/local/bin/composer`。

#### `files/install_composer.sh`

```bash
#!/bin/sh

EXPECTED_CHECKSUM="$(wget -q -O - https://composer.github.io/installer.sig)"

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

ACTUAL_CHECKSUM="$(php -r "echo hash_file('sha384', 'composer-setup.php');")"

if [ "$EXPECTED_CHECKSUM" != "$ACTUAL_CHECKSUM" ]
then
    >&2 echo 'ERROR: Invalid installer checksum'
    rm composer-setup.php
    exit 1
fi

php composer-setup.php --quiet

RESULT=$?

rm composer-setup.php

exit $RESULT
```

现在更新安装子任务，并添加 Composer 安装任务。

```yaml
- name: Install Composer
  script: files/install_composer.sh
  register: composer_install_status

- name: Install Composer globally
  command: mv composer.phar /usr/local/bin/composer
  when: composer_install_status.changed
```

### 配置子任务

接下来，通过创建 `php/tasks/configure.yml` 并添加额外的默认变量来配置安装。在 Debian/Ubuntu 系统中，PHP 配置文件通常符号链接到 `mods-available` 文件夹，因此我们将在该文件夹中创建配置，并将其符号链接到 `cli` 和 `fpm` 目录。在 `php/defaults/main.yml` 中添加用于生成自定义配置的默认变量及配置存储目录。

```yaml
php_common_conf_directory: /etc/php/{{ php_version }}/mods-available
php_conf_directories:
  - /etc/php/{{ php_version }}/cli/conf.d
  - /etc/php/{{ php_version }}/fpm/conf.d

php_register_modules:
  - name: mcrypt
    priority: 20
  - name: redis
    priority: 20
```

在上述默认变量中，我们添加了通用的 `mods-available` 目录和两个配置目录，它们均依赖于 PHP 版本。我们想要注册的模块列在 `php_register_modules` 下。`priority` 用于生成文件名（格式为 `priority-name.ini`，例如 `20-mcrypt.ini`），并决定模块的加载顺序。

接着，创建存储于 `mods-available` 文件夹中的文件模板，保存为 `templates/module.ini.j2`。

#### `templates/module.ini.j2`

```ini
; configuration for php {{ item.name }} module
; priority={{ item.priority }}
extension={{ item.name }}.so
```

为稳妥起见，添加任务以确认 PHP 自定义配置目录确实存在。

#### `php/tasks/configure.yml`

```yaml
---
### php/tasks/configure.yml
- name: Ensure common configuration directory exist
  file:
    path: "{{ php_common_conf_directory }}"
    state: directory
    follow: true

- name: Ensure configuration directories exist
  file:
    path: "{{ item }}"
    state: directory
    follow: true
  loop: "{{ php_conf_directories }}"
```

随后，复制配置文件。首先配置默认文件中 `php_register_modules` 列出的两个已安装模块。将以下两个任务追加到 `configure.yml` 子任务中。

```yaml
- name: Add modules configs
  template:
    dest: "{{ php_common_conf_directory }}/{{ item.name }}.ini"
    src: module.ini.j2
    owner: root
    group: root
    mode: 0644
  loop: "{{ php_register_modules }}"

- name: Enable modules
  file:
    src: "{{ php_common_conf_directory }}/{{ item.1.name }}.ini"
    dest: "{{ item.0 }}/{{ item.1.priority }}-{{ item.1.name }}.ini"
    state: link
    force: yes
  loop: "{{ php_conf_directories | product(php_register_modules) | list }}"
```

现在通过配置 Opcache 来提升 PHP 性能。添加一些 Opcache 默认变量，供 `opcache.ini.j2` 模板文件使用。

```yaml
opcache_enable: "1"
opcache_enable_cli: "1"
opcache_memory_consumption: "512"
opcache_string_buffer: "64"
opcache_accelerated_files: "30000"
opcache_validate_timestamps: "0"
opcache_fast_shutdown: "1"
opcache_save_comments: "1"
```

建议启用 Opcache，因为它通过将预编译的脚本字节码存储在共享内存中来提高 PHP 性能，从而消除了 PHP 在每次请求时加载和解析脚本的需要。一旦文件被读取并编译，它就会被存储在内存中，后续所有请求都无需再次读取该文件。

> **注意**：禁用 `validate_timestamps` 选项时，每次新部署都需要重启 PHP-FPM，以便刷新预编译脚本。

现在创建 `opcache.ini.j2` 模板：



此模板将替换 `mods-available` 目录下的 `opcache.ini` 文件。该文件会自动符号链接到 `cli` 和 `fpm` 目录，其余工作自动完成。

```ini
zend_extension=opcache.so

[opcache]
opcache.enable={{ opcache_enable }}
opcache.enable_cli={{ opcache_enable_cli }}
opcache.memory_consumption={{ opcache_memory_consumption }}
opcache.interned_strings_buffer={{ opcache_string_buffer }}
opcache.max_accelerated_files={{ opcache_accelerated_files }}
opcache.validate_timestamps={{ opcache_validate_timestamps }}
opcache.fast_shutdown={{ opcache_fast_shutdown }}
opcache.save_comments = {{ opcache_save_comments }}
```

```yaml
- name: Setup Opcache
  template:
    dest: "{{ php_common_conf_directory }}/opcache.ini"
    src: opcache.ini.j2
    owner: root
    group: root
    mode: 0644
```

接下来，设置 PHP-FPM 池。默认通常是 `www` 池。

创建新模板文件 `www.conf.j2`，并添加以下池定义：

```ini
[www]
user = {{ php_fpm_user }}
group = {{ php_fpm_group }}
listen = /run/php/php{{ php_version }}-fpm.sock
listen.owner = {{ php_fpm_user }}
listen.group = {{ php_fpm_group }}
pm = dynamic
pm.max_children = {{ php_pm_max_children }}
pm.start_servers = {{ php_pm_start_servers }}
pm.min_spare_servers = {{ php_pm_min_spare_servers }}
pm.max_spare_servers = {{ php_pm_max_spare_servers }}
pm.max_requests = {{ php_pm_max_requests }}
{% if php_pm_enable_stats %}
pm.status_path = {{ php_pm_status_path }}
{% endif %}
{% if php_pm_enable_monitoring %}
ping.path = {{ php_pm_ping_path }}
ping.response = {{ php_pm_ping_response }}
{% endif %}
```

此池配置文件将根据服务器需求填充。如果服务器资源不足以处理 100 个子进程，将 `pm.max_children` 设为 100 将毫无意义！每个子进程通常消耗 20-60 MB 内存。以运行 MySQL（约 1 GB 内存）及系统资源和其他服务（约 0.5 GB）的 4 GB 服务器为例，剩余约 2.5 GB 内存。最大进程数可估算为 2560/60 ≈ 42.6，取整为 40。

即使我们使用 8 GB 内存的服务器，但系统负载不高，因此将最大进程数变量设为 50。更新 `php/defaults/main.yml` 文件，添加以下变量。

```yaml
php_fpm_user: "www-data"
php_fpm_group: "www-data"
php_pm_max_children: "50"
php_pm_start_servers: "3"
php_pm_min_spare_servers: "1"
php_pm_max_spare_servers: "5"
php_pm_max_requests: "500"
php_pm_enable_stats: true
php_pm_status_path: "/php_status"
php_pm_enable_monitoring: true
php_pm_ping_path: "/php_ping"
php_pm_ping_response: "pong"
```

> **注意**：若要实现用户隔离，请将 FPM 用户设置为你创建的用户（本例中为 `deploy`）。

现在可以添加任务来处理模板部署，并设置 FPM 开机自启。将以下两个任务追加到 `configure.yml` 子任务中。

```yaml
- name: Setup the default pool
  template:
    dest: "/etc/php/{{ php_version }}/fpm/pool.d/www.conf"
    src: www.conf.j2
    owner: root
    group: root
    mode: 0644

- name: Enable PHP-FPM on boot
  service:
    name: "php{{ php_version }}-fpm"
    state: started
    enabled: true
```

PHP 的配置到此结束。只剩两件事：一个用于在所有任务完成后重启 PHP 的处理器，以及将子任务添加到主任务中。处理器将监听 `restart php-fpm` 事件，然后为我们处理重启。编辑 `php/handlers/main.yml`：

```yaml
---
### handlers file for php
- name: restart php-fpm
  service:
    name: "php{{ php_version }}-fpm"
    state: restarted
```

最后，更新我们的 `php/tasks/main.yml` 任务文件并添加子任务。请记住，在配置子任务完成后重启 PHP-FPM：

```yaml
---
### tasks file for php
- name: Install PHP
  import_tasks: installs.yml
- name: Configure PHP
  import_tasks: configure.yml
  notify: restart php-fpm
```

## Nginx 角色

[Nginx 可作为发行版软件包获得，也可以通过官方 PPA 安装](https://www.nginx.com/)。发行版软件包并不总是最新的，所以让我们使用 PPA。我们将有两个子任务，一个用于安装，另一个用于配置 Nginx。我提供了一个经过优化的 `nginx.conf` 文件，以及一个带有一些额外优化的示例默认服务器块。

为了设置 `worker_processes` 配置值，我们将使用当前服务器可用的核心数。如果该变量未定义，该值将被提取并保存在 `nginx_worker_processes` 变量中。如果您想使用自己的值并禁用自动计算，请将 `nginx_worker_processes` 变量添加到 playbook 变量中并为其赋值。

那么让我们开始吧！创建两个子任务：`installs.yml` 和 `configure.yml`；并将它们添加到 nginx 的 main.yml 任务文件中。

```yaml
---
### tasks file for nginx
- name: Install nginx
  import_tasks: installs.yml
- name: Configure Nginx
  import_tasks: configure.yml
```

### 安装子任务

我们现在可以打开 `nginx/tasks/installs.yml` 并添加官方 Nginx PPA，安装它并设置为在系统启动时运行。

```yaml
---
- name: Add Nginx PPA.
  apt_repository:
    repo: 'ppa:nginx/stable'
    state: present
    update_cache: true
    mode: 0666

- name: Remove Apache if present
  apt:
    name: apache2
    state: absent

- name: Install Nginx
  apt:
    name: nginx
    state: latest

- name: Enable Nginx on boot
  service:
    name: nginx
    state: started
    enabled: true
```

我们的安装子任务到此完成！很快吧？

### 配置子任务

接下来，我们打开 `nginx/tasks/configure.yml` 文件，设置 worker 进程自动计算任务，仅在 `nginx_worker_processes` 变量未定义时运行。

```yaml
---
- name: Check the available processor cores
  shell: grep processor /proc/cpuinfo | wc -l
  register: nginx_core_number
  when: nginx_worker_processes is not defined

- name: Set the nginx_worker_processes variable
  set_fact:
    nginx_worker_processes: "{{ nginx_core_number.stdout_lines[0] }}"
  when: nginx_worker_processes is not defined
```

我们现在可以将 `nginx.conf` 模板文件添加到 `templates/nginx.conf.j2` 下。

```nginx
user {{ nginx_user }};
worker_processes {{ nginx_worker_processes }};
pid /var/run/nginx.pid;
error_log /var/log/nginx/error.log {{ nginx_error_level }};
events {
  worker_connections {{ nginx_worker_connections }};
}
http {
  include /etc/nginx/mime.types;
  default_type application/octet-stream;
  log_format main_ext '$remote_addr - $remote_user [$time_local] "$request" '
    '$status $body_bytes_sent "$http_referer" '
    '"$http_user_agent" "$http_x_forwarded_for" '
    '"$host" sn="$server_name" '
    'rt=$request_time '
    'ua="$upstream_addr" us="$upstream_status" '
    'ut="$upstream_response_time" ul="$upstream_response_length" '
    'cs=$upstream_cache_status';
  access_log /var/log/nginx/access.log main_ext;
  sendfile on;
  tcp_nopush on;
  tcp_nodelay on;
  keepalive_timeout {{ nginx_keepalive_timeout }};
  types_hash_max_size {{ nginx_types_hash_max_size }};
  # allow the server to close connection on non responding client,
  # this will free up memory
  reset_timedout_connection on;
  ##
  # Client Settings
  ##
  client_body_timeout {{ nginx_client_body_timeout }};
  client_header_timeout {{ nginx_client_header_timeout }};
  client_body_buffer_size {{ nginx_client_body_buffer_size }};
  client_header_buffer_size {{ nginx_client_header_buffer_size }};
  client_max_body_size {{ nginx_client_max_body_size }};
  large_client_header_buffers {{ nginx_large_client_header_buffers }};
  {% if nginx_enable_gzip %}
  ##
  # Gzip Settings
  ##
  gzip on;
  gzip_disable "msie6";
  gzip_vary on;
  gzip_proxied any;
  gzip_comp_level 6;
  gzip_min_length 1000;
  gzip_buffers 16 8k;
  gzip_http_version 1.1;
  gzip_types application/atom+xml application/javascript application/json application/ld+json application/manifest+json application/rdf+xml application/rss+xml application/schema+json application/vnd.geo+json application/vnd.ms-fontobject application/x-font-ttf application/x-javascript application/x-web-app-manifest+json application/xhtml+xml application/xml font/collection font/eot font/opentype font/otf font/ttf image/bmp image/svg+xml image/vnd.microsoft.icon image/x-icon text/cache-manifest text/calendar text/css text/javascript text/plain text/markdown text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy text/xml;
  {% endif %}
  ##
  # Server Settings
  ##
  server_tokens off; # don't send the version number in error pages and headers
  include /etc/nginx/conf.d/*.conf;
  include /etc/nginx/sites-enabled/*;
}
```

太棒了！上述配置禁用了 server tokens，以便我们保持 Nginx 详情的私密性，并启用了超时连接的重置，以便我们能尽可能多地重用内存。让我们将配置要用到的变量添加到 `nginx/defaults/main.yml` 文件中。

```yaml
---
### defaults file for nginx
nginx_user: "www-data"
nginx_error_level: "warn"
nginx_worker_connections: "2048"
nginx_keepalive_timeout: "65"
nginx_types_hash_max_size: "2048"
nginx_client_body_timeout: "12"
nginx_client_header_timeout: "12"
nginx_client_body_buffer_size: "10k"
nginx_client_header_buffer_size: "1k"
nginx_client_max_body_size: "8m"
nginx_large_client_header_buffers: "4 32k"
nginx_enable_gzip: true
```

如前所述，如果您想设置 `worker_processes`，您需要编辑 `sites.yml` 文件并按如下方式添加 `nginx_worker_processes` 变量：

```yaml
---
- name: Spinning up our LEMP server.
  hosts: all
  vars:
    nginx_worker_processes: "auto"
  roles:
    - common
    - mysql
    - php
    - nginx
```



我们现在可以向 `nginx/tasks/configure.yml` 文件添加任务，这些任务将验证两个配置和日志目录是否存在，并在缺失时处理创建（`/etc/nginx/conf.d`、`/etc/nginx/sites-enabled` 和 `/var/log/nginx`）。另一个任务将处理部署我们自定义的 `nginx.conf` 模板。

```yaml
- name: Validate the config directories exist
  file:
    path: "{{ item }}"
    state: directory
    owner: root
    group: root
  loop:
    - /etc/nginx/conf.d
    - /etc/nginx/sites-enabled

- name: Validate the log directory exist
  file:
    path: /var/log/nginx
    state: directory
    owner: root
    group: adm

- name: Deploy custom nginx.conf
  template:
    dest: /etc/nginx/nginx.conf
    src: nginx.conf.j2
    owner: root
    group: root
    mode: 0644
```

注意：如果使用用户隔离，请设置 `nginx_user` 和

## Nginx 配置与 SSL 安全加固

### 生成 Diffie-Hellman 参数

进入 `/var/log/nginx` 目录以匹配创建的用户账户。

为了通过 HTTPS 提供站点服务并增强加密强度，我们需要添加一些配置。首先，让我们生成 4096 位素数字段的安全 **Diffie-Hellman (DH)** 参数。此过程耗时取决于服务器资源。

在 `nginx/defaults/mail.yml` 文件中指定保存文件的位置：

```yaml
### defaults/main.yml
nginx_dhparam_location: "/etc/ssl/certs/dhparam.pem"
```

在 `nginx/tasks/configure.yml` 中添加生成任务：

```yaml
- name: Generate 4096 bit DH Params
  community.crypto.openssl_dhparam:
    path: "{{ nginx_dhparam_location }}"
    size: 4096
    mode: 0666
```

上述任务使用了 `community.crypto.openssl_dhparam` 模块，这是一个社区模块，不在默认 Ansible 模块中。我们需要安装 **Community Crypto Collection**（包含许多其他实用工具）：

```bash
$ ansible-galaxy collection install community.crypto
```

### 配置 SSL 参数模板

添加 `nginx/templates/ssl-params.conf.j2` 模板，用于配置 SSL 参数。此文件应包含在每个使用 HTTPS 的 `server` 块中。

```nginx
### Use per block. ssl-params

ssl_protocols TLSv1.2 TLSv1.3;
ssl_prefer_server_ciphers on;
ssl_ciphers "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH";
ssl_ecdh_curve secp384r1;
ssl_session_timeout 60m;
ssl_session_cache shared:SSL:10m;
ssl_session_tickets off;
ssl_stapling on;
ssl_stapling_verify on;
resolver {{ nginx_dns_ip_1 }} {{ nginx_dns_ip_2 }} valid=300s;
resolver_timeout 5s;

{% if nginx_enable_strict_transport_security_header %}
add_header Strict-Transport-Security "max-age={{ nginx_hsts_max_age }}{% if nginx_hsts_include_subdomains %};includeSubdomains{% endif %}{% if nginx_hsts_preload %};preload{% endif %}";
{% endif %}

{% for option in nginx_xframe_options %}
add_header X-Frame-Options {{ option }};
{% endfor %}

add_header X-Content-Type-Options nosniff;
add_header X-Robots-Tag {{ nginx_x_robots_tag }};
ssl_dhparam {{ nginx_dhparam_location }};
```

配套的默认变量如下：

```yaml
nginx_dns_ip_1: "8.8.8.8"
nginx_dns_ip_2: "8.8.4.4"
nginx_enable_strict_transport_security_header: true
nginx_hsts_max_age: "63072000"
nginx_hsts_preload: false
nginx_hsts_include_subdomains: true
nginx_xframe_options:
  - "SAMEORIGIN"
nginx_x_robots_tag: "none" # https://developers.google.com/search/reference/robots_meta_tag
```

### SSL 配置说明

查看 `ssl-params.conf.j2` 文件，我们设置了一些 Nginx 参数：

- 仅保留 TLS 1.2 和 TLS 1.3 协议，其它协议被认为不安全。
- 启用的 `ssl_ciphers` 被公认为最佳配置，详情请参考 [Mozilla Foundation](https://wiki.mozilla.org/Security/Server_Side_TLS)。
- `ssl_dhparam` 和 `ssl_ecdh_curve` 用于前向保密：客户端和服务器协商一个特定于连接的预主密钥，仅在有限时间内使用，会话结束即销毁（因此称为 Ephemeral）。我们使用这些选项指示 Nginx 使用生成的 DH 参数进行 DHE 密钥交换。
- 通过 **HTTP Strict Transport Security (HSTS)** 头指示现代浏览器仅通过 HTTPS 通信；若 HTTPS 不可用则拒绝连接，保障客户端安全。详见 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)。
- **X-Frame-Options** 头指导浏览器如何在 `<frame>`、`<iframe>`、`<embed>` 和 `<object>` 标签中展示站点，可有效防范 [Clickjacking](https://en.wikipedia.org/wiki/Clickjacking)。详见 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)。
- **X-Content-Type-Options** 头指示客户端服务器设置的 MIME 类型为准，不得更改。详见 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options)。

### 部署 SSL 片段

编辑 `nginx/tasks/configure.yml`，追加以下任务以创建 snippets 目录并部署模板：

```yaml
- name: Validate the snippets directory exist
  file:
    path: /etc/nginx/snippets
    state: directory
    owner: root
    group: root

- name: Deploy the ssl-snippet
  template:
    dest: /etc/nginx/snippets/ssl-params.conf
    src: ssl-params.conf.j2
    owner: root
    group: root
    mode: 0644
```

### 默认 Server 块模板

启用 HTTPS 时，默认 server 块将引用上述 SSL 片段及证书路径片段。由于暂未配置域名和 SSL 证书，请创建 `nginx/templates/ssl-default.conf.j2` 并根据实际情况更新：

```nginx
ssl_certificate /etc/letsencrypt/live/domain.example.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/domain.example.com/privkey.pem;
```

默认 server 块还包含两个额外的 `location` 块，用于监控 PHP 和 Nginx 状态：

1. **PHP status/ping**：将请求转发给 PHP-FPM，输出 FPM 池状态并提供健康检查 ping 响应。
2. **Nginx status**：提供 Nginx 状态指标。

这两个块在需要采集服务器指标时非常有用。

### 默认变量

在 `nginx/defaults/main.yml` 中添加：

```yaml
nginx_default_server_root: "/var/www/app/current/public"
nginx_default_server_name: "_"
nginx_default_enable_https: false
```

### 默认 Server 块模板文件 `nginx/templates/default.j2`

```nginx
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    {% if nginx_default_enable_https %}
    listen 443 ssl http2 default_server;
    listen [::]:443 ssl http2 default_server;
    include snippets/ssl-params.conf;
    include snippets/ssl-default.conf;
    {% endif %}

    root {{ nginx_default_server_root }};
    index index.php index.html index.htm index.nginx-debian.html;
    server_name {{ nginx_default_server_name }};

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php{{ php_version }}-fpm.sock;
    }

    location ~ /\.(ht) {
        deny all;
    }

    location ~ ^/(php_status|php_ping)$ {
        access_log off;
        fastcgi_param SCRIPT_FILENAME $fastcgi_script_name;
        include fastcgi_params;
        fastcgi_pass unix:/run/php/php{{ php_version }}-fpm.sock;
        allow 127.0.0.1;
        deny all;
    }

    location /nginx_status {
        stub_status on;
        access_log off;
        allow 127.0.0.1;
        deny all;
    }
}
```

> **注意**：`/php_status`、`/php_ping` 和 `/nginx_status` 的访问仅限本地回环地址（由 `allow 127.0.0.1` 指令限制）。

### 部署默认 Server 块

在 `nginx/tasks/configure.yml` 中追加部署任务：

```yaml
- name: Validate the default server root directory exist
  file:
    path: "{{ nginx_default_server_root }}"
    state: directory
    owner: www-data
    group: www-data

- name: Deploy the default server block
  template:
    dest: /etc/nginx/sites-available/default
    src: default.j2
    owner: root
    group: root
    mode: 0644
  notify: restart nginx
```

这就搞定了！我们的 nginx 设置应该能让我们充分发挥服务器的性能。剩下的就是给部署用户添加一些权限，以便其能写入 `/var/www` 目录，并且无需 sudo 密码即可重启 `php-fpm`。但在此之前，让我们先重启 nginx，确保一切按预期运行。

打开 nginx 处理器文件（`nginx/handlers/main.yml`）并添加重启处理器，该处理器可从任何角色调用：

---

### nginx 的处理器文件

```yaml
- name: restart nginx
  service:
    name: nginx
    state: restarted
```

完成后，运行 playbook 看看效果。完整的配置子任务如下：

---

```yaml
- name: Check the available processor cores
  shell: grep processor /proc/cpuinfo | wc -l
  register: nginx_core_number
  when: nginx_worker_processes is not defined

- name: Set the nginx_worker_processes variable
  set_fact:
    nginx_worker_processes: "{{ nginx_core_number.stdout_lines[0] }}"
  when: nginx_worker_processes is not defined

- name: Validate the config directories exist
  file:
    path: "{{ item }}"
    state: directory
    owner: root
    group: root
  loop:
    - /etc/nginx/conf.d
    - /etc/nginx/sites-enabled

- name: Validate the log directory exist
  file:
    path: /var/log/nginx
    state: directory
    owner: root
    group: adm

- name: Deploy custom nginx.conf
  template:
    dest: /etc/nginx/nginx.conf
    src: nginx.conf.j2
    owner: root
    group: root
    mode: 0644

- name: Generate 4096 bit DH Params
  shell: "openssl dhparam -out {{ nginx_dhparam_location }} 4096"
  args:
    creates: "{{ nginx_dhparam_location }}"

- name: Validate the snippets directory exist
  file:
    path: /etc/nginx/snippets
    state: directory
    owner: root
    group: root

- name: Deploy the ssl-snippet
  template:
    dest: /etc/nginx/snippets/ssl-params.conf
```



## 部署 Nginx 配置

- name: Deploy the default certificate configuration file
  template:
    dest: `/etc/nginx/snippets/ssl-default.conf`
    src: `ssl-default.conf.j2`
    owner: root
    group: root
    mode: `0644`

- name: Validate the server root directory exist
  file:
    path: `"{{ nginx_default_server_root }}"`
    state: directory
    owner: www-data
    group: www-data

- name: Deploy the default server block
  template:
    dest: `/etc/nginx/sites-available/default`
    src: `default.j2`
    owner: root
    group: root
    mode: `0644`
  notify: restart nginx

最后，通过登录到您的服务器并创建一个 phpinfo 索引文件来测试您的安装：`/var/www/app/current/public/index.php`。

```
$ echo -e "<?php\nphpinfo();" > /var/www/app/current/public/index.php
```

打开浏览器并确认一切正常启动！PHP 信息页面应该会渲染出来。

## ACL 角色

现在我们已经完成了服务器设置，我们需要允许部署用户在不需要 sudo 密码的情况下执行某些操作。

编辑 `acl/tasks/main.yml` 文件并添加以下任务。

### ACL 的任务文件

- name: Set up facl for /var/www
  acl:
    path: `/var/www`
    entity: www-data
    etype: group
    permissions: rwx
    default: no
    state: present
    recursive: yes

- name: Set up default facl for /var/www
  acl:
    path: `/var/www`
    entity: www-data
    etype: group
    permissions: rwx
    default: yes
    state: present
    recursive: yes

- name: Allow www-data to restart php
  lineinfile:
    path: `/etc/sudoers.d/wwwdata`
    line: `"%www-data ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service php{{ php_version }}-fpm restart,/usr/sbin/service php{{ php_version }}-fpm reload"`
    create: yes

- name: Change /var/www ownership
  file:
    path: `/var/www`
    recurse: yes
    group: www-data
    owner: www-data

太棒了！您应该能够以部署用户身份登录，在 `/var/www` 下创建、编辑或删除文件，并能够无需密码运行 `sudo service php7.4-fpm restart`，这太酷了！

## 测试与部署

### 测试用例

许多人一听到“测试”这个词就害怕。我们其实都想逃避测试，但测试能让软件在部署前就暴露故障，从而提高正常运行时间。当我们将 CI/CD 集成到开发流水线中时，我们会高枕无忧，因为我们知道部署到生产环境的代码确实是可用的。

[对于 PHP，我们将使用 PHPUnit，它随大多数框架捆绑在一起](https://phpunit.de/)。如果使用原生 PHP，您仍然可以通过 composer 引入它并测试您的工作。

### 本地测试

#### 测试 Laravel

[让我们使用 Laravel](https://laravel.com) 并设置一些测试。您可以使用 Laravel 安装器或 composer create-project。为简单起见，我们使用 composer create-project。

```
$ composer create-project --prefer-dist laravel/laravel devops-app
```

现在我们有了一个可用的 Laravel 安装，我们可以创建一个接收数据并将其存储在数据库中的端点。这将允许我们测试数据库连接和与应用程序的交互。

导航到项目目录并编辑 `.env` 文件。填入正确的数据库连接信息，然后创建一个新模型及其工厂、迁移和资源控制器：

```
$ php artisan make:model -mcrf Post
```

```
Model created successfully.
Factory created successfully.
Created Migration: 2020_10_29_070516_create_posts_table
Controller created successfully.
```

在迁移文件中，只添加一个字段 `content`，类型为 text。我们将不专注于创建一个功能齐全的应用程序，而只关注测试部分。

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreatePostsTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('posts', function (Blueprint $table) {
            $table->id();
            $table->text('content');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('posts');
    }
}
```

完成后，我们可以运行迁移并在数据库中创建表。使用迁移作为数据库结构的蓝图非常有效，因为无需将带有数据的 SQL 文件移入 GIT，再传到服务器。

```
$ php artisan migrate
```

```
Migrating: 2014_10_12_000000_create_users_table
Migrated: 2014_10_12_000000_create_users_table (40.59ms)
Migrating: 2014_10_12_100000_create_password_resets_table
Migrated: 2014_10_12_100000_create_password_resets_table (32.51ms)
Migrating: 2019_08_19_000000_create_failed_jobs_table
Migrated: 2019_08_19_000000_create_failed_jobs_table (16.03ms)
Migrating: 2020_10_29_070516_create_posts_table
Migrated: 2020_10_29_070516_create_posts_table (0.06 seconds)
```

我们现在可以编辑 `database/factories` 下的 `PostFactory`，指示工厂如何创建 Post。

```php
<?php

namespace Database\Factories;

use App\Models\Post;
use Illuminate\Database\Eloquent\Factories\Factory;

class PostFactory extends Factory
{
    /**
     * The name of the factory's corresponding model.
     *
     * @var string
     */
    protected $model = Post::class;

    /**
     * Define the model's default state.
     *
     * @return array
     */
    public function definition()
    {
        return [
            'content' => $this->faker->paragraphs(4, true),
        ];
    }
}
```

搞定！现在创建一个新的 posts 功能测试。我们将编写测试来执行我们设想的最终用户将执行的任何操作。在我们的例子中，我们期望最终用户能够创建新帖子、编辑它并删除它。

让我们添加一个 composer 脚本来处理测试的运行。

打开 `composer.json` 并在 scripts 下添加以下内容。

```json
"test": [
    "./vendor/bin/phpunit"
]
```

此脚本将使用测试环境迁移数据库，然后运行 `phpunit`。要执行该脚本，只需运行 `composer test`。

由于我们使用的是 PHPUnit，可以使用项目根目录下的 `phpunit.xml` 来配置测试环境。取消注释两个数据库变量：`DB_CONNECTION` 和 `DB_DATABASE`，以便我们使用 sqlite 驱动并将内存作为测试期间数据库的存储位置。这也将加快测试速度，并防止覆盖实际数据库中可能存在的任何数据。

确保你的 `phpunit.xml` 中的 php 部分看起来类似于：

```xml
<php>
    <server name="APP_ENV" value="testing"/>
    <server name="BCRYPT_ROUNDS" value="4"/>
    <server name="CACHE_DRIVER" value="array"/>
    <server name="DB_CONNECTION" value="sqlite"/>
    <server name="DB_DATABASE" value=":memory:"/>
    <server name="MAIL_MAILER" value="array"/>
    <server name="QUEUE_CONNECTION" value="sync"/>
    <server name="SESSION_DRIVER" value="array"/>
    <server name="TELESCOPE_ENABLED" value="false"/>
</php>
```

注意：你可以根据需要在 php 部分下添加任意数量的环境变量。

我们不会实现认证，但我们会了解一下验证和表单请求，以便在提供的输入不符合预期时进行测试。

[创建一个表单请求](https://laravel.com/docs/validation#form-request-validation)[来处理验证，并创建一个功能测试来包含](https://laravel.com/docs/testing)测试。

```bash
$ php artisan make:request PostRequest
Request created successfully.

$ php artisan make:test PostTest
Test created successfully.
```

确认已在 `tests/Feature/PostTest.php` 创建了一个新的功能测试，且包含默认内容：

```php
<?php

namespace Tests\Feature;

use Illuminate\Foundation\Testing\RefreshDatabase;
use Illuminate\Foundation\Testing\WithFaker;
use Tests\TestCase;

class PostTest extends TestCase
{
    /**
     * A basic feature test example.
     *
     * @return void
     */
    public function testExample()
    {
        $response = $this->get('/');
        $response->assertStatus(200);
    }
}
```

我们需要在每次运行测试时刷新测试数据库，以便之前运行的测试不会干扰下一个测试。Laravel 方便地包含了一个 [RefreshDatabase trait](https://laravel.com/docs/8.x/database-testing#resetting-the-database-after-each-test) 来为我们完成此操作。

```php
<?php

namespace Tests\Feature;

use Illuminate\Foundation\Testing\RefreshDatabase;
use Tests\TestCase;

class PostTest extends TestCase
{
    use RefreshDatabase;
}
```

我们要编写的第一个测试将检查帖子是否可以被创建。由于我们已经有了一个现成的工厂，我们将获取原始内容，发起一个 POST 请求，并断言数据已成功持久化到数据库中。

```php
/**
 * @return void
 */
public function testCanCreatePost(): void
{
    $post = Post::factory()->raw();

    $this->assertEquals(0, Post::count());

    $this->withExceptionHandling()
        ->post(route('posts.store'), [])
        ->assertSessionHasErrors(['content']);

    $this->assertEquals(0, Post::count());

    $this->withoutExceptionHandling()
        ->followingRedirects()
        ->post(route('posts.store'), $post)
        ->assertSuccessful();

    $this->assertDatabaseHas('posts', ['content' => $post['content']]);
}
```

在上面的测试中，我们首先使用定义的工厂为我们生成一个帖子。由于我们想测试帖子是否已被创建，我们需要先确认在发出创建请求之前它不存在。

接下来，我们通过传递一个空的请求体来测试验证是否生效。既然我们知道它应该会失败，我们就启用异常处理，以便正确渲染 Unprocessable HTTP Exception（不可处理的 HTTP 异常）。我们还断言会话中包含预期的错误。如果你使用的是 API，你会使用 `assertJsonValidationErrors` 断言 JSON 响应包含验证错误。

发出请求后，我们想确认它没有错误地持久化数据并返回错误，因此断言数据库中仍然没有帖子。然后我们将正确的数据发送到端点。我们禁用异常处理，以便抛出的任何错误都能在输出中显示。

这在执行 CI/CD 集成时也非常有用，因为它会给你正确的输出，使调试更容易。请求发出后，我们断言它成功了，最后断言数据库中有生成的帖子。

由于我们没有路由、没有验证规则，控制器也没有响应，这个测试肯定会失败，运行它来确认：

```bash
$ composer test
> ./vendor/bin/phpunit
PHPUnit 9.4.3 by Sebastian Bergmann and contributors.
..E 3 / 3
(100%)
Time: 00:00.568, Memory: 26.00 MB

There was 1 error:

1) Tests\Feature\PostTest::testCanCreatePost
Symfony\Component\Routing\Exception\RouteNotFoundException: Route
[posts.store] not defined.
...
```

所以让我们根据你的实现将路由添加到 `web.php` 或 `api.php`。在我们的例子中，我们将使用 `web.php`。



```php
<?php

use App\Http\Controllers\PostController;
use Illuminate\Support\Facades\Route;

Route::view('/', 'welcome');
Route::resource('posts', PostController::class);
```

接下来，编辑 `PostRequest` 以添加验证规则；将 `content` 字段设置为必填字符串。我们还将在 `authorize()` 函数中返回 `true` 来授权帖子的创建。

```php
<?php

namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class PostRequest extends FormRequest
{
    /**
     * Determine if the user is authorized to make this request.
     *
     * @return bool
     */
    public function authorize()
    {
        return true;
    }

    /**
     * Get the validation rules that apply to the request.
     *
     * @return array
     */
    public function rules()
    {
        return [
            'content' => ['required', 'string'],
        ];
    }
}
```

现在可以在 `PostController` 的 `store()` 方法上使用 `PostRequest`。表单请求在被解析时就会验证，因此无需添加额外的验证逻辑。由于创建和更新时的验证逻辑相同，此表单请求也将用于 `update()` 方法。

请求可能包含我们不需要的额外数据，所以我们不使用 `$request->all()`，而是使用 `$request->validated()` 仅获取经过清理的数据。

```php
<?php

namespace App\Http\Controllers;

use App\Http\Requests\PostRequest;
use App\Models\Post;
use Illuminate\Http\Response;

class PostController extends Controller
{
    ...

    /**
     * Store a newly created resource in storage.
     *
     * @param PostRequest $request
     *
     * @return Response
     */
    public function store(PostRequest $request)
    {
        Post::create($request->validated());

        return redirect()->route('posts.index');
    }

    ...
}
```

接下来，将帖子的 `content` 字段设置为可批量赋值。打开 `Post` 模型，添加 `fillable` 属性。这可以防止属性被批量赋值。我个人更喜欢 `fillable` 而不是 `guarded`，这样我总能确定到底赋值了什么。

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Post extends Model
{
    use HasFactory;

    protected $fillable = ['content'];
}
```

测试现在应该能运行并通过，但不要只听我的，打开终端运行：

```bash
$ composer test
> ./vendor/bin/phpunit
PHPUnit 9.4.3 by Sebastian Bergmann and contributors.
... 3 / 3
(100%)
Time: 00:00.292, Memory: 28.00 MB

OK (3 tests, 8 assertions)
```

太棒了！我们的第一个测试运行成功了！所以我们确定帖子可以被创建。

让我们确认它也可以被编辑和删除。由于我们使用了 `RefreshDatabase` trait，每次运行测试后数据库都会被清空，所以我们需要为后续的每个测试创建一个新帖子。

```php
/**
 * @return void
 */
public function testCanEditPosts(): void
{
    $post = Post::factory()->create();

    $this->withExceptionHandling()
        ->put(route('posts.update', ['post' => $post]), [])
        ->assertSessionHasErrors(['content']);
}
```

## 测试文章更新与删除功能

### 更新文章测试

```php
$this->assertDatabaseHas('posts', [
    'id' => $post->id,
    'content' => $post->content,
]);

$postUpdate = Post::factory()->raw();

$this->withoutExceptionHandling()
    ->followingRedirects()
    ->put(route('posts.update', ['post' => $post]), $postUpdate)
    ->assertSuccessful();

$this->assertDatabaseHas('posts', [
    'id' => $post->id,
    'content' => $postUpdate['content'],
]);
```

我们使用工厂的 `create()` 方法创建并持久化了文章。

然后，我们发起了一个无法处理的请求，断言其失败，并检查数据库以确保失败操作未影响数据库。

接下来，我们通过工厂创建新的文章内容并持久化，断言操作成功且数据已存在于数据库中。

打开 `PostController` 并修改 `update()` 函数以包含持久化代码。

```php
/**
 * Update the specified resource in storage.
 *
 * @param PostRequest $request
 * @param Post $post
 *
 * @return Response
 */
public function update(PostRequest $request, Post $post)
{
    $post->update($request->validated());

    return redirect()->route('posts.index');
}
```

我们添加了资源路由，因此无需向路由文件添加任何内容。现在可以运行测试并断言其按预期通过。

```bash
./vendor/bin/phpunit
```

```text
PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

.... 4 / 4 (100%)

Time: 00:00.321, Memory: 28.00 MB

OK (4 tests, 13 assertions)
```

### 删除文章测试

我们现在可以测试文章是否可以被删除。我们将添加一个新测试并更新 `PostController` 中的 `destroy()` 函数。对于此测试，删除请求无需发送负载，因此只会有一个请求。

```php
/**
 * @return void
 */
public function testCanDeletePosts(): void
{
    $post = Post::factory()->create();

    $this->withoutExceptionHandling()
        ->followingRedirects()
        ->delete(route('posts.destroy', ['post' => $post]))
        ->assertSuccessful();

    $this->assertDatabaseMissing('posts', [
        'id' => $post->id,
        'content' => $post->content,
    ]);
}
```

以及 `PostController` 中的对应代码：

```php
/**
 * Remove the specified resource from storage.
 *
 * @param Post $post
 *
 * @return Response
 */
public function destroy(Post $post)
{
    $post->delete();

    return redirect()->route('posts.index');
}
```

我们现在可以运行测试并确认其工作正常。

```bash
composer test
```

```text
> ./vendor/bin/phpunit
PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

..... 5 / 5 (100%)

Time: 00:00.355, Memory: 28.00 MB

OK (5 tests, 15 assertions)
```

太棒了！我们已经测试了文章的创建、更新和删除。你可以继续添加其余测试：查看所有文章、查看单篇文章、查看创建页面和编辑页面。

## 完整文件

### Post Controller

```php
<?php

namespace App\Http\Controllers;

use App\Http\Requests\PostRequest;
use App\Models\Post;
use Illuminate\Http\Response;

class PostController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return Response
     */
    public function index()
    {
        //
    }

    /**
     * Show the form for creating a new resource.
     *
     * @return Response
     */
    public function create()
    {
        //
    }

    /**
     * Store a newly created resource in storage.
     *
     * @param PostRequest $request
     * @return Response
     */
    public function store(PostRequest $request)
    {
        Post::create($request->validated());

        return redirect()->route('posts.index');
    }

    /**
     * Display the specified resource.
     *
     * @param Post $post
     * @return Response
     */
    public function show(Post $post)
    {
        //
    }

    /**
     * Show the form for editing the specified resource.
     *
     * @param Post $post
     * @return Response
     */
    public function edit(Post $post)
    {
        //
    }

    /**
     * Update the specified resource in storage.
     *
     * @param PostRequest $request
     * @param Post $post
     * @return Response
     */
    public function update(PostRequest $request, Post $post)
    {
        $post->update($request->validated());

        return redirect()->route('posts.index');
    }

    /**
     * Remove the specified resource from storage.
     *
     * @param Post $post
     * @return Response
     */
    public function destroy(Post $post)
    {
        $post->delete();

        return redirect()->route('posts.index');
    }
}
```

### Post Test



```php
<?php

namespace Tests\Feature;

use App\Models\Post;
use Illuminate\Foundation\Testing\RefreshDatabase;
use Tests\TestCase;

class PostTest extends TestCase
{
    use RefreshDatabase;

    /**
     * @return void
     */
    public function testCanCreatePost(): void
    {
        $post = Post::factory()->raw();

        $this->assertEquals(0, Post::count());

        $this->withExceptionHandling()
            ->post(route('posts.store'), [])
            ->assertSessionHasErrors(['content']);

        $this->assertEquals(0, Post::count());

        $this->withoutExceptionHandling()
            ->followingRedirects()
            ->post(route('posts.store'), $post)
            ->assertSuccessful();

        $this->assertDatabaseHas('posts', ['content' => $post['content']]);
    }

    /**
     * @return void
     */
    public function testCanEditPosts(): void
    {
        $post = Post::factory()->create();

        $this->withExceptionHandling()
            ->put(route('posts.update', ['post' => $post]), [])
            ->assertSessionHasErrors(['content']);

        $this->assertDatabaseHas('posts', [
            'id' => $post->id,
            'content' => $post->content,
        ]);

        $postUpdate = Post::factory()->raw();

        $this->withoutExceptionHandling()
            ->followingRedirects()
            ->put(route('posts.update', ['post' => $post]), $postUpdate)
            ->assertSuccessful();

        $this->assertDatabaseHas('posts', [
            'id' => $post->id,
            'content' => $postUpdate['content'],
        ]);
    }

    /**
     * @return void
     */
    public function testCanDeletePosts(): void
    {
        $post = Post::factory()->create();

        $this->withoutExceptionHandling()
            ->followingRedirects()
            ->delete(route('posts.destroy', ['post' => $post]))
            ->assertSuccessful();

        $this->assertDatabaseMissing('posts', [
            'id' => $post->id,
            'content' => $post->content,
        ]);
    }
}
```

# 使用 GitLab CI/CD 进行自动化测试

我们已成功创建测试并在本地运行。现在我们要创建一个流水线，为每次推送到 [GitLab](https://gitlab.com/) 的提交处理代码测试。如果失败，我们将收到邮件通知；如果是合并请求，它会警告你流水线失败。通过这种设置，我们可以确保部署到生产环境的代码是稳定的。

我们需要构建一个包含运行 Laravel 代码所需所有依赖的 Docker 镜像，并尽最大努力保持环境一致性。

## 开始使用 Docker

请遵循你所用平台的 Docker 安装及安装后说明：[Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)、[Mac](https://docs.docker.com/docker-for-mac/install/)、[Windows](https://docs.docker.com/docker-for-windows/install/)。完成后，我们可以开始构建 Docker 镜像。

## 构建与发布 Docker 镜像

我们将尝试使 Docker 镜像尽可能接近服务器环境。我们将使用 Docker 提供的官方 [Ubuntu 20.04 镜像](https://hub.docker.com/_/ubuntu)，并在其中添加我们的二进制文件和服务。由于服务器使用 PHP 7.4，我们在 Docker 镜像中也将使用相同版本。这些镜像仅包含运行所需的最基本组件，因此文件体积较小。

首先，在项目根目录下的 `docker` 目录中创建 `Dockerfile`。

```bash
mkdir docker
cd docker
touch Dockerfile
```

打开 `Dockerfile` 并使用 [`FROM` 指令](https://docs.docker.com/engine/reference/builder/#from) 指示 Docker 我们将使用基础镜像。然后我们将安装一些系统包、PHP 包，启用 PHP 包，最后[安装 Composer 和 Laravel Envoy](https://laravel.com/docs/envoy)。

## Docker 镜像构建与 GitLab CI/CD 配置

### Docker 镜像构建

我们将使用 `&&` 运算符链接命令，并使用反斜杠终止长行。制作 Docker 镜像时，请务必在执行 `apt` 请求后进行清理，这将保持镜像体积精简。

[我们将使用 `RUN` 指令来执行安装。](https://docs.docker.com/engine/reference/builder/#run)

开始构建吧。我们将遵循与搭建服务器时类似的步骤。

```dockerfile
FROM ubuntu:20.04

LABEL maintainer="David Mjomba <smodavprivate@gmail.com>"

ENV DEBIAN_FRONTEND noninteractive

ENV PHP_VERSION 7.4

RUN apt update && \
    apt install -y software-properties-common curl \
    inetutils-syslogd build-essential pkg-config && \
    LC_ALL=C.UTF-8 apt-add-repository ppa:ondrej/php -y && \
    apt-get update && apt install -y \
    php-pear \
    php-gettext \
    php-ast \
    php${PHP_VERSION} \
    php${PHP_VERSION}-bcmath \
    php${PHP_VERSION}-bz2 \
    php${PHP_VERSION}-curl \
    php${PHP_VERSION}-cli \
    php${PHP_VERSION}-dev \
    php${PHP_VERSION}-fpm \
    php${PHP_VERSION}-gd \
    php${PHP_VERSION}-intl \
    php${PHP_VERSION}-json \
    php${PHP_VERSION}-mbstring \
    php${PHP_VERSION}-mysql \
    php${PHP_VERSION}-readline \
    php${PHP_VERSION}-soap \
    php${PHP_VERSION}-sqlite3 \
    php${PHP_VERSION}-xml \
    php${PHP_VERSION}-xsl \
    php${PHP_VERSION}-zip \
    zip unzip g++ gcc git libmcrypt-dev libbz2-dev libmagickwand-dev \
    mcrypt imagemagick && \
    apt autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    pecl install imagick mcrypt redis && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    composer global require laravel/envoy
```

我们构建的镜像仅包含 PHP，因为我们只打算运行 PHP CLI 并用它来运行 Composer、PHPUnit 和 Laravel Envoy。如果你没有 [Docker Hub 账号，请先创建一个。完成后，我们](https://hub.docker.com/) 将登录 Docker Hub 以便发布容器镜像。我倾向于使用 Docker Hub 而非 GitLab Registry，因为它对所有仓库可用，也可以与他人共享。开始吧！运行 `docker login` 并输入你的 Hub 凭据。

```bash
$ docker login
Username: awesome_dude
Password:
Login Succeeded
```

现在我们可以构建 Docker 镜像并将其标记为 `latest`。请确保你位于包含 `Dockerfile` 的目录中，然后构建、标记并推送 Docker 镜像。将 `docker_username` 替换为你的实际 Docker 用户名，将 `php74` 替换为你使用的 PHP 版本。

```bash
$ docker build -t docker_username/php74:latest .
...
$ docker push docker_username/php74
The push refers to repository ...
5bd5ae06fb33: Pushed
...
latest: digest: sha256:a80f55a4c34419490034e6...
```

在第一条命令中，我们通过命令末尾的句点将上下文设置为当前目录。如果你想构建容器，但身处不同于 `Dockerfile` 所在的目录，则需将句点替换为 `Dockerfile` 的路径。

成功构建并部署后，你应该能在 [`hub.docker.com/repositories`](https://hub.docker.com/repositories) 下看到一个标记为 `latest` 的新 `php74` 仓库。现在我们可以使用此镜像运行 GitLab 测试。

### 生成 `.gitlab-ci.yml`

既然我们有了测试和 Docker 镜像，就可以在仓库上启用 GitLab CI/CD。导航到 `devops` Laravel 项目并创建一个新文件 `.gitlab-ci.yml`。Ansible 中使用的 YAML 基础知识仍将适用于 `.gitlab-ci.yml` 文件。

```bash
$ touch .gitlab-ci.yml
```

我们将使用的第一个指令是 `image`，它指示 GitLab 拉取特定镜像并在其上执行后续任务。让我们使用刚才创建的 Docker 镜像：

```yaml
image: docker_username/php74:latest
```

接下来，我们需要确定系统还需要哪些其他服务。如果需要 Redis 和/或 MySQL，我们需要按如下方式引入它们，使用 MySQL 8 并将原生密码作为默认认证插件。正如你所料，我们将使用 `services` 指令来设置这些服务。GitLab Pipeline 将首先启动服务，然后再启动我们上面指定的 Docker 镜像。开始配置吧！

```yaml
services:
  - name: redis:latest
    alias: redis
  - name: mysql:8
    alias: mysql
    command: ["--default-authentication-plugin=mysql_native_password"]
```

我们为服务设置了别名，以便将它们作为环境变量使用。说到环境变量，让我们更新它们以匹配当前环境。我们将使用 `variables` 指令并更新 `.env` 变量：

```yaml
variables:
  MYSQL_DATABASE: homestead
  MYSQL_ROOT_PASSWORD: secret
  DB_DATABASE: homestead
  DB_HOST: mysql
  DB_USERNAME: root
  DB_PASSWORD: secret
  REDIS_HOST: redis
  REDIS_PORT: 6379
```

查看 [官方 MySQL Docker 镜像文档](https://hub.docker.com/_/mysql)，我们可以获得一些在容器运行时用于设置的变量：`MYSQL_ROOT_PASSWORD` 设置要使用的 root 密码，`MYSQL_DATABASE` 设置服务启动后要创建的数据库。这两个变量也映射到 Laravel 使用的 `DB_PASSWORD` 和 `DB_DATABASE` 环境变量。`DB_USERNAME` 将为 `root`，如果你注意到了，我们将 `DB_HOST` 改为 `mysql` 以匹配 MySQL 服务使用的别名。我们还将 `REDIS_HOST` 设为 `redis`（Redis 服务的别名），将 `REDIS_PORT` 设为 `6379`（Redis 默认端口）。

接下来，我们将定义构成 Pipeline 的作业。每个作业独立处理，某些作业可以：

- 被允许失败
- 仅在单个分支上运行
- 仅手动触发等

在前置作业不允许失败的情况下，如果它失败了，后续作业将不会执行。在我们的案例中，我们将有两个作业：`test` 和 `deploy`。

```yaml
stages:
  - test
  - deploy
```

在运行任何脚本之前打印一些调试信息总是不错的。目前，让我们在运行脚本前打印 PHP 版本：

```yaml
before_script:
  - php -v
```

现在我们将运行功能测试以确认应用完全正常。

```yaml
feature_tests:
  stage: test
  script:
    - cp .env.example .env
    - composer install
    - php artisan key:generate
    - composer test
```

在功能测试作业中，我们首先将其分配给 `test` 阶段，然后定义要运行的控制台命令。由于这是仓库的全新克隆，我们首先创建新的 `.env` 文件，运行 `composer install`，生成应用密钥，然后运行预定义的 `composer` 脚本，该脚本反过来运行测试。

既然我们有 Redis 服务，可以将缓存和会话驱动设置为 `redis`。这可以在 `variables` 层面完成，也可以通过更新 `.env.example` 文件完成。我倾向于更新 `.env.example`，因为它将被克隆仓库的任何人使用。

```dotenv
BROADCAST_DRIVER=log
CACHE_DRIVER=redis
QUEUE_CONNECTION=sync
SESSION_DRIVER=redis
```

现在我们可以添加处理生产环境部署的脚本。你也可以为预发布环境添加另一个。

```yaml
deploy_production:
  stage: deploy
  script:
    - time
  when: manual
  only:
    - master
```

这是一个虚拟阶段，我们将在测试完成后运行它以确保一切正常。我们指定它仅在 `master` 分支上运行，且需手动触发。这将防止代码自动部署到服务器。

> **注意**：为了获得最佳的 Pipeline 体验，我建议保护 `master` 分支免受直接提交，并通过移除配置中的 `when: manual` 部分来自动运行部署。合并请求创建后，测试将运行。一旦合并到 `master`，将自动部署到服务器。



在本书的其余部分，我们将假设部署是手动的，以记录那些本应自动化的操作。以下是当前的 `.gitlab-ci.yml` 文件：

## GitLab CI/CD 配置与自动化部署

### GitLab CI/CD 配置文件

```yaml
image: docker_username/php74:latest

services:
  - name: redis:latest
    alias: redis
  - name: mysql:8
    alias: mysql
    command: ["--default-authentication-plugin=mysql_native_password"]

variables:
  MYSQL_DATABASE: homestead
  MYSQL_ROOT_PASSWORD: secret
  DB_DATABASE: homestead
  DB_HOST: mysql
  DB_USERNAME: root
  DB_PASSWORD: secret
  REDIS_HOST: redis
  REDIS_PORT: 6379

stages:
  - test
  - deploy

before_script:
  - php -v

feature_tests:
  stage: test
  script:
    - cp .env.example .env
    - composer install
    - php artisan key:generate
    - composer test

deploy_production:
  stage: deploy
  script:
    - time
  when: manual
  only:
    - master
```

### 仓库初始化与推送

我们现在可以登录 GitLab 并创建一个新的仓库。创建完成后，你将获得仓库地址，将其添加为新的远程仓库。进入 DevOps Laravel 目录并初始化 Git 仓库，添加远程仓库，提交并推送到服务器。

```bash
$ git init
Initialized empty Git repository in .../devops/.git/

$ git remote add origin git@gitlab.com:your_awesome_username/posts-test.git
$ git add .
$ git commit -m 'adds gitlab ci/cd'
[master (root-commit) e41dd42] adds gitlab ci/cd
 94 files changed, 8578 insertions(+)
 create mode 100644 .editorconfig
 create mode 100644 .env.example
 create mode 100644 webpack.mix.js
 ...

$ git push origin master
Enumerating objects: 118, done.
Counting objects: 100% (118/118), done.
...
To gitlab.com:your_awesome_username/posts-test.git
 * [new branch] master -> master
```

提交完成后，GitLab Runner 会扫描仓库中的 `.gitlab-ci.yml` 文件，如果存在则自动执行流水线。让我们查看一下！打开你的仓库并导航到 **CI/CD -> Pipelines**。你应该能看到一个正在运行的流水线：

![Pipeline Overview](img/index-117_1.png)

点击流水线将显示两个作业。点击 `feature_test` 作业将显示该作业的控制台输出。作业完成后，你将获得成功的绿色提示：**Job succeeded**。

![Job Success](img/index-117_2.png)

太棒了！我们的第一个作业已成功完成！你可以前往作业页面（**CI/CD -> Jobs**）并运行 `deploy_production` 作业。它应该能顺利运行！现在我们可以设置服务器以访问 GitLab，并让 GitLab 访问我们的服务器，以便按预期运行部署作业。

### 使用 GitLab CI/CD 实现自动化部署

#### SSH 配置

为了让服务器能够读取我们的仓库，我们需要获取 `deploy` 用户的公钥，并将其作为部署密钥添加到 GitLab。接下来，我们将获取 `deploy` 用户的私钥，并将其作为秘密 CI/CD 变量添加，以便 Runner 能够登录服务器并进行必要的更改。让我们登录到服务器！

```bash
$ ssh -p 4033 deploy@123.45.6.78
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQc... ansible-generated on devops-for-php-developers
```

复制该密钥，导航到你的 GitLab 仓库 -> **Settings -> Repository**。你会找到 **Deploy Keys** 部分。展开它并在提供的表单中粘贴复制的密钥，给它一个好的标题。完成后，点击 **Add key**。这将允许 `deploy` 用户从 GitLab 获取仓库，但无法推送任何更改。

接下来，我们可以设置仓库密钥，以允许 GitLab Runner 登录服务器并拉取新更改。打开终端并获取 `deploy` 用户的私有 SSH 密钥：

```bash
$ cat ~/.ssh/id_rsa
-----BEGIN RSA PRIVATE KEY-----
MICDpZGu+H...
...gc8bN
-----END RSA PRIVATE KEY-----
```

导航到仓库的 **CI/CD 设置 (Settings -> CI/CD)** 并展开 **Variables** 部分。将 **Key** 设为 `SSH_KEY`，将私钥粘贴到 **Value** 部分，将状态设为 **protected**，并保存变量。

太棒了！现在 GitLab Runner 将能够登录到我们的服务器并拉取新更改！让我们设置目录结构，以实现零停机时间部署。

#### 目录结构

为了实现零停机时间，我们将创建一个指向应用最新版本的符号链接，并将 Nginx 指向该符号链接。

由于我们将部署多个版本，我们需要某些数据在版本间持久化。在 Laravel 中，`storage` 目录应在版本间持久化。为了实现这一点，我们将保留一个 `persistent` 文件夹来存放 `.env` 文件和 `storage` 目录。期望的结构如下：

```text
/var/www/app/
├── persistent/
│   ├── .env
│   └── storage/
├── releases/
│   ├── 20200101000000/
│   └── 20200102000000/
└── current/ -> symbolic link to latest release 20200102000000
```

我们将最多保留 5 个版本并删除其余版本。如果需要旧版本，我们可以随时从 GitLab 重新部署。

#### Laravel Envoy

Laravel Envoy 将用于配置我们的服务器并生成所需的目录和版本。它提供了一种简洁、极简的语法，用于定义在远程服务器上运行的常见任务。使用 Blade 风格的语法，你可以轻松设置部署任务、Artisan 命令等。

我们将指示它在应用目录缺失时创建它们，如果 `persistent` 目录缺失，则首先将仓库克隆到 `releases` 目录，然后将所需的文件和目录复制到 `persistent` 目录。部署完成后，脚本应移除 `current` 目录并将其符号链接到最新版本。

开始之前，在 DevOps Laravel 应用目录的根目录下创建一个新的 `Envoy.blade.php` 文件。在该文件中，我们将定义要部署的服务器集合及其对应的 SSH 端口。为了使 Envoy 文件可配置且可复用，我们将通过两个选项执行它：第一个是 GitLab 仓库地址，第二个是 JSON 编码的服务器列表。这两个选项将允许 Envoy 文件跨仓库使用，而无需修改文件。

在执行任何操作之前，我们将进行一些设置。在 `@setup` 部分，我们需要验证这两个选项是否已设置。其次，我们将根据目录结构设置基础路径，并检查持久化存储是否存在，以便在缺失时创建它。设置完成后，我们将使用 JSON 解码后的服务器列表定义服务器列表。

```php
@setup
    if (!$repo || !$servers) {
        echo 'The repo and servers parameter is required';
        die();
    }

    $servers = json_decode($servers, true, JSON_THROW_ON_ERROR);
    if (!$servers || count($servers) < 1) {
        echo 'servers parameter should be a valid json array of servers.';
        die();
    }

    $persistentDir = '/var/www/app/persistent';
    $releasesDir = '/var/www/app/releases';
    $appDir = '/var/www/app/current';
    $release = date('YmdHis');
    $newReleaseDir = $releasesDir . '/' . $release;
    $persistentStorageExists = is_dir($persistentDir . '/storage');
@endsetup

@servers($servers)
```

我们现在可以设置将由 GitLab Runner 调用的 `deploy` 任务故事。你可以根据需要定义任意数量的故事。在我们的例子中，我们只需要 `deploy` 故事，它将处理：

- 克隆新版本
- 关联持久化存储和 `.env` 文件
- 安装 Composer（以及 yarn/npm）依赖
- 关联公共存储目录
- 迁移数据库
- 缓存路由和配置
- 激活版本为当前版本
- 最后清理旧版本

```php
@story('deploy')
    cloneRelease
    linkPersistentStorage
    installDependencies
    optimiseRelease
    activateRelease
    cleanup
@endstory
```

故事中的每一项都是一个任务，将在 `servers` 数组中定义的每台服务器上运行。Envoy 的优点在于你可以轻松地在运行的任何命令中引入变量。让我们设置所有任务，按照我们手动操作的步骤执行。我已经注释了 Horizon 终止步骤，因为我们尚未设置 Supervisor。

## Laravel Envoy 部署脚本与 CI/CD 配置

参考 [Laravel Horizon 文档](https://laravel.com/docs/horizon#deploying-horizon)。完整的 `Envoy.blade.php` 文件如下：

```blade
@setup
if (!$repo || !$servers) {
    exit('The repo and servers parameter is required');
}

$servers = json_decode($servers, true, JSON_THROW_ON_ERROR);
if (!$servers || count($servers) < 1) {
    exit('servers parameter should be a valid json array of servers.');
}

$persistentDir = '/var/www/app/persistent';
$releasesDir = '/var/www/app/releases';
$appDir = '/var/www/app/current';
$release = date('YmdHis');
$newReleaseDir = $releasesDir . '/' . $release;
$persistentStorageExists = is_dir($persistentDir . '/storage');
@endsetup

@servers($servers)

@story('deploy')
    cloneRelease
    linkPersistentStorage
    installDependencies
    optimiseRelease
    activateRelease
@endstory

@task('cloneRelease')
echo 'Cloning repository into release {{ $release }}'
[ -d {{ $releasesDir }} ] || mkdir -p {{ $releasesDir }}
cd {{ $releasesDir }}
git clone -b master --depth 1 {{ $repo }} {{ $release }}

@if(!$persistentStorageExists)
mkdir -p {{ $persistentDir }}/storage
cp -rf {{ $newReleaseDir }}/storage {{ $persistentDir }}
@endif

rm -rf {{ $newReleaseDir }}/storage
@endtask

@task('linkPersistentStorage')
echo 'Link Persistent Storage'
ln -nfs {{ $persistentDir }}/.env {{ $newReleaseDir }}/.env
ln -nfs {{ $persistentDir }}/storage {{ $newReleaseDir }}/storage
@endtask

@task('installDependencies')
echo "Installing Dependencies"
cd {{ $newReleaseDir }}
composer install --no-dev --prefer-dist -q -o
@endtask

@task('optimiseRelease')
echo 'Linking public storage directory'
cd {{ $newReleaseDir }}
php artisan storage:link

echo 'Migrating Database'
php artisan migrate --force

echo 'Caching routes and configs'
php artisan route:cache
php artisan config:cache
@endtask

@task('activateRelease')
echo 'Linking current release'
rm -rf {{ $appDir }}
ln -nfs {{ $newReleaseDir }} {{ $appDir }}

sudo service php7.4-fpm restart

{{-- echo 'Restarting Horizon' --}}
{{-- php artisan horizon:terminate --}}

echo 'Removing old releases'
cd {{ $releasesDir }}
echo 'Current Releases:'
ls
echo 'Releases to remove:'
ls | head -n -6
if (($(ls | head -n -6 | wc -l) > 0)); then rm -rf $(ls | head -n -6); fi
@endtask
```

现在我们有了一个可工作的部署脚本。

### 生产环境配置

然而，我们还缺少生产环境的 `.env` 文件和数据库。

在 Laravel 应用目录下生成新的应用密钥，然后打开 `.env` 文件，通过 SSH 连接到服务器，在 `persistent` 文件夹中创建新的 `.env` 文件。在新文件中粘贴本地 `.env` 内容，然后按需更新值。更新数据库配置以匹配数据库用户和数据库名称（无论是已存在的还是待创建的）。我们的 Ansible 脚本已经创建了 `/var/app/current` 目录并更新了 Nginx 指向它，因此那里无需额外操作。



```bash
$ php artisan key:generate
$ cat .env
APP_NAME=Laravel
APP_ENV=local
...
$ ssh -p 4033 deploy@123.45.6.78
Welcome to Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-70-generic x86_64)
...
$ mkdir -p /var/www/app/persistent
$ vi /var/www/app/persistent/.env
### paste the content
### update the variables
...
DB_DATABASE=posts
DB_USERNAME=devops # username and password from the mysql ansible role
DB_PASSWORD=devops
BROADCAST_DRIVER=log
CACHE_DRIVER=redis
QUEUE_CONNECTION=sync
SESSION_DRIVER=redis
...
$ mysql -u root -p
Enter password: #enter the root password set by ansible
Welcome to the MySQL monitor. Commands end with ; or \g.
mysql> create database posts;
Query OK, 1 row affected (0.00 sec)
mysql> exit;
Bye
```

预部署设置到此完成。现在我们需要配置 GitLab CI/CD 来调用 `Envoy` 并更新代码库。

## 部署流程配置

在部署新变更之前，我们需要对路由文件进行一项更改。闭包不可序列化，因此我们需要从路由文件中移除所有闭包，以便使用 `php artisan route:cache` 进行缓存。打开 `routes/api.php` 并注释掉 `/user` 端点。

```php
// Route::middleware('auth:api')->get('/user', function (Request $request) {
//     return $request->user();
// });
```

接下来，我们需要更新 GitLab YAML 文件以包含对 Laravel Envoy 的调用。我们已经在 CI/CD 变量中添加了一个密钥，定义了允许 GitLab Runner 登录服务器并使用 Envoy 脚本进行更改的部署用户私钥。我们需要添加一个新变量来保存服务器列表，称之为 `ENVOY_HOSTS`。其值应为要部署的服务器的 JSON 字符串，例如：

```json
[{"web": "deploy@123.45.6.78 -p 4033"}]
```

数组中可根据需要使用任意数量的主机。接下来，让我们更新 `.gitlab-ci.yml` 文件，设置 SSH agent 和用于登录服务器的私钥。最后，我们将执行 `envoy` 并将仓库地址和服务器列表作为参数传递。

```yaml
image: smodav/php74:latest
services:
  - name: redis:latest
    alias: redis
  - name: mysql:8
    alias: mysql
    command: ["--default-authentication-plugin=mysql_native_password"]
variables:
  MYSQL_DATABASE: homestead
  MYSQL_ROOT_PASSWORD: secret
  DB_DATABASE: homestead
  DB_HOST: mysql
  DB_USERNAME: root
  DB_PASSWORD: secret
  REDIS_HOST: redis
  REDIS_PORT: 6379
stages:
  - test
  - deploy
before_script:
  - php -v
feature_tests:
  stage: test
  script:
    - cp .env.example .env
    - composer install
    - php artisan key:generate
    - composer test
deploy_production:
  stage: deploy
  script:
    - 'which ssh-agent || (apt-get update -y && apt-get install openssh-client -y)'
    - eval $(ssh-agent -s)
    - ssh-add <(echo "$SSH_KEY")
    - mkdir -p ~/.ssh
    - '[[ -f /.dockerenv ]] && echo -e "Host *\n\tStrictHostKeyChecking no\n\n" > ~/.ssh/config'
    - ~/.config/composer/vendor/bin/envoy run deploy --repo=$CI_REPOSITORY_URL --servers="$ENVOY_HOSTS"
  when: manual #only for those who want “semi-CI/CD”
  only:
    - master
```

搞定！剩下的就是创建一个新提交，让 Runner 施展魔法。手动部署部分仅在设置了 `when: manual` 时生效。

![Manual Deployment](img/index-129_1.png)

## 手动部署

首个流水线阶段完成后，即可运行手动部署阶段。该阶段可根据需要重复运行多次。

现在我们可以访问服务器验证是否成功。打开浏览器访问 IP 地址 `123.45.6.78`，应该会看到 Laravel 欢迎页。

为了测试 CI/CD 流水线是否真正工作，让我们将 Laravel 欢迎页的文字从 "Laravel has wonderful..." 修改为 "DevOps is Awesome!"，然后部署。

```html
<div class="p-6">
  <div class="flex items-center">
    <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" class="w-8 h-8 text-gray-500">
      <path d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
    </svg>
    <div class="ml-4 text-lg leading-7 font-semibold"><a href="https://laravel.com/docs" class="underline text-gray-900 dark:text-white">Documentation</a></div>
  </div>
  <div class="ml-12">
    <div class="mt-2 text-gray-600 dark:text-gray-400 text-sm"> DevOps is Awesome! </div>
  </div>
</div>
```

提交变更：

```bash
$ git add .
$ git commit -m "changes greeting message"
$ git push origin master
```

现在前往 GitLab CI/CD 流水线，如果使用半自动 CI/CD 则部署手动任务，观察其运行。任务成功完成后，访问你的 IP 地址确认变更已上线。

到此结束！你已经成功搭建了一台服务器，且无需编写任何 `apt` 命令，现在我们完成了一个零停机时间设置，让你的生活变得相当轻松。无需登录服务器手动执行 `git` 拉取和迁移。说实话，我们都是人，难免会健忘。是否曾遇到过一个 Bug 让你调试了一整天，结果才发现只是忘记重启某个服务？有了这套自动化，你只需设置一次，其余的一切都会自动处理。

## 还有更多！

这还远未结束——PHP 只是你可以在这种流水线中使用的语言之一！自动化的世界如此庞大，你可以自动化任何让你觉得在浪费时间的事情。这只是冰山一角，去创造奇迹吧！

## 文档大纲

*   目录
*   前言
    *   本书的设计理念
    *   谁应该阅读本书？
    *   责任声明
*   手动服务器搭建
    *   寻找合适的服务器
    *   服务器更新
    *   无人值守升级
    *   安装构建工具
    *   搭建 MySQL 服务器
    *   搭建 PHP 7.4
    *   搭建 Redis 服务器
    *   搭建 Nginx
*   使用 Ansible 进行自动化服务器搭建
    *   什么是 Ansible？
    *   设置 Ansible
    *   Ansible 清单
    *   YAML 基础
    *   Ansible 剧本
    *   角色结构
    *   Common 角色
    *   MySQL 角色
    *   PHP 角色
    *   Nginx 角色
    *   ACL 角色
*   测试与部署
    *   测试用例
    *   本地测试
    *   使用 GitLab CI/CD 进行自动化测试
    *   使用 GitLab CI/CD 进行自动化部署
    *   Laravel Envoy
    *   部署
    *   还有更多！
