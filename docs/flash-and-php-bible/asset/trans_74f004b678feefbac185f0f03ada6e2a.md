

## 返回数据

可以安全地假设，在您的应用程序中，您会在某个时刻希望将数据返回到 Flash。此过程中的总体安全问题与发送数据类似，不同之处在于返回数据时会尝试更多漏洞利用。

### 安全地返回数据

安全地将数据传回 Flash 的想法是一个讨论较少的话题。这主要是因为 Flash 不需要安全；不过，确保其安全仍然是良好的做法。

如果您未能验证返回到 Flash 的数据，可能会打开一个安全漏洞，例如，允许用户访问应用程序的私有部分。更糟糕的是，这可能对用户体验产生负面影响，您的用户可能会失去对您的应用程序的信心。

返回到 Flash 的数据可以像发出的数据一样被篡改。在前面的示例中，返回了一串数据，但从未检查以确保数据有效。让我们在前面的示例基础上扩展以添加这额外的安全性。响应函数是唯一需要修改的代码部分，因为请求将保持不变。

```actionscript
function response(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var param:URLVariables = URLVariables(loader.data);

    var username:String;
    var userLevel:uint;
    var userStyle:String;
    var validData:Boolean = true;

    if(param.username != "")
    {
        username = param.username;
    }
    else
    {
        validData = false;
    }

    if(param.userlevel != "")
    {
        userLevel = param.userlevel;
    }
    else
    {
        validData = false;
    }

    if(param.userstyle != "")
    {
        userStyle = param.userstyle;
    }
    else
    {
        validData = false;
    }

    if(!validData)
    {
        trace("User data was not properly loaded");
    }
    else
    {
        trace("User Information Loaded");
        trace("\tUser: " + param.username);
        trace("\tLevel: " + param.userlevel);
        trace("\tStyle: " + param.userstyle);
    }
}
```

基本上，此代码首先初始化变量以存储用户数据，然后检查每个传入的值是否为有效条目。验证变量从一开始就被赋值为 true，因为如果任何 if 语句失败，它将更改为 false。此过程被视为逆向逻辑，但对验证例程效果相当好。

### 使用更安全的方法返回数据

在前面的示例中，您学习了如何安全地处理返回的数据。这种简化方法的问题在于，存在其他方式来拦截 Flash 和服务器之间传递的信息。

### 使用唯一响应

创建更安全应用程序有几种选择，所有这些都取决于开发时间和成本。忽略成本以追求终极安全是一种常见的想法，但这并非始终可能。通常，您会参与一个达到“足够好”阶段并带有问题的项目发布；这是应用程序开发的一个缺点，但非常常见。

保持成本现实的最佳方法是查看所有选项。一种选择是使用 md5 创建唯一的响应代码并确保数据有效，这有效，但无法阻止“黑客”反编译您的 SWF 并直接查看代码。

### 保护您的文件

在 ActionScript 的早期版本中，您可以创建混淆的 SWF，这意味着大多数应用程序无法反编译它们。但是，在撰写本文时，AS3 应用程序不存在这样的工具。

## 了解 Flash 安全沙箱

Flash 中的沙箱取决于 SWF 文件的位置来确定可以访问哪些文件。SWF 文件在用户本地计算机上运行时与在服务器上运行时的功能不同。

例如，本地沙箱中的 SWF 无法同时访问本地和远程对象。这对应用程序实施了一定程度的安全性，以确保源不能相互穿越。

本地文件可以放置在三个沙箱之一中：

- local-with-filesystem: 这确保本地内容不会意外发送到网络或共享。
- local-with-networking-sandbox: 允许本地 SWF 访问远程对象，前提是找到有效的策略文件。
- local-trusted: 此沙箱中的 SWF 可以访问任何地方的数据，包括本地和远程。只有用户和管理员才能将 SWF 移动到此沙箱。

local-trusted 沙箱不能意外由独立的 SWF 设置。这样做是为了确保用户期望的安全级别。

为了允许访问远程域，您必须首先通过调用 allowDomain() 将其添加到 Security 类中。

```
Security.allowDomain("www.example.org");
```

您还可以使用跨域策略文件，允许来自特定域或使用通配符 ("*") 的所有域的访问。

```
<allow-access-from-domain="*" />
```

### 设置沙箱类型

发布 SWF 时，您可以根据使用所需的资源选择指定的沙箱类型。要设置沙箱类型，请执行以下步骤：

- 1. 选择“文件” > “发布设置”。
- 2. 单击“Flash”选项卡。
- 3. 在下拉列表中，单击“播放安全”。
- 4. 单击“确定”。

### 使用 sandboxType 属性

SWF 文件可以使用只读静态 Security.sandboxType 属性来确定 Flash 播放器已将当前 SWF 分配到哪个沙箱。

在某些情况下，您会在编程中使用 sandboxType 属性的当前值来确定应用程序应该如何交互。使用简单的 switch 语句，您可以构建一个自定义函数来跟踪当前的沙箱类型，如图 7.4 所示。

图 7.4

输出窗口显示来自 whichSandbox 函数的示例结果

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_167_0.png)

```actionscript
function whichSandbox():String
{
    var str:String = "";
    switch(Security.sandboxType)
    {
        case Security.REMOTE:
            str = "This SWF is from an Internet URL. "
            + "It cannot access local files";
            break;
        case Security.LOCAL_WITH_FILE:
            str = "This SWF is local, but not trusted by "
            + "the user. It does not have access to "
            + "remote files.";
            break;
        case Security.LOCAL_WITH_NETWORK:
            str = "This SWF can communicate with remote "
            + "files, but can with local files.";
            break;
        case Security.LOCAL_TRUSTED:
            str = "This SWF has been trusted by the user. "
            + "It can read both local and remote files.";
            break;
    }

    return str;
}

trace("Checking for current sandbox type.");
trace(whichSandbox());
```

## 确定活动沙箱

确定当前沙箱类型不仅限于简单的 trace 响应。您可以向用户显示警告屏幕，通知他或她当前 SWF 无法访问远程资源，因为它正在本地运行。如果发现本地沙箱，您还可以强制停止电影运行，这意味着电影不再从您的网站运行。例如，本地运行的电影可能已从您的网站被盗，因此检查此情况并相应采取措施是个好主意。

### 在本地沙箱中运行应用程序

如图 7.5 所示的示例检查沙箱类型，如果电影正在本地运行，则显示倒计时。

图 7.5

显示活动倒计时的已完成应用程序示例

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_168_0.png)

要开始，请打开本书网站上可找到的入门文件。

此示例的资源已完成，因此您可以专注于编程。第一步是创建所需的变量。

```actionscript
var timer:Timer;
var sandbox:String;
var startingTime:uint = 5;
```

分配变量后，您可以构建初始函数 init，该函数在电影开始时立即调用。

```actionscript
function init():void
{
    timerMC.alpha = 0;
    sandbox = Security.sandboxType;

    if(sandbox.indexOf('local') == -1)
    {
        startTimer();
    }
}
```

此函数的主要部分是 if 语句，它检查沙箱类型中是否存在字符串 "local"。这涵盖了任何本地版本，并确定电影不在远程沙箱上运行。如果检测到本地沙箱，将调用 startTimer，该函数初始化并启动倒计时计时器。

```actionscript
if (sandbox.indexOf('local') != -1)
{
    startTimer();
}
```

startTimer 函数首先初始化一个新的计时器实例，然后添加一个每毫秒调用一次的事件监听器。此函数的最后操作是通过将 alpha 属性设置为 1.0 来显示计时器文本，这使其完全可见。

注意：长时间使用 1 毫秒的计时器更新可能会导致电影无响应。对于即时检查（如本示例），这不是什么大问题。

```actionscript
function startTimer():void
{
    startingTime *= 1000;
```

