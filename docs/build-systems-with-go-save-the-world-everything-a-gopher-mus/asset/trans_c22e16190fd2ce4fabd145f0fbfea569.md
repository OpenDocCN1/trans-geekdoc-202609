

Marshal 函数将布尔、整数、浮点数、字符串、数组和切片转换为对应的 JSON 表示。示例 8.3 显示了在序列化（marshalling）类型后生成的输出。注意，Marshal 函数返回一个带有输入 JSON 表示形式的 `[]byte`，并在失败时返回错误。

## 示例 8.3: JSON 序列化。

```go
package main

import (
	"encoding/json"
	"fmt"
)

func main() {
	number, err := json.Marshal(42)
	if err != nil {
		panic(err)
	}
	fmt.Println(string(number))

	float, _ := json.Marshal(3.14)
	fmt.Println(string(float))

	msg, _ := json.Marshal("This is a msg!!")
	fmt.Println(string(msg))

	numbers, _ := json.Marshal([]int{1,1,2,3,5,8})
	fmt.Println(string(numbers))

	aMap, _ := json.Marshal(map[string]int{"one":1,"two":2})
	fmt.Println(string(aMap))
}
```

如果 JSON 格式正确，unmarshal 函数（反序列化）可以将其转换为之前已的类型。示例 8.4 恢复了 `int` 和 `map[string]int` 的 JSON 表示。反序列化过程需要转换为与要序列化的数据兼容的类型，如果过程失败则返回错误。注意，此示例的输出是 Go 类型的字符串表示，而不是 JSON 表示。

## 示例 8.4: JSON 反序列化。

```go
package main

import (
	"encoding/json"
	"fmt"
)

func main() {
	aNumber, _ := json.Marshal(42)

	var recoveredNumber int = -1
	err := json.Unmarshal(aNumber, &recoveredNumber)
	if err != nil {
		panic(err)
	}
	fmt.Println(recoveredNumber)

	aMap, _ := json.Marshal(map[string]int{"one":1,"two":2})
	recoveredMap := make(map[string]int)
	err := json.Unmarshal(aMap, &recoveredMap)
	if err != nil {
		panic(err)
	}
	fmt.Println(recoveredMap)
}
```

结构体也可以与 Marshal 和 Unmarshal 函数配合使用。实际上，Go 提供了特殊的标签（tags）来帮助完成此任务。可以对字段进行标记，以指示它们如何转换为 JSON。

在示例 8.5 中，我们定义了一个用户数据库，其中用户用 `User` 值表示。每个字段都标记有一个由以下内容组成的表达式：

```
FieldName type json:`jsonFieldName,omitempty`````

该标签定义了在 JSON 对象中如何命名该字段，以及在发现零值时是否跳过它。在我们的示例中，user 没有 `Score`。在打印序列化后的表示 (`dbJson`) 时，注意缺少了一个分数。此外，密码始终是缺失的。这是因为字段的可见性不允许导出值。在这种情况下，我们可以认为使用用户密码是一种良好的做法。

## 示例 8.5: 自定义结构体 JSON 序列化。

```go
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
)

type User struct {
	UserId   string `json:"userId,omitempty"`
	Score    int    `json:"score,omitempty"`
	password string `json:"password,omitempty"`
}

func main() {
	userA := User{UserId: "Gopher", Score: 1000}
	userJSON, _ := json.Marshal(userA)
	fmt.Println(string(userJSON))

	userList := []User{
		{UserId: "Gopher", Score: 1000},
		{UserId: "BigJ", Score: 10},
		{UserId: "GBoom"},
	}
	dbJson, _ := json.Marshal(userList)
	fmt.Println(string(dbJson))
}
```

```json
{"userId":"Gopher","score":1000}
[{"userId":"Gopher","score":1000},{"userId":"BigJ","score":10},{"userId":"GBoom"}]
```

为了提高 JSON 输出的可读性，可以使用缩进进行序列化。`indent` 函数会添加缩进并将输出发送到缓冲区类型 (`io.Writer`)。最后，示例显示了反序列化的结构体。观察，字段省略仅在序列化期间起作用。在反序列化期间，省略的字段会被简单地设置为零值。

## XML

可扩展标记语言 (XML) 是 W3C 在 1998 年开发的标记语言。和 JSON 一样，它是人类可读且易于解析的。然而，它非常冗长，限制了它在某些场景下的适用性。`encoding/xml` 包提供了处理这种格式的函数。它的工作方式与上一节解释的 `encoding/json` 包类似。它们共享相同的接口。但是，XML 有一些限制，我们将在下面的示例中解释。

## 示例 8.6: XML 序列化。

```go
package main

import (
	"encoding/xml"
	"fmt"
)

func main() {
	number, err := xml.Marshal(42)
	if err != nil {
		panic(err)
	}
	fmt.Println(string(number))

	float, _ := xml.Marshal(3.14)
	fmt.Println(string(float))

	msg, _ := xml.Marshal("This is a msg!")
	fmt.Println(string(msg))

	numbers, _ := xml.Marshal([]int{1, 2, 3, 5, 8})
	fmt.Println(string(numbers))

	aMap, err := xml.Marshal(map[string]int{"one":1,"two":2})
	if err != nil {
		fmt.Println(err)
	}
	fmt.Println("-", string(aMap))
}
```

```xml
<int
xml: unsupported type: map[string]int
```

注意在序列化 `map[string]int` 时我们得到了一个错误。与示例 8.3 不同（我们可以将相同类型序列化为格式正确的 JSON），我们无法在 XML 中直接这样做。这是因为在 XML 中表示 map 没有单一方法。由于这个原因，该包的实现从序列化中除了 map 类型。

对于这种情况，我们需要定义自己的序列化。为了实现这一点，我们可以创建一个实现 `MarshalXML` 和 `UnmarshalXML` 的类型。这些方法在序列化和反序列化操作期间被调用，因此我们可以控制任何类型的 XML 表示。示例 8.7 定义了 `map[string]` 类型的转换，使用键作为元素标签，值作为元素。代码没有涵盖所有场景，但可以作为读者理解自定义序列化器的起点。

 示例 8.7: XML 反序列化。

```go
package main

import (
	"encoding/xml"
	"errors"
	"fmt"
)

type MyMap map[string]string

func (m *MyMap) MarshalXML(e *xml.Encoder, start xml.Element) error {
	tokens := []xml.Token{start}

	for key, value := range m {
		t := xml.StartElement{Name: xml.Name(Space: "", Local: key)}
		tokens = append(tokens, t, xml.CharData(value), xml.EndElement{t.Name})
	}

	tokens = append(tokens, xml.EndElement{start.Name})

	for _, t := range tokens {
		err := e.EncodeToken(t)
		if err != nil {
			return err
		}
	}
	return e.Flush()
}

func (m *MyMap) UnmarshalXML(d *xml.Decoder, start xml.Element) error {
	key := ""
	val := ""
	for {
		t, _ := d.Token()
		switch tt := t.(type) {
		case xml.StartElement:
			key = tt.Name.Local
		case xml.CharData:
			val = string(tt)
		case xml.EndElement:
			if len(key) != 0 {
				(*m)[key] = val
				key, val = "", ""
			}
			if tt.Name == start.Name {
				return nil
			}
		default:
			return errors.New(fmt.Sprintf("unknown %T", t))
		}
	}
}
```

```go
func main() {
	var theMap MyMap = map[string]string{"one": "1", "two": "2", "three": "3"}
	aMap, _ := xml.Marshal(&theMap, "", " ")
	fmt.Println(aMap)

	var recoveredMap MyMap = make(map[string]string)

	err := xml.Unmarshal(aMap, &recoveredMap)
	if err != nil {
		panic(err)
	}

	fmt.Println(recoveredMap)
}
```

```xml
<MyMap>
<one>1</one>
<two>2</two>
<three>3</three>
</MyMap>
```

