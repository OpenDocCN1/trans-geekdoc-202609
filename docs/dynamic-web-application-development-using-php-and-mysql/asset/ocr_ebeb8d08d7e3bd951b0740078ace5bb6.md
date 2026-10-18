FIGURE 7.10 The form and the alert that appears if both fields are left empty, running in Internet Explorer 7

![](bbox=[0.23, 0.09, 0.93, 0.42])

# Validating other types of form component

In addition to checking if text fields contain characters, a common process for mandatory fields, we can do other types of check. For example we can see if the user has made a selection from a select list, or see if a radio button or check box has been checked.

It is useful to add an empty option to a ‘select’ component to confirm that the user has made a choice. If they accept the default (i.e. nothing selected) then we can flag that as an error using the JavaScript validation function. In this select, for example, the first option is empty. This means we can ensure that the user specifically chooses either ‘Administrator’ or ‘User’ from the list by validating that the zero-indexed selection (the empty one) has not been selected.

```
<select id="loginoptions" size="1">
  <option></option>
  <option>Administrator</option>
  <option>User</option>
</select>
```

In our JavaScript validation function, we can check the index of the selected option using the ‘selectedIndex’ property. If the index is zero then we can do some error notification.

```
if(loginForm.loginoptions.selectedIndex == 0 )
{
  strErrorMessage += "you must select your Login role\n";
  booValid=false;
}
```