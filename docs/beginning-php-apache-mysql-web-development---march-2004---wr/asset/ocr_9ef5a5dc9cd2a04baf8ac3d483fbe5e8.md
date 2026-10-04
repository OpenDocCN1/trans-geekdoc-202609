# Chapter 2

| Syntax | When to Use It |
| --- | --- |
| `$_SESSION['varname']` | When the variable has been assigned the value from a particular session |
| `$_COOKIE['varname']` | When the variable has been assigned the value from a cookie |
| `$_REQUEST['varname']` | When it doesn't matter ($_REQUEST includes variables passed from any of the methods) |
| `$_SERVER['varname']` | When the variable has been assigned the value from the server |
| `$_FILES['varname']` | When the variable has been assigned the value from a file upload |
| `$_ENV['varname']` | When the variable has been assigned the value from the operating environment |

If you do not retrieve the values using this syntax, the variable value will appear to be empty in your program and can cause you grief in debugging:

# Passing Variables Through a URL

The first method of passing variables between pages is through the page's URL. You've undoubtedly seen URLs such as this:

```
http://www.mydomain.com/news/articles/showart.php?id=12345
```

This is an example of passing variable values through the URL. In the preceding example, we are requesting the article with the ID number of “12345” be chosen for the showart.php program. The text after the URL is called the `query string`.

You can also combine variables in a URL by using an ampersand (&), as in this example:

```
http://www.mydomain.com/news/articles/showart.php?id=12345&lang=en
```

This asks to retrieve the file with an ID of “12345” and the language presumably equal to “en,” English.

There are a few disadvantages to passing variables through a URL:

+   - Everyone can see the values of the variables, so passing sensitive information isn't really secure using this method.

+   - The user can change the variable value in the URL, leaving your site potentially open to show-something you'd rather not.

+   - A user might also pull up inaccurate or old information using a saved URL with older variables embedded in it.