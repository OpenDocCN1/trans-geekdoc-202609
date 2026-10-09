```
$calendarEs = new Calendar($localeEs);
$year = 2016;
echo $calendarTh->calendarForYear($year);
echo $calendarEs->calendarForYear($year);
```

Here is the browser output showing a full year calendar in Spanish:

![](bbox=[0.2, 0.25, 0.8, 0.58])

# See also

+   > For more information on codes used by `IntlDateFormatter::setPattern()`, see this article: `http://userguide.icu-project.org/formatparse/datetime`

# Building a recurring events generator

A very common need related to generating a calendar is the scheduling of events. Events can be in the form of one-off events, which take place on one day, or on a weekend. There is a much greater need, however, to track events that are *recurring*. We need to account for the start date, the recurring interval (daily, weekly, monthly), and the number of occurrences or a specific end date.