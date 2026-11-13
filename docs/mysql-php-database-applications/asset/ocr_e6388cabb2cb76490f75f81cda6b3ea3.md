If the character set is left undefined, it can be much more difficult to detect and prevent hacks into your scripts (by looking for < and > characters, for example). If you have access to the php.ini file for your site, you can uncomment the 'default_charset' value there to the same effect. You can find more information about this topic at the following sites:

+   http://www.cert.org/tech_tips/malicious_code_mitigation.html
+   http://www.apache.org/info/css-security/encoding_examples.html

# CLEANUP_TEXT() This function goes a long way toward making sure we don't insert malicious text into our database.

```
function cleanup_text ($value='', $preserve='', $allowed_tags='')
{
    if (empty($preserve))
    {
        $value = strip_tags($value, $allowed_tags);
    }
    $value = htmlspecialchars($value);
    return $value;
}
```

This function accomplishes two things. First, it removes all HTML tags. The strip_tags() function takes care of that. We can indicate tags we want to keep with the third argument ($allowed_tags). For instance, if we want to allow bold and italic tags, the second argument to strip_tags() can be a string like this: <b><i>. If we want to leave tags as they are, we can indicate this with a non-empty value in the second argument, $preserve.

Then htmlentities() changes characters like ampersands (&) and double quotes to their equivalent HTML entities (&amp; and &quot;, respectively). After being run through this little function, your text is ready to be inserted in the database.

# REVERSE_CLEANUP_TEXT() So we've run all the text from your users through cleanup_text() before storing it in our database, for safety's sake. Now, though, we need to get that text back out of the database and display it on a Web page. If we did allow some HTML tags to be included, we'll need to reverse the effects of cleanup_text(), or instead of seeing this —

My mom won't let me watch The Exorcist tonight!

-you'll see this:

My mom won't let me watch <i>The Exorcist</i> tonight!