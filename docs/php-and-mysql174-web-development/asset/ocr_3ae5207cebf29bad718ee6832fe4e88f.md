Save the file and load it in your browser by filling out Bob’s form and clicking the Submit Order button. You should see something similar to the output shown in Figure 1.2.

![](bbox=[0.142, 0.173, 0.558, 0.403])

Figure 1.2 Text passed to PHP's echo construct is echoed to the browser

Notice how the PHP code you wrote was embedded inside a normal-looking HTML file. Try viewing the source from your browser. You should see this code <!DOCTYPE html>

```
<html>
<head>
  <title>Bob's Auto Parts - Order Results</title>
</head>
<body>
  <h1>Bob's Auto Parts</h1>
  <h2>Order Results</h2>
  <p>Order processed.</p>
</body>
</html>
```

None of the raw PHP is visible because the PHP interpreter has run through the script and replaced it out with the script. This means that from PHP you can produce HTML viewable by any browser; in other words, the user’s browser does not need to understand PHP.

This example illustrates the concept of server-side scripting in a nutshell. The PHP has been interpreted and executed on the web server, as distinct from JavaScript and other client-side technologies interpreted and executed within a web browser on a user’s machine.

The code that you now have in this file consists of four types of text:

+   - HTML
- PHP tags
- PHP statements
- Whitespace