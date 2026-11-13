In the case of a simple one-to-one relationship, a single table is all you'll need. An example of a one-to-one relationship that you've seen is the email address of each author in our joke database. Since there will be one e-mail address for each author, and one author for each e-mail address, there is no reason to split the addresses off into a separate table.

A many-to-one relationship is a little more complicated, but you've already seen one of these as well. Each joke in our database is associated with just one author, but many jokes may have been written by that one author. This joke-author relationship is many-to-one. I've already covered the problems that result from storing the information associated with a joke's author in the same table as the joke itself. In brief, it can result in many copies of the same data, which are difficult to keep synchronized, and which waste space. If we split the data into two tables, and use an ID column to link the two together (making joins possible as shown above), all these problems disappear.

You have yet to see a one-to-many relationship, but finding an example isn't difficult. In our database so far, we've assumed that each author only has one email address. While this may not always be the case, this is a reasonable limitation to impose since you only really need one e-mail address to get in touch with an author. You simply trust that he or she would enter their most-used email address -- or at least one that is checked regularly -- when adding him or herself to the database. If you did, however, want to support multiple email addresses, you'd be faced with a one-to-many relationship (one author may have many email addresses, but each email address belongs to exactly one author).

When someone inexperienced in database design approaches a one-to-many relationship like this one, his or her first approach is often to try to store multiple values in a single database field, like this:

| ID | Name | EMail |
|---|---|---|
| 1 | Kevin Yank | kevin@sitepoint.com, kyank@attglobal.net |
| 2 | Joan Smith | joan@somewhere.net, jsmith@else.net |

While this would work, to retrieve a single email address from the database, we'd need to break up the string by searching for commas (or whatever special character you chose to use as a separator) -- a not-so-simple and potentially time-consuming operation. Try to imagine the PHP code necessary to remove one particular email address from one particular author! In addition, you'd need to allow for much longer values in the EMail column,