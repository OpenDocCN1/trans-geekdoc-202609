![](index-1_1.jpg)

Table of Contents

[Preface](#index_split_000.html#p4) .............................................................................................................. [4](#index_split_000.html#p4)

[How this book is designed](#index_split_000.html#p5) ......................................................................... [5](#index_split_000.html#p5)

[Who should read this book?](#index_split_000.html#p6) ...................................................................... [6](#index_split_000.html#p6)

[Notice of Liability](#index_split_000.html#p7) ....................................................................................... [7](#index_split_000.html#p7)

[Manual Server Setup](#index_split_000.html#p8) ........................................................................................ [8](#index_split_000.html#p8)

[Finding the Right Server](#index_split_000.html#p9) ............................................................................ [9](#index_split_000.html#p9)

[Server Updates](#index_split_000.html#p11) ........................................................................................ [11](#index_split_000.html#p11)

[Unattended Upgrades](#index_split_000.html#p12) ............................................................................. [12](#index_split_000.html#p12)

[Installing Build Tools](#index_split_000.html#p14) ................................................................................ [14](#index_split_000.html#p14)

[Setting Up MySQL Server](#index_split_000.html#p15) ....................................................................... [15](#index_split_000.html#p15)

[Setting Up PHP 7.4](#index_split_000.html#p17) .................................................................................. [17](#index_split_000.html#p17)

[Setting Up Redis Server](#index_split_000.html#p19) ........................................................................... [19](#index_split_000.html#p19)

[Setting Up Nginx](#index_split_000.html#p20) ..................................................................................... [20](#index_split_000.html#p20)

[Automated Server Setup using Ansible](#index_split_000.html#p24) ......................................................... [24](#index_split_000.html#p24)

[What is Ansible?](#index_split_000.html#p25) ....................................................................................... [25](#index_split_000.html#p25)

[Setting up Ansible](#index_split_000.html#p26) ................................................................................... [26](#index_split_000.html#p26)

[Ansible Inventory](#index_split_000.html#p28) ..................................................................................... [28](#index_split_000.html#p28)

[YAML Basics](#index_split_000.html#p30) ............................................................................................ [30](#index_split_000.html#p30)

[Ansible Playbooks](#index_split_000.html#p32) .................................................................................... [32](#index_split_000.html#p32)

[Role Structure](#index_split_000.html#p36) .......................................................................................... [36](#index_split_000.html#p36)

[The Common Role](#index_split_000.html#p37) ................................................................................... [37](#index_split_000.html#p37)

[The MySQL Role](#index_split_000.html#p54) ...................................................................................... [54](#index_split_000.html#p54)

[The PHP Role](#index_split_000.html#p61) ........................................................................................... [61](#index_split_000.html#p61)

[The Nginx Role](#index_split_000.html#p71) ......................................................................................... [71](#index_split_000.html#p71)

[The ACL Role](#index_split_000.html#p86) ........................................................................................... [86](#index_split_000.html#p86)

[Testing & Deployment](#index_split_000.html#p88) .................................................................................... [88](#index_split_000.html#p88)

[Test Cases](#index_split_000.html#p89) ................................................................................................ [89](#index_split_000.html#p89)

[Local Testing](#index_split_000.html#p90) ............................................................................................ [90](#index_split_000.html#p90)

[Automated Testing with GitLab CI/CD](#index_split_000.html#p109) ................................................. [109](#index_split_000.html#p109)

[Automated Deployment with GitLab CI/CD](#index_split_000.html#p119) ......................................... [119](#index_split_000.html#p119)

[Laravel Envoy](#index_split_000.html#p121) ......................................................................................... [121](#index_split_000.html#p121)

[Deployment](#index_split_000.html#p127) ........................................................................................... [127](#index_split_000.html#p127)

[And There’s More!](#index_split_000.html#p131) ................................................................................. [131](#index_split_000.html#p131)

Preface

4

How this book is designed

Although this book is focusing on PHP, the techniques described here can be applied to any other language or deployment, including and not limited to publishing of containers, Node.js applications, Ruby etc.

We'll mainly focus on a full LEMP (Linux Nginx MySQL PHP) server, that has all binaries running in the same server. Depending on your desires, you can have a dedicated MySQL instance, and a separate Nginx instance that works as a gateway, you will just need to modify the scripts to match your setup.

You can read this book in any order you prefer. The referenced resources are readily available, and some of them are opensource.

All the shell commands to be executed will be written with a prefix of either $

or # followed by a string of characters, and the output will follow thereafter, for example:

$ echo 'hello world'

hello world

5

Who should read this book?

Any software developer or administrator can read the book. It is ideal for freelancers, startups, entrepreneurs and anyone who works with servers, and a bit of code.

Since it primarily deals with PHP, you should know the language and understand the stack that you are using; whether LAMP or LEMP; and understand a little about server setup, ssh and using the terminal.

6

Notice of Liability

I've made every effort to ensure the accuracy of the information herein.

However, the information contained in this book is sold without warranty, either express or implied. Neither the author, nor the dealers or distributors will be held liable for any damages caused either directly or indirectly by the instructions contained in this book, or by the software or service providers described herein.

7

Manual Server Setup

8

Finding the Right Server

There are a couple of providers ([DigitalOcean](https://www.digitalocean.com/?refcode=9724e049fc4d), [Linode Cloud](https://www.linode.com/products/standard-linodes/)[, AWS](https://aws.amazon.com/ec2/)[, Vultr](https://www.vultr.com/?ref=7275395) etc.) with competitive pricing ranging from $2.5/month for a 10GB SSD, 1 vCPU

and 512 MB RAM on [Vultr](https://www.vultr.com/?ref=7275395) to a $960/month for a 3,840GB SSD, 32 vCPUs and 192GB RAM on [DigitalOcean.](https://www.digitalocean.com/?refcode=9724e049fc4d)

In our case, we shall use the [$40/month DigitalOcean Droplet (160GB SSD, 4](https://cloud.digitalocean.com/droplets/new?size=s-4vcpu-8gb)

[vCPUs and 8GB of RAM) running the latest version of Ubuntu, 20.04 LTS.](https://cloud.digitalocean.com/droplets/new?size=s-4vcpu-8gb)

123.45.6.78 If you would like to separate your services and have Redis, MySQL, Nginx and PHP servers, then enable private networking under Select additional options. This will give the droplets private IP

addresses for server-to-server communication within in the same datacenter region.

As per your needs, increase the number of droplets to be created. In our case we'll use only one. Finally, add your ssh key ([or create one), choose a desired](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

hostname and create the droplet.

Once your droplet is created, copy the public IP address, open your terminal and ssh into the server:

9

$ ssh root@123.45.6.78

The authenticity of host '123.45.6.78 (123.45.6.78)' can't be established.

ECDSA key fingerprint is SHA256:shashashasahashashashasaha.

Are you sure you want to continue connecting (yes/no/\[fingerprint\])? yes Warning: Permanently added '123.45.6.78' (ECDSA) to the list of known hosts.

Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-51-generic x86\_64)

\* Documentation: https://help.ubuntu.com

\* Management: https://landscape.canonical.com

\* Support: https://ubuntu.com/advantage

System information as of Wed Oct 28 05:26:58 UTC 2020

System load: 0.47 Users logged in: 0

Usage of /: 0.7% of 24.06GB IPv4 address for eth0:123.45.6.78

Memory usage: 4% IPv4 address for eth0: 10.10.0.5

Swap usage: 0% IPv4 address for eth1: 10.116.0.2

Processes: 97

1 update can be installed immediately.

0 of these updates are security updates.

To see these additional updates run: apt list --upgradable The list of available updates is more than a week old.

To check for new updates run: sudo apt update

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/\*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

root@ubuntu-s-1vcpu-1gb-nyc1-01:~#

Great! We have liftoff!

10

Server Updates

By default, our Ubuntu 20.04 LTS server has some outdated binaries, so let’s first update them:

\# apt update

Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease \[107 kB\]

Get:2 http://mirrors.digitalocean.com/ubuntu focal InRelease \[265 kB\]

...

...

Building dependency tree

Reading state information... Done

53 packages can be upgraded. Run 'apt list --upgradable' to see them.

\# apt upgrade -y

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

Get:1 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64

libperl5.30 amd64 5.30.0-9ubuntu0.2 \[3,952 kB\]

Get:2 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 perl amd64 5.30.0-9ubuntu0.2 \[224 kB\]

Get:3 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 perl-base amd64 5.30.0-9ubuntu0.2 \[1,513 kB\]

...

...

done

11

Unattended Upgrades

Debian/Ubuntu provides [Unattended Upgrades package that can be used to](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

automatically update the system, think of it like the Windows Update for Debian or Ubuntu. Let’s set it up to take care of security updates. The package is usually installed by default but if it is missing install it using: apt install unattended-upgrades.

We now need to locate and modify /etc/apt/apt.conf.d/50unattended-upgrades to match our requirements. For now, we'll only enable security updates, but feel free to tweak the file to meet your needs. Confirm that the Unattended-Upgrade::Allowed-Origins section has the following as active:

Unattended-Upgrade::Allowed-Origins {

"${distro\_id}:${distro\_codename}";

"${distro\_id}:${distro\_codename}-security";

"${distro\_id}ESMApps:${distro\_codename}-apps-security";

"${distro\_id}ESM:${distro\_codename}-infra-security";

// "${distro\_id}:${distro\_codename}-updates";

// "${distro\_id}:${distro\_codename}-proposed";

// "${distro\_id}:${distro\_codename}-backports";

};

The Extended Security Maintenance (ESM) origin is not always present for all releases but when available it will be used, so no harm done when we keep it there.

All the packages that you would like to manually update should be added to the Unattended-Upgrade::Package-Blacklist section. Whenever the automatic update is run, those packages will be excluded from updates. This is particularly useful for problematic packages.

Some packages require a system reboot to finish the installation. You can either allow the reboot to occur, or you can manually be rebooting the server.

In our case, we shall allow the reboot to occur at around 02:00 UTC.

12

Unattended-Upgrade::Automatic-Reboot "true"; Unattended-Upgrade::Automatic-Reboot-Time "02:00"; All that’s left now is to enable unattended updates by editing (or creating) the apt config file: /etc/apt/apt.conf.d/20auto-upgrades and setting how often we would like the upgradable packages to be downloaded and how often auto-clean should be run.

APT::Periodic::Update-Package-Lists "1";

APT::Periodic::Download-Upgradeable-Packages "1"; APT::Periodic::AutocleanInterval "7";

APT::Periodic::Unattended-Upgrade "1";

That’s it! We are all set with automatic updates.

13

Installing Build Tools

We’ll now install some packages that will be needed to compile other packages from source.

\# apt install -y build-essential g++ gcc unzip

Reading package lists... Done

Building dependency tree

Reading state information... Done

The following additional packages will be installed:

binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-9

...

...

Processing triggers for man-db (2.9.1-1) ...

Processing triggers for mime-support (3.64ubuntu1) ...

Now we can get going with setting up our LEMP server.

Notice: Most of the manual steps will be skipped but will be fully explained in the automation section.

14

Setting Up MySQL Server

[I personally prefer using Percona Server](https://www.percona.com/software/mysql-database/percona-server) [over MySQL Community as it is a](https://www.mysql.com/products/community)

free, fully compatible, enhanced and opensource drop-in replacement for any MySQL database. It provides superior performance, scalability and instrumentation.

Since Percona Server is not available in the standard Ubuntu repository, we will need to add its source and enable the ps80 repository to use MySQL

8.

\# wget https://repo.percona.com/apt/percona-release\_latest.$(lsb\_release -

sc)\_all.deb

\--2020-10-28 06:51:13-- https://repo.percona.com/apt/percona-release\_latest.focal\_all.deb

Resolving repo.percona.com (repo.percona.com)... 167.99.233.229, 157.245.119.64, 167.71.118.3

Connecting to repo.percona.com (repo.percona.com)|167.99.233.229|:443...

connected.

...

...

\# dpkg -i percona-release\_latest.$(lsb\_release -sc)\_all.deb (Reading database ... 100078 files and directories currently installed.) Preparing to unpack percona-release\_latest.focal\_all.deb ...

...

...

\# percona-release setup ps80

\* Disabling all Percona Repositories

\* Enabling the Percona Server 8.0 repository

\* Enabling the Percona Tools repository

Get:1 http://mirrors.digitalocean.com/ubuntu focal InRelease \[265 kB\]

...

Reading package lists... Done

We can now install Percona Server. Since most applications are not yet using the new MySQL authentication plugin, we will instruct Percona to use the legacy MySQL 5.x authentication. Follow the prompts and enter a secure password for the root user and then select the native authentication plugin.

15

\# apt install -y percona-server-server

...

...

Processing triggers for man-db (2.9.1-1) ...

Processing triggers for libc-bin (2.31-0ubuntu9.1) ...

Notice: In case you did not enable the native authentication plugin, and you now need to, create a new MySQL config file to set it on MySQL

boot up, then restart MySQL. We'll also make sure MySQL is enabled to run on system boot.

\# echo -e "\[mysqld\]\\ndefault-authentication-plugin =

mysql\_native\_password" > /etc/mysql/mysql.conf.d/default-auth-override.cnf

\# service mysql restart

\# systemctl enable mysql

Next, let’s run the mysql provided script that improves the security of our installation.

\# mysql\_secure\_installation

Finally, we can clean up and remove the file we downloaded:

\# rm percona-release\_latest.$(lsb\_release -sc)\_all.deb

And we're done!

Next, we switch the default authentication plugin, enable it to run at startup and restart it so that our new configs are loaded: Finally, let’s run the mysql provided script that improves the security of our installation. And we’re done!

16

Setting Up PHP 7.4

At the time of writing, the latest version of PHP is 7.4. Switch this to match the version you are interested in. Let’s use [Ondrej's PPA](https://launchpad.net/~ondrej/+archive/ubuntu/php) to setup our PHP 7.4

instance.

\# add-apt-repository ppa:ondrej/php

Co-installable PHP versions: PHP 5.6, PHP 7.x and most requested extensions are included. Only Supported Versions of

PHP (http://php.net/supported-versions.php) for Supported Ubuntu Releases (https://wiki.ubuntu.com/Releases) are

provided. Don't ask for end-of-life PHP versions or Ubuntu release, they won't be provided.

...

...

Get:14 http://ppa.launchpad.net/ondrej/php/ubuntu focal/main Translation-en

\[28.2 kB\]

Fetched 1,030 kB in 2s (564 kB/s)

Reading package lists... Done

We can now select the set of PHP modules that we will require to run our applications. The ones provided are a good start for most applications.

\# apt install -y php-pear php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-dev php7.4-gd php7.4-json php7.4-mysql php7.4-opcache php7.4-readline php7.4-sqlite3 php7.4-tidy php7.4-xml php7.4-bcmath php7.4-bz2 php7.4-fpm php7.4-imap php7.4-zip php7.4-mbstring php7.4-soap php7.4-xsl php7.4-intl imagemagick php7.4-imagick

Reading package lists... Done

Building dependency tree

Reading state information... Done

The following additional packages will be installed:

autoconf automake autopoint autotools-dev debhelper

...

...

Processing triggers for php7.4-cli (7.4.12-3+ubuntu20.04.1+deb.sury.org+1) ...

Processing triggers for php7.4-fpm (7.4.12-3+ubuntu20.04.1+deb.sury.org+1) ...

Then enable PHP-FPM to run on startup.

17

\# systemctl enable php7.4-fpm

Synchronizing state of php7.4-fpm.service with SysV service script with

/lib/systemd/systemd-sysv-install.

Executing: /lib/systemd/systemd-sysv-install enable php7.4-fpm Since we consume other people's packages, we will definitely require

[Composer to manage our dependencies. Follow the Composer install guide](https://getcomposer.org/doc/00-intro.md)

found on the [Download Composer Page and then move composer so that it is](https://getcomposer.org/download/)

accessible globally.

Warning: The snippet below will be outdated with time since the hash changes whenever the setup file is changed.

\# php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

\# php -r "if (hash\_file('sha384', 'composer-setup.php') ===

'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353f de0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP\_EOL;"

Installer verified

\# php composer-setup.php

All settings correct for using Composer

Downloading...

Composer (version 2.0.4) successfully installed to: /root/composer.phar Use it: php composer.phar

\# php -r "unlink('composer-setup.php');"

\# mv composer.phar /usr/local/bin/composer

\# which composer

/usr/local/bin/composer

We’ve got our PHP instance! Whoop whoop!

18

Setting Up Redis Server

[Redis](https://redis.io) is an awesome in-memory key-value store. It’s used as a database, cache or even a message broker using [Pub/Sub. Setting it up and enabling it](https://redis.io/topics/pubsub)

to run on start up is pretty straight forward:

\# apt install -y redis-server

Reading package lists... Done

Building dependency tree

Reading state information... Done

...

...

Processing triggers for man-db (2.9.1-1) ...

Processing triggers for libc-bin (2.31-0ubuntu9.1) ...

\# systemctl enable redis-server

Synchronizing state of redis-server.service with SysV service script with

/lib/systemd/systemd-sysv-install.

Executing: /lib/systemd/systemd-sysv-install enable redis-server 19

Setting Up Nginx

[Nginx is an opensource web server and as they state in their website, it](https://www.nginx.com/)

powers over 400 million websites. Nginx is pretty robust and can also act as a load balancer. To get started, we have to confirm that apache2 is not installed.

\# apt remove apache2

Reading package lists... Done

Building dependency tree

Reading state information... Done

Package 'apache2' is not installed, so not removed

0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

Next, we will add the Official Nginx PPA so that we always have the latest updates.

\# add-apt-repository ppa:nginx/stable

This PPA contains the latest Stable Release version of the nginx web server software.

\*\*Only Non-End-of-Life Ubuntu Releases are supported in this PPA\*\*

\*\*Development releases of Ubuntu are not officially supported by this PPA, and uploads for those will not be available until actual final releases for those versions\*\*

More info: https://launchpad.net/~nginx/+archive/ubuntu/stable Press \[ENTER\] to continue or Ctrl-c to cancel adding it.

Hit:1 http://repo.percona.com/prel/apt focal InRelease

...

...

Reading package lists... Done

We can now install and enable Nginx to run on startup.

20

\# apt install -y nginx

Reading package lists... Done

Building dependency tree

...

...

Processing triggers for nginx-core (1.18.0-3ubuntu1+focal2) ...

Triggering nginx reload ..

\# systemctl enable nginx

Synchronizing state of nginx.service with SysV service script with

/lib/systemd/systemd-sysv-install.

Executing: /lib/systemd/systemd-sysv-install enable nginx

Great! We can now setup our default server block to process PHP files and create a sample PHP file to test our installation. We’ll need to find our php-fpm socket (TCP or Unix socket) from the configuration file.

Notice: You can change the listen option in the pool definition to use the configuration you prefer, it defaults to a Unix socket.

\# cat /etc/php/7.4/fpm/pool.d/www.conf | grep 'listen ='

listen = /run/php/php7.4-fpm.sock

From the output above, we see that PHP-FPM is listening via a socket located at /run/php/php7.4-fpm.sock. We will use this socket as our fastcgi\_pass parameter in the default Nginx config. Open up

/etc/nginx/sites-available/default and update it so that it allows processing of PHP files.

[The first thing we will change is the index directive](http://nginx.org/en/docs/http/ngx_http_index_module.html). This directive determines the default file that is loaded when the url ends with slash (/).

Warning: The order that you set the parameters matters. If you have an index.php and an index.html file and the index directive is set as index index.html index.php, then the index.html file will have preference over the index.php file.

21

We shall also add a new location block with a regular expression to match all files ending with .php and send them to the running PHP-FPM process.

\# vi /etc/nginx/sites-available/default

root /var/www/html;

index index.php index.html index.htm index.nginx-debian.html; server\_name \_;

location / {

try\_files $uri $uri/ =404;

}

location ~ \\.php$ {

include snippets/fastcgi-php.conf;

fastcgi\_pass unix:/run/php/php7.4-fpm.sock;

}

Once done, save the file, test that it is correct and with no errors, then restart nginx so that the new configuration takes over.

\# nginx -t

nginx: the configuration file /etc/nginx/nginx.conf syntax is ok nginx: configuration file /etc/nginx/nginx.conf test is successful

\# service nginx restart

We can now add a php info script that allows us to check our installation.

\# echo -e "<?php\\nphpinfo();" > /var/www/html/info.php That was tedious! Imagine performing all these steps to setup ten servers!

The best thing is that we have Ansible to help us with automation! Open your favourite browser and navigate to http://your.ip.over.here/info.php and confirm that the php info page loaded.

22

![](index-23_1.png)

23

Automated Server Setup using

Ansible

24

What is Ansible?

[Ansible](https://www.ansible.com/) is a platform by Red Hat that has endless automation uses which allows performing actions in multiple servers at the same time. Ansible uses YAML Language for its files and depends on the SSH protocol to manage the machines.

Once Ansible is installed, it will not add a database, and there will be no daemons to start or keep running. You only need to install it on one machine (which could easily be a laptop), and it can manage an entire fleet of remote machines from that central point. When Ansible manages remote machines, it does not leave software installed or running on them, so there’s no real question about how to upgrade Ansible when moving to a new version. If you would like to contribute to the project, you can have a look at [GitHub](https://github.com/ansible/ansible)

25

Setting up Ansible

For you to run Ansible, you need a machine running any version of unix, be it Red Hat, Debian, CentOS, macOS, Ubuntu and its flavours and many more.

Microsoft Windows is currently not supported. Depending on your local distro, install ansible using your package manager. Ansible is also available via Python pip.

\## Fedora

$ sudo dnf install ansible

\## CentOS

$ sudo yum install ansible

\## Ubuntu

$ sudo apt update && sudo apt install -y software-properties-common $ sudo apt-add-repository --yes --update ppa:ansible/ansible

$ sudo apt install ansible

\## local single user installation on macOS or any other system $ pip install --user ansible

\## system wide installation on macOS or any other system

$ sudo pip install ansible

We’re set! When Ansible is making remote connections, it will use the native SSH service and assumes that you are using SSH keys. It is always advised to use SSH keys over plain password authentication. If you already have a running server but you have not setup passwordless authentication, you can easily copy your public SSH key using ssh-copy-id on your local machine.

Substitute the server IP address (and the user if you want passwordless authenticaion for a different user) in the command below.

$ ssh-copy-id root@123.45.6.78

Now we’ve installed Ansible. We need a fresh server with nothing installed so that we can automate the manual process we completed in the previous section. Once we spin up a new droplet from Digital Ocean (or any other provider, or a local server), we can start playing around with Ansible. Make an 26

ansible directory somewhere awesome on your local machine. In our case, we will use ~/devops.

27

Ansible Inventory

Ansible allows us to list our server IP addresses in [different formats](https://docs.ansible.com/ansible/latest/plugins/inventory.html#inventory-plugins). Let’s use both INI and YAML formats to explain the difference. Inside the new directory, create two new files; hosts and hosts.yml; to keep an [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

of all our server IP addresses. Since we have not setup another user for our servers, we shall use the root user. We can also give each of our servers names and group them as per our needs.

$ cat hosts

\# your server ip addresses

1.x.x.x

2.x.x.x

\[databases\]

3.y.y.y

4.y.y.y

\[php\]

server ansible\_host=5.z.z.z

worker ansible\_host=6.z.z.z ansible\_port=8888

In the INI file above the:

x.x.x addresses are only in the all and ungrouped groups,

y.y.y in the databases group and,

z.z.z in the php group.

The two PHP server groups have aliases (server and worker) which can be used when you explicitly want to target either of the two servers. The worker server also has a custom SSH port 8888 which must be defined using the ansible\_port variable.

The YAML equivalent of the INI above is:

28

$ cat hosts.yml

\# your server ip addresses

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

ansible\_host: 5.z.z.z

worker:

ansible\_host: 6.z.z.z

ansible\_port: 8888

For the Ansible hosts, the colon at the end of each list item is required when the hosts are more than one thus, it’s always advised to keep the colon with or without multiple hosts. To test our inventory, ping any of the listed servers using the ansible [ping module:](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/ping_module.html)

$ ansible all -i hosts -m ping

$ ansible all -i hosts.yml -m ping

$ ansible databases -i hosts -m ping

$ ansible databases -i hosts.yml -m ping

$ ansible worker -i hosts -m ping

$ ansible worker -i hosts.yml -m ping

...

6.z.z.z | SUCCESS => {

"ansible\_facts": {

"discovered\_interpreter\_python": "/usr/bin/python3"

},

"changed": false,

"ping": "pong"

}

29

YAML Basics

The YAML syntax is pretty straight forward. We’ll go through a few basics before having a look at playbooks.

As a common convention, Ansible files can begin with --- and end with ...

denoting the start and end of the document. Most files will only include the beginning marker. Comments are defined by the # character.

Lists are very common in Ansible and are defined by using - (hyphen) followed by a space.

\---

\- php

\- vue

\- react

Dictionaries are key: value pairs in which the colon must always be followed by a space.

php:

latest: 7.3

Installed: 7.3

In the case that you have a line that is too long, it can be wrapped using the Literal Block Scalar character | (pipe character), or the Folded Block Scalar character > (greater than character). The Literal Block Scalar character will render the input as typed, literally including the new lines and any additional spaces while the Folded Block Scalar character will convert the new lines into spaces. New lines can be enforced by either indenting the line or adding an extra empty line.

30

\# Literal

exact\_hello\_world\_template: |

this is

the

hello world template

\# same as:

\# this is\\nthe\\nwrapped\\nhello world template

\# Folded

wrapped\_hello\_world\_template: >

this is

the

wrapped

hello world template

\# same as:

\# this is the wrapped\\nhello world template

Notice: In case your strings contain a colon or a #, you will need to quote them as YAML will expect a mapping when a colon is followed by a space i.e. John Doe: Look for him. Anything after the # will be regarded as a comment.

31

Ansible Playbooks

Playbooks are Ansible’s configuration, deployment, and orchestration language. They can describe a policy you want your remote systems to enforce, or a set of steps in a general IT process and in our case, how we want our servers to be setup.

Each playbook consists of tasks, which are a set of steps that should be performed on the hosts that you select. The tasks are executed in the order that they are written against the selected hosts, one task at a time. In order to make our playbooks configurable, we must use variables within our tasks.

These variables can be defined in the Ansible Inventory file or the play or even in the task.

When the tasks are executed, the name of the task is displayed as part of the output. Each task within the play should therefore have a name, a simple human readable description of the task.

We can group our tasks by following any structure we prefer. Since we are setting up a LEMP server, we can have php, mysql, nginx, common and acl groups. In ansible these groups are referred to as roles. The good thing with roles is that they are self-contained thus, easily sharable between playbooks.

We’re good to go! In the ~/devops directory, add a new site.yml file. This will be our play definition file. Next we need a directory to store all our roles; create the roles directory. We will then use ansible-galaxy to create our 5

roles.

$ touch site.yml

$ mkdir roles

$ cd roles

$ ansible-galaxy init php

$ ansible-galaxy init mysql

$ ansible-galaxy init nginx

$ ansible-galaxy init common

$ ansible-galaxy init acl

First, let's give Ansible the list of hosts to use. Define your Ansible Inventory in the format you prefer. I prefer using the INI format:

32

123.45.6.78 ansible\_user=root

Notice: Since we are using the root account in our server, we will have to explicitly instruct ansible by adding the ansible\_user=root parameter; failure to which, it will try to connect using the local user account and fail.

Next, open site.yml using your favourite editor. I prefer Visual Studio Code with the YAML and Ansible extensions.

Notice: Each playbook consists of a list of plays and each play executed against a list or servers (hosts).

The first directive we shall give is a list of hosts that the play should be executed on; all should do for now.

\---

\- hosts: all

Next we’ll define a section to hold variables that will be used by the play. This section is defined by the key vars and should have its properties indented from the margin since it's a dictionary.

\---

\- hosts: all

vars:

KEY: sample value

We can now test whether the playbook is set up correctly by adding a ping task that will do the same thing as running ansible all -i hosts -m ping.

33

\---

\- hosts: all

vars:

KEY: sample value

tasks:

\- name: Ping our awesome server

ping:

data: pong

Open up the terminal and navigate to the ~/devops directory and execute the playbook

$ cd ~/devops

$ ansible-playbook -i ./hosts site.yml

PLAY \[all\] \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

TASK \[Gathering Facts\] \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

ok: \[123.45.6.78\]

TASK \[Ping our awesome server\] \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

ok: \[123.45.6.78\]

PLAY RECAP \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

123.45.6.78 : ok=2 changed=0 unreachable=0 failed=0 skipped=0 rescued=0

ignored=0

Congratulations! You’ve run your first playbook. Looking back, the playbook has a similar syntax to the YAML hosts file. We will be using YAML for all our playbook information including the roles.

Remove the tasks that we just added and replace them with our roles.

Depending on your setup, you will need to have more than one play in the playbook, each with its own set of hosts. In our case, we are using one common server for all our services.

When running the play, we will execute the common role first so that we do the basic server setup and perform system upgrades. We plan on using PHP-FPM via a unix socket. The path of the unix socket is dependent on the PHP

version we are running. If we choose PHP 7.3, the socket will be unix:/run/php/php7.3-fpm.sock while PHP 7.4 will give us

34

unix:/run/php/php7.4-fpm.sock. The socket location is used by both Nginx and PHP. The PHP version also determines the PHP modules to be installed. If we are using PHP 7.3, we will have to install the php7.3-\*

modules. In light of all this, it makes perfect sense to keep the PHP version as a variable. So let's add it as our first var.

\---

\- name: Spinning up our LEMP server.

hosts: all

vars:

php\_version: "7.3"

roles:

\- common

\- mysql

\- php

\- nginx

\- acl

When using different hosts you can use:

\---

\- name: Common Setup

hosts: all

roles:

\- common

\- security

\- ...

\- ...

\- name: Spin up php

hosts:

\- php

vars:

php\_version: "7.3"

roles:

\- php

Great! Let's get started on our roles and check out their structure.

35

Role Structure

Each role that is created using ansible-galaxy init role comes with a set of folders. Not all the folders are required but at the least, the tasks folder should be present. Below are the default folders that you get: Defaults => stores the default variables that will be used in the role in case a variable is undefined.

Files => keeps the deployable files that are to be used in the role.

Handlers => keeps the handlers (event listeners) that can be used within or without the role.

Meta => defines some metadata that will be used by the role.

Tasks => keeps the list of tasks to be executed by the role.

Templates => contains templates that can be edited and deployed by the role.

Vars => contains variables that are used by the role.

You can raise events in Ansible which will be handled by the listeners that are defined in the handlers directory. All our tasks will be defined and stored in the tasks directory.

36

The Common Role

Open up main.yml located under common/tasks. We shall use this file to define all the common tasks to be executed on each of the hosts we defined in site.yml. We will add a couple of things that are not in the Manual Server Setup Chapter. The steps we shall take are:

Update server

Setup unattended upgrades

Install extra packages

Perform some system optimisations

Create a new user; deploy to handle our CI/CD deployments

Setup our firewall.

We will create subtasks that will be imported into the main.yml file. Having subtasks makes the process very atomic thus, easier to manage. We'll create the subtask files then add them to the common task.

$ cd ~/devops/roles/common/tasks

$ touch pre\_setup.yml optimisations.yml users.yml security.yml Then import the created subtasks into the main task file:

\---

\# tasks file for common role

\- name: Pre-setup tasks

import\_tasks: pre\_setup.yml

\- name: Optimise system

import\_tasks: optimisations.yml

\- name: Create additional users

import\_tasks: users.yml

\- name: Boot firewall and configure SSH

import\_tasks: security.yml

37

Pre-Setup Subtask

Open up pre\_setup.yml and use the apt module to update our server, install packages and setup unattended upgrades. For the unattended upgrades, we will either use templates or complete files or the lineinfile module. The line in file module is useful for adding, editing and removing lines in a file and if the file does not exist, it can also be created.

To get started, let’s update the apt cache and any outdated packages. We shall set the apt cache expiry to 24Hrs. Since the apt module takes the TTL in seconds, we’ll use 86400.

\---

\- name: Update the system

apt:

update\_cache: yes

cache\_valid\_time: 86400

upgrade: 'dist'

One man's meat is another man's poison hence, the need for variables! Each server will be different, have different package requirements, the unattended upgrades package will need to act differently, etc. We shall set default variables for our role and store them in the defaults directory. These variables can be overridden by having variables of the same name in the play definition or the vars directory.

We'll definitely require some basic packages to be present, and some packages might use snap. Therefore, we can create three variables; one to hold the apt packages (pre\_setup\_packages), and the last two to hold the snap packages (pre\_setup\_snap and pre\_setup\_snap\_classic).

[Assuming we’ll use Let’s Encrypt](https://letsencrypt.org/) and Ubuntu 18.04. we will need the ppa:certbot/certbot repository to be added. In our case, Ubuntu 20.04, we shall use snap to install certbot.

38

\---

\# defaults file for common

pre\_setup\_snap:

pre\_setup\_snap\_classic:

\- certbot

pre\_setup\_packages:

\- wget

\- curl

\- zsh

\- software-properties-common

\- build-essential

\- g++

\- gcc

\- git

\- vim

\- nscd

\- supervisor

\- unzip

\- acl

\- unattended-upgrades

\- ufw

Switch back to the pre\_setup subtask and add the tasks for installing the desired packages.

39

\---

\# pre\_setup tasks

\- name: Update the system

apt:

update\_cache: yes

cache\_valid\_time: 86400

upgrade: 'dist'

\- name: Install packages

apt:

name: "{{ pre\_setup\_packages | default(\[\], true) | list }}"

state: latest

\- name: Install Snap Packages

snap:

name: "{{ pre\_setup\_snap | default(\[\], true) | list }}"

state: present

\- name: Install Classic Snap Packages

snap:

name: "{{ pre\_setup\_snap\_classic | default(\[\], true) | list }}"

classic: true

state: present

Unattended Upgrades

Unattended upgrades only runs using origins that have been enabled. We can either create a file and store it under the files directory or use variables to enable the origins we need. We’ll go for the latter. Let’s add some default variables into the common/default/main.yml file.

40

unattended\_upgrades\_security: true

unattended\_upgrades\_esm: true

unattended\_upgrades\_updates: true

unattended\_upgrades\_proposed: false

unattended\_upgrades\_backports: false

unattended\_upgrades\_blacklisted: \[\]

unattended\_upgrades\_remove\_dependencies: false

unattended\_upgrades\_auto\_reboot: true,

unattended\_upgrades\_auto\_reboot\_time: "00:00"

unattended\_upgrades\_update\_period: 1

unattended\_upgrades\_upgrade\_period: 1

unattended\_upgrades\_auto\_clean\_period: 7

unattended\_upgrades\_unattended\_upgrade\_period: 1

Feel free to add any more variables as required. Take a copy of

[/etc/apt/apt.conf.d/50unattended-upgrades](https://help.ubuntu.com/community/AutomaticSecurityUpdates) and use it as a template, saving it as common/templates/50unattended-upgrades.j2 and then replace the values with variables.

[Ansible uses Jinja as the templating engine. You can read more about it on](https://jinja.palletsprojects.com)

the [documentation site](https://jinja.palletsprojects.com).

41

Unattended-Upgrade::Allowed-Origins {

"${distro\_id}:${distro\_codename}";

{% if unattended\_upgrades\_security %}

"${distro\_id}:${distro\_codename}-security";

{% endif %}

{% if unattended\_upgrades\_esm %}

"${distro\_id}ESMApps:${distro\_codename}-apps-security";

"${distro\_id}ESM:${distro\_codename}-infra-security";

{% endif %}

{% if unattended\_upgrades\_updates %}

"${distro\_id}:${distro\_codename}-updates";

{% endif %}

{% if unattended\_upgrades\_proposed %}

"${distro\_id}:${distro\_codename}-proposed";

{% endif %}

{% if unattended\_upgrades\_backports %}

"${distro\_id}:${distro\_codename}-backports";

{% endif %}

};

Unattended-Upgrade::Package-Blacklist {

{% for item in unattended\_upgrades\_blacklisted %}

"{{ item }}";

{% endfor %}

};

Unattended-Upgrade::MinimalSteps "true";

Unattended-Upgrade::InstallOnShutdown "false";

Unattended-Upgrade::Remove-Unused-Dependencies "{% if unattended\_upgrades\_remove\_dependencies %}true{% else %}false{% endif %}"; Unattended-Upgrade::Automatic-Reboot "{% if unattended\_upgrades\_auto\_reboot

%}true{% else %}false{% endif %}";

Unattended-Upgrade::Automatic-Reboot-Time "{{

unattended\_upgrades\_auto\_reboot\_time }}";

Create a task under pre\_setup.yml that will be used to replace the variables and deploy the template to the server. If the Ansible tasks are written well, re-running them on a system that is already setup will not break anything and should simply update what needs to be changed.

42

\- name: Configure Unattended Upgrades

template:

dest: /etc/apt/apt.conf.d/50unattended-upgrades

src: 50unattended-upgrades.j2

Add the second template; common/templates/20auto-upgrades.j2; with the following content. This file determines how frequent the auto upgrade will be performed.

APT::Periodic::Update-Package-Lists "{{ unattended\_upgrades\_update\_period }}"; APT::Periodic::Download-Upgradeable-Packages "{{

unattended\_upgrades\_upgrade\_period }}";

APT::Periodic::AutocleanInterval "{{ unattended\_upgrades\_auto\_clean\_period

}}";

APT::Periodic::Unattended-Upgrade "{{

unattended\_upgrades\_unattended\_upgrade\_period }}";

All that’s left now is to set up the task that will copy over the template:

\- name: Configure Unattended Upgrades Frequency

template:

dest: /etc/apt/apt.conf.d/20auto-upgrades

src: 20auto-upgrades.j2

owner: root

group: root

mode: 0644

That’s it! We’ve successfully created two template files, added some variables and created tasks that will render the templates and deploy them to the server. To run the playbook, we’ll use the same command as before: $ ansible-playbook -i ./hosts site.yml

Below is our complete pre-setup file:

43

\---

\# pre\_setup tasks

\- name: Update the system

apt:

update\_cache: yes

cache\_valid\_time: 86400

upgrade: 'dist'

\- name: Install packages

apt:

name: "{{ pre\_setup\_packages | default(\[\], true) | list }}"

state: latest

\- name: Install Snap Packages

snap:

name: "{{ pre\_setup\_snap | default(\[\], true) | list }}"

state: present

\- name: Install Classic Snap Packages

snap:

name: "{{ pre\_setup\_snap\_classic | default(\[\], true) | list }}"

classic: true

state: present

\- name: Configure Unattended Upgrades

template:

dest: /etc/apt/apt.conf.d/50unattended-upgrades

src: 50unattended-upgrades.j2

owner: root

group: root

mode: 0644

\- name: Configure Unattended Upgrades Frequency

template:

dest: /etc/apt/apt.conf.d/20auto-upgrades

src: 20auto-upgrades.j2

owner: root

group: root

mode: 0644

Optimisations Subtask

As per our main.yml task file, the next item in the queue is optimisations 44

(optimisations.yml). In order to get the most out of our server, we will need to increase some default values. Somaxconn defines the size of the kernel queue for accepting new connections. The lower the value the lower the maximum concurrent users.

By default, the value is set to 128, giving a max of 128 concurrent users. We’ll set this value to 100000. Open up optimisations.yml and add the first task:

\---

\- name: Update the maximum concurrent connections

sysctl:

name: net.core.somaxconn

value: "100000"

state: present

The ip\_local\_port\_range defines the available and usable ports which is usually set to 32768 - 61000 by default. We shall increase this range and offer port 10000 to port 65535.

\- name: Update available port range

sysctl:

name: net.ipv4.ip\_local\_port\_range

value: "1024 65535"

state: present

The TCP protocol offers a wait state which keeps a socket open for up to 4

minutes after the connection has been closed. This can be problematic on a busy server as it will run out of sockets and ports. We can instruct the system to reuse sockets when it’s safe to do so without waiting for the 4 minutes to elapse.

45

\- name: Allow socket reuse

sysctl:

name: net.ipv4.tcp\_tw\_reuse

value: 1

reload: yes

state: present

Most developers have faced an issue with the maximum number of open files allowed per process. The default value is usually very low; set to 1024 and this causes an issue since sockets are essentially files on any unix system (e.g.

/run/php/php7.4-fpm.sock) and thus, the maximum concurrent connections are limited. If we do our math right, the gateway is only allowed to have a maximum of 512 connections. This is because each connection from a client is counted as one inbound connection, which will then be forwarded to the upstream server which will require another outbound connection, making those 2 open connections per client. We definitely have to up this value and set the soft and hard limits to 999999.

\- name: Set the soft and hard open file limits

pam\_limits:

domain: "{{ item.domain }}"

value: "999999"

limit\_item: nofile

limit\_type: "{{ item.type }}"

with\_items:

\- type: soft

domain: "\*"

\- type: hard

domain: "\*"

\- type: soft

domain: root

\- type: hard

domain: root

Let's add our first handler which will listen to events requiring a system reboot. We shall fire the event once we’ve changed our soft and hard file limits. Open common/handlers/main.yml:

46

\---

\# handlers file for common

\- name: reboot server

reboot:

Here’s the complete common/tasks/optimisations.yml file:

47

\---

\- name: Update the maximum concurrent connections

sysctl:

name: net.core.somaxconn

value: "100000"

state: present

\- name: Update available port range

sysctl:

name: net.ipv4.ip\_local\_port\_range

value: "1024 65535"

state: present

\- name: Allow socket reuse

sysctl:

name: net.ipv4.tcp\_tw\_reuse

value: 1

reload: yes

state: present

\- name: Set the soft and hard open file limits

pam\_limits:

domain: "{{ item.domain }}"

value: "999999"

limit\_item: nofile

limit\_type: "{{ item.type }}"

with\_items:

\- type: soft

domain: "\*"

\- type: hard

domain: "\*"

\- type: soft

domain: root

\- type: hard

domain: root

notify:

\- reboot server

Users Subtask

In order for us to be able to clone our Git repository, we'll require a user (of course not root). I prefer calling the user "deploy" but feel free to create any 48

username you like. Let’s add a couple of default variables under common/defaults/main.yml, then write the user creation task in common/tasks/users.yml.

deploy\_user: "deploy"

deploy\_user\_generate\_ssh\_key: true

deploy\_user\_shell: "/bin/bash"

deploy\_user\_local\_ssh\_keys:

\- ~/.ssh/id\_rsa.pub

deploy\_user\_groups:

\- www-data

Notice: Since this user will be required to handle the web server files, we’ve added him to the www-data group. We are not implementing User Isolation. If you intend to, modify the user groups that are attached to the deploy user.

Using the ansible user module, let's create a new user and generate the SSH

key pair that will be used by our CI/CD pipelines. We'll also use the authorized\_key module which allows us copy our local public SSH key so that we have password-less login. We also want to allow the deploy user to login as himself when using our CI/CD pipeline from GitLab.

49

\---

\# tasks for users.yml

\- name: Create the deploy user groups

group:

name: "{{ item }}"

state: present

loop: "{{ deploy\_user\_groups | default(\[\], true) }}"

\- name: Create the deploy user

user:

name: "{{ deploy\_user }}"

groups: "{{ (deploy\_user\_groups | default(\[\], true) | join(',')) }}"

generate\_ssh\_key: "{{ deploy\_user\_generate\_ssh\_key }}"

shell: "{{ deploy\_user\_shell }}"

register: created\_user

\- name: Add GitLab to known hosts

lineinfile:

dest: "/home/{{ deploy\_user }}/.ssh/known\_hosts"

create: yes

state: present

line: "{{ lookup('pipe', 'ssh-keyscan -t rsa gitlab.com') }}"

regexp: "^gitlab\\\\.com"

mode: 0600

\- name: Allow SSH key based logins

authorized\_key:

user: "{{ deploy\_user }}"

key: "{{ lookup('file', item) }}"

state: present

loop: "{{ deploy\_user\_local\_ssh\_keys | default(\[\], true) }}"

\- name: Allow Deploy User to Login

authorized\_key:

user: "{{ deploy\_user }}"

key: "{{ created\_user\['ssh\_public\_key'\] }}"

state: present

Let’s run the playbook and see if the changes will be made as desired. Once the playbook is run, try logging in as the created user, in our case, the deploy user: ssh deploy@123.45.6.78. You should be able to login successfully without a password.

50

Security Subtask

Let’s beef up the security of our server! The first thing I like changing is the default SSH Port. We also installed UFW (uncomplicated firewall) for filtering which connections should be accepted and which should be dropped.

Let's add some new default variables. The ufw\_allow variable will house the port and protocol (tcp/udp) to be used and can contain as many ports as needed.

ssh\_port: "4033"

ufw\_allow:

\- port: 80

proto: tcp

\- port: 443

proto: tcp

Then we add the tasks in common/tasks/security.yml:

51

\---

\# tasks for security

\- name: Update the SSH port

lineinfile:

path: /etc/ssh/sshd\_config

regexp: "^#?Port "

line: "Port {{ ssh\_port }}"

\- name: Allow SSH traffic through firewall

ufw:

rule: allow

port: "{{ ssh\_port }}"

proto: tcp

\- name: Allow traffic through firewall

ufw:

rule: allow

port: "{{ item.port }}"

proto: "{{ item.proto }}"

loop: "{{ ufw\_allow | default(\[\], true) | list }}"

\- name: Restart SSH

service:

name: ssh

state: restarted

\- name: Ensure we use the configured SSH port for the remainder of the role set\_fact:

ansible\_port: "{{ ssh\_port }}"

\- name: Start UFW

ufw:

direction: incoming

state: enabled

policy: deny

You’ll notice that we have updated the ansible\_port fact under the Ensure we use the configured SSH port for the remainder of the role task. This allows ansible to carry on working for the rest of the role since we have changed the default SSH port to 4033. If using other firewalls, make sure the port is open before changing it, otherwise the task will fail.

If you try to use the default SSH command, it will fail unless the port is 52

specified. To connect as the previously created deploy user, add -p 4033 to the SSH command. You can also create an alias for this connection or add a host to your local SSH config ~/.ssh/config:

$ ssh -p 4033 deploy@123.45.6.78

\# using an alias

$ echo 'alias devops="ssh -p 4033 deploy@123.45.6.78"' >> ~/.bashrc $ source ~/.bashrc

$ devops # this calls the alias above

\# using ssh config

$ vi ~/.ssh/config

Host devops

Hostname 123.45.6.78

Port 4033

User deploy

$ ssh devops # this will use the devops config

Notice: If you are running the playbook after each change, you’ll need to add the ansible\_port variable on your Ansible inventory hosts file and then remove it once the whole playbook is done so that new servers will get the correct configuration.

Using INI format: 123.45.6.78 ansible\_user=root

ansible\_port=4033

The common role is done!

53

The MySQL Role

Percona Subtask

Under the mysql role directory, create a new percona.yml file under tasks to house our percona preparation and installation tasks. We will also add some python libraries so that ansible can connect to our database.

\---

\- name: Setup Percona Repository

apt:

deb: "https://repo.percona.com/apt/percona-release\_latest.{{

ansible\_distribution\_release }}\_all.deb"

\- name: Enable Percona 8 Repository

command: percona-release setup ps80

\- name: Install Percona Server

apt:

name: percona-server-server

state: latest

update\_cache: yes

\- name: Determine required MySQL Python libraries

set\_fact:

mysql\_python\_package: "{% if ansible\_python.version.major == 3 %}python3-pymysql{% else %}python-pymysql{% endif %}"

\- name: Ensure MySQL Python libraries are installed

apt:

name: "{{ mysql\_python\_package }}"

state: latest

Let's also add a handler (mysql/handlers/main.yml) that will allow us to restart mysql server.

54

\---

\# mysql/handlers/main.yml

\- name: restart mysql

service:

name: mysql

state: restarted

Configure Subtask

Create a new task file, configure.yml file under mysql/tasks and a new my.cnf.j2 template file under mysql/templates. The template will be used to modify the default my.cnf file that comes with Percona.

55

\# templates/my.cnf.j2

\[mysqld\]

default-authentication-plugin={{ default\_authentication\_plugin }}

\# Disabling symbolic-links is recommended to prevent assorted security risks symbolic-links = 0

\# Memory settings.

max\_allowed\_packet = {{ mysql\_max\_allowed\_packet }}

sort\_buffer\_size = {{ mysql\_sort\_buffer\_size }}

read\_buffer\_size = {{ mysql\_read\_buffer\_size }}

key\_buffer\_size = {{ mysql\_key\_buffer\_size }}

myisam\_sort\_buffer\_size = {{ mysql\_myisam\_sort\_buffer\_size }}

read\_rnd\_buffer\_size = {{ mysql\_read\_rnd\_buffer\_size }}

table\_open\_cache = {{ mysql\_table\_open\_cache }}

max\_connections = {{ mysql\_max\_connections }}

group\_concat\_max\_len = {{ mysql\_group\_concat\_max\_len }}

thread\_cache\_size = {{ mysql\_thread\_cache\_size }}

join\_buffer\_size = {{ mysql\_join\_buffer\_size }}

tmp\_table\_size = {{ mysql\_tmp\_table\_size }}

max\_heap\_table\_size = {{ mysql\_max\_heap\_table\_size }}

\# InnoDB settings.

innodb\_file\_per\_table = {{ mysql\_innodb\_file\_per\_table }}

innodb\_buffer\_pool\_size = {{ mysql\_innodb\_buffer\_pool\_size }}

innodb\_log\_file\_size = {{ mysql\_innodb\_log\_file\_size }}

innodb\_log\_buffer\_size = {{ mysql\_innodb\_log\_buffer\_size }}

innodb\_flush\_log\_at\_trx\_commit = {{ mysql\_innodb\_flush\_log\_at\_trx\_commit }}

innodb\_lock\_wait\_timeout = {{ mysql\_innodb\_lock\_wait\_timeout }}

!includedir /etc/mysql/conf.d/

!includedir /etc/mysql/mysql.conf.d/

Let's also add some default values for use with a server of about 512MB RAM.

Edit mysql/defaults/main.yml and add the following variables.

56

\---

\# defaults file for mysql

\# caching\_sha2\_password is the default but most clients are not supporting it default\_authentication\_plugin: "mysql\_native\_password"

mysql\_max\_allowed\_packet: "64M"

mysql\_sort\_buffer\_size: "1M"

mysql\_read\_buffer\_size: "1M"

mysql\_key\_buffer\_size: "256M"

mysql\_myisam\_sort\_buffer\_size: "64M"

mysql\_read\_rnd\_buffer\_size: "4M"

mysql\_table\_open\_cache: "256"

mysql\_max\_connections: "151"

mysql\_group\_concat\_max\_len: "1024"

mysql\_thread\_cache\_size: "8"

mysql\_join\_buffer\_size: "262144"

mysql\_tmp\_table\_size: "16M"

mysql\_max\_heap\_table\_size: "16M"

mysql\_innodb\_file\_per\_table: "1"

mysql\_innodb\_buffer\_pool\_size: "256M"

mysql\_innodb\_log\_file\_size: "64M"

mysql\_innodb\_log\_buffer\_size: "8M"

mysql\_innodb\_flush\_log\_at\_trx\_commit: "1"

mysql\_innodb\_lock\_wait\_timeout: "50"

mysql\_root\_password: "t00r"

mysql\_grant\_users:

\- name: "devops"

password: "devops"

host: "localhost"

privileges: "\*.\*:All" # '\*.\*:ALL,GRANT' generates a "root" user We can now copy the template file over to our server and replace the existing one. Once we are done with the configurations, we shall restart mysql server using the handler we created. We shall also ensure that mysql is started on system boot.

We'll also create extra mysql users who will have the permissions we need.

Add as many as required under the mysql\_grant\_users variable. Also set a sensible password for root via the role variables. Lastly, we shall perform the secure installation and remove the test database and the anonymous user.

57

\---

\# mysql/tasks/configure.yml

\- name: Update MySQL Configuration

template:

src: my.cnf.j2

dest: /etc/mysql/my.cnf

owner: root

group: root

mode: 0644

force: true

notify: restart mysql

\- name: Enable MySQL on boot

service:

name: mysql

state: started

enabled: true

\- name: Disallow remote root login

command: 'mysql -NBe "{{ item }}"'

with\_items:

\- DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost',

'127.0.0.1', '::1')

changed\_when: false

\- name: Get defined hosts for root

command: mysql -NBe "SELECT Host FROM mysql.user WHERE User = 'root' ORDER

BY (Host='localhost') ASC"

register: mysql\_hosts

changed\_when: false

check\_mode: false

\- name: Update MySQL root password

shell: mysql -u root -NBe 'ALTER USER "root"@"{{ item }}" IDENTIFIED WITH

mysql\_native\_password BY "{{ mysql\_root\_password }}";'

with\_items: "{{ mysql\_hosts.stdout\_lines | default(\[\]) }} "

\- name: Set MySQL root configuration

template:

src: "root-my.cnf.j2"

dest: "/root/.my.cnf"

owner: root

group: root

mode: 0600

force: true

58

\- name: Create additional users

mysql\_user:

name: "{{ item.name }}"

host: "{{ item.host }}"

password: "{{ item.password }}"

priv: "{{ item.privileges }}"

state: present

loop: "{{ mysql\_grant\_users | default(\[\]) }}"

no\_log: true

\- name: Get defined hosts for the anonymous user

command: mysql -NBe 'SELECT Host FROM mysql.user WHERE User = ""'

register: mysql\_anonymous\_hosts

changed\_when: false

check\_mode: false

\- name: Remove anonymous MySQL users.

mysql\_user:

name: ""

host: "{{ item }}"

state: absent

with\_items: "{{ mysql\_anonymous\_hosts.stdout\_lines | default(\[\]) }}"

\- name: Remove MySQL test database

mysql\_db:

name: test

state: absent

notify: restart mysql

The task above references a root-my.cnf.j2 template file which stores the credentials for the root mysql user. Create the file under templates and use the content below.

\[client\]

user="root"

password="{{ mysql\_root\_password }}"

All that’s left is to include the two sub tasks into the mysql/tasks/main.yml task.

59

\---

\# tasks file for mysql

\- name: Handle Percona Installation

import\_tasks: percona.yml

\- name: Configure the database engine

import\_tasks: configure.yml

That should take care of our MySQL server. You should be able to login to MySQL with the set password, and the other created users should also be able to login.

60

The PHP Role

Setting up PHP is usually easy. Since we are using PHP 7.4, we have an option of using the Debian maintained version or Ondrej’s PPA but since a lot of people like having the flexibly, let’s use the latter. We shall setup PHP,

[Composer and configure modules like opcache.](https://getcomposer.org/)

Installs Subtask

Add a new subtask; installs.yml; which will hold our installation of PHP

and other required binaries. We shall compile some modules like redis from source. The list of packages to be installed will be defined in the php/defaults/main.yml file.

61

\---

\# defaults file for php

php\_version: 7.4

php\_packages:

\- php-pear

\- php{{ php\_version }}

\- php{{ php\_version }}-cli

\- php{{ php\_version }}-common

\- php{{ php\_version }}-curl

\- php{{ php\_version }}-dev

\- php{{ php\_version }}-gd

\- php{{ php\_version }}-json

\- php{{ php\_version }}-mysql

\- php{{ php\_version }}-opcache

\- php{{ php\_version }}-readline

\- php{{ php\_version }}-sqlite3

\- php{{ php\_version }}-xml

\- php{{ php\_version }}-bcmath

\- php{{ php\_version }}-bz2

\- php{{ php\_version }}-fpm

\- php{{ php\_version }}-intl

\- php{{ php\_version }}-mbstring

\- php{{ php\_version }}-soap

\- php{{ php\_version }}-xsl

\- php{{ php\_version }}-zip

\- php{{ php\_version }}-imagick

\- imagemagick

\- libmcrypt-dev

php\_pecl\_install:

\- mcrypt

\- redis

Changing the playbook's php\_version (defined in site.yml) will also change the modules that will be installed since we are using the variable as a reference in all our modules. You can add as many packages above as needed. Each project will have its own specification of extensions that will be needed. If image processing will not be required, the image processing extensions like imagick can be removed.

There are two extra packages sourced from PECL, In our case, mcrypt and redis. Update the php/tasks/installs.yml subtask and add:

62

\---

\- name: Add Ondrej PPA

apt\_repository:

repo: ppa:ondrej/php

state: present

update\_cache: yes

mode: 0666

\- name: Install PHP packages

apt:

name: "{{ php\_packages | default(\[\]) }}"

state: latest

\- name: Update PECL protocols

shell: pecl channel-update pecl.php.net

\- name: Install PECL Packages

shell: yes '' | pecl install -s --force {{ item }}

loop: "{{ php\_pecl\_install }}"

[Following the programatic installation of composer, create a new script and](https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md)

save it at files/install\_composer.sh, which we shall execute and register the output which we shall use to determine if the installation was successful. If successful, we shall move the created composer.phar file to

/usr/local/bin/composer.

63

#!/bin/sh

EXPECTED\_CHECKSUM="$(wget -q -O - https://composer.github.io/installer.sig)"

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

ACTUAL\_CHECKSUM="$(php -r "echo hash\_file('sha384', 'composer-setup.php');")"

if \[ "$EXPECTED\_CHECKSUM" != "$ACTUAL\_CHECKSUM" \]

then

\>&2 echo 'ERROR: Invalid installer checksum'

rm composer-setup.php

exit 1

fi

php composer-setup.php --quiet

RESULT=$?

rm composer-setup.php

exit $RESULT

Now update the installs subtask and add the composer install task.

\- name: Install Composer

script: files/install\_composer.sh

register: composer\_install\_status

\- name: Install Composer globally

command: mv composer.phar /usr/local/bin/composer

when: composer\_install\_status.changed

Configure Subtask

Next, configure the installation by adding a new subtask;

php/tasks/configure.yml and adding some extra default variables. In Debian/Ubuntu, the PHP configuration files are usually symlinked to the mods-available folder thus, we shall create our configs in the mods-available folder and symlink them to the cli and fpm directories. Add the default variables (php/defaults/main.yml) that will be used to generate the custom configs, and the directory to store the configs.

64

php\_common\_conf\_directory: /etc/php/{{ php\_version }}/mods-available php\_conf\_directories:

\- /etc/php/{{ php\_version }}/cli/conf.d

\- /etc/php/{{ php\_version }}/fpm/conf.d

php\_register\_modules:

\- name: mcrypt

priority: 20

\- name: redis

priority: 20

In the default variables above, we’ve added the common mods-available directory and the two config directories. These are also dependent on the PHP version. The modules we want to register are listed under php\_register\_modules. The priority is used in the generation of the filename (priority-name.ini: 20-mcrypt.ini). The priority determines the order in which the modules are loaded.

Next we create the template for the file that will be stored in the mods-available folder. Save it as templates/module.ini.j2.

; configuration for php {{ item.name }} module

; priority={{ item.priority }}

extension={{ item.name }}.so

Better be safe than sorry! Let's add tasks to confirm that the directory for PHP custom configs is actually present.

65

\---

\# php/tasks/configure.yml

\- name: Ensure common configuration directory exist

file:

path: "{{ php\_common\_conf\_directory }}"

state: directory

follow: true

\- name: Ensure configuration directories exist

file:

path: "{{ item }}"

state: directory

follow: true

loop: "{{ php\_conf\_directories }}"

Next, we can copy over our configurations. The first configs will be the two modules we’ve installed and listed on the defaults file as php\_register\_modules. Append the two tasks into configure.yml subtask.

\- name: Add modules configs

template:

dest: "{{ php\_common\_conf\_directory }}/{{ item.name }}.ini"

src: module.ini.j2

owner: root

group: root

mode: 0644

loop: "{{ php\_register\_modules }}"

\- name: Enable modules

file:

src: "{{ php\_common\_conf\_directory }}/{{ item.1.name }}.ini"

dest: "{{ item.0 }}/{{ item.1.priority }}-{{ item.1.name }}.ini"

state: link

force: yes

loop: "{{ php\_conf\_directories | product(php\_register\_modules) | list }}"

New we give our PHP installation a boost by configuring Opcache. Add some opcache default variables that will be used with the opcache template file, opcache.ini.j2.

66

opcache\_enable: "1"

opcache\_enable\_cli: "1"

opcache\_memory\_consumption: "512"

opcache\_string\_buffer: "64"

opcache\_accelerated\_files: "30000"

opcache\_validate\_timestamps: "0"

opcache\_fast\_shutdown: "1"

opcache\_save\_comments: "1"

I’d advice you to use opcache as it improves PHP performance by storing precompiled script bytecode in shared memory, thereby removing the need for PHP to load and parse scripts on each request. So once a file has been read and compiled, it’s stored in memory and all subsequent request will not need to read the file again.

Notice: When you disable the validate timestamps option, you will need to restart PHP-FPM with every new deployment so that the precompiled scripts are flushed

And now the opcache.ini.j2 template:

zend\_extension=opcache.so

\[opcache\]

opcache.enable={{ opcache\_enable }}

opcache.enable\_cli={{ opcache\_enable\_cli }}

opcache.memory\_consumption={{ opcache\_memory\_consumption }}

opcache.interned\_strings\_buffer={{ opcache\_string\_buffer }}

opcache.max\_accelerated\_files={{ opcache\_accelerated\_files }}

opcache.validate\_timestamps={{ opcache\_validate\_timestamps }}

opcache.fast\_shutdown={{ opcache\_fast\_shutdown }}

opcache.save\_comments = {{ opcache\_save\_comments }}

This template will be used to replace the opcache.ini file located under mods-available directory. It is automatically symlinked to the cli and fpm directories so the rest of the work is done for us.

67

\- name: Setup Opcache

template:

dest: "{{ php\_common\_conf\_directory }}/opcache.ini"

src: opcache.ini.j2

owner: root

group: root

mode: 0644

Next, we set up our PHP-FPM pools. The default is usually the www pool.

Create a new template file; www.conf.j2; and add the following pool definitions:

\[www\]

user = {{ php\_fpm\_user }}

group = {{ php\_fpm\_group }}

listen = /run/php/php{{ php\_version }}-fpm.sock

listen.owner = {{ php\_fpm\_user }}

listen.group = {{ php\_fpm\_group }}

pm = dynamic

pm.max\_children = {{ php\_pm\_max\_children }}

pm.start\_servers = {{ php\_pm\_start\_servers }}

pm.min\_spare\_servers = {{ php\_pm\_min\_spare\_servers }}

pm.max\_spare\_servers = {{ php\_pm\_max\_spare\_servers }}

pm.max\_requests = {{ php\_pm\_max\_requests }}

{% if php\_pm\_enable\_stats %}

pm.status\_path = {{ php\_pm\_status\_path }}

{% endif %}

{% if php\_pm\_enable\_monitoring %}

ping.path = {{ php\_pm\_ping\_path }}

ping.response = {{ php\_pm\_ping\_response }}

{% endif %}

This pool file will be populated depending on the server requirements. If your server does not have enough resources to handle 100 children, setting pm.max\_children to 100 will be a joke! Each child usually consumes between 20 - 60 megabytes of RAM. Taking a 4GB server with MySQL

running (~ 1GB RAM) and system resources and other services (~0.5BG), we would have approximately 2.5GB of RAM remaining. So we can calculate our max processes as 2560/60 = 42.6, give it a round figure of 40.

68

Even though we will be using an 8GB RAM server, our system is not that busy, so we’ll set the max processes variable to 50. Update the

php/defaults/main.yml file and add the following variables.

php\_fpm\_user: "www-data"

php\_fpm\_group: "www-data"

php\_pm\_max\_children: "50"

php\_pm\_start\_servers: "3"

php\_pm\_min\_spare\_servers: "1"

php\_pm\_max\_spare\_servers: "5"

php\_pm\_max\_requests: "500"

php\_pm\_enable\_stats: true

php\_pm\_status\_path: "/php\_status"

php\_pm\_enable\_monitoring: true

php\_pm\_ping\_path: "/php\_ping"

php\_pm\_ping\_response: "pong"

Notice: If you intend to implement User Isolation, set the fpm user to the user you created, in our case it was deploy.

We can now add the task that will handle the deployment of the template and set fpm to run on system boot. Append the two tasks into the configure.yml subtask.

\- name: Setup the default pool

template:

dest: "/etc/php/{{ php\_version }}/fpm/pool.d/www.conf"

src: www.conf.j2

owner: root

group: root

mode: 0644

\- name: Enable PHP-FPM on boot

service:

name: "php{{ php\_version }}-fpm"

state: started

enabled: true

And that should do it for PHP. Only two things left: a handler for restarting 69

PHP once all the tasks have been completed and adding the subtasks into the main task. The handler will listen to the restart php-fpm event then handle the restart for us. Edit php/handlers/main.yml:

\---

\# handlers file for php

\- name: restart php-fpm

service:

name: "php{{ php\_version }}-fpm"

state: restarted

Finally, update our php/tasks/main.yml task file and add our subtasks.

Remember to restart PHP-FPM when the configuration subtask is done:

\---

\# tasks file for php

\- name: Install PHP

import\_tasks: installs.yml

\- name: Configure PHP

import\_tasks: configure.yml

notify: restart php-fpm

70

The Nginx Role

[Nginx is available as a distribution package and can also be installed via the](https://www.nginx.com/)

official PPA. The distribution package is not always up to date, so let’s use the PPA. We shall have two subtasks, one for the installation, and the other to configure Nginx. I’ve provided an optimised nginx.conf file, and a sample default server block that has some extra optimisations.

To set up the worker\_processes configuration value, we shall use the number of cores available in the current server. This value shall be extracted and saved in the nginx\_worker\_processes variable if it is undefined. If you would prefer to use your own value and disable the auto calculation, add the nginx\_worker\_processes variable to the playbook variables and assign it a value.

So let’s get going! Create the two subtasks; installs.yml and configure.yml; and add them to the nginx main.yml task file.

\---

\# tasks file for nginx

\- name: Install nginx

import\_tasks: installs.yml

\- name: Configure Nginx

import\_tasks: configure.yml

Installs Subtask

We can now open up nginx/tasks/installs.yml and add the official Nginx PPA, install it and set it to run on system boot.

71

\---

\- name: Add Nginx PPA.

apt\_repository:

repo: 'ppa:nginx/stable'

state: present

update\_cache: true

mode: 0666

\- name: Remove Apache if present

apt:

name: apache2

state: absent

\- name: Install Nginx

apt:

name: nginx

state: latest

\- name: Enable Nginx on boot

service:

name: nginx

state: started

enabled: true

That’s it for our installs subtask! Pretty fast hey?

Configure Subtask

Next, we open up the nginx/tasks/configure.yml file and setup the worker process auto calculation tasks to run only when the nginx\_worker\_processes variable is undefined.

72

\---

\- name: Check the available processor cores

shell: grep processor /proc/cpuinfo | wc -l

register: nginx\_core\_number

when: nginx\_worker\_processes is not defined

\- name: Set the nginx\_worker\_processes variable

set\_fact:

nginx\_worker\_processes: "{{ nginx\_core\_number.stdout\_lines\[0\] }}"

when: nginx\_worker\_processes is not defined

We can now add our nginx.conf template file under

templates/nginx.conf.j2.

user {{ nginx\_user }};

worker\_processes {{ nginx\_worker\_processes }};

pid /var/run/nginx.pid;

error\_log /var/log/nginx/error.log {{ nginx\_error\_level }}; events {

worker\_connections {{ nginx\_worker\_connections }};

}

http {

include /etc/nginx/mime.types;

default\_type application/octet-stream;

log\_format main\_ext '$remote\_addr - $remote\_user \[$time\_local\]

"$request" '

'$status $body\_bytes\_sent "$http\_referer" '

'"$http\_user\_agent" "$http\_x\_forwarded\_for" '

'"$host" sn="$server\_name" '

'rt=$request\_time '

'ua="$upstream\_addr" us="$upstream\_status" '

'ut="$upstream\_response\_time"

ul="$upstream\_response\_length"'

'cs=$upstream\_cache\_status';

access\_log /var/log/nginx/access.log main\_ext;

sendfile on;

tcp\_nopush on;

tcp\_nodelay on;

keepalive\_timeout {{ nginx\_keepalive\_timeout }};

73

 types\_hash\_max\_size {{ nginx\_types\_hash\_max\_size }};

\# allow the server to close connection on non responding client,

\# this will free up memory

reset\_timedout\_connection on;

##

\# Client Settings

##

client\_body\_timeout {{ nginx\_client\_body\_timeout }};

client\_header\_timeout {{ nginx\_client\_header\_timeout }};

client\_body\_buffer\_size {{ nginx\_client\_body\_buffer\_size }}; client\_header\_buffer\_size {{ nginx\_client\_header\_buffer\_size }}; client\_max\_body\_size {{ nginx\_client\_max\_body\_size }};

large\_client\_header\_buffers {{ nginx\_large\_client\_header\_buffers }};

{% if nginx\_enable\_gzip %}

##

\# Gzip Settings

##

gzip on;

gzip\_disable "msie6";

gzip\_vary on;

gzip\_proxied any;

gzip\_comp\_level 6;

gzip\_min\_length 1000;

gzip\_buffers 16 8k;

gzip\_http\_version 1.1;

gzip\_types application/atom+xml application/javascript application/json application/ld+json application/manifest+json application/rdf+xml application/rss+xml application/schema+json application/vnd.geo+json application/vnd.ms-fontobject application/x-font-ttf application/x-javascript application/x-web-app-manifest+json application/xhtml+xml application/xml font/collection font/eot font/opentype font/otf font/ttf image/bmp image/svg+xml image/vnd.microsoft.icon image/x-icon text/cache-manifest text/calendar text/css text/javascript text/plain text/markdown text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy text/xml;

{% endif %}

##

\# Server Settings

##

server\_tokens off; # don't send the version number in error pages and headers

74

 include /etc/nginx/conf.d/\*.conf;

include /etc/nginx/sites-enabled/\*;

}

Great! The above config disables server tokens so that we keep our Nginx details private, and enables the resetting of timed out connections so that we can have as much memory reuse as possible. Let’s add the variables that are to be used by the config to the nginx/defaults/main.yml file.

\---

\# defaults file for nginx

nginx\_user: "www-data"

nginx\_error\_level: "warn"

nginx\_worker\_connections: "2048"

nginx\_keepalive\_timeout: "65"

nginx\_types\_hash\_max\_size: "2048"

nginx\_client\_body\_timeout: "12"

nginx\_client\_header\_timeout: "12"

nginx\_client\_body\_buffer\_size: "10k"

nginx\_client\_header\_buffer\_size: "1k"

nginx\_client\_max\_body\_size: "8m"

nginx\_large\_client\_header\_buffers: "4 32k"

nginx\_enable\_gzip: true

As stated before, in case you want to set the worker\_processes, you will need to edit the sites.yml file and add the nginx\_worker\_processes variable as below:

\---

\- name: Spinning up our LEMP server.

hosts: all

vars:

nginx\_worker\_processes: "auto"

roles:

\- common

\- mysql

\- php

\- nginx

We can now add tasks to the nginx/tasks/configure.yml file, that will 75

validate that the two config and log directories are present and handle the creation if missing (/etc/nginx/conf.d, /etc/nginx/sites-enabled and

/var/log/nginx). The other task will handle the deploying of our custom nginx.conf template.

\- name: Validate the config directories exist

file:

path: "{{ item }}"

state: directory

owner: root

group: root

loop:

\- /etc/nginx/conf.d

\- /etc/nginx/sites-enabled

\- name: Validate the log directory exist

file:

path: /var/log/nginx

state: directory

owner: root

group: adm

\- name: Deploy custom nginx.conf

template:

dest: /etc/nginx/nginx.conf

src: nginx.conf.j2

owner: root

group: root

mode: 0644

Notice: If using User Isolation, set the nginx\_user and owner of

/var/log/nginx directory to match the created user account Good! It’s a great practise to have your sites served over HTTPS, and to make your encryption even stronger, we shall add a couple of things. First, let’s generate our secure [Diffie-Hellman (DH)](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) parameters of 4096 bit field primes. This process takes a while depending on your server resources. Let’s specify the location to save the file under our nginx/defaults/mail.yml file:

76

\# defaults/main.yml

nginx\_dhparam\_location: "/etc/ssl/certs/dhparam.pem"

and add the task that will generate it to nginx/tasks/configure.yml:

\- name: Generate 4096 bit DH Params

community.crypto.openssl\_dhparam:

path: "{{ nginx\_dhparam\_location }}"

size: 4096

mode: 0666

In the task above, we use the community.crypto.openssl\_dhparam module which is a community module that is not available in the default ansible modules. We will need to install the [Community Crypto Collection](https://github.com/ansible-collections/community.crypto)

which includes a lot of other goodies. To install run:

$ ansible-galaxy collection install community.crypto

Let’s add the nginx/templates/ssl-params.conf.j2 template that will be used to configure our SSL params. This file should be included within each server block that will be using HTTPS.

77

\## Use per block. ssl-params

ssl\_protocols TLSv1.2 TLSv1.3;

ssl\_prefer\_server\_ciphers on;

ssl\_ciphers "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH"; ssl\_ecdh\_curve secp384r1;

ssl\_session\_timeout 60m;

ssl\_session\_cache shared:SSL:10m;

ssl\_session\_tickets off;

ssl\_stapling on;

ssl\_stapling\_verify on;

resolver {{ nginx\_dns\_ip\_1 }} {{ nginx\_dns\_ip\_2 }} valid=300s; resolver\_timeout 5s;

{% if nginx\_enable\_strict\_transport\_security\_header %}

add\_header Strict-Transport-Security "max-age={{ nginx\_hsts\_max\_age }};{% if nginx\_hsts\_include\_subdomains %}includeSubdomains;{% endif %}{% if nginx\_hsts\_preload %} preload;{% endif %} ";

{% endif %}

{% for option in nginx\_xframe\_options %}

add\_header X-Frame-Options {{ option }};

{% endfor %}

add\_header X-Content-Type-Options nosniff;

add\_header X-Robots-Tag {{ nginx\_x\_robots\_tag }};

ssl\_dhparam {{ nginx\_dhparam\_location }};

And the default variables that go with it:

78

nginx\_dns\_ip\_1: "8.8.8.8"

nginx\_dns\_ip\_2: "8.8.4.4"

nginx\_enable\_strict\_transport\_security\_header: true

nginx\_hsts\_max\_age: "63072000"

nginx\_hsts\_preload: false

nginx\_hsts\_include\_subdomains: true

nginx\_xframe\_options:

\- "SAMEORIGIN"

nginx\_x\_robots\_tag: "none" #

https://developers.google.com/search/reference/robots\_meta\_tag So far so good! If you have a look at the ssl-params.conf.j2 file, we are setting some nginx parameters. We’ve dropped all other protocols except TLS 1.2 and TLS 1.3 since they are considered unsafe. The enabled ssl\_ciphers are also regarded as the best. You can read more on that at

[Mozilla Foundation.](https://wiki.mozilla.org/Security/Server_Side_TLS)

The ssl\_dhparam and ssl\_ecdh\_curve are used for forward security whereby the client and server negotiate a pre-master key that is: specific to the connection between them,

used only for a limited amount of time, and

destroyed at the end of the session thus, it's called Ephemeral.

We use these configuration options to instruct nginx to use the generated DH

Parameters it for DHE key-exchange.

[Instructions can be sent to all modern browsers via headers. We use the HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)

[Strict Transport Security Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security) to instruct the browsers that are connecting to the server to only communicate via HTTPS. When HTTPS is not available, the browsers cannot connect, keeping your clients secure.

Just like the HSTS Header, we have the [Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) header which directs browsers how to handle your site when it comes to viewing it via the

<frame>, <iframe>, <embed> and <object> tags. This is an easy way of dealing with [Clickjacking](https://en.wikipedia.org/wiki/Clickjacking).

[We have the Content-Type-Options Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options) that instructs the clients that the mime type that has been set by the server is the correct one and should not 79

be changed.

We can now add the task that will handle the creation of the snippets directory if it doesn't exist, and deploy of the template. Edit nginx/tasks/configure.yml and append:

\- name: Validate the snippets directory exist

file:

path: /etc/nginx/snippets

state: directory

owner: root

group: root

\- name: Deploy the ssl-snippet

template:

dest: /etc/nginx/snippets/ssl-params.conf

src: ssl-params.conf.j2

owner: root

group: root

mode: 0644

Now comes the default server block template. When HTTPS is enabled, it will use the SSL snippet we created, and an extra snippet that will direct nginx where our certificates are. In our case, we have not set up a domain, or the SSL Certificates. Create the nginx/templates/ssl-default.conf.j2 file that houses the certificate paths. Update it as needed.

ssl\_certificate /etc/letsencrypt/live/domain.example.com/fullchain.pem; ssl\_certificate\_key /etc/letsencrypt/live/domain.example.com/privkey.pem; The default server block will include two extra location blocks that can be used to monitor PHP and Nginx. The first block is the PHP status and ping location block which will forward the request to PHP-FPM which will then output the status of the FPM pool and give ping responses for health checks.

The second block is for the Nginx status. These two block are useful when you need to attach some metrics to the server.

Let’s add the default variables that will be used by our server blocks to nginx/defaults/main.yml:

80

nginx\_default\_server\_root: "/var/www/app/current/public"

nginx\_default\_server\_name: "\_"

nginx\_default\_enable\_https: false

And the default server block template file, nginx/templates/default.j2: server {

listen 80 default\_server;

listen \[::\]:80 default\_server;

{% if nginx\_default\_enable\_https %}

listen 443 ssl http2 default\_server;

listen \[::\]:443 ssl http2 default\_server;

include snippets/ssl-params.conf;

include snippets/ssl-default.conf;

{% endif %}

root {{ nginx\_default\_server\_root }};

index index.php index.html index.htm index.nginx-debian.html; server\_name {{ nginx\_default\_server\_name }};

location / {

try\_files $uri $uri/ /index.php?$query\_string;

}

location ~ \\.php$ {

include snippets/fastcgi-php.conf;

fastcgi\_pass unix:/run/php/php{{ php\_version }}-fpm.sock;

}

location ~ /\\.ht {

deny all;

}

location ~ ^/(php\_status|php\_ping)$ {

access\_log off;

fastcgi\_param SCRIPT\_FILENAME $fastcgi\_script\_name;

include fastcgi\_params;

fastcgi\_pass unix:/run/php/php{{ php\_version }}-fpm.sock;

allow 127.0.0.1;

deny all;

}

81

 location /nginx\_status {

stub\_status on;

access\_log off;

allow 127.0.0.1;

deny all;

}

}

Notice: The access to /php\_status, php\_ping and nginx\_status is limited to localhost as described by the allow 127.0.0.1 directive.

We can now add the task that will deploy the server block to nginx/tasks/configure.yml

\- name: Validate the default server root directory exist

file:

path: "{{ nginx\_default\_server\_root }}"

state: directory

owner: www-data

group: www-data

\- name: Deploy the default server block

template:

dest: /etc/nginx/sites-available/default

src: default.j2

owner: root

group: root

mode: 0644

notify: restart nginx

That should do it! Our nginx settings should be able to give us the best of our servers. All that’s left now is to add some permissions to deploy user so that he can write to /var/www directory, and restart php-fpm without a sudo password. But before all that, let’s restart nginx and make sure everything is running as expected.

Open up the nginx handlers (nginx/handlers/main.yml) and add the restart handler which can be called from any role:

82

\---

\# handlers file for nginx

\- name: restart nginx

service:

name: nginx

state: restarted

Once done, run the playbook and see how it plays. The complete configure subtask:

\---

\- name: Check the available processor cores

shell: grep processor /proc/cpuinfo | wc -l

register: nginx\_core\_number

when: nginx\_worker\_processes is not defined

\- name: Set the nginx\_worker\_processes variable

set\_fact:

nginx\_worker\_processes: "{{ nginx\_core\_number.stdout\_lines\[0\] }}"

when: nginx\_worker\_processes is not defined

\- name: Validate the config directories exist

file:

path: "{{ item }}"

state: directory

owner: root

group: root

loop:

\- /etc/nginx/conf.d

\- /etc/nginx/sites-enabled

\- name: Validate the log directory exist

file:

path: /var/log/nginx

state: directory

owner: root

group: adm

\- name: Deploy custom nginx.conf

template:

dest: /etc/nginx/nginx.conf

src: nginx.conf.j2

owner: root

83

 group: root

mode: 0644

\- name: Generate 4096 bit DH Params

shell: "openssl dhparam -out {{ nginx\_dhparam\_location }} 4096"

args:

creates: "{{ nginx\_dhparam\_location }}"

\- name: Validate the snippets directory exist

file:

path: /etc/nginx/snippets

state: directory

owner: root

group: root

\- name: Deploy the ssl-snippet

template:

dest: /etc/nginx/snippets/ssl-params.conf

src: ssl-params.conf.j2

owner: root

group: root

mode: 0644

\- name: Deploy the default certificate configuration file

template:

dest: /etc/nginx/snippets/ssl-default.conf

src: ssl-default.conf.j2

owner: root

group: root

mode: 0644

\- name: Validate the server root directory exist

file:

path: "{{ nginx\_default\_server\_root }}"

state: directory

owner: www-data

group: www-data

\- name: Deploy the default server block

template:

dest: /etc/nginx/sites-available/default

src: default.j2

owner: root

group: root

mode: 0644

84

 notify: restart nginx

Finally, test out your installation by logging in to your server and creating a phpinfo index file: /var/www/app/current/public/index.php.

$ echo -e "<?php\\nphpinfo();" > /var/www/app/current/public/index.php Open your browser and confirm that you have liftoff! The PHP Info page should render.

85

The ACL Role

Now that we are done with setting up the server, we need to allow the deploy user to perform some actions without requiring a sudo password.

Edit the acl/tasks/main.yml file and add the following tasks.

\---

\# tasks file for acl

\- name: Set up facl for /var/www

acl:

path: /var/www

entity: www-data

etype: group

permissions: rwx

default: no

state: present

recursive: yes

\- name: Set up default facl for /var/www

acl:

path: /var/www

entity: www-data

etype: group

permissions: rwx

default: yes

state: present

recursive: yes

\- name: Allow www-data to restart php

lineinfile:

path: /etc/sudoers.d/wwwdata

line: "%www-data ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service php{{

php\_version }}-fpm restart,/usr/sbin/service php{{ php\_version }}-fpm reload"

create: yes

\- name: Change /var/www ownership

file:

path: /var/www

recurse: yes

group: www-data

owner: www-data

86

Great! You should be able to login as the deploy user and create, edit or delete files under /var/www, and be able to run sudo service php7.4-fpm restart without any password, call that awesome!

87

Testing & Deployment

88

Test Cases

A lot of people are scared of the term testing. We actually strive to run away from tests, yet they improve the uptime of our software by allowing them to fail before they are deployed. When we integrate CI/CD to our development pipeline, we will be at ease knowing that whatever we have deployed to production is actually working.

[For PHP, we will use PHP Unit which comes bundled up with most of the](https://phpunit.de/)

frameworks. If working on vanilla PHP, you can still require it using composer and test out your work.

89

Local Testing

Testing Laravel

[Let’s use Laravel](https://laravel.com) and set up a few tests. You can either use the Laravel Installer or composer create-project. For simplicity, let’s use the composer create-project.

$ composer create-project --prefer-dist laravel/laravel devops-app Now that we’ve got a working Laravel installation, we can create an endpoint that will receive some data, and store it in the database. This will allow us to test the database connectivity and interaction with our app.

Navigate to the project directory and edit the .env file. Include the correct database connection, then create a new model with its factory, migration and a resource controller:

$ php artisan make:model -mcrf Post

Model created successfully.

Factory created successfully.

Created Migration: 2020\_10\_29\_070516\_create\_posts\_table

Controller created successfully.

In the migration, add just one field, body, of type text. We will not focus on the creation of a full fledged application but only on the testing bit.

90

<?php

use Illuminate\\Database\\Migrations\\Migration;

use Illuminate\\Database\\Schema\\Blueprint;

use Illuminate\\Support\\Facades\\Schema;

class CreatePostsTable extends Migration

{

/\*\*

\* Run the migrations.

\*

\* @return void

\*/

public function up()

{

Schema::create('posts', function (Blueprint $table) {

$table->id();

$table->text('content');

$table->timestamps();

});

}

/\*\*

\* Reverse the migrations.

\*

\* @return void

\*/

public function down()

{

Schema::dropIfExists('posts');

}

}

Once done, we can migrate and create the table in our database. Using migrations as the blueprints for our database structure is very effective as there is no need of moving SQL files with data into GIT and then, to the server.

91

$ php artisan migrate

Migrating: 2014\_10\_12\_000000\_create\_users\_table

Migrated: 2014\_10\_12\_000000\_create\_users\_table (40.59ms)

Migrating: 2014\_10\_12\_100000\_create\_password\_resets\_table

Migrated: 2014\_10\_12\_100000\_create\_password\_resets\_table (32.51ms) Migrating: 2019\_08\_19\_000000\_create\_failed\_jobs\_table

Migrated: 2019\_08\_19\_000000\_create\_failed\_jobs\_table (16.03ms) Migrating: 2020\_10\_29\_070516\_create\_posts\_table

Migrated: 2020\_10\_29\_070516\_create\_posts\_table (0.06 seconds) We can now edit the PostFactory under database/factories and instruct the factory how it can create a Post.

92

<?php

namespace Database\\Factories;

use App\\Models\\Post;

use Illuminate\\Database\\Eloquent\\Factories\\Factory;

class PostFactory extends Factory

{

/\*\*

\* The name of the factory's corresponding model.

\*

\* @var string

\*/

protected $model = Post::class;

/\*\*

\* Define the model's default state.

\*

\* @return array

\*/

public function definition()

{

return \[

'content' => $this->faker->paragraphs(4, true),

\];

}

}

Done! Now create a new posts feature test. We'll write the test to perform whatever action we are envisioning the end user performing. In our case, we expect the end user to be able to create a new post, edit it and delete it.

Let’s add a composer script that will handle the running of the test.

Open up composer.json and add the following under scripts.

"test": \[

"./vendor/bin/phpunit"

\]

This script will migrate the database using the testing environment, then 93

run phpunit. To execute the script, simply run composer test.

Since we are using PHP Unit, we can configure our test environment using phpunit.xml which is present in the root of our project. Uncomment the two database variables: DB\_CONNECTION and DB\_DATABASE so that we run the tests using sqlite driver and memory as the location where the database will be stored for the duration of the test. This will also speed up the tests and prevent overriding any data that you might have in your actual database.

Ensure that the php section of your phpunit.xml looks similar to:

<php>

<server name="APP\_ENV" value="testing"/>

<server name="BCRYPT\_ROUNDS" value="4"/>

<server name="CACHE\_DRIVER" value="array"/>

<server name="DB\_CONNECTION" value="sqlite"/>

<server name="DB\_DATABASE" value=":memory:"/>

<server name="MAIL\_MAILER" value="array"/>

<server name="QUEUE\_CONNECTION" value="sync"/>

<server name="SESSION\_DRIVER" value="array"/>

<server name="TELESCOPE\_ENABLED" value="false"/>

</php>

Notice: You can add as many env variables as needed under the php section.

We will not implement authentication, but we’ll have a look at validation and form requests so that we can test when the input provided is not as expected.

[Create a Form Request](https://laravel.com/docs/validation#form-request-validation) [to handle the validation, and a Feature Test to contain](https://laravel.com/docs/testing)

the tests.

$ php artisan make:request PostRequest

Request created successfully.

$ php artisan make:test PostTest

Test created successfully.

Confirm that a new feature test has been created at

94

tests/Feature/PostTest.php with the default content:

<?php

namespace Tests\\Feature;

use Illuminate\\Foundation\\Testing\\RefreshDatabase;

use Illuminate\\Foundation\\Testing\\WithFaker;

use Tests\\TestCase;

class PostTest extends TestCase

{

/\*\*

\* A basic feature test example.

\*

\* @return void

\*/

public function testExample()

{

$response = $this->get('/');

$response->assertStatus(200);

}

}

We'll need to refresh the test database with every test we run so that the previously run test does not interfere with the next test. Laravel conveniently includes a [RefreshDatabase trait](https://laravel.com/docs/8.x/database-testing#resetting-the-database-after-each-test) that does this for us.

<?php

namespace Tests\\Feature;

use Illuminate\\Foundation\\Testing\\RefreshDatabase;

use Tests\\TestCase;

class PostTest extends TestCase

{

use RefreshDatabase;

}

95

The first test we shall write will be to check if a post can be created. Since we have a ready factory, we shall get the raw contents, make a POST request, and assert that the data has been successfully persisted in the database.

/\*\*

\* @return void

\*/

public function testCanCreatePost(): void

{

$post = Post::factory()->raw();

$this->assertEquals(0, Post::count());

$this->withExceptionHandling()

\->post(route('posts.store'), \[\])

\->assertSessionHasErrors(\['content'\]);

$this->assertEquals(0, Post::count());

$this->withoutExceptionHandling()

\->followingRedirects()

\->post(route('posts.store'), $post)

\->assertSuccessful();

$this->assertDatabaseHas('posts', \['content' => $post\['content'\]\]);

}

In the test above, we are first using the defined factory to generate for us a post. Since we want to test that the post has been created, we need to first confirm that it was not there before we made the request to create it.

Next, we test whether our validation works by passing an empty request body. Since we know that it should fail, we enable exception handling so that the Unprocessable HTTP Exception is rendered correctly. We also assert that the session has the expected errors. In the event that you’re using an API, you would assert that the JSON response has validation errors using assertJsonValidationErrors.

After making the request, we want to confirm that it did not erroneously persist the data and return errors, so we assert that there are still no posts in the database. We then send the correct data to the endpoint. We disable exception handling so that any error that is thrown is visible in the output.

96

This is also very useful when performing the CI/CD integrations as it will give you the correct output making it easier to debug. Once the request has been made, we assert that it was successful, and finally assert that the database has the generated post.

This test will definitely fail since we have no routes, no validation rules and no response from the controller, run it to confirm:

$ composer test

\> ./vendor/bin/phpunit

PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

..E 3 / 3

(100%)

Time: 00:00.568, Memory: 26.00 MB

There was 1 error:

1) Tests\\Feature\\PostTest::testCanCreatePost

Symfony\\Component\\Routing\\Exception\\RouteNotFoundException: Route

\[posts.store\] not defined.

...

So let’s add the routes to web.php or api.php depending on your implementation. In our case, we'll use web.php.

<?php

use App\\Http\\Controllers\\PostController;

use Illuminate\\Support\\Facades\\Route;

Route::view('/', 'welcome');

Route::resource('posts', PostController::class);

Next, edit the PostRequest to add the validation rules; setting the content field as a string that is required. We'll also authorise the creation of the post by returning true in the authorize function.

97

<?php

namespace App\\Http\\Requests;

use Illuminate\\Foundation\\Http\\FormRequest;

class PostRequest extends FormRequest

{

/\*\*

\* Determine if the user is authorized to make this request.

\*

\* @return bool

\*/

public function authorize()

{

return true;

}

/\*\*

\* Get the validation rules that apply to the request.

\*

\* @return array

\*/

public function rules()

{

return \[

'content' => \['required', 'string'\],

\];

}

}

The PostRequest can now be used on the store method of the PostController. The Form Request validates when it is resolved so no need of adding extra validation logic. This form request will also be used on the update method since the validation logic is the same when creating and updating.

The request can contain extra data that we do not need, so instead of using $request->all() we shall use $request->validated() to only get the sanitised data.

98

<?php

namespace App\\Http\\Controllers;

use App\\Http\\Requests\\PostRequest;

use App\\Models\\Post;

use Illuminate\\Http\\Response;

class PostController extends Controller

{

...

/\*\*

\* Store a newly created resource in storage.

\*

\* @param PostRequest $request

\*

\* @return Response

\*/

public function store(PostRequest $request)

{

Post::create($request->validated());

return redirect()->route('posts.index');

}

...

}

Next, set the post content field to be mass assignable. Open up the Post model, add the fillable property. This prevents mass assignment of properties. I personally prefer fillable over guarded so that I am always sure of what is being assigned.

99

<?php

namespace App\\Models;

use Illuminate\\Database\\Eloquent\\Factories\\HasFactory;

use Illuminate\\Database\\Eloquent\\Model;

class Post extends Model

{

use HasFactory;

protected $fillable = \['content'\];

}

The test should now run and pass, but don’t take my word for it, open up your terminal and run:

$ composer test

\> ./vendor/bin/phpunit

PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

... 3 / 3

(100%)

Time: 00:00.292, Memory: 28.00 MB

OK (3 tests, 8 assertions)

Great! We’ve got our first test running! So we’re sure a post can be created.

Let’s confirm that it can also be edited and deleted. Since we are using the RefreshDatabase trait, the database will be empty after running every test, so we will need to create a new post for every subsequent test.

100

 /\*\*

\* @return void

\*/

public function testCanEditPosts(): void

{

$post = Post::factory()->create();

$this->withExceptionHandling()

\->put(route('posts.update', \['post' => $post\]), \[\])

\->assertSessionHasErrors(\['content'\]);

$this->assertDatabaseHas('posts', \[

'id' => $post->id,

'content' => $post->content,

\]);

$postUpdate = Post::factory()->raw();

$this->withoutExceptionHandling()

\->followingRedirects()

\->put(route('posts.update', \['post' => $post\]), $postUpdate)

\->assertSuccessful();

$this->assertDatabaseHas('posts', \[

'id' => $post->id,

'content' => $postUpdate\['content'\],

\]);

}

We have created and persisted the post using the factory create method.

Then, we made a request that cannot be processed, asserted that it failed, and checked the database to ensure that whatever failed did not affect the database.

Next we create a new post content via the factory and persist it, asserting it was successful and that it’s present in the database.

Open up PostController and modify the update function to include the persistence code.

101

 /\*\*

\* Update the specified resource in storage.

\*

\* @param PostRequest $request

\* @param Post $post

\*

\* @return Response

\*/

public function update(PostRequest $request, Post $post)

{

$post->update($request->validated());

return redirect()->route('posts.index');

}

We added a route resource, so there’s no need of adding anything to the routes file. We can now run the test and assert that it passes as expected.

\> ./vendor/bin/phpunit

PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

.... 4 / 4

(100%)

Time: 00:00.321, Memory: 28.00 MB

OK (4 tests, 13 assertions)

We can now test whether a post can be deleted. We’ll add a new test and update the destroy function in our PostController. For this test, there is no payload to be sent with the delete request, so we will only have one request.

102

 /\*\*

\* @return void

\*/

public function testCanDeletePosts(): void

{

$post = Post::factory()->create();

$this->withoutExceptionHandling()

\->followingRedirects()

\->delete(route('posts.destroy', \['post' => $post\]))

\->assertSuccessful();

$this->assertDatabaseMissing('posts', \[

'id' => $post->id,

'content' => $post->content,

\]);

}

And the PostController:

/\*\*

\* Remove the specified resource from storage.

\*

\* @param Post $post

\*

\* @return Response

\*/

public function destroy(Post $post)

{

$post->delete();

return redirect()->route('posts.index');

}

We can now run the tests and confirm that it works.

103

$ composer test

\> ./vendor/bin/phpunit

PHPUnit 9.4.3 by Sebastian Bergmann and contributors.

..... 5 / 5

(100%)

Time: 00:00.355, Memory: 28.00 MB

OK (5 tests, 15 assertions)

Great! We have tested creating, updating and deleting a post. You can carry on and add the remaining tests to view all the posts, view one, view the create page and the edit page.

Here are the complete files:

Post Controller

<?php

namespace App\\Http\\Controllers;

use App\\Http\\Requests\\PostRequest;

use App\\Models\\Post;

use Illuminate\\Http\\Response;

class PostController extends Controller

{

/\*\*

\* Display a listing of the resource.

\*

\* @return Response

\*/

public function index()

{

//

}

/\*\*

\* Show the form for creating a new resource.

\*

\* @return Response

104

 \*/

public function create()

{

//

}

/\*\*

\* Store a newly created resource in storage.

\*

\* @param PostRequest $request

\*

\* @return Response

\*/

public function store(PostRequest $request)

{

Post::create($request->validated());

return redirect()->route('posts.index');

}

/\*\*

\* Display the specified resource.

\*

\* @param Post $post

\*

\* @return Response

\*/

public function show(Post $post)

{

//

}

/\*\*

\* Show the form for editing the specified resource.

\*

\* @param Post $post

\*

\* @return Response

\*/

public function edit(Post $post)

{

//

}

/\*\*

\* Update the specified resource in storage.

105

 \*

\* @param PostRequest $request

\* @param Post $post

\*

\* @return Response

\*/

public function update(PostRequest $request, Post $post)

{

$post->update($request->validated());

return redirect()->route('posts.index');

}

/\*\*

\* Remove the specified resource from storage.

\*

\* @param Post $post

\*

\* @return Response

\*/

public function destroy(Post $post)

{

$post->delete();

return redirect()->route('posts.index');

}

}

Post Test

<?php

namespace Tests\\Feature;

use App\\Models\\Post;

use Illuminate\\Foundation\\Testing\\RefreshDatabase;

use Tests\\TestCase;

class PostTest extends TestCase

{

use RefreshDatabase;

/\*\*

\* @return void

106

 \*/

public function testCanCreatePost(): void

{

$post = Post::factory()->raw();

$this->assertEquals(0, Post::count());

$this->withExceptionHandling()

\->post(route('posts.store'), \[\])

\->assertSessionHasErrors(\['content'\]);

$this->assertEquals(0, Post::count());

$this->withoutExceptionHandling()

\->followingRedirects()

\->post(route('posts.store'), $post)

\->assertSuccessful();

$this->assertDatabaseHas('posts', \['content' => $post\['content'\]\]);

}

/\*\*

\* @return void

\*/

public function testCanEditPosts(): void

{

$post = Post::factory()->create();

$this->withExceptionHandling()

\->put(route('posts.update', \['post' => $post\]), \[\])

\->assertSessionHasErrors(\['content'\]);

$this->assertDatabaseHas('posts', \[

'id' => $post->id,

'content' => $post->content,

\]);

$postUpdate = Post::factory()->raw();

$this->withoutExceptionHandling()

\->followingRedirects()

\->put(route('posts.update', \['post' => $post\]), $postUpdate)

\->assertSuccessful();

$this->assertDatabaseHas('posts', \[

'id' => $post->id,

107

 'content' => $postUpdate\['content'\],

\]);

}

/\*\*

\* @return void

\*/

public function testCanDeletePosts(): void

{

$post = Post::factory()->create();

$this->withoutExceptionHandling()

\->followingRedirects()

\->delete(route('posts.destroy', \['post' => $post\]))

\->assertSuccessful();

$this->assertDatabaseMissing('posts', \[

'id' => $post->id,

'content' => $post->content,

\]);

}

}

108

Automated Testing with GitLab CI/CD

We've successfully created the tests and run them locally. Now we want to create a pipeline that will handle the testing of our code for each commit

[that is pushed into GitLab](https://gitlab.com/). In case of a failure, we will get an email and if it was a merge request, it will warn you that the pipeline failed. With this set up, we will have a surety that the code deployed to production is stable.

We will need to build a Docker image that has all the requirements to run our Laravel code, doing our best to keep the environment as similar as possible.

To get started with Docker, please follow the installation and post installation instructions for your platform: [Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/), [Mac,](https://docs.docker.com/docker-for-mac/install/) [Windows. Once done, we can go](https://docs.docker.com/docker-for-windows/install/)

ahead and start building our docker image.

Building & Publishing the Docker Image

We'll try to have a docker image that is as close to our server environment as possible. We'll use the official [Ubuntu 20.04 image provided by Docker, and](https://hub.docker.com/_/ubuntu)

add our binaries and services there. Since we are using PHP7.4 on our server, we shall do the same on the docker image. These images come with the bare minimum required to run, so they will have a small file size.

To get started, create a Dockerfile in a docker directory in our project root.

$ mkdir docker

$ cd docker

$ touch Dockerfile

Open up the Dockerfile and instruct Docker that we are going to use a base image by using the [FROM directive. We'll then install a couple of system](https://docs.docker.com/engine/reference/builder/#from)

packages, then PHP packages, then enable the PHP packages and finally

[install Composer and Laravel Envoy](https://laravel.com/docs/envoy).

We shall chain our commands using the && operator and terminate our long lines using a backslash. When making Docker images, always make sure you clean out after performing apt requests as this will keep the image small.

[We will use the RUN directive to do the installs.](https://docs.docker.com/engine/reference/builder/#run)

109

Let’s get going. We shall follow similar steps to what we had when building up our server.

FROM ubuntu:20.04

LABEL maintainer="David Mjomba <smodavprivate@gmail.com>"

ENV DEBIAN\_FRONTEND noninteractive

ENV PHP\_VERSION 7.4

RUN apt update && \\

apt install -y software-properties-common curl \\

inetutils-syslogd build-essential pkg-config && \\

LC\_ALL=C.UTF-8 apt-add-repository ppa:ondrej/php -y && \\ apt-get update && apt install -y \\

php-pear \\

php-gettext \\

php-ast \\

php${PHP\_VERSION} \\

php${PHP\_VERSION}-bcmath \\

php${PHP\_VERSION}-bz2 \\

php${PHP\_VERSION}-curl \\

php${PHP\_VERSION}-cli \\

php${PHP\_VERSION}-dev \\

php${PHP\_VERSION}-fpm \\

php${PHP\_VERSION}-gd \\

php${PHP\_VERSION}-intl \\

php${PHP\_VERSION}-json \\

php${PHP\_VERSION}-mbstring \\

php${PHP\_VERSION}-mysql \\

php${PHP\_VERSION}-readline \\

php${PHP\_VERSION}-soap \\

php${PHP\_VERSION}-sqlite3 \\

php${PHP\_VERSION}-xml \\

php${PHP\_VERSION}-xsl \\

php${PHP\_VERSION}-zip \\

zip unzip g++ gcc git libmcrypt-dev libbz2-dev libmagickwand-dev \\ mcrypt imagemagick && \\

apt autoremove -y && \\

apt-get clean && \\

rm -rf /var/lib/apt/lists/\* && \\

pecl install imagick mcrypt redis && \\

curl --silent --show-error https://getcomposer.org/installer | php -- --

install-dir=/usr/local/bin --filename=composer && \\ composer global require laravel/envoy

110

The image we’re building will only have PHP since we are only going to run the PHP cli and use it to run Composer, PHPUnit and Laravel Envoy. If you do not have a [Docker Hub account, go ahead and create one. Once done, we](https://hub.docker.com/)

shall login to Docker Hub to be able to publish our container image. I prefer using Docker Hub over gitlab registry since it is available to all repositories and can also be shared by other people. Let’s get going! Run docker login and enter your hub credentials.

$ docker login

Username: awesome\_dude

Password:

Login Succeeded

We can now build our docker image and tag it as the latest. Make sure you are in the directory that contains the Dockerfile then build, tag and publish the docker image. Replace docker\_username with your actual Docker username and php74 with the PHP version you have used.

$ docker build -t docker\_username/php74:latest .

...

$ docker push docker\_username/php74

The push refers to repository ...

5bd5ae06fb33: Pushed

...

latest: digest: sha256:a80f55a4c34419490034e6...

In the first command, we set the context to the current directory by using the full stop at the end of the command. In case you wanted to build the container, and you were in a different directory than the Dockerfile, then you would replace the full stop with the path to the Dockerfile.

Once you’ve successfully built and deployed, you should be able to see a new php74 [repository under https://hub.docker.com/repositories tagged as](https://hub.docker.com/repositories)

latest. We can now use this image to run our gitlab tests.

Generating the .gitlab-ci.yml

Now that we have some tests and a docker image, we can enable Gitlab 111

CI/CD on our repository. Navigate to the devops Laravel project and create a new file, .gitlab-ci.yml. The YAML basics that were used with ansible will still be used on the .gitlab-ci.yml file.

$ touch .gitlab-ci.yml

The first directive we shall use is image, which instructs GitLab to pull a certain image and perform the tasks that follow on it. Let’s use the docker image we created:

image: docker\_username/php74:latest

Next, we have to figure out what other service our system will require. If we required redis and/or MySQL, we would need to pull them in as below, using MySQL 8 with the native password as the default authentication plugin. To set up these services, as you might have guessed, we shall use the services directive. The GitLab pipeline will first boot up the services, before it boots up the docker image we specified above. Let’s get cracking!

services:

\- name: redis:latest

alias: redis

\- name: mysql:8

alias: mysql

command: \[“--default-authentication-plugin=mysql\_native\_password"\]

We have aliased our services so that we can use them as environment variablea. Speaking of environment variables, let’s update them to match our current environment. We’ll use the variables directive and update the .env variables:

112

variables:

MYSQL\_DATABASE: homestead

MYSQL\_ROOT\_PASSWORD: secret

DB\_DATABASE: homestead

DB\_HOST: mysql

DB\_USERNAME: root

DB\_PASSWORD: secret

REDIS\_HOST: redis

REDIS\_PORT: 6379

Looking at the [official MySQL Docker Image docs](https://hub.docker.com/_/mysql), we get some variables that can be used to set up the container when it runs: MYSQL\_ROOT\_PASSWORD

sets the root password to be used and MYSQL\_DATABASE sets the database to be created once the service has booted. These two are also mapped to the DB\_PASSWORD and DB\_DATABASE env variables that are used by Laravel. The DB\_USERNAME will be root and if you have noticed, we changed the DB\_HOST to mysql to match the alias we used on the MySQL

service. We have also set the REDIS\_HOST to redis; the alias of the redis service; and the REDIS\_PORT to 6379; the default redis port.

Next, we shall define the jobs that make up the pipeline. Each job is treated independently and some jobs can:

be allowed to fail,

run only on a single branch,

only be manually triggered etc.

In situations where the preceding job is not allowed to fail; then it fails; the next job will not be executed. In our case, we shall have two Jobs: test and deploy.

stages:

\- test

\- deploy

It’s always nice to print out some debug information before running any scrips. For now, let’s print the PHP version before running the script: 113

before\_script:

\- php -v

We shall now run our feature tests to confirm that our app is fully functional.

feature\_tests:

stage: test

script:

\- cp .env.example .env

\- composer install

\- php artisan key:generate

\- composer test

In our feature test job, we have first assigned it to the test stage, then we have defined the console commands to be run. Since it’s a fresh clone of the repository, we first make a new .env file, run composer install, generate the application key then run or predefined composer script which in turn runs the test.

Since we have a redis service, we can set our cache and session drivers to redis. This can either be done at the variables level or by updating the

.env.example file. I prefer updating the .env.example since it will be used by anyone who clones the repository.

BROADCAST\_DRIVER=log

CACHE\_DRIVER=redis

QUEUE\_CONNECTION=sync

SESSION\_DRIVER=redis

We can now add our script that will handle the deployment to production. You can add another for the deployment to staging.

114

deploy\_production:

stage: deploy

script:

\- time

when: manual

only:

\- master

This is a dummy stage which we will run after the tests complete to make sure all is well. We have specified that it should only be run on master, and it’s triggered manually. This will prevent the automatic deployment of code to the server.

Notice: For the best pipeline experience, I would advise protecting the master branch from direct commits and running the deployment automatically by removing the when: manual part of the

configuration. After a merge request has been made, the tests will run.

Once merged to master, it will automatically deploy to the server.

For the remainder of this book, we shall assume that the deployment is manual, in order to document the actions that would otherwise be automated. Here's the current .gitlab-ci.yml file:

115

image: docker\_username/php74:latest

services:

\- name: redis:latest

alias: redis

\- name: mysql:8

alias: mysql

command: \["--default-authentication-plugin=mysql\_native\_password"\]

variables:

MYSQL\_DATABASE: homestead

MYSQL\_ROOT\_PASSWORD: secret

DB\_DATABASE: homestead

DB\_HOST: mysql

DB\_USERNAME: root

DB\_PASSWORD: secret

REDIS\_HOST: redis

REDIS\_PORT: 6379

stages:

\- test

\- deploy

before\_script:

\- php -v

feature\_tests:

stage: test

script:

\- cp .env.example .env

\- composer install

\- php artisan key:generate

\- composer test

deploy\_production:

stage: deploy

script:

\- time

when: manual

only:

\- master

We can now login to GitLab, and create a new repository. Once created, you will be given the repository location which we can add as our new 116

![](index-117_1.png)

![](index-117_2.png)

remote. Navigate to the DevOps Laravel directory and initialise a Git repository, add the new remote, make a commit and push to the server.

$ git init

Initialized empty Git repository in .../devops/.git/

$ git remote add origin git@gitlab.com:your\_awesome\_username/posts-test.git $ git add .

$ git commit -m 'adds gitlab ci/cd'

\[master (root-commit) e41dd42\] adds gitlab ci/cd

94 files changed, 8578 insertions(+)

create mode 100644 .editorconfig

create mode 100644 .env.example

create mode 100644 webpack.mix.js

...

$ git push origin master

Enumerating objects: 118, done.

Counting objects: 100% (118/118), done.

...

To gitlab.com:your\_awesome\_username/posts-test.git

\* \[new branch\] master -> master

Once you make the commit, the GitLab runners will scan the repository for a

.gitlab-ci.yml file and if present, it shall automatically execute the pipeline. Let’s check it out! Open your repository and navigate to CI/CD -> Pipelines. You should see one pipeline running:

Clicking on the pipeline will show you two jobs. Clicking on the feature\_test job will give you the console output of the job. Once the job is complete, you will get a successful green message: Job succeeded.

117

Awesome! Our first job has been completed successfully! You can go to the jobs page (CI/CD -> Jobs) and run the deploy production job. It should run smoothly! We can now set up our server to have access to GitLab and GitLab to have access to our server so that we can have the deployment job running as expected.

118

Automated Deployment with GitLab CI/CD

SSH Configuration

For the server to be able to read our repository, we need to get the deploy user’s public key and add it as a deployment key on GitLab. Next we shall take the deploy user’s private key and add it as a secret CI/CD variable so that our runners can be able to login to the server and make the necessary changes. Let’s log in to the server!

$ ssh -p 4033 deploy@123.45.6.78

$ cat ~/.ssh/id\_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQc... ansible-generated on devops-for-php-developers

Copy the key and navigate to your GitLab repository -> Settings -> Repository. You will find a Deploy Keys section. Expand it and in the form provided, paste the key you copied and give it a good title. Once done, click on Add key. This will allow the deploy user to be able to fetch the repository from GitLab but he cannot push back any changes.

Next, we can set up the repository secrets that will allow the GitLab runners to be able to log in to the server and pull the new changes. Open up the terminal and get the private SSH key for the deploy user:

$ cat ~/.ssh/id\_rsa

\-----BEGIN RSA PRIVATE KEY-----

MICDpZGu+H...

...gc8bN

\-----END RSA PRIVATE KEY-----

Navigate to your repository’s CI/CD settings (Settings -> CI/CD) and expand the Variables section. Set the Key as SSH\_KEY, paste the private key in the Value section, set the state as protected and save the variable.

Great! Now the GitLab runners will be able to log in to our server and pull the new changes! Let’s set up the directory structure that we will be using in 119

order to have zero downtime.

Directory Structure

In order to have zero downtime, we shall create a symbolic link pointing to the latest release of our application and point nginx to the symbolic link.

Since we will be deploying releases, we will need some of the data to persist across releases. In Laravel, the storage directory should persist across releases. To achieve that, we will keep a persistent folder that will hold our

.env file and storage directory. The desired structure will be as below:

/var/www/app/

persistent/

.env

storage/

releases/

20200101000000/

20200102000000/

current/ - symbolic link to latest release 20200102000000

We shall keep a maximum of 5 releases and delete the rest. In case we need something old, we can always re-deploy from GitLab.

120

Laravel Envoy

Laravel Envoy will be used to configure our server and generate any new directories and releases. It provides a clean, minimal syntax for defining common tasks you run on your remote servers. Using Blade style syntax, you can easily setup tasks for deployment, Artisan commands, and more.

We shall instruct it to create the app directories if they are missing and if the persistent directory is missing, it should first clone the repository to the releases directory, then copy over the needed files and directories to the persistent directory. Once the deployment is done, the script should remove the current directory and symlink it to the latest release.

To get started, create a new Envoy.blade.php file at the root of the devops Laravel app directory. In this file, we shall define the set of servers we are going to deploy to with their corresponding SSH ports. To make the envoy file configurable and reusable, we shall execute it with two options; the first will be the GitLab repository, and the second will be a JSON encoded list of servers. These two options will allow the envoy file to be used across repositories without the need of changing the file.

Before executing anything we shall do some setup. In the setup section, we’ll need to validate that the two options have been set. Secondly, we will setup the base paths as per our directory structure and check if the persistent storage exits so that we can create it if missing. After the setup, we shall define our servers list using the json decoded list of servers.

121

@setup

if (!$repo || !$servers) {

echo 'The repo and servers parameter is required';

die();

}

$servers = json\_decode($servers, true, JSON\_THROW\_ON\_ERROR); if (!$servers || count($servers) < 1) {

echo 'servers parameter should be a valid json array of servers.'; die();

}

$persistentDir = '/var/www/app/persistent';

$releasesDir = '/var/www/app/releases';

$appDir = '/var/www/app/current';

$release = date('YmdHis');

$newReleaseDir = $releasesDir .'/'. $release;

$persistentStorageExists = is\_dir($persistentDir . '/storage');

@endsetup

@servers($servers)

We can now setup our deploy story that will be called by the GitLab runner. You can have as many stories as needed. In our case, we only need the deploy story which will handle:

the cloning of the new release,

linking of the persistent storage and env file,

installing of composer (and yarn/npm) dependencies,

linking of the public storage directory,

migrating the database,

caching routes and configs,

activating the release as the current one and,

finally removing old releases.

122

@story('deploy')

cloneRelease

linkPersistentStorage

installDependencies

optimiseRelease

activateRelease

cleanup

@endstory

Each item in the story above is a task that will be run on each of the servers defined in the servers array. The good thing about Envoy is that you can incorporate your variables easily in any command you are running. Let’s setup all the tasks, performing the steps as we would manually do it. I have commented out the horizon termination since we have not setup supervisor

[and horizon. Checkout the docs](https://laravel.com/docs/horizon#deploying-horizon). The complete Envoy.blade.php file:

@setup

if (!$repo || !$servers) {

exit('The repo and servers parameter is required');

}

$servers = json\_decode($servers, true, JSON\_THROW\_ON\_ERROR); if (!$servers || count($servers) < 1) {

exit('servers parameter should be a valid json array of servers.');

}

$persistentDir = '/var/www/app/persistent';

$releasesDir = '/var/www/app/releases';

$appDir = '/var/www/app/current';

$release = date('YmdHis');

$newReleaseDir = $releasesDir .'/'. $release;

$persistentStorageExists = is\_dir($persistentDir . '/storage');

@endsetup

@servers($servers)

@story('deploy')

cloneRelease

linkPersistentStorage

installDependencies

optimiseRelease

activateRelease

@endstory

123

@task('cloneRelease')

echo 'Cloning repository into release {{ $release }}'

\[ -d {{ $releasesDir }} \] || mkdir -p {{ $releasesDir }}

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

ln -nfs {{ $persistentDir }}/.env {{ $newReleaseDir }}/.env ln -nfs {{ $persistentDir }}/storage {{ $newReleaseDir }}/storage

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

124

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

Great! We now have a working script that will handle our deployment.

However, we are missing the production env file and a database.

While in the Laravel app directory, generate a new application key then open up the .env file, SSH to the server and create a new .env file in the persistent folder. In the new file, paste the local .env content, then update the values as desired. Update the database configuration to match the database user and database name (either present or to be created). Our ansible script already created the /var/app/current directory and updated Nginx to point to it, so nothing needs to be done there.

125

$ php artisan key:generate

$ cat .env

APP\_NAME=Laravel

APP\_ENV=local

. . .

$ ssh -p 4033 deploy@123.45.6.78

Welcome to Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-70-generic x86\_64)

. . .

$ mkdir -p /var/www/app/persistent

$ vi /var/www/app/persistent/.env

\# paste the content

\# update the variables

. . .

DB\_DATABASE=posts

DB\_USERNAME=devops # username and password from the mysql ansible role DB\_PASSWORD=devops

BROADCAST\_DRIVER=log

CACHE\_DRIVER=redis

QUEUE\_CONNECTION=sync

SESSION\_DRIVER=redis

. . .

$ mysql -u root -p

Enter password: #enter the root password set by ansible

Welcome to the MySQL monitor. Commands end with ; or \\g.

mysql> create database posts;

Query OK, 1 row affected (0.00 sec)

mysql> exit;

Bye

That’s it for the pre-deployment setup. Now we need to configure our GitLab CI/CD to call envoy and update our codebase.

126

Deployment

Before we can deploy our new batch of changes, we need to add one more change to our routes file. Closures are not serializable thus, we need to remove all closures from our route files in order to cache them using php artisan route:cache. Open up routes/api.php and comment out the

/user endpoint.

// Route::middleware('auth:api')->get('/user', function (Request $request) {

// return $request->user();

// });

Next, we need to update our GitLab YAML file to include the call to Laravel Envoy. We had added one secret in the CI/CD variables which defined the private key of the deploy user that will allow the GitLab runners to log in to the servers and make changes using the envoy script. We will need to add a new variable that will hold our list of servers, call it ENVOY\_HOSTS. The value should be a JSON string of the servers you want to deploy to, for example:

\[{"web": "deploy@123.45.6.78 -p 4033"}\]

Use as many hosts as needed in the array. Next, let’s update the .gitlab-ci.yml file and setup the SSH agent and the private key that will be used to login to the server. Finally, we'll execute envoy and pass the repository and the servers list as parameters.

image: smodav/php74:latest

services:

\- name: redis:latest

alias: redis

\- name: mysql:8

alias: mysql

command: \["--default-authentication-plugin=mysql\_native\_password"\]

variables:

MYSQL\_DATABASE: homestead

MYSQL\_ROOT\_PASSWORD: secret

DB\_DATABASE: homestead

127

 DB\_HOST: mysql

DB\_USERNAME: root

DB\_PASSWORD: secret

REDIS\_HOST: redis

REDIS\_PORT: 6379

stages:

\- test

\- deploy

before\_script:

\- php -v

feature\_tests:

stage: test

script:

\- cp .env.example .env

\- composer install

\- php artisan key:generate

\- composer test

deploy\_production:

stage: deploy

script:

\- 'which ssh-agent || (apt-get update -y && apt-get install openssh-client

\-y)'

\- eval $(ssh-agent -s)

\- ssh-add <(echo "$SSH\_KEY")

\- mkdir -p ~/.ssh

\- '\[\[ -f /.dockerenv \]\] && echo -e "Host \*\\n\\tStrictHostKeyChecking no\\n\\n" > ~/.ssh/config'

\- ~/.config/composer/vendor/bin/envoy run deploy --repo=$CI\_REPOSITORY\_URL

\--servers="$ENVOY\_HOSTS"

when: manual #only for those who want “semi-CI/CD”

only:

\- master

That should do it! All that’s left is to create a new commit and let the runners do their magic. The manual deployment section is only if you have set when: manual.

128

![](index-129_1.png)

Manual Deployment

Once the first stage of the pipeline completes, you should be able to run the manual deployment stage. This stage can be re-run as many times as needed.

We can now go to our server and see if we have been successful in our endeavour. Open up your browser and navigate to you IP address: 123.45.6.78. You should be greeted by the Laravel Welcome page.

To test if our CI/CD pipeline really works, let’s change the Laravel welcome page to read DevOps is Awesome! instead of Laravel has wonderful...

then deploy it.

<div class="p-6">

<div class="flex items-center">

<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" class="w-8 h-8 text-gray-500"><path d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3

6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477

14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5

18c-1.746 0-3.332.477-4.5 1.253"></path></svg>

<div class="ml-4 text-lg leading-7 font-semibold"><a href="https://laravel.com/docs" class="underline text-gray-900 dark:text-white">Documentation</a></div>

</div>

<div class="ml-12">

<div class="mt-2 text-gray-600 dark:text-gray-400 text-sm"> DevOps is Awesome!

</div>

</div>

</div>

Let’s add a new commit:

129

$ git add .

$ git commit -m "changes greeting message"

$ git push origin master

We can now head to the GitLab CI/CD pipelines and deploy the manual job if using semi-CI/CD, and watch it work. Once the job has completed successfully, head over to your IP Address and confirm the changes are live.

And that wraps it up! You’ve managed to set up a server without writing any apt commands and now we have just completed a zero downtime setup that makes your life pretty easy. No need of logging in to the servers to do manual git fetches and migrations. Truth be told, we are humans and we tend to forget. Ever had a bug that takes you a day to debug only to realise you did not restart a given service? Well, with this automation, you only setup once and the rest is taken care of.

130

And There’s More!

It doesn’t stop there - PHP is just one of the languages you can use with this type of pipeline! The automation world is so huge you can automate anything that makes you feel like you’re wasting time. This is just the tip of the iceberg, go out and do wonders!

131

# Document Outline

*   [Contents](#index_split_000.html#p2)
*   [Preface](#index_split_000.html#p4) 
    *   [How this book is designed](#index_split_000.html#p5)
    *   [Who should read this book?](#index_split_000.html#p6)
    *   [Notice of Liability](#index_split_000.html#p7)
*   [Manual Server Setup](#index_split_000.html#p8) 
    *   [Finding the Right Server](#index_split_000.html#p9)
    *   [Server Updates](#index_split_000.html#p11)
    *   [Unattended Upgrades](#index_split_000.html#p12)
    *   [Installing Build Tools](#index_split_000.html#p14)
    *   [Setting Up MySQL Server](#index_split_000.html#p15)
    *   [Setting Up PHP 7.4](#index_split_000.html#p17)
    *   [Setting Up Redis Server](#index_split_000.html#p19)
    *   [Setting Up Nginx](#index_split_000.html#p20)
*   [Automated Server Setup using Ansible](#index_split_000.html#p24) 
    *   [What is Ansible?](#index_split_000.html#p25)
    *   [Setting up Ansible](#index_split_000.html#p26)
    *   [Ansible Inventory](#index_split_000.html#p28)
    *   [YAML Basics](#index_split_000.html#p30)
    *   [Ansible Playbooks](#index_split_000.html#p32)
    *   [Role Structure](#index_split_000.html#p36)
    *   [The Common Role](#index_split_000.html#p37)
    *   [The MySQL Role](#index_split_000.html#p54)
    *   [The PHP Role](#index_split_000.html#p61)
    *   [The Nginx Role](#index_split_000.html#p71)
    *   [The ACL Role](#index_split_000.html#p86)
*   [Testing & Deployment](#index_split_000.html#p88) 
    *   [Test Cases](#index_split_000.html#p89)
    *   [Local Testing](#index_split_000.html#p90)
    *   [Automated Testing with GitLab CI/CD](#index_split_000.html#p109)
    *   [Automated Deployment with GitLab CI/CD](#index_split_000.html#p119)
    *   [Laravel Envoy](#index_split_000.html#p121)
    *   [Deployment](#index_split_000.html#p127)
    *   [And There’s More!](#index_split_000.html#p131)