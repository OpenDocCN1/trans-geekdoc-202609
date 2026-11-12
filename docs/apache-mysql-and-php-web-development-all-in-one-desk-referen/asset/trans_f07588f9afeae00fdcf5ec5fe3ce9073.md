

或者可以在系统属性的环境变量页面中设置CVSROOT。

如果你使用远程系统，你的CVSROOT更可能像这样：pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp。（这是我从SourceForge开源网站摘取的一个，用于一个名为Dev-C++的项目。）

或者，你可以在每个CVS命令中传递目录名。例如，要登录SourceForge，你可以这样做：

```
CVSROOT=pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp
export CVSROOT
cvs login
```

或者，你可以将所有内容合并在一行中，直接在命令行上放置CVSROOT。为此，你使用-d选项：

```
cvs -d pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp login
```

命令格式相同：单词cvs后跟单词login。中间，我包含-d选项和仓库信息。（在下一节中，我将详细介绍登录过程。）

## 登录CVS

在使用CVS之前，你需要登录到远程CVS服务器。你可以随时使用本地客户端CVS程序，但在从CVS服务器检出任何文件之前，服务器必须允许你访问。

关于CVS可能让你觉得奇怪或别扭的一件事是，要登录CVS，你需要使用login参数运行CVS命令。然后CVS命令结束，你回到shell提示符。但你仍然已登录。是的，这有点奇怪：服务器记住了你是谁，你可以在提示符下运行更多CVS命令，直到完成工作，之后可以登出。

![](img/3f967ab8a8fddc723173059f56621648_727_0.png)

如果你为本地工作使用CVS且未连接到远程CVS服务器，则无需登录。有关在本地使用CVS的更多信息，请参见本章后面的“创建CVS仓库和项目”。

只要命令格式正确，登录就很容易。login命令需要知道以下信息：

- 你是谁
- 你的密码是什么
- 你想登录的系统的域名
- 你想访问的项目

如果你使用CVS访问开源项目（例如SourceForge上的项目），开源项目网页可能会向你显示登录的CVS命令。我建议将命令从网页粘贴到命令shell中，而不是全部手动输入。CVS对语法很挑剔。

要登录CVS，你使用login命令，并相应地设置CVSROOT。下面是一个示例：

```
cvs -d me@mydomain.com:/cvsroot/myproject login
```

让我们更仔细地看一下这个示例：

- 用户名是me。
- 你正在连接的服务器是mydomain.com。
- 你正在访问的项目位于仓库/cvsroot/myproject中。
- 命令是login。

然后系统会提示你输入密码。

## 检出整个项目

你可能出于两个原因想要检出整个项目：

- 你是该项目的新手，没有任何文件。
- 你想“获取所有最新更改”，这意味着你想下载自上次下载文件以来发生更改的任何文件。

在检出项目之前，请确保你已登录到系统（如果需要）。然后你需要选择要从项目中检出的模块。（通常项目只有一个与项目同名的模块。）你可以简单输入以下行，其中project是你要检出的项目的名称：

```
cvs checkout project
```

## 定期检出更新

如果你正在与多个人一起参与项目，你不会自动获得其他人的更改。如果其他团队成员对代码进行更改并将新代码复制到仓库，你需要定期查找更改。

你可以通过移动到根目录并再次检出整个项目来查找更改，如下所示：

```
cvs -d/MyCVSStuff checkout project
```

这里的好处是CVS很智能：它知道你当前是否正在处理某些文件，并且不会覆盖那些文件。

请记住，你需要保存CVSROOT。如果没有，请像这样在命令行中包含它：

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp checkout project
```

CVS随后会运行，将所有文件下载到你的本地目录中。或者，如果你的仓库在你自己的本地系统上，你可以使用此命令：

```
cvs -d/MyCVSStuff checkout project
```

![](img/3f967ab8a8fddc723173059f56621648_729_0.png)

如果你愿意，CVS允许你使用get而不是checkout。你的命令行如下所示：

```
cvs -d/MyCVSStuff get project
```

一切都相同；你只需说get而不是checkout。

## 检出项目中的单个文件

如果你想检出项目中的单个文件，请移动到项目的根目录，然后使用文件的完整路径名检出该文件，如下所示：

```
cvs -d/MyCVSStuff checkout project/src/myfile.cpp
```

project是项目的名称，/src/myfile.cpp是项目中要检出的文件（即myfile.cpp）的路径。

## 提交你的更改（以及创建新文件）

当你完成对文件的更改后，可以使用commit命令将更改复制回仓库。此命令易于使用。确保你位于文件所在的目录中，并键入以下行，其中myfile.cpp是你要签入的文件：

```
cvs -d/MyCVSStuff commit myfile.cpp
```

这是有趣的部分：在签入文件之前，CVS会打开一个默认文本编辑器（通常是Unix计算机上的vi，Windows计算机上的记事本）。在文本编辑器内，你输入一条描述你对文件所做更改的注释。

最初，你在文本文件中看到类似这样的信息：

```
CVS: ---------------------------------------------------------
CVS: Enter Log. Lines beginning with `CVS:' are
CVS: removed automatically
CVS:
CVS: Modified Files:
CVS: myfile.cpp
CVS: ---------------------------------------------------------
```

这是一些默认文本，告诉你正在做什么；CVS不使用此文本。在末尾输入一条消息，从新的空行开始。如果你愿意，你的消息可以跨越多行。下面是一个示例：

```
CVS: ---------------------------------------------------------
CVS: Enter Log. Lines beginning with `CVS:' are
CVS: removed automatically
CVS:
CVS: Modified Files:
CVS: myfile.cpp
CVS: ---------------------------------------------------------
Fixed the bug that was bugging everybody.
Added a new class for removing really bad bugs.
Updated the time to be Y2K compliant.
```

然后保存文件并退出。CVS会等待你完成，然后为你签入文件。

如果你正在处理刚刚创建的新文件，在提交文件之前，你必须先将其添加到仓库。是的，这是一个额外步骤，但你必须执行。在键入commit命令之前，你需要键入一个add命令：

```
cvs -d/MyCVSStuff add myfile.cpp
```

之后，你可以继续执行commit命令。

## 匿名检出文件

如果你使用开源产品，并希望下载完整的源代码树但不是开发团队成员，大多数开源项目允许通过CVS进行匿名检出。这意味着你可以像往常一样检出文件，但你没有用户名，因此无法提交你所做的任何更改。这并不意味着你不能做任何更改；它只是意味着目前你的更改仅供你自己使用，并不会成为官方源代码的一部分。（但是，大多数开源项目欢迎新开发人员，这意味着你以后可以获得用户名并签入你的更改。）

要匿名检出文件，请遵循开源网站上的说明。例如，SourceForge随每个项目提供了关于如何匿名检出文件的说明。但是，这些说明假设你熟悉CVS。说明包括一条登录行，例如：

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp login
```

当SourceForge提示你输入密码时，你只需按Enter键。其他开源网站会为你提供密码说明。

但这只是让你登录。接下来，你需要检出文件然后登出。（请记住登出。）有些人使用别名co而不是checkout；co与checkout含义相同。SourceForge页面包含一条检出文件的行，但你需要知道项目名称：

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp checkout V5
```

在此示例中，项目名称是V5。我怎么知道的？SourceForge上每个项目的开发人员都会选择他们的项目名称。（官方术语是*模块*，而不是*项目*，所以如果你在SourceForge网站上看到单词*项目*，不要感到惊讶。）要找出开发人员使用的模块名称，请单击每个SourceForge项目的CVS页面上找到的“浏览CVS仓库”链接。（CVS页面可从每个项目页面顶部的CVS链接访问。）“浏览CVS仓库”链接打开一个仓库的浏览器版本，你可以在其中看到项目名称。你会在这里看到几个名称，例如以下内容：

```
Attic/
CVSROOT/
V5/
copying.txt
```

