# FIGURE 15.10 Output from multiple tables

![](bbox=[0.095, 0.07, 0.79, 0.405])

# 15.7 Inserting, deleting and amending records

# Inserting records

All of our examples thus far have illustrated reading and displaying database information. It is now time to examine how we can create new database records. To do this we need to introduce a new SQL statement, the INSERT INTO statement which looks like this:

```
INSERT INTO table (field1, field2, . . . ) VALUES ('value1', 'value2', . . . )
```

With the above statement the name of the table into which we are going to insert some data is specified after the INSERT INTO keywords. Next, each of the table field names into which we are going to insert are specified, separated by commas and enclosed in parentheses. Following this, the keyword VALUES is followed by the values to be placed in the field names, also separated by commas and enclosed in parentheses.

The above statement looks a little complex, however, we are able to simplify it a little like so:

```
INSERT INTO table VALUES ('value1', 'value2', . . . )
```

The above INSERT INTO statement inserts the provided values into each database field in the order in which they have been provided. The following script provides an example of this:

```
<?php
// File: example15-15.php
require_once("database2.php");
```