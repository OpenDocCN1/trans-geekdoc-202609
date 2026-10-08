# Core PHP Programming

![](bbox=[0.235, 0.107, 0.642, 0.316])

<<?

```
$UserName = "Leon";
$Today = date('1 F d, Y\');
$CostOfLunch = 3.50;
$DaysBuyingLunch = 4;
```

?<HTML>

```
<HEAD>
<TITLE>Listing 1-3</TITLE>
</HEAD>
<body>
Today's Date:
```

```
<?
/*
** print today's date
*/
print("<H3>$Today</H3>\n");

/*
** print message about lunch cost
*/
print("$UserName, you will be out $ ");
print("$CostOfLunch * $DaysBuyingLunch);
print(" dollars this week.<BR>\n");
```

```
?>
</BODY>
</HTML>
```

The first block of PHP code puts values into some variables. The four variables are UserName, Today, CostOfLunch, and DaysBuyingLunch. knows they are variables because they are preceded by a dollar sign ($). The first time you use a variable in a PHP

IT-SC book 34