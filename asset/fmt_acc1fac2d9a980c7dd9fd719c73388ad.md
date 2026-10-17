
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
