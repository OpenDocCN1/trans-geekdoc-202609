![](bbox=[0.14, 0.1, 0.86, 0.45])

Figure 14.5 The Browser Developer Tools Reveal the Arrival of Cookies.

> > **Tip**
> > If you still want to set cookies in the middle of the PHP page for convenience (or even have to), you can use the functions for *output buffering*. You can find more information on this at the end of the chapter.

> > **Note**
> > If you want to change the value of a cookie, you must enter exactly the same information as when the cookie was created (with the exception of the expiration date and, of course, the cookie value, as you may want to change this information). If you fail to do this, PHP or the web browser will create several cookies with the same name.

And a final brief note on the time sequence: Cookies are sent to the client in the order in which they appear in the PHP script.

# Special Characters

The cookie value is automatically URL-coded, so under the hood, a call is made to `urlencode()` is made. However, there may be situations in which this is not desired, such as if the cookie value is already URL-encoded. In this case, use the `setrawcookie()`