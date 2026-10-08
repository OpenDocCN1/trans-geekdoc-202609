

## 在 UNIX 609 下安装 Apache、PHP 和 MySQL

- 找到以 #ServerName 开头的一行，并将其简单改为 Serverusername.com
- 找到包含 AddType 的行块，并添加以下内容，以确保 PHP 扩展名的文件能够正确通过 PHP 模块进行处理：

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phpps
```

现在你已经准备好启动 Apache 服务器以检查它是否支持 PHP。首先，让我们在不开启 SSL 支持的情况下启动服务器，看看它能否启动。在接下来的章节中，我们将检查 PHP 支持和 SSL 支持，以确保一切运行正常。

你可以使用 configtest 来检查配置是否设置正确：

```
# cd /usr/local/apache2/bin
# sudo ./apachectl configtest
Syntax OK
# sudo ./apachectl start
/apachectl start: httpd started
```

如果运行正常，当你用 Web 浏览器连接到服务器时，将看到类似于图 A.3 的界面。请检查两种情况，以确保一切工作正常。

> 注意
> 你可以使用域名或计算机的实际 IP 地址连接到服务器。检查这两种情况以确保一切运行正常。

![](img/654520c37415debd4290b9b4aa2c03f2_640_0.png)

图 A.3 Apache 提供的默认测试页

## 录 A 安装 Apache、PHP 和 MySQL

### # PHP 支持正常吗？

现在你已经确定 Apache 服务器可以独立运行，可以测试它的 PHP 支持了。在文档根路径下创建一个名为 test.php 的文件，如果你遵循了上面的安装说明，该路径应该是 /usr/local/apache/htdocs。请注意，你可以在 httpd.conf 文件中更改此目录路径。

该文件应仅包含以下一行代码：
<?php phpinfo(); ?>

输出结果应该类似于图 A.4。

![](img/654520c37415debd4290b9b4aa2c03f2_641_0.png)

图 A.4 phpinfo() 函数提供了有用信息

### # SSL 正常吗？

在此阶段，你的机器上不应该可以正常工作，因为我们还没有创建配套的 SSL 证书和密钥。Apache 已经配置并就绪，但保护你数据的底层证书尚不存在。

## 在 UNIX 下安装 Apache、PHP 和 MySQL

你可以使用 OpenSSL 为开发目的创建自签名证书；如果你打算在生产环境中使用网站，应该使用由证书颁发机构签署的 SSL 证书。例如，Let's Encrypt 是由互联网安全研究小组 (ISRG) 为公共利益提供的免费、自动化且开放的证书机构 (CA)。可以在 https://letsencrypt.org 了解更多信息。

要创建自签名证书，请使用以下命令创建证书并将它们放在 Apache 预期的位置：

```
# openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /usr/local/apache2/conf/server.key \
-out /usr/local/apache2/conf/server.crt
```

证书和密钥创建脚本会询问有关国家、州、公司名称和域名的信息；你可以根据意愿填写虚拟信息或真实信息。重启后，你将获得一个有效期为 365 天的虚拟自签名证书，并位于 /usr/local/apache2/conf，连同其匹配密钥。

Apache SSL 模块有自己的配置文件，位于 /usr/local/apache2/conf/extra/httpd-ssl.conf。你可以保持其不变，只需重启 Apache 以使所有更改生效，也可以根据需要继续修改配置。关于 Apache httpd-ssl.conf 修改的文档，请参阅 http://apache.org/docs/2.4/mod_ssl.html。

在 Apache 2.4 中，启用 SSL 仅需取消 httpd.conf 中以下几行的注释即可：

```apache
LoadModule ssl_module modules/mod_ssl.so
Include conf/extra/httpd-ssl.conf
```

进行更改后，重启服务器以查看 SSL 是否工作正常。你可以使用 configtest 来检查配置是否设置正确：

```
# cd /usr/local/apache2/bin
# sudo ./apachectl configtest
Syntax OK
# sudo ./apachectl start
```

如果运行正常，当你用 Web 浏览器连接到服务器时，将看到类似于图 A.3 的界面。请检查两种情况，以确保一切工作正常。

> 注意
> 你可以使用域名或计算机的实际 IP 地址连接到服务器。检查这两种情况以确保一切运行正常。

![](img/654520c37415debd4290b9b4aa2c03f2_640_0.png)

