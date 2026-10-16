
assertStatus(t, res.Code, http.StatusCreated)

if res.Body.String() != expectedInsertedID {
    t.Errorf("expected body of %q but got %q", res.Body.String())
}

if len(service.UsersRegistered) != 1 {
    t.Fatalf("expected 1 user added but got %d", len(service.UsersRegistered))
}

if !reflect.DeepEqual(service.UsersRegistered[0], user) {
    t.Errorf("the user registered %+v was not what was expected")
}
})

t.Run("returns 400 bad request if body is not valid user JSON"
    server := NewUserServer(nil)

    req := httptest.NewRequest(http.MethodGet, "/", strings.
    res := httptest.NewRecorder()

    server.RegisterUser(res, req)

    assertStatus(t, res.Code, http.StatusBadRequest)
})

t.Run("returns a 500 internal server error if the service fa:"
    user := User{Name: "CJ"}

    service := &MockUserService{
        RegisterFunc: func(user User) (string, error) {
            return "", errors.New("couldn't add new user")
        },
    }
    server := NewUserServer(service)

    req := httptest.NewRequest(http.MethodGet, "/", userToJS(
    res := httptest.NewRecorder()

    server.RegisterUser(res, req)

```go
assertStatus(t, res.Code, http.StatusInternalServerError)
})
}
```

现在我们的处理器不依赖于特定的存储实现，因此我们可以轻松编写一个 `MockUserService` 来帮助我们编写简单、快速的单元测试，以验证其特定的职责。

## 数据库代码怎么办？你在作弊！

这都是经过深思熟虑的。我们不希望 HTTP 处理器关心业务逻辑、数据库、连接等。

通过这样做，我们将处理器从混乱的细节中解放出来，*同时*也使测试持久层和业务逻辑变得更容易，因为它也不再与无关的 HTTP 细节耦合。

我们现在需要做的就是使用我们想要的任何数据库来实现我们的 `UserService`

```go
type MongoUserService struct {
}

func NewMongoUserService() *MongoUserService {
    //todo: pass in DB URL as argument to this function
    //todo: connect to db, create a connection pool
    return &MongoUserService{}
}

func (m MongoUserService) Register(user User) (insertedID string,
    // use m.mongoConnection to perform queries
    panic("implement me")
}
```

我们可以单独测试它，一旦在 `main` 中满意，我们就可以将这两个单元组合起来，形成我们的工作应用程序。

```go
func main() {
    mongoService := NewMongoUserService()
    server := NewUserServer(mongoService)
    http.ListenAndServe(":8000", http.HandlerFunc(server.Registe
}
```

## 付出少量努力即可获得更健壮且可扩展的设计

这些原则不仅在短期内让我们的生活更轻松，还使系统在未来更容易扩展。

在该系统的后续迭代中，我们希望向用户发送注册确认邮件，这并不令人意外。

使用旧设计，我们必须更改处理器和周围的测试。这通常就是代码部分变得难以维护的原因，越来越多的功能不断渗入，因为它就是这样设计的；让“HTTP 处理器”处理……一切！

通过使用接口分离关注点，我们根本不需要编辑处理器，因为它不关心注册周围的业务逻辑。

## 总结

测试 Go 的 HTTP 处理器并不困难，但设计良好的软件可能很困难！

人们常犯的错误是认为 HTTP 处理器很特殊，在编写它们时抛弃了良好的软件工程实践，这随后使测试变得困难。

再次重申；Go 的 http 处理器只是函数。如果你像编写其他函数一样编写它们，具有明确的职责，

并且有良好的关注点分离，你将不会遇到测试它们的任何问题，你的代码库也会因此更健康。

## TDD 反模式

不时需要回顾你的 TDD 技术，并提醒自己避免的行为。

TDD 过程在概念上很简单，但你在实践中会发现它挑战了你的设计技能。**不要因此认为 TDD 很困难，困难的是设计！**

本章列出了一些 TDD 和测试反模式，以及如何纠正它们。

## 完全不做 TDD

当然，没有 TDD 也能编写出优秀的软件，但是，我见过的许多代码设计和测试质量问题，如果采用了纪律严明的 TDD 方法，就很难出现。

TDD 的优势之一是它为你提供了一个正式的过程来分解问题，了解你想要实现的目标（红），完成它（绿），然后好好思考如何使其正确（蓝/重构）。

没有它，这个过程通常是临时性和松散的，这*可能*使工程比*本可以*更困难。

## 对重构步骤的限制理解错误

我参加过许多研讨会、集体编程或结对编程会议，在那里有人让测试通过并进入了重构

阶段。经过一些思考，他们认为将一些代码抽象到新的结构体中会很好；一个初出茅庐的书呆子大喊：

> 你不允许这样做！你应该先为此编写测试，我们正在做 TDD！

这似乎是一个常见的误解。**当测试为绿色时，你可以随意修改代码**，唯一不允许做的是**添加或更改行为**。

这些测试的目的是给你*重构的自由*，找到合适的抽象并使代码更容易更改和理解。

## 有不会失败的测试（或，常青测试）

这令人惊讶地经常出现。你开始调试或更改一些测试并意识到：没有场景会导致此测试失败。或者至少，它不会以测试*本应*保护的方式失败。

如果你遵循**第一步**，在 TDD 中这几乎是不可能的，

- 编写测试，观察它失败

这几乎总是在开发人员在代码编写后编写测试时发生，和/或追求测试覆盖率而不是创建有用的测试套件。

## 无用的断言

你是否曾在某个系统上工作过，破坏了一个测试，然后看到这个？

false was not equal to true

我知道 false 不等于 true。这不是一个有帮助的信息；它没有告诉我破坏了什么。这是没有遵循 TDD 过程且没有阅读失败错误信息的症状。

回到原点，

编写测试，观察它失败（不要为错误信息感到羞愧）

## 对无关细节进行断言

一个例子是在复杂对象上进行断言，而实际上在测试中你关心的只是其中一个字段的值。

```
// not this, now your test is tightly coupled to the whole objec
if !cmp.Equal(complexObject, want) {
    t.Error("got %v, want %v", complexObject, want)
}
```

```
// be specific, and loosen the coupling
got := complexObject.fieldYouCareAboutForThisTest
if got != want {
    t.Error("got %q, want %q", got, want)
}
```

额外的断言不仅通过在文档中创建“噪音”使你的测试更难以阅读，而且还不必要地将测试与它不关心的数据耦合。这意味着如果你碰巧更改了对象的字段，或它们的行为方式，你可能会遇到意外的编译问题或测试失败。

这是不够严格遵循红阶段的一个例子。

- 让现有设计影响你编写测试的方式，而不是思考期望的行为
- 没有充分考虑失败测试的错误信息

## 单元测试中单个场景包含大量断言

许多断言会使测试难以阅读，并且在失败时难以调试。

它们通常会逐渐渗入，尤其是在测试设置复杂时，因为你不愿意复制相同的糟糕设置来断言其他内容。相反，你应该修复设计中的问题，这些问题使断言新事物变得困难。

一个有用的经验法则是每个测试只做一个断言。在 Go 中，利用子测试在需要时清晰地区分断言。这也是分离对行为与实现细节的断言的一个方便技巧。

对于设置或执行时间可能受约束的其他测试（例如驱动 Web 浏览器的验收测试），你需要在稍难调试的测试的利弊与测试执行时间之间权衡。

## 不倾听你的测试

Dave Farley 在他的视频“当 TDD 出错时”中指出，

> TDD 为你的设计提供了最快的反馈

从我自己的经验来看，许多开发人员试图实践 TDD，但经常忽略从
