
To find these weaknesses, you must look inside the `applet` itself. To do this, you need to first find a `Java` decompiler, such as `JD-GUI`. The decompiler takes the `Java` bytecode and turns it back into code that you can browse. Using the `JD-GUI18` application, you can take apart a `Java` applet to look for weaknesses, and then determine how you would need to modify a web page to leverage those weaknesses. You may occasionally run into `Java` applet code that has a degree of obfuscation, and in those instances you may need to also spend some time de-obfuscating the code.

To demonstrate this, the following example shows how reversing a contrived `Java` applet can enable you to further compromise the underlying browser and OS. In this instance, your goal is to abuse the normal applet behavior in order to execute arbitrary OS commands.

Through analysis of the `HTML` and `JavaScript`, you determine that a number of arguments are passed directly to the applet. The applet also appears to expose an `execute()` method:

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

This sample code tells the browser to execute the `signedAppletCmdExec` class from the `signedAppletCmdExec.jar` file. It sets the `debug` argument to true, and the `dir` value to `c:/`. When the browser runs the code, the arguments are passed to `Java` and the `debug` and `dir` values are available to the applet. To finally run the applet, the following `JavaScript` is required as well:

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

The `JavaScript` code creates a function that accesses the applet and runs the `execute` method inside the applet itself. It also outputs some messages coming from the applet to the browser’s console. When this code is run, you see the output from [Figure 8-12](#c08.html#figure8-12).

 start figure 

[**Figure 8-12:**](#c08.html#figureanchor8-12) The `cmd.exe` window showing a `C:\\` prompt

![c08f012.tif](image_fi/662090c08/c08f012.png)

 end figure 

Armed with an understanding of the behavior of this code, it would appear that there might be an opportunity to execute arbitrary OS commands. To figure out exactly how to do that, you need to know how the code is being called inside `Java`. This is where you need to take apart the `Java` code and investigate how the `cmd.exe` is called.

First, you need to extract the `.class` file from the `.jar` file. Download the `.jar` file and save it to a temporary directory. To extract the content from the `.jar` file, type in the following command. Remember, a `.jar` file is simply a `.zip` file containing all the necessary `Java` class files and other associated content:

```
$ jar xvf signedAppletCmdExec.jar 
 inflated: META-INF/MANIFEST.MF
 inflated: META-INF/MYKEY.SF
 inflated: META-INF/MYKEY.DSA
  created: META-INF/
 inflated: signedAppletCmdExec.class
 inflated: RelaxedSecurityManager.class
```

You will see that two class files are extracted along with the META-INF information about how the applet is signed. The two class files contain the applet code compiled into bytecode. Next, run the `JD-GUI` application and double-click `signedAppletCmdExec.class`. Once it’s loaded, you should see something that resembles [Figure 8-13](#c08.html#figure8-13).

 start figure 

[**Figure 8-13:**](#c08.html#figureanchor8-13) `JD-GUI` showing the extracted source

![c08f013.tif](image_fi/662090c08/c08f013.png)

 end figure 

In the code snippet are two areas that are important to note. The first is that the applet is overriding the default Security Manager in order to relax permissions required to execute commands. Without giving explicit permissions to the applet, or giving all permissions like in this example, the applet would throw a security exception refusing to execute commands. Second, the `str2` variable is setting the command to be run with the `dir` argument that’s being passed into the code.

This information tells you all you need to know about executing additional operating system commands. To leverage this finding, you need to provide additional commands that will be executed by `cmd.exe`. Because the original command isn’t output to the screen, additional appended commands are transparent. To try this out, modify the initial HTML code to the following:

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

The highlighted modification causes the `cmd.exe` process, when it is executed by the `Java` applet, to change into the `c:/` directory and then start `notepad.exe`. To verify that this works, reload the attack page and you should see output similar to [Figure 8-14](#c08.html#figure8-14). The `cmd.exe` title changes to show that the user is executing `notepad.exe`. However, if the execution completed quickly, it is unlikely that the user would have noticed the short-lived change.

This would be a great opportunity to execute a Metasploit Meterpreter payload that would migrate quickly to another process. Other attacks may include adding new local users or, given appropriate permissions, even Domain Admin members if your target has elevated privileges in a Windows domain.

 start figure 

[**Figure 8-14:**](#c08.html#figureanchor8-14) The signed applet launching `cmd.exe` and `notepad.exe`

![c08f014.tif](image_fi/662090c08/c08f014.png)

 end figure 

This scenario shows a somewhat contrived example of how to leverage vulnerable `Java` applets to execute additional OS commands. However, think back to more sophisticated `Java` Applets that you may have encountered.

Whether your targets are downloaders, installers, or other applets with similar functionality, they almost always are delegated as trusted by the user. What if you modified the options of those trusted applications and sent that to a target? To leverage these techniques, you’ll have to pull out your `Java` decompiler and dig deeper.

### Bypassing the Java Sandbox

Every so often, `Java` sandbox vulnerabilities are found that allow a bypass of the sandbox and execution of malicious code outside of the sandbox19. Not every version of `Java` is vulnerable, though; part of the challenge is fingerprinting the specific version of `Java` to determine if there is a weakness. Without this information, breaking out of the sandbox will be difficult.

The fingerprinting code earlier in the chapter enables you to fingerprint the specific version of `Java` that is running. With this information, you can determine if a sandbox bypass exists for that specific version of `Java`. Because `Java` changes regularly, and therefore so do exploitation tactics, listing specific vulnerable versions within this book is pointless. A quick search on the web for the version you are dealing with is the most effective way to uncover potential bypasses.

Other aspects to consider are the previous two examples of `Java` code. Each of them enables you to leverage a signed applet to bridge `JavaScript` and a `Java` applet. This is the only way to deal with operating system manipulations in an applet without an exploit. As you may have seen, this can generate alerts, and additional social engineering or other attacks are needed to make this an effective attack.
