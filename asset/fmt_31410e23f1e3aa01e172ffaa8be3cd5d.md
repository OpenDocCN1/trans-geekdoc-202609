
```go
package main

import (
    "encoding/xml"
    "io/ioutil"
)

type Campus struct {
    XMLName xml.Name `xml:"campus"`
    Name string `xml:"name,attr"`
    Comment string `xml:",comment"`
    Building Building
}
type Building struct {
    XMLName xml.Name `xml:"building"`
    Name string `xml:"name,attr"`
    Comment string `xml:",comment"`
    Device Device
}
type Device struct {
    XMLName xml.Name `xml:"device"`
    Name string `xml:"name,attr"`
    Type string `xml:"type,attr"`
}
```

```go
XMLName xml.Name `xml:"device"`
    Name string `xml:"name,attr"`
    Type string `xml:"type,attr"`
}

func main() {
    camp := &Campus {Name: "campus1",
                     Comment: "building-comment",
                     Building: Building{Name: "bldg1",
                          Comment: "device-comment",
                          Device: Device{Name: "rtr1",
                              Type: "router"}}}

    indt, _ := xml.MarshalIndent(camp, "", "  ")

    _ = ioutil.WriteFile("file.xml", indt, 0644)
}
```

输出显示了以 XML 格式呈现每个值的文件。虽然为了演示过程，XML 被写入到文件中，但将 XML 写入 REST API 也很常见。

```xml
<campus name="campus1">
    <!-- building-comment -->
    <building name="bldg1">
        <!-- device-comment -->
        <device type="router" name="rtr1"></device>
    </building>
</campus>
```

# 第 3 章：文本模板

文本模板常用于网络运维中，生成大量遵循标准模板的配置。它们能够实现一致的准确性，并允许版本控制。

模板包通过解析文本并评估动态元素来处理模板。本章将探讨常见的模板操作，然后介绍一个基本模板，再深入讲解模板继承。

本章将涵盖以下主题：

- 定义模板元素
- 创建基本模板
- 实现模板继承

## 第 3.1 节：模板元素

模板的基本构建块是其元素。元素由双花括号包围的参数和操作组成。参数包括值和操作，而操作由语句组成，例如 if-else、range 或 with。

| 元素 | 描述 |
| :--- | :--- |
| `{{.}}` | 根元素 |
| `{{.Var}}` | 变量 |
| `{{- .Var -}}` | 移除两侧的空白 |
| `{{ $version := "0.1" }} {{ $version }}` | 内部变量赋值 |
| `{{/* comment here */}}` | 注释 |
| `Name: {{if .Name }} {{ .Name }} {{ else }} anonymous {{end}} .` | If-else 条件判断 |
| `{{with .Var}} {{end}}` | With 语句 |
| `{{range .Array}} {{end}}` | 遍历切片、映射或通道 |
| `{{ lt 3 4 }}` | 小于（其他布尔运算符：eq, ne, lt, le, gt, ge） |

## 第 3.2 节：基本模板

基本模板由数据源和单个模板组成。模板继承（将在下一节中涵盖）用于组装嵌套模板。

在这个示例中，使用了三个文件：一个 CSV 数据文件、一个模板文件和一个 Go 文件。下面的 CSV 数据文件表示一个 VLAN 列表，每行一个，第一列是数字，第二列是名称。模板文件将表示配置每个 VLAN 的格式。它将遍历数据文件的每一行，并按照各自的布局格式化来自这两列的数据。Go 文件将用于将 CSV 文件和模板文件合并，然后生成输出。

CSV 数据文件：

```csv
1,ONE
2,TWO
3,THREE
```

既然上面已经定义了 CSV 数据文件，模板文件用于定位数据。下面定义的模板文件使用 range 元素封装了中间两行。它遍历代表 CSV 数据文件中行的根元素切片结构体。在循环内，普通文本后面跟着一个用于应用结构体成员的变量。请注意下面模板文件中用于修剪名称后空格的破折号元素。

```go
{{range .}}
  vlan {{.Id}}
  name {{.Name -}}
{{end}}
```

遍历下面的 Go 文件，CSV 数据文件使用 `os.Open()` 函数以只读模式打开，返回 `os.File` 的实例。接下来，`os.File` 实例作为参数传递给 `csv.NewReader()` 函数，以接收一个带缓冲的 `csv.Reader` 对象。然后，创建 `V lans` 结构体的切片实例，用于存储 CSV 文件每行中的值。使用 `csv.Reader.Read()` 方法逐行解码文件到结构体字段中。然后，将它们存储在一个切片中，直到返回预期的 `io.EOF` 错误，表示已达到文件末尾。最后，使用 `template.ParseFiles()` 函数解析模板文件，然后调用 `tmpl.Execute()` 函数与模板文件合并，将结果发送到终端标准输出。

```go
package main

import (
    "encoding/csv"
    "io"
    "os"
    "text/template"
)

type V lans struct {
    Id, Name string
}

func main() {
    data, _ := os.Open("file.csv")

    reader := csv.NewReader(data)

    vlans := []V lans{}

    for {
        row, err := reader.Read()
        if err == io.EOF {
            break
        }

        vlans = append(vlans, V lans{
            Id: row[0],
            Name: row[1],
        })
    }

    tmpl, _ := template.ParseFiles("file.tpl")
    _ = tmpl.Execute(os.Stdout, vlans)
}
```

输出展示了基本模板数据：

```text
vlan 1
    name ONE
vlan 2
    name TWO
vlan 3
    name THREE
```

## 第 3.3 节：模板继承

模板继承用于处理嵌套模板，通过构建包含子模板的基本骨架来实现。这使得能够跨多个基本模板重用子模板。想象一下多种类型的路由器模板，它们都共享相同的公共子 BGP 或 NTP 模板。

在这个示例中，使用模板继承来组装一个由基本配置数据和多个代表路由器 BGP 和 NTP 配置的子组件组成的路由器配置。数据源将设置在下面的 YAML 文件中，以便轻松解析用户输入。

```yaml
base:
  hostname: router1

bgp:
  as: 1234
  id: 4.4.4.4
  neighbors:
    - ip: 1.1.1.1
      as: 1
    - ip: 2.2.2.2
      as: 2

ntp:
  source: Loopback0
  primary: 11.11.11.11
  secondary: 22.22.22.22
```

总共将使用三个模板文件：一个基本模板和两个嵌套模板。在每个文件中，在顶部利用注释元素来标识文件名，同时使用 define 元素来分配模板名称。由于这是模板继承，子模板通过在各自的位置引用子模板名称以及模板元素来与基本模板关联。

```go
{{/* base.tpl */}}

{{define "base"}}
hostname {{.Base.Hostname}}
{{template "bgp" .}}
{{template "ntp" .}}
{{end}}

{{/* bgp.tmpl */}}

{{ define "bgp" }}
router {{.Bgp.As }}
router-id {{.Bgp.Id -}}
{{range .Bgp.Neighbors}}
neighbor {{.Ip}} remote-as {{.As -}}
{{end}}
{{ end }}

{{/* ntp.tmpl */}}

{{ define "ntp" }}
ntp source-interface {{.Ntp.Source}}
ntp server {{.Ntp.Primary}} prefer
ntp server {{.Ntp.Secondary}}
{{ end }}
```

在下面的 Go 文件中，使用 `ioutil.ReadFile()` 函数将 YAML 文件读取到一个字节切片中。然后，使用 `yaml.Unmarshal()` 函数将字节切片解析为结构体实例。接下来，通过解析基本模板和子模板创建模板映射。最后，使用 `template.Template.ExecuteTemplate()` 方法将数据与模板映射合并，将数据发送到终端标准输出。

```go
package main

import (
    "text/template"
    "os"
    "gopkg.in/yaml.v2"
    "io/ioutil"
)

type Config struct {
    Base Base `yaml:"base"`
    Bgp Bgp `yaml:"bgp"`
    Ntp Ntp `yaml:"ntp"`
}
type Base struct {
    Hostname string `yaml:"hostname"`
}
type Bgp struct {
    As string `yaml:"as"`
    Id string `yaml:"id"`
    Neighbors []Neighbors `yaml:"neighbors"`
}
type Neighbors struct {
    Ip string `yaml:"ip"`
    As string `yaml:"as"`
}
type Ntp struct {
    Source string `yaml:"source"`
    Primary string `yaml:"primary"`
    Secondary string `yaml:"secondary"`
}

func main() {
    config := Config{}

    data, _ := ioutil.ReadFile("file.yaml")

    _ = yaml.Unmarshal(data, &config)

    tmpl := make(map[string]*template.Template)

    files, _ := template.ParseFiles("base.tpl", "bgp.tmpl", "ntp.tmpl")
    
    // 注意：原文在此处截断。根据上下文，接下来的行通常会是：
    // baseTmpl, _ := tmpl.ParseFiles("base.tpl") ... 或类似的解析逻辑以填充映射。
    // 然而，严格遵循“不要添加内容”的原则，我将在源文本停止的地方停止。
}
```

```
"bgp.tmpl", "ntp.tmpl")
tmpl["base.tmpl"] = template.Must(files, nil)
_ = tmpl["base.tmpl"].ExecuteTemplate(
  os.Stdout, "base", config)
}
```

下方的输出显示了合并后的数据和模板。

```
hostname router1

router 1234
  router-id 4.4.4.4
  neighbor 1.1.1.1 remote-as 1
  neighbor 2.2.2.2 remote-as 2

ntp source-interface Loopback0
ntp server 11.11.11.11 prefer
ntp server 22.22.22.22
```

# 第 4 章：HTTP 客户端

超文本传输协议（HTTP）客户端用于建立连接并向 HTTP 服务器请求数据。最常用的方法是 GET 和 POST。`http` 包支持 RFC 2616 中定义的属性，如超时、重定向和 Cookie。虽然该包提供了更基本的方法，如 `http.Client.Get()` 和 `http.Client.Post()` 方法，但为了应用自定义请求头，可以将 `http.NewRequest()` 函数与 `http.Client.Do()` 方法结合使用。本章将通过使用更常见的功能（如客户端超时、Cookie 和自定义请求头）示例，演示 GET 和 POST 请求。

本章将涵盖以下 HTTP 客户端主题：

- GET 请求
- POST 请求

## 4.1：GET

`http` 包支持 RFC 7231 第 4.3.1 节中定义的 GET 方法。简单的 GET 请求可以使用 `http.Client.Get()` 方法完成；如果需要自定义请求头，则可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数设置方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置一个请求头。接下来，在 `http.Client` 结构体中初始化 Timeout 字段，返回一个新的 `http.Client` 对象。现在，GET 请求已根据 URL 构建，客户端请求头也已定义，将它们与自定义超时一起使用，通过 `http.Client.Do()` 方法发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法接收 Response 对象，并在打印响应之前关闭请求体。

```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
	"time"
)

func main() {
	req, _ := http.NewRequest("GET",
		"http://example.com", nil)
	
	req.Header.Set("Cache-Control", "no-cache")
	
	client := &http.Client{Timeout: time.Second * 10}
	
	resp, _ := client.Do(req)
	body, _ := ioutil.ReadAll(resp.Body)
	resp.Body.Close()
	
	fmt.Printf("%s\n", body)
}
```

## 4.2：POST

`http` 包支持 RFC 7231 第 4.3.3 节中定义的 POST 方法。简单的 POST 请求可以使用 `http.Client.Post()` 方法完成。如果需要自定义请求头，可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数定义方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置请求头。接下来，在 `http.Cookie` 结构体中定义 Cookie 的 Name 和 Value 字段，返回一个新的 Cookie 对象，并通过 `http.Request.AddCookie()` 方法将其添加到请求中。然后，在 `http.Client` 结构体中设置 Timeout 字段，并返回一个新的 `http.Client` 对象。现在，POST 请求已构建，请求头已设置，将它们与新的客户端一起使用，在 `http.Client.Do()` 方法中发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法返回 Response 对象，并在打印响应之前关闭请求体。
