
```text
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```

在本示例中，使用 `os.Open()` 函数以只读模式打开文件，该函数返回一个 `os.File` 实例。接着，将 `os.File` 对象作为参数传递给 `csv.NewReader()` 函数，该函数返回一个缓冲的 `csv.Reader` 对象。然后，使用 `csv.Reader.Read()` 方法将每个文件记录解码到结构体中，并将它们存储在一个切片中，直到返回 `io.EOF`，表明已达到文件末尾。最后，切片遍历每个值。

```go
package main

import (
	"encoding/csv"
	"fmt"
	"io"
	"os"
)

type Row struct {
	ColA, ColB, ColC string
}

func main() {
	file, _ := os.Open("file.csv")

	reader := csv.NewReader(file)

	rows := []Row{}

	for {
		row, err := reader.Read()
		if err == io.EOF {
			break
		}

		rows = append(rows, Row{
			ColA: row[0], ColB: row[1], ColC: row[2],
		})
	}
	for _, row := range rows {
		fmt.Printf("%s -- %s -- %s\n",
			row.ColA, row.ColB, row.ColC)
	}
}
```

### 2.2.2 章：编写 CSV

`csv` 包包含一个 `NewWriter()` 函数，该函数返回一个用于写入 CSV 记录的 Writer 对象。`csv.Writer` 写入以换行符结尾的记录，并使用逗号作为字段分隔符。本示例演示如何将数据写入 CSV 文件。

以下示例首先将示例数据格式化为二维切片。然后，使用 `os.Create()` 函数创建文件，如果文件已存在则将其截断，并返回一个 `os.File` 对象实例。接着，将 `os.File` 实例作为参数传递给 `csv.NewWriter()` 函数，以获得一个缓冲的 `csv.Writer` 对象。然后，调用 `csv.Writer.Write()` 方法将每个字符串切片作为 CSV 记录写入文件。最后，使用 `csv.Writer.Flush()` 方法将剩余的缓冲数据刷新到潜在的 `csv.Writer` 中，并使用 `os.File.Close()` 方法关闭文件。

```go
package main

import (
	"encoding/csv"
	"os"
)

func main() {
	rows := [][]string{
		{"HOST", "IP ADDR", "LOCATION"},
		{"RTR1", "1.1.1.1", "Seattle, WA"},
		{"RTR2", "2.2.2.2", "Nevada, NV"}
	}

	file, _ := os.Create("file.csv")

	writer := csv.NewWriter(file)

	for _, row := range rows {
		_ = writer.Write(row)
	}

	writer.Flush()

	file.Close()
}
```

以下是以表格形式查看生成的文件。

| 主机 | IP 地址 | 位置 |
| :--- | :--- | :--- |
| RTR1 | 1.1.1.1 | 西雅图, 华盛顿 |
| RTR2 | 2.2.2.2 | 内华达, 内华达州 |

以下是以纯文本形式在文本编辑器中查看的相同文件。

```text
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```

## 2.3 章：YAML

YAML Ain't Markup Language（YAML）是一种流行的格式，通常用于读取和写入配置文件。它也可以用于转换数据并支持兼容性。

YAML 具有人类友好的布局，并支持易于遵循的语法。通常，冒号用于键值对，缩进用于嵌套，连字符用于列表成员。

`yaml.v2` 包与大多数 YAML 1.1 和 1.2 兼容。它通常被用作解析和生成 YAML 格式数据的快速且可靠的首选包。

本小节将涵盖以下主题：

- 读取 YAML 文件
- 编写 YAML 文件

### 2.3.1 章：读取 YAML

`yaml.v2` 包支持一个 `Unmarshal()` 函数，该函数将数据从字节切片解码为值。如果解码的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "yaml" 结构体字段标签定义自定义键。

在这个简单示例中，使用 `yaml.Unmarshal()` 函数将以下 YAML 文件中的数据解码到结构体中。

```yaml
host: localhost
ports:
 - 80
 - 443
```

首先，定义一个结构体，首字母大写，并使用 "yaml" 字段标签来识别键。然后，使用 `ioutil.ReadFile()` 函数读取文件，该函数返回一个字节切片，并使用 `yaml.Unmarshal()` 函数将数据解码到结构体实例中。最后，打印结构体实例的成员值，以展示解码后的 YAML 文件。

```go
package main

import (
	"fmt"
	"gopkg.in/yaml.v2"
	"io/ioutil"
)

type Config struct {
	Host  string `yaml:"host"`
	Ports []int  `yaml:"ports"`
}

func main() {
	data, _ := ioutil.ReadFile("file.yaml")
	conf := Config{}
	_ = yaml.Unmarshal(data, &conf)
	fmt.Printf("%s:%d\n", conf.Host, conf.Ports)
}
```

以下输出显示每个值在冒号的两侧格式化。

```text
localhost:[80,443]
```

### 2.3.2 章：编写 YAML

`yaml.v2` 包支持一个 `Marshal()` 函数，该函数用于将值序列化为 YAML 格式。虽然通常使用结构体来支持这些值，但也接受映射和指针。只有当结构体字段是导出的（即首字母大写）时才会被序列化。使用 "yaml" 结构体字段标签定义自定义键。

在本示例中，使用 `yaml.Marshal()` 函数将结构体中的数据序列化并写入到 YAML 格式的文件中。首先，定义一个结构体，首字母大写，并使用 "yaml" 字段标签来识别文件中的键。接着，用值初始化结构体，并使用 `yaml.Marshal()` 函数进行序列化。最后，接收序列化后的 YAML 格式字节切片，并使用 `ioutil.WriteFile()` 函数将其写入文件。

```go
package main

import (
	"gopkg.in/yaml.v2"
	"io/ioutil"
)

type Config struct {
	Host  string `yaml:"host"`
	Ports []int  `yaml:"ports"`
}

func main() {
	conf := Config{
		Host:  "localhost",
		Ports: []int{80, 443},
	}

	data, _ := yaml.Marshal(&conf)
}
```

_ = ioutil.WriteFile("file.yaml", data, 0644)

}

以下输出展示了示例中创建的文件，其中包含以 YAML 格式写入的各个值。

```
host: localhost
ports:
 - 80
 - 443
```

## 第 2.4 章：JSON

JavaScript 对象表示法（JSON）是一种数据交换格式，通常用于 Web 前端与后端服务器以及移动应用之间。大多数现代网络设备支持交换 JSON 编码数据的 REST 接口。

`json` 包支持读取和写入 RFC 7159 中定义的 JSON 格式。必须遵守一些特定的 Go 语言规则：

- 导出的结构体字段必须以大写字母开头。
- JSON 对象仅支持字符串作为键。
- 函数、通道和复数类型不会被编码。
- 不支持循环数据结构。
- 指针在编码前会被解引用。

本章将涵盖以下主题：

- 读取 JSON 文件
- 写入 JSON 文件

### 第 2.4.1 节：读取 JSON

`json` 包包含一个 `Unmarshal()` 函数，支持将字节切片中的数据解码为值。如果解码后的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "json" 结构体字段标签可以自定义键。

在这个示例中，使用 `json.Unmarshal()` 函数将以下 JSON 格式文件中的值解码到结构体中。

```json
{
  "total": 3,
  "devices": [
    "SW1",
    "SW2",
    "SW3"
  ]
}
```

首先，定义一个与 JSON 文件中的数据对应的结构体。然后，使用 "json" 字段标签来标识各个键。接下来，使用 `ioutil.ReadFile()` 函数读取文件，该函数返回一个字节切片，该切片通过 `json.Unmarshal()` 函数解码到结构体实例中。最后，打印结构体实例的成员值，以演示 JSON 文件已被解码。

```go
package main

import (
  "encoding/json"
  "fmt"
  "io/ioutil"
)

type Inventory struct {
Total int `json:"total"`
Devices []string `json:"devices"`
}

func main() {
    data, _ := ioutil.ReadFile("file.json")

    inv := Inventory{}

    _ = json.Unmarshal([]byte(data), &inv)

    fmt.Printf("Total: %d\nDevices: %q\n",
               inv.Total, inv.Devices)
}
```

输出显示冒号右侧的每个值，旁边是对应的标签。为清晰起见，设备保持字符串切片格式。

Total: 3

Devices: ["SW1" "SW2" "SW3"]

### 第 2.4.2 节：写入 JSON

`json` 包支持 `Marshal()` 函数，用于将值序列化为 JSON 格式。虽然通常使用结构体来分组值，但也接受 maps。只有导出的结构体字段（因此首字母为大写）才会被序列化。使用 "json" 结构体字段标签可以自定义键。

在这个示例中，使用 `json.Marshal()` 函数将结构体中的值序列化并写入 JSON 格式的文件。首先，定义一个首字母大写并带有 "json" 字段标签的结构体，以标识文件中的键。初始化结构体值，然后使用 `json.Marshal()` 函数进行序列化。最后，接收序列化后的 JSON 格式字节切片，并将其写入文件，使用 `ioutil.WriteFile()` 函数。

```go
package main

import (
	"encoding/json"
	"fmt"
)

type Inventory struct {
	Total int `json:"total"`
	Devices []string `json:"devices"`
}

func main() {
	data := &Inventory{
		Total: 3,
		Devices: []string{"SW1", "SW2", "SW3"},
	}

	inv, _ := json.MarshalIndent(data, "", "  ")

fmt.Println(string(inv))
}
```

输出显示一个文件，其中每个值均以 JSON 格式呈现。虽然此处将 JSON 格式数据写入文件以展示其功能，但将 JSON 格式数据写入 REST API 也很常见，如第 4.2 章稍后所示。

```json
{
"total": 3,
"devices": [
"SW1",
"SW2",
"SW3"
]
}
```

## 第 2.5 章：XML

可扩展标记语言（XML）是一种标记语言，通常用作 Web 服务中的数据通信格式。由于其紧凑的结构，这种简化格式通常比 JSON 更受欢迎。

`xml` 包支持读取和写入 XML 1.0。由于 XML 形成树状数据结构，可以使用 Go 中的结构体以类似的层级结构进行定义。后续小节中的示例将利用结构体来编码和解码 XML。

本章将涵盖以下主题：

- 读取 XML 文件
- 写入 XML 文件

### 第 2.5.1 节：读取 XML

`xml` 包包含一个 `Unmarshal()` 函数，支持将字节切片中的数据解码为值。如果解码后的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "xml" 结构体字段标签可以自定义键。

在这个示例中，使用 `xml.Unmarshal()` 函数将以下 XML 格式文件中的值解码到结构体中。

```xml
<campus name="campus1">
    <!-- building-comment -->
    <building name="bldg1">
        <!-- device-comment -->
        <device type="router" name="rtr1"></device>
    </building>
</campus>
```

首先，定义一个结构体，并使用 "xml" 字段标签来标识文件中的键。接下来，使用 `ioutil.ReadFile()` 函数读取文件并返回一个字节切片，然后使用 `xml.Unmarshal()` 函数将其解码到结构体实例中。最后，打印结构体实例的成员值，以演示解码后的数据。

```go
package main

import (
    "encoding/xml"
    "fmt"
    "io/ioutil"
)

type Campus struct {
    XMLName xml.Name `xml:"campus"`
    Name     string   `xml:"name,attr"`
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

func main() {
    data, _ := ioutil.ReadFile("file.xml")

    camp := &Campus{}

    _ = xml.Unmarshal([]byte(data), &camp)

    fl := fmt.Println
    fl("Campus Name: ", camp.Name)
    fl("Building Name: ", camp.Building.Name)
    fl("Building Comment:", camp.Comment)
    fl("Device Comment: ", camp.Building.Comment)
    fl("Device Name: ", camp.Building.Device.Name)
    fl("Device Type: ", camp.Building.Device.Type)
}
```

输出显示每个值及其相应的字段名。

- Campus Name: campus1
- Building Name: bldg1
- Building Comment: building-comment
- Device Comment: device-comment
- Device Name: rtr1
- Device Type: router

### 第 2.5.2 节：写入 XML

`xml` 包支持 `Marshal()` 函数，用于将值序列化为 XML 格式。虽然通常使用结构体来分组值，但也接受 maps。只有导出的结构体字段（因此首字母为大写）才会被序列化。使用 "xml" 结构体字段标签可以自定义键。

在这个示例中，使用 `xml.Marshal()` 函数将结构体中的值序列化并写入 XML 格式的文件。首先，定义一个首字母大写并使用 "xml" 字段标签标识键的结构体。初始化结构体值，然后使用 `xml.Marshal()` 函数进行序列化。最后，接收序列化后的 XML 格式字节切片，并使用 `ioutil.WriteFile()` 函数将其写入文件。
