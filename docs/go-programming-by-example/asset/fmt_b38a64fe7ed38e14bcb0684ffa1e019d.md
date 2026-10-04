
![ch12-5](Images/ch12-5.png)

# 14. Database Programming

This chapter explains how to build database application using Go.

## 14.1 Database for Go

Go can communicate with database server through database driver. Go provides generic interfaces for database drive on `http://golang.org/pkg/database/`. We must install database driver and Go database package before we start to develop database application.

In this chapter, I only focus on MySQL scenario.

## 14.2 MySQL Driver for Go

We use Go-MySQL-Driver for database driver. Further information about this driver, please visit on `https://github.com/go-sql-driver/mysql`.

To install Go-MySQL-Driver, you can try to write this command in terminal

```
$ go get github.com/go-sql-driver/mysql
```

![ch14-1](Images/ch14-1.png)

After finished, we can do testing.

## 14.3 Testing Connection

In this section, we try to connect MySQL database. Firstly, we can create a new project, called `mysqldemo`.

```
$ mkdir mysqldemo
$ cd mysqldemo
```

Create a file, `main.go`. Firstly, we import our Go packages for the demo. Write this code.

```
package main

import (
    "fmt"
    "database/sql"
    _ "github.com/go-sql-driver/mysql"
)
```

Firstly, we can start to create simple Go application to connect to mysql database. Write this code

```
func main(){
    testConnection()
}

func testConnection(){
    // change database user and password
    db, err := sql.Open("mysql",string("user:password@tcp(127.0.0.1:3306)/researchdb"))
    if err != nil {
        panic(err)
    }
    err = db.Ping()  // test connection
    if err != nil {
        panic(err.Error())
    }
    fmt.Println("connected")
    defer db.Close()
}
```

change host, user, and password based on your mysql database configuration and authentication.

Save all.

Now you can test to build and run the program.

```
$ go build
$ go run main.go
```

A sample output can be seen in Figure below.

![ch14-2](Images/ch14-2.png)

## 14.4 Querying

In this section, we try to insert data into a table. The following is our table scheme on MySQL.

![ch14-3](Images/ch14-3.png)

Here is sample code to insert data into mysql database using Go.

```
func main(){
    insertData()

}

func insertData(){

    db, err := sql.Open("mysql",string("researcher:researcher@tcp(127.0.0.1:3306)/researchdb"))
    if err != nil {
        panic(err)
    }
    err = db.Ping()  // test connection
    if err != nil {
        panic(err.Error())
    }
    fmt.Println("connected")

    // prepare development
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

After finished, we can do testing.

![ch14-4](Images/ch14-4.png)

You can verify this data into your table.

![ch14-5](Images/ch14-5.png)

# 15. Socket Programming

This chapter explains how to create socket application using Go.

## 15.1 Socket Module

We can create application based on socket stack using `net` package. You can find it for further information on `http://golang.org/pkg/net/`. I recommend you to read some books or websites about the concept of socket.

## 15.2 Hello World

To get started, we create a simple application to get a list of IP Address in local computer. We can use `net` package and call `Interfaces()` to get a list of network interfaces in our local computer. Each network interface provides information about IP address.

In this section, we try to get local IP Address. Firstly, we can create a new project, called `netdemo`.

```
$ mkdir netdemo
$ cd netdemo
```

Create a file, `main.go`. Then, write this code.

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

Save this code. Try to build and run it.

The following is a sample program output which runs on Windows:

![ch15-1](Images/ch15-1.png)

## 15.3 Client/Server Socket

Now we create a client/server socket using Go. We will use `net` package to build client/server application. For illustration, we create server and client.

### 15.3.1 Server Socket

How to create server socket? It is easy. The following is a simple algorithm how to build server socket

* create server socket
* listen incoming client on the specific port
* if client connected, listen incoming data and then disconnect from client

In this section, we build server app. Firstly, we can create a new project, called `netserver`.

```
$ mkdir netserver
$ cd netserver
```

Create a file, `main.go`. Write this code.

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

It uses port `9982`. You can change it.

### 15.3.2 Client Socket

Client socket is client application that connects to server and then sends/receives data from/to server. We should know about IP address and port from target server. We can call `Dial()` to connect to server. Use `Write()` for sending data.

In this section, we build client app. Firstly, we can create a new project, called `netclient`.

```
$ mkdir netclient
$ cd netclient
```

Create a file, `main.go`. Write this code.

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

### 15.3.3 Testing

Now we can test our client/server application. Firstly, we run server application and then execute client application.

Here is sample of program output for server application:

![ch15-2](Images/ch15-2.png)

Here is sample of program output for client application:

![ch15-3](Images/ch15-3.png)

# Source Code

You can download source code on `http://www.aguskurniawan.net/book/go_cd.zip`.

# Contact

If you have question related to this book, please contact me at `aguskur@hotmail.com`. My blog: `http://blog.aguskurniawan.net`
