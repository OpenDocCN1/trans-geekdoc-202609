
The `dist_pscanner.rb` script, available from [`https://browserhacker.com`](https://browserhacker.com), provides an interactive way to conduct a distributed port scan. It asks for which browsers to distribute the scan over, the target IP address, and the TCP port range. The script then splits up the load, and queues up the commands for each of the selected browsers. Here is the command using just a single browser (inputs are highlighted):

``` 
$ ruby ./dist_pscanner.rb 
[>>>] BeEF Distributed Port Scanner] 
 [+] Retrieved RESTful API token: 
     006c1aed13b124d0c1c8fb50c98fb35d04a78d5e 
[+] Retrieved Hooked Browsers list. Online: 3 
[+] Retrieved 185 available command modules 

[+] Online Browsers: 
[1] 127.0.0.1 - C28 Macintosh 
[2] 192.168.1.101 - C28 Windows 7 
[3] 127.0.0.1 - C28 Macintosh 

[+] Provide a comma separated list of browsers to use (i.e. 1 or 1,3 or 
    1,2,3 etc): 
1 
[+] Using: 
[1] 127.0.0.1 - C28 Macintosh 

[+] Enter target IP to port scan: 
192.168.1.254 

[+] Enter target ports to scan (i.e. 1-65535 or 22-80 or 1-1024): 
70-80 

[+] Split will be as follows: 
[1] 70-80 

[+] Ready to proceed? <Enter> 

[+] Starting port scan against 192.168.1.254 from 70-80 [1] 
[+] Scan queued... 
[1] port=Scanning: 70,71,72,73,74,75,76,77,78,79,80 
[1] port=WebSocket: Port 80 is OPEN (http) 
[1] Scan Finished in 43995 ms 
[+] All Scans Finished!! 
Time Taken: 60.248801 
```

In this example, a single Chrome browser scanned an IP address’s ports from 70 to 80 in about 60 seconds. If the same is executed again using three hooked browsers, the response is slightly different:

``` 
$ ruby ./dist_pscanner.rb 
[>>>] BeEF Distributed Port Scanner] 
 [+] Retrieved RESTful API token: 
     006c1aed13b124d0c1c8fb50c98fb35d04a78d5e 
[+] Retrieved Hooked Browsers list. Online: 3 
[+] Retrieved 185 available command modules 

[+] Online Browsers: 
[1] 127.0.0.1 - C28 Macintosh 
[2] 192.168.1.101 - C28 Windows 7 
[3] 127.0.0.1 - C28 Macintosh 

[+] Provide a comma separated list of browsers to use (i.e. 1 or 1,3 or 
    1,2,3 etc): 
1,2,3 
[+] Using: 
[1] 127.0.0.1 - C28 Macintosh 
[2] 192.168.1.101 - C28 Windows 7 
[3] 127.0.0.1 - C28 Macintosh 

[+] Enter target IP to port scan: 
192.168.1.254 

[+] Enter target ports to scan (i.e. 1-65535 or 22-80 or 1-1024): 
70-80 

[+] Split will be as follows: 
[1] 70-73 
[2] 74-77 
[3] 78-80 

[+] Ready to proceed? <Enter> 

[+] Starting port scan against 192.168.1.254 from 70-73 [1] 
[+] Scan queued... 
[+] Starting port scan against 192.168.1.254 from 74-77 [2] 
[+] Scan queued... 
[+] Starting port scan against 192.168.1.254 from 78-80 [3] 
[+] Scan queued... 
[1] port=Scanning: 70,71,72,73 
[2] port=Scanning: 74,75,76,77 
[3] port=Scanning: 78,79,80 
[3] port=CORS: Port 80 is OPEN (http) 
[3] port=WebSocket: Port 80 is OPEN (http) 
[2] Scan Finished in 14800 ms 
[3] Scan Finished in 11997 ms 
[1] Scan Finished in 15998 ms 
[+] All Scans Finished!! 
Time Taken: 32.306009 
```

Splitting up the same command over three browsers brings it down to around 32 seconds, as opposed to 60 seconds. This can be further optimized by reducing the polling time of the hooked browsers, and also by using the WebSocket protocol as the main communication channel between the hooked browser and BeEF.

Although this Ruby script has been constructed with this single purpose in mind, there’s nothing preventing the BeEF RESTful API from being used to distribute any other logic within a hooked browser. Another example is to speed up the process of dumping data cross-origin with SQL injection, as discussed in Chapter 9.

# Fingerprinting Non-HTTP Services

Fingerprinting non-HTTP services is quite different from fingerprinting web applications. Examining web applications, as explored in Chapter 9, is relatively straightforward. The browser can request resources using standard HTTP requests, and from this information you extrapolate what the web application might be.

Unlike fingerprinting web interfaces, these same techniques cannot often be used directly against a non-HTTP service. These services do not expose known resources, such as images or pages, which you can identify and fingerprint cross-origin. Due to this limitation, fingerprinting non-HTTP services from a browser often ends with less reliable results. Luckily, you can use a few techniques to increase your knowledge of the target service.

The first technique is to simply rely on the results from the port scanning discussed at the beginning of the chapter. If TCP port 6667 appears to be up, you can assume that it’s an IRC service according to the default port number. If port TCP 5900 is up, you can assume it’s a VNC service. Of course, there could be different implementations of a service listening on the same port. You’ll want to narrow down the possibilities to increase the likelihood of choosing the appropriate exploit to launch at your target.

To help refine these assumptions, perhaps even to the point of differentiating between different VNC listening applications, you can analyze the timing of requests. This is the second method of fingerprinting non-HTTP services. Mark Lowe initially used the FTP scheme to demonstrate the effectiveness of this method.18 In this instance, you will use HTTP instead.

You start with analyzing the amount of time a service requires to close a TCP connection—monitoring when the status of the XMLHttpRequest object you use is equal to 4 (done).19 Detecting version differences, say between UltraVNC 1.0.9 and 1.1.9, is unrealistic because the timing difference (if any) will be too minimal. However, detecting different implementations, like identifying UltraVNC or TightVNC, is a plausible option. You can use the following code as a starting point:

``` 
var target = "172.16.37.151"; 
var port = 5900; 
var count = 1; 
var time = 0; 

function doRequest(){
if(count <= 3){
    var xhr = new XMLHttpRequest(); 
    var port = 5900; 
    xhr.open("POST", "http://" + target + ":" + 
        port + "/" + Math.random()); 
    var start = new Date().getTime(); 
    xhr.send("foo"); 
        
    xhr.onreadystatechange = function () { 
     if (xhr.readyState == 4) { 
         var end = new Date().getTime(); 
         console.log("DONE in " + (end-start) + " ms"); 
         count++; time += end-start; 
         doRequest(); 
      } 
    } 
}else{
    console.log("COMPLETED. Average: " + time/3); 
} 

doRequest(); 
``` 
This code is simply sending three XHRs to the same target port, in this case 5900. It then monitors how long it takes for the service to close the connection. Finally, the average timing for the service to close the connection is calculated. [Figure 10-10](#c10.html#figure10-10) shows the code targeting TightVNC 2.7.1, and [Figure 10-11](#c10.html#figure10-11) shows the same test on UltraVNC 1.1.9.

 start figure 

[**Figure 10-10:**](#c10.html#figureanchor10-10) Fingerprinting TightVNC 

![c10f010.tif](image_fi/662090c10/c10f010.png) 

 end figure   start figure 

[**Figure 10-11:**](#c10.html#figureanchor10-11) Fingerprinting UltraVNC 

![c10f011.tif](image_fi/662090c10/c10f011.png) 

As you can see from these two screenshots in [Figure 10-10](#c10.html#figure10-10) and [Figure 10-11](#c10.html#figure10-11), the average close timing for TightVNC is 15 milliseconds, whereas for UltraVNC it is 20. This is a very simple example, but many services out there have a much bigger timing difference.

The third fingerprinting method is by implementing Inter-protocol Communication (IPC) requests. For instance, if the browser is able to establish a bidirectional channel to a listening Telnet service it will be able to see the Telnet service’s header. These methods are discussed in more detail in the upcoming sections. In the presence of IPC-capable services, particularly those that can be communicated with in a bidirectional manner, fingerprinting can be very effective.

# Attacking Non-HTTP Services

