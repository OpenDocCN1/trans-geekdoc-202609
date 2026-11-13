When array_key_value() is called from the preceding example, the first if block will be ignored. In the second if block, the array_key_exists() function checks if a key by name of email exists in the $_POST array. If it does, the value of $_POST['email'] will be assigned to $email when the function returns a value. If the email key does not exist, $email will contain an empty string.

# IS_ASSOC()

Sometimes you need to know not just if a variable is an array, which the PHP function is_array() can tell you, but if it's an associative array — in other words, do all the elements have named keys? The is_assoc() function exists for this situation.

```
function is_assoc($a)
{
     if (is_array($a) || is_object($a))
     {
         $nkeys = array_filter(array_keys($a),'is_numeric');
         if (empty($nkeys))
         {
             return TRUE;
         }
     }
     return FALSE;
}
```

# DEFENSIVE AND TEXT-HANDLING FUNCTIONS

A shocking amount of programming work has to do with the manipulation of strings. It seems there's always text to be chopped up, stuck together, searched for, or formatted. This section deals with some of the text-processing functions available in PHP.

# CHARSET()

This function sends out an HTTP header that explicitly sets the character-set-encoding value for the page to ISO-8859-1:

```
function charset($charset='',$mimetype='')
{
     if (empty($charset))
     {
         $charset = 'ISO-8859-1';
     }
     if (empty($mimetype))
     {
         $mimetype = 'text/html';
     }
     header("Content-Type: $mimetype; charset=$charset");
}
```