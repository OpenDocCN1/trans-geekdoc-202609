
However, every other test sets cash_advance to zero. What happens if you remove cash_advance
from the test? It breaks! This is because PersistableObject blindly creates SQL based on every field of
the database record.

Modify the persistence test to reflect that neither cash_advance nor comments is required:

```
function testTravelExpenseWeekPersistence() {
	$this->session->getDatabaseHandle()->query("delete FROM
travel_expense_week WHERE emp_id = 1 and
week_start = '1980-01-01'"); // remove multiples

	$tvi = new TravelExpenseWeek (
	array ('emp_id' => "1",
		'week_start' => "1980-01-01",
		'territory_worked' => "Midwest",
		'mileage_rate' => "0.31"));
	$this->session->getDatabaseHandle();

	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");

	$this->assertEquals(0, $result->numRows (), "pre check");
	$this->assertEquals (true, $tvi->persist (), "save");
	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");
	$this->assertEquals(1, $result->numRows (), "persisted ok");
	$row = $result->fetchRow();
	$this->assertEquals (0.0, (float) $row['cash_advance'],
	"cash advance default");
}
```

The default values of cash_advance are an easy fix, too. Just modify the constructor of
TravelExpenseWeek to set the default of zero and an empty string:

```
class TravelExpenseWeek extends PersistableObject {
function __construct ($results, $dbh = null) {
$this->contentMetaTable = "travel_expense_week";
$this->contentMetaOnly = array ("emp_id",
"week_start",
"comments",
"territory_worked",
"cash_advance",
"mileage_rate");

$this->contentBase['comments'] = "";
$this->contentBase['cash_advance'] = "0.0";
	parent::__construct ($results, $dbh);
}
```

## Part III: A Real-World Case Study

The tests are again passing, which means that you’re done now, right? Doing a quick “grep to-do” uncovers this nagging problem:

```
/**
* todo: will this fail on daylight savings time?
*/
public function addDays($start, $days) {
 return date("Y-m-d", strtotime($start)+$days*86400);
}
```

Looking at it again, you decide there may indeed be an issue. Daylight Saving Time ends on the last Sunday in October in most places in the United States, which means that the clocks are set back, and there are more than 86,400 seconds during that day. Write up a test to confirm that it fails:

```
function testDaylightSavingTime() {
 $tw = new TravelExpenseWeek (array());
 $this->assertEquals("2004-10-30", $tw->addDays("2004-10-29", 1));
 $this->assertEquals("2004-10-31", $tw->addDays("2004-10-29", 2));
 $this->assertEquals("2004-11-01", $tw->addDays("2004-10-29", 3, "no DST"));
}
```

Sure enough, there is a problem. Adding three days to October 29 should land in November, rather than October 31, twice. Reading up on your functions, strtotime() can do the date math for you by accepting date offsets. Recode the addDays() function of PersistableObject without the presumption of seconds per day:

```
public function addDays($start, $days) {
 return date("Y-m-d", strtotime($start." + ".$days." days"));
}
```

Because your remaining “to-do” of modifying the getExpenseAmount function is really an optimization, it can wait until later. There is no need for pre-optimization, and it’s important that you keep the momentum going.

Although that was indeed a lot of work, you now have reasonably well-written, persistable objects that are completely backwardly compatible. Your system is growing in stages, and you’ll update Contact and ContactVisit the next time you touch them. Now it’s time to turn to finish the current task of the Travel Expense Report.

### The Finalized Travel Expense Report

After a few hours of work, you have what is shown in Figure 19-9.

### Widget World

### Travel Expense Report

Employee Name: Ed Locky-Thompson
Number: 1
Territory Worked: worked
Department: sales
Start Week: 2004-07-04

| | Sun | Mon | Tues | Wed | Thur | Fri | Sat | Total |
|---|---|---|---|---|---|---|---|---|
| Lodging | | | | | | | | |
| Lodging & Hotel | 1.00 | 2.00 | 3.00 | | | | | |
| Other | 2.00 | | | | | | | |
| Tips | 3.00 | | | | | | | |
| Lodging Total | | | | | | | | |
| Meals | | | | | | | | |
| Breakfast | 4.00 | | | | | | | |
| Lunch & Snacks | 5.00 | | | | | | | |
| Dinner | 6.00 | | | | | | | |
| Tips | 7.00 | | | | | | | |
| Entertainment | 8.00 | | | | | | | |
| Meals Total | | | | | | | | |
| Transportation | | | | | | | | |
| Airfare | 9.00 | | | | | | | |
| Auto Rental | 10.00 | | | | | | | |
| Auto Maint./Gas | 11.00 | | | | | | | |
| Local Transportation | 12.00 | | | | | | | |
| Tolls/Parking | 13.00 | | | | | | | |
| Transportation Subtotal | | | | | | | | |
| Nbr of miles traveled | 19.00 | | | | | | | |
| Miles at 0.36 / mile | | | | | | | | |
| Transportation Total | | | | | | | | |
| Miscellaneous | | | | | | | | |
| Gifts | 14.00 | | | | | | | |
| Telephone & Fax | 15.00 | | | | | | | |
| Supplies | 16.00 | | | | | | | |
| Postage | 17.00 | | | | | | | |
| Other | 18.00 | | | | | | | |
| Miscellaneous Total | | | | | | | | |

Subtotal
Less Cash Advance 20.00
Due Employee
Due Company

Comments:
comment

Submit Report

Logout

For Widget World use only - testing environment.

Figure 19-9: Finished Travel Expense form

It's a first pass, so start with how to feed the Smarty template in the file travel-expenses.php, which is the user's landing point if coming in from the main menu:

```
<?php
require_once ("lib/common.php");
require_once ("lib/expense.php");
// is the user logged in?
if (!($session->isLoggedIn()) {
    redirect ("index.php");
}

$user = $session->getUserObject();
$week = new TravelExpenseWeek (
    array ('emp_id' => $user->id,
        'week_start' => getCurrentStartWeek(),
        'territory_worked' => $_REQUEST["territory_worked"],
        'comments' => $_REQUEST["comments"],
        'cash_advance' => $_REQUEST["cash_advance"],
        'mileage_rate' => $GLOBALS["expense-mileage-travelrate"]),
    $session->getDatabaseHandle());
```

```
// display
if ($_REQUEST["action"] != "persist_expense") {
    $week->readWeek();
    $smarty->assign_by_ref ("user",
        $user);
    $smarty->assign_by_ref ("week",
        $week);
    $smarty->assign('start_weeks',
        getStartWeeks());
    $smarty->assign('current_start_week',
        getCurrentStartWeek());
    $smarty->assign_by_ref ('expenses',
        $week->getExpensesMetaArray());
    $smarty->assign('travelrate',
        $GLOBALS["expense-mileage-travelrate"]);
    $smarty->display('travel-expenses.tpl');
    exit();
}
```

```
// gather and persist week
$week->parse($_REQUEST);
$week->persist();
print "saved, thanks";
?>
```

Being the user-accessible landing spot, this script has two modes of operation: one is displaying the travel expenses by reading them from the database (readWeek), and the other is saving the form data (persist) based on whether the action is set to persist_expense.

As usual, your very interesting getExpensesMetaArray() is the cornerstone of the screen, and is passed in as the Smarty variable expenses. Note that all heavyweight objects are passed to Smarty by reference, so copies aren't automatically created.

Now for the basic Smarty template that displays the travel expense page, which is in templates/travel-expenses.tpl:

```
{include file="header.tpl" title="Widget World - Travel Expenses"}
{literal}
<SCRIPT TYPE="text/javascript">
<!--
function reloadCalc () {
    window.document.forms[0].week_start.value =
    window.document.forms[1].week_start.value // hidden form
    // window.document.forms[0].submit(); // hidden form )
-->
</SCRIPT>
{/literal}
<h3>Travel Expense Report</h3>
<form method="post">
<input type="hidden" name="action" value="reload_expense">
<input type="hidden" name="week_start" value="">
</form>
<form id="calc" name="calc" action="travel-expenses.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td>
<td>({$user->first_name}) {$user->last_name}</td> <td><b>Department:</b></td>
<td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td>
<td>{$user->id}</td> <td><b>Start Week:</b></td>
<td><SELECT NAME="week_start" onchange="reloadCalc()">{html_options
values=$start_weeks output=$start_weeks selected=$current_start_week}
</SELECT></td>
</tr>
<tr>
<td><b>Territory Worked:</b></td>
<td colspan=3><input name="territory_worked" size=20 maxsize=60 value =
"{$week->territory_worked}"></td>
</tr>
</table>
<br><br>
```

The first form on the page is similar to that of the Customer Contact Report, in which you utilized a special “hidden” form that was populated (by JavaScript) with the value for your starting week. The form was then automatically submitted when a new week was selected.

The start of the second form simply contains some of the basic information that you are collecting, including the territory_worked.
