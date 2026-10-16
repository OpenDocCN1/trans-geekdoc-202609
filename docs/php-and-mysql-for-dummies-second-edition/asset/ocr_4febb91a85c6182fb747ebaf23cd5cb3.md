# Listing 8-13 (continued)

```
</tr>
<tr><td align='right'><B>|$label_array['last_name']|:</B></td>
<td> <input type='text' name='last_name' size='65' maxlength='65' value='$last_name'> </td>

</tr>
<tr><td align='right'><B>|$label_array['phone']|:</B></td>
<td> <input type='text' name='phone' size='65' maxlength='65' value='$phone'> </td>

</tr>
</table>
<p><input type='submit' value='Submit name and phone number'>
</form>
</center>";
exit();
}
echo "Welcome";
?>
</body></html>
```

Here are the differences between this program and the program in Listing 8-12:

+   ✔ **This program creates two arrays for problem data.** It creates $blank_array, as did the previous program. But this program also creates $bad_format for fields that contain information that is not in an acceptable format.
+   
+   ✔ **This program loops through $bad_format to create a separate list of problem data.** If any fields are blank, it creates one error message and list of problem fields, as did the previous program. If any fields are in an unacceptable format, this program also creates a second error message and list of problem fields.

The Web page in Figure 8-14 results when the user accidentally types his or her first name into the Middle Name field and also types nonsense for his or her phone number. Notice that two error messages appear, showing that the First Name field is blank and that the Phone field contains incorrect information.

# Giving users a choice with multiple submit buttons

You can use more than one submit button in a form. For instance, in a customer order form, you might use a button that reads *Submit Order* and another button that reads *Cancel Order*. However, you can only list one program in the `action=programname` part of your `form` tag, meaning that the two buttons run the same program. PHP solves this problem. By using PHP, you can process the form differently, depending on which button the user clicks.