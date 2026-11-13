
## Introduction

```
<b>Location:</b>
<input type="text" size="40" name="location">
<br>
<b>Email:</b>
<input type="text" size="40" name="email">
<br>
<b>Home Page URL:</b>
<input type="text" size="40" name="url">
<br>
<b>Comments:</b>
<textarea name="comments" cols="40" rows="4" 
wrap="virtual"></textarea>
<br>

<input type="submit" name="submit" value="Sign!">
<input type="reset" name="reset" value="Start Over">

</form>
```

When the user fills out this form and submits it, the information is sent to create_entry.php. The first thing to do on this page is to check if the form has been submitted. If it has, take the values entered into the form and use them to create a query to send to MySQL. Don't worry about the specifics of the query just yet. Just know that it inserts a row into the database table you created earlier.

```
<?php
include("dbconnect.php");

if ($_REQUEST["submit"] == "Sign!")
{
	$query = "insert into guestbook
	(name,location,url,comments) values ('"
	.$_REQUEST["name"]
	.",'."
	.$_REQUEST["location"]
	.",'."
	.$_REQUEST["email"]
	.", '".
	.$_REQUEST["url"]
	.", '".
	.$_REQUEST["comments"]
	."')";
}

mysql_query($query);
?>
<h2>Thanks!</h2>
<h2><a href="view.php">View My Guest Book!!!</a></h2>
<?php
}
else
{
    include("sign.php");
}
?>
```

If the form, which is in sign.php, hasn't been submitted, it is included and, therefore, shows the same form. You might notice that this page is submitted to itself. The first time the create_entry.php page is called, the form in sign.php is displayed. The next time, though, the data are inserted into the database. Figures 1-2 and 1-3 show the pages that this script creates.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_41_0.png)

Figure 1-2: create_entry.php the first time through

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_42_0.png)

Figure 1-3: create_entry.php after submission

## VIEWING INFORMATION IN THE DATABASE

This shouldn't be too tough. You already know that the file needs to include dbconnect.php. Other than that, we've already mentioned that databases store information in tables. Each row of the table contains information on a specific person who signed the guestbook, so to view all the information the page needs to retrieve and print out every row of data. Here's the script that can do it (you should notice that it's pretty sparse):

```
<?php include("dbconnect.php"); ?>

<h2>View My Guest Book!!</h2>

<?php

$result = mysql_query("select * from guestbook")
        or die(mysql_error());
while ($row = mysql_fetch_array($result))
{

echo "<b>Name:</b>";
echo $row["name"];
echo "<br>\n";
echo "<b>Location:</b>";
echo $row["location"];
echo "<br>\n";
echo "<b>Email:</b>";
echo $row["email"];
echo "<br>\n";
echo "<b>URL:</b>";
echo $row["url"];
echo "<br>\n";
echo "<b>Comments:</b>";
echo $row["comments"];
echo "<br>\n";
echo "<br>\n";
echo "<br>\n";
}
mysql_free_result($result);
?>
```

```
<h2><a href="sign.php">Sign My Guest Book!</a></h2>
```

The query in the preceding code asks MySQL for every row in the database. Then the script enters a loop. Each row in the database is loaded into the variable $row, one row at a time. Rows continue to be accessed until none is left. At that time, the script drops out of the while loop.

As it works through the loop, each column in that row is displayed. For example, the following code prints out the email column for the row being accessed:

```
echo $row["email"]
```

When run, the simple script at the beginning of this section prints out every row in the database. Figure 1-4 shows what the page will look like.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_44_0.png)

Figure 1-4: view.php

And that about does it for our first application.

## WHY YOU SHOULD NOT USE THIS APPLICATION

Again, we strongly recommend against putting the application discussed in this introduction anywhere that the general public can get to it. If you want a guest-book, use the application made exclusively for this book, which you find in Chapter 8. We call this application Guestbook 2003. But we cover a lot of ground and present a lot of information before we get there.

We hope you enjoy the read!

## Part I

### Working with MySQL

CHAPTER 1
Database Design with MySQL

CHAPTER 2
The Structured Query Language for Creating and Altering Tables

CHAPTER 3
The Structured Query Language for Inserting, Editing, and Selecting Data

## Chapter 1

### Database Design with MySQL

### IN THIS CHAPTER

- Identifying the problems that led to the creation of the relational database
- Learning the normalization process
- Examining advanced database concepts

THE BULK OF THIS CHAPTER is for those of you who have made it to the early twenty-first century without working with relational databases. If you're a seasoned database pro, having worked with Oracle, Sybase, or even something like Microsoft Access or Paradox, you may want to skip this little lesson on database theory. However, we do suggest that you look at the final section of this chapter, where we discuss some of MySQL's weirder points. MySQL's implementation of SQL is incomplete, so it might not support something you want to use.

### Why Use a Relational Database?

If you're still here and are ready to read with rapt attention about database theory and the wonders of normalization, you probably don't know much about the history of the relational database. You may not even care. For that reason, I'll keep this very brief. Dr. E. F. Codd was a research scientist at IBM in the 1960s. A mathematician by training, he was unhappy with the available models of data storage, finding them all prone to error and redundancy. He worked on these problems and then, in 1970, published a paper with the rousing title “A Relational Model of Data for Large Shared Data Banks.” In all honesty, nothing has been the same since.

A programmer named Larry Ellison read the paper and started work on software that could put Dr. Codd’s theories into practice. If you've been a resident of this planet during the past 20 years, you may know that Ellison's product and company took the name Oracle and that he is now one of the richest individuals in the world. His earliest product was designed for huge mainframe systems. Responding to market demands over the years, Oracle, and many other companies that have sprung up since, have designed systems with a variety of features geared toward a variety of operating systems. Now relational databases are so common that you can get one that runs on a Palm Pilot.

To understand why Dr. Codd's theories have revolutionized the data-storage world, it's best to have an idea of what the troubles are with other means of data storage. Take the example of a simple address book – nothing too complex, just something that stores names, addresses, phone numbers, emails, and the like. If you have no persistent, running program to put this information into, the file system of whatever OS you're running becomes the natural choice for storage.

For a simple address book, a delimited text file can be created to store the information. If the first row serves as a header and commas are used as delimiters, the text file might look something like this:

| Name | Addr1 | Addr2 | City | State | Zip | Phone | Email |
|------|-------|-------|------|-------|-----|-------|-------|
| Jay Greenspan | 211 Some St | Apt 2 | San Francisco | CA | 94107 | 4155551212 | jay@not.real |
| Brad Bulger | 411 Some St | Apt 6 | San Francisco | CA | 94109 | 4155552222 | brad@not.real |
| John Doe | 444 Madison Ave. | | New York | NY | 11234 | 2125556666 | nobody@mysql.phpapps.com |

This isn't much to look at, but it is at least machine-readable. Using whatever language you wish, you can write a script that opens this file and then parses the information. You will probably want it in some sort of two-dimensional or associative array so that you'll have some flexibility in addressing each portion of each line of the file. Any way you look at it, there's going to be a fair amount of code to write. If you want this information to be sortable and queryable by a variety of criteria, you're going to have to write scripts that will, for instance, sort the list alphabetically by name or find all people within a certain area code. What a pain.

You might face another major problem if your data needs to be used across a network by a variety of people. Presumably more than one person is going to need to write information to this file. What happens if two people try to make changes at once? For starters, it's quite possible that one person will overwrite another's changes. To prevent this from happening, the programmer has to specify file locking if the file is in use. While this might work, it's kind of a pain in the neck for the person who gets locked out. Obviously, the larger the system gets the more unmanageable this all becomes.

What you need is something more robust than the file system—a program or daemon that stays in memory seems to be a good choice. Furthermore, you'll need a data-storage system that reduces the amount of parsing and scripting that the programmer needs to be concerned with. No need for anything too arcane here. A plain, simple table like Table 1-1 should work just fine.

Now this is pretty convenient. It's easy to look at and if a running program accesses this table it should happen pretty quickly. What else might this program do? First, it should be able to address one row at a time without affecting the others. That way, if two or more people want to insert information into this table they
