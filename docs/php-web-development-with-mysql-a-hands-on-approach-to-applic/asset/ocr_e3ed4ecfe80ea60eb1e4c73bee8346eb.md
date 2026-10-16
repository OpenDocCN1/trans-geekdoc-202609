Next create a Boolean variable called $output_form that we can set to true or false based on the success of our validation. We’ll set it to true in the else clause because we want to output the FullName form when a user first navigates to this script:

```
if (isset($_POST['submit']))
{
    // ...
}
else
{
    $output_form = true;
    // ...
}
// ...
```

# Adding Field Validation

If you remember, we named the form variables first_name and last_name:

```
<input name="first_name"/>
...
<input name="last_name"/>
```

Working inside the condition where the user submits the form, we’ll create a couple of variables for our first and last name as shown in Listing 14.1.

Listing 14.1.

```
1. <?php
2. if (isset($_POST['submit']))
3. {
4.     $first_name = $_POST['first_name'];
5.     $last_name = $_POST['last_name'];
6.     // ...
7. }
8. else
9. {
10.    $output_form = true;
11.    // ...
12. }
```