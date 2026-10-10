
答案与方法有关。用于选择嵌入类型字段的简写表示法也适用于选择其方法。实际上，外部结构体类型不仅获得了嵌入类型的字段，还获得了它的方法。这种机制是将复杂对象行为从简单行为中组合而成的主要方式。`Composition`（组合）是 Go 语言面向对象编程的核心，我们将在[第 6.3 节](#ebook_split_055.html#id-composition)中进一步探讨它。

## 4.5 JSON

JavaScript 对象表示法（JSON）是一种用于发送和接收结构化信息的标准表示法。JSON 并非唯一的此类表示法。XML（[§7.14](#ebook_split_073.html#id-exampletokenbasedxmldecoding)）、ASN.1 和 Google 的 Protocol Buffers 服务于类似目的，各有其适用领域，但由于其简洁性、可读性和通用支持，JSON 是应用最广泛的。

Go 语言通过标准库包 `encoding/json`、`encoding/xml`、`encoding/asn1` 等为这些格式的编码和解码提供了出色的支持，这些包都拥有相似的 API。本节简要概述 `encoding/json` 包中最重要的部分。

JSON 是 JavaScript 值（字符串、数字、布尔值、数组和对象）的编码，以 Unicode 文本形式呈现。它是对[第 3 章](#ebook_split_027.html#id-basicdatatypes)中的基本数据类型和本章中的复合类型（数组、切片、结构体和映射）的一种高效且可读的表示。

基本 JSON 类型包括数字（采用十进制或科学计数法）、布尔值（`true` 或 `false`）和字符串，字符串是包含在双引号中的 Unicode 码点序列，使用类似 Go 的反斜杠转义表示法，尽管 JSON 的 `\U`*hhhh* 数字转义表示 UTF-16 码位，而非 rune。

这些基本类型可以通过 JSON 数组和对象递归组合。JSON 数组是值的有序序列，写作用方括号括起来的逗号分隔列表；JSON 数组用于编码 Go 数组和切片。JSON 对象是从字符串到值的映射，写作用逗号分隔、用大括号包围的 `name:value` 对序列；JSON 对象用于编码 Go 映射（具有字符串键）和结构体。例如：

[单击此处查看代码图像](#ch04_images.html#id107pro01_r)

```
boolean            true
number             -273.15
string             "She said \"Hello, \""
array              ["gold", "silver", "bronze"]
object             {"year": 1980,
                    "event": "archery",
                    "medals": ["gold", "silver", "bronze"]}
```

考虑一个收集电影评论并提供推荐的应用程序。其 `Movie` 数据类型和典型值列表声明如下。（`Year` 和 `Color` 字段声明后的字符串字面量是*字段标签*；我们稍后会解释它们。）

[单击此处查看代码图像](#ch04_images.html#id108pro01_r)

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

像这样的数据结构非常适合 JSON，且双向转换都很容易。将像 `movies` 这样的 Go 数据结构转换为 JSON 称为*编组*。编组由 `json.Marshal` 完成：

[单击此处查看代码图像](#ch04_images.html#id108pro02_r)

```
data, err := json.Marshal(movies)
if err != nil {
    log.Fatalf("JSON marshaling failed: %s", err)
}
fmt.Printf("%s\n", data)
```

`Marshal` 生成一个包含非常长字符串的字节切片，没有多余的空白字符；我们折叠了行以便显示：

[单击此处查看代码图像](#ch04_images.html#id108pro03_r)

```
[{"Title":"Casablanca","released":1942,"Actors":["Humphrey Bogart","Ingr
id Bergman"]},{"Title":"Cool Hand Luke","released":1967,"color":true,"Ac
tors":["Paul Newman"]},{"Title":"Bullitt","released":1968,"color":true,"
Actors":["Steve McQueen","Jacqueline Bisset"]}]
```

这种紧凑表示包含所有信息但难以阅读。为了方便人类阅读，一种名为 `json.MarshalIndent` 的变体会生成整齐缩进的输出。两个额外的参数分别定义每行输出的前缀和每级缩进的字符串：

[单击此处查看代码图像](#ch04_images.html#id108pro04_r)

```
data, err := json.MarshalIndent(movies, "", "    ")
if err != nil {
    log.Fatalf("JSON marshaling failed: %s", err)
}
fmt.Printf("%s\n", data)
```

上述代码打印：

[单击此处查看代码图像](#ch04_images.html#id109pro01_r)

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

编组通过*反射*（正如我们将在[第 12.6 节](#ebook_split_116.html#id-exampledecodingsexpressions)中看到的）使用 Go 结构体字段名作为 JSON 对象的字段名。只有导出字段会被编组，这就是为什么我们为所有 Go 字段名选择了大写字母开头的名称。

您可能已经注意到，输出中 `Year` 字段的名称变成了 `released`，`Color` 变成了 `color`。这是因为*字段标签*。字段标签是一个在编译时与结构体字段关联的元数据字符串：

[单击此处查看代码图像](#ch04_images.html#id109pro02_r)

```
Year  int  `json:"released"`
Color bool `json:"color,omitempty"`
```

字段标签可以是任何字面字符串，但通常被解释为空格分隔的 `key:"value"` 对列表；因为它们包含双引号，字段标签通常使用原始字符串字面量编写。`json` 键控制 `encoding/json` 包的行为，其他 `encoding/...` 包遵循此约定。`json` 字段标签的第一部分为 Go 字段指定了一个替代的 JSON 名称。字段标签常用于为 Go 字段（如 `TotalCount`）指定惯用的 JSON 名称（如 `total_count`）。`Color` 的标签有一个额外选项 `omitempty`，表示如果字段具有其类型的零值（此处为 `false`）或为空，则不应生成 JSON 输出。果然，*Casablanca* 这部黑白电影的 JSON 输出中没有 `color` 字段。

编组的逆操作，即解码 JSON 并填充 Go 数据结构，称为*解组*，由 `json.Unmarshal` 完成。下面的代码将 JSON 电影数据解组到一个结构体切片中，该结构体只包含 `Title` 字段。通过这种方式定义合适的 Go 数据结构，我们可以选择解码 JSON 输入的哪些部分并丢弃哪些部分。`Unmarshal` 返回时，已用 `Title` 信息填充了切片；JSON 中的其他名称被忽略。

[单击此处查看代码图像](#ch04_images.html#id110pro01_r)

```
var titles []struct{ Title string }
if err := json.Unmarshal(data, &titles); err != nil {
    log.Fatalf("JSON unmarshaling failed: %s", err)
}
fmt.Println(titles) // "[{Casablanca} {Cool Hand Luke} {Bullitt}]"
```
