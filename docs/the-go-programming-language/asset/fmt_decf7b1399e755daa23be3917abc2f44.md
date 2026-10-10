
## 5.2 递归

```
// visit appends to links each link found in n and returns the result.
func visit(links []string, n *html.Node) []string {
    if n.Type == html.ElementNode && n.Data == "a" {
        for _, a := range n.Attr {
            if a.Key == "href" {
                links = append(links, a.Val)
            }
        }
    }
    for c := n.FirstChild; c != nil; c = c.NextSibling {
        links = visit(links, c)
    }
    return links
}
```

要遍历节点 `n` 的树，`visit` 会为 `n` 的每个子节点递归调用自身，这些子节点保存在 `FirstChild` 链表中。

让我们在 Go 官网主页上运行 `findlinks`，将 `fetch`（[§1.5](#ebook_split_015.html#id-fetchingaurl)）的输出通过管道传给 `findlinks` 的输入。我们为简洁起见略微编辑了输出。

[Click here to view code image](#ch05_images.html#id123pro01_r)

```
$ go build gopl.io/ch1/fetch
$ go build gopl.io/ch5/findlinks1
$ ./fetch https://golang.org | ./findlinks1
#
/doc/
/pkg/
/help/
/blog/
http://play.golang.org/
//tour.golang.org/
https://golang.org/dl/
//blog.golang.org/
/LICENSE
/doc/tos.html
http://www.google.com/intl/en/policies/privacy/
```

请注意页面中出现的链接形式多种多样。稍后我们将看到如何相对于基础 URL `https://golang.org` 解析它们，以生成绝对 URL。

下一个程序使用对 HTML 节点树的递归来以大纲形式打印树的结构。当它遇到每个元素时，会将元素的标签压入栈，然后打印该栈。

[Click here to view code image](#ch05_images.html#id123pro02_r)

gopl.io/ch5/outline

```
func main() {
    doc, err := html.Parse(os.Stdin)
    if err != nil {
        fmt.Fprintf(os.Stderr, "outline: %v\n", err)
        os.Exit(1)
    }
    outline(nil, doc)
}

func outline(stack []string, n *html.Node) {
    if n.Type == html.ElementNode {
        stack = append(stack, n.Data) // push tag
        fmt.Println(stack)
    }
    for c := n.FirstChild; c != nil; c = c.NextSibling {
        outline(stack, c)
    }
}
```

注意一个细微点：虽然 `outline` 将元素“压入” `stack`，但没有相应的弹出操作。当 `outline` 递归调用自身时，被调用者接收到的是 `stack` 的副本。虽然被调用者可能向该切片追加元素，修改其底层数组，甚至分配新数组，但它不会修改调用者可见的初始元素，因此当函数返回时，调用者的 `stack` 与调用前完全相同。

这是 `https://golang.org` 的大纲，同样为简洁起见进行了编辑：

[Click here to view code image](#ch05_images.html#id124pro01_r)

```
$ go build gopl.io/ch5/outline
$ ./fetch https://golang.org | ./outline
[html]
[html head]
[html head meta]
[html head title]
[html head link]
[html body]
[html body div]
[html body div]
[html body div div]
[html body div div form]
[html body div div form div]
[html body div div form div a]
...
```

通过尝试 `outline` 可以看出，大多数 HTML 文档只需几层递归即可处理，但构造需要极深递归的病态网页并不难。

许多编程语言实现使用固定大小的函数调用栈；64KB 到 2MB 是典型大小。固定大小的栈限制了递归的深度，因此在递归遍历大型数据结构时必须小心避免*栈溢出*；固定大小的栈甚至可能构成安全风险。相比之下，典型的 Go 实现使用可变大小的栈，起始很小，按需增长，上限可达 GB 级别。这让我们能安全地使用递归，无需担心溢出。

**练习 5.1：** 修改 `findlinks` 程序，使用对 `visit` 的递归调用来遍历 `n.FirstChild` 链表，而不是循环。

**练习 5.2：** 编写一个函数，统计 HTML 文档树中各元素名称——`p`、`div`、`span` 等——出现的次数，填充一个映射。

**练习 5.3：** 编写一个函数，打印 HTML 文档树中所有文本节点的内容。不要深入 `<script>` 或 `<style>` 元素，因为它们的内容在网页浏览器中不可见。

**练习 5.4：** 扩展 `visit` 函数，使其从文档中提取其他类型的链接，如图片、脚本和样式表。

## 5.3 多返回值

函数可以返回多个结果。我们已经见过许多标准库函数返回两个值：期望的计算结果，以及一个指示计算是否成功的错误值或布尔值。下面的示例展示了如何编写自己的多返回值函数。

下面的程序是 `findlinks` 的一个变体，它自身发起 HTTP 请求，因此不再需要运行 `fetch`。因为 HTTP 和解析操作都可能失败，`findLinks` 声明了两个返回值：发现的链接列表和一个错误。顺便提一下，HTML 解析器通常能从错误输入中恢复并构建包含错误节点的文档，所以 `Parse` 很少失败；失败时通常是由于底层 I/O 错误。

[Click here to view code image](#ch05_images.html#id125pro01_r)

gopl.io/ch5/findlinks2

```
func main() {
    for _, url := range os.Args[1:] {
        links, err := findLinks(url)
        if err != nil {
            fmt.Fprintf(os.Stderr, "findlinks2: %v\n", err)
            continue
        }
        for _, link := range links {
            fmt.Println(link)
        }
    }
}

// findLinks performs an HTTP GET request for url, parses the
// response as HTML, and extracts and returns the links.
func findLinks(url string) ([]string, error) {
    resp, err := http.Get(url)
    if err != nil {
        return nil, err
    }
    if resp.StatusCode != http.StatusOK {
        resp.Body.Close()
        return nil, fmt.Errorf("getting %s: %s", url, resp.Status)
    }
    doc, err := html.Parse(resp.Body)
    resp.Body.Close()
    if err != nil {
        return nil, fmt.Errorf("parsing %s as HTML: %v", url, err)
    }
    return visit(nil, doc), nil
}
```

`findLinks` 中有四条 `return` 语句，每条都返回一对值。前三条 `return` 将 `http` 和 `html` 包的底层错误传递给调用者。第一种情况直接返回错误；第二、三种情况通过 `fmt.Errorf`（[§7.8](#ebook_split_067.html#id-theerrorinterface)）附加上下文信息后返回。如果 `findLinks` 成功，最后一条 `return` 语句返回链接切片，错误为 `nil`。

我们必须确保关闭 `resp.Body`，以便在出错时也能正确释放网络资源。Go 的垃圾回收器会回收未使用的内存，但不要指望它会释放未使用的操作系统资源，如打开的文件和网络连接。这些资源应显式关闭。

调用多返回值函数的结果是一个值元组。如果要使用其中的任何值，调用者必须显式地将它们赋给变量：

```
links, err := findLinks(url)
```

要忽略其中一个值，可将其赋给空标识符：

[Click here to view code image](#ch05_images.html#id126pro01_r)

```
links, _ := findLinks(url) // errors ignored
```

多返回值调用的结果本身可以从一个（多返回值的）调用函数中返回，如这个记录参数日志的函数，其行为类似 `findLinks`：

[Click here to view code image](#ch05_images.html#id126pro02_r)

```
func findLinksLog(url string) ([]string, error) {
    log.Printf("findLinks %s", url)
    return findLinks(url)
}
```
