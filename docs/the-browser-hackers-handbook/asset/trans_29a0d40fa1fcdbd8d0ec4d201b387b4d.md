
为了找到这些弱点，你必须检查 `applet` 本身。为此，你首先需要找到一个 `Java` 反编译工具，例如 `JD-GUI`。反编译工具会将 `Java` 字节码转换回可浏览的代码。使用 `JD-GUI18` 应用，你可以拆解 `Java` Applet 以查找弱点，然后确定如何修改网页以利用这些弱点。你可能会偶尔遇到带有一定混淆的 `Java` Applet 代码，在这种情况下可能需要花费一些时间对代码进行去混淆。

为了演示这一点，下面的示例展示了如何通过反向工程一个伪造的 `Java` Applet，从而进一步威胁底层浏览器和操作系统。在此情形下，你的目标是利用正常的 Applet 行为来执行任意操作系统命令。

通过分析 `HTML` 和 `JavaScript`，你发现有多个参数直接传递给 Applet。Applet 还似乎暴露了一个 `execute()` 方法：

```
<object id='signedAppletCmdExec' 
  classid='clsid:8AD9C840-044E-11D1-B3E9-00805F499D93' 
  name='signedAppletCmdExec'>
  <param name='code' value='signedAppletCmdExec.class' />
  <param name='codebase' value='null' />
  <param name='archive' 
  value='http://browserhacker.com/signedAppletCmdExec.jar' />
  <param name='debug' value='true' />
  <param name='dir' value='c:/' />
</object>
```

这段示例代码指示浏览器执行 `signedAppletCmdExec` 类，并从 `signedAppletCmdExec.jar` 文件中加载。它将 `debug` 参数设为 `true`，`dir` 设为 `c:/`。当浏览器运行代码时，参数会传递给 `Java`，`debug` 与 `dir` 的值在 Applet 中可用。要最终运行 Applet，还需要下面的 `JavaScript` 代码：

```
<script>
try {
    output = document.signedAppletCmdExec.execute();
    console.log("output: " + output);
    return;
}catch (e) {
    console.log("timeout");
      return;
}
</script>
```

这段 `JavaScript` 代码创建了一个函数，用于访问 Applet 并调用 Applet 内部的 `execute` 方法。它还会把 Applet 输出的信息打印到浏览器控制台。运行此代码后，你会在 [Figure 8-12](#c08.html#figure8-12) 中看到输出。

 start figure 

[**Figure 8-12:**](#c08.html#figureanchor8-12) `cmd.exe` 窗口显示 `C:\\` 提示符

![c08f012.tif](image_fi/662090c08/c08f012.png)

 end figure 

掌握了这段代码的行为后，似乎可以利用脆弱的 `Java` Applet 执行任意操作系统命令。为了确定具体方法，你需要了解代码在 `Java` 内部是如何被调用的。这正是需要拆解 `Java` 代码、调查 `cmd.exe` 是如何被调用的地方。

首先，你需要从 `.jar` 文件中提取 `.class` 文件。下载 `.jar` 文件并保存到临时目录。要从 `.jar` 文件中提取内容，输入以下命令。记住，`.jar` 文件本质上是包含所有必要的 `Java` 类文件和相关内容的 `.zip` 文件：

```
$ jar xvf signedAppletCmdExec.jar 
 inflated: META-INF/MANIFEST.MF
 inflated: META-INF/MYKEY.SF
 inflated: META-INF/MYKEY.DSA
  created: META-INF/
 inflated: signedAppletCmdExec.class
 inflated: RelaxedSecurityManager.class
```

你会看到除了 META-INF 相关的签名信息外，还提取出了两个类文件，它们包含已编译的 Applet 代码字节码。接下来，启动 `JD-GUI` 应用并双击 `signedAppletCmdExec.class`。加载后，你应该看到类似 [Figure 8-13](#c08.html#figure8-13) 的内容。

 start figure 

[**Figure 8-13:**](#c08.html#figureanchor8-13) `JD-GUI` 显示提取的源码

![c08f013.tif](image_fi/662090c08/c08f013.png)

 end figure 

代码片段中有两个重要之处。第一，Applet 正在覆盖默认的安全管理器，以降低执行命令所需的权限。如果不显式授予 Applet 权限，或像本例那样授予全部权限，Applet 会抛出安全异常并拒绝执行命令。第二，`str2` 变量用于设置要执行的命令，并结合传入的 `dir` 参数。

这些信息告诉你，如何执行额外的操作系统命令。要利用这一发现，你需要提供额外的命令，让 `cmd.exe` 执行它们。由于原始命令不会直接显示在屏幕上，追加的命令是透明的。为了验证，可以将初始 HTML 代码修改为：

```
<object id='signedAppletCmdExec'
  classid='clsid:8AD9C840-044E-11D1-B3E9-00805F499D93'
  name='signedAppletCmdExec'>
  <param name='code' value='signedAppletCmdExec.class' />
  <param name='codebase' value='null' />
  <param name='archive'
  value='http://browserhacker.com/signedAppletCmdExec.jar' />
  <param name='debug' value='true' />
<param name='dir' value='c:/ && notepad.exe' />
<object id=’signedAppletCmdExec’>
```

高亮的修改导致 `cmd.exe` 在 `Java` Applet 执行时切换到 `c:/` 目录，然后启动 `notepad.exe`。重新加载攻击页面后，你应该看到类似 [Figure 8-14](#c08.html#figure8-14) 的输出。`cmd.exe` 标题会改变，显示正在执行 `notepad.exe`。但如果执行速度很快，用户可能根本注意不到短暂的变化。

这为执行 Metasploit Meterpreter 负载提供了很好的机会，能够快速迁移到其他进程。其他攻击手段包括添加本地用户，或在拥有适当权限的情况下，甚至提升到域管理员（如果目标在 Windows 域中拥有提升权限）。

 start figure 

[**Figure 8-14:**](#c08.html#figureanchor8-14) 受信任 Applet 启动 `cmd.exe` 并 `notepad.exe`

![c08f014.tif](image_fi/662090c08/c08f014.png)

 end figure 

这一情形展示了如何通过脆弱的 `Java` Applet 来利用操作系统命令执行。然而，思考更高级的 `Java` Applet 时，情况会不同。

无论目标是下载器、安装程序，还是其他具有类似功能的 Applet，它们几乎总是被用户视为受信任的。如果你修改这些受信任应用的选项并将其发送给目标，如何利用这些技术？要做到这一点，你需要拿出 `Java` 反编译工具，进一步深入挖掘。

### 绕过 Java 沙箱

偶尔会发现 `Java` 沙箱漏洞，使得可以绕过沙箱执行恶意代码19。不过并非每个 `Java` 版本都易受影响；挑战之一是指纹识别具体的 `Java` 版本，以判断是否存在此类漏洞。没有这方面的信息，绕过沙箱将会很困难。

本章早前的指纹识别代码可以帮助你确定运行的 `Java` 版本。有了这份信息，你就能判断该版本是否存在沙箱绕过的漏洞。由于 `Java` 定期更新，导致利用手段也在变化，书中列出具体易受影响的版本没有意义。快速在网络上搜索你所使用的版本，是发现潜在绕过方法的最有效途径。

还需考虑前面两个 `Java` 代码示例。每个示例都让你能够利用已签名的 Applet 将 `JavaScript` 与 `Java` Applet 关联，这是在不使用漏洞的情况下进行操作系统操作的唯一途径。正如你所见，这可能会触发警报，还需要配合社交工程或其他攻击手段才能使其成为有效的攻击。

