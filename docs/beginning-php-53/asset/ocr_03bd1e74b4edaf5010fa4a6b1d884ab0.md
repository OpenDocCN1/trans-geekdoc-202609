# Part III: Using PHP in Practice

Next, the data is output, one record per table row:

```
<?php
$rowCount = 0;

foreach ( $members as $member ) {
$rowCount++;
?>
<tr><?php if ( $rowCount % 2 == 0 ) echo ' class="alt"' ?>>
<td><a href="view_member.php?memberId=<?php echo $member->
getValueEncoded( "id" ) ?>"><?php echo $member->
getValueEncoded( "username" ) ?></a></td>
<td><?php echo $member->getValueEncoded( "firstName" ) ?></td>
<td><?php echo $member->getValueEncoded( "lastName" ) ?></td>
</tr>
<?php
}
?>
```

For each row, the script displays the values of three fields — username, firstName, and lastName —
for the current member in individual table cells. For each cell, the Member object’s getValueEncoded ()
method is called to retrieve the appropriate field value with any special XHTML characters encoded. In
addition, the values in the username cells are linked to the view_member.php script (which you create
in a moment), passing in the ID of the member whose details should be displayed.

$rowCount is used to track the current row number. If the number is even, the table row’s CSS class is
set to alt, producing an alternating row effect as defined in the CSS in the page header.

The last section of the script produces the links to jump to the previous and next page of members:

```
<div style="width: 30em; margin-top: 20px; text-align: center;">
<?php if ( $start > 0 ) { ?>
 <a href="view_members.php?start=<?php echo max( $start - PAGE_SIZE, 0 )
?>&amp;order=<?php echo $order ?>">Previous page</a>
<?php } ?>
&nbsp;
<?php if ( $start + PAGE_SIZE < $totalRows ) { ?>
 <a href="view_members.php?start=<?php echo min( $start + PAGE_SIZE,
$totalRows ) ?>&amp;order=<?php echo $order ?>">Next page</a>
<?php } ?>
</div>
```

If the current page doesn’t begin at the start of the member list ($start > 0), the “Previous page” link
is created. This links to the same view_members.php script, passing in a new start value one page less
than the current value. (If the new start value should happen to be negative, it is set to zero.)

Similarly, if the current page isn’t the last page of the member list ($start + PAGE_SIZE <
$totalRows), the “Next page” link is created, setting start to one page greater than the current start
value (or $totalRows if start would end up being greater than $totalRows).

Notice that both links also pass through the order query string parameter, ensuring that the correct sort
order is preserved across pages.