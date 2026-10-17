
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
