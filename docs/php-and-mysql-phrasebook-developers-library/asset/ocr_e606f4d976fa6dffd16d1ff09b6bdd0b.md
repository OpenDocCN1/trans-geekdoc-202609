When it comes to prefilling form elements, multiple selection lists are the most difficult ones to implement. This is because in $_GET or $_POST, you have an array of chosen options; so you cannot just compare strings, but you have to search for the specified value in the array. Lucky for us, PHP offers something suitable in the form of the in_array() function. So, the effort required is not much more than with the other form elements: If the current value is in $_GET/$_POST, print out the selected attribute.

However, the HTML form must be specially prepared to allow PHP to access the data from the multiple selection list: The value of the name attribute has to end with [], hinting to PHP that it should expect an array of values, not just a string value. Accessing the list data, however, can still be done using $_GET['listname']/$POST['listname'] and not $_GET['listname[]']/$POST['listname[]'], as shown in the preceding code.

If you want to prefill the list with data from the cookie, you just have to use the well-known file getFormData.inc.php from the previous phrases. It contains two additional functions that return an array rather than a string:

```
function getFormDataArrayGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null && isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
}
```