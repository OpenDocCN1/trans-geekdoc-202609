
## 用 Go 编写编译器

Thorsten Ball

### 目录

- 致谢
- 引言
  - Monkey 的演进
  - 如何使用本书
- 编译器与虚拟机
  - 编译器
  - 虚拟机与真实机器
  - 我们要做什么，或者说：虚拟机与编译器的双重性
- 你好，字节码！
  - 第一批指令
  - 在栈上相加
  - 接入 REPL
- 编译表达式
  - 清理栈
  - 中缀表达式
  - 布尔值
  - 比较运算符
  - 前缀表达式
- 条件语句
  - 跳转
  - 编译条件语句
  - 执行跳转
  - 欢迎回来，Null！
- 跟踪名字
  - 计划
  - 编译绑定
  - 在虚拟机中添加全局变量
- 字符串、数组与哈希
  - 字符串
  - 数组
  - 哈希
  - 添加索引运算符
- 函数
  - 小试牛刀：一个简单函数
  - 局部绑定
  - 参数
  - 内置函数
    - 让改动更容易
    - 做出改动：计划
    - 为内置函数开辟新作用域
    - 执行内置函数
  - 闭包
    - 问题
    - 计划
    - 万物皆为闭包
    - 编译并解析自由变量
    - 运行时创建真正的闭包
  - 花点时间
- 资源
- 反馈
- 更新日志

### 引言

这或许不是最礼貌的做法，但让我们从一个谎言开始：这本书的前作*用 Go 编写解释器*的成功程度远超我的想象。是的，这是个谎言。当然，我*想象*过它的成功。畅销书排行榜上名列前茅的名字，我沐浴在赞美和钦佩之中，受邀参加各种高级活动，陌生人在街上走向我，想要拿到我的签名书——在写一本关于一种名为 Monkey 的编程语言的书时，谁会没有这样的想象呢？不过，现在严肃地说，事实是：我确实没有*预期*到这本书会像它实际那样成功。

当然，我隐隐觉得有些人可能会喜欢它。主要是因为这本书是我自己想读却找不到的书。在我徒劳的寻找中，我看到了其他人在寻找完全一样的东西：一本关于解释器的书，容易理解，不偷工减料，并且把可运行且经过测试的代码放在核心位置。我想，如果我能写出这样一本书，也许别人也会喜欢它。

但关于我的想象就说到这里，来看看实际发生的事：读者们确实喜欢我写的内容。他们不仅购买并阅读了这本书，还发邮件感谢我写了它。他们写博客文章表达他们有多喜欢它。他们在社交网络上分享并点赞。他们摆弄这些代码，调整它，扩展它，并在 GitHub 上分享。他们甚至帮助修正了书中的错误。想想看！他们给我发来修正错误的内容，同时一直为发现了错误而道歉。显然，他们无法想象我对每一条建议和修正有多感激。

然后，在阅读了一封读者想要*更多*内容的邮件后，我的内心有什么被触动了。一个原本在我脑海中只是一个想法的东西，变成了一种义务：我必须写第二部。请注意，我写的不是“另一部”，而是“第二部”。这是因为第一本书诞生于一种妥协。

当我开始写*用 Go 编写解释器*时，我并没有打算写续集，而是只想写一本书。然而，当我意识到最终这本书会太长时，这个想法就变了。我从来不想写一本会用篇幅把人们吓跑的书。即使我想，完成这本书很可能会花费太长时间，以至于我很可能早就放弃了。

这让我做出了妥协。与其写构建一个树遍历解释器并将其转变为虚拟机，我*只*写树遍历部分。这变成了*用 Go 编写解释器*，而你正在读的正是我一直想写的续集。

但这里的续集到底意味着什么？到目前你已经知道，这本书并不是以“第一本书中事件发生几十年后，在另一个星系，Monkey 这个名字已经毫无意义……”开头。不，这本书意在与其前作无缝连接。同样的方法，同样的编程语言，同样的工具，以及我们在第一本书末尾留下的代码库。

想法很简单：我们接着上次的地方继续 Monkey 的开发。这不仅是一本前书的继任者，也是 Monkey 的续集，是其演化的下一步。但在我们能看到那是什么样子之前，我们需要回顾一下，以重新唤醒对 Monkey 的记忆。

### Monkey 的演进

#### 过去与现在

在*用 Go 编写解释器*中，我们为 Monkey 编程语言构建了一个解释器。Monkey 被发明出来只有一个目的：在*用 Go 编写解释器*中从零构建，并由它的读者从零构建。它唯一的官方实现包含在*用 Go 编写解释器*中，尽管许多由读者用各种语言构建的非官方实现也流传于互联网。

如果你忘了 Monkey 长什么样，这里有一个小片段，它试图把尽可能多的 Monkey 特性塞进尽可能少的行数里：

```go
let name = "Monkey";
let age = 1;
let inspirations = ["Scheme", "Lisp", "JavaScript", "Clojure"];
let book = {
    "title": "Writing A Compiler In Go",
    "author": "Thorsten Ball",
    "prequel": "Writing An Interpreter In Go"
};

let printBookName = fn(book) {
    let title = book["title"];
    let author = book["author"];
    puts(author + " - " + title);
};

printBookName(book);
// => prints: "Thorsten Ball - Writing A Compiler In Go"

let fibonacci = fn(x) {
    if (x == 0) {
        0
    } else {
        if (x == 1) {
            return 1;
        } else {
            fibonacci(x - 1) + fibonacci(x - 2);
        }
    }
};

let map = fn(arr, f) {
    let iter = fn(arr, accumulated) {
        if (len(arr) == 0) {
            accumulated
        } else {
            iter(rest(arr), push(accumulated, f(first(arr))));
        }
    };

    iter(arr, []);
};

let numbers = [1, 1 + 1, 4 - 1, 2 * 2, 2 + 3, 12 / 2];
map(numbers, fibonacci);
// => returns: [1, 1, 2, 3, 5, 8]
```

转换成特性列表，我们可以说 Monkey 支持：

- 整数
- 布尔值
- 字符串
- 数组
- 哈希
- 前缀、中缀和索引运算符
- 条件语句
- 全局和局部绑定
- 头等函数
- return 语句
- 闭包

这个列表不小吧？而且我们把这些全部构建到了自己的 Monkey 解释器中，最重要的是——我们是从零构建的，没有使用任何第三方工具或库。

我们从构建词法分析器开始，它将输入到 REPL 中的字符串转换为令牌。词法分析器定义在 lexer 包中，它生成的令牌可以在 token 包中找到。

之后，我们构建了解析器，一个自顶向下的递归下降解析器（通常称为 Pratt 解析器），它将令牌转换为抽象语法树，简称 AST。AST 的节点定义在 ast 包中，解析器本身可以在 parser 包中找到。

在通过解析器后，Monkey 程序在内存中表示为一棵树，下一步是求值它。为此，我们构建了一个求值器。它就是定义在 evaluator 包中的一个名为 Eval 的函数。Eval 递归地向下遍历 AST 并求值，使用定义在 object 包中的对象系统来产生值。例如，它会把表示 1 + 2 的 AST 节点转换成 object.Integer{Value: 3}。这样，Monkey 代码的生命周期就完成了，结果被打印到 REPL 中。

这一系列转换——从字符串到令牌，从令牌到树，从树到 object.Object——在我们构建的 Monkey REPL 的主循环中从头到尾可见：

```go
// repl/repl.go

package repl

func Start(in io.Reader, out io.Writer) {
    scanner := bufio.NewScanner(in)
    env := object.NewEnvironment()

    for {
        fmt.Printf(PROMPT)
        scanned := scanner.Scan()
        if !scanned {
            return
        }

        line := scanner.Text()
        l := lexer.New(line)
        p := parser.New(l)

        program := p.ParseProgram()
        if len(p.Errors()) != 0 {
            printParserErrors(out, p.Errors())
            continue
        }

        evaluated := evaluator.Eval(program, env)
        if evaluated != nil {
            io.WriteString(out, evaluated.Inspect())
            io.WriteString(out, "\n")
        }
    }
}
```

这就是我们在上一本书结束时离开 Monkey 的地方。

然后，半年之后，*遗失章节：为 Monkey 编写宏系统*重新浮出水面，告诉读者如何让 Monkey 用宏来编程自己。不过，在这本书中，《遗失章节》及其宏系统将不会出现。事实上，就好像《遗失章节》从未被找到，我们又回到了*用 Go 编写解释器*的结尾。不过，这很好，因为我们在实现解释器方面做得非常出色。

