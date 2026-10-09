Here is another example, an event that occurs on the first of every month until September 2017:

```
$title = 'Pay Rent';
$description = 'Sent rent check to landlord';
$startDate = new DateTime('2016-02-01');
$event = new Event($title, $description, $startDate,
    Event::INTERVAL_MONTH, '2017-09-01', NULL, Event::FLAG_FIRST);
$calendarEs->addEvent($event);
```

You can then add sample weekly, bi-weekly, monthly, and so on events as desired. You can then close the try...catch block, and produce suitable display logic:

```
} catch (Throwable $e) {
$message = $e->getMessage();
}
?>
<!DOCTYPE html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css" href="php7cookbook_html_table.css">
</head>
<body>
<h3>Year: <?= $year ?></h3>
<?= $calendarEs->calendarForYear($year, 'Europe/Berlin',
  Calendar::DAY_3, Calendar::MONTH_FULL, 2); ?>
<?= $calendarEs->calendarForMonth($year, 1 , 'Europe/Berlin',
  Calendar::DAY_FULL); ?>
</body>
</html>
```