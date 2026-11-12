```
// Server-side validation of anti-CSRF token
if (isset($_POST['csrf_token']) && $_POST['csrf_token'] == = $_SESSION['csrf_token']) {
// Processing the request
    echo "Request processed successfully";
} else {
// Reject request
    echo "Error: invalid CSRF request.";
}
?>
```

This PHP code illustrates the use of anti-CSRF tokens to prevent CSRF attacks on a web form. Here is a detailed explanation of each part of the code:

**session_start():** This function starts a new session or resumes an existing one. Sessions are used to store session variables, such as the anti-CSRF token, which can be accessed via different pages.

**Anti-CSRF token generation:** The code checks whether the anti-CSRF token is already present in the session. If not, a new token is generated using the **random_bytes()** function to create a 32-byte random string, then **bin2hex()** to convert this string to a hexadecimal representation.

**Inclusion of the anti-CSRF token in a form:** The anti-CSRF token is then included in an HTML form as a hidden field (<input type="hidden">). This ensures that the token is submitted with the rest of the form data when it is sent to the server.