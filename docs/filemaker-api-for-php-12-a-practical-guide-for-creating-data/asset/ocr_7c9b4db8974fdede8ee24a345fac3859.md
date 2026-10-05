seconds (since Unix Epoch on January 1, 1970).

```
$today = date('U', strtotime($record->getField('Date')));
$date = date('U', strtotime($record->getField('Date2')));
If($today <= $date) {
    echo $today "<" . $date;
} else {
    echo $today ">" . $date;
}
?>
<body>
</html>
```

![](bbox=[0.094, 0.313, 0.699, 0.555])

Figure 7-100: Five different methods to compare dates.