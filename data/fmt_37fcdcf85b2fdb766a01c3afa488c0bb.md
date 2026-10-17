
```html
<html>
<head>
<style>
iframe{
 filter:alpha(opacity=0);
 opacity:0;
 position:absolute;
 top: 250px;
 left: 40px;
 height: 300px; 
 width: 250px;
}
img{
 position:absolute;
 top: 0px;
 left: 0px;
 height: 300px; 
 width: 250px;
}
</style>
</head>
<body>
<!-- The user sees the following image-->
<img src="http://localhost/clickjacking/yes-no_mod.jpg">

<!-- but he effectively clicks on the following framed content -->
<iframe src="http://localhost/clickjacking
/iframe_content.html"></iframe>
</body>
</html>
```

The result is shown in Figure 4-8. Note that it looks like there is no visible presence of the framed content. This undetectable content is actually the basis of many UI redressing attacks as it is actually what your target interacts with.

start figure 

**Figure 4-8:** An apparently innocuous poll page with two buttons

![c04f008.tif](img/c04f008.png)

end figure 

start figure 

**Figure 4-9:** Removing the IFrame opacity reveals the real positioning.

![c04f009.tif](img/c04f009.png)

end figure 

When the user clicks either YES or NO, what is really clicked will be the HTML form submit button loaded in the IFrame, as you can see in Figure 4-10.

start figure 

**Figure 4-10:** Clicking on the hidden IFrame submit button

![c04f010.tif](img/c04f010.png)

end figure 

This is a very simple example of how a user can be fooled into performing unwanted actions. The concept behind this attack could be used for a number of purposes, for example elevating the privileges of a normal user. The victim of such an attack could be a user that has administrator privileges. They could be already logged in to an application with functionality similar to the code snippet presented earlier.

The fact the application relies on an anti-XSRF token doesn’t impact the delivery of the Clickjacking attack. This is because the resource to be framed is loaded normally and contains a valid anti-XSRF token. Clickjacking is in fact an ideal attack method you can perform against an application that uses anti-XSRF tokens, effectively nullifying the protection offered by those tokens.

Chapter 3 discusses how to prevent loading resources in IFrames. The same caveats presented in that chapter can be applied here. A way to generally prevent UI redressing attacks (as almost every attack relies on loading a resource into an IFrame) is by using the header `X-Frame-Options: DENY`. As you will learn in the next sections, there have been cases where simple frame-busting code was not enough to prevent some attacks.

start feature 

* * *

**Clickjacking the Flash Settings Manager** Robert Hansen and Jeremiah Grossman contributed greatly to the public awareness of Clickjacking attacks. In 2008, they were able to mount a Clickjacking attack on the Flash Settings Manager.30 Using transparent (`opaque=0`) IFrames and divs, they successfully hid the Flash Settings Manager “Allow” button over those elements. The target, while apparently clicking an innocuous button, would actually be clicking on the Flash Settings widget as shown in Figure 4-11. start figure  

**Figure 4-11:** The opaque IFrames and divs cover the Flash widget text.

![c04f011.tif](img/c04f011.png) end figure  The impact of such an action is clearly visible here, resulting in the compromise of the target’s privacy. Note that the text displayed in the Flash Settings Manager isn’t visible either, leaving the target completely unaware of what is happening and where they are clicking. 

* * *

end feature 

The previous Clickjacking examples have demonstrated what is possible with CSS alone. If you need the attack to take dynamic information from the target, for instance mouse movements, you can throw JavaScript into the mix. The flexibility of JavaScript enables you to determine the exact x and y coordinates of the current mouse position. This comes in handy when mounting complex Clickjacking attacks that rely on multiple clicks to be performed.

Imagine you framed a page with a button that required a user click in order to execute your attack. In this instance, your Clickjacking aim is to ensure your target’s mouse is always on top of that button. In this way, as soon as they click anywhere, the user is effectively clicking exactly where you want. Rich Lundeen and Brendan Coles created a BeEF command module implementing this very technique.31

In this scenario you have two frames, an inner and an outer IFrame. The outer I think the target origin you want to exploit with the Clickjacking attack. The inner IFrame instead listens to `onmousemove` events, and its position gets updated according to the current mouse cursor position. In this way, the mouse cursor is always over what you want the target to click on.

The following code uses the jQuery API to dynamically update the position of `outerObj` given the current mouse coordinates:

```
$j("body").mousemove(function(e) {
  $j(outerObj).css('top', e.pageY);
  $j(outerObj).css('left', e.pageX);
});
```

The inner IFrame style uses the opacity trick to render an invisible element:

```
filter:alpha(opacity=0);
opacity:0;
```

Consider the following sample page, which is the target of the Clickjacking attack. You want the user to click the Add User button, which in this case simply creates a pop-up when the user clicks it. Note the `body`background that has been added to better illustrate the following example:

```
<html>
<head>
</head>
<body style="background-color:red">
<p> </p>
<button onclick="javascript:alert('User Added')" \ 
type="button">Add User to Admin group</button>
<p> </p>
</body>
<html>
```

If you launch the “Clickjacking” BeEF module with the preceding HTML as the inner IFrame, then all the clicks will be sent to the IFrame. The results of this can be seen in Figure 4-12 and Figure 4-13. As you can see, the IFrame is following the mouse movements, so that wherever the user clicks on the page, they will actually be clicking the Add User button.

start figure 

**Figure 4-12:** The IFrame is reliably following the mouse movements.

![c04f012.tif](img/c04f012.png)

end figure   start figure 

**Figure 4-13:** The cursor is still on top of the button.

![c04f013.tif](img/c04f013.png)

end figure 

当用户决定点击某个位置时，点击会触发框架页面中按钮的 `onClick` 事件。正如你在框架页面的源代码中所看到的，这会弹出一个提示框对话框，如图 4-14 所示。

start figure 

**Figure 4-14:** 成功的点击劫持

![c04f014.tif](img/c04f014.png)

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

**Figure 4-15:** 点击“第二”按钮会导致点击“第一”按钮。

![c04f015.tif](img/c04f015.png)

end figure 

为了演示的需要，背景图像是可见的。在真实攻击中，图像仍是 PNG 格式，但背景透明。当目标点击“第二”或“第四”按钮时，实际上是点击页面左侧的按钮。真实的鼠标位置通过新光标图像隐藏。

Krzysztof Kotowicz34 和 Mario Heiderich 扩展了这些光标劫持技术。他们的新攻击向量完全隐藏了光标，并在 `body` 元素上添加了以下样式：

```
<body style="cursor:none">
```
