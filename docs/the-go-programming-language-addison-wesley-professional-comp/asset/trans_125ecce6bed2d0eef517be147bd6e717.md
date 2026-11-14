
# 基本 JSON 类型

基本 JSON 类型包括数字（十进制或科学计数法）、布尔值（`true` 或 `false`）和字符串，字符串是用双引号括起来的 Unicode 码点序列，使用反斜杠转义，其表示法与 Go 语言类似，不过 JSON 的 `\Uhhhh` 数字转义表示 UTF-16 码值，而非符文。

# JSON 数组和对象

这些基本类型可以通过 JSON 数组和对象进行递归组合。JSON 数组是值的有序序列，写作用方括号括起来的逗号分隔列表；JSON 数组用于编码 Go 数组和切片。JSON 对象是从字符串到值的映射，写作用花括号括起来的、逗号分隔的 `name:value` 对序列；JSON 对象用于编码 Go 映射（字符串键）和结构体。例如：

```
boolean            true
number             -273.15
string             "She said \"Hello, \""
array              ["gold", "silver", "bronze"]
object             {"year": 1980,
                    "event": "archery",
                    "medals": ["gold", "silver", "bronze"]}
```

# 示例：电影数据类型

考虑一个收集电影评论并提供推荐的应用程序。其 `Movie` 数据类型和一个典型的值列表声明如下。（`Year` 和 `Color` 字段声明后面的字符串字面量是*字段标签*；我们稍后会解释它们。）

`gopl.io/ch4/movie`

```
type Movie struct {
    Title  string
    Year   int  `json:"released"`
    Color  bool `json:"color,omitempty"`
    Actors []string
}

var movies = []Movie{
    {Title: "Casablanca", Year: 1942, Color: false,
        Actors: []string{"Humphrey Bogart", "Ingrid Bergman"}},
    {Title: "Cool Hand Luke", Year: 1967, Color: true,
        Actors: []string{"Paul Newman"}},
    {Title: "Bullitt", Year: 1968, Color: true,
        Actors: []string{"Steve McQueen", "Jacqueline Bisset"}},
    // ...
}
```

# 使用 json.Marshal 进行编组

此类数据结构非常适合 JSON，且双向转换都很容易。将像 `movies` 这样的 Go 数据结构转换为 JSON 称为*编组*。编组由 `json.Marshal` 完成：

```
data, err := json.Marshal(movies)
if err != nil {
    log.Fatalf("JSON marshaling failed: %s", err)
}
fmt.Printf("%s\n", data)
```

`Marshal` 生成一个字节切片，其中包含一个没有多余空白的很长字符串；我们折叠了行以便适应版面：

```
[{"Title":"Casablanca","released":1942,"Actors":["Humphrey Bogart","Ingr
id Bergman"]},{"Title":"Cool Hand Luke","released":1967,"color":true,"Ac
tors":["Paul Newman"]},{"Title":"Bullitt","released":1968,"color":true,"
Actors":["Steve McQueen","Jacqueline Bisset"]}]
```

# 使用 json.MarshalIndent 进行美化打印

这种紧凑表示包含所有信息，但难以阅读。为了人类阅读，一种名为 `json.MarshalIndent` 的变体会生成整齐缩进的输出。两个额外参数分别定义每行输出的前缀和每级缩进的字符串：

```
data, err := json.MarshalIndent(movies, "", "    ")
if err != nil {
    log.Fatalf("JSON marshaling failed: %s", err)
}
fmt.Printf("%s\n", data)
```

上面的代码打印：

```
[
    {
        "Title": "Casablanca",
        "released": 1942,
        "Actors": [
            "Humphrey Bogart",
            "Ingrid Bergman"
        ]
    },
    {
        "Title": "Cool Hand Luke",
        "released": 1967,
        "color": true,
        "Actors": [
            "Paul Newman"
        ]
    },
    {
        "Title": "Bullitt",
        "released": 1968,
        "color": true,
        "Actors": [
            "Steve McQueen",
            "Jacqueline Bisset"
        ]
    }
]
```

# 字段标签

编组使用 Go 结构体字段名称作为 JSON 对象的字段名称（通过*反射*，正如我们将在[第 12.6 节](#part0117.html#id-exampledecodingsexpressions)中看到的）。只有导出的字段会被编组，这就是为什么我们为所有 Go 字段名选择了大写字母开头的名称。

您可能已经注意到，输出中 `Year` 字段的名称变成了 `released`，而 `Color` 变成了 `color`。这是因为*字段标签*。字段标签是一个在编译时与结构体字段关联的元数据字符串：

```
Year  int  `json:"released"`
Color bool `json:"color,omitempty"`
```

字段标签可以是任何字面量字符串，但按照惯例，它被解释为以空格分隔的 `key:"value"` 对列表；因为它们包含双引号，字段标签通常使用原始字符串字面量书写。`json` 键控制 `encoding/json` 包的行为，其他 `encoding/...` 包遵循此惯例。`json` 字段标签的第一部分为 Go 字段指定一个替代的 JSON 名称。字段标签常用于为名为 `TotalCount` 的 Go 字段指定符合惯例的 JSON 名称，如 `total_count`。`Color` 的标签有一个额外选项 `omitempty`，它表示如果字段具有其类型的零值（此处为 `false`）或为空，则不应生成 JSON 输出。果然，黑白电影 *Casablanca* 的 JSON 输出没有 `color` 字段。

# 使用 json.Unmarshal 进行解组

编组的逆操作，即解码 JSON 并填充 Go 数据结构，称为*解组*，由 `json.Unmarshal` 完成。下面的代码将 JSON 电影数据解组到一个结构体切片中，该结构体唯一的字段是 `Title`。通过以这种方式定义合适的 Go 数据结构，我们可以选择解码 JSON 输入的哪些部分，丢弃哪些部分。当 `Unmarshal` 返回时，它已经用 `Title` 信息填充了切片；JSON 中的其他名称被忽略。

```
var titles []struct{ Title string }
if err := json.Unmarshal(data, &titles); err != nil {
    log.Fatalf("JSON unmarshaling failed: %s", err)
}
fmt.Println(titles) // "[{Casablanca} {Cool Hand Luke} {Bullitt}]"
```

# Web 服务：GitHub 问题跟踪器示例

许多 Web 服务提供 JSON 接口——发起一个 HTTP 请求，返回的就是 JSON 格式的所需信息。为了演示，让我们使用其 Web 服务接口查询 GitHub 问题跟踪器。首先我们将定义必要的类型和常量：

`gopl.io/ch4/github`

```
// Package github provides a Go API for the GitHub issue tracker.
// See https://developer.github.com/v3/search/#search-issues.
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
    Body      string    // in Markdown format
}

type User struct {
    Login   string
    HTMLURL string `json:"html_url"`
}
```

与之前一样，所有结构体字段的名称必须大写，即使它们的 JSON 名称不是大写。然而，在解组期间将 JSON 名称与 Go 结构体名称关联的匹配过程是大小写不敏感的，因此只有当 JSON 名称中有下划线而 Go 名称中没有时，才需要使用字段标签。同样，我们选择性地解码字段；GitHub 搜索响应包含的信息比我们在这里展示的要多得多。
