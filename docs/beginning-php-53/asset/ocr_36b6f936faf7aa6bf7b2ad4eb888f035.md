In this chapter, you look at other ways to save state. You learn how to use:

+   - Query strings to store small amounts of data in the URL
+   - Cookies to store larger amounts of data in the browser itself
+   - Sessions to store even larger amounts of data, and store it in a much more secure fashion

By using any of these three methods (or a combination of them), you can create persistent Web applications that carry their data from one page view to the next.

# Saving State with Query Strings

Query strings are a quick, convenient way to pass small amounts of data between browser requests. Common uses of query strings include remembering a user’s entered keywords when using a search function, identifying which topic within a forum to display to the user, and specifying which post within a blog to display.

Query string data is very easy for the user to alter, because it’s visible and editable within the browser’s address bar. Therefore, query strings should be used only in situations where sending incorrect data won’t compromise security. For example, don’t use query strings for storing things such as user IDs (unless your script additionally verifies that the users are who they say they are).

> You also need to make sure you don’t rely on query strings to authenticate users, because people often send URLs to friends in emails or instant messaging applications. If your URL contains all the data needed to authenticate a user, and that user sends the URL to a friend, then the friend can pretend to be them! You’ll find that sessions — discussed later in the chapter — are a much better way of authenticating users.

If you’ve worked your way through Chapter 9, you’re already somewhat familiar with the concept of query strings. You’ll remember that you can embed sent form data in a URL by setting the form’s method attribute to get. When the form data is sent to the server, it is appended to the end of the URL as follows:

```
http://localhost/myscript.php?firstName=Fred&lastName=Bishop& ...
```

In other words, the browser adds a query (?) character to the end of the URL, then follows it with each of the form fields as “name=value” pairs, with each pair separated by an ampersand (&). The query string is the part of the URL after the ? character.

# Building Query Strings

The great thing about query strings is that they’re not limited to form data. Because a query string is simply a string of characters stored in a URL, you can manually create a URL containing a query string in your PHP script, then include the URL as a link within the displayed page or in an email, for example. PHP even provides some built-in functions to make the process easier.

Here’s a simple example that creates two variables, $firstName and $age, then creates a link in the displayed page that contains a query string to store the variable values: