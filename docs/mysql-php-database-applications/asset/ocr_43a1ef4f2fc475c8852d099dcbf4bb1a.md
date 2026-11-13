The comparison $user_email != $winner_email will work because the query that ran at the top of the page retrieved the correct winner's email, and we get $user_email from the form submitted by the user. If that comparison fails, an error message prints. If it does not fail, the following code updates the winners database, recording the time the prize was claimed, and sends an email to the winner letting him or her know that the claim was successful:

```
else
{
// everything matches. we can update the database
// to record a valid claim.
$claimquery = "update winners set claim_dt = now()
where user_id = $user_id
and claim_code = '$claim_code'
and weekday = '$weekdate'
";
my_query($claimquery);
if (mysql_affected_rows() > 0)
{
// send a notification to the administrator that
// the prize has been claimed.
$confirm_url = regular_url('admin/winners.php');
$msgtext = <<<EOQ
```

The prize for $weekdate has been claimed by $user_email.

Confirm the prize at

```
$confirm_url
EOQ;
```

```
$subject = 'Prize Claim';
$result = mail($admin_email,$subject,$msgtext);

if ($result)
{
// we don't need to re-display the form now.
// print out congratulations and bail.
$msg = <<<EOQ
```

Thanks! Your claim has been accepted.
Your prize should be on its way soon!

```
EOQ;
print paragraph($msg);
exit;
}
```