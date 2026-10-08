Instead of including your email address literally on the page, such as r, write a small Javascript program which uses one or more document.write() statements. For example, whenever you want to quote your email address, use the following on the page instead:

```
<script language="javascript"> document.write("robert"); document.write("@"); document.write("the-web-book.c"); document.write("om"); </script>
```

Such behaviour is enough to confuse the vast majority of the so-called automatic email address harvester programs that are continually scanning the web in search of fresh addresses.

If you want something even smarter, search online with your favourite search engine for "javascript email address obfuscation". This will lead you to a variety of web sites which allow you to enter an email address and which will then generate a complex impenetrable Javascript program just for you which, when run by a visitor's web browser, will show your email address.

# Why Upload?

You may be wondering why, if JavaScript is a client-side language that gets executed by the browser, we have to upload pages to the server before we can test them. Can you not just double-click on jstest.html from within Windows and get the browser to execute the local copy instead, and save yourself the hassle of uploading the file until it's ready for public consumption?

In theory, yes you can. You don't need to trouble your web server at all when you're developing JS pages. However, in practice, many web browsers don't like letting you do this. They regard it as a security risk, on the basis that any JS code in a local page must be malicious. Internet Explorer versions 7 and 8, for example, will pop up various warnings asking if you really want to allow this code to run. The only way to stop this is to reduce the security settings on your browser, which is not wise as it will also reduce your safety on the web in general.

Therefore, it's best to always run JavaScript code off a server. But it's important to realise that this is not because it's a requirement of the language.