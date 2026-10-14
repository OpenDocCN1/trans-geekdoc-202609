
# 安装 PHP 包

```yaml
- name: Install PHP packages
  apt:
    name: "{{ php_packages | default([]) }}"
    state: latest
```

# 更新 PECL 协议

```yaml
- name: Update PECL protocols
  shell: pecl channel-update pecl.php.net
```

# 安装 PECL 包

```yaml
- name: Install PECL Packages
  shell: yes '' | pecl install -s --force {{ item }}
  loop: "{{ php_pecl_install }}"
```

按照 [Composer 官方文档](https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md) 中的程序化安装方法，创建一个新脚本并保存为 `files/install_composer.sh`。我们将执行该脚本并注册输出，以此判断安装是否成功。若成功，则将生成的 `composer.phar` 文件移动至 `/usr/local/bin/composer`。

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

# 配置子任务

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

```ini
; configuration for php {{ item.name }} module
; priority={{ item.priority }}
extension={{ item.name }}.so
```

为稳妥起见，添加任务以确认 PHP 自定义配置目录确实存在。

```yaml
---
# php/tasks/configure.yml
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

此模板将替换 `mods-available` 目录下的 `opcache.ini` 文件。该文件会自动符号链接到 `cli` 和 `fpm` 目录，其余工作自动完成。

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
