# Part III: A Real-World Case Study

It's a first pass, so start with how to feed the Smarty template in the file travel-expenses.php, which is the user's landing point if coming in from the main menu:

```
<?php
require_once ("lib/common.php");
require_once ("lib/expense.phppm");
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
// // display
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