```
<input type="submit" name="submit" value="submit">
</form>
```

Before we show the script itself, now is a good time to note that Web programming is slightly different from other types of programming in one important respect: It is stateless. To display a page, a Web server must first receive a request from a browser. The language they speak is called HTTP, the Hypertext Transfer Protocol. The request will include several things—the page the browser wishes to see, the form data, the type of browser being used, and the IP address the browser is using. Based on this information, the Web server will decide what to serve.

Once it has served this page, the server maintains no connection to the browser. It has absolutely no memory of what it served to whom. Each HTTP request is dealt with individually with no regard to what came before it. For this reason, in Web programming you need to come up with some way of maintaining state. That is, if you are progressing through an application, you will need some way of letting the server know what happened. Essentially, you will need ways of passing variables from page to page. This will come up in our applications. The applications will solve this problem in one of three ways: by passing hidden form elements, by using cookies, or by using sessions.

Now back to our script.

```
<form action="myscript.php">
    <input type="text" name="surnmae">
    <input type="submit" name="submit" value="submit">
</form>
```

You can decide what you will display on a page based on the variable information that comes from HTML forms. For instance, you could check if the preceding form had been submitted by checking if the variable name $submit had a value of "submit." This very technique will come into play when it comes to creating the page for inserting information into the database.

There is one page in our application, called sign.php, that has an HTML form. The action of the form in this page is create_entry.php. Here's the page in all its glory:

```
<h2>Sign my Guest Book!!!</h2>

<form method=post action="create_entry.php">

<b>Name:</b>
<input type=text size=40 name=name>
<br>
<b>Location:</b>
<input type=text size=40 name=location>
<br>
```