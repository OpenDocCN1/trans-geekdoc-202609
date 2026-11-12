

然而，@names[0] 本身是一个列表，而不是标量，因为它以 @ 字符开头。它是一个包含一个项目的列表，在 Perl 中这与仅仅是一个标量没有区别，这就是为什么两者都有效。不过，Perl 的创建者制定了你必须遵循的规则：使用 $names[0] 而不是 @names[0]。

当你试图访问数组的第一个元素时，只需使用 $names[0]。也就是说，使用 $ 字符，而不是 @ 字符，即使 Perl 允许你使用 @ 字符。（我知道在第三卷第四章开头我曾声明 $goodfood 和 @goodfood 是两个不同的变量。但这次，$ 和 @ 实际上指的是同一个变量。这只是另一条需要遵循的规则。）

你通过使用 [0] 来访问列表中的第一个元素，如 $names[0]。你通过使用 [1] 来访问列表中的第二个元素。括号内的数字称为索引。因此，第一个索引是 0。第二个索引是 1。

你也可以从列表末尾开始访问项目。$names[-1] 会给你列表中的最后一项：

```
print $names[-1];
```

这会打印出 Frank。然后 $names[-2] 会给你列表中倒数第二个项目，即 Egbert。

你也可以使用标量变量来访问元素，如下所示：

```
$index = 3;
print $names[$index];
print "\n";
```

在此示例中，我将数字 3 保存在标量变量 $index 中，并访问 @names 数组的 "$index'th" 元素，打印出其内容。此示例打印出名字 Danielle，即索引 3（但是第四个项目）。

如果你熟悉 foreach 循环（我在第三卷第四章中会讨论），你可以使用 foreach 循环遍历数组的元素，如下所示：

```
foreach (@names) {
  print $_;
  print "\n";
}
```

这会打印出列表中的每个名字。在循环内部，每个名字都会被放入默认变量中，该变量称为 $_。我所做的就是打印默认变量的内容，然后打印一个换行。很简单！

## 更改列表中的项目

更改一个项目很简单。你只需访问列表中的项目，将其放在等号左侧，然后在右侧放入新内容。假设你的列表如下所示：

```
@names = ("Amy", "Bob", "Carl", "Danielle",
"Egbert", "Frank");
```

然后你使用这一行代码：

```
$names[2] = 'Carrie';
```

你的列表现在包含 Amy、Bob、Carrie、Danielle、Egbert 和 Frank。（请记住，第一个项目的索引是 0，因此 $names[2] 指的是列表中的第三个项目，即 Carl。）

现在，假设你使用这一行：

```
print $names[2];
```

会打印出名字 Carrie。原始数据 Carl 已永久消失……至少在你执行以下操作之前会消失：

```
$names[2] = 'Carl';
```

![](img/3f967ab8a8fddc723173059f56621648_146_0.png)

Carl 现在重新回到了列表中，而 Carrie 已消失。

列表中的每个项目都是一个标量。因此，当你有以下这行代码时：

```
$names[2] = 'Carrie';
```

元素中的先前值 Carl 会被值 Carrie 替换。你不会在数组中同时拥有 Carl 和 Carrie。你不能这样做，因为该元素是一个标量，而不是列表。

## 将列表元素嵌入字符串

如果你想将列表元素放入字符串中，请像处理任何其他变量一样将其输入字符串。以下是一个示例：

```
print "Hello $names[0], how are you?\n";
```

如果你的数组 @names 包含一组字符串列表，且第一个是 Amy，你将看到以下输出：

你好 Amy，你好吗？

你也可以通过使用索引变量来增加一些复杂性：

```
$current = 3;
print "Hello $names[$current], good to see you!\n";
```

> 就像我在前面的代码中所做的那样，当你将数组中的特定元素嵌入时，请确保在索引变量名称之前包含 $ 字符。例如，如果你错误地使用 $names[current] 而不是 $names[$current]，运行程序时你会得到奇怪的行为。亲自试一下；你将始终得到数组的第一个元素，因为 Perl 编译器认为没有 $ 字符的 current 是一个字符串，并且它尝试将 current 转换为数字，但结果只是 0，因为 current 不是一个数字。

## 获取列表的切片

Perl 使获取列表的 *切片* 变得容易，切片是指仅由原列表的一部分组成的新列表。假设你的列表如下：

```
@names = ("Amy", "Bob", "Carl", "Danielle",
       "Egbert", "Frank");
```

你想获取第二个元素、第三个元素和第四个元素，并将它们保存在一个新列表中。下面是一行极其简短的代码，可以完成所有这些操作：

```
@somenames = @names[1..3];
```

两个点表示你正在获取一系列元素，从索引 1（即 *第二个* 元素）一直到包含索引 3。这意味着 @somenames 现在包含元素 Bob、Carl 和 Danielle。

> 原始数组保持不变。这意味着在运行前面的代码后，你的原始数组 @names 仍然包含 Amy、Bob、Carl、Danielle、Egbert 和 Frank。数组 @somenames 包含 Bob、Carl 和 Danielle，它们是副本。现在假设在复制切片后，你像这样更改原始数组：

```
$names[1] = 'Bridgette';
```

现在 @names 包含 Amy、Bridgette、Carl、Danielle、Egbert 和 Frank，而 @somenames 仍然包含 Bob、Carl 和 Danielle。

这个新变量是一个保存列表的数组，因此你可以使用其自身的索引来访问它，这些索引与原始数组的索引毫无关系：

```
print $somenames[0];
print "\n";
print $somenames[1];
print "\n";
print $somenames[2];
print "\n";
```

这会打印出以下内容：

```
Bob
Carl
Danielle
```

![](img/3f967ab8a8fddc723173059f56621648_148_0.png)

不同语言对于切片和范围有不同的规则。在 Perl 中，较大的数字（即 [1..3] 中的 3）会被包含在范围内。其他一些语言（Python 即是一个例子，尽管我在这本书中不讨论它）返回的切片不包括最终数字。Perl 不是这样：你得到你要求的内容。

你也可以通过用逗号分隔索引来提取列表中的特定元素并将其保存到新数组中。以下是一个示例：

```
@morenames = @names[1,2,4];
```

这会提取出 Bob、Carl 和 Egbert 名字，它们分别是索引为 1、2 和 4 的名字。还不错，是吧？

## 将切片放入单独变量中

如果你想将列表中的多个元素存储到单独的变量中，Perl 有一个方便的语法可以帮助你做到这一点。假设你的列表如下：

```
@food = ("Asparagus", "Broccoli", "Cabbage",
"Donut", "Eggplant");
```

现在你想将其中三个食物项目复制到三个单独的变量中。你可以这样做：

```
($goodfood, $badfood, $funfood) = @food[0,3,4];
```

然后如果你打印这些中的每一个，你可以看到该过程有效：

```
print "$goodfood\n";
print "$badfood\n";
print "$funfood\n";
```

请确保你理解它为什么有效。代码 @food[0,3,4] 返回一个包含三个元素的列表。等号左半部分也是一个包含三个元素的列表，Perl 将元素一个接一个地从右侧复制到左侧。

现在看看这段代码：

```
@pres = ("Washington", "Adams", "Jefferson");
($first, $second, $third) = @pres;
```

第一行创建一个列表并将其放入 @pres 数组中；没什么大不了的。第二行将存储在 @pres 中的列表的单个元素复制到左侧的列表。因此，第一个元素 Washington 最终会存入 $first 变量；第二个元素 Adams 最终会存入 $second 变量；第三个元素 Jefferson 最终会存入 $third 变量。

如果右侧列表的元素比左侧多，则只会复制必要的元素数量。请看这段稍作修改的代码：

```
@pres = ("Washington", "Adams", "Jefferson");
($tallguy, $funguy) = @pres;
```

等号右侧列表的元素比左侧多，但这没关系。在运行第二行代码后，$tallguy 包含字符串 Washington，$funguy 包含字符串 Adams。第三个字符串 Jefferson 未被使用。

在处理数组并将元素复制到其他位置时，请记住你只是复制元素。例如，当你这样做时，原始数组 @pres 保持不变：

```
($tallguy, $funguy) = @pres;
```

因此，如果 @pres 分别包含 Washington、Adams 和 Jefferson，那么在运行此代码后，$tallguy 将包含 Washington，而 $pres[0] 也仍然包含 Washington。

如果你稍后探索函数（或者如果你已经探索过），你会感兴趣地知道，当你调用一个返回列表的函数时，该列表会悬而未决，直到你将其存储在变量中。然而，你也可以使用我本节中描述的技术，仅提取列表中的某些元素并将它们存储在单独的变量中。下面的代码展示了如何做到这一点：
