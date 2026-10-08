Hey presto, a dynamically-created collection of checkboxes. Now, hopefully, you can start to see how PHP and MySQL work together to allow you to create powerful web-based applications. And you're probably itching to get to the database stuff. Don't worry, not long now.

Note how I've preceded quotation marks with a backslash when I want to echo them to the visitor's browser, ie when they're not part of the PHP code itself. This was discussed in more detail on page 246.

# Retrieving Textarea and Dropdown Data

So far, I've shown you how to retrieve the contents of a textbox, checkbox and radio button using PHP. For completeness, it's worth explaining how to retrieve the value of a textarea and a dropdown too.

A textarea's content is retrieved in the same way as a textbox. Just use `$_POST["xyz"]`, where xyz is the name of the textarea as defined in the form. Remember, though, that it may contain carriage return characters if the user pressed Return while entering the contents of the textarea. Carriage returns are harmless from a security perspective, but if you don't want them you can remove them with the same type of `ereg_replace` command used for sanitizing. The `ereg` code for a carriage return character is \r although it's often also followed by a "line feed" character (\n) as well. So you need to search for \n and \r and delete them both.

As for a dropdown box, this too is easy to retrieve. Just use `$_POST[]` with the name of the dropbox as specified in the form. For example, here's the HTML code for a simple dropdown box. As you can see, it is created by a `<select>` tag, though few people ever refer to it as a select box:

```
<select name="dd_season">
<option>Spring</option>
<option>Summer</option>
<option>Autumn</option>
<option>Winter</option>
</select>
```

This produces, on a form, the following:

![](bbox=[0.12, 0.82, 0.25, 0.9])