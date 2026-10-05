

## 16.7. 设置服务器

```
RestartSec=30

[Install]
WantedBy=multi-user.target
```

这与我们为 Caddy 创建的服务文件大致相同，不再是在 ExecStart 中运行 Caddy 二进制文件，而是运行一个名为“server”的二进制文件，它位于 /root/app 目录下。

我们还没有构建该二进制文件，但每当我们编写部署脚本时，它会将我们的源代码上传到服务器并为我们构建二进制文件。然后我们就可以使用二进制文件重启 systemd 服务，以发布新版本的 Web 应用程序。

现在，我们需要重新加载 systemctl 并启用我们的服务。

```bash
$ systemctl daemon-reload
$ systemctl enable lenslocked.com.service
```

我们现在不会尝试运行此服务，因为我们还没有可以运行的二进制文件。我们将在下一节学习如何创建它并重启（或首次启动）我们的服务。

### 16.7.6 设置生产配置

我们需要在生产服务器上创建一个配置文件供应用程序使用。与 Caddyfile 不同，这个文件**我不会**存储在你的版本控制中。相反，它应该只存储在生产服务器上，并仅供非常信任的人员访问。

如果你还没有登录服务器，请通过 SSH 登录。

```bash
$ ssh root@123.123.22.33
```

在运行应用程序的 /root/app 目录下创建 .config 文件。

```bash
$ nano /root/app/.config
```

在其中填入有效的应用程序的配置文件。大部分必要的更改如下所示，但生成你自己的 pepper 和 HMAC 密钥是一个好主意。 PostgreSQL 使用的密码可能不同。

```json
{
  "port": 3000,
  "env": "prod",
  "pepper": "replace-this-with-a-secret-pepper",
  "hmac_key": "replace-this-with-a-secret-hmac-key",
  "database": {
    "host": "localhost",
    "port": 5432,
    "user": "postgres",
    "password": "replace-this-with-the-password-from-earlier",
    "name": "lenslocked-prod"
  }
}
```

注意：你的数据库密码将是在你设置 PostgreSQL 时运行 `ALTER USER ...` 命令时设置的那个。

按 ctrl-x  nano，然后按 y 确认，最后按回车确认我们使用提供的原始文件名。

### 16.7.7 创建部署脚本

在本节中，我们将创建一个部署脚本，它将执行以下操作：

1. 将我们的源代码复制到生产服务器。
2. 在生产服务器上构建 Web 应用程序。
3. 将二进制文件和任何资源（图像、css 等）复制到 /root/app 目录。
4. 在生产服务器上重启我们的 Web 应用程序。

注意：我们的部署脚本将是一个 bash 文件，在 Windows 下没有经过测试。如果你遇到问题，请随时寻求帮助。

首先，我们需要创建一个 scripts 目录，用于存储部署脚本以及我们以后创建的任何其他脚本。一旦有了目录，我们将创建一个 bash 发布脚本文件，并赋予其可执行权限，这样我们就可以运行它，而不是仅仅作为文本文件打开。

```bash
mkdir scripts
atom scripts/release.sh
# 保存文件后...
# 将其设为可执行
chmod +x scripts/release.sh
```

注意：我们将在自己的源代码中进行此操作，因此请确保先登出生产服务器。

我们首先告诉计算机这是一个应该用 bash 二进制文件运行的 bash 脚本。这一行应该位于你部署脚本的最顶部。

```bash
#!/bin/bash
```

接下来，我们要确保在正确的源代码目录中进行工作。

```bash
# 切换到计划工作的代码目录
cd "$GOPATH/src/lenslocked.com"
```

之后，我们可以通过删除存在的二进制文件来开始发布。我倾向于在构建时将其命名为 lenslocked.com，这就是我们要删除的内容。我们并不是删除 lenslocked.com 目录。

```bash
echo "==== Releases lenslocked.com ===="
echo "删除本地二进制文件（以防被上传）..."
rm lenslocked.com
echo "Done!"
```

我们将把源代码上传到服务器进行构建，但首先我们应该删除服务器上的任何源代码，以确保没有从之前的构建中遗留的文件。

```bash
echo "删除现有代码..."
sh root@123.123.22.33 "rm -rf /go/root/src/lenslocked.com"
echo "代码删除成功!"
```

之后我们可以上传源代码。我们将使用 rsync，这是一用于在不同服务器之间传输和同步文件的极其有用的工具。如果你从未用过它，我强烈建议你深入研究。

目前，我想说的是这些参数

