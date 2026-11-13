

服务浏览器会为每个参数添加一个文本字段；在此示例中共有三个。在第一个文本字段中输入字符串，从该字符串中选择一个单词作为查找词，然后将其输入到第二个 TextField 中。最后，将替换文本输入到第三个文本字段中。填写完所有三个文本字段后，可以单击 Call 按钮，并在 Results 选项卡中查看输出。

假设使用字符串 "hello world"，查找词为 "world"，替换词为 "earth"，您应看到以下结果。该单词已被替换，并且使用 upperCaseWords 方法将每个单词的首字母大写。

```
"Hello Earth"
```

既然您已彻底测试了 AMFPHP 服务，现在可以继续安装 Flash 实际使用此设置所需的必要类。该过程将在下一节中说明。

## 在 Flash 中使用 AMFPHP

与早期版本不同，ActionScript 3 已预安装所有用于远程处理和与 AMFPHP 交互的必要类。您只需加载这些类并编写 ActionScript 代码，过程相当简单。本节将引导您构建一个简单的 Flash 应用程序，以便更好地了解在 Flash 中使用 AMFPHP 的过程。

### 加载远程处理类

在 Flash 中使用 AMFPHP 的第一步是加载这些类。构建的任何 AMFPHP 项目都需要此步骤，因为它包含了远程处理系统的核心。

```
import flash.net.*;
```

加载类后，可以定义一个指向 AMFPHP 网关文件的变量。

```
var gatewayURL:String =
"http://localhost/flashservices/gateway.php";
```

下一步是创建 NetConnection 实例，并将其分配给 gateway 变量。此时，还可以设置在单击按钮时调用的方法事件。

```
var gateway:NetConnection;
getDateBtn.addEventListener(MouseEvent.CLICK, getDate);
searchBtn.addEventListener(MouseEvent.CLICK, searchAndReplace);
upperCaseWordsBtn.addEventListener(MouseEvent.CLICK, upperCaseWords);
debugTxt.wordWrap = false;
```

以下是将在下一部分中创建的按钮处理程序的骨架。这些函数中的每一个都会调用 AMFPHP 服务。

```
function getDate(e:MouseEvent):void
{
    ...
}
function searchAndReplace(e:MouseEvent):void
{
    ...
}
function upperCaseWords(e:MouseEvent):void
{
    ...
}
```

首先关注的方法是 getDate，它将不带参数调用服务器并接收当前日期的字符串。Responder 类用于处理成功和失败调用的对象响应。

```
var responder:Responder = new Responder(onResult, onFault);
```

函数的下一部分会分配 NetConnection 类的新实例。会调用 connect 方法并传入 gateway URL 变量。连接建立后，会发出一次调用，第一个参数是服务名和方法，第二个变量是对 Responder 类实例的引用。

```
gateway = new NetConnection();
gateway.connect(gatewayURL);
gateway.call("Example.getDate", responder);
```

以下是负责建立 AMFPHP 连接并调用请求服务的完整 getDate 函数。

```
function getDate(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);

    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.getDate", responder);
}
```

另外两个函数非常相似，仅传递给服务的方法名和参数不同。

searchAndReplace 函数接受三个参数。

- arg1: 要搜索的字符串
- arg2: 要查找的单词
- arg3: 替换单词

AMFPHP 设置中的服务负责运行 `searchAndReplace` 方法，但在返回字符串之前还会调用 `uppercase` 方法。

```actionscript
function searchAndReplace(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);
    
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.searchAndReplace", responder,
        "hello world",
        "world",
        "earth"
    );
}
```

最后一个函数是 `upperCaseWords`，它接受一个参数并返回一个新字符串，其中每个单词的首字母已转换为大写。函数的其余部分与前两个相同。这是 AMFPHP 能够完成 ActionScript 原生不支持之事的一个很好示例，当然，这部分就是大写转换。

```actionscript
function upperCaseWords(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);
    
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.upperCaseWords", responder, "hello
    world");
}
```

定义完负责调用服务的三个函数后，下一部分是服务返回有效响应时调用的调试和结果函数。

当收到成功消息时，会调用 `onResult` 函数。在此简单示例中，输出的原始内容将发送到舞台上的 `TextArea` 组件。也可以将代码中的 `TextArea` 部分替换为简单的 `trace()` 语句，以便更快地进行测试。

```actionscript
function onResult(responds:Object):void
{
    debugTxt.text = "Response: " + responds;
}
```

如果发生错误，将调用 `onFault` 函数，该函数包含特定错误。为更好地查看错误，会对对象内容运行 `for..in` 循环，以显示每个项目。该函数还会清除 `TextArea`，以确保旧数据不会混入，从而在调试应用程序时造成混淆。

appendText 方法是 AS3 中替代旧版 ActionScript 中 "+=" 字符串连接方式的方法。该方法速度更快，意味着代码执行更迅速。

```
function onFault(responds:Object):void
{
    debugTxt.text = "";
    debugTxt.appendText("Debug : Error\n");
    for(var i in responds)
    {
    debugTxt.appendText(" " + responds[i] + "\n");
    }
}
```

图 9.4、9.5 和 9.6 显示了 AMFPHP 中示例应用程序的示例响应。您可以基于这些示例构建更完整的应用程序，这将在下一节中完成。

第一个示例是显示示例 AMFPHP 类中 getDate 方法的响应。该示例将以字符串格式返回当前日期。

### 图 9.4

以下是第一个 AMFPHP 服务方法的示例响应。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_229_0.png)

第二个示例接受一个参数并替换文本。这全都是一个简单示例，展示了在 AMFPHP 中处理参数的过程。

### 图 9.5

以下是第二个 AMFPHP 服务方法的示例响应。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_230_0.png)

第三个也是最后一个示例是回显响应。它基本上会获取传入的字符串，并按原样返回。

### 图 9.6

以下是第三个 AMFPHP 服务方法的示例响应。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_231_0.png)

## 使用 AMFPHP 构建实际应用程序

既然您已了解 AMFPHP 服务的用法以及如何在 Flash 中实现它，现在可以继续构建实际应用程序。实际应用程序的一个好示例是基于 Flash 的专辑列表应用程序，这将在下一节中说明。

本示例使用的数据库与第 2 章中创建的数据库相同。如果您尚未完成该章节，我建议从这里开始。

### AMFPHP 服务

本示例所需的 AMFPHP 服务负责根据传入的参数查询数据库。这还需要一个安全的数据库连接系统。这意味着这些方法不会由 AMFPHP 导出或查看。

