
```
"bgp.tmpl", "ntp.tmpl")
tmpl["base.tmpl"] = template.Must(files, nil)
_ = tmpl["base.tmpl"].ExecuteTemplate(
  os.Stdout, "base", config)
}
```

下方的输出显示了合并后的数据和模板。

```
hostname router1

router 1234
  router-id 4.4.4.4
  neighbor 1.1.1.1 remote-as 1
  neighbor 2.2.2.2 remote-as 2

ntp source-interface Loopback0
ntp server 11.11.11.11 prefer
ntp server 22.22.22.22
```

## 第 4 章：HTTP 客户端

超文本传输协议（HTTP）客户端用于建立连接并向 HTTP 服务器请求数据。最常用的方法是 GET 和 POST。http 包支持 RFC 2616 中定义的属性，如超时、重定向和 Cookie。虽然该包提供了更基本的方法，如 `http.Client.Get()` 和 `http.Client.Post()` 方法，但为了应用自定义请求头，可以将 `http.NewRequest()` 函数与 `http.Client.Do()` 方法结合使用。本章将通过使用更常见的功能（如客户端超时、Cookie 和自定义请求头）示例，演示 GET 和 POST 请求。

本章将涵盖以下 HTTP 客户端主题：

-   GET 请求
-   POST 请求

### 4.1：GET

http 包支持 RFC 7231 第 4.3.1 节中定义的 GET 方法。简单的 GET 请求可以使用 `http.Client.Get()` 方法完成；如果需要自定义请求头，则可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数设置方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置一个请求头。接下来，在 `http.Client` 结构体中初始化 Timeout 字段，返回一个新的 `http.Client` 对象。现在，GET 请求已根据 URL 构建，客户端请求头也已定义，将它们与自定义超时一起使用，通过 `http.Client.Do()` 方法发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法接收 Response 对象，并在打印响应之前关闭请求体。

```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
	"time"
)

func main() {
	req, _ := http.NewRequest("GET",
		"http://example.com", nil)
	
	req.Header.Set("Cache-Control", "no-cache")
	
	client := &http.Client{Timeout: time.Second * 10}
	
	resp, _ := client.Do(req)
	body, _ := ioutil.ReadAll(resp.Body)
	resp.Body.Close()
	
	fmt.Printf("%s\n", body)
}
```

### 4.2：POST

http 包支持 RFC 7231 第 4.3.3 节中定义的 POST 方法。简单的 POST 请求可以使用 `http.Client.Post()` 方法完成。如果需要自定义请求头，可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数定义方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置请求头。接下来，在 `http.Cookie` 结构体中定义 Cookie 的 Name 和 Value 字段，返回一个新的 Cookie 对象，并通过 `http.Request.AddCookie()` 方法将其添加到请求中。然后，在 `http.Client` 结构体中设置 Timeout 字段，并返回一个新的 `http.Client` 对象。现在，POST 请求已构建，请求头已设置，将它们与新的客户端一起使用，在 `http.Client.Do()` 方法中发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法返回 Response 对象，并在打印响应之前关闭请求体。

```go
package main

import (
	"bytes"
	"fmt"
	"io/ioutil"
	"net/http"
	"time"
)

func main() {
	url := "http://example.com"

	data := []byte(`{"hello":"world"}`)

	req, _ := http.NewRequest("POST",
		url, bytes.NewBuffer(data))
	req.Header.Set(
		"Content-Type", "application/json")

	cookie := http.Cookie{
		Name:  "cookie name",
		Value: "cookievalue",
	}
	req.AddCookie(&cookie)

	client := &http.Client{Timeout: time.Second * 10}

	resp, _ := client.Do(req)

	body, _ := ioutil.ReadAll(resp.Body)
	resp.Body.Close()

	fmt.Printf("%s\n", body)
}
```

## 第 5 章：SSH 客户端

安全外壳协议（SSH）常用于在远程服务器上执行命令。它也可以用于通过安全文件传输协议（SFTP）传输文件。虽然 ssh 包不是 Go 标准库的一部分，但它是由 Go 团队编写和支持的官方 SSH 包。ssh 包支持多种认证方法，例如使用密码或私钥。本章将通过演示执行命令和传输文件的示例，涵盖这两种认证形式。

本章将涵盖以下 SSH 客户端主题：

-   使用私钥认证的单个命令
-   使用密码认证的多个命令
-   使用密码认证的 SFTP 文件复制

### 5.1：使用私钥认证的单个命令

ssh 包支持私钥认证。这种认证形式比简单密码更安全，因为它难以被暴力破解，并且无需记住或写下密码。

为了准备这个示例，使用 `ssh-keygen` 工具在本地机器上生成公钥和私钥。`ssh-keygen` 在大多数 Linux 或 Mac 安装中可用。该工具创建公钥（`id_rsa.pub`）和私钥文件（`id_rsa`），如下所示。

```bash
$ ssh-keygen -b 4096
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/username/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/username/.ssh/id_rsa.
Your public key has been saved in /Users/username/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:2Bx44V(8c61...BeawULC+z919UW5F username@mycomputer.local
The key's randomart image is:
+----[RSA 4096]----+
| o.@=...ooo |
| o.*+@+ oO |
| ..=.*= oB |
| .o+=.o& Eo |
| + To.+., |
| o .o |
| , |
| |
+----[SHA256]-----+
```

接下来，使用 `ssh-copy-id` 工具将公钥（`id_rsa.pub`）复制到远程主机。它将放置在该主机的 `~/.ssh/authorized_keys` 文件中。

```bash
$ ssh-copy-id remotehost

/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed:
"/Users/username/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys

Password:

Number of key(s) added: 1
```

现在尝试登录该机器，使用：`"ssh 'remotehost'"`
并检查是否只添加了您想要的密钥。

现在，公钥已在远程主机上，私钥已在本地就位，两个密钥均已正确准备用于私钥认证。

接下来，为了准备验证远程主机的身份，使用 `ssh-keyscan` 工具将远程主机公钥获取为 `known_hosts` 文件格式的指纹。如果本地机器之前通过 SSH 连接过该主机，指纹可能已经存在于本地 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAAAE...jJHN
```

本示例开始于将远程主机公钥复制到一个变量中，该变量将用于在客户端配置中验证远程主机并防止欺骗。使用 `ssh.ParseKnownHosts()` 函数，以 `known_hosts` 文件格式解析公钥。出于简化的目的，密钥是硬编码的；然而，在实际应用中，它可能从文件或数据库中解析。

接下来，使用 `ioutil.ReadFile()` 函数读取私钥文件，并以字节切片形式返回。然后，它与密码一起在 `ssh.ParsePrivateKeyWithPassphrase()` 函数中使用，以获取一个 Signer 实例。然后，通过添加用户名，然后将 Signer 签名添加到 `ssh.PublicKeys()` 函数中进行认证，构建 `ssh.ClientConfig` 结构体。接下来，使用 `ssh.FixedHostKey()` 函数定义 `HostKeyCallback` 以进行授权。最后，设置建立 TCP 连接的最大时间作为 Timeout 值，其中零表示无超时。

请注意，通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数，可以选择绕过远程主机授权，但此不安全函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以在 `ssh.ClientConfig` 结构体中可选地定义可接受的密钥类型和加密列表，以及优先级顺序。由 `KeyAlgoXxxx` 常量标识的密钥类型将定义为 `HostKeyAlgorithms` 切片中的值。可接受的加密列表将在嵌入在 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在，`ssh.ClientConfig` 结构体已构建，它与远程主机一起使用，通过 `ssh.Dial()` 函数启动 SSH 连接，返回一个 `ssh.Client` 实例。接下来，使用 `ssh.Client.NewSession()` 方法创建一个新的会话，然后将其映射到终端的本地标准输出和错误，以便进行演示。最后，使用 `ssh.Session.Run()` 函数在远程主机上运行命令，然后调用 `ssh.Session.Close()` 方法终止连接。

```go
package main

import (
	"golang.org/x/crypto/ssh"
	"io/ioutil"
	"os"
	"time"
)
```
