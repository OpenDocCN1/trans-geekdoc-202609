
# 创建 MySQL 配置文件

在 `mysql/tasks` 下创建一个新的任务文件 `configure.yml`，在 `mysql/templates` 下创建一个新的模板文件 `my.cnf.j2`。该模板将用于修改 Percona 自带的默认 `my.cnf` 文件。

## `templates/my.cnf.j2`

```
[mysqld]
default-authentication-plugin={{ default_authentication_plugin }}

# 禁用符号链接以防止各种安全风险
symbolic-links = 0

# 内存设置。
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

# InnoDB 设置。
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

## `defaults/main.yml`

```yaml
---
# mysql 的默认文件
# caching_sha2_password 是默认值，但大多数客户端不支持它
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

## `mysql/tasks/configure.yml`

```yaml
---
# mysql/tasks/configure.yml
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

## `templates/root-my.cnf.j2`

```
[client]
user="root"
password="{{ mysql_root_password }}"
```

剩下的就是将这两个子任务包含到 `mysql/tasks/main.yml` 中。

## `mysql/tasks/main.yml`

```yaml
---
# tasks file for mysql
- name: Handle Percona Installation
  import_tasks: percona.yml

- name: Configure the database engine
  import_tasks: configure.yml
```

这应该能搞定我们的 MySQL 服务器。你应该能够使用设置的密码登录 MySQL，其他创建的用户也应该能够登录。

# PHP 角色

设置 PHP 通常很简单。由于我们使用的是 PHP 7.4，我们可以选择使用 Debian 维护的版本或 Ondrej 的 PPA，但既然很多人喜欢拥有灵活性，我们就使用后者。我们将设置 PHP、[Composer](https://getcomposer.org/) 并配置诸如 `opcache` 之类的模块。

## 安装子任务

添加一个新的子任务 `installs.yml`，用于存放 PHP 和其他所需二进制文件的安装。我们将从源码编译一些模块，如 `redis`。要安装的包列表将在 `php/defaults/main.yml` 中定义。

## `php/defaults/main.yml`

```yaml
---
# defaults file for php
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

## `php/tasks/installs.yml`

```yaml
---
- name: Add Ondrej PPA
  apt_repository:
    repo: ppa:ondrej/php
    state: present
    update_cache: yes
    mode: "0666"
```
