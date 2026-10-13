
To show what date and time MySQL currently thinks it is, you can select the `CURDATE()` and `CURTIME()` functions, which return these values. This is another example of a query that can be run without referring to a particular table.

**4.** Show the last day of the current month ![Image](graphics/circle-j.jpg):

```sql
SELECT LAST_DAY(CURDATE()),
MONTHNAME(CURDATE());
```

![Image](graphics/05_figure_46_j.jpg)

![Image](graphics/circle-j.jpg)Among the many things MySQL can do with date and time types is determine the last date in a month or the name value of a given date.

As the last query showed, `CURDATE()` returns the current date on the server. This value can be used as an argument to the `LAST_DAY()` function, which returns the last date in the month for a given date. The `MONTHNAME()` function returns the name of the current month.

***

**Tip**

The date and time returned by MySQL's date and time functions correspond to those on the server, not on the client accessing the database.

***

***

**Tip**

Not mentioned in this section or in [Table 5.4](#ch05.html#ch05table04) are `ADDDATE()`, `SUBDATE()`, `ADDTIME()`, `SUBTIME()`, and `DATEDIFF()`. Each can be used to perform arithmetic on date and time values. These can be very useful (for example, to find everyone registered within the past week), but their syntax is cumbersome. As always, see the MySQL manual for more information.

***

***

**Tip**

[Chapter 6](#ch06.html#ch06) discusses the concept of time zones in MySQL.

***

***

**Tip**

As of MySQL 5.0.2, the server will also prevent invalid dates (e.g., February 31, 2011) from being inserted into a date or date/time column.

***

#### Formatting the date and time

There are two additional date and time functions that you might find yourself using more than all of the others combined: `DATE_FORMAT()` and `TIME_FORMAT()`. There is some overlap between the two and when you would use one or the other.

`DATE_FORMAT()` can be used to format both the date and time if a value contains both (e.g., `YYYY-MM-DD HH:MM:SS`). Comparatively, `TIME_FORMAT()` can format only the time value and must be used if only the time value is being stored (e.g., `HH:MM:SS`). The syntax is

```sql
SELECT DATE_FORMAT(datetime, formatting)
```

The *formatting* relies upon combinations of key codes and the percent sign to indicate what values you want returned. **[Table 5.5](#ch05.html#ch05table05)** lists the available date- and time-formatting parameters. You can use these in any combination, along with literal characters, such as punctuation, to return a date and time in a more presentable form.

Assuming that a column called `the_date` has the date and time of `1996-04-20 11:07:45` stored in it, common formatting tasks and results would be

*   Time (11:07:45 AM)
    ```sql
    TIME_FORMAT(the_date, '%r')
    ```
*   Time without seconds (11:07 AM)
    ```sql
    TIME_FORMAT(the_date, '%l:%i %p')
    ```
*   Date (April 20th, 1996)
    ```sql
    DATE_FORMAT(the_date, '%M %D, %Y')
    ```

**Table 5.5. \*_FORMAT() Parameters**

![Image](graphics/05tab05.jpg)

#### To format the date and time

**1.** Return the current date and time as *Month DD, YYYY - HH:MM* ![Image](graphics/circle-k.jpg):

```sql
SELECT DATE_FORMAT(NOW(),'%M %e, %Y %l:%i');
```

![Image](graphics/05_figure_47_k.jpg)

![Image](graphics/circle-k.jpg)The current date and time, formatted.

Using the `NOW()` function, which returns the current date and time, you can practice formatting to see what results are returned.

**2.** Display the current time, using 24-hour notation ![Image](graphics/circle-l.jpg):

```sql
SELECT TIME_FORMAT(CURTIME(),'%T');
```

![Image](graphics/05_figure_48_l.jpg)

![Image](graphics/circle-l.jpg)The current time, in a 24-hour format.

**3.** Select the email address and date registered, ordered by date registered, formatting the date as *Weekday (abbreviated) Month (abbreviated) Day Year*, for the last five registered users ![Image](graphics/circle-m.jpg):

```sql
SELECT email, DATE_FORMAT (registration_date, '%a %b %e %Y')
AS Date FROM users
ORDER BY registration_date DESC
LIMIT 5;
```

![Image](graphics/05_figure_49_m.jpg)

![Image](graphics/circle-m.jpg)The `DATE_FORMAT()` function is used to preformat the registration date when selecting records from the `users` table.

This is just one more example of how you can use these formatting functions to alter the output of an SQL query.

***

**Tip**

In your Web applications, you should almost always use MySQL functions to format any dates coming from the database (as opposed to formatting the dates within PHP after retrieving them from the database).

***

***

**Tip**

The only way to access the date or time on the client (the user's machine) is to use JavaScript. It cannot be done with PHP or MySQL.

***

### Review and Pursue

If you have any problems with the review questions or the pursue prompts, turn to the book's supporting forum (**[www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)**).

#### Review

*   What version of MySQL are you using? If you don't know, find out now!
*   What SQL command is used to make a new database? What command is used to make a new table in a database?
*   What SQL command is used to select the database with which you want to work?
*   What SQL commands are used for adding records to a table? Hint: There are multiple options.
*   What types of values must be quoted in queries? What types of values shouldn't be quoted?
*   What does the asterisk in `SELECT * FROM` `tablename` mean? How do you restrict which columns are returned by a query?
*   What does the `NOW()` function do?
*   How do you restrict which *rows* are returned by a query?
*   How do `LIKE` and `NOT LIKE` differ from simple equality comparisons? Which type of comparison will be faster? What are the two `LIKE` and `NOT LIKE` wildcard characters?
*   How do you affect the sorting of the returned records? What is the default sorting method? How do you inverse the sort? What is the syntax for sorting by multiple columns?
*   What does the `LIMIT` clause do? How does `LIMIT` `x` differ from `LIMIT` `x`,`y`?
*   What SQL command is used to change the values already stored in a table? How do you change multiple columns at once? How do you restrict to which rows the changes are applied?
*   What SQL command is used to delete rows stored in a table? How do you restrict to which rows the deletions are applied?
*   What is an SQL alias? How do you create one? Why is an alias useful?

#### Pursue

*   If you haven't done so already, bookmark the version of the MySQL manual that matches the version of MySQL you are running.
*   Go through each of the step sequences in this chapter again, coming up with your own queries to execute (that demonstrate similar concepts as those in the steps).
*   Check out the MySQL manual pages for operators used in conditionals.
*   Check out the MySQL manual pages for some of MySQL's functions.
*   Create, populate, and manipulate your own table of data.
*   Do some more practice using functions and aliases.
*   Check out the MySQL manual pages for the various date and time types. Also check out `ADDDATE()` and other date-related functions.

## 6. Database Design

In This Chapter

[Normalization](#ch06.html#ch06lev1sec1) [166](#ch06.html#ch06lev1sec1)

[Creating Indexes](#ch06.html#ch06lev1sec2) [179](#ch06.html#ch06lev1sec2)

[Using Different Table Types](#ch06.html#ch06lev1sec3) [182](#ch06.html#ch06lev1sec3)

[Languages and MySQL](#ch06.html#ch06lev1sec4) [184](#ch06.html#ch06lev1sec4)

[Time Zones and MySQL](#ch06.html#ch06lev1sec5) [189](#ch06.html#ch06lev1sec5)

[Foreign Key Constraints](#ch06.html#ch06lev1sec6) [195](#ch06.html#ch06lev1sec6)

[Review and Pursue](#ch06.html#ch06lev1sec7) [202](#ch06.html#ch06lev1sec7)
