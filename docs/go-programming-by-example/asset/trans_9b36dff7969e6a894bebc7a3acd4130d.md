

![ch12-5](Images/ch12-5.png)

# 14. 数据库编程

本章介绍如何使用 Go 构建数据库应用程序。

## 14.1 Go 的数据库

Go 可以通过数据库驱动程序与数据库服务器通信。Go 在 `http://golang.org/pkg/database/` 上提供了数据库驱动的通用接口。在开始开发数据库应用程序之前，我们必须安装数据库驱动程序和 Go 数据库包。

在本章中，我只关注 MySQL 场景。

## 14.2 Go 的 MySQL 驱动

我们使用 Go-MySQL-Driver 作为数据库驱动。有关此驱动的更多信息，请访问 `https://github.com/go-sql-driver/mysql`。

要安装 Go-MySQL-Driver，您可以在终端中尝试输入以下命令

```
$ go get github.com/go-sql-driver/mysql
```

![ch14-1](Images/ch14-1.png)

完成后，我们可以进行测试。

## 14.3 测试连接

在本节中，我们尝试连接 MySQL 数据库。首先，我们可以创建一个名为 `mysqldemo` 的新项目。

```
$ mkdir mysqldemo
$ cd mysqldemo
```

创建一个文件 `main.go`。首先，我们为演示导入 Go 包。编写此代码。

```
package main

import (
    "fmt"
    "database/sql"
    _ "github.com/go-sql-driver/mysql"
)
```

首先，我们可以开始创建简单的 Go 应用程序以连接到 mysql 数据库。编写此代码

```
func main(){
    testConnection()
}

func testConnection(){
    // 更改数据库用户和密码
    db, err := sql.Open("mysql",string("user:password@tcp(127.0.0.1:3306)/researchdb"))
    if err != nil {
        panic(err)
    }
    err = db.Ping()  // 测试连接
    if err != nil {
        panic(err.Error())
    }
    fmt.Println("connected")
    defer db.Close()
}
```

根据您的 mysql 数据库配置和身份验证更改主机、用户和密码。

保存全部。

现在您可以测试构建和运行程序。

```
$ go build
$ go run main.go
```

示例输出如下图所示。

![ch14-2](Images/ch14-2.png)

## 14.4 查询

在本节中，我们尝试向表中插入数据。以下是我们在 MySQL 上的表结构。

![ch14-3](Images/ch14-3.png)

以下是使用 Go 向 mysql 数据库插入数据的示例代码。

```
func main(){
    insertData()

}

func insertData(){

    db, err := sql.Open("mysql",string("researcher:researcher@tcp(127.0.0.1:3306)/researchdb"))
    if err != nil {
        panic(err)
    }
    err = db.Ping()  // 测试连接
    if err != nil {
        panic(err.Error())
    }
    fmt.Println("connected")

    // 准备开发
    stmt, err := db.Prepare("INSERT INTO sensordevice(deviceid,temperature,humidity,light_intensity,pressure) VALUES(?,?,?,?,?)")
    if err != nil {
        panic(err)
    }
    defer stmt.Close()
    fmt.Println("inserting data...")
    for i := 0; i < 10; i++ {
        _, err = stmt.Exec(2,0.2*float64(i),0.6*float64(i),0.5*float64(i),0.3*float64(i))
        if err != nil {
            panic(err)
        }
    }
    fmt.Println("done")
    defer db.Close()

}
```

完成后，我们可以进行测试。

![ch14-4](Images/ch14-4.png)

您可以在表中验证此数据。

![ch14-5](Images/ch14-5.png)

# 15. Socket 编程

本章介绍如何使用 Go 创建 socket 应用程序。

## 15.1 Socket 模块

我们可以使用 `net` 包基于 socket 栈创建应用程序。您可以在 `http://golang.org/pkg/net/` 上找到更多信息。我建议您阅读有关 socket 概念的书籍或网站。

## 15.2 Hello World

入门时，我们创建一个简单的应用程序来获取本地计算机中的 IP 地址列表。我们可以使用 `net` 包并调用 `Interfaces()` 来获取本地计算机中网络接口的列表。每个网络接口都提供有关 IP 地址的信息。

在本节中，我们尝试获取本地 IP 地址。首先，我们可以创建一个名为 `netdemo` 的新项目。

```
$ mkdir netdemo
$ cd netdemo
```

创建一个文件 `main.go`。然后，编写此代码。

```
package main

import (
    "fmt"
    "net"
)

func main(){
    ifaces, err := net.Interfaces()
    if err!=nil {
        panic(err)
    }

    fmt.Println("getting local IP Address...")
    for _, i := range ifaces {
        addrs, err := i.Addrs()
        if err!=nil {
            panic(err)
        }
        for _, addr := range addrs {
            switch v := addr.(type) {
                case *net.IPAddr:
                    if v.String()!="0.0.0.0"{
                        fmt.Println(v.String())
                    }
            }
        }
    }
}
```

保存此代码。尝试构建并运行它。

以下是 Windows 上运行的示例程序输出：

![ch15-1](Images/ch15-1.png)

## 15.3 客户端/服务器 Socket

现在我们使用 Go 创建客户端/服务器 socket。我们将使用 `net` 包构建客户端/服务器应用程序。为说明目的，我们创建服务器和客户端。

### 15.3.1 服务器 Socket

如何创建服务器 socket？很简单。以下是构建服务器 socket 的简单算法

* 创建服务器 socket
* 在特定端口监听传入客户端
* 如果客户端连接，监听传入数据然后与客户端断开连接

在本节中，我们构建服务器应用。首先，我们可以创建一个名为 `netserver` 的新项目。

```
$ mkdir netserver
$ cd netserver
```

创建一个文件 `main.go`。编写此代码。

```
package main

import (
    "fmt"
    "net"
    "os"
)

const (
    SVR_HOST = "localhost"
    SVR_PORT = "9982"
    SVR_TYPE = "tcp"
)

func main() {
    fmt.Println("server is running")
    svr, err := net.Listen(SVR_TYPE, SVR_HOST+":"+SVR_PORT)
    if err != nil {
        fmt.Println("Error listening:", err.Error())
        os.Exit(1)
    }
    defer svr.Close()
    fmt.Println("Listening on " + SVR_HOST + ":" + SVR_PORT)
    fmt.Println("Waiting client...")

    for {

        conn, err := svr.Accept()
        if err != nil {
            fmt.Println("Error accepting: ", err.Error())
            os.Exit(1)
        }
        fmt.Println("client connected")
        go handleClient(conn)
    }
}

func handleClient(conn net.Conn) {

    buff := make([]byte, 1024)
    msgLen, err := conn.Read(buff)
    if err != nil {
        fmt.Println("Error reading:", err.Error())
    }
    fmt.Println("Received: ",string(buff[:msgLen]))
    conn.Close()
}
```

它使用端口 `9982`。您可以更改它。

### 15.3.2 客户端 Socket

客户端 socket 是连接到服务器然后向/从服务器发送/接收数据的客户端应用程序。我们应该知道目标服务器的 IP 地址和端口。我们可以调用 `Dial()` 来连接到服务器。使用 `Write()` 发送数据。

在本节中，我们构建客户端应用。首先，我们可以创建一个名为 `netclient` 的新项目。

```
$ mkdir netclient
$ cd netclient
```

创建一个文件 `main.go`。编写此代码。

```
package main

import (
    "fmt"
    "net"
)

const (
    SVR_HOST = "localhost"
    SVR_PORT = "9982"
    SVR_TYPE = "tcp"
)

func main() {
    fmt.Println("client is running")
    conn, err := net.Dial(SVR_TYPE, SVR_HOST+":"+SVR_PORT)
    if err != nil {
        panic(err)
    }
    fmt.Println("send data")
    _, err = conn.Write([]byte("message from client"))
    defer conn.Close()
}
```

### 15.3.3 测试

现在我们可以测试我们的客户端/服务器应用程序。首先，我们运行服务器应用程序然后执行客户端应用程序。

以下是服务器应用程序的程序输出示例：

![ch15-2](Images/ch15-2.png)

以下是客户端应用程序的程序输出示例：

![ch15-3](Images/ch15-3.png)

# 源代码

您可以在 `http://www.aguskurniawan.net/book/go_cd.zip` 上下载源代码。

# 联系方式

如果您对本书有任何问题，请通过 `aguskur@hotmail.com` 联系我。我的博客：`http://blog.aguskurniawan.net`

