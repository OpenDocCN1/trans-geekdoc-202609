# What is Automated Testing

hello_test_with_your_eyes.php

```
<?php
require __DIR__ . '/hello.php';
echo hello();
```

If you navigate to hello_test_with_your_eyes.php in your browser and see Hello World!, the function and the test both work.

Alternatively, you can just run it from PHP’s Command Line Interface (CLI):

```
$ php hello_test_with_your_eyes.php
Hello World!
```

This is manual testing.

All PHP developers have tested this at some point. Manual testing with your web browser is very common. You write some code expecting a outcome, then you run the code to verify that you receive the expected outcome. If you look at the web page you built to verify you aren’t receiving errors and the outcome looks more or less as you expect, you are already testing your application.

However, if you test your application by yourself, and by manually checking every possible action the user might take, it could take some time to test. If your application is very big, testing every possibility in the entire application could take a very long time, which means you cannot possibly test everything often.

# Automated Testing

What if, instead of manually checking the results in a web browser, you write code to test your application? The following is some very primitive test code for our primitive hello.php application. We would place this code in a file called hello_test_automated.php alongside our application and our manual test.