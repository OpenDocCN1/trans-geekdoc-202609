
```go
import "testing/fstest"
```

```go
type Post struct {
}
```

```go
func NewPostsFromFS(fileSystem fstest.MapFS) []Post {
	return nil
}
```

测试现在应该正确失败

```
=== RUN TestNewBlogPosts
blogposts_test.go:48: got 0 posts, wanted 2 posts
```

## 编写足够代码使其通过

我们可以通过“slime”使其通过：

```go
func NewPostsFromFS(fileSystem fstest.MapFS) []Post {
	return []Post{{}, {}}
}
```

> Slime is useful for giving a “skeleton” to your object. Designing an interface and executing logic are two concerns, and sliming tests strategically lets you focus on one at a time.

我们已经有了结构。那么，我们该怎么做呢？

由于我们缩小了范围，我们需要做的就是读取目录并为遇到的每个文件创建一个文章。我们暂时不必担心打开文件和解析它们。

```go
func NewPostsFromFS(fileSystem fstest.MapFS) []Post {
	dir, _ := fs.ReadDir(fileSystem, ".")
	var posts []Post
	for range dir {
		posts = append(posts, Post{})
	}
	return posts
}
```

`fs.ReadDir` 读取给定 `fs.FS` 内的目录，返回 `[...]DirEntry`。

我们理想化的设想已经被现实打破了，因为错误可能发生，但请记住，我们现在的重点是*让测试通过*，而不是改变设计，所以暂时忽略这个错误。

剩下的代码很直接：遍历这些条目，为每一个创建一个 `Post`，然后返回这个切片。

## 重构

尽管我们的测试通过了，我们仍然无法在这个上下文之外使用我们的新包，因为它与具体的实现 `fstest.MapFS` 耦合在一起。但这不是必须的。把我们 `NewPostsFromFS` 函数的参数改为接受标准库中的接口。

```go
func NewPostsFromFS(fileSystem fs.FS) []Post {
    dir, _ := fs.ReadDir(fileSystem, ".")
    var posts []Post
    for range dir {
        posts = append(posts, Post{})
    }
    return posts
}
```

重新运行测试：一切都应该正常。

## 错误处理

在专注于让“快乐路径”工作时，我们把错误处理搁置了。在继续迭代功能之前，我们应该认识到，在处理文件时错误是可能发生的。

除了读取目录之外，打开单个文件时也可能会遇到问题。让我们改变 API（当然，首先通过测试驱动），使其能够返回错误。

```go
func TestNewBlogPosts(t *testing.T) {
    fs := fstest.MapFS{
        "hello world.md": {Data: []byte("hi")},
        "hello-world2.md": {Data: []byte("hola")},
    }
    posts, err := blogposts.NewPostsFromFS(fs)
    if err != nil {
        t.Fatal(err)
    }
    if len(posts) != len(fs) {
        t.Errorf("got %d posts, wanted %d posts", len(posts), len(fs))
    }
}
```

运行测试：它应该会抱怨返回值数量不对。修复代码很简单。

```go
func NewPostsFromFS(fileSystem fs.FS) ([]Post, error) {
    dir, err := fs.ReadDir(fileSystem, ".")
    if err != nil {
        return nil, err
    }
    var posts []Post
    for range dir {
        posts = append(posts, Post{})
    }
    return posts, nil
}
```

这将使测试通过。你体内的 TDD 实践者可能会感到不满，因为在编写从 `fs.ReadDir` 传播错误的代码之前，我们没有看到一个失败的测试。要“正确地”做到这一点，我们需要

```go
// rest of test code cut for brevity
got := posts[0]
want := blogposts.Post{Title: "Post 1"}
if !reflect.DeepEqual(got, want) {
    t.Errorf("got %v, want %v", got, want)
}
}
```

## 尝试运行测试

```
./blogpost_test.go:58:26: unknown field 'Title' in struct literal of type blogposts.Post
```

## 编写最少的代码让测试运行，并检查失败的测试输出

给我们的 `Post` 类型添加新字段，以便测试能够运行。

```go
type Post struct {
    Title string
}
```

重新运行测试，你应该能看到一个明确的、失败的测试。

```
=== RUN   TestNewBlogPosts
=== RUN   TestNewBlogPosts/parses_the_post
    blogpost_test.go:61: got {Title:}, want {Title:Post 1}
```

## 编写足够的代码让它通过

我们需要打开每个文件，然后提取标题。

```go
func NewPostsFromFS(fileSystem fs.FS) ([]Post, error) {
    dir, err := fs.ReadDir(fileSystem, ".")
    if err != nil {
        return nil, err
    }
    var posts []Post
    for _, f := range dir {
        post, err := getPost(fileSystem, f)
        if err != nil {
            return nil, err //todo: needs clarification, should
        }
        posts = append(posts, post)
    }
    return posts, nil
}

func getPost(fileSystem fs.FS, f fs.DirEntry) (Post, error) {
    postFile, err := fileSystem.Open(f.Name())
    if err != nil {
        return Post{}, err
    }
    defer postFile.Close()
    postData, err := io.ReadAll(postFile)
    if err != nil {
        return Post{}, err
    }
    post := Post{Title: string(postData)[7:]}
    return post, nil
}
```

记住，我们此时的重点不是编写优雅的代码，而是达到一个拥有可用软件的阶段。

尽管这感觉像是一小步前进，它仍然需要我们编写相当多的代码，并在错误处理方面做出一些假设。这时候你应该和同事讨论，决定最佳方法。

迭代方法给了我们快速反馈，表明我们对需求的理解还不完整。

`fs.FS` 通过它的 `Open` 方法提供了一种按名称打开其中文件的方式。接着我们从文件读取数据，目前我们还不需要任何复杂的解析，只需通过切片字符串把 `Title:` 文本去掉。

## 重构

将“打开文件的代码”和“解析文件内容的代码”分离开，会让代码更易于理解和维护。

```go
func getPost(fileSystem fs.FS, f fs.DirEntry) (Post, error) {
	postFile, err := fileSystem.Open(f.Name())
	if err != nil {
		return Post{}, err
	}
	defer postFile.Close()
	return newPost(postFile)
}
```

```go
func newPost(postFile fs.File) (Post, error) {
	postData, err := io.ReadAll(postFile)
	if err != nil {
		return Post{}, err
	}
	post := Post{Title: string(postData)[7:]}
	return post, nil
}
```

当你重构出新的函数或方法时，要小心并思考参数。你正在这里进行设计，并且由于你有通过状态的测试，可以自由深入地思考什么才是合适的。想想耦合和内聚。在这种情况下，你应该问自己：

`newPost` 必须与 `fs.File` 耦合在一起吗？我们真的用到了这个类型的所有方法和数据吗？我们真正需要的是什么？

在我们的例子中，我们只是将它用作 `io.ReadAll` 的参数，而 `io.ReadAll` 需要的是 `io.Reader`。所以我们应该放宽函数中的耦合，改为要求传入 `io.Reader`。

```go
func newPost(postFile io.Reader) (Post, error) {
    postData, err := io.ReadAll(postFile)
    if err != nil {
        return Post{}, err
    }
    post := Post{Title: string(postData)[7:]}
    return post, nil
}
```

对于 `getPost` 函数，你也可以提出类似的论据：它接受一个 `fs.DirEntry` 参数，但只是调用 `Name()` 来获取文件名。我们用不着全部这些；让我们与该类型解耦，直接以字符串形式传入文件名。这是完全重构后的代码：

```go
func NewPostsFromFS(fileSystem fs.FS) ([]Post, error) {
    dir, err := fs.ReadDir(fileSystem, ".")
    if err != nil {
        return nil, err
    }
    var posts []Post
    for _, f := range dir {
        post, err := getPost(fileSystem, f.Name())
        if err != nil {
            return nil, err //todo: needs clarification, should
        }
        posts = append(posts, post)
    }
    return posts, nil
}

func getPost(fileSystem fs.FS, fileName string) (Post, error) {
    postFile, err := fileSystem.Open(fileName)
    if err != nil {
        return Post{}, err
    }
    defer postFile.Close()
    return newPost(postFile)
}

func newPost(postFile io.Reader) (Post, error) {
	postData, err := io.ReadAll(postFile)
	if err != nil {
		return Post{}, err
	}
	post := Post{Title: string(postData)[7:]}
	return post, nil
}
```

从现在开始，我们的大部分工作都可以干净地集中在 `newPost` 中。打开文件和遍历文件的事情已经完成了，现在我们可以专注于为 `Post` 类型提取数据。虽然从技术上讲不是必须的，但将相关的东西按逻辑分组，文件是一种很好的方式，所以我把 `Post` 类型和 `newPost` 移动到一个新的 `post.go` 文件中。

## 测试辅助函数

我们也应该关心一下测试。我们会经常对 Posts 做断言，所以应该编写一些代码来辅助处理。

```go
func assertPost(t *testing.T, got blogposts.Post, want blogposts.Post) {
	if !reflect.DeepEqual(got, want) {
		t.Errorf("got %+v, want %+v", got, want)
	}
}
```

`assertPost(t, posts[0], blogposts.Post{Title: "Post 1"})`

## 先写测试

让我们进一步扩展测试，以从文件中提取下一行，即描述。直到使其通过为止，现在应该感觉舒适且熟悉。

```go
func TestNewBlogPosts(t *testing.T) {
    const (
        firstBody = `Title: Post 1

Description: Description 1`
        secondBody = `Title: Post 2

Description: Description 2`
    )
    fs := fstest.MapFS{
        "hello world.md":  {Data: []byte(firstBody)},
        "hello-world2.md": {Data: []byte(secondBody)},
    }
    // rest of test code cut for brevity
    assertPost(t, posts[0], blogposts.Post{
        Title:       "Post 1",
        Description: "Description 1",
    })
}
```

## 尝试运行测试

```
./blogpost_test.go:47:58: unknown field 'Description' in struct literal of type blogposts.Post
```

## 编写最少的代码使测试运行并检查失败的测试输出

为 `Post` 添加新字段。

```go
type Post struct {
    Title         string
    Description string
}
```

测试现在应该可以编译，但会失败。

```
--- RUN   TestNewBlogPosts
    blogpost_test.go:47: got {Title:Post 1
        Description:  Description 1  Description:},  want
{Title:Post 1 Description:Description 1}
```

## 编写足够多的代码使其通过

标准库提供了一个方便的库，可帮助你逐行扫描数据；`bufio.Scanner`

`Scanner` 为读取数据（例如换行分隔的文本行文件）提供了一个便捷的接口。

```go
func newPost(postFile io.Reader) (Post, error) {
    scanner := bufio.NewScanner(postFile)
    scanner.Scan()
    titleLine := scanner.Text()
    scanner.Scan()
    descriptionLine := scanner.Text()
    return Post{Title: titleLine[7:], Description: descriptionLine
}
```

方便的是，它还接受一个 `io.Reader` 来读取（再次感谢松耦合），我们不需要更改函数参数。

调用 `Scan` 读取一行，然后使用 `Text` 提取数据。

这个函数永远不会返回错误。此时可能会想从返回类型中移除它，但我们知道以后需要处理无效的文件结构，所以还是保留它吧。

## 重构

我们在扫描一行然后读取文本时存在重复。我们知道至少还要再执行一次此操作，这是一个简单的重构以实现 DRY，所以让我们从这里开始。

```go
func newPost(postFile io.Reader) (Post, error) {
```
