As we've seen, these administration pages must be protected by an appropriate access restriction scheme. One way to do this would be to place the relevant PHP files into a directory that was protected by an Apache-style .htaccess file that listed authorized users. Consult your Web server's documentation for information on how to restrict access to Web pages.

Since we'll work with some fairly large PHP files in this part, it'll be necessary to gloss over some of the details, due to space constraints. The complete code of all the files discussed in this chapter, which, together with the SQL code you'll need to create the database tables from scratch, will form a complete content management system, is provided in the code archive (located at http://www.sitepoint.com/books/).

# The Front Page

As of the end of Chapter 5, your database contained tables for three types of entities: jokes, authors, and joke categories. This database layout is represented in the diagram shown here. Note that we're sticking with our original assumption that we'll have one email address per author.

![](bbox=[0.05, 0.42, 0.97, 0.77])

The front page of the content management system, therefore, will contain links to pages that manage each of these three things: