BIGNT or plain INT? Because each can store a different range of numbers. TINYINT can only store numbers between 1 and 255, which clearly isn't enough to give every member of a hotel's customer database a unique number. MEDIUMINT stores up to 16 million (or -8m to +8m if you're going to want negative numbers in there too, which we don't). And that's plenty for us. If we need to change it later, we can do so without losing data.

Firstname, surname and title can all be TINYTEXT, which allows up to 255 characters of text. The address might conceivably be too long for this, so we'll use a TEXT type, which allows up to 65,000 characters or so. Not that we'll ever use that many, and nor will MySQL require 65,000 characters of disk space for every field in the database. But the space is there for the database to be sufficiently expanded should we use it.

TINYTEXT will also suffice for the phone and email fields.

There's one more thing we need to do. Scroll the screen sideways and you'll see some more options for each field:

![](bbox=[0.13, 0.44, 0.83, 0.81])

In the "Extra" entry for the id field, and *only for this field*, choose the auto_increment option. Each time you create a new row in the table, ie a new customer record, MySQL will