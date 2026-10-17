![](bbox=[0.257, 0.087, 0.743, 0.367])

**FIGURE 3.18**  Simple login page for a PHP web application showing potential control over the “error” parameter.

Exploiting this vulnerability is as simple as it gets, simply place a set of **<script>** tags with JavaScript inside to determine if it fires. We need to validate if it’s possible to exploit this vulnerability or not before creating a full payload. To do this, we will send the payload **<script>alert(1)</script>** into the **error** parameter, with a request like **http://127.0.0.1/login.php?message=%3Cscript%3Ealert(1)%3C/script%3E**. Note that the error parameter is URL encoded at this point, as this is required to ensure the special characters are interpreted properly by the application and not by the browser.

![](bbox=[0.178, 0.537, 0.822, 0.902])

**FIGURE 3.19**  Successful XSS exploitation using the message parameter.