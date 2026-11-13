# #3: Creating Previous/Next Links

If you need to display a large number of items on a page, you may want to simplify the display by breaking it into several pages with a limited number of items per page. By doing so, you make your results easier to view and speed page-loading times.

A navigation bar gives the users control of these pages. You want a bar with Previous and Next links, as well as direct page number links. Here's a script that does it all:

```
<?php
function create_navbar($start_number = 0, $items_per_page = 50, $count) {
// Creates a navigation bar
$current_page = $_SERVER["PHP_SELF"];

if (($start_number < 0) || (! is_numeric($start_number))) {
$start_number = 0;
}

$navbar = "";
$prev_navbar = "";
$next_navbar = "";

if ($count > $items_per_page) {
$nav_count = 0;
$page_count = 1;
$nav_passed = false;

while ($nav_count < $count) {
// Are we at the current page position?
if (($start_number == $nav_count) && ($nav_passed != true)) {
$navbar .= "<b><a href=\"$current_page?start=$nav_count\\">[$page_count]</a></b>";
$nav_passed = true;
// Do we need a "prev" button?
if ($start_number != 0) {
$prevnumber = $nav_count - $items_per_page;
if ($prevnumber < 1) {
$prevnumber = 0;
}
$prev_navbar = "<a href=\"$current_page?start=$prevnumber\\">&lt;&lt;&lt;Prev - </a>";
}
}

$nextnumber = $items_per_page + $nav_count;
// Do we need a "next" button?
if ($nextnumber < $count) {
```