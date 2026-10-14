
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
# handlers file for common
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
# tasks for users.yml
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
# tasks for security
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

# 使用别名
$ echo 'alias devops="ssh -p 4033 deploy@123.45.6.78"' >> ~/.bashrc
$ source ~/.bashrc
$ devops # 这将调用上述别名

# 使用 ssh config
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
# mysql/handlers/main.yml
- name: restart mysql
  service:
    name: mysql
    state: restarted
```

### 配置子任务
