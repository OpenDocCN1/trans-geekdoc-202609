

// And likewise with the "htmlBody" template.
htmlBody := new(bytes.Buffer)
err = tmpl.ExecuteTemplate(htmlBody, "htmlBody", data)
if err != nil {
    return err
}

// Use the mail.NewMessage() function to initialize a new mail.Message instance.
// Then we use the SetHeader() method to set the email recipient, sender and subject
// headers, the SetBody() method to set the plain-text body, and the AddAlternative()
// method to set the HTML body. It's important to note that AddAlternative() should
// always be called *after* SetBody().
msg := mail.NewMessage()
msg.SetHeader("To", recipient)
msg.SetHeader("From", m.sender)
msg.SetHeader("Subject", subject.String())
msg.SetBody("text/plain", plainBody.String())
msg.AddAlternative("text/html", htmlBody.String())

// Call the DialAndSend() method on the dialer, passing in the message to send. This
// opens a connection to the SMTP server, sends the message, then closes the
// connection. If there is a timeout, it will return a "dial tcp: i/o timeout"
// error.
err = m.dialer.DialAndSend(msg)
if err != nil {
    return err
}

return nil
}

## 使用嵌入式文件系统

在我们继续之前，让我们花一点时间更详细地讨论嵌入式文件系统，因为初次接触时有一些地方可能会让人困惑。

-   你只能在包级别的全局变量上使用 `//go:embed` 指令，而不能在函数或方法内部使用。如果你尝试在函数或方法中使用它，编译时会得到错误 `"go:embed cannot apply to var inside func"`。
-   当你使用指令 `//go:embed "<path>"` 创建嵌入式文件系统时，路径应*相对于包含该指令的源代码文件*。因此在我们的例子中，`//go:embed "templates"` 嵌入的是 `internal/mailer/templates` 目录下的内容。
-   嵌入式文件系统的根目录是包含 `//go:embed` 指令的目录。因此，在我们的例子中，要获取 `user_welcome.tmpl` 文件，我们需要在嵌入式文件系统中从 `templates/user_welcome.tmpl` 检索它。
-   路径不能包含 `.` 或 `..` 元素，也不能以 `/` 开头或结尾。这实际上限制了你只能嵌入与包含 `//go:embed` 指令的源代码位于同一目录（或其子目录）中的文件。
-   如果路径指向的是一个目录，则该目录中的所有文件都会被递归嵌入，但名称以 `.` 或 `_` 开头的文件除外。如果你想包含这些文件，应在路径中使用 `*` 通配符，例如 `//go:embed "templates/*"`。
-   你可以在一条指令中指定多个目录和文件。例如：`//go:embed "images" "styles/css" "favicon.ico"`。
-   路径分隔符应始终使用正斜杠，即使在 Windows 机器上也是如此。

## 使用我们的邮件助手

现在我们的邮件助手包已经就绪，我们需要将它连接到 `cmd/api/main.go` 文件中的其余代码。具体来说，我们需要做两件事：

-   调整我们的代码，使其接受 SMTP 服务器的配置设置作为命令行标志。
-   初始化一个新的 `Mailer` 实例，并通过 `application` 结构体将其提供给我们的处理器。

如果你在跟着操作，请确保使用上一章中你自己的 Mailtrap SMTP 服务器设置作为此处命令行标志的默认值——而不是我在下面代码中使用的确切值。

文件：cmd/api/main.go

```go
package main
```

```go
import (
    "context"
    "database/sql"
    "flag"
    "os"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer" // New import

    _ "github.com/lib/pq"
)

const version = "1.0.0"

// Update the config struct to hold the SMTP server settings.
type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
    limiter struct {
        enabled bool
        rps     float64
        burst   int
    }
    smtp struct {
        host     string
        port     int
        username string
        password string
        sender   string
    }
}
```

```go
// Update the application struct to hold a new Mailer instance.
type application struct {
    config config
    logger *jsonlog.Logger
    models data.Models
    mailer mailer.Mailer
}
```

```go
func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.BoolVar(&cfg.limiter.enabled, "limiter-enabled", true, "Enable rate limiter")
    flag.Float64Var(&cfg.limiter.rps, "limiter-rps", 2, "Rate limiter maximum requests per second")
    flag.IntVar(&cfg.limiter.burst, "limiter-burst", 4, "Rate limiter maximum burst")

    // Read the SMTP server configuration settings into the config struct, using the
    // Mailtrap settings as the default values. IMPORTANT: If you're following along,
    // make sure to replace the default values for smtp-username and smtp-password

// with your own Mailtrap credentials.
flag.StringVar(&cfg.smtp.host, "smtp-host", "smtp.mailtrap.io", "SMTP host")
flag.IntVar(&cfg.smtp.port, "smtp-port", 25, "SMTP port")
flag.StringVar(&cfg.smtp.username, "smtp-username", "0abf276416b183", "SMTP username")
flag.StringVar(&cfg.smtp.password, "smtp-password", "d8672aa2264bb5", "SMTP password")
flag.StringVar(&cfg.smtp.sender, "smtp-sender", "Greenlight <no-reply@greenlight.alexedwards.net>", "SMTP sender")

flag.Parse()

logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)

db, err := openDB(cfg)
if err != nil {
    logger.PrintFatal(err, nil)
}
defer db.Close()

logger.PrintInfo("database connection pool established", nil)

// Initialize a new Mailer instance using the settings from the command line
// flags, and add it to the application struct.
app := &application{
    config: cfg,
    logger: logger,
    models: data.NewModels(db),
    mailer: mailer.New(cfg.smtp.host, cfg.smtp.port, cfg.smtp.username, cfg.smtp.password, cfg.smtp.sender),
}

err = app.serve()
if err != nil {
    logger.PrintFatal(err, nil)
}
}
```

...
然后，我们需要做的最后一件事是更新 `registerUserHandler`，让它真正发送邮件，我们可以这样做：

```go
File: cmd/api/users.go

package main

...

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ... // Nothing above here needs to change.

    // Call the Send() method on our Mailer, passing in the user's email address,
    // name of the template file, and the User struct containing the new user's data.
    err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    err = app.writeJSON(w, http.StatusCreated, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

好了，让我们来试一试！

运行应用程序，然后在另一个终端中使用 `curl` 注册一个新用户，邮箱地址为 `bob@example.com`：

```
$ BODY='{"name": "Bob Jones", "email": "bob@example.com", "password": "pa55word"}'
$ curl -w '\nTime: %{time_total}\n' -d "$BODY" localhost:4000/v1/users
{
  "user": {
    "id": 3,
    "created_at": "2021-04-11T20:26:22+02:00",
    "name": "Bob Jones",
    "email": "bob@example.com",
    "activated": false
  }
}

Time: 2.331957
```

**注意：** 我再次使用了 `-w` 标志来显示请求完成所用的总时间，在我的例子中约为 2.3 秒。对于一个 HTTP 请求来说，这已经算是相当长的时间了；在下一章中，我们将通过在后台 goroutine 中发送欢迎邮件来加快这一过程。

