
# 测试分类：黑盒测试与白盒测试

## 黑盒测试和白盒测试

对测试进行分类的一种方式是根据它们对被测包内部工作原理所需了解的程度。`黑盒`测试对包一无所知，只知道其 `API` 暴露的内容及其文档中规定的内容；包的内部是不透明的。相反，`白盒`测试拥有对包内部函数和数据结构的特权访问，可以进行普通客户端无法进行的观察和更改。例如，白盒测试可以检查包的数据类型的不变量在每次操作后是否得以保持。（`white box` 这个名称是传统叫法，但 `clear box` 会更准确。）

## 互补的方法

这两种方法是互补的。黑盒测试通常更健壮，随着软件演进需要的更新较少。它们还能帮助测试作者站在包客户的角度思考，并能揭示 `API` 设计中的缺陷。相比之下，白盒测试可以对实现中较棘手的部分提供更详细的覆盖。

## 示例

我们已经看过这两种测试的示例。`TestIsPalindrome` 仅调用导出函数 `IsPalindrome`，因此它是一个黑盒测试。`TestEcho` 调用 `echo` 函数并更新全局变量 `out`，两者均未导出，这使其成为一个白盒测试。

## 伪实现

在开发 `TestEcho` 时，我们修改了 `echo` 函数，使其在写入输出时使用包级变量 `out`，以便测试能用一个记录数据以供后续检查的替代实现来替换标准输出。使用相同的技术，我们可以将生产代码的其他部分替换为易于测试的 `fake`（伪）实现。伪实现的优势在于它们配置更简单、行为更可预测、更可靠且更易于观察。它们还能避免不良副作用，例如更新生产数据库或扣款信用卡。

### 存储示例

下面的代码展示了一个为用户提供网络存储的 Web 服务中的配额检查逻辑。当用户超过其配额的 90% 时，系统会向他们发送警告邮件。

[点击此处查看代码图像](#part0141_split_016.html#id311pro01_r)

`gopl.io/ch11/storage1`

```go
package storage

import (
    "fmt"
    "log"
    "net/smtp"
)

var usage = make(map[string]int64)
func bytesInUse(username string) int64 { return usage[username] } 

// Email sender configuration.
// NOTE: never put passwords in source code!
const sender = "notifications@example.com"
const password = "correcthorsebatterystaple"
const hostname = "smtp.example.com"

const template = `Warning: you are using %d bytes of storage,
%d%% of your quota.`

func CheckQuota(username string) {
    used := bytesInUse(username)
    const quota = 1000000000 // 1GB
    percent := 100 * used / quota
    if percent < 90 {
        return // OK
    }
    msg := fmt.Sprintf(template, used, percent)
    auth := smtp.PlainAuth("", sender, password, hostname)
    err := smtp.SendMail(hostname+":587", auth, sender,
        []string{username}, []byte(msg))
    if err != nil {
        log.Printf("smtp.SendMail(%s) failed: %s", username, err)
    }
}
```

### 为可测试性重构

我们想测试它，但不希望测试发送真实的邮件。因此我们将邮件逻辑移入一个独立函数，并将该函数存储在一个未导出的包级变量 `notifyUser` 中。

[点击此处查看代码图像](#part0141_split_017.html#id312pro01_r)

`gopl.io/ch11/storage2`

```go
var notifyUser = func(username, msg string) {
    auth := smtp.PlainAuth("", sender, password, hostname)
    err := smtp.SendMail(hostname+":587", auth, sender,
        []string{username}, []byte(msg))
    if err != nil {
        log.Printf("smtp.SendEmail(%s) failed: %s", username, err)
    }
}

func CheckQuota(username string) {
    used := bytesInUse(username)
    const quota = 1000000000 // 1GB
    percent := 100 * used / quota
    if percent < 90 {
        return // OK
    }
    msg := fmt.Sprintf(template, used, percent)
    notifyUser(username, msg)
}
```

### 使用伪通知进行测试

现在我们可以编写一个测试，用一个简单的伪通知机制替代发送真实邮件。这个测试会记录被通知的用户和消息内容。

[点击此处查看代码图像](#part0141_split_018.html#id312pro02_r)

```go
package storage

import (
    "strings"
    "testing"
)

func TestCheckQuotaNotifiesUser(t *testing.T) {
    var notifiedUser, notifiedMsg string
    notifyUser = func(user, msg string) {
        notifiedUser, notifiedMsg = user, msg
    }

    const user = "joe@example.org"
    usage[user]=  980000000 // simulate a 980MB-used condition

    CheckQuota(user)
    if notifiedUser == "" && notifiedMsg == "" {
        t.Fatalf("notifyUser not called")
    }
    if notifiedUser != user {
        t.Errorf("wrong user (%s) notified, want %s",
            notifiedUser, user)
    }
    const wantSubstring = "98% of your quota"
    if !strings.Contains(notifiedMsg, wantSubstring) {
        t.Errorf("unexpected notification message <<%s>>, "+
            "want substring %q", notifiedMsg, wantSubstring)
    }
}
```

### 使用 defer 恢复全局状态

还有一个问题：测试函数返回后，`CheckQuota` 不再按预期工作，因为它仍在使用测试的 `notifyUsers` 伪实现。（更新全局变量时总存在这种风险。）我们必须修改测试以恢复之前的值，以便后续测试不受影响，并且必须在所有执行路径上都这样做，包括测试失败和 panic 的情况。这自然提示使用 `defer`。

[点击此处查看代码图像](#part0141_split_019.html#id313pro01_r)

```go
func TestCheckQuotaNotifiesUser(t *testing.T) {
    // Save and restore original notifyUser.
    saved := notifyUser
    defer func() { notifyUser = saved }()

    // Install the test's fake notifyUser.
    var notifiedUser, notifiedMsg string
    notifyUser = func(user, msg string) {
        notifiedUser, notifiedMsg = user, msg
    }
    // ...rest of test...
}
```

这种模式可用于临时保存和恢复各种全局变量，包括命令行标志、调试选项和性能参数；安装和移除钩子，使生产代码在发生有趣的事情时调用某些测试代码；以及诱导生产代码进入罕见但重要的状态，例如超时、错误，甚至特定的并发活动交织。以这种方式使用全局变量之所以安全，仅仅是因为 `go test` 通常不并发运行多个测试。

## 外部测试包

考虑包 `net/url`（提供 URL 解析器）和 `net/http`（提供 Web 服务器和 HTTP 客户端库）。正如预期的那样，高层的 `net/http` 依赖于低层的 `net/url`。然而，`net/url` 中的一个测试是一个演示 URL 与 HTTP 客户端库交互的示例。换句话说，低层包的测试导入了高层包。

![net/url 的测试依赖于 net/http。](images/00038.jpeg)

**图 11.1.** `net/url` 的测试依赖于 `net/http`。

在 `net/url` 包中声明此测试函数会在包导入图中形成一个循环，如 [图 11.1](#part0106.html#id-figures-testcycle) 中的向上箭头所示，但正如我们在 [第 10.1 节](#part0097.html#id-pkgintro) 中所解释的，Go 规范禁止导入循环。

我们通过在 `external test package`（外部测试包）中声明测试函数来解决这个问题，即在 `net/url` 目录下的一个文件中，其包声明为 `package url_test`。额外的后缀 `_test` 向 `go test` 发出信号，指示它构建一个仅包含这些文件的额外包并运行其测试。将这个外部测试包视为具有导入路径 `net/url_test` 可能会有帮助，但它不能用这个或任何其他名称导入。
