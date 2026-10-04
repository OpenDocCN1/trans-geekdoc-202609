# admin_get_winner.php

Most of this file is readable. Your goal is to draw a qualified winner at random from the database. First you use the weekstart function (discussed earlier in this chapter in the section "Functions and code from /book/survey/header.php") to get the date that the current week begins.

```
$qweekdt = weekstart($weekdate);
list($thisweek) = mysql_fetch_array(safe_query("select $qweekdt"));
print subtitle("Draw a winner for the week of $thisweek");
```

You then create a query that will qualify. As you can see, we've decided in addition to signing in the last week, you need to have entered a name and an e-mail address, and a legitimate age.

```
$query = "select name, email, user_id from users
where (create_dt) = week('$thisweek')
and year(create_dt) = year('$thisweek')
and name is not null and name != ''
and email is not null and email != '' and email like
'%%%%'
and age > 0
and country is not null and country != '";

$result = safe_query($query);
$tot = mysql_num_rows($result);
```

With the total number of qualified entrants in hand, the script makes a couple of decisions to determine a winner. First it needs to account for occasions when there are no possible winners.

```
if($tot ==0)
{
  echo "There were no entrants this week";
}
```

We already ran a query that has the potential winners. The first row in the result set is row number zero. If there's only one possible winner, row 0 is the only row returned.

```
else
{
  if($tot == 1)
{
    // if there's only one entry, they win.
```