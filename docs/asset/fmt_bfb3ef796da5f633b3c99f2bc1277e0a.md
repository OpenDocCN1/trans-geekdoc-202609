
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
