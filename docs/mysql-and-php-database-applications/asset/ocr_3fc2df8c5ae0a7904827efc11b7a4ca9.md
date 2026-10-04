# Part III: Simple Applications

```
CREATE TABLE winners (
user_id int(11) NOT NULL,
weekdate datetime DEFAULT '0000-00-00 00:00:00' NOT NULL,
notify_dt datetime,
claim_dt datetime,
confirm_dt datetime
);
```

# Code Overview

If you already read the section by the same name in Chapter 8, the structure we use here should be familiar to you. Items in the /functions folder are included and ready for reuse.
It's obvious that this survey application requires several more pages than the guestbook: there's that needs to be done. Though you can include several actions in a single page, and sort those you need by passing variables and using states, it can make code difficult to keep track of. Better to have use intuitively named files that. That said, there are pages in this application that make use of variables in order to decide what action to take on a given page.
If you've done any work at all you know how it is to deal with HTML tables and forms. For that reason, in this and most of the other applications in this book, we will try to ease the pain involved in dealing with tables and forms. In the following sections you will see several functions that make life, in the long run at least, a lot easier. The functions in the coming sections will make a lot more sense if you see what they accomplish first. Here's some code that will work just if you used with the following functions.

```
print start_table()
print table_row(
    table_cell("Cell text")
)
print end_table();
```

![](bbox=[0.167, 0.743, 0.237, 0.803])

If you don't like the functions we've created for tables, forms, and other HTML elements, don't use them. It is perfectly acceptable (and perhaps even more common) to type out HTML elements, rather than create them through functions. Like many things in programming, it comes down to a matter of preference. In a case like there's no right answer:Do what you prefer.

This will create a table with one cell. You could build on the complexity of this by adding additional table_cell() calls within the table_row function call. You