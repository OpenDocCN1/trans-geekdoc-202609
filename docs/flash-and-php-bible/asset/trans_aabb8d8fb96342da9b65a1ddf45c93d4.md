
The last step in the method is for aligning each pollItem, attaching the pollItem to the display list, and finally adding it to the pollItems array.

```
pollItem.y = (pollItems.length * (pollItem.height + 20));
container.addChild(pollItem);
pollItems.push(pollItem);
```

At this point, the Document class is built, and is shown in its entirety here:

```
package
{
 import flash.display.MovieClip;
 import flash.events.*;
 import flash.net.URLVariables;
 import flash.net.URLRequest;
 import flash.net.URLLoader;
 import flash.text.TextField;

 public class Poll extends MovieClip
 {
 public var POLL_ID:uint = 1;
 public var phpFile:String = 
 "http://localhost/ch12/Poll/poll.php";

 public var container:MovieClip;
 public var pollItems:Array;

 public function Poll()
 {
 pollItems = new Array();
 container = new MovieClip();
 container.x = 15;
 container.y = 100;

 addChild(container);

 loadPollData();
 }

 public function loadPollData():void
 {
 var urlVariables:URLVariables = new URLVariables;
 urlVariables.a = "getpolldata";
 urlVariables.id = POLL_ID;

 var urlRequest:URLRequest = new URLRequest(phpFile);
 urlRequest.data = urlVariables;

 var urlLoader:URLLoader = new URLLoader();
 urlLoader.addEventListener(Event.COMPLETE,
     dataLoaded);
 urlLoader.load(urlRequest);
 }

 public function dataLoaded(e:Event):void
 {
     var urlLoader:URLLoader = URLLoader(e.target);
     var xml:XML = new XML(urlLoader.data);

     for each(var item in xml..element)
     {
         var type:String = item..attribute('type');
         var value:String = item..attribute('value');
         var total:uint =
             uint(xml..attribute('total'));

         if(type == "question")
         {
             this['questionTxt'].text = value;
             continue;
         }

         if(type == "answer")
         {
             var votes:uint =
                 uint(item..attribute('votes'));
         }

         var pollItem:PollItem = new PollItem();
         pollItem['percentTxt'].text =
             Math.round(votes / total * 100) + "%";
         pollItem['barMC'].width =
             (votes / total * 100) * 4;

         pollItem.y =
             (pollItems.length *
             (pollItem.height + 20));

         container.addChild(pollItem);
         pollItems.push(pollItem);
     }
 }
 }
}
```

## 构建简单文件编辑器

至此，您已经见过大量现实世界的应用程序，但仍有一个尚未讨论过。当然，那就是内容管理系统。完整的内容管理系统将是一个庞大的项目，但本节只关注应用程序的一个方面。

文件编辑器用于添加和编辑文件，是任何内容管理系统的关键部分。管理员可能在某个时刻需要进行更新。与其下载源材料，不如使用动态文件编辑器效率更高。

本节的应用程序正是如此——一个连接到 PHP 以实际保存和加载文件的动态文件编辑器。通常您可以使用 Flash 来加载文件，但 PHP 提供了加载不存储在 Web 根目录中的文件的功能。对于模板文件来说，这是一个好主意，因为它们永远不需要被访客直接访问。

文件编辑器的设计包含基本的 TextArea、提交按钮、TextField 和 ComboBox。文件编辑器的设计并无什么令人兴奋的地方；相反，应用程序的真正核心在于 ActionScript 和 PHP 代码中。

从 PHP 代码开始，可以在开发 Flash 部分的同时对其进行测试。本示例的 PHP 实际上非常简单。首先，检查是否存在有效文件，因为无论是保存还是加载，都需要一个有效文件。

```
if(!empty($_GET['file']))
{
    $file = './files/' . $_GET['file'];
    ...
}
```

确定存在有效文件后，下一步是检查 action 是否为空。如果 action 为空，代码会自动加载 action；如果 action 包含值，则使用内部 if 语句进行比较。

```
if($_GET['action'] == 'save')
{
    ...
}
else
{
    ...
}
```

本示例仅允许加载和保存文件。在更健壮的应用程序中，您很可能还希望拥有删除或移动 action。

save action 负责加载请求的文件、替换现有文本，最后重新保存文件。需要注意的是，本示例忽略了任何现实世界应用程序中至关重要的一点，即对从 Flash 发送的数据进行转义。您还可能需要添加一个访问密钥，以防止通过浏览器的 GET 请求运行任意代码。

变量 $fileContents 从 Flash 发送的 GET 数据中检索。

```
$fileContents = $_GET['fileContents'];
```

使用 fopen 加载文件，写入权限设置为覆盖。这意味着原始内容被删除，仅保存新版本。

```
$handle = fopen($file, 'w+');
```

文件加载后，会调用 fwrite()，它实际上将内容写入文件并保存文件。save action 的最后一步是关闭文件资源并释放内存。

```
fwrite($handle, $fileContents);
fclose($handle);
```

加载文件要容易得多。基本上，引用文件并使用 file_get_contents() 加载内容，该函数将整个文件作为字符串返回，如图 13.7 所示。

```
$loadedFile = file_get_contents($file);
print "fileContents=" . $loadedFile;
```

下面是完成的 PHP 文件，应保存为 fileManager.php：

```
<?php
error_reporting(0);

if(!empty($_GET['file']))
{
	$file = './files/' . $_GET['file'];

	if($_GET['action'] == 'save')
	{
		$fileContents = $_GET['fileContents'];

		$handle = fopen($file, 'w+');
		fwrite($handle, $fileContents);
		fclose($handle);
	}

	else
	{
		$loadedFile = file_get_contents($file);
		print "fileContents=" . $loadedFile;
	}
}
}
?>
```

下一步是开发 ActionScript。设计部分之前已创建，因此您可以直接进入代码编写。

第一步是定义本示例中使用的变量。

```
var phpFile:String="http://localhost/ch12/FileEditor/fileEditor.php";
var files:Array = ['sample.txt', 'anotherfile.txt',
'readme.txt' ];
var storedFileData:String;
```

## 图 13.7

从 Web 浏览器中看到的 PHP 传递的原始文件内容

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_396_0.png)

定义变量后，您可以继续编写函数。第一个函数负责填充文件列表组合框。

```
function populateFileList():void
{
... 
}
```

组合框的 addItem 方法接受一个 Object 作为参数，用于定义 label 和 data 的数据。对于本应用程序，文件名同时用作 label 和 data 值。

```
for(var i:uint=0; i < files.length; i++)
{
fileListCombo.addItem({label:files[i], data:files[i]});
}
```

单击 loadBtn 时会调用 loadFile 方法。该处理程序设置一个文件请求，其中包含 PHP 用于加载实际文件的 file 变量。

```
function loadFile(e:MouseEvent):void
{
var variables:URLVariables = new URLVariables();
variables.file = fileListCombo.selectedItem.data;

var urlRequest:URLRequest = new URLRequest(phpFile);
urlRequest.data = variables;

var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, fileLoaded);
urlLoader.load(urlRequest);
}
```

请求的文件加载完毕且 PHP 返回内容后，内容会发送到 bodyTxt TextArea，也会发送到 storedFileData 变量。该变量用于缓存未修改的结果。您可以之后单击重置按钮恢复这些结果。

```
function fileLoaded(e:Event):void
{
var urlLoader:URLLoader = URLLoader(e.target);
var variables:URLVariables = new URLVariables(urlLoader.data);

bodyTxt.text = unescape(variables.fileContents);
storedFileData = bodyTxt.text;
}
```

重置方法只是将主体内容替换为加载原始文件时存储的未修改数据。
