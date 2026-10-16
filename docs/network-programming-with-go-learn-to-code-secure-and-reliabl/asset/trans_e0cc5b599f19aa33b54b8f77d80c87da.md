
-   [日志服务器](https://example.org)的结构化日志使得在中央服务器上收集日志变得容易，因为每条日志条目关联的元数据允许服务器组织和整理跨服务的日志条目。一旦索引化，你就可以向日志服务器查询特定的日志条目，以便更快地找到及时的答案。

**使用 Zap 日志记录器**

讨论具体的中央日志解决方案超出了本书的范围。如果你想进一步学习，我建议你先研究 Logging and Metrics `301` Elasticsearch 或 Apache Solr。相反，本节专注于实现日志记录器本身。你将使用 Uber 的 Zap 日志记录器，地址为 `https://pkg.go.dev/go.uber.org/zap/`，它支持日志文件轮转。

`日志文件轮转` 是指当日志文件达到特定年龄或大小阈值时，关闭当前日志文件、重命名它，然后打开新的日志文件的过程。轮转日志文件是一个良好实践，可防止它们占满可用硬盘空间。此外，通过搜索较小的、按日期划分的日志文件比在单个大型日志文件中搜索更高效。例如，你可能希望每周轮转日志文件，并仅保留八周的轮转日志。如果你想查看上周发生的事件的日志条目，可以将搜索范围限制在单个日志文件中。此外，你还可以压缩轮转后的日志文件以进一步节省硬盘空间。

我在大型项目中使用过其他结构化日志记录器，在我经验中，Zap 的开销最小；我可以在繁忙的代码部分使用它而不会明显影响性能，不像其他重量级结构化日志记录器那样。

但你的实际情况可能不同，因此我鼓励你找到最适合你的方案。你可以将本文中描述的结构化日志原则和日志文件管理技术应用到其他结构化日志记录器中。

Zap 日志记录器包含 `zap.Core` 及其选项。`zap.Core` 包含三个组件：日志级别阈值、输出和编码器。`log-level` `threshold` 设置 Zap 记录的最低日志级别；Zap 会忽略低于该级别的日志条目，从而允许你在代码中保留调试日志，并让 Zap 有条件地忽略它们。Zap 的 `output` 是 `zapcore.WriteSyncer`，这是一个带有额外 `Sync` 方法的 `io.Writer`。Zap 可以将日志条目写入实现该接口的任何对象。`encoder` 在写入输出之前对日志条目进行编码。

**编写编码器**

尽管 Zap 提供了一些快速创建生产和开发日志记录器的 helper 函数（如 `zap.NewProduction` 或 `zap.NewDevelopment`），但你需要从头开始创建一个，先从 Listing 13-6 中的编码器配置入手。

```go
package ch13

import (
	"bytes"
	"fmt"
	"io/ioutil"
	"log"
	"os"
	"path/filepath"
	"runtime"
	"testing"
	"time"
	"go.uber.org/zap"
	"go.uber.org/zap/zapcore"
	"gopkg.in/fsnotify.v1"
	"gopkg.in/natefinch/lumberjack.v2"
)

var encoderCfg = zapcore.EncoderConfig{
	MessageKey:  "msg",
	NameKey:    "name",
	LevelKey:   "level",
	EncodeLevel: zapcore.LowercaseLevelEncoder,
	CallerKey:  "caller",
	EncodeCaller: zapcore.ShortCallerEncoder,
	// TimeKey: "time",
	// EncodeTime: zapcore.ISO8601TimeEncoder,
}
```

*Listing 13-6: 用于你的 Zap 日志记录器的编码器配置 (`zap_test.go`) 编码器配置与编码器本身是独立的，无论你是将其传递给 JSON 编码器还是控制台编码器，都可以使用相同的配置。编码器会根据你的配置决定输出格式。这里，你的编码器配置指定编码器使用键 `msg` 表示日志消息，使用键 `name` 表示记录器的名称；同时指定使用键 `level` 表示日志级别，并使用全小写字符编码级别名称。如果你希望记录调用者信息，需要将这些信息与 `caller` 键关联并以简短格式编码。为了保持以下示例输出一致，我们省略了时间键，以便它不会出现在输出中。实际使用中，你应该取消注释这两个字段。*

**创建日志记录器及其选项**

现在你已经定义了编码器配置，让我们通过在 Listing 13-7 中使用它来实例化一个 Zap 日志记录器。

```go
func Example_zapJSON() {
	zl := zap.New(
		zapcore.NewCore(
			zapcore.NewJSONEncoder(encoderCfg),
			zapcore.Lock(os.Stdout),
			zapcore.DebugLevel,
		),
		zap.AddCaller(),
		zap.Fields(
			zap.String("version", runtime.Version()),
		),
	)

	defer func() { _ = zl.Sync() }()

	Logging and Metrics `303`

	example := zl.Named("example")

	example.Debug("test debug message")

	example.Info("test info message")

	// Output:

	// {"level":"debug","name":"example","caller":"ch13/zap_test.go:49",
	// "msg":"test debug message","version":"ago1.15.5"}

	// {"level":"info","name":"example","caller":"ch13/zap_test.go:50",
	// "msg":"test info message","version":"go1.15.5"}
}
```

*Listing 13-7: 从编码器配置中实例化新的日志记录器并记录到 JSON (`zap_test.go`)*

`zap.New` 函数接受一个 `zap.Core` 和零个或多个 `zap.Options`。

在这一例子中，你传入了 `zap.AddCaller` 选项，指示日志记录器在每条记录中包含调用者信息，并为每条记录添加一个名为 `version` 的字段，插入运行时版本。

`zap.Core` 包含一个使用你的编码器配置的 JSON 编码器、一个 `zapcore.WriteSyncer` 和日志级别阈值。如果 `zapcore.WriteSyncer` 不安全用于并发，你可以使用 `zapcore.Lock` 使其安全，如本例所示。

Zap 日志记录器包含七种日志级别，按严重程度递增：`DebugLevel`、`InfoLevel`、`WarnLevel`、`ErrorLevel`、`DPanicLevel`、`PanicLevel` 和 `FatalLevel`。`InfoLevel` 是默认值。`DPanicLevel` 和 `PanicLevel` 条目会记录并触发 panic。记录 `FatalLevel` 条目会在写入日志后调用 `os.Exit(1)`。由于你的日志记录器使用 `DebugLevel`，它会记录所有条目。

我建议你在开发环境中仅使用 `DPanicLevel` 和 `PanicLevel`，在生产环境中仅在发生灾难性启动错误（如连接数据库失败）时使用 `FatalLevel`，否则会带来麻烦。如前所述，`DebugLevel`、`ErrorLevel` 以及偶尔的 `InfoLevel` 能发挥更大的作用。

在开始使用日志记录器之前，请确保你调用其 `Sync` 方法的 defer 语句，以确保所有缓冲数据都写入输出。

你也可以通过调用其 `Named` 方法为日志记录器赋予名称，并使用返回的日志记录器。默认情况下，日志记录器没有名称。命名日志记录器会在日志条目中包含 name 键，前提是你在编码器配置中定义了该键。

日志条目现在包含了围绕日志消息的元数据，以至于输出行的长度超过了本书的宽度。还需提及的是，示例中的 Go 版本依赖于你用于测试的 Go 版本。

虽然你在编码每条日志记录时使用 JSON，但你仍然可以读取日志中包含的额外元数据。你可以将这些 JSON 导入诸如 Elasticsearch 之类的工具，并运行查询，让 Elasticsearch 承担只返回与查询相关的日志行的重担。

**304** 第 13 章

**使用控制台编码器**

前面的示例在相对较少的代码中包含了大量功能。让我们假设你想记录一些更具人性化的内容。

