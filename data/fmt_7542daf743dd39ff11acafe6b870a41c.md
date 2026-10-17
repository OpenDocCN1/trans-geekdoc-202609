
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

# 第 5 章：SSH 客户端

安全外壳协议（SSH）常用于在远程服务器上执行命令。它也可以用于通过安全文件传输协议（SFTP）传输文件。虽然 `ssh` 包不是 Go 标准库的一部分，但它是由 Go 团队编写和支持的官方 SSH 包。`ssh` 包支持多种认证方法，例如使用密码或私钥。本章将通过演示执行命令和传输文件的示例，涵盖这两种认证形式。

本章将涵盖以下 SSH 客户端主题：

- 使用私钥认证的单个命令
- 使用密码认证的多个命令
- 使用密码认证的 SFTP 文件复制

## 5.1：使用私钥认证的单个命令

`ssh` 包支持私钥认证。这种认证形式比简单密码更安全，因为它难以被暴力破解，并且无需记住或写下密码。

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

```go
func main() {
    user := "username"
    pass := []byte("password")
    remotehost := "remotehost:22"
    cmd := "hostname"
    privkeyfile := "/Users/username/.ssh/id_rsa"
    knownhost := []byte(
        "remotehost ecdsa-sha2-nistp256 AAE...jZHN")

    _, _, hostkey, _, _ := ssh.ParseKnownHosts(
        knownhost)

    privkeydata, _ := ioutil.ReadFile(privkeyfile)

    parsekey := ssh.ParsePrivateKeyWithPassphrase
    privkey, _ := parsekey(privkeydata, pass)

    config := &ssh.ClientConfig{
        User: user,
        Auth: []ssh.AuthMethod{
            ssh.PublicKeys(privkey),
        },
        HostKeyCallback: ssh.FixedHostKey(hostkey),
        Timeout: 5 * time.Second,
    }
    conn, _ := ssh.Dial("tcp", remotehost, config)

    sess, _ := conn.NewSession()

    sess.Stdout = os.Stdout
    sess.Stderr = os.Stderr

    _ = sess.Run(cmd)

    sess.Close()
}
```

## 第 5.2 章：使用密码认证执行多个命令

接下来的示例首先收集用于验证远程主机身份并构建客户端配置的远程主机公钥。

与前面的示例一样，远程主机公钥是以 `known_hosts` 文件格式的指纹形式获取的，使用 `ssh-keyscan` 实用工具。同样，如果本机之前通过 SSH 连接过该主机，它也可能存在于本地的 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAE...jZHN
```

接下来，远程主机公钥被复制到客户端配置中用于防止欺骗的变量中。然后，使用 `ssh.ParseKnownHosts()` 函数以 `known_hosts` 文件格式解析该公钥。为了简化起见，密钥是硬编码的，但在实际操作中，可以从文件或数据库中解析。同样，虽然本例中用户名的密码是硬编码的，但在生产环境中应使用更安全、更便捷的方式获取。接下来，通过添加用户名，然后将密码加入 `ssh.Password()` 函数进行身份验证，构建 `ssh.ClientConfig` 结构体。通过定义带有 `ssh.FixedHostKey()` 函数的 `HostKeyCallback` 来启用授权。最后，设置 TCP 连接建立的最大时间作为 `Timeout` 值，其中零表示无超时。

请注意，可以通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数来选择绕过远程主机授权，但是，这种不安全的函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以选择在 `ssh.ClientConfig` 结构体中定义可接受的密钥类型和加密算法列表以及偏好顺序。由 KeyAlgoXxxx 常量识别的密钥类型将作为 `HostKeyAlgorithms` 切片中的值进行定义。可接受的加密算法列表将在嵌入到 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在 `ssh.ClientConfig` 结构体已构建完成，它与远程主机一起使用，通过调用 `ssh.Dial()` 函数返回 `ssh.Client` 实例来启动 SSH 连接。接下来，使用 `ssh.Client.NewSession()` 方法创建新会话，然后将其映射到终端的本地标准错误和标准输出，以便演示。然后，使用 `ssh.Session.Shell()` 方法在远程主机上启动 shell 以运行命令。最后，执行命令，并使用 `ssh.Session.Wait()` 方法等待命令执行完毕，然后调用 `ssh.Session.Close()` 方法关闭会话并终止连接。

```go
package main

import (
    "fmt"
    "golang.org/x/crypto/ssh"
    "os"
    "time"
)

func main() {
    user := "username"
    pass := "password"
    remotehost := "remotehost:22"
    knowhost := []byte(
        "remotehost ecdsa-sha2-nistp256 AAE...jZHN")

    _, _, hostkey, _, _ := ssh.ParseKnownHosts(
        knowhost)

    config := &ssh.ClientConfig{
        User: user,
        Auth: []ssh.AuthMethod{
            ssh.Password(pass),
        },
        HostKeyCallback: ssh.FixedHostKey(hostkey),
        Timeout: 5 * time.Second,
    }
    conn, _ := ssh.Dial("tcp", remotehost, config)

    sess, _ := conn.NewSession()

    stdin, _ := sess.StdinPipe()

    sess.Stdout = os.Stdout
    sess.Stderr = os.Stderr

    _ = sess.Shell()

    fmt.Fprintf(
        stdin, "%s\n%s\n%s\n", "pwd", "ls", "exit")

    _ = sess.Wait()

    sess.Close()
}
```

## 第 5.3 章：使用密码认证的 SFTP 文件复制

在这个 SFTP 示例中，检索远程主机公钥以验证远程主机的身份。它将用于构建客户端配置。

首先，使用 `ssh-keyscan` 实用工具以 `known_hosts` 文件格式收集远程主机公钥作为指纹。同样，如果本机之前通过 SSH 连接过该主机，它也可见于本地的 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAE...jZHN
```

接下来，远程主机公钥被复制到客户端配置中用于防止欺骗的变量中。然后，使用 `ssh.ParseKnownHosts()` 函数从 `known_hosts` 格式的条目中解析公钥。为了简化起见，密钥是硬编码的；然而，在实际操作中，可以从文件或数据库中解析。接下来，通过将用户名和密码加入 `ssh.Password()` 函数进行身份验证，构建 `ssh.ClientConfig` 结构体。然后，使用 `ssh.FixedHostKey()` 函数定义 `HostKeyCallback` 以进行授权。最后，在 `Timeout` 中设置 TCP 连接建立的最大时间，其中值为零表示无超时。

请注意，可以通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数来绕过远程主机授权，但是，这种不安全的函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以选择在 `ssh.ClientConfig` 结构体中定义可接受的密钥类型和加密算法列表以及偏好顺序。由 KeyAlgoXxxx 常量识别的密钥类型将作为 `HostKeyAlgorithms` 切片中的值进行定义。可接受的加密算法列表将在嵌入到 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在 `ssh.ClientConfig` 结构体已构建完成，它与远程主机一起使用，通过调用 `ssh.Dial()` 函数返回 `ssh.Client` 实例来启动 SSH 连接。

接下来，通过调用 `sftp.NewClient()` 函数并使用 `ssh.Client` 会话对象作为参数，创建一个新的 SFTP 客户端。这使得 `sftp.Client.MkdirAll()` 方法可以创建包含路径中所有父级的目录，`sftp.Client.Create()` 方法可以创建将要复制到的目标文件。现在目标目录和文件已创建，使用 `os.Open()` 函数打开源文件，并使用 `io.Copy()` 函数复制内容，直到源文件达到 EOF。然后，在目标文件上调用 `sftp.File.Close()` 方法，并使用 `sftp.Client.Close()` 方法关闭 SFTP 会话。最后，使用 `ssh.Client.Close()` 方法关闭 SSH 会话。
