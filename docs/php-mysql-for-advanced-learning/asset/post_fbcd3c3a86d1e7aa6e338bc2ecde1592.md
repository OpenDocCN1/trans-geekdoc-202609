
A CMS like WordPress uses the MySQL database to store and retrieve data to dynamically generate webpages.

A database is not required if you plan to run a static website without using any CMS or PHP language.

## Server Control and Access

Many hosts out there won’t give a Web developer full access and/or control over their hosted domain.

We tend to shy away from those hosts because you are more likely to run into problems with them when you want to do some custom configuration to the server.

Look into the type of access your host provides. Obviously, your host will give you FTP access so you can upload your files to the Web server. Some hosts, however, will give you FTP access but nothing else.

The problem is that you are likely to run into a situation in which you want to configure your server. For this you will need either telnet or SSH access to use the command line.

In fact, the ability to configure is often necessary when performing tasks that usually aren’t allowed by hosts by default. For example, consider htaccess. With htaccess, you can deny and allow access to certain files and directories based on the users you allow in the htpasswd file

![](img/9ab4a56a650535285811bb802190e58f_183_0.png)

## Administration GUIs

Certain hosts offer Administration GUIs (Graphical User Interfaces) or User Control Panels as a feature of their packages. A lot of people don’t really care for GUIs, but when you don’t have a choice, either because you don’t have sufficient access to the server or you don’t fully understand how to get things done through telnet, a point-and-click solution is a wonderful tool.

The interface can be as simple as one that allows you to view information about the server, or it can be as complex as one that allows you to install applications and programming languages with the click of a button. Also, keep in mind that if you have a client that wants to be able to administer its e-mail users, many of the control panels have utilities that allow the client to do so themselves. With such a feature, rather than having to call you or
the hosting company to set up an e-mail account, the client can simply log on to the control panel and set up and delete users as the need arises.

## Notes

## Notes

## PHP Pagination

When we display large amount of content on the same page then we start thinking about adding pagination because loading all data on the same page is not the right choice in terms of optimization. So we split all our content to several pages. And in this case – each page contain some part of our information. And we can just use server-side as well as client side pagination using javascript and PHP to manage with our pages.

It’s always possible that your SQL SELECT statement query may result into thousand of records. But it is not good idea to display all the results on one page. So we can divide this result into many pages as per requirement.

Paging means showing your query result in multiple pages instead of just put them all in one page.

### A simple example to fetch records using LIMIT to generate paging

```
<?php

include 'dbconnectivity.php';

// to check if page url already contain page number like
test.php?pageNum=2

if (isset($_GET['pageNum']))

{

$pageNum = $_GET['pageNum'];

} else
{
    // if no pageNum variable exist in url then set pageNum variable to page 1
    $pageNum = 1;
}

// place your query here
$query=mysql_query("select * from imageslave");

$resultRows = mysql_num_rows($query);

// Set number of Records per page
$rowsPerPage = 4;

/* Calculate how many pages to be generate example if you have 20 record and you want to display 4 pages each page then last page will be 5. ( 20/4 =5 )*/
$lastPage = ceil($resultRows/$rowsPerPage);

// set page position to beginning or at the end of the page
if ($pageNum > $lastPage)
{
    $pageNum = $lastPage;
}
    else if ($pageNum < 1)
{
$pageNum = 1;
}
while($row =mysql_fetch_assoc($query))
{

// display data fields here
echo $row['fname'];
echo " " .$row['lname']."<br>";
}
echo "<br><br>";

// Display links of Next / Prev Page
if ($pageNum > 1)
{
    $prevPage = $pageNum-1;
    echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=1'>FIRST</a> ";
    echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$prevPage'>PREVIOUS</a> ";
}
echo "Page $pageNum of $lastPage ";
if ($pageNum < $lastPage)
{

$nextPage = $pageNum+1;

echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$nextPage'>NEXT</a> ";

echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$lastPage'>LAST</a>" ;

}

?>
```

## Notes

## **Bootstrap – Framework**

Bootstrap is a free and open-source CSS framework directed at responsive, mobile-first front-end web development. It contains CSS- and (optionally) JavaScript-based design templates for typography, forms, buttons, navigation, and other interface components. *(Source: Wikipedia)*

Originally named Twitter Blueprint, was developed by **Mark Otto and Jacob Thornton** at **Twitter** as a framework to encourage consistency across internal tools.

**Installation Guide:** You can visit getbootstrap.com to download the latest version of bootstrap. After downloading the setup you need to unzip or extract it. You will get three directories as below

- **CSS** – Contain required css files example – bootstrap.min.css, bootstrap-theme.css etc
- **Fonts** - Contain ttf and otf files for additional fonts
- **JS** - Contain required JS Files – example – bootstrap.min.js, npm.js etc.

### **Sample Code: Installing Bootstrap**

```
<!DOCTYPE html>

<html lang="en">

  <head>

    <meta charset="utf-8">

    <meta http-equiv="X-UA-Compatible" content="IE=edge">

    <meta name="viewport" content="width=device-width, initial-scale=1">

<title>Bootstrap 101 Template</title>
<link href="css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
// Your HTML code goes
</body>
</html>
```

## Some Major Classes available in Bootstrap 3

### .container

- sets fixed width to an element (which changes depending on a screen size to other fixed values, so it's still responsive) on all screen sizes except xs - on xs, the width is calculated automatically (this behaviour can be changed)
- a fixed width responsive website should be wrapped in .container (or just the content without menu, whatever - it's up to you)
- .container can't be nested!

### .container-fluid

- sets 100% width, margin-left and margin-right: auto, padding-left and padding-right: 15px
- a full screen website should be wrapped in .container - fluid
- .container-fluid can't be nested!

### .row

- creates horizontal groups of columns (which usually have width classes, see below)
- must be within .container to ensure correct padding and alignment
- only columns (block elements with width classes) may be immediate children of rows
- sets margin-left and margin-right: -15px

### .pull-right

### .pull-left

- sets float to either left or right

### .center-block

- sets margin-left and margin-right to auto

## Bootstrap Grid Classes

- can be nested, the nested columns must be wrapped in .row as well
- all columns have float: left and position: relative styles

### .col-xs-1 .col-xs-2 .col-xs-3 .col-xs-4 .col-xs-5 .col-xs-6 .col-xs-7 .col-xs-8 .col-xs-9 .col-xs-10 .col-xs-11 .col-xs-12

- sets width of a column (specified in %) on extra small screens (<768px)

### .col-sm-1 .col-sm-2 .col-sm-3 .col-sm-4 .col-sm-5 .col-sm-6 .col-sm-7 .col-sm-8 .col-sm-9 .col-sm-10 .col-sm-11 .col-sm-12

- sets width of a column (specified in %) on small screens (≥768px)

### .col-md-1.col-md-2.col-md-3.col-md-4.col-md-5.col-md-6.col-md-7.col-md-8.col-md-9.col-md-10.col-md-11.col-md-12

- sets width of a column (specified in %) on medium size screens (≥992px)

### .col-lg-1.col-lg-2.col-lg-3.col-lg-4.col-lg-5.col-lg-6.col-lg-7.col-lg-8.col-lg-9.col-lg-10.col-lg-11.col-lg-12

- sets width of a column (specified in %) on large screens (≥1200px)
- sets offset (margin-left) by specified number of columns (eg. set .col-sm-offset-3 class to a column to move it by three columns on small screens)

### .col-xs-pull-* (.col-xs-pull-1, .col-xs-pull-2 ... up to -12)
.col-sm-pull-* (.col-sm-pull-1, .col-sm-pull-2 ... up to -12)
.col-md-pull-* (.col-md-pull-1, .col-md-pull-2 ... up to -12)
.col-lg-pull-* (.col-lg-pull-1, .col-lg-pull-2 ... up to -12)

- sets left position in % as it is with columns (e.g. left: 75% with -pull-9)

## Bootstrap Visibility Classes

- you can apply all as many of these classes on a single element as you wish and this mixing gives you even more possibilities for your layout

### .clearfix

- obvious, clear: both
- often combined with classes below
