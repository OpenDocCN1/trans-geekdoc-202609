
-   [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1.  运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```javascript
if (condVar > someVal) {console.log("xxx")}
```
[/content]

[content]
为了实践，你可以把这段知识封装成一个 JavaScript 函数，用于识别特定版本的 Firefox。查看 Firefox 的发布说明，除了 Firefox 18 的变更外，Firefox 21 版本还增加了 `window.crypto.getRandomValues` 的额外属性。通过两次检查，你可以很容易地缩小浏览器版本的可能范围：

```javascript
function fingerprint_FF(){
    result = "Unknown";
    if(!!window.crypto.getRandomValues) {
        result = "21+";
    }else{
        if(!!window.devicePixelRatio){
            result = "18+";
        }else{
            result = "-17";
        }
    }
    alert(result);
}
```

使用这个 JavaScript，你可以通过两次检查判断浏览器是否等于或大于 21 版，等于或大于 18 版，或者小于 17 版。要进一步精确到具体版本还需要更多信息，但通过组合多个检查，可以逐步实现对浏览器版本的更细粒度识别，如你在 [Figure 6-9](#c06.html#figure6-9) 中所见。

start figure 

[**Figure 6-9:**](#c06.html#figureanchor6-9) Alert 框显示 Firefox 版本大于 21。

![c06f009.tif](image_fi/662090c06/c06f009.png)

end figure 

这些推断不过是一种基于提供的细节进行估算的过程。在几个假设性例子中，网页浏览器开发者可能会在版本 25 移除 `devicePixelRatio` 属性，甚至在 Firefox 17.9 中添加它。这些变化可能导致你的检测算法出现假阳或假阴，因此请记住这只是一种估算，而非绝对确定。

请记住，就像可以伪造 UA 头部一样，你也可以伪造 DOM 属性。假设 http://browservictim.com 是你控制的源站。现在在文档的 head 部分预置以下代码。如果第三方 JavaScript 试图通过 DOM 属性进行指纹识别，它可能会被误导：

```javascript
<script>
// with the following, the !!window.opera check returns true
var opera = {isOpera: true}
window.opera = opera;
</script>
```

当 DOM 被指纹识别时，访问 `window.opera` 会返回以下结果：

```
>window.opera
Object {isOpera: true}

>!!window.opera
true
```

如果你只依赖单一的浏览器指标来获得高确定度，你会遇到问题。上面的代码正是说明了为什么需要结合多种检测方法，以降低指纹识别结果不准确的可能性。

### 使用 DOM 属性值

仅凭 DOM 属性的存在，只能让你走一部分路径来识别浏览器。要获取更多信息，你需要查看 DOM 中变量的实际值。

不同浏览器会有不同的、固有于浏览器本身的变量值，这些值不容易被更改。这一点很重要，因为更改 User-Agent 字符串非常容易。例如，Firefox 有很多扩展程序可以轻松更改 User-Agent。这在 [Figure 6-10](#c06.html#figure6-10) 中有所展示，其中 User-Agent 已被更改为 Internet Explorer，但通过查看 DOM 变量，你仍然可以确定你在使用 Firefox。

start figure 

[**Figure 6-10:**](#c06.html#figureanchor6-10) 使用 Firebug 控制台获取浏览器信息

![c06f010.tif](image_fi/662090c06/c06f010.png)

end figure 

尽管在 [Figure 6-10](#c06.html#figure6-10) 中 User-Agent 已被更改为 Internet Explorer，但 `window.navigator` 数据实际上同时包含修改后的值和真实值。`appName` 字段包含修改后的值，而 `userAgent` 字段仍保留真实的 User-Agent。通过这种信息，你可以揭示真实的浏览器版本，以及语言和操作系统等其他重要信息。

为了更好地理解有多少人实际伪造了 User-Agent 头部，我们可以查看安装了“User-Agent Switcher for Chrome”扩展的 Chrome 用户数量。据此 writing 时统计，该扩展已安装接近半百万次。Firefox 用户安装“User Agent Switcher”扩展的情况也类似。

## 指纹识别使用软件缺陷

浏览器缺陷是进行浏览器指纹识别的最可靠方式之一。请注意，这里的“bug”并非通常意义上的缺陷，即导致安全问题的意外功能。在此语境下，bug 指的是常规的、意外的功能，不一定与安全直接相关。

缺陷可能由特定供应商在特定版本中引入，并在后续补丁或更新中修复。触发该缺陷可让你通过将其映射回修复时间，从而确定供应商和版本边界。

下面的示例缺陷详见 [https://bugs.webkit.org/show_bug.cgi?id=96694](https://bugs.webkit.org/show_bug.cgi?id=96694)。当执行以下代码时，该缺陷应返回 false：

```javascript
function testVuln(){
 return !!document.implementation.createHTMLDocument(undefined)
  .querySelector("title").textContent ;
}

alert(testVuln())
```

然而，如果返回 true，则说明该缺陷已被修复。了解这一点，你就可以判断目标浏览器是否为基于 WebKit 的浏览器，且该缺陷已修复。如果是，浏览器不可能早于 2012 年 10 月之前的版本。你可以通过在 Safari 5 中测试（结果应为 false）以及在 Safari 6.0.2 中再次测试（结果应为 true）来验证这一点。这种检查有助于你缩小浏览器的具体补丁级别。

这种方法是进行浏览器指纹识别最可靠的方式之一，因为它相对难以伪造（虽然并非完全不可能）。对你来说最困难的部分是确定哪些缺陷具有实用价值，因为这并非一蹴而就的过程。

## 指纹识别使用 Quirks（怪癖）

Quirks 与缺陷类似，是特定浏览器或浏览器版本独有的功能。这可能包括浏览器支持的元素、JavaScript 函数返回的特定值，甚至是对同一功能的实现差异。

Erwan Abgrall 等人发布了一篇聚焦浏览器怪癖的论文，表明可以通过 XSS 浏览器怪癖来识别浏览器家族，甚至确定具体版本。

浏览器怪癖是区分不同浏览器版本和操作系统的最具揭示性的方面之一。由于浏览器不断将最新功能纳入，速度往往优先于标准化。这导致不同浏览器在变量名称、参数或其他同一功能的实现上存在差异。

一个典型例子是最近浏览器中可见性功能的实现差异。存在一个 DOM 变量用于显示页面是否可见。此外，Firefox 和 IE 分别使用 `mozHidden` 和 `msHidden` 两个独立变量。通过检查这些变量，你可以区分 Firefox 和 IE：

```javascript
var browser="Unknown";
var version = "";
if ( !document.hidden){
  if(!!document.mozHidden == document.mozHidden){
    browser="Firefox";
  }else if(!!document.msHidden == document.msHidden){
    browser="IE";
  }
}
if(browser == "Firefox")
{
  if(!!('content' in document.createElement('template'))){
    version = ">=22";
  }else{
    version = "<= 21";
  }
}else if(browser == "IE")
{
  version = ">=10";
}

alert(browser + ":" + version);
```

