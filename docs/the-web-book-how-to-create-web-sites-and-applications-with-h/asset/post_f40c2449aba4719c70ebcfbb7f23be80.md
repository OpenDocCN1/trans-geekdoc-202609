
![](img/50e1558b8202f19b96c1cc386ea5ec66_190_0.png)

Depending on which version of phpMyAdmin your hosting company runs, and the security permissions that it applies to your account, the screen may look slightly different, but the basic structure will be the same.

On the left hand side of the screen, in the blue panel, are your databases. In the example above, there are 4. One is called information_schema, and the number in brackets tells you that it contains 21 tables. There are also databases called thewebbo_cms, thewebbo_hms, and thewebbo_rs44. In this particular case, the _rs44 one is something that I have been testing, so you can ignore it. The _cms one is a remnant of our earlier experiments with Joomla, Plogger, phpBB and the like. The _hms one is what we’re interested in right now, as this is what we’ll be using throughout the rest of this book as we build our rudimentary hotel management system.

The information_schema database is part of the inner workings of MySQL on your hosting account. Some hosts allow you to see it, whereas others don’t. If your host does, feel free to browse around it if you’re curious, but don’t change or delete any of the information in it. If you do, you face the serious risk of breaking your hosting account or at least your ability to use MySQL.

## Creating The Customers Table

The first stage in building our hotel management system is to create the "customers" table. Once we’ve done this, we’ll then use PHP to create a web site that allows hotel staff to create new customers and add them to the database. We can then use those customers to create bookings, and slowly build up our system.

Although it’s possible to write PHP code which creates database tables (assuming the hosting company doesn’t specifically block you from doing so), most web developers don’t bother. Creating the tables for your database is something that you’ll only ever do once, so you might as well let phpMyAdmin do it for you. If you make a mistake, or if you subsequently want to add new columns to the table (eg. you want to store a customer’s car registration number), phpMyAdmin allows that too.

Fire up phpMyAdmin and get to the front screen, as shown above. Click on the _hms entry in the left hand panel, to view the thewebbo_hms database. There are currently no tables in the hms database so the screen will look like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_191_0.png)

We’re interested in the "create new table on database thewebbo_hms" bit. Type the name of the table (customers) into the box. We’ll start with 7 fields, so enter that number into the box and click the Go button. You’ll see the following:

![](img/50e1558b8202f19b96c1cc386ea5ec66_192_0.png)

You now have 7 lines (one for each field) into which you can enter the field name, its type, its length, and a few other things too.

As you can see from the list of possible field types that I’ve clicked on in the top field, there are lots to choose from. It’s important that you choose the right field type for each field (column) in your table. This generally means making two decisions. First, whether or not the content of that field will be purely numeric. Because if it will be, choosing one of the numeric field types will result in a database that can be searched and indexed more efficiently. The second decision is for when you decide that the field won’t be purely numeric, but will also hold alphabetical text. In which case you need to specify the maximum length of any one field. I’ll explain more about this as we create the customers table.

The field names are going to be:

- id
- firstname
- surname
- title
- address
- phone
- email

So type those into the first column of each row on the screen. Note that we use all lower-case letters. That way, we won't have to worry about remembering whether a field is called FirstName, firstname, Firstname or FIRSTNAME when we're trying to access it later on.

Before we choose the "type" for each field, it's important to consider for a moment our choice of fields.

The "id" field exists because of our desire for normalization, as mentioned on page 183. Each time we refer to a customer within any table other than the "customers" one, we'll do so by id number rather than name.

You'll see that we've split the customer's name into 3 fields, namely firstname, surname and title. So Mr John Smith will actually be stored as a firstname of John, a surname of Smith, and a title of Mr. Why do we do it like this? Because, thinking ahead, we might want to use our hotel management system to create mailshots, and we can easily construct the first line of the mailshot by printing the word "Dear" followed by the customer's title and then their surname.

The address, phone and email fields are fairly obvious. Although, if you were creating this project "for real", you might want to consider splitting the address into 4 or 5 separate fields, and perhaps a separate one for the postcode or zip code. Why? Because you might want to create reports or mailshots based on specific postcodes, and it's much easier to search a database table by one specific field (eg, show me all the customers whose postcode starts with TN) rather than searching within a larger non-specific field (eg, show me all the customers where the letters TN appear somewhere within the address field).

Don't underestimate the value of thinking ahead in this way. When you're planning any database, the more thought and consideration you give to the way that your data is stored BEFORE you start writing code and firing up phpMyAdmin, the easier the task of creating the system will be. The decision to store a customer name in 3 separate fields is trivial to implement at this stage. If you were to go ahead with a single field called "name", then write half the system, and then decide that actually it would be better to store the name in 3 parts, it might take many days or even weeks to rewrite all the relevant parts of the system.

Anyway, back to our field creation screen. Hopefully you've typed in the 7 field names. Now to choose their types.

For the id field, choose MEDIUMINT. An INT field stores an integer, ie a whole number. You can't store text in there, and you can't store decimal numbers such as 3.5. But we'll use whole numbers for customer id's so that's fine. Why medium rather than a TINYINT or BIGNT or plain INT? Because each can store a different range of numbers. TINYINT can only store numbers between 1 and 255, which clearly isn't enough to give every member of a hotel's customer database a unique number. MEDIUMINT stores up to 16 million (or -8m to +8m if you're going to want negative numbers in there too, which we don't). And that's plenty for us. If we need to change it later, we can do so without losing data.

Firstname, surname and title can all be TINYTEXT, which allows up to 255 characters of text. The address might conceivably be too long for this, so we'll use a TEXT type, which allows up to 65,000 characters or so. Not that we'll ever use that many, and nor will MySQL require 65,000 characters of disk space for every field in the database. But the space is there for the database to be sufficiently expanded should we use it.

TINYTEXT will also suffice for the phone and email fields.

There's one more thing we need to do. Scroll the screen sideways and you'll see some more options for each field:

![](img/50e1558b8202f19b96c1cc386ea5ec66_194_0.png)

In the "Extra" entry for the id field, and *only for this field*, choose the auto_increment option. Each time you create a new row in the table, ie a new customer record, MySQL will automatically generate a new unique id number. It saves you having to manually write code to look for an unused id number.

As for all the other options, such as Attributes, Null, Default and so on, you can leave these alone. They are not required here. Typically, all you need is a field name, a field type, and possibly an auto_increment on your id field.

When you’re done, click on the Save button and you should see a summary of the table that has been created. That’s it. The job is done.

In the left hand panel, click on the database name (thewebbo_hms in this example). You will now see a list of all the tables in that database, of which there is currently just one. So click on "customers" and you’ll see the structure of the table like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_195_0.png)

Get used to this screen, as you’ll be using it a lot when you start to become a regular user of phpMyAdmin. The "structure" tab shows you the field names and types. The other tabs that we’ll use later are "browse" and "insert", which let you look at the data and create new rows.

Before we go any further, there are two fundamental things that you need to make sure you understand. First, the database and all its data resides on the web server. There’s nothing
