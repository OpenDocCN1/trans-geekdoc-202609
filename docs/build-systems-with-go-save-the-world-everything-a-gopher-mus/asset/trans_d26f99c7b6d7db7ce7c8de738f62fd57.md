
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

### 示例 11.6：示例的定义。

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

## 11.3 基准测试 (BENCHMARKING)

为带有 `Benchmark` 前缀的函数提供基准测试。当设置 `-bench` 标志时，会使用 `go test` 命令执行基准测试。它们使用 `testing.B` 类型而不是普通测试的 `testing.T`。

示例 11.7 显示了一个用于计算数字和的循环的基本基准测试。`b` 的值包含了性能测量中每次操作的重复次数。正如基准输出确认的那样，基准测试带有 `b.N` 值运行了三次。这样做是为了确保基准测试的可靠性。

可以使用提供的 `go test` 标志对基准测试进行高度配置。基准输出指示了可用的 goroutine 数量 (BenchmarkSum-16)、执行的迭代次数 (3817) 以及每次迭代经过的纳秒数 (265858)。

### 示例 11.7：函数基准测试。

```go
package example_01

import (
  "fmt"
  "testing"
)

func Sum(n int64) int64 {
  var result int64 = 0
  for i := 0; i<n; i++ {
    result = result + i
  }
  return result
}

func BenchmarkSum(b *testing.B) {
  fmt.Printf("b.N: %d\n", b.N)
  for i := 0; i < b.N; i++ {
    Sum(1000)
  }
}
```
