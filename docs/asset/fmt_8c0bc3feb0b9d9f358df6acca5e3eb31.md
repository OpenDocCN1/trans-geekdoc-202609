
```html
<!DOCTYPE html>
<html style="background-image: url('signup.jpg');background-size: cover;">
<head>
<style type="text/css">
.data_form{
margin-top: 15%;
margin-left: 29%;
}
.label{
font-size: 25px;
font-weight: 25px;
display: inline-block;
min-width: 22%;
}
.in_field{
width: 27%;
display: inline-block;
}
.goforlogin{
margin-left: 39%;
}
div{
margin-bottom: 1.5%;
}
</style>
</head>
<body>
<form action="/AddUser" method="post" class="data_form">
<div><span class="label">First Name:</span><span ><input class="in_field" type="text" name ="first_name" required/></span></div>
<div><span class="label">Last Name:</span><span><input class="in_field" type="text" name ="last_name"/></span></div>
<div><span class="label">Email Id:</span><span><input class="in_field" type="Email" name ="email" required /></span></div>
<div><span class="label">Password:</span><span><input class="in_field" type="password" name ="password" required /></span></div>
<div><span class="label">Phone Number:</span><span><input class="in_field" type="tel" name ="phone" pattern="[0-9]{10}" required /></span></div>
<input type="submit" style="width: 14%;font-size: 20px;margin: 4% 0% 0% 13%;" value="Confirm"/>
</form>
<a class="goforlogin" href="login.html">Already registered</a>
<div id="msg"></div>
<script type="text/javascript">
var vars = {};
var parts = window.location.href.replace(/[?&]+)=([^&)/gi, function(m,key,value) {vars[key] = value;});
if (vars["msg"]!==undefined){
document.getElementById("msg").innerHTML = decodeURI(vars["msg"])
}
</script>
</body>
</html>
```

在提交表单后，我们将流程引导到主页（`/home`）。再次，如下所示创建一个处理器来处理此请求：

### `server.go`

```go
package main

import (
	"log"
	"strings"
	"html/template"
	"net/http"
	"database/sql"
	"fmt"
	_ "github.com/go-sql-driver/mysql"
)

func Home(w http.ResponseWriter, r *http.Request) {
	if err := r.ParseForm(); err != nil {
		fmt.Fprintf(w, "ParseForm() err: %v", err)
	}
	user_email := r.FormValue("email")
	user_password := r.FormValue("password")
	// 创建数据库连接
	db, err := sql.Open("mysql", "root:@/go_web")
	fmt.Println(db,err)
	if err != nil {
		panic(err.Error())
	}
	type UserInfo struct {
		First_name, Last_name, Email, Password string
		Contact int64
	}
	var info UserInfo
	// 从数据库获取数据
	quer := "SELECT* FROM user_info WHERE email=?"
	errr := db.QueryRow(quer,user_email).Scan(&info.First_name, &info.Last_name, &info.Email, &info.Contact, &info.Password)
	if errr != nil {
		fmt.Println(errr.Error())
		// 不存在此 Email
		if strings.Contains(errr.Error(), "no rows") {
			http.Redirect(w, r, "http://localhost:8080/login?msg=Invalid Email", 301)
		}
	}
	db.Close() //关闭数据库连接
	// 检查用户密码
	if user_password==info.Password{
		t, err := template.ParseFiles("home.html")
		if err != nil {
			log.Print("template parsing error: ", err)
		}
		err = t.Execute(w, info)
		// 如果发生错误
		if err != nil {
			log.Print("template executing error: ", err)
		}
	} else {
		// 在密码错误的情况下
	}
}
```

```go
http.Redirect(w, r, "http://localhost:8080/login?msg=Invalid Password", 301)
}
}

func main() {
    http.HandleFunc("/", Signup)
    http.HandleFunc("/AddUser", AddUser)
    http.HandleFunc("/login", Login)
    http.HandleFunc("/home", Home)
    http.ListenAndServe(":8080", nil)
}
```

在登录处理函数中，我们可以看到用户尝试登录的 `Email Id`（邮箱 ID）和 `Password`（密码）。检查数据库中是否存在该邮箱 ID。如果邮箱存在（用户已注册），则检查密码是否正确。如果发生任何不匹配，程序将带有错误消息并重定向用户。如果邮箱 ID 和密码都正确，用户将将重定向到首页。

![](img/20-20.jpg)

**图 20.20:** 无效邮箱的输出

![](img/20-21.jpg)

**图 20.21:** 无效密码的输出

![](img/20-22.jpg)

**图 20.22:** 上述代码的输出

以下是所示的完整的服务器代码：

`server.go`

```go
package main

import (
    "log"
    "strings"
    "html/template"
    "net/http"
    "database/sql"
    "fmt"
    _ "github.com/go-sql-driver/mysql"
)

func Signup(w http.ResponseWriter, r *http.Request){
    t, err := template.ParseFiles("signup.html")
    if err != nil {
        log.Print("template parsing error: ", err)
    }
    err = t.Execute(w, nil)
    if err != nil {
        log.Print("template executing error: ", err)
    }
}

func AddUser(w http.ResponseWriter, r *http.Request) {
    if err := r.ParseForm(); err != nil {
        fmt.Fprintf(w, "ParseForm() err: %v", err)
    }
    fName := r.FormValue("first_name")
    lName := r.FormValue("last_name")
    emailId := r.FormValue("email")
    phoneNo := r.FormValue("phone")
    password := r.FormValue("password")
    // Create Database connection
    db, err := sql.Open("mysql", "root:@/go_web")
    if err != nil {
        panic(err.Error())
    }
    // insert data
    stmtIns, err := db.Query("INSERT INTO user_info VALUES(?,?,?,?,?)", fName, lName, emailId, phoneNo, password)
    if err != nil {
        panic(err.Error()) // proper error handling instead of panic in your app
    }
    defer stmtIns.Close()
    t, err := template.ParseFiles("registrationConfirm.html")
    if err != nil {
        log.Print("template parsing error: ", err)
    }
    err = t.Execute(w, nil)
}

func Login(w http.ResponseWriter, r *http.Request){
    t, err := template.ParseFiles("login.html")
    if err != nil {// if there is an error
        log.Print("template parsing error: ", err)
    }
    err = t.Execute(w, nil)
    if err != nil {
        log.Print("template executing error: ", err)
    }
}

func Home(w http.ResponseWriter, r *http.Request){
    if err := r.ParseForm(); err != nil {
        fmt.Fprintf(w, "ParseForm() err: %v", err)
    }
    user_email := r.FormValue("email")
    user_password := r.FormValue("password")
    // Create Database connection
    db, err := sql.Open("mysql", "root:@/go_web")
    fmt.Println(db,err)
    if err != nil {
        panic(err.Error())
    }

    type UserInfruct {
        First_name, Last_name, Email, Password string
        Contact int64
    }
    var info UserInfo
    // Getting data from Database
    quer := "SELECT* FROM user_info WHERE email=?"
    errr := db.QueryRow(quer,user_email).Scan(&info.First_name, &info.Last_name, &info.Email, &info.Contact, &info.Password)
    if errr != nil {
        fmt.Println(errr.Error())
        // No such Email exists
        if strings.Contains(errr.Error(), "no rows") {
            fmt.Println("no rows here")
            http.Redirect(w, r, "http://127.0.0.1:8080/ login?msg=Invalid Email", 301)
        }
    }
    db.Close() //Close database connection
    // Check user password
    if user_password==info.Password{
        fmt.Println("come",info.First_name)
        t, err := template.ParseFiles("home.html")
        if err != nil {
            log.Print("template parsing error: ", err)
        }
        err = t.Execute(w, info)
        if err != nil {// if there is an error
            log.Print("template executing error: ", err)
        }
    } else {
        //in case of incorrect password
        http.Redirect(w, r, "http://127.0.0.1:8080/login?msg=Invalid Password", 301)
    }
}
}

func main() {
    http.HandleFunc("/", Signup)
    http.HandleFunc("/AddUser", AddUser)
    http.HandleFunc("/login", Login)
    http.HandleFunc("/home", Home)
    http.ListenAndServe(":8080", nil)
}
```

通过这种方式，我们使用 Go 语言创建了一个简单的 Web 应用程序。实现一次有助于更好地理解。

## 结论

在本章中，我们理解了...（注：提供的文本在结论标题处戛然而止）。

# 发送操作 203

# 无缓冲通道 204

# 循环导入 90-92

# 闭包函数 77, 78

# 云端 IDE 11, 12

# 代码复用性 4

# 编译器 12

# 组合 158-160

# 并发

## 关于 192

## 与并行的区别 192

# 常数

## 关于 41

## 布尔常量 43

## iota 标识符 43

## 数值常量 42

## 字符串常量 42

# 容器标签

- `<a>` 标签 263
- `<b>` 263
- `<body>` 262
- `<div>` 262
- `<head>` 261
- `<html>` 261
- `<i>` 263
- `<ol>` 264
- `<p>` 264
- `<span>` 262
- `<sub>` 264
- `<sup>` 264
- `<table>` 263
- `<textarea>` 263
- `<title>` 262
- `<u>` 263
- `<ul>` 264

# continue 语句 63

## 控制结构

## 定义 60

# 自定义包

## 创建 87-89

# D

## 数据库 277
## 数据库管理系统 277
## 数据定义语言 (DDL) 277
## 数据操纵语言 (DML) 278

# 数据竞态

## 检查 223, 224
## 在 Go 语言中 222, 223

### 数据类型

## 关于 33
## 非基本数据类型 37
## 原始数据类型 34

## 死锁

## 关于 206-208
## 多个 Goroutine，使用 208, 209

# defer 关键字 79

## defer 语句

## 关于 237-239
## 工作原理 237

# 解引用运算符 140

# 点导入 86

# E

## else 语句 60

### 空元素

## 关于 265

- `<base>` 265
