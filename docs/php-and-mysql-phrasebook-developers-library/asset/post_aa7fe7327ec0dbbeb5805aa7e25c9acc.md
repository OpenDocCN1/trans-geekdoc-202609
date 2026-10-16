
## Checking Whether a Form Has Been Submitted

```php
<?php
if (isset($_POST['Submit'])) {
    echo '<h1>Thank you for filling out this form!</h1>';
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```

When both the HTML form and the processing PHP code are on the same page (something that is recommended when it comes to prefilling forms), it is important to find out whether a form is just called in the browser (using GET) or if the form is submitted (and the data must be processed).

You can take several different approaches to this task: something that always works is assigning the Submit button a name and then testing whether this name is present when the form is submitted.

**TIP:** If your form has multiple Submit buttons, give each of them a distinctive name; then, you can check specifically for this name and, therefore, determine which Submit button has been used.

## Saving Form Data into a Cookie

```php
function setCookieData($arr) {
    $formdata = getCookieData();
    if ($formdata == null) {
        $formdata = array();
    }
    foreach ($arr as $name => $value) {
        $formdata[$name] = $value;
    }
    setcookie('formdata', serialize($formdata), time()+30*24*60*60);
}
```

After the form has been submitted, the data must go somewhere, possibly in a database (see Chapters 8, “Working with MySQL Databases,” and 9, “Working with Other Databases”), in a file, or sent via email. When a Web site contains several similar forms (for example, forms that all require the user to provide his name and contact information), it is a good idea to save the data after the user fills it in. Because HTTP is a stateless protocol, you have to use cookies (see Chapter 7, “Using Files on the Server File System”)—sessions are useless because they expire when the user closes the browser.

Because user agents only have to save 20 cookies per domain (although they might store more), it’s a good idea to store the form information in one cookie, in the form of an array. However, only string values are allowed in cookies; this is why you have to serialize the array. Also be aware that you usually can only store a bit less than 4KB of data in a cookie; the rest may get truncated.

The function shown in the listing at the beginning of this phrase writes the contents of the array provided as a parameter into the cookie.

The function getCookieData() returns the existing data from the cookie (if available) and unserializes it into an array. You will see the code in a later phrase.

The only thing left to do is to write the required form data into this array. You can specifically submit only certain values, or the complete array `$_GET` or `$_POST`, as shown in the following code:

```php
<?php
require_once 'getFormData.inc.php';
if (isset($_POST['Submit'])) {
    setCookieData($_POST);
}
?>
...
<?php
if (isset($_POST['Submit'])) {
    echo '<h1>Thank you for filling out this form!</h1>';
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
...
</form>
<?php
}
?>
```

Figure 5.2 shows the resulting cookie.

![](img/2862989e5dc7f1b1d0bc64321737f084_142_0.png)

Figure 5.2 The serialized form data is saved in a cookie.

**NOTE:** Note that you have to save the form data prior to any HTML output. Because cookies are sent as part of the HTTP header, they have to be declared before HTML starts (and, as a matter of consequence, the HTTP header ends). You can find more information about the timing of cookies in Chapter 6.

## Prefilling Text Fields and Password Fields

```php
<input type="text" name="textfieldname" value="<?php echo isset($_POST['textfieldname']) ? htmlspecialchars($_POST['textfieldname']) : '';?>" />
```

The value in a text field (and in a password field and in a hidden field, as well) is provided in its value attribute. However, the data there must be properly encoded with htmlspecialchars() to get rid of dangerous characters such as `"`, `<`, or `>`. The code snippet in the preceding code expects the form to be submitted back to itself: thus, it extracts the current value of the text field from `$_POST` (it would work analogously with `$_GET`). This works for password fields and hidden fields, as well (although it is considered bad practice to prefill password fields, since the "secret" data in there is not encrypted in HTML).

**NOTE:** If you also want to escape the single quote (`'`) character, use htmlspecialchars() in the following fashion:

```php
htmlspecialchars($_POST['textfieldname'], ENT_QUOTES)
```

Because in our form all HTML attributes are delimited by double quotes, we do not need to specifically escape single quotes. If you are using single quotes, however, you absolutely need to escape them within attribute values.

If you want to use a default value for this form element, you just have to provide this default value rather than the empty string in the PHP code:

```php
<input type="text" name="textfieldname"
    value="<?php
    echo (isset($_POST['textfieldname'])) ?
    htmlspecialchars($_POST['textfieldname']) : 'default
    value';
    ?>" />
```

Another possibility is to prefill form values from cookies. This is quite useful when users enter their data into a form several times. So, when they visit a form on the site a couple of days later, the old data can be retrieved from the cookie. Yes, just 1 cookie because only 20 cookies per domain are allowed. We use an array for that, of course. However, only strings are allowed as cookie values, so the use of serialize() and unserialize() is required.

The following function retrieves a value from the cookie that contains the form data. The order of precedence is by default (but can be changed by the `variables_order` php.ini setting) as follows: If `$_GET` or `$_POST` contains a current value for this field, this value is used. (Specific versions of the function exist for `$_GET` and `$_POST` because only one of these two methods is normally used at a time.) Otherwise, the script looks in `$_COOKIE` for an associated value. If nothing is found, an empty string is returned:

```php
function getCookieData() {
    if (isset($_COOKIE['formdata'])) {
        $formdata = $_COOKIE['formdata'];
        if ($formdata != '') {
            if (get_magic_quotes_gpc()) {
                $formdata = stripslashes($formdata);
            }
            return unserialize($formdata);
        } else {
            return array();
        }
    } else {
        return null;
    }
}

function getFormDataPOST($name) {
    if (isset($_POST[$name])) {
        return $_POST[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return '';
}

function getFormDataGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return '';
}
```

Now, prefilling the form value is easy: Because getFormDataGET() and getFormDataPOST() always return anything—including an empty string—the return value can be directly used in the text field's value attribute:

```php
<?php
require_once 'getFormData.inc.php';
?>
...
<input type="text" name="textfieldname"
    value="<?php
    echo
    htmlspecialchars(getFormDataPOST('textfieldname'));
?>">
```

## Prefilling Multiline Text Fields

```php
<textarea cols="40" rows="5" name="areafieldname"><?php echo (isset($_POST['areafieldname'])) ? htmlspecialchars($_POST['areafieldname']) : ''; ?></textarea>
```

With multiline text fields, almost the same approach as with single-line text fields and password fields can be used. The only difference is the location where to put the prefill value: It belongs between `<textarea>` and `</textarea>`, as shown in the preceding code.

**NOTE:** If you want to provide a default value in the multiline text field (for example, "Enter your data here"), provide this instead of the empty string in the PHP code. Remember that line feeds are possible, as well:

```php
<?php
 echo (isset($_POST['areafieldname'])) ?
 htmlspecialchars($_POST['areafieldname']) :
 "default\nvalue";
?>
```

Using the combined cookie/GET or cookie/POST approach, the code simplifies a bit:

```php
<?php
require_once 'getFormData.inc.php';
?>
...
<textarea cols="40" rows="5" name="areafieldname"><?php
 echo htmlspecialchars(getFormDataPOST('areafieldname'));
?></textarea>
```
