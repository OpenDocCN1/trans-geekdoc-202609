# How to do it...

+   First, to demonstrate the problem, we create a web page that simulates an infected page that generates a request to post an entry to the database. For this illustration, we will call the file `chap_12_form_csrf_test_unprotected.html`:  
```html
<!DOCTYPE html>
<body onload="load()">
    <form action="chap_12_form_unprotected.php"
          method="post" id="csrf_test" name="csrf_test">
        <input name="name" type="hidden" value="No Goodnick" />
        <input name="email" type="hidden" value="malicious@owasp.org" />
        <input name="comments" type="hidden"
               value="Form is vulnerable to CSRF attacks!" />
        <input name="process" type="hidden" value="1" />
    </form>
    <script>
        function load() { document.forms['csrf_test'].submit(); }
    </script>
</body>
</html>
```

+   Next, we create a script called `chap_12_form_unprotected.php` that responds to the form posting. As with other calling programs in this book, we set up autoloading and use the `Application\Database\Connection` class covered in *Chapter 5, Interacting with a Database*:  
```php
<?php
define('DB_CONFIG_FILE', '../../../config/db.config.php');
require __DIR__ . '../../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Database\Connection;

$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
```

+   We then check to see the process button has been pressed, and even implement a filtering mechanism, as covered in the Filtering $_POST data recipe in this chapter. This is to prove that a CSRF attack is easily able to bypass filters:

```php
if ( $_POST['process'] ) {
    $filter = [
        'trim' => function ($item) { return trim($item); },
        'email' => function ($item) {
            return filter_var($item, FILTER_SANITIZE_EMAIL); },
        'length' => function ($item, $length) {
            return substr($item, 0, $length); },
        'stripTags' => function ($item) {
```