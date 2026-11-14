**tip**

You could decide whether each time a user visits the same page should be reflected in the history table or not.

```
SELECT COUNT(history.id) AS num, pages.id, pages.title FROM pages,
history WHERE pages.id=history.page_id AND history.type='page'
GROUP BY (history.page_id) ORDER BY num DESC LIMIT 10
```

# Making Notes

Another added service would be allowing users to make notes on pages.
The table would be:

```
CREATE TABLE notes (
`id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
`user_id` INT UNSIGNED NOT NULL,
`page_id` MEDIUMINT UNSIGNED NOT NULL,
`note` TINYTEXT NOT NULL,
`date_created` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
PRIMARY KEY (`id`),
UNIQUE (`user_id`, `page_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

Next you add a form on each page containing just a textarea. When the form
is submitted, the information is stored in that table. On the user's viewing
history page, you could easily indicate those pages for which the user has left
notes (by performing a left outer join from the pages to the notes table). On
a specific content page, you could easily retrieve the notes a user previously
made on its content.

# Recording Favorites

To make the site easier to use, especially as you create more content, users
might appreciate being able to bookmark their favorite content. To do that for
the HTML pages is simple. First, create a table defined like so:

```
CREATE TABLE favorite_pages (
`user_id` INT UNSIGNED NOT NULL,
`page_id` MEDIUMINT UNSIGNED NOT NULL,
`date_created` TIMESTAMP NOT NULL,
PRIMARY KEY (`user_id`, `page_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

This is a junction table, used to manage the many-to-many relationship
between users and pages. It has only three columns and the first two together
constitute the primary key (that is, it's a compound primary key). Each favorite
for each user will represent one record in this table.