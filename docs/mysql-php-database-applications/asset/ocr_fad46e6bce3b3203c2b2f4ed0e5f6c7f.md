there are other perfectly acceptable ways to write queries that do not put newlines in the queries,yet show indenting to the reader. Here are a couple of examples using the concatenation operators:

```
$query = "select col_1, col2 ";
$query .= " from table_1, table_2 ";
$query .= " where col_1 = $var";
or
$query = "select col_1, col2 "
 . " from table_1, table_2 "
 . " where col_1 = $var"
;
```

Choose whichever you like best.

# Includes

Every language has a facility for including external files. PHP has four commands that enable you to do this. Before we get to those, we briefly discuss why includes are so critical for writing organized and readable code. And we start with a very common example.

In most Web sites, header information varies little from page to page. There are opening tags (<HTML>, <HEAD>, and so on) and perhaps some navigation information. The following is a typical HTML-page header:

```
<HTML>
<HEAD>
<TITLE>My Page Name</TITLE>
</HEAD>
<body bgcolor="#FFFFFF" link="#8E0402" vlink="#20297C">
```

It is an absolute waste to type this text into every file within a Web site. Moreover, it can be a real pain. Suppose you want to change the bgcolor attribute of the <body> tag throughout the site. If this information were hard-coded in every file, you would have no choice but to either go into each file individually and make the change or write a script to do it for you.

You are far better off keeping all of this information in a single file (maybe called header.php) and then using a command that spits the contents of that file into the file being accessed. For this, you can use one of the PHP functions discussed in the next section. For this example we use include().