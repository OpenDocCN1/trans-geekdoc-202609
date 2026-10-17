
task you ask it to perform. Therefore, because you want your list of chores to persist between executions of the application, you need to store the chore state on disk. In other words, you retrieve the chores from storage, modify them, and flush the changes to storage. The changes persist until the next time you run the app.

You want the option to add more than one chore at a time, so you split the incoming chore description by commas and append each chore to the slice. Granted, this keeps you from using commas in individual chore descriptions, so the members of your household will have to keep their requests short (which isn’t all bad, in my opinion). As an exercise, figure out a way around this limitation. One approach may be to use a different delimiter, but keep in mind, whatever you choose as a delimiter may have significance on the command line. Another approach may be to add support for quoted strings containing commas.

The last piece of this puzzle is my favorite part about working on chores: marking them as complete (see Listing 12-8).

*--snip--*

```go
func complete(s string) error {
	i, err := strconv.Atoi(s)
	if err != nil {
		return err
	}

	chores, err := load()
	if err != nil {
		return err
	}

	if i < 1 || i > len(chores) {
		return fmt.Errorf("chore %d not found", i)
	}

	chores[i-1].Complete = true
	return flush(chores)
}
```

*Listing 12-8: Marking a chore as complete (`cmd/housework.go`)*

The `complete` function accepts the command line argument representing the chore you want to complete and converts it to an integer. I find I’m more efficient if I perform tasks one by one, so I’ll have you mark only one complete at a time. You then load the chores from storage and make sure the integer is within range. If so, you mark the chore complete. Since you’re numbering chores starting with 1 when displaying the list, you need to account for placement in the slice by subtracting 1. Finally, you flush the chores to storage.

Now, let’s tie everything together by implementing the app’s `main` function in Listing 12-9.

*--snip--*

```go
func main() {
	flag.Parse()

	var err error
	switch strings.ToLower(flag.Arg(0)) {
	case "add":
		err = add(strings.Join(flag.Args()[1:], " "))
	case "complete":
		err = complete(flag.Arg(1))
	}

	if err != nil {
		log.Fatal(err)
	}

	err = list()
	if err != nil {
		log.Fatal(err)
	}
}
```

*Listing 12-9: The main logic of the housework application (`cmd/housework.go`)*

You’ve put as much logic in the previous functions as possible, so this `main` function is quite minimal. You check the first argument to determine whether it’s an expected subcommand. If so, you call the appropriate function. You call the `list` function if `err` is still `nil` after accounting for the optional subcommand and its arguments.

All that’s left to do now is implement the storage `Load` and `Flush` functions for JSON, Gob, and protocol buffers.

## JSON

JSON is a common, human-readable, text-based data serialization format that uses key-value pairs and arrays to represent complex data structures. Most contemporary languages offer official library support for JSON, which is one reason it’s the customary encoding format for RESTful APIs.

JSON’s types include strings, Booleans, numbers, arrays, key-value objects, and `nil` values specified by the keyword `null`. JSON numbers do not differentiate between floating-points and integers. You can read more about Go’s JSON implementation at `https://blog.golang.org/json`.

Let’s look at what the contents of the `housework.db` file would be if we JSON-encoded the chores from Listing 12-6. I’ve formatted the JSON for easier reading in Listing 12-10, though you could use the encoder’s `SetIndent` method to do it for you.

```json
[
	{
		"Complete": false,
		"Description": "Mop floors"
	},
	{
		"Complete": false,
		"Description": "Clean dishes"
	},
	{
		"Complete": false,
		"Description": "Mow the lawn"
	}
]
```

*Listing 12-10: Formatted contents of the `housework.db` file after serializing the chores to JSON*

As you can see, the JSON is an array of objects, and each object includes `Complete` and `Description` fields and corresponding values.

Listing 12-11 details the JSON storage implementation using Go’s `encoding/json` package.

```go
package json

import (
	"encoding/json"
	"io"

	"github.com/awoodbeck/gnp/ch12/housework"
)

func Load(r io.Reader) ([]*housework.Chore, error) {
	var chores []*housework.Chore
	return chores, json.NewDecoder(r).Decode(&chores)
}

func Flush(w io.Writer, chores []*housework.Chore) error {
	return json.NewEncoder(w).Encode(chores)
}
```

*Listing 12-11: JSON storage implementation (`json/housework.go`)*

The `Load` function passes the `io.Reader` to the `json.NewDecoder` function and returns a decoder. You then call the decoder’s `Decode` method, passing it a pointer to the `chores` slice. The decoder reads JSON from the `io.Reader`, deserializes it, and populates the `chores` slice.

The `Flush` function accepts an `io.Writer` and a `chores` slice. It then passes the `io.Writer` to the `json.NewEncoder` function, which returns an encoder. You pass the `chores` slice to the encoder’s `Encode` function, which serializes the `chores` slice into JSON and writes it to the `io.Writer`.

Now that you’ve implemented a JSON package that can serve as storage for your application, let’s try it out in Listing 12-12.

```bash
$ go run cmd/housework.go

You're all caught up!

$ go run cmd/housework.go add Mop floors, Clean dishes, Mow the lawn
# [X] Description
1 [ ] Mop floors
2 [ ] Clean dishes
3 [ ] Mow the lawn

$ go run cmd/housework.go complete 2
# [X] Description
1 [ ] Mop floors
2 [X] Clean dishes
3 [ ] Mow the lawn

$ cat housework.db
[{"Complete":false,"Description":"Mop floors"},
{"Complete":true,"Description":"Clean dishes"},
{"Complete":false,"Description":"Mow the lawn"}]
```

*Listing 12-12: Testing the housework application with JSON storage on the command line*

Your first execution of the app lets you know you have nothing in your list of chores. You then add three comma-separated chores and complete the second one. Looks good. Note that the `housework.db` file also contains readable JSON (on Windows, use the `type` command instead of the `cat` command to view this file).

Let’s modify this application to use Go’s native binary encoding format.

## Gob

`Gob`，即“二进制数据大量”的缩写，是 Go 原生的二进制序列化格式。

Go 团队的工程师开发了 Gob，以结合协议缓冲器（protocol buffers）的高效性（这是 arguably 最流行的二进制序列化格式）与 JSON 的易用性。例如，协议缓冲器不允许我们像在 Listing 12-11 的 JSON 示例中那样直接实例化一个编码器并将数据结构丢给它。相反，Gob 的功能类似于 JSON 编码器，它能够智能推断对象的结构并对其进行序列化。

如果你想了解 Gob 的动机和细节，请阅读 Rob Pike 的博客文章 “Gobs of Data”（`https://blog.golang.org/gob`）。在此期间，让我们在 Gob（参见 Listing 12-13）中实现我们的存储后端。

```go
package gob

import (
	"encoding/gob"
	"io"

	"github.com/awoodbeck/gnp/ch12/housework"
)

func Load(r io.Reader) ([]*housework.Chore, error) {
	var chores []*housework.Chore
	return chores, gob.NewDecoder(r).Decode(&chores)
}

func Flush(w io.Writer, chores []*housework.Chore) error {
	return gob.NewEncoder(w).Encode(chores)
}
```

*Listing 12-13: Gob 存储实现（`gob/housework.go`）*

如果你在观察这段代码并发现它将 Listing 12-11 中的所有 `json` 替换为 `gob`，你并没有错。在 Go 中，Gob 与 JSON 使用起来同样方便，因为它会根据对象本身来推断需要编码的内容。下一节将说明这与协议缓冲器的区别。

最后一步是通过修改导入（参见 Listing 12-2 和 Listing 12-14）来替换 JSON 存储实现，改为 Gob 存储实现。

```go
// storage "github.com/awoodbeck/gnp/ch12/json"
storage "github.com/awoodbeck/gnp/ch12/gob"
// storage "github.com/awoodbeck/gnp/ch12/protobuf"
```

*Listing 12-14: 将 JSON 存储包替换为 Gob 存储包（`cmd/housework.go`）*

注释掉 Listing 12-2 中的 JSON 存储包导入，并取消注释 Gob 存储包导入。

由于你当前的 `housework.db` 文件包含 JSON，它与 Gob 不兼容。因此，使用 Gob 解码它时会出错。删除 `housework.db` 文件并重新测试应用（参见 Listing 12-15）。

```bash
$ rm housework.db
$ go run cmd/housework.go
```

完成了！
