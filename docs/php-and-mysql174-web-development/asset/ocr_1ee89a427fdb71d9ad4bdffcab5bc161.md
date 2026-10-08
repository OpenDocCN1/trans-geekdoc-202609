# Formatting Strings 107

If the example in Listing 4.1, we are sending out to email. But do we need to take into account here? We don't care if the email contains HTML, so using the `htmlspecialchars()` function is not appropriate here.

The main issue in email headers that are separated by the character `\r\n` (carriage return-line feed). We need to take that user data we use in the email headers does not contain these characters, or we run the risk of a set of attacks, called header injection. (We discuss this in detail in Part III.)

With many string processing problems, there are many ways to achieve this. One way is by using the `str_replace()` function, as follows:

```
$mailcontent = "Customer name: ".str_replace("\r\n","","",$name)."\n";
"Customer email: ".str_replace("\r\n","","",$email)."\n";
"Customer comments: ".str_replace("\r\n","","",$feedback)."\n";
```

If you have more complicated replacement or replacement rules, you can use the regular expression functions described later in this chapter. In a simple case like this where you want to entirely replace one string with another, you should always use the `str_replace()` function. We'll discuss the `str_replace()` function in more detail later in this chapter.

# Using HTML Formatting: The nl2br() Function

The `nl2br()` function takes a string as a parameter and replaces all the newlines in it with the HTML `<br/>` tag. This capability is useful for echoing a long string to the browser. For example, you can use this function to format the customer's feedback to echo it:

```
<p>Your feedback (show below) has been sent.</p>
<p>?php echo nl2br(htmlspecialchars($feedback)); ?></p>
```

Remember that HTML disregards plain whitespace, so if you don't filter your output through nl2br(), it will appear on a single line (except for newlines forced by the browser window). The result is illustrated in Figure 4.2.

Notice that we first applied the `htmlspecialchars()` function and then the `nl2br()` function. This is because if we did them in the opposite order, `<br>` tags inserted by the `nl2br()` function would be translated into HTML entities by the `htmlspecialchars()` function and hence would have no effect.