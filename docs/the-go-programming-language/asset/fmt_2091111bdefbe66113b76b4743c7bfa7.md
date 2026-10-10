
在下面的会话中，我们使用`bzipper`将系统字典`/usr/share/dict/words`从938,848字节压缩到335,405字节——约为其原始大小的三分之一——然后使用系统`bunzip2`命令解压缩。压缩前后的SHA256哈希值相同，这让我们确信压缩器工作正常。（如果你的系统没有`sha256sum`，请使用你对[练习 4.2](#ebook_split_035.html#id-ex-sha256)的解决方案。）

[点击此处查看代码图像](#ch13_images.html#id365pro02_r)

```
$ go build gopl.io/ch13/bzipper
$ wc -c < /usr/share/dict/words
938848
$ sha256sum < /usr/share/dict/words
126a4ef38493313edc50b86f90dfdaf7c59ec6c948451eac228f2f3a8ab1a6ed -
$ ./bzipper < /usr/share/dict/words | wc -c
335405
$ ./bzipper < /usr/share/dict/words | bunzip2 | sha256sum
126a4ef38493313edc50b86f90dfdaf7c59ec6c948451eac228f2f3a8ab1a6ed -
```

我们已经演示了将C库链接到Go程序中。反之，也可以将Go程序编译为静态归档文件以便链接到C程序，或编译为共享库以便被C程序动态加载。我们这里只是浅显地介绍了`cgo`，关于内存管理、指针、回调、信号处理、字符串、`errno`、终结器，以及goroutine与操作系统线程之间的关系，还有很多内容要讲，其中许多都非常微妙。特别是正确地在Go和C之间传递指针的规则很复杂，原因类似于我们在[第 13.2 节](#ebook_split_122.html#id-unsafepointer)中讨论的，且尚未有权威规范。更多阅读请从`https://golang.org/cmd/cgo`开始。

**练习 13.3：** 使用`sync.Mutex`使`bzip2.writer`能够安全地被多个goroutine并发使用。

**练习 13.4：** 依赖C库有其缺点。请提供一个纯Go实现的`bzip.NewWriter`替代方案，使用`os/exec`包运行`/bin/bzip2`作为子进程。

## 13.5 再一次警示

我们在上一章末尾曾警告过反射接口的缺点。本章所述的`unsafe`包，该警告适用得更为强烈。

高级语言不仅将程序和程序员与各个计算机指令集的晦涩细节隔离开来，还使其免受内存中变量位置、数据类型大小、结构体布局细节以及其他大量实现细节等无关因素的依赖。正是由于这层隔离，才能编写出安全、健壮且无需修改即可在任何操作系统上运行的程序。

`unsafe`包让程序员穿透这层隔离，以使用某些关键但原本无法访问的特性，或者可能为了获得更高的性能。代价通常是牺牲可移植性和安全性，因此使用`unsafe`需自担风险。我们关于如何以及何时使用`unsafe`的建议，与我们在[第 11.5 节](#ebook_split_108.html#id-profiling)中引用的Knuth关于过早优化的评论不谋而合。大多数程序员永远不需要使用`unsafe`。尽管如此，偶尔会出现某些关键代码最适合用`unsafe`编写的情况。如果仔细研究和测量表明`unsafe`确实是最佳方法，请将其限制在尽可能小的区域内，使程序的大部分对其使用毫不知情。

暂时将最后两章放在脑后。编写一些实质性的Go程序。避免使用`reflect`和`unsafe`；只有在不得已时才回头阅读这些章节。

同时，祝你Go编程愉快。我们希望你像我们一样享受编写Go的乐趣。

# 索引

[A](#ebook_split_126.html#ix-A)  [B](#ebook_split_126.html#ix-B)  [C](#ebook_split_126.html#ix-C)  [D](#ebook_split_126.html#ix-D)  [E](#ebook_split_126.html#ix-E)  [F](#ebook_split_126.html#ix-F)  [G](#ebook_split_126.html#ix-G)  [H](#ebook_split_126.html#ix-H)  [I](#ebook_split_126.html#ix-I)  [J](#ebook_split_126.html#ix-J)  [K](#ebook_split_126.html#ix-K)  [L](#ebook_split_126.html#ix-L)  [M](#ebook_split_126.html#ix-M)  [N](#ebook_split_126.html#ix-N)  [O](#ebook_split_126.html#ix-O)  [P](#ebook_split_126.html#ix-P)  [Q](#ebook_split_126.html#ix-Q)  [R](#ebook_split_126.html#ix-R)  [S](#ebook_split_126.html#ix-S)  [T](#ebook_split_126.html#ix-T)  [U](#ebook_split_126.html#ix-U)  [V](#ebook_split_126.html#ix-V)  [W](#ebook_split_126.html#ix-W)  [X](#ebook_split_126.html#ix-X)  [Y](#ebook_split_126.html#ix-Y)  [Z](#ebook_split_126.html#ix-Z)

`、` `-=` 、等，赋值运算符 `+=`，[1.2](#ebook_split_012.html#ix72)

`-=` 、等，赋值运算符 `+=` 、 `、`，[1.2](#ebook_split_012.html#ix72)

`|`  在模板中，[4.6](#ebook_split_040.html#ix760)

`.`  在模板中，点 ，[4.6](#ebook_split_040.html#ix758)

`:=`  短变量声明，[1.2](#ebook_split_012.html#ix75)，[2.3.1](#ebook_split_022.html#ix248)，[2.7](#ebook_split_026.html#ix369)

`&`，取地址运算符，[1.8](#ebook_split_018.html#ix215)，[2.3.2](#ebook_split_022.html#ix252)，[2.3.2](#ebook_split_022.html#ix255)，[2.3.2](#ebook_split_022.html#ix259)，[4.3](#ebook_split_037.html#ix655)，[6.2](#ebook_split_054.html#ix944)，[6.5](#ebook_split_057.html#ix973)

`&^`，AND-NOT运算符，[3.1](#ebook_split_028.html#ix397)

`...` 参数，[5.6](#ebook_split_047.html#ix874)，[5.7](#ebook_split_048.html#ix884)

`...` 数组长度，[4.1](#ebook_split_035.html#ix584)

`` ` `` 反引号字符，[3.5.1](#ebook_split_032.html#ix491)

`&^`，位清除运算符，[3.1](#ebook_split_028.html#ix396)

`^`，按位取反运算符，[3.1](#ebook_split_028.html#ix394)

`|`，按位或运算符，[6.5](#ebook_split_057.html#ix968)，[6.5](#ebook_split_057.html#ix975)

`_`，空白标识符，[1.2](#ebook_split_012.html#ix88)，[2.4.1](#ebook_split_023.html#ix300)，[4.3](#ebook_split_037.html#ix660)，[5.1](#ebook_split_042.html#ix792)，[5.3](#ebook_split_044.html#ix827)，[10.5](#ebook_split_100.html#ix1470)

`//` 注释，[1.2](#ebook_split_012.html#ix66)

`//` 注释，[1.8](#ebook_split_018.html#ix222)

`==`，比较运算符，[2.5](#ebook_split_024.html#ix316)，[3.4](#ebook_split_031.html#ix461)

`--`，递减语句，[1.2](#ebook_split_012.html#ix77)，[2.4](#ebook_split_023.html#ix291)

`、` 等，赋值运算符 `+=` 、 `-=`，[1.2](#ebook_split_012.html#ix72)

`^`，异或运算符，[3.1](#ebook_split_028.html#ix395)

`&`，隐式，[6.2](#ebook_split_054.html#ix943)，[6.5](#ebook_split_057.html#ix974)

`*`，间接运算符，[1.8](#ebook_split_018.html#ix216)，[2.3.2](#ebook_split_022.html#ix253)

`<<`，左移运算符，[3.1](#ebook_split_028.html#ix399)

`!`，取反运算符，[3.4](#ebook_split_031.html#ix462)

`// Output` 注释，[11.6](#ebook_split_109.html#ix1633)

`...` 参数，[4.2.1](#ebook_split_036.html#ix636)，[5.7](#ebook_split_048.html#ix882)，[5.7](#ebook_split_048.html#ix885)，[7.1](#ebook_split_060.html#ix997)

`...` 路径，[10.7.2](#ebook_split_102.html#ix1499)，[10.7.6](#ebook_split_102.html#ix1525)

`'` 引号字符，[3.1](#ebook_split_028.html#ix422)

`%`，取余运算符，[3.1](#ebook_split_028.html#ix387)，[6.5](#ebook_split_057.html#ix969)

`>>`，右移运算符，[3.1](#ebook_split_028.html#ix400)

`&&`，短路与运算符，[3.4](#ebook_split_031.html#ix466)

`||`，短路或运算符，[3.4](#ebook_split_031.html#ix467)

`-`，一元运算符，[3.1](#ebook_split_028.html#ix392)

`、` Unicode替换字符 ，[3.5.3](#ebook_split_032.html#ix512)，[4.3](#ebook_split_037.html#ix680)

`+=` 、 `-=` 、等，赋值运算符，[1.2](#ebook_split_012.html#ix72)

`+`，字符串连接运算符，[1.2](#ebook_split_012.html#ix71)，[3.5](#ebook_split_032.html#ix479)

`+`，一元运算符，[3.1](#ebook_split_028.html#ix391)

`++`，递增语句，[1.2](#ebook_split_012.html#ix76)，[2.4](#ebook_split_023.html#ix290)，[4.3](#ebook_split_037.html#ix654)
