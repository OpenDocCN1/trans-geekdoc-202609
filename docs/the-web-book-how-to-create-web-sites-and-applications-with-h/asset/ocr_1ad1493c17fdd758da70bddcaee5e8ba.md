automatically generate a new unique id number. It saves you having to manually write code to look for an unused id number.

As for all the other options, such as Attributes, Null, Default and so on, you can leave these alone. They are not required here. Typically, all you need is a field name, a field type, and possibly an auto_increment on your id field.

When you’re done, click on the Save button and you should see a summary of the table that has been created. That’s it. The job is done.

In the left hand panel, click on the database name (thewebbo_hms in this example). You will now see a list of all the tables in that database, of which there is currently just one. So click on "customers" and you’ll see the structure of the table like this:

![](bbox=[0.12, 0.38, 0.82, 0.75])

Get used to this screen, as you’ll be using it a lot when you start to become a regular user of phpMyAdmin. The "structure" tab shows you the field names and types. The other tabs that we’ll use later are "browse" and "insert", which let you look at the data and create new rows.

Before we go any further, there are two fundamental things that you need to make sure you understand. First, the database and all its data resides on the web server. There’s nothing