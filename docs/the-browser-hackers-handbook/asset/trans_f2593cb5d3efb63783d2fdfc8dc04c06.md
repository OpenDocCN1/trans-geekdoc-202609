
你可能会注意到一些相似之处，特别是`Accept`和`Accept-Language`头部的位置，它们在`User-Agent`头部之前。`Host`头部仍然是倒数第二个项目。但是，`Accept-Encoding`头部已经移动了。`User-Agent`也在提供一些更新的信息。你可以看到布局引擎被列为`Trident/4.0`，新特性如`Media Center PC`和`SLCC2`也被列为可用特性。你还可以看到`Accept`字段列出的内容与IE 6不同。

如果`User-Agent`字段被伪造，了解这些差异将帮助你推断出该浏览器仍然是IE的一个变体。由于`Accept-Encoding`头部在`User-Agent`头部之后，你也知道这个IE版本高于6。你能结合的信息越多，就越能精确定位浏览器的具体版本。

你可能也注意到，`User-Agent`字符串似乎包含了底层操作系统的描述符，例如`Windows NT 6.1`。虽然确定浏览器下方的桌面操作系统相对简单，因为操作系统组合的数量有限，但当涉及移动设备时，这种复杂性会大幅增加。

`MobileESP`项目由Anthony Hand开发，旨在提供一个轻量级的移动设备检测API。`MobileESP`支持多种语言，包括ASP.NET、Ruby、Python和PHP，因此被认为相当可移植。项目还提供一个开源JavaScript库，用于在客户端有限度地检测移动设备。`mdetect.js`库通过包含来自约75种不同移动设备的User-Agent字符串列表来工作。库然后暴露了一系列JavaScript函数，可用于设备判断；例如，以下代码演示了如何检测iPhone：

```
var deviceIphone = "iphone";
var deviceIpod = "ipod";
var deviceIpad = "ipad";

function DetectIphone()
{
  if (uagent.search(deviceIphone) > -1)
  {
    if (DetectIpad() || DetectIpod())
      return false;
    else
      return true;
  }
  else
    return false;
}
```

除了检测iPhone外，该库还提供检测Symbian设备、Google TV、Motorola Xoom设备、各种BlackBerry设备、Palm的WebOS、游戏主机等的函数。你可以从[https://code.google.com/p/mobileesp/](https://code.google.com/p/mobileesp/)查看`mdetect.js`的最新版本。

### 使用DOM属性进行指纹识别

要准确定义目标浏览器的真实版本，你必须比较不同浏览器版本之间可用的特征和其他信息。DOM是进行这类调查最易访问的领域之一。

DOM不仅存储显示在屏幕上的文档信息，还包含如分辨率、导航功能等其他信息，帮助开发者更轻松地与浏览器交互。随着新特性的实现，它使你能够映射浏览器类型，并进一步缩小所使用浏览器的版本范围。

#### 使用DOM属性存在性检查

检查特定DOM属性的存在可以帮助你确定浏览器的精确版本。如果你访问[http://webbrowsercompatibility.com/dom/desktop/](http://webbrowsercompatibility.com/dom/desktop/)，可以看到不同浏览器的DOM属性差异。该网站对DOM特性与浏览器版本进行映射，方便开发者判断函数是否在多种浏览器中可用。在本节中，你将研究类似的属性，但目标是判断某些函数是否存在而其他函数不存在。通过比较某些函数存在而其他不存在的情况，你可以缩小浏览器版本的范围。

在查询DOM属性时，你可能会收到以下四种响应之一：

*   未定义，因为属性不存在

*   为null或NaN，因为未设置

*   未知，用于已废弃的属性或需要ActiveX（仅限Internet Explorer）的属性

*   属性的实际值

你需要检查返回的值，但希望每个检查都返回true或false。为此，你可以使用类似`!window.devicePixelRatio`的语句来判断属性是否存在。如果属性存在，该表达式返回false；如果不存在，返回true。这是一种反直觉的检查方式，因此为了获得更直观的答案，使用双重否定，如`!!window.devicePixelRatio`。双重否定会返回true表示属性存在，false表示不存在。这使得在构建查询时更加清晰，并确保每个查询的结果只有true或false。

让我们来看看实际应用。

Firefox 18.0的发布中，Mozilla将`devicePixelRatio`作为新DOM属性加入。7 你不必感到惊讶，该属性与显示网页内容有关。为什么你需要关注它？因为在指纹识别中，你不关心它的功能，只关心该属性在Firefox 17.0中不存在，而在下一个主版本Firefox 18.0中存在（如[Figure 6-5](#c06.html#figure6-5)所示的发布说明）。

 start figure 

[**Figure 6-5:**](#c06.html#figureanchor6-5) Firefox发布说明显示该属性的添加。

![c06f005.eps](image_fi/662090c06/c06f005.png)

 end figure 

现在你已经掌握了这些知识，让我们来应用它进行指纹识别。从Mozilla发布服务器[https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)下载Firefox 17和18版本。安装这两个全新版本的Firefox后，在两个版本上安装Firebug扩展。你可以从[http://getfirebug.com/](http://getfirebug.com/)获取Firebug。Firebug将让你查看DOM元素并查询元素。

打开Firebug，进入Console标签页，确保勾选“Show Command Editor”选项，如[Figure 6-6](#c06.html#figure6-6)所示。你应该在屏幕右下角看到一个新的文本块，底部附带四个按钮：Run、Clear、Copy和History。

 start figure 

[**Figure 6-6:**](#c06.html#figureanchor6-6) 启用Firebug命令编辑器面板

![c06f006.eps](image_fi/662090c06/c06f006.png)

 end figure 

在两个Firefox版本的Firebug控制台中分别执行`!!window.devicePixelRatio`。你会看到相反的布尔值返回。在Firefox 17上执行该语句会返回false布尔值，如[Figure 6-7](#c06.html#figure6-7)所示。

 start figure 

[**Figure 6-7:**](#c06.html#figureanchor6-7) 查看Firefox 17中的devicePixelRatio检查

![c06f007.tif](image_fi/662090c06/c06f007.png)

 end figure 

在Firefox 18上执行该语句会返回true布尔值，如[Figure 6-8](#c06.html#figure6-8)所示。

 start figure 

[**Figure 6-8:**](#c06.html#figureanchor6-8) 查看Firefox 18中的devicePixelRatio检查

![c06f008.tif](image_fi/662090c06/c06f008.png)

 end figure 

需要注意的是，这并非针对Firefox 18的测试。该测试会告诉你：如果浏览器是Firefox（它可能不是），那么版本号大于或等于18（如果返回true）；或者版本号小于18（如果返回false）。

