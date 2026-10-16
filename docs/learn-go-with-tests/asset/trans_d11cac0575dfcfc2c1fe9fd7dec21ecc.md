
TDD 流程。所以他们仍然困于脆弱、令人厌烦的系统，且测试套件质量低下。

简单来说，如果测试你的代码很困难，那么*使用*你的代码也很困难。将你的测试视为你代码的第一个用户，然后你就能看出你的代码是否令人愉快地工作。

我在书中大量强调了这一点，我再说一次**倾听你的测试**。

## 过度的设置、过多的测试替身等。

你是否看过一个测试，在测试中发生任何有趣的事情之前，先有 20、50、100、200 行的设置代码？然后你是否必须更改代码、重新审视这堆混乱，并希望自己从事不同的职业？

这里的信号是什么？*倾听*，复杂的测试 == 复杂的代码。为什么你的代码很复杂？它必须如此吗？

- 当你的测试中有很多测试替身时，这意味着你正在测试的代码有很多依赖项 - 这意味着你的设计需要改进。
- 如果你的测试依赖于设置与模拟对象的各种交互，这意味着你的代码与它的依赖项进行了大量交互。问问自己这些交互是否可以更简单。

## 泄漏的接口

如果你声明了一个包含许多方法的`interface`，那就指向了一个泄漏的抽象。思考一下如何用更精简的方法集，最好是一个方法，来定义这种协作。

## 思考你使用的测试替身的类型

- Mocks 有时很有帮助，但它们功能极其强大，因此很容易被误用。尝试给自己施加使用 stubs 的限制。
- 使用 spies 验证实现细节有时有帮助，但尽量避免。记住你的实现细节通常并不重要，而且如果可能的话，你不希望你的测试与它们耦合。让你的测试耦合到**有用的行为而非偶然的细节**。
- [阅读我在命名测试替身方面的文章](), 如果测试替身的分类法有点不清楚

## 合并依赖项

这里有一些用于处理网站新用户注册的 `http.HandlerFunc` 代码。

```
type User struct {
    // Some user fields
}

type UserStore interface {
    CheckEmailExists(email string) (bool, error)
    StoreUser(newUser User) error
}

type Emailer interface {
    SendEmail(to User, body string, subject string) error
}

func NewRegistrationHandler(userStore UserStore, emailer Emailer) http.HandlerFunc {
    return func(writer http.ResponseWriter, request *http.Request) {
        // extract out the user from the request body (handle err)
        // check user exists (handle duplicates, errors)
        // store user (handle errors)
        // compose and send confirmation email (handle error)
        // if we got this far, return 2xx response
    }
}
```

初看之下，说这个设计不算太差是合理的。它只有 2 个依赖项！

通过考虑处理程序的职责来重新评估设计：

- 将请求体解析为 `User` ✔
- 使用 `UserStore` 检查用户是否存在 ?
- 使用 `UserStore` 存储用户 ?
- 撰写电子邮件 ?
- 使用 `Emailer` 发送电子邮件 ?
- 根据成功、错误等返回适当的 http 响应 ✔

为了测试这段代码，你将不得不编写许多测试，其中测试替身设置、spies 等各不相同

- 如果需求扩展了呢？电子邮件的翻译？还要发送 SMS 确认？对你来说，让你必须更改 HTTP 处理程序来适应这种变化合理吗？
- 重要的规则“我们应该发送电子邮件”存在于 HTTP 处理程序中感觉对吗？
  - 为什么你必须经历创建 HTTP 请求和读取响应的仪式来验证该规则？

**倾听你的测试。** 以 TDD 方式为这段代码编写测试应该会让你很快感到不舒服（或者至少，让你内心的懒惰开发者感到恼火）。如果感觉痛苦，就停下来思考。

如果设计是这样的呢？

```
type UserService interface {
    Register(newUser User) error
}
```

```
func NewRegistrationHandler(userService UserService) http.HandlerFunc {
    return func(writer http.ResponseWriter, request *http.Request) {
        // parse user
        // register user
        // check error, send response
    }
}
```

- 处理程序易于测试 ✔
- 关于注册的规则的更改与 HTTP 隔离，因此也更简单地测试 ✔

## 违反封装

封装非常重要。我们不把包中的所有内容都导出（或公开）是有原因的。我们希望拥有连贯的 API 且表面积小，以避免紧密耦合。

有时人们会想让函数或方法公开以便测试某些东西。通过这样做，你会使设计变差，并向维护者和代码使用者发送令人困惑的信息。

其结果可能是开发者尝试调试测试，最终意识到被测试的函数*只在测试中被调用*。这显然是**一个糟糕的结果，浪费时间**。

在 Go 中，考虑你编写测试的默认立场是*从你包的消费者角度*。你可以通过让测试位于测试包中，例如 `package gocoin_test`，将其作为编译时约束。这样做的话，你只能访问包的已导出成员，因此不可能将自己耦合到实现细节。

## 复杂的表格测试

表格测试是在测试设置相同且你只想改变

输入时，练习多种不同场景的绝佳方式。

*但是*当你试图把其他类型的测试硬塞进一个辉煌的表格的名义下时，它们可能变得难以阅读和理解。

```
cases := []struct {
    X               int
    Y               int
    Z               int
    err             error
    IsFullMoon      bool
    IsLeapYear      bool
    AtWarWithEurasia bool
}{}
```

**不要害怕跳出你的表格并编写新的测试**而不是向表格 `struct` 添加新的字段和布尔值。

编写软件时需要记住的一件事是，

[简单并不容易]()

"仅仅"向表格添加一个字段可能很容易，但它可能使事情远离简单。

## 总结

大多数单元测试问题通常可以追溯到：

- 开发者未遵循 TDD 流程
- 设计不佳

所以，学习良好的软件设计！

好消息是 TDD 可以帮助你*提高你的设计技能*，因为正如开头所述：

**TDD 的主要目的是为你的设计提供反馈。** 第无数次，倾听你的测试，它们正在把你的设计反映回给你。

通过倾听它们给你的反馈，诚实地对待你的测试质量，你会因此成为更好的开发者。
