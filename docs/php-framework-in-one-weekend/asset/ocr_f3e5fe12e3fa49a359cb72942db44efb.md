# Listing 3.2: public/index.php

Start PHP’s built-in web server (if it’s not already still running from before) and load up
the page in your browser to check it works.

```
$ php -S localhost:4000 -t public/
```

Be sure to provide a value for the $name parameter in the URL, like this:

```
http://localhost:4000/?name=World
```

NB: Directly printing out user input is never a good idea. It is the easiest way to introduce
security issues into your code. In this example we have taken the $name variable directly
from user input and then printed it out. In reality you would filter this value to remove any
dangerous characters to prevent against cross-site scripting (XSS). We’re not doing this
here because we’re going to use a templating system that takes care of this for us. You can
confirm that this is insecure by loading the following URL:

```
http://localhost:4000/?name=Danger<script>alert(’hi!’)</script>
```

You will see a JavaScript alert. The code in the GET parameter is embedded directly in the
page. You don’t have to be a security expert to realise that allowing users to inject
JavaScriptcodeintothepageisabadidea.