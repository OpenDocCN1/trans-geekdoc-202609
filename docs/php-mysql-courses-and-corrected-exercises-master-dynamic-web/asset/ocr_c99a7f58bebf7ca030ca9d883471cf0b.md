Deleting data from a database can sometimes have significant consequences. This is why it is essential to implement a confirmation mechanism before executing a deletion operation, to avoid accidental or unwanted deletions. Always ask for confirmation before carrying out a final deletion.

To addition deletion confirmation before permanently deleting the author, you can use, for example, a JavaScript dialog box to ask the user to confirm his action.
In the "display_authors.php" file, modify the delete link to call a JavaScript function that displays a confirmation dialog box:

```
echo "<td>
	<a href='delete_author.php?author_id={$author['author_id']}' onclick='return confirmDelete()'>
	Delete
	</a></td>";
```

In the deletion link of the table displaying all authors, we've integrated the onclick attribute with the value 'return confirmDelete()'. This triggers a call to the JavaScript function confirmDelete() when a user clicks on the associated element. The return keyword is used to convey the return value of this function. In this context, we'll create a new JavaScript function that we'll call confirmDelete(). This function displays a confirmation dialog to the user, inviting them to confirm whether they really wish to perform the associated action, such as deleting an element. If the user confirms, the function returns true, allowing the click event to proceed normally and execute the intended action. On the other hand, if the user cancels the confirmation, the function returns false, thus cancelling the click action and preventing any further action. It's important to note that this book doesn't focus on JavaScript, so we won't go into detail on these concepts. Next, we create the JavaScript function named "confirmDelete()" in a <script> tag, located