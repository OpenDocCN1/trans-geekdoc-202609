The Firefox browser (and all other browsers) also offers options in the browser settings for cookie handling. You can access this via Tools • Settings • Privacy & Security and then can make the appropriate settings in the Enhanced Tracking Protection area (see Figure 14.3).

# ## 14.2 Facts and Background

But what are these what are these ominous cookies all about? The idea came from Netscape in the mid-1990s, at a time when the company was still the world market leader in web browsers. A copy of the original description document can be found at http://s-prs.co/v602279. It refers to a “preliminary specification,” a provisional description. Nevertheless, most browser manufacturers adhere to these specifications. A new approach with extended possibilities can be found at http://s-prs.co/v602280.

# ## 14.2.1 What Is a Cookie?

A _cookie_ is text information that is sent back and forth between the server (the web server) and the client (the web browser). A web server sends a cookie as part of the HTTP header of the request. This is expressed in a header entry according to the following pattern:

```
Set-Cookie: ProgrammingLanguage=PHP
Set-Cookie: LanguageVersion=8
```

The web browser receives this data and processes it according to the configuration, resulting in one of the following:

+   - The cookie is saved.
+   - The cookie is rejected.
+   - The user is asked whether the cookie should be accepted or rejected.

The web server is initially unaware of what exactly happens to the cookie. The text information is stored on the user’s hard disk or in the system’s memory. The real trick is only revealed the next time a page is called up from the web server, when the web browser sends the cookie back to the web server. It looks like this:

```
Cookie: ProgrammingLanguage=PHP; LanguageVersion=8
```

This allows the server to access the previously sent data again and recognize the user.

The cookies themselves end up on the user’s hard disk. The exact implementation is the responsibility of each browser manufacturer and is always slightly different. A file-based database, such as SQLite, is usually used.