```
new Month($_GET['y'], $_GET['m'])
);
```

Finally, we call the Year's build method and pass it the array of selected months:

```
// Instruct the Year to build Month objects
$year->build($selectedMonths);
```

It's the build method that actually instructs the Calendar subclasses (with the exception of Second) to build their children. Again, this will become clear in a moment.

Next, we create two variables that we'll use to make the “next” and “previous” links, allowing users to navigate between years:

```
$prev = $_SERVER['PHP_SELF'] . "?y=" . $year->lastYear();
$next = $_SERVER['PHP_SELF'] . "?y=" . $year->nextYear();
```

Notice that we use the Year method, lastYear, to get the numeric value for the previous year, and nextYear to return the value for the coming year. Then, as we begin to build the calendar output HTML, we use thisYear to obtain the value of the current year:

```
// Start building HTML
$calendar = "<table>\n";
$calendar .=
    "<caption><a href=\"$prev\" class=\"nav\">&lt;&lt;</a> " .
    $year->thisYear() .
    " <a href=\"$next\" class=\"nav\">&gt;&gt;</a></caption>\n";
```

Note that passing the value TRUE to any method beginning with the word “this” (e.g. thisYear) will return a timestamp instead of a numeric, human-readable value. We’ll use this capability in a moment.

With the top of the calendar built, we can start to build the body using the iterator method fetch in a while loop. The fetch method returns the “children” of the class you're working with; for example, a Day returns Hours, while a Minute returns Seconds.