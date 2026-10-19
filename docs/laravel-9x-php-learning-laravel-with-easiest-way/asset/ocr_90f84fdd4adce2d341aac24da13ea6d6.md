email input field to contain the email address the user would like to begin using. Without CSRF protection, a malicious website could create an HTML form that points to your application's /user/email route and submits the malicious user's own email address:

```
<form action="https://your-application.com/user/email" method="POST">
    <input type="email" value="malicious-email@example.com">
</form>

<script>
    document.forms[0].submit();
</script>
```

If the malicious website automatically submits the form when the page is loaded, the malicious user only needs to lure an unsuspecting user of your application to visit their website and their email address will be changed in your application.

To prevent this vulnerability, we need to inspect every incoming POST , PUT , PATCH , or DELETE request for a secret session value that the malicious application is unable to access.

# Preventing CSRF Requests