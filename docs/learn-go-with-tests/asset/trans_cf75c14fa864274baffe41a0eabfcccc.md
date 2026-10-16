
```
return strings.TrimSuffix(buf.String(), "\n")
}
```

## 进一步迭代

我们已经实现了功能的“钢丝线程”，采取最短路径到达我们的理想路径，但很明显，在它准备好投入生产之前还有一段距离。

我们尚未处理：

- 文件格式不正确时
- 文件不是 `.md` 时
- 如果元数据字段的顺序不同怎么办？应该允许吗？我们应该能够处理它吗？

然而至关重要的是，我们拥有可工作的软件，并且我们已经定义了接口。以上只是进一步的迭代，需要编写更多测试来驱动我们的行为。为了支持以上任何一项，我们不应该改变我们的 *设计*，只需要实现细节。

保持专注于目标意味着我们做出了重要决策，并根据期望行为对其进行了验证，而不是在不会影响整体设计的问题上浪费时间。

## 总结

`fs.FS` 以及 Go 1.16 中的其他更改为我们提供了一些优雅的方式来从文件系统读取数据并简单地测试它们。

如果你想“真正”尝试代码：

- 在项目中创建 `cmd` 文件夹，添加 `main.go` 文件
- 添加以下代码

```
import (
    blogposts "github.com/quii/fstest-spike"
    "log"
    "os"
)

func main() {
    posts, err := blogposts.NewPostsFromFS(os.DirFS("posts"))
    if err != nil {
        log.Fatal(err)
    }
    log.Println(posts)
}
```

- 在 `posts` 文件夹中添加一些 Markdown 文件并运行程序！

注意生产代码之间的对称性

```
posts, err := blogposts.NewPostsFromFS(os.DirFS("posts"))
```

以及测试

```
posts, err := blogposts.NewPostsFromFS(fs)
```

这就是消费者驱动、自顶向下 TDD *感觉正确* 的时候。

我们包的用户可以查看我们的测试，快速了解它应该做什么以及如何使用它。作为维护者，我们可以确信我们的测试是有用的，因为它们来自消费者的角度。我们没有测试实现细节或其他偶然细节，因此我们可以合理地确信我们的测试在重构时会帮助我们，而不是阻碍我们。

通过依赖注入等良好的软件工程实践，我们的代码易于测试和复用。

当你创建包时，即使它们仅限于项目内部，也应优先采用自顶向下消费者驱动的方法。这将阻止

你过度想象设计并创建可能根本不需要的抽象，并有助于确保你编写的测试是有用的。

迭代方法使每一步都很小，持续的反馈帮助我们比其他更随意的方法更早地发现不明确的需求。

## 写入？

需要注意的是，这些新功能仅提供 *读取* 文件的操作。如果你的工作需要写入，你需要寻找其他方法。记住要保持 HTTP 请求。

对于我们的博客，我们希望生成两种页面：

- 1. **查看文章。** 渲染特定文章。`Post` 中的 `Body` 字段是一个包含 Markdown 的字符串，因此应将其转换为 HTML。
- 2. **索引。** 列出所有文章，并附带查看特定文章的超链接。

我们还希望网站在整体上保持一致的外观和感觉，因此每个页面都会有通常的 HTML 结构，如 `<html>` 和包含 CSS 样式表链接以及我们可能想要的其他内容的 `<head>`。

当你构建博客软件时，在如何构建和向用户浏览器发送 HTML 方面有几种选择。

我们将设计代码使其接受 `io.Writer`。这意味着我们代码的调用者具有灵活性：

- 将其写入 [os.File]，以便静态提供服务
- 直接将 HTML 写入 `http.ResponseWriter`
- 或者真的写入任何东西！只要实现了 `io.Writer`，用户就可以从 `Post` 生成一些 HTML

## 先写测试

如同往常一样，在过快深入之前思考需求很重要。我们如何将这一大块需求分解为一个小而可实现、可以专注的步骤？

在我看来，实际查看内容比索引页面优先级更高。我们可以发布此产品并分享指向我们精彩内容的直接链接。无法链接到实际内容的索引页面是没有用的。

尽管如此，按前面描述渲染文章仍然感觉很大。所有 HTML 结构、将正文 Markdown 转换为 HTML、列出标签等。

在这个阶段，我不太关心具体的标记，一个简单的第一步就是检查我们是否可以将文章标题渲染为 <h1>。这 *感觉* 像是能让我们向前迈进一点的最小第一步。

```
```go
package blogrenderer_test

import (
    "bytes"
    "github.com/quii/learn-go-with-tests/blogrenderer"
    "testing"
)

func TestRender(t *testing.T) {
    var (
        aPost = blogrenderer.Post{
            Title:        "hello world",
            Body:         "This is a post",
            Description:  "This is a description",
            Tags:         []string{"go", "tdd"},
        }
    }
```
```

```
```go
)
t.Run("it converts a single post into HTML", func(t *testing.T) {
    buf := bytes.Buffer{}
    err := blogrenderer.Render(&buf, aPost)

    if err != nil {
        t.Fatal(err)
    }

    got := buf.String()
    want := `<h1>hello world</h1>`
    if got != want {
        t.Errorf("got '%s' want '%s'", got, want)
    }
})
}
```
```

我们决定接受 `io.Writer` 也使测试变得简单，在这种情况下我们写入到 [bytes.Buffer](#)，然后可以稍后检查其内容。

### 尝试运行测试

如果你读过本书的前几章，现在应该已经熟练了。你将无法运行测试，因为我们还没有定义包或 `Render` 函数。尝试自己跟随编译器消息，直到可以运行测试并看到它以清晰的消息失败。

非常重要的一点是你要练习让测试失败，当你 6 个月后意外让测试失败时，你会感谢自己现在花了精力 *现在* 确保它以清晰的消息失败。

### 编写最少的代码使测试运行并检查失败
