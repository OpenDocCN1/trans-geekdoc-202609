# Working with Date/Time and International Aspects

You can then develop appropriate view logic to display the different calendars. For example, you can include parameters to display the full month and day names:

```
<!DOCTYPE html>
<html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="content-type"
content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css"
href="php7cookbook_html_table.css">
</head>
<body>
<h3>Year: <?= $year ?></h3>
<?= $calendarFr->calendarForMonth($year, $month, NULL,
Calendar::DAY_FULL); ?>
<?= $calendarUs->calendarForMonth($year, $month, NULL,
Calendar::DAY_FULL); ?>
<?= $calendarTh->calendarForMonth($year, $month, NULL,
Calendar::DAY_FULL) ; ?>
</body>
</html>
```

![](bbox=[0.22, 0.49, 0.78, 0.74])

With a couple of modifications, you can also display a calendar for the entire year:

```
$localeTh = new Locale('th_TH');
$localeEs = new Locale('es_ES');
$calendarTh = new Calendar($localeTh);
```