
## 10.5 总结

本章解释了 Go 如何定义模板。本章的示例演示了根据输入数据创建变体。

## 第11 章 测试

测试是开发成功项目的任务之一。不幸的是，测试通常被推迟或未被认真考虑。测试可能是重复且复杂的。坦率地说，Go 以简单的方式定义测试，帮助开发者更多地关注测试而非构造。本章探索测试、基准测试和性能分析。

### 11.1 测试

Go 提供了一个集成的测试解决方案。实际上，任何签名为 `TestXXX(*testing.T)` 的函数都被解释为测试函数。示例 11.1 是检查 2+2 正性的简单演示。在这种情况下不会发生错误。然而，如果发现任何错误，参数 `t` 提供了 `Error` 方法来将此测试标记为失败。

#### 示例 11.1：简单测试。

```go
package example_01

import "testing"

func TestMe(t *testing.T) {
	r := 2 + 2
	if r != 4 {
		t.Error("expected 2 got", r)
	}
}
```

测试被认为用于 `go test` 工具。对于该示例，我们可以这样运行测试：

```bash
go test
PASS
ok github.com/juanmuel-tirado/SaveTheWorldWithGo/go_10_testing/testing/example_01.341s
>>> go test -v
=== RUN TestMe (0.00s)
- PASS TestMe (0.00s)
ok github.com/juanmuel-tirado/SaveTheWorldWithGo/go_10_testing/testing/example_01.090s
```

`go test` 的基本输出是测试的最终状态（ok）和经过的时间。当使用详细标志 (`-v`) 时，这些信息会打印给每一个测试。现在，如果我们强制产生错误，会得到：

```bash
go test
FAIL: TestMe (0.00s)
- example_01_test.go:8: expected 2 got 3
```

FAIL
exit status 1
FAIL github.com/juanmanuel-tirado/SaveTheWorldWithGo/10_testing/testing/example_010.089s

输出显示最终状态为 FAIL，并包含了我们在发生错误时添加的错误信息。

测试旨在提高代码的可靠性，同时帮助我们发现潜在的错误。在示例 11.2 中，我们测试了一个打印施瓦辛格电影台词的简单函数。为了测试我们实现的完整性，我们使用所有已有的电影调用了 `MovieQuote`。遗憾的是，我们忘记为电影《掠夺者》（Predator）定义对应的台词了。

#### 示例 11.2：函数测试。

```go
package example_02

import "testing"

type Quote string
type Movie string

const (
	Crush Quote = "To crush your enemies..."
	T1000 Quote = "I'll be back"
	Unknown Quote = "unknown"
	Conan Movie = "conan"
	Terminator2 Movie = "terminator2"
	Predator Movie = "predator"
)

func MovieQuote(movie Movie) Quote {
	switch movie {
	case Conan:
		return Crush
	case Terminator2:
		return T1000
	default:
		return Unknown
	}
}

func TestMovieQuote(t *testing.T) {
	movies := []Movie{Conan, Predator, Terminator2}
	for _, m := range movies {
		if q := MovieQuote(m); q == Unknown {
			t.Error("unknown quote for movie", m)
		}
	}
}
```

```
=== RUN TestMovieQuote
example02.go:33: unknown quote for movie
predator
FAIL: MovieQuote(0.0s)
FAIL
```

`testing` 包提供了许多功能来帮助测试的创建。在这方面，测试需求可能会随时间等因素而变化。有时会出现根据阶段产生的时间限制。可以使用 `t.Skip()` 跳过测试。它可以与 `testing.Short()` 函数配合使用，当在 `go test` 命令中设置了 `-short` 参数时，该函数返回 `true`，以避免详尽的测试。示例 11.3 展示了当迭代持续时间超过给定时间如何跳过测试。如果设置了 `-short` 标志，将会自动跳过测试。

## 示例 11.3：跳过测试。

```go
package example_03

import (
	"fmt"
	"math"
	"testing"
	"time"
)

func Sum(n int64, done chan bool) {
	var result int64 = 0
	var i int64
	for i = 0; i < n; i++ {
		result = result + i
	}
	done <- true
}

func TestSum(t *testing.T) {
	var i int64
	done := make(chan bool)
	for i = 0; i < math.Max64; i+=100000 {
		go Sum(i, done)
		timeout := time.NewTimer(time.Millisecond)
		select {
		case <-timeout.C:
			t.Skip(fmt.Sprintf("%d took longer than 1 millisecond", i))
		case <-done:
		}
	}
}
```

```
go test -v
=== RUN
example03.test.go:27: 411000 took longer than 1 millisecond
SKIP: TestSum(0.02s)
PASS
ok github.com/juanuel-tirado/SaveTheWorldWithGo/10_testing/testing/example_030.256s
```

#### 11.1.1 子测试

某些测试可以用于测试特定的代码属性。可以使用 `t.Run()` 函数触发其他测试。

```go
func TestFoo(t *testing.T) {
	t.Run("A1", func(t *testing.T) { })
	t.Run("A2", func(t *testing.T) { })
	t.Run("B1", func(t *testing.T) { })
}
```

在下面的示例中，`TestFoo` 调用了三个函数。随后，这些测试函数又调用了其他。第一个参数是字符串，可以方便地设为 `key=value` 格式。这可以标识测试，并允许我们在 `go` 命令中隔离要运行的测试。

我们通过一个实际示例展示了如何处理子测试。由于代码可能较大，无法一次性显示，我们将其分为两个部分以提高可读性。在这个示例中，我们想要测试一个可以用 XML 和 JSON 格式定义的的用户类型。如果你不熟悉编码器（encoders），请查阅 B 章。

## 示例 11.4：实践中的子测试（第一部分）。

```go
package example_03

import (
	"encoding/json"
	"encoding/xml"
	"errors"
	"fmt"
	"io/ioutil"
	"os"
	"testing"
)

type Encoding int

const (
	XML Encoding = iota
	JSON
)

type User struct {
	UserID string `xml:"id" json:"id"`
	Email string `xml:"email" json:"email"`
	Score int    `xml:"score" json:"score"`
}

var Users []User

func (u *User) Equal(v User) bool {
	if u.UserID != v.UserID || u.Email != v.Email || u.Score != v.Score {
		return false
	}
	return true
}

func (u *User) encode(format Encoding) ([]byte, error) {
	var encoded []byte
	var err error
	switch format {
	case XML:
		encoded, err = xml.Marshal(u)
	case JSON:
		encoded, err = json.Marshal(u)
	default:
		return nil, errors.New("unknown encoding")
	}
	return encoded, err
}

func (u *User) fromEncoded(format Encoding, encoded []byte) error {
	recovered := User{}
	var err error
	switch format {
	case XML:
		err = xml.Unmarshal(encoded, &recovered)
	case JSON:
		err = json.Unmarshal(encoded, &recovered)
	default:
		err = errors.New("unknown encoding")
	}
	if err == nil {
		*u = recovered
	}
	return err
}

func (u *User) write(encoded []byte, path string) error {
	return ioutil.WriteFile(path, encoded, 0644)
}

func (u *User) writeEncoded(format Encoding, path string) error {
	encoded, err := u.encode(format)
	if err != nil {
		return err
	}
	return u.write(encoded, path)
}
```

我们可以使用正则表达式 `/../Action=Write` 运行匹配任何编码的写操作。

```
go test -v run //../Action/Write
=== RUN TestEncoding
=== RUN TestEncoding/EncodingXML
=== RUN TestEncoding/EncodingXML/Action=Write
=== RUN TestEncoding/EncodingJSON
=== RUN TestEncoding/EncodingJSON/Action=Write
PASS: TestEncoding (0.00s)
  PASS: TestEncoding/EncodingXML/Action=Write (0.00s)
  PASS: TestEncoding/EncodingJSON (0.00s)
  PASS: TestEncoding/EncodingJSON/Action=Write (0.00s)
```

PASS
okithub.com/juanmanuel-tirado/SaveTheWorldWithGo/10_testing/testing/example_030.083s

注意，只有测试读操作将会失败，因为该操作期望一个之前由测试写入的文件。修改代码以允许运行 `go test -v run ../Action/Read` 仍留给读者作为练习。

## 11. 示例 (EXAMPLES)

同样地，Go 中的测试是通过以 `Test` 开头的函数定义的，而示例也可以用 `Example` 开头的函数定义。示例的一个有趣特性是，在测试期间可以检查它们生成的标准标准输出。这是确保代码一致性的一个重要特性。此外，如第 12.2 节所述，示例会被包含在 Go 生成的文档中。

示例遵循下方描述的命名规范。

```go
func Example() { // 用于包
func ExampleF(f *F) // F 用于函数
func ExampleT(t *T) // T 用于类型
func ExampleM(m *M) // 类型为 T 的方法
func ExampleMSuffix(suffix string) // 如果有多个，则带有后缀
```

为了检查正确性，每个示例都必须定义要生成的输出。这通过使用 `Output` 命令来指示，因为输出顺序是不保证的，我们可以使用无序输出：而不是 `Output`。

```go
func Example() {
  // Output:
  // 预期输出
}
```

示例 11.6 定义了用户类型及其方法。注意，不同示例的表示遵循上述指南。示例像测试一样运行运行。

#### 示例 11.6：示例的定义。

```go
1 package example_01

2
3 import (
4     "fmt"
5     "strings"
6 )
7
8 type User struct {
9     UserId string
10    Friends []User
11 }
12
13 func (u *User) GetUserId() string {
14     return strings.ToUpper(u.UserId)
15 }
16
17 func (u *User) CountFriends() int {
18     return len(u.Friends)
19 }
20
21 func CommonFriend(a *User, b *User) *User {
22     for _, af := range a.Friends {
23         for _, bf := range b.Friends {
24             if af.UserId == bf.UserId {
25                 return &af
26             }
27         }
28     }
29     return nil
30 }
31
32 func ExampleUser() {
33     j := User("John", nil)
34     m := User("Mary", []User{j})
35     fmt.Println(m)
36
37     // Output:
38     {Mary ([John])}
39 }
40
41 func ExampleCommonFriend() {
42     a := User("a", nil)
43     b := User("b", []User{a})
44     c := User("c", []User{a,b})
45
46     fmt.Println(CommonFriend(&a, &c))
47
48     // Output:
49     &(a)
50 }
51
52 func ExampleUser_GetUserId() {
```

| go test -v |
| --- |
| === RUN ExampleUser |
| PASS: ExampleUser (0.00s) |
| === RUN ExampleCommonFriend |
| PASS: ExampleCommonFriend (0.00s) |
| === RUN ExampleGetUserId |
| PASS: ExampleGetUserId (0.00s) |
| === RUN ExampleCountFriends_User |
| PASS: ExampleCountFriends_User (0.00s) |
| PASS (0.00s) |

```go
u := User("John",nil)
fmt.Println(u.GetUserId())
// Output:
// JOHN
}

func ExampleUser_CountFriends() {
  u := User("John", nil)
  fmt.Println(u.CountFriends())
  // Output:
  // 0
}
```
