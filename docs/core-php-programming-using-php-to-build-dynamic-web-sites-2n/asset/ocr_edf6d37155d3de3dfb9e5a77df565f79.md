# Core PHP Programming

```
</body>
</HTML>
```

# Listing 20.9 Page Content

This is the body of the page.<BR>
It's just a bit of HTML.<BR>

# Listing 20.10 Page-Building Script

```
<?
/*
** include code to open HTML page
 */
require("20-7.html");

/*
** include content
 */
require("20-9.html");

/*
** include code to close HTML page
 */
require("20-8.html");
?>
```

In this way, HTML and PHP are separated into modules. In this example I have-coded the inclusion of a two-line HTML file, but I could as easily have included the color tables from Listing 20.2. The HTML in Listing 20.7 can be reused from page to page, and if I need to add something to every page on the site, I need to edit only one file. I might want to add the PHP function from Listing 20.1. It will then be available for use inside the code from Listing 20.9.

It may occur to you that this approach is exhibiting another pattern. Every page on the site will simply become three calls to require. The first and last calls will be the same. In every page on the site will simply vary by the name of the file included in the second require statement. This takes us beyond the issue of integrating HTML and PHP into the structural design of a site. It is possible to create a site that has exactly one PHP script. This is developed in Chapter 21, "Design."

# Creating Fields

An HTML SELECT tag allows you to list several options that appear as a pull-down menu. I am in the situation of creating the contents of the list on the fly. Sometimes the contents are pulled from a database, such as for choosing among users in a Web