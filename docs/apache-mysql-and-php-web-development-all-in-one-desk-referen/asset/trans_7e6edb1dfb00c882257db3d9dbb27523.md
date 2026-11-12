

(或者，如果你在Linux上，可以加上井号感叹号行，为文件设置可执行权限，然后直接通过输入 basicwindow.tcl 来运行文件。在Windows上，如果设置了文件关联，也可以通过输入 basicwindow.tcl 来运行文件)

你将看到一个简单的窗口打开。图 7-1 显示了Windows系统上的示例。

![](img/3f967ab8a8fddc723173059f56621648_324_0.png)

> 如果你好奇，我之所以在这一章中使用Windows进行截图，有两个原因：首先，我需要使用Microsoft Word来撰写此书，而它运行在Windows上；其次，事实是，虽然你可能在Linux机器上开发Tk程序，但大多数最终用户会在Windows上运行它们。但这没关系。请记住，Tk的优点之一是，你的Tcl/Tk程序可以在任何包含Tcl/Tk系统的操作系统上运行。

## 向窗口添加按钮

如果要在窗口上放置一个按钮，可以使用 button 命令，它是Tk库的一部分。请记住，在Tcl中，一切都以命令开始。使用Tk时，你仍然遵循此规则。看看这个程序：

```
button .mybutton -text Hello
pack .mybutton
```

将此程序保存为 simplewin.tcl，并使用以下行运行它：

```
wish simplewin.tcl
```

你会看到一个像图 7-2 所示的小窗口。

图 7-2：这个小窗口上有一个按钮。

![](img/3f967ab8a8fddc723173059f56621648_325_0.png)

如你所见，这个小窗口的代码很简单。第一行通过调用 button 命令创建一个按钮。button 命令的第一个参数（通常来说，所有小部件命令的第一个参数）是按钮的名称。

请记住，你必须以点号开头来命名小部件。从那里，你指定小部件是否包含在另一个小部件中。这个按钮不是，所以我就在点号后面跟上名称的最后部分：.mybutton。

然后我指定一个选项，在本例中是 -text。该选项是按钮上显示的文本。我选择在按钮上显示 Hello，如图 7-2 所示。

但仅仅创建一个小部件并不意味着Tk会自动将小部件放置到窗口上。要将小部件添加到窗口，需要使用 pack 命令：

```
pack .mybutton
```

pack 命令的格式很简单；你只需输入 pack 后跟小部件的名称即可。

![](img/3f967ab8a8fddc723173059f56621648_325_1.png)

pack 这个词作为添加小部件到窗口的命令，可能看起来是个奇怪的选择。但实际上，pack 指的是小部件在窗口中定位的方式。pack 命令是一个组织小部件的几何管理器。Tk提供三种不同的几何管理器，分别称为 pack、grid 和 place。pack 命令是一种特殊的命令，它会将控件尽可能紧密地挤在一起。你也可以在 pack 命令中包含一些选项；这些选项在本章的许多示例中都有出现。如果想了解更多关于几何管理器的信息，请参见第四卷第8章。

前面的程序虽然很酷，但我必须承认它没什么用。如果你点击按钮，什么也不会发生。一个好的按钮应该是撸起袖子实际做点事情，而不是整天坐在沙发上吃薯片。

请记住，`button` 是一个命令，和Tcl中的大多数命令一样，你可以提供选项。`button` 命令包含一个名为 `-command` 的选项。如果你输入这个选项，后面跟一组花括号，其中可以包含用户单击按钮时运行的代码。

这是一个你可以尝试的新程序：

```
button .mybutton -text Hello -command {
    tk_messageBox -icon info -message \
    "Hello, thank you for stopping by!"
}
pack .mybutton
```

我将其保存为 `buttoncmd.tcl`。使用 `wish buttoncmd.tcl` 运行时，你会看到一个带按钮的窗口，就像图 7-2 所示程序中的那个一样。但这次，当你点击按钮时，它实际上会执行某些操作：`-command` 选项内部的代码会运行。

该代码会调用名为 `tk_messageBox` 的命令，该命令显示一个消息框。消息框显示的消息是 `Hello, thank you for stopping by!` 尝试点击按钮，亲自看看吧。

## 创建列表框（关于 Pack 和 Bind 命令的更多内容）

你以前见过列表框，我相信你会同意它们非常有用。这里有一个快速的小程序，它在窗口上放置一个列表框：

```
wm title . "Simple Listbox"
listbox .lb -width 10 -height 10
pack .lb
```

这将创建一个名为 `.lb` 的列表框。注意 `listbox` 命令后面有一些选项，即 `width` 和 `height`。这些单位是字符，*不是*像素。也就是说，此程序中定义的列表框大约可以横向显示十个字符，并且可以容纳十行文本。我说 *大约*，是因为当今所有主要操作系统都使用比例间距字体，这意味着你不一定能看到恰好十个字符适合分配的空间。

如果你运行前面的示例，你不会看到什么。如果列表框中出现几个项目会很好，如果你可以双击这些项目也会更好。这里有一个更复杂的示例，它可以做到所有这些，甚至更多：

```
wm title . "Listbox Demo 2"
pack propagate . off

frame .buttonbar
pack .buttonbar -side top

button .buttonbar.bt1 -text "Add" -command {
.lb insert end grapes kiwi
}
button .buttonbar.bt2 -text "Del" -command {
.lb delete 1 3
}

pack .buttonbar.bt1 .buttonbar.bt2 \
    -side left -padx 5 -pady 5

listbox .lb -width 250 -height 250
pack .lb -side bottom

.lb insert end apple banana orange

# Create a handler to catch double-clicks from the listbox
# Note: This is a digit 1 after the word Double!
bind .lb <Double-1> {
    tk_messageBox -icon info -message [selection get]
}
```

在这个程序中，你首先会注意到我包含了不止一个按钮。但这些按钮都在一个 frame 中。frame 只不过是其他小部件的容器。pack 命令要求你为某些复杂布局使用大量的 -side 参数，我发现，如果我想在窗口顶部排成一排放置按钮，最简单的方法是在顶部放置一个 frame，然后用按钮填充它。因此，在这个示例程序中，我创建了一个 frame，然后创建了一些按钮。注意我是如何命名按钮的，即以 frame 开头，例如 .buttonbar.bt1。

还要注意，我在 pack 命令中包含了两个额外参数，-padx 和 -pady。它们只是指定在我的打包按钮周围包含一些空白空间。你可能也注意到，我可以在单个 pack 命令中包含两个按钮；这算不上什么大事。

第一个按钮的命令将项目插入列表框。注意我的做法：我将列表框的名称视为一个命令，然后跟上一个子命令。第一个按钮中的子命令是 insert，第二个按钮中的子命令是 delete。insert 命令接受一个索引，可以是数字或单词 end，然后是几个我想放入列表框的字符串（在此例中，是字符串 grapes 和 kiwi）。delete 命令接受两个索引，代表我想删除的范围的起始和结束。在此例中，我删除索引为 1、2 和 3 的项目。（列表框中的第一个项目索引为 0。）

但你可能会注意到一件奇怪的事：如果你从上到下阅读程序，会发现我在创建 .lb 控件的代码之前就已经将 .lb 用作命令了。但这没关系，因为我使用 .lb 作为命令的位置（在按钮命令中）是在创建 .lb 控件之后运行的；.lb 控件在程序启动时创建，而按钮命令仅在程序用户单击按钮时运行。

在按钮之后，我创建列表框。注意跟在这个 listbox 命令后面的 pack 命令，并将其与之前的 pack 命令（即跟在 frame 语句后面的那个）进行比较。frame 语句对应的 pack 命令包含选项 -side top。listbox 语句对应的 pack 命令包含选项 -side bottom。pack 命令相对于窗口的一个边来定位控件。因此，第一个 pack 命令将 frame 放置在窗口顶部，第二个 pack 命令将列表框放置在窗口底部。（但是，在窗口中定位项目比看起来要复杂一些，因此请务必阅读第四卷第8章，其中更详细地解释了这一点。）

程序的最后一部分可能是最有趣的。如果你想编写响应鼠标单击等操作的代码，可以使用 bind 命令。虽然一些小部件（如带有 -command 选项的 button）内置了鼠标功能，但其他小部件则需要你将函数绑定到小部件上。列表框就是后一种类型小部件的示例。

虽然这个概念看起来可能很奇怪，但在实践中这非常简单：你只需选择小部件和要响应的事件类型；在此例中，我希望它响应左键双击。Tk为每种事件类型命名，左键双击的名称是 Double-1。（是的，那是数字 1。）那么，你可以看到命令的格式；它类似于 proc 命令，以单词 bind 开头。然后是你绑定的小部件名称（在此例中是列表框）以及尖括号内的事件名称。最后，有一组花括号，包含要运行的命令。

如需了解可用事件的详细解释，请查看 www.scriptics.com/man/tcl8.4/TkCmd/bind.htm。或者，要看简短版本，请继续阅读。

