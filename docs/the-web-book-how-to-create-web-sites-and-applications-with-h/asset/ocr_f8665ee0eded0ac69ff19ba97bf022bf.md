# ## Security and Cookies

Having a fully-functional programming language built into a web browser would be a serious security risk. Being able to find out the time on someone’s PC is perfectly safe, but what if a malicious web site tried to read the user’s private files instead, or write a virus onto the computer? Thankfully, this is impossible, because JS is designed with security in mind. Most fundamentally, there are no facilities in the language that allows the programmer, and thus a malicious web site, to access any of the files on the visitor’s computer.

Actually, there’s one exception. Let me tell you about cookies.

A cookie is a small text file which a web site can write to the hard disk of any computer that visits the site, and then retrieve at a later date. It’s part of the HTML specification, rather than anything to do with JavaScript particularly. But it needs a programming language such as JavaScript or PHP in order to operate.

Cookies are rather like pieces of electronic graffiti. They can contain any data which the web site operator wishes to store, but are limited to around 1000 characters each. A site can store more than one cookie on a visitor’s computer. Crucially, for security purposes, the only site which can read a cookie is the site that put it there in the first place.

So what are cookies used for? Imagine a public web site where you’re browsing a library catalogue in search of that excellent volume, “*Defeating The Hacker*” by Robert Schifreen. A couple of days later, you visit the site again and, as if by magic, you find yourself on the page about Defeating The Hacker. How did the web site know? Because last time you visited, the site stored a small cookie on your computer called “last-book-visited”, the value of which was set to “defeating the hacker”. Or, more likely, the value was set to the database record ID or the ISBN of the book, but that’s not important right now. All you need to know is that each cookie has a name (in this case, last-book-visited) and a value (in this case, defeating the hacker).

Creating and reading a cookie isn’t particularly difficult. There are commands built into JavaScript to do it, and it only takes a few lines of code. A Google search for “javascript set cookie” or “javascript read cookie” will show you some examples.

Unfortunately, reading cookies in JS is slightly more difficult than setting them. That’s because there’s no specific command in JavaScript which says “give me the value of the last-book-browsed cookie”. Instead, there is only a command which says “give me a list of all my cookie names and values”. Once you have this list, you then have to search through it in search of the cookie you want. But, as with everything web-related, a Google search will