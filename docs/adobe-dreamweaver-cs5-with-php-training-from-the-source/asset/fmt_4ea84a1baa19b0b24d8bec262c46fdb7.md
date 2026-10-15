
4. Select the “First name” text field in Design view. Open the Bindings panel, and select `first_name` in the `getUser` recordset. Make sure that “Bind to” at the bottom of the Bindings panel is set to `input.value` (this should happen automatically), and click Bind.

![Image](graphics/fig06_44.jpg)

This inserts a dynamic text object for `first_name` in the text input field.

![Image](graphics/tip.jpg)**TIP:**

If you’re good at dragging and dropping, you can drag the value from the Bindings panel and drop it on the text input field in Design view. Dreamweaver automatically binds the dynamic text object to the `value` attribute of the `<input>` tag.

5. Repeat step 4 with the “Family name” and Username text fields, selecting `family_name` and `username` in the Bindings panel respectively. You should now have dynamic text objects in the first three text fields.

![Image](graphics/fig06_45.jpg)

6. Save update_user.php, and switch to user_list.php.

7. Launch Live View. Hold down the Ctrl/Cmd key, and click one of the EDIT links. You should see the update form with the first three fields populated from the database.

![Image](graphics/fig06_46.jpg)

Notice that the Address field in the Browser Navigation Bar displays the query string with the `user_id` at the end of the URL.

8. Turn off Live View. If everything is OK so far, you’re ready to apply the Update Record server behavior in the next section.

You can compare your code with lesson06/completed/update_user01.php.

#### Using the Update Record server behavior

Using the Update Record server behavior is very similar to the Insert Record server behavior. However, you’ll need to do some hand coding to handle the password. If nothing is entered in the Password text field, you need to use the existing value. Otherwise, you encrypt the new one and use that.

1. You need to store the value of the primary key in the form so that the Update Record server behavior knows which record to update.

With update_user.php open in Design view, position the insertion point anywhere inside the form, and choose Insert > Form > Hidden field.

2. In the Property inspector, change the name of the hidden field to `user_id`. Then click the lightning bolt icon next to Value to open the Dynamic Data dialog box.

3 Select `user_id` from the `getUser` recordset in the Dynamic Data dialog box, and click OK. This is the same procedure you used before when creating the query string for the EDIT and DELETE links.

4. Click the plus button in the Server Behaviors panel, and choose Update Record to open the Update Record dialog box.

You need to use the `cs5write` connection, and select the `users` table. As with the Insert Record server behavior, you need to set the `family_name` column to get its value from `FORM.surname`.

The important difference is that the Update Record server behavior picks up the primary key from the hidden form field. Select `user_id` in the Columns section, and check that it selects the record using `FORM.user_id`.

Set “After updating, go to” to user_list.php.

Check that the values match the following screen shot, and click OK.

![Image](graphics/fig06_47.jpg)

It’s a good idea to save the page at this point in case you make a mistake in the following steps.

5. Switch to Code view, and cut the following lines of code to your clipboard. Use the line numbers in the screen shot only as a guide. The code might be in a slightly different location in your page.

![Image](graphics/fig06_48.jpg)

This is the code created by the Recordset server behavior. It needs to come before the Update Record server behavior code, because you need the value of the `password` column in case it is to be reinserted in the database.

6. Scroll up to the following location, and paste the code on the blank line between the closing curly brace and the line beginning `$editFormAction`.

![Image](graphics/fig06_49.jpg)

7. Insert a blank line after the code you just pasted, and add the following:

if (isset($_POST['password']) && empty($_POST['password'])) {  
  $_POST['password'] = $row_getUser['password'];  
} else {  
  $_POST['password'] = sha1($_POST['password']);  
}

This conditional statement starts by checking if `$_POST['password']` has been set. If it has, it means the update form has been submitted. If the field was left empty, the value already stored in the database is reassigned to `$_POST['password']`. But if the field isn’t empty,

`$_POST['password']` is encrypted before being reassigned to the same variable. This ensures that the correct value is passed to the Update Record server behavior code.

8. Save update_user.php, and test it by launching user_list.php.

Click the EDIT link for the user you created before encrypting passwords, and update the user’s password.

9. If you check in phpMyAdmin, you’ll see that the password has now been encrypted. Test the username and password in login.php, and you should be able to log into members_only.php.

A working update form is in lesson06/completed/update_user.php.

#### Using the Delete Record server behavior

By default, the Delete Record server behavior assumes you just want to delete the selected record without asking for confirmation. This seems a foolhardy approach, because there’s no way to recover a record once it has been deleted. Fortunately, it’s quite easy to modify the default behavior using these steps:

1 With delete_user.php open, click the plus button in the Server Behaviors panel, and choose Recordset. Create a recordset using the same settings as in step 2 of “Loading a record into the update form.”

2. Use the Bindings panel to add dynamic text objects next to Name and Username. This will identify the record about to be deleted.

![Image](graphics/fig06_50.jpg)

3. Click inside the red outline of the form, and insert a hidden field.

### NOTE:

In Windows, Dreamweaver’s visual aids display a form with a dotted outline in Design view, as shown in the preceding screen shot. The Mac version uses a solid outline.

Name the field `user_id`, and set its value to `user_id` from the `getUser` recordset in the same way as you did for the update form.

4. Click the plus button in the Server Behaviors panel, and choose Delete Record. Use the following settings in the Delete Record dialog box.

![Image](graphics/fig06_51.jpg)

By default, “Primary key value” is set to URL Parameter. This deletes the record as soon as the page loads. You *must* change this to Form Variable.

5. Click OK to apply the Delete Record server behavior.

6. All that remains is to wire up the Cancel button.

In Code view, insert a new line *before* this code (it should be on line 3):

if (!function_exists("GetSQLValueString")) {

7. In the space you just created, add the following code:

if (isset($_POST['cancel'])) {  
  header('Location: user_list.php');  
  exit;  

}

The `name` attribute of the Cancel button has been set to `cancel`. The `isset()` function checks the `$_POST` array to see if it contains `cancel`. This will be the case only if the Cancel button has been clicked. If it has, the `header()` function redirects the page to user_list.php, and `exit` ensures that no further part of the script is executed.

![Image](graphics/caution.jpg)**CAUTION!**

This redirect must come before the Delete Record server behavior. Otherwise, the record will still be deleted.

8. Test the page in a browser or Live View by launching user_list.php and clicking one of the DELETE links (hold down Ctrl/Cmd if using Live View). You should see the details of the record in delete_user.php.

9. Click the Cancel button. When you’re redirected to user_list.php, the record is still listed.
