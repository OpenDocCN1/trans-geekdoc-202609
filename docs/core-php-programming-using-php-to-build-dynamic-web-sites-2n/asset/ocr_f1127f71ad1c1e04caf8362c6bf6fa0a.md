# Core PHP Programming

```
print("<A HREF=\$session\>page2.php?session=\$\>next</A>");
```

to send session to the next page. This technique works with all browsers, even Lynx.

An alternative is to use cookies. Like GET and POST variables, cookies are turned into variables by PHP. So, you could create a cookie named session. The difference would be that, cookies may only be in headers, unless you have to send them to the browser before sending any HTML code. Check out the setcookie function in Chapter 8, "I/O Functions," if you wish to pursue this strategy. A more complex strategy attempts to use cookies, but falls back on GET variables if necessary.

Both methods are used on the Internet. Check any e-commerce site. For the purpose of example, I will present a strategy that uses session for. The first step is to create a table to hold session identifiers. Listing 17.4 is SQL code for creating a simple session table in MySQL database.

This table is keyed by an eight-character string. Each time the user moves to a new page, we will update the LastAction column. That way we can clear any sessions that appear to be unused. Every visit to our page will trigger a clearing of all sessions without action for 30 minutes. We will need to test each visitor for having a session identifier. If they don't have one, we will create one. If they do have one, we will need to check it to make sure it's valid.

# Listing 17.4 Creating Session Table

```
CREATE TABLE session
(
  ID VARCHAR(8) NOT NULL,
  LastAction DATETIME,
  PRIMARY KEY (ID)
);
```

The first time you load Listing 17.5, it will create a session for you. Each click of the "Refresh Page" link will cause the script to check the session. If the session identifier is not in the session table, then the session identifier will be rejected, and a new one will be created. You can try submitting a bad session identifier by erasing a character in the location box of your browser.

# Listing 17.5 Checking Session ID