
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
