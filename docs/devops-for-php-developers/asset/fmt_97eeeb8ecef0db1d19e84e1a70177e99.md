
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

And that should do it for PHP. Only two things left: a handler for restarting PHP once all the tasks have been completed and adding the subtasks into the main task. The handler will listen to the `restart php-fpm` event then handle the restart for us. Edit `php/handlers/main.yml`:

```
---
# handlers file for php
- name: restart php-fpm
  service:
    name: "php{{ php_version }}-fpm"
    state: restarted
```

Finally, update our `php/tasks/main.yml` task file and add our subtasks. Remember to restart PHP-FPM when the configuration subtask is done:

```
---
# tasks file for php
- name: Install PHP
  import_tasks: installs.yml
- name: Configure PHP
  import_tasks: configure.yml
  notify: restart php-fpm
```

# The Nginx Role

[Nginx is available as a distribution package and can also be installed via the official PPA](https://www.nginx.com/). The distribution package is not always up to date, so let’s use the PPA. We shall have two subtasks, one for the installation, and the other to configure Nginx. I’ve provided an optimised `nginx.conf` file, and a sample default server block that has some extra optimisations.

To set up the `worker_processes` configuration value, we shall use the number of cores available in the current server. This value shall be extracted and saved in the `nginx_worker_processes` variable if it is undefined. If you would prefer to use your own value and disable the auto calculation, add the `nginx_worker_processes` variable to the playbook variables and assign it a value.

So let’s get going! Create the two subtasks; `installs.yml` and `configure.yml`; and add them to the nginx main.yml task file.

```
---
# tasks file for nginx
- name: Install nginx
  import_tasks: installs.yml
- name: Configure Nginx
  import_tasks: configure.yml
```

## Installs Subtask

We can now open up `nginx/tasks/installs.yml` and add the official Nginx PPA, install it and set it to run on system boot.

```
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

That’s it for our installs subtask! Pretty fast hey?

## Configure Subtask

Next, we open up the `nginx/tasks/configure.yml` file and setup the worker process auto calculation tasks to run only when the `nginx_worker_processes` variable is undefined.

```
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

We can now add our `nginx.conf` template file under `templates/nginx.conf.j2`.

```
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

Great! The above config disables server tokens so that we keep our Nginx details private, and enables the resetting of timed out connections so that we can have as much memory reuse as possible. Let’s add the variables that are to be used by the config to the `nginx/defaults/main.yml` file.

```
---
# defaults file for nginx
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

As stated before, in case you want to set the `worker_processes`, you will need to edit the `sites.yml` file and add the `nginx_worker_processes` variable as below:

```
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

We can now add tasks to the `nginx/tasks/configure.yml` file, that will validate that the two config and log directories are present and handle the creation if missing (`/etc/nginx/conf.d`, `/etc/nginx/sites-enabled` and `/var/log/nginx`). The other task will handle the deploying of our custom `nginx.conf` template.

```
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

Notice: If using User Isolation, set the `nginx_user` and owner of
