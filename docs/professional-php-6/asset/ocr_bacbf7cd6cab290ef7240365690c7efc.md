# # Finishing the Iteration

Keeping in mind your newfound skills in refactoring, tackle the remaining stories with an eye toward removing duplication and making the code simpler.

# # Story 14: Changing the Week Recalls a Previous Week

Recalling state is not difficult because the ContactVisit state practically begs it. You quickly get halfway there by adding the following function to customer-contacts.php:

```
function gatherContactVisits ($dbh, $emp_id) {
	$result = $dbh->query ("select * from contact_visits where
		emp_id = ".$emp_id." and week_start = 
		'".getCurrentStartWeek()."' order by seq");
	if (DB::isError($result)) {
		return array();
	}
	$visits = array();
	while ($row =& $result->fetchRow()) {
		array_push ($visits, new ContactVisit($row));
	}
	return $visits;
}
```

You should be lazy about calling the gatherContactVisits() function because the act of recalling ContactVisits() from the database might not be required each time (for example, when ContactVisits() are being saved).

Now, assign the contact visit data by reference to ContactVisits and recall it for display like so in customer-contacts.tpl:

```
<input name="company_name_${smarty.section.idx.index}" size="20"
	maxlength="50" value="${contactVisits[idx]->company_name}">
```

You have everything except for the reload if the week is changed in the drop-down. Here is a cute trick: Drop-downs don’t normally cause submits to happen, but in this case you need to force it.

In order to force a submit, you create a hidden form with the week_start value defined in it. When the date is changed, call the JavaScript function reload, which, in turn, populates the week_start with whatever was selected. Then, “submit” it with a new action:

```
{literal}
<SCRIPT TYPE="text/javascript">
<!--
function reload () {
	window.document.forms[0].week_start.value =
		window.document.forms[1].week_start.value // hidden form
	window.document.forms[0].submit(); // hidden form
}
```