# Create Self-updating Form Fields for Date Selection

```
(int)$_POST['year'] <= 2010)) {
    $year = (int)$_POST['year'];
} else {
    $year = date('Y');
}
?>
<form method="post" action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <select name="day"><?php
    $maxdays = date('t', mktime(12, 0, 0, $month, 1,
        $year));
    for ($i = 1; $i <= $maxdays; $i++) {
        if (isset($_POST['day']) && $_POST['day'] ==
            $i) {
            $sel = ' selected';
        } elseif ($i == date('j')) {
            $sel = ' selected';
        } else {
            $sel = '';
        }
        echo "<option value=\"$i\"$sel>$i</option>\n";
    }
?></select>
    // ...
</form>
```

The Date Selection Updates Itself Automatically
(dateselection-js.php; excerpt)