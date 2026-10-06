
# Chapter 14: Manipulating MySQL Data with PHP

```php
$errorMessages[] = '<p class="error">A member with username already exists in the database. Please choose another username.</p>';

if ($existingMember = Member::getByEmailAddress($member->getValue("email address")) && $existingMember->getValue("id") != "") {
    $errorMessages[] = '<p class="error">A member with that email address already exists in the database. Please choose another email address.</p>';
}

if ($errorMessages) {
    displayForm($errorMessages, $memberFields, $member);
} else {
    $member->update();
    displaySuccess();
}
```

```php
function deleteMember() {
    $member = new Member(array(
        "id" => isset($_POST["memberId"]) ? (int)$_POST["memberId"] : "",
    ));
    LogEntry::deleteAllMember($member->getValue("id"));
    $member->delete();
    displaySuccess();
}
```

```php
function displaySuccess() {
    $start = isset($_REQUEST["start"]) ? $_REQUEST["start"] : 0;
    $order = isset($_REQUEST["order"]) ? preg_replace("/^ [a-zA-Z]-\/", "", $_REQUEST["order"]) : "username";
    displayPageHeader("Changes saved");
?>
    <p>Your changes have been saved. <a href="view_members.php?start=<?php echo $start;&order=<?php echo $order; ?>">Return to member list</a></p>
    <?php
    displayPageFooter();
?>
```

The script starts off much like before. It retrieves the supplied member ID from either the query string or form post, then looks up the member in the database by calling `Member::get()`. If the member couldn't be found, an error is displayed and the script exits. Otherwise, the member is stored in `$member`.

# Part III: Using PHP in Practice

Next, the script makes a decision about which function to call. If the Save button was clicked, deleteMember() is called to update the member record in the database. If Delete Member was clicked, deleteMember() is called to remove the member from the database. Otherwise, displayForm() is called to display the member details and access record logs. The script passes the retrieved `$member` object so that it can be displayed.

displayForm() works in a similar way to its counterpart in the register.php script created earlier in the chapter. It first retrieves the logEntry objects belonging to the member in query, and stores them in a `$logEntries` array. After displaying the page header, the function outputs any error messages at the top of the page.

Next, displayForm() retrieves the start and order parameters from the query string or the form post, and stores them in `$start` and `$order`. Then the form is displayed. The form includes three fields:

```html
<input type="hidden" name="memberId" id="memberId" value="<?php echo $member->id; ?>">
<input type="hidden" name="start" id="start" value="<?php echo $start; ?>">
<input type="hidden" name="order" id="order" value="<?php echo $order; ?>">
```

`memberId` tracks the member ID being viewed or edited, and start and order propagate their respective values from the member list page, so that the administrator can return to the same point in the member list after viewing or editing the member.

The rest of the form works like it does in register.php. Each field is displayed, using `Member::getValue()`, `setChecked()`, and `setSelected()` to retrieve the data from the member object and display it. The bottom of the form contains a Save Changes button and a Delete Member button. After the form, the access log details are displayed in the same way as the old_member.php script.

The Back link at the bottom of the form works slightly different than register.php. Because you don't know how many times the administrator has submitted the form, you can't use a JavaScript function to call back one page to the member list page, as register.php did. So instead construct a new link to view_members.php, passing in the `$start` and `$order` values as start and query string parameters, in order to return the administrator to the same point in the member list.

saveMember() checks that the data was submitted in the form and, if, updates the member record in the database. It works like `processForm()` in register.php. A New Member object is created that contains the filtered values from the form. If any fields were missing, or if the username or email is already used by another member, an error message is generated, and the form is redisplayed by calling displayForm().

If all went well, the member record is updated by calling `$member->update()`, and a success message is displayed by calling `displaySuccess()`. Note, that to the design of the `Member::update()` method, the administrator can leave the password field in order to retain the member's existing password.

deleteMember() simply creates a new Member object containing the ID stored in the form's memberId hidden field, then calls the object::delete() method to remove the member record from the members table. It also calls the `logEntry::deleteAllMember()` static method, passing the member ID, in order to delete any log entries associated with this member.

Finally, the displaySuccess() function informs the administrator that the update or delete operation was successful, and provides a link to return to the member list at the point the administrator left off. It does this by passing the start and order parameters from the form post into the query string.

# Testing the Member

You've built your member manager, now it's time to test it. Navigate to view_members.php, select the member you want to edit, and change some details. Click Save and verify that the changes were updated in the database by viewing the member list again. You can also try deleting a member and verify that they are removed from the table and that their log entries are also deleted.
