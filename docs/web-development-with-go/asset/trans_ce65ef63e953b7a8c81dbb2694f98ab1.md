

## 16.6. 配置我们的应用程序

现在我们需要一种方法来创建默认配置。单个开发者如果需要，可以使用针对自己的机器自定义的内容来覆盖它，但如果他们的设置与我们相似，这将是一个很好的起点。

```
func DefaultPostgresConfig() PostgresConfig {
  return PostgresConfig(
    Host: "localhost",
    Port: 5432,
    User: "jon",
    Password: "your-password",
    Name: "lenslocked_dev",
  )
}
```

接下来是应用程序其他部分的配置 - 比如端口、环境（开发与生产），以及最终的密码盐和 HMAC 密钥。

```
type Config struct {
  Port int
  Env string
}

func (c Config) IsProd() bool {
  return c.Env == "prod"
}

func DefaultConfig() Config {
  return Config(
    Port: 3000,
    Env: "dev",
```

注意：我们将在下一节中为 HMAC 密钥和密码盐添加值。

大部分配置完成后，我们可以更新现有的代码来使用它们。我们将从 `NewServices` 函数开始，将其更新为接受一个方言字符串（dialect）。之后，我们将更新 `main` 函数来实例化默认配置实例，并使用它们来设置之前硬编码的值。

## 第16章：部署到生产环境

```
$ atom models/services.go
import (
"github.com/jinzhu/gorm"
"github.com/jinzhu/gorm/dialects/postgres"
)
func NewServices(dialect, connectionInfo string) (*Services, error) {
db, err := gorm.Open(dialect, connectionInfo)
// .. 其他地方没有变化
}
```

然后是 `main` 函数...

```
$ atom main.go
func main() {
cfg := DefaultConfig()
dBCfg := DefaultPostgresConfig()
services, err := NewServices(dbCfg.Dialect,
dBCfg.ConnectionInfo())
// .. 此处代码保持不变

// .. 我们的路由保持不变
// 删除 IsProd 变量
nisprod = false
ber, err := rand.Bytes(32)
if err != nil {
panic(err)
}
// 改用配置的 IsProd 方法
csrfMW = csrf.Protect(b, csrf.Secure(cfg.IsProd))

// 我们的端口没有通过配置提供，因此我们需要
// 更新 main 函数的最后部分。
fmt.Printf("Starting the server on %d...\n", cfg.Port)
http.ListenAndServe(fmt.Sprintf(":%d", cfg.Port),
csrfMW(userMW.Apply(r)))
}
```

## 16.6. 配置我们的应用程序

接下来，我们需要通过提供主包中所有的源文件作为参数来运行和构建应用程序，但我们也可以通过配置提供所有的变量！

```
$ go run *.go
```

这告诉我们，在构建和运行程序时，我们需要构建多个 Go 文件，而不是 `main.go`。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/16.6.1

更改 - book.usegolang.com/16.6.1-diff

## 16.6.2 使用函数选项 (functional options)

我们需要一种方法在构建服务时为它们提供配置变量。每当我们设置 `UserService` 时，都希望为它提供密码盐和 HMAC 密钥等内容，但我们目前的代码设计不允许这样做。

实现此点的一种方法是将所有内容作为参数传递给 `NewServices` 函数，但通过这样做，我们很快就会面临函数需要冗长参数列表的情况。

```
// 这个列表只会增长
func NewServices(dialect, connectionInfo string, pepper, hmacKey string,
logMode bool) (*Services, error) {
```

```
// ...
```

注意：不要编写此代码。我们显然不想使用一个需要 10 个以上参数的函数。使用起来非常困难，而且很难记住需要哪些参数。

另一种方案是为 `NewServices` 创建一个配置数据并使用它。

```
type ServicesConfig struct {
  Dialect string
  ConnectionInfo string
  Pepper string
}

func NewServices(cfg ServicesConfig) (*Services, error) { ...
```

注意：不要编写此代码。这种方法初看起来看起来整洁一点，但仍然存在相同的问题。我们需要意识到哪些变量是配对使用的。例如，如果我们没有提供方言但提供了连接信息，会发生什么？

与其使用这些方法，我们将使用所谓的**函数选项 (functional options)**。

## 6.2. 关于函数选项的更多内容

##6.6. 配置我们的应用程序

函数选项基本上是使用函数作为参数的花名。该参数通常是变变的（variadic），意味着你可以提供任意数量的参数（函数），接收它们的函数将按照接收的顺序执行操作或构建内容。

如果你想阅读更多关于该主题的内容，建议阅读以下文章：
- https://book.usegolang.com/func-opts
- https://book.usegolang.com/func-opts-jon

在使用函数选项之前，让我们在配置类型中添加最后两个配置变量——盐和 HMAC 密钥——以便我们访问它们。

```
$ atom config.go
```

```
type Config struct {
  Port int `json:"port"`
  Env string `json:"env"`
  Pepper string `json:"pepper"`
  HMACKey string `json:"hmac_key"`
}

func DefaultConfig() Config {
  return Config{
    Port: 3000,
    Env: "dev",
    Pepper: "random-string",
    HMACKey: "secret-key",
  }
}
```

## 第16章：部署到生产环境

注意：我们将在后续章节中讨论 `Config` 类型的 JSON 标签，但在这里添加它们是为了让它们可用。

函数选项允许我们提供一系列函数来帮助我们构建服务。例如，如果我们想向对象中添加 `UserService`，我们可能会编写如下代码：

```
// WithUser 接受 pepper 和 hmacKey 作为参数，
// 返回一个函数。它返回的函数接受一个 Services 指针
// 作为参数并返回错误。
func WithUser(pepper, hmacKey string) func(*Services) error {
	return func(s *Services) error {
		// 我们的 UserService 还没有匹配这个
		s.User = NewUserService(s.db, pepper, hmacKey)
		return nil
	}
}
```

注意：我们最终会编写这个函数并在代码中使用再次展示。

这与我们构建验证代码时的做法非常相似；特别是当我们创建 `idGreaterThan` 验证时。我们正在创建一个使用传入部分数据的函数。但这带给我们什么呢？回想我们编写 `runFns` 函数时；通过创建一个接受许多函数的函数，我们能够轻松地遍历所有函数并运行它们，而无需关心每个具体做了什么。我们只知道这些函数在验证数据并在出现问题时返回错误。

在使用函数选项构建 `Services` 对象时，我们可以做类似的事情。我们可以编写一个接受用于构建对象的函数列表的 `NewServices` 函数，但不需要担心它们是如何构建的。我们只需要按照提供的顺序运行每个函数并返回错误或生成的 `Services` 对象。让我们开始编写新的源代码，这将使其变得更清晰。

```
$ atom models/services.go
```

```
// ServicesConfig 实际上只是一个函数，但我发现在源代码
// 使用这样的类型更容易读。
type ServicesConfig func(*Services) error

// NewServices 将接受一个要运行的配置列表。
// 每个函数将接受当前 Services 对象的指针作为唯一
// 参数，并在内联编辑该对象，如果有错误则返回错误。
// 一旦我们运行了所有配置，我们将返回 Services 对象。
func NewServices(cfgs ...ServicesConfig) (*Services, error) {
  var s Services
  // 对于每个 ServicesConfig 函数...
  for _, cfg := range cfgs {
    // 传递我们的 Services 对象指针并运行函数
    // 捕获任何错误
    if err := cfg(&s); err != nil {
      return nil, err
    }
  }
  // 最后返回结果
  return s, nil
}
```

我们不需要我们的 `NewServices` 函数知道一个巨大的配置文件或传入的许多不同变量。它不需要像下面的逻辑那样：

```
如果有方言和连接信息
那么构建一个 gorm
如果我们有盐和 hmac 密钥
那么构建一个用户服务
```

这种逻辑可以通过执行这些这些任务的函数来显式地处理。例如，当我们更新 `NewServices` 函数时

