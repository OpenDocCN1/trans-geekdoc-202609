The following is one possible format for comments at the beginning of each program:

```
/*  name:          catalog.php
    description:  Program that displays descriptions of
                  products. The descriptions are stored
                  in a database. The product descriptions
                  are selected from the database based on
                  the category the user entered into a form.
    written by:   Lola Designer
    created:      2/1/02
    modified:     3/15/02
*/
```

You should use comments throughout the program to describe what the program does. Comments are particularly important when the program statements are complicated. Use comments such as the following frequently:

```
/* Get the information from the database */
/* Check whether the customer is over 18 years old */
/* Add shipping charges to the order total */
```

PHP also has a short comment format. You can specify that a single line is a comment by using the pound sign (#) or two forward slashes (//) in the following manner:

```
# This is comment line 1
// This is comment line 2
```

You can also use # or // in the middle of a line to signal the beginning of a comment. PHP will ignore everything from the # or // to the end of the line. This is useful for commenting a particular statement, as in the following example:

```
$average = $orderTotal/$nItems  // compute average price
```

Sometimes you really want to emphasize a comment. The following format makes a comment very noticeable:

```
###################################
## Double-Check This Section   ##
###################################
```

PHP comments are not included in the HTML code that is sent to the user's browser. The user does not see these comments.

Use comments as often as necessary in the script to make it clear. However, using too many comments is a mistake. Don't comment every line or everything that you do in the script. If your script is too full of comments, the really important comments can get lost in the maze. Only use comments to label sections and to explain code that is unusual or complicated — not code that is obvious.