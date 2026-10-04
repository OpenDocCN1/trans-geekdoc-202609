

```go
func failC() error {
	return errors.New("C failed")
}
```

```go
func main() {
	zerolog.ErrorStackMarshaller = pkgerrors.MarshalStack

	err := failA()
	log.Error().Stack().Err(err).Msg("")
}
```

```json
{"level":"error","stack":[{"func":"failC","line":"9","source":"main.go"},{"func":"failA","line":"15","source":"main.go"},{"func":"main","line":"25","source":"main.go"},{"func":"main","line":"204","source":"proc.go"},{"func":"getext","line":"1374","source":"asm_amd64.s"}],"error":"C failed","time":"2021-02-18T19:42:21.000Z"}
```

# 16.3 ZEROLOG 设置

Zerolog 拥有一大量的配置选项。这些选项可以修改消息输出格式，其中输出设置用于定义子日志记录（subloggers）等。在本节中，我们将探索开发者在项目中定义记录内容和记录方式时可能会发现实用的设置。

### 16.3.1 将日志写入文件

标准输出日志并不总是最佳解决方案，尤其是在无监督的场景下。将日志写入文件可以获得非易失性的版本，此外便于并发，并可用于为分析系统。可以使用接收 `io.Writer` 的 `New` 函数创建日志器。示例 16.9 创建了一个将所有消息转到临时文件的日志器。

示例 16.9：堆栈跟踪日志。

```go
package main

import (
	"io/ioutil"
	"os"
	"fmt"
	"github.com/rs/zerolog/log"
	"github.com/rs/zerolog"
)

func main() {
	tempFile, err := ioutil.TempFile(os.TempDir(),"deleteme")
	if err != nil {
		// 我们在获取日志器之前可以记录错误吗？:)
		log.Error().Err(err).
		Msg("there was an error creating a temporary file for our log")
	}
	defer tempFile.Close()
	fileLogger := zerolog.New(tempFile).With(temp.Logger)
	fileLogger.Info().Msg("This is an entry from my log")
	fmt.Printf("The log file is allocated at %s\n", tempFile.Name())
}
```

日志文件分配在 /var/6h/xfffh4j07715cbsmmbk48z0000gp/T/deleteme930052425

### 16.3.2 输出自定义

我们已经提到过 Zerolog 设计用于使用 JSON。然而，JSON 可能不是最用户友好的格式，特别是我们将日志打印到控制台时。控制台会移除 JSON 语法中的冒号、括号和引号，允许我们轻松地定义输出格式。示例 16.10 自定义了 `ConsoleWriter` 来为级别、消息、字段、名称和返回值定义新格式。每个项目都可以使用一个接收接口并返回字符串的函数进行重新定义。参见示例，字段被方括号包围，或者日志级别是如何始终固定为六个字符字符串的。

示例 16.10：使用 ConsoleWriter 的自定义输出

```go
package main

import (
	"os"
	"strings"
	"time"
	"fmt"
	"github.com/rs/zerolog"
)

func main() {
	output := zerolog.ConsoleWriter(Out: os.Stdout, Time: time.RFC3339)
	output.FormatLevel = func(i interface{}) string {
		return strings.ToUpper(fmt.Sprintf("%%s", i))
	}
	output.FormatMessage = func(i interface{}) string {
		return fmt.Sprintf(">>>%s<<", i)
	}
	output.FormatFieldName = func(i interface{}) string {
		return fmt.Sprintf("%%%s", i)
	}
	output.FormatFieldValue = func(i interface{}) string {
		return strings.ToUpper(fmt.Sprintf("%%%s", i))
	}

	log := zerolog.New(output).With(time.Timestamp()).Logger()
	log.Str("foo", "bar").Msg("Save the world!")
}
```

### 16.3.3 多日志器

根据日志级别、消息输出（文件、标准输出）分离日志是常见做法。`MultiLevelWriter` 聚合日志器，使得单个日志消息可以写入不同的格式。示例 16.11 定义了一个同时将消息发送到文件、标准输出和 `ConsoleWriter` 的多日志器。输出显示了日志器向日志记录的内容。可以进行设置专用日志等额外自定义。

示例 16.11：使用 MultiLevelWriter 同时记录多个输出。

```go
package main

import (
	"io/ioutil"
	"os"
	"fmt"
	"github.com/rs/zerolog"
	"github.com/rs/zerolog/log"
)

func main() {
	tempFile, err := ioutil.TempFile(os.TempDir(),"deleteme")
	if err != nil {
		log.Error().Err(err).
		Msg("there was an error creating a temporary file for our log")
	}
	defer tempFile.Close()
	fmt.Printf("The log file is allocated at %s\n", tempFile.Name())

	fileLogger := zerolog.New(tempFile).With().Logger()
	consoleWriter := zerolog.ConsoleWriter(Out: os.Stdout)

	multi := zerolog.MultiLevelWriter(consoleWriter, os.Stdout, fileLogger)
	logger := zerolog.New(multi).With(time.Timestamp()).Logger()

	logger.Info().Msg("Save the world!")
}
```

日志分配在 /var/folders/6h/xffff45j07715cb5mbk48000gp/T/deleteme5817032842:32 Save the world!
{"level":"info","time":"2021-02-08T12:32:01Z","message":"Save the world!"}

### 16.3.4 子日志

通过 Zerolog，日志器是可扩展的。这使得增强现有配置并扩展上下文成为可能。在示例 16.12 中，我们从 `mainLogger` 创建了一个带有额外上下文的新日志器。检查子日志器的输出，它保持了与主日志相同的配置，没有额外信息。

示例 16.12：使用子日志的可扩展记录。

```go
package main

import (
	"os"
	"github.com/rs/zerolog"
)

func main() {
	mainLogger := zerolog.New(os.Stdout).With().Logger()
	mainLogger.Info().Msg("This is the main logger")

	sublogger := mainLogger.With("component", "componentA").Logger()
	sublogger.Info().Msg("This is the sub-logger")
}
```

```json
{"level":"info","message":"This is the main logger"}
{"level":"info","component":"componentA","message":"This is the sub-logger"}
```

# 16.4 ZEROLOG 高级设置

本节通过解释特定场景的额外解决方案概述 Zerolog 功能概述。

### 16.4.1 Hooks

Hooks 在每次调用日志器时执行。`Hook` 接口定义了 `Run` 方法，允许访问日志的参数。示例 16.13 使用 `Hook` 将组件名称添加到调试消息的上下文中。此外，第二个 hook 将一个随机数添加到上下文中。两个 hook 都被添加到同一个日志器中，修改了日志器的最终行为。观察发现只有调试消息包含上下文中的组件字符串。

示例 16.13：使用子日志记录。

```go
package main

import (
	"github.com/rs/zerolog"
	"github.com/rs/zerolog/log"
	"math/rand"
)

type ComponentHook struct {
	component string
}

func (h ComponentHook) Run(e *zerolog.Event, level zerolog.Level, msg string) {
	if level == zerolog.DebugLevel {
		e.Str("component", h.component)
	}
}

type RandomHook struct{}

func (r RandomHook) Run(e *zerolog.Event, level zerolog.Level, msg string) {
	e.Int("random", rand.Int())
}

func main() {
	logger := log.Hook(ComponentHook("moduleA"))
	logger = logger.Hook(RandomHook())
	logger.Info().Msg("Info message")
	logger.Debug().Msg("Debug message")
}
```

| {"level":"info","time":"2021-02-08T16:37:01.00Z","random":"5577006791947794140","message":"Info message"} |
| {"level":"debug","time":"2021-02-08"} |
| 0813:16:36:37+01:00,"component":"moduleA","random":"8674652238082153551","message":"Debug message"} |

### 16.4.2 采样

在循环内部执行日志消息时可能会特别困扰。对于大量的迭代，情况会糟糕。Zerolog 提供了采样日志器，可以进行配置以适应生成的日志消息数量。`Sample` 函数根据 `Sample` 类型返回日志器。采样器仅包含一个 `sample` 方法，当消息被采样时返回 `true`。

`basicSampler` 每隔 N 次调用采样一次消息。这在循环内部特别有用，例如示例 16.14 所示，在 1000 次迭代的循环中每隔 200 次打印一次消息。

示例 16.14：使用基础采样器的日志器。

