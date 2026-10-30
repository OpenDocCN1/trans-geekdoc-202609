Char(39) is the single quote. So instead of ‘ or ‘1’ = ‘1 you have:

```
Char(39)  or Char(39) 1 Char(39) =Char(39) 1
```

Char(42) is the asterisk.

# Additional Resources

This is just an introduction to SQL injection. If you wish to delve deeper into this, I recommend the following sites:

+   - http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet
+   - http://www.sqlinjectionwiki.com/categories/2/mysql-sql-injection-cheat-sheet/
+   - https://information.rapid7.com/rs/rapid7/images/R7%20SQL_Injection_Cheat_Sheet.v1.pdf

# XSS

Cross-site scripting (commonly called XSS) is a relatively simple attack. You attempt to load scripts into a text field so they will be executed when another user visits that site. For example, you go to a product review section, but rather than enter a review, you enter JavaScript.

Essentially you enter scripts into an area that other users interact with, so that when they go to that part of the site, you have your own script run, rather than the intended website functionality. This can include redirecting them.

Cross-site scripting exploits the trust a user has for a particular site. Cross-Site Request Forgery (CSRF), discussed in a later section, exploits the trust that a site has in a user’s browser. What can you do with this? First let’s look at a bit of basic JavaScript.

# Basic JavaScript

In order to understand cross-site scripting, you need at least some understanding of JavaScript. It is also helpful to be able to manually enter a few scripts in order to test if a target website is susceptible.

Consider this elementary JavaScript example:

```
<SCRIPT>
document.write("<H1>Hello World.</H1>")
</SCRIPT>
```

Write to an element:

```
<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>
```