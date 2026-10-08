
## Security and Cookies

Having a fully-functional programming language built into a web browser would be a serious security risk. Being able to find out the time on someone’s PC is perfectly safe, but what if a malicious web site tried to read the user’s private files instead, or write a virus onto the computer? Thankfully, this is impossible, because JS is designed with security in mind. Most fundamentally, there are no facilities in the language that allows the programmer, and thus a malicious web site, to access any of the files on the visitor’s computer.

Actually, there’s one exception. Let me tell you about cookies.

A cookie is a small text file which a web site can write to the hard disk of any computer that visits the site, and then retrieve at a later date. It’s part of the HTML specification, rather than anything to do with JavaScript particularly. But it needs a programming language such as JavaScript or PHP in order to operate.

Cookies are rather like pieces of electronic graffiti. They can contain any data which the web site operator wishes to store, but are limited to around 1000 characters each. A site can store more than one cookie on a visitor’s computer. Crucially, for security purposes, the only site which can read a cookie is the site that put it there in the first place.

So what are cookies used for? Imagine a public web site where you’re browsing a library catalogue in search of that excellent volume, “*Defeating The Hacker*” by Robert Schifreen. A couple of days later, you visit the site again and, as if by magic, you find yourself on the page about Defeating The Hacker. How did the web site know? Because last time you visited, the site stored a small cookie on your computer called “last-book-visited”, the value of which was set to “defeating the hacker”. Or, more likely, the value was set to the database record ID or the ISBN of the book, but that’s not important right now. All you need to know is that each cookie has a name (in this case, last-book-visited) and a value (in this case, defeating the hacker).

Creating and reading a cookie isn’t particularly difficult. There are commands built into JavaScript to do it, and it only takes a few lines of code. A Google search for “javascript set cookie” or “javascript read cookie” will show you some examples.

Unfortunately, reading cookies in JS is slightly more difficult than setting them. That’s because there’s no specific command in JavaScript which says “give me the value of the last-book-browsed cookie”. Instead, there is only a command which says “give me a list of all my cookie names and values”. Once you have this list, you then have to search through it in search of the cookie you want. But, as with everything web-related, a Google search will

## Javascript and Semicolons

A word is in order about Javascript and semicolons. You'll have noticed in the examples that some lines end with a semicolon while others don't. In Javascript, each line of code is considered to end either at the end of the line or at the semicolon. So if you write each statement on a single line, you don't need a semicolon. But if you're including multiple statements on a single line, they need to be separated with a semicolon. For example, these are all valid (I've coloured the semicolons for clarity):

```javascript
document.write ("Hello")
document.write ("Hello");
document.write ("Hello"); document.write ("Hello again");
document.write ("Hello"); document.write ("Hello again");
```

But these are not:

```javascript
document.write ("Hello") document.write ("Hello again");
document.write ("Hello") document.write ("Hello again")
```

## Email Address Obfuscation

Those who send spam email for a living need to find a constant source of new email addresses to which they can send their annoying, offensive advertisements. They do this in various ways, one of which is to scour the internet looking for web pages that contain email addresses. It's actually not difficult to do. All that's required is a program to randomly connect to millions of web pages and scan the content for an "@" symbol. Then look for the nearest space to the left, and space to the right. Everything between those two spaces is likely to be an email address, ready to add to the spammer's mailing list.

Because of this, one of the best ways to ensure that your email address remains relatively free from spam is to never mention it on a web page. However, you probably also want people to be able to contact you by email. Thankfully, Javascript provides a great solution to the problem.

Instead of including your email address literally on the page, such as r, write a small Javascript program which uses one or more document.write() statements. For example, whenever you want to quote your email address, use the following on the page instead:

```javascript
<script language="javascript"> document.write("robert"); document.write("@"); document.write("the-web-book.c"); document.write("om"); </script>
```

Such behaviour is enough to confuse the vast majority of the so-called automatic email address harvester programs that are continually scanning the web in search of fresh addresses.

If you want something even smarter, search online with your favourite search engine for "javascript email address obfuscation". This will lead you to a variety of web sites which allow you to enter an email address and which will then generate a complex impenetrable Javascript program just for you which, when run by a visitor's web browser, will show your email address.

## Why Upload?

You may be wondering why, if JavaScript is a client-side language that gets executed by the browser, we have to upload pages to the server before we can test them. Can you not just double-click on jstest.html from within Windows and get the browser to execute the local copy instead, and save yourself the hassle of uploading the file until it's ready for public consumption?

In theory, yes you can. You don't need to trouble your web server at all when you're developing JS pages. However, in practice, many web browsers don't like letting you do this. They regard it as a security risk, on the basis that any JS code in a local page must be malicious. Internet Explorer versions 7 and 8, for example, will pop up various warnings asking if you really want to allow this code to run. The only way to stop this is to reduce the security settings on your browser, which is not wise as it will also reduce your safety on the web in general.

Therefore, it's best to always run JavaScript code off a server. But it's important to realise that this is not because it's a requirement of the language.

Before we leave this example program, there’s one slight problem that we need to fix. The minutes and the seconds don’t look right, because there’s a zero missing from the front of each of them. Which is just as we’d expect if, for example, the current time is 8 minutes past the hour. The date() function is doing what it’s supposed to do, and returning a value of 8 for the minutes. If we want to display it in a cosmetically-enhanced way, it’s up to us to add the necessary code.

So, edit the jtest.html file and add the following after line 7:

```javascript
if (d.getMinutes() < 10 )
{
 document.write("0")
}
```

And add the following after what’s shown above as line 9:

```javascript
if (d.getSeconds() < 10 )
{
 document.write("0")
}
```

The purpose of this code should be obvious. Before we display the minutes, we check whether the value is less than 10 and, if so, insert a zero into the document (ie, the web page). Ditto for the seconds.

This also shows you how to use the "if..." statement in JavaScript. Specifically, note the way that everything which should be executed if the statement is true, goes in curly brackets.

The ability to perform date-based calculations in web pages is very handy. For example, you could easily write a web page which automatically alters its appearance according to the season. Just create 4 images that correspond to spring, summer, autumn and winter. Then use some Javascript to find out the current month and perform one of 4 different `<img src=xyz.jpg>` operations, where xyz corresponds to the name of one of your image files. Alternatively, you could automatically add a "Merry Christmas" footer to your home page if the month is December and the date is the 25th.
