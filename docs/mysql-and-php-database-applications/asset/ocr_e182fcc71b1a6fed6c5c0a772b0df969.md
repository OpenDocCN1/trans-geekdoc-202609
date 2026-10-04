# Introduction

```
<input type="submit" name="submit" value="submit">
</form>
```

Before we show the script itself, now is a good time to note that Web programming is slightly different from other types of programming in one important respect: it is stateless. To display a page, a Web server must first receive a request from a browser. The language they speak is called HTTP, the Hypertext Transfer Protocol. The request will include several things—the page browser wishes to see, the data, the type of browser being used, and the IP address the browser is using. Based on this information, the Web server will decide what to serve.

Once it has served this page, the server maintains no memory of what it served to. Each HTTP request is dealt individually with no regard to what came before. For this reason, in Web programming you will need to come up with some way of maintaining state. That is, if you are progressing through an application, you will need some way of letting the server know what happened. Essentially, you will need ways of passing variables from page to page. This will come up in our applications. The applications will solve this problem in one of three ways: by using hidden form elements, cookies, or by using sessions.

Now back to our script.

```
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

You can decide what you will display on a page based on the variable information that comes from HTML forms. For instance, you could check if the preceding form has been submitted by checking the variable name $submit has a value of “submit”. This very technique will come into play when it comes to creating the page for inserting information into the database.

There is one page in our application, called sign.php, that has an HTML form. Here’s the page in all its glory:

```
<h2>Sign my Guest Book!</h2></h2>
```

```
<form method="post" action="create_entry.php">
<b>Name:</b>
<input type="text" size=40 name="name">
<br>
<b>Location:</b>
<input type="text" size=40 name="location">
<br>
```