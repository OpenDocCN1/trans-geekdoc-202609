+   ■ Microsoft Edge (Windows)
+   Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36 Edg/132.0.0.0

+   ■ Chrome 132 (Windows)
+   Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36

+   ■ Firefox 135 (Windows)
+   Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:135.0) Gecko/20100101 Firefox/135.0

+   ■ Safari (macOS)
+   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.6 Safari/605.1.15

+   ■ Internet Explorer 6 (Windows)
+   Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)

+   ■ Internet Explorer 10 (Windows)
+   Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)

+   ■ Internet Explorer 11 (Windows)
+   Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; AS; rv:11.0) like Gecko

+   ■ Netscape 7.1 (Windows)
+   Mozilla/5.0 (Windows; U; Windows NT 5.1; de-DE; rv:1.4) Gecko/20030619 Netscape/7.1 (ax)

+   ■ Konqueror 4.9 (Linux)
+   Mozilla/5.0 (X11; Linux) KHTML/4.9.1 (like Gecko) Konqueror/4.9

+   ■ Internet Explorer 5.23 (macOS)
+   Mozilla/4.0 (compatible; MSIE 5.23; Mac_PowerPC)

This information can be the basis for a browser switch. You will also find other useful variables in $_SERVER, such as PHP_SELF, which contains the URL of the current PHP script.

There is a whole range of other environment variables. However, some of these are very dependent on the operating system and the web server used. To demonstrate this, the following small script outputs the content of $_SERVER and $_ENV (see also Figure 8.22).

```
<h1>Server variables</h1>
<table><tr><th>Name</th><th>Value</th></tr>

<?php
ksort($_SERVER);
foreach ($_SERVER as $name => $value) {
if (is_array($value)) {
```