# Chapter 7: Writing Organized and Readable Code 169

(category_id, product)
values($category_id, '$product')
);

![](bbox=[0.186, 0.196, 0.256, 0.246])

We've heard stories of database engines refining to process queries, like the ones above, that have newlines in them. This is not a problem with MySQL and won't be a problem with most databases. However, there are other acceptable ways to write queries. Here are a couple of examples:

```
$query = "select col_1, col2 "
$query = "from table_1, table_2 "
$query = "where col_1 = $var";
or:
$query = "select col_1, col_2 "
  "from table_1, table_2 "
  "where col_1 = $var";
```

Choose whichever you like.

# Includes

Every language has a facility for including external files. PHP has four commands that accomplish this. Before we get to those, we will briefly discuss why includes are so critical for writing organized and readable code. We'll start with a very common example.

In Web sites, header information will vary very little from page. There are opening tags (<HTML>, <HEAD>, etc), and perhaps some navigation information. The following is a typical header to an HTML page.

```
<HTML>
<HEAD>
<TITLE>My Page Name</TITLE>
</HEAD>
<body bgcolor="#FFFF" link="#8e0402" vlink="#20297c">
```

It would be an absolute waste to type this text into every file within a Web site. Moreover, it could be a real pain. Say you wanted to change the bgcolor attribute of the <body> tag throughout the site. If this information were hard-coded in every file, you would have no choice but to go into each file individually and make the change, or write a script that would do it for you.