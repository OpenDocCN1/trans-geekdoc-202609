Let's make sure it worked. Quit PSPad and open your web browser. Surf to your site and page. In this case it's www.the-web-book.com/jtest.html, which brings up the following:

![](bbox=[0.123, 0.19, 0.627, 0.347])

So far so good. But that's plain HTML rather than JavaScript, and nothing we haven't seen before. So let's remedy that.

Fire up PSPad again. Connect to the server by clicking the FTP tab, and then the first icon in the row beneath it. Go into your public_html folder then double-click your jtest.html file to open it.

Now, before the \u003c/body> tag, add the following:

```
```
<script type="text/javascript"> alert("Hello There"); </script>
```

```

When you're done, save the file to the server (File, Save should do it, as PSPad has its handy built-in FTP program). Then quit PSPad, open your browser, and surf to your jtest page again. You should see the following: