

许多 Web 服务都提供 JSON 接口——发起一个 HTTP 请求，返回的就是 JSON 格式的所需信息。为了演示，我们将使用 GitHub 的 Web 服务接口来查询其问题追踪器。首先我们将定义必要的类型和常量：

[点击此处查看代码图像](#ch04_images.html#id110pro02_r)

`gopl.io/ch4/github`

```
package github

import "time"

const IssuesURL = "https://api.github.com/search/issues"

type IssuesSearchResult struct {
    TotalCount int `json:"total_count"`
    Items      []*Issue
}

type Issue struct {
    Number    int
    HTMLURL   string `json:"html_url"`
    Title     string
    State     string
    User      *User
    CreatedAt time.Time `json:"created_at"`
    Body      string    // Markdown 格式
}

type User struct {
    Login   string
    HTMLURL string `json:"html_url"`
}
```

和之前一样，所有结构体字段的名称都必须首字母大写，即使它们的 JSON 名称不是。然而，在反序列化过程中将 JSON 名称与 Go 结构体名称关联的匹配过程是大小写不敏感的，因此只有当 JSON 名称中包含下划线而 Go 名称中不包含时，才需要使用字段标签。同样，我们在解码时选择了特定的字段；GitHub 的搜索响应包含的信息比我们这里展示的要多得多。

`SearchIssues` 函数发起一个 HTTP 请求并将结果解码为 JSON。由于用户提供的查询词可能包含 `?` 和 `&` 等在 URL 中具有特殊含义的字符，我们使用 `url.QueryEscape` 来确保它们被按字面意思处理。

[点击此处查看代码图像](#ch04_images.html#id111pro01_r)

`gopl.io/ch4/github`

```
package github

import (
    "encoding/json"
    "fmt"
    "net/http"
    "net/url"
    "strings"
)

// SearchIssues 查询 GitHub 问题追踪器。
func SearchIssues(terms []string) (*IssuesSearchResult, error) {
    q := url.QueryEscape(strings.Join(terms, " "))
    resp, err := http.Get(IssuesURL + "?q=" + q)
    if err != nil {
        return nil, err
    }

    // 我们必须在所有执行路径上关闭 resp.Body。
    // （第 5 章将介绍 'defer'，这会让这更简单。）
    if resp.StatusCode != http.StatusOK {
        resp.Body.Close()
        return nil, fmt.Errorf("search query failed: %s", resp.Status)
    }

    var result IssuesSearchResult
    if err := json.NewDecoder(resp.Body).Decode(&result); err != nil {
        resp.Body.Close()
        return nil, err
    }
    resp.Body.Close()
    return &result, nil
}
```

前面的示例使用 `json.Unmarshal` 将字节切片的全部内容解码为单个 JSON 实体。为了多样化，本示例使用了*流式*解码器 `json.Decoder`，它允许从同一个流中按顺序解码多个 JSON 实体，尽管我们这里不需要该特性。正如你所料，还有一个对应的流式编码器叫 `json.Encoder`。

对 `Decode` 的调用会填充变量 `result`。我们有多种方式来美观地格式化其值。最简单的方式由下面的 `issues` 命令演示，即作为一个固定列宽的文本表格，但在下一节我们将看到一种基于模板的更复杂的方法。

[点击此处查看代码图像](#ch04_images.html#id112pro01_r)

`gopl.io/ch4/issues`

```
package main

import (
    "fmt"
    "log"
    "os"

    "gopl.io/ch4/github"
)

func main() {
    result, err := github.SearchIssues(os.Args[1:])
    if err != nil {
        log.Fatal(err)
    }
    fmt.Printf("%d issues:\n", result.TotalCount)
    for _, item := range result.Items {
        fmt.Printf("#%-5d %9.9s %.55s\n",
            item.Number, item.User.Login, item.Title)
    }
}
```

命令行参数指定搜索词。下面的命令查询 Go 项目的问题追踪器，获取与 JSON 解码相关的开放 Bug 列表：

[点击此处查看代码图像](#ch04_images.html#id112pro02_r)

```
$ go build gopl.io/ch4/issues
$ ./issues repo:golang/go is:open json decoder
13 issues:
#5680    eaigner encoding/json: set key converter on en/decoder
#6050  gopherbot encoding/json: provide tokenizer
#8658  gopherbot encoding/json: use bufio
#8462  kortschak encoding/json: UnmarshalText confuses json.Unmarshal
#5901        rsc encoding/json: allow override type marshaling
#9812  klauspost encoding/json: string tag not symmetric
#7872  extempora encoding/json: Encoder internally buffers full output
#9650    cespare encoding/json: Decoding gives errPhase when unmarshalin
#6716  gopherbot encoding/json: include field name in unmarshal error me
#6901  lukescott encoding/json, encoding/xml: option to treat unknown fi
#6384    joeshaw encoding/json: encode precise floating point integers u
#6647    btracey x/tools/cmd/godoc: display type kind of each named type
#4237  gjemiller encoding/base64: URLEncoding padding is optional
```

GitHub 的 Web 服务接口位于 `https://developer.github.com/v3/`，其功能远不止我们这里有空间介绍的这些。

**练习 4.10：** 修改 `issues`，按时间范围分类报告结果，例如不到一个月、不到一年、超过一年。

**练习 4.11：** 构建一个工具，让用户能从命令行创建、读取、更新和删除 GitHub 问题，在需要大量文本输入时调用他们偏好的文本编辑器。

**练习 4.12：** 流行的网络漫画 *xkcd* 提供了 JSON 接口。例如，请求 `https://xkcd.com/571/info.0.json` 会生成第 571 期漫画的详细描述，这是许多人的最爱之一。下载每个 URL（仅一次！）并构建一个离线索引。编写一个工具 `xkcd`，利用该索引，打印出与命令行提供的搜索词匹配的每部漫画的 URL 和逐字稿。

**练习 4.13：** 开放电影数据库基于 JSON 的 Web 服务允许你在 `https://omdbapi.com/` 按名称搜索电影并下载其海报图片。编写一个工具 `poster`，下载命令行指定电影名称的海报图片。

## 4.6 文本和 HTML 模板

前面的示例仅演示了最简单的格式化，对此 `Printf` 完全足够。但有时格式化必须更加复杂，并且最好将格式与代码更彻底地分离。这可以通过 `text/template` 和 `html/template` 包来实现，它们提供了一种将变量值替换到文本或 HTML 模板中的机制。

模板是一个字符串或文件，包含一个或多个用双大括号 `{{...}}` 括起来的部分，称为*动作*。字符串的大部分内容会按原样打印，但动作会触发其他行为。每个动作包含一个模板语言表达式，这是一种简单但强大的表示法，用于打印值、选择结构体字段、调用函数和方法、表达控制流（如 `if`-`else` 语句和 `range` 循环）以及实例化其他模板。下面展示了一个简单的模板字符串：

[点击此处查看代码图像](#ch04_images.html#id113pro01_r)

`gopl.io/ch4/issuesreport`

```
const templ = `{{.TotalCount}} issues:
{{range .Items}}----------------------------------------
Number: {{.Number}}
User:   {{.User.Login}}
Title:  {{.Title | printf "%.64s"}}
Age:    {{.CreatedAt | daysAgo}} days
{{end}}`
```

