
## Chapter 14 Validating Form Data and Creating Sticky Fields

> “C is quirky, flawed, and an enormous success.”
> -Dennis M. Ritchie

## 14. VALIDATING FORM DATA AND CREATING STICKY FIELDS

When creating a web application that requires form data, it is crucial to validate the data being entered before processing it. At a minimum, we usually want to make sure that the user entered text into all the form fields.

Likewise, it is always annoying from the user’s perspective if a user is sent back to a form that they missed entering a field of data, only to find out that all the data they entered in the other fields didn’t persist. In this case, we want to create sticky fields that will fill in the form fields with the user’s data if we have to redisplay the form.

We will take the FullName application we’ve been working on in the last two chapters and add validation and sticky fields for the form entries.

## Modifying FullName Behavior Based On Validation

When a user brings up the FullName application, we want to process the first and last name entries only if they enter text into both fields. Otherwise, we want to send the user back to the form.

Therefore, we want to add logic to display the form as long as any field is empty and display an appropriate error message indicating what data needs to be filled in for missing fields. If the fields validate correctly, we can output our thanks to the user for submitting their full name.

Let’s start by adding conditional logic that runs when the user submits the form, or navigates to this script the first time:

```
<?php
    if (isset($_POST['submit']))
    {
        // ...
    }
    else
    {
        // ...
    }
    // ...
```

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

## Adding Field Validation

If you remember, we named the form variables first_name and last_name:

```
<input name="first_name"/>
...
<input name="last_name"/>
```

Working inside the condition where the user submits the form, we’ll create a couple of variables for our first and last name as shown in Listing 14.1.

### Listing 14.1.

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

## 14. VALIDATING FORM DATA AND CREATING STICKY FIELDS

Next, we want to add linear nested conditional logic that tests if the first name, last name, or both are empty, then output an appropriate message to the user if necessary. See Listing 14.2.

### Listing 14.2.

```
```php
if (isset($_POST['submit']))
{
    $first_name = $_POST['first_name'];
    $last_name = $_POST['last_name'];

    // Validate first and last name fields
    if (empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name and last name</p>';
        $output_form = true;
    }
    else if (empty($first_name) && !empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name</p>';
        $output_form = true;
    }
    else if (!empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter last name</p>';
        $output_form = true;
    }
    else
    {
        // Both first name AND last name are filled in, form entry is validated
    }
}
```
```

We want to add our code to insert the first and last name into the FullName table in the last else clause above. Then, we echo our message thanking the user for submitting their full name. Let's add that code now. See Listing 14.3.

### Listing 14.3.

```
```php
else // Both first name AND last name are filled in, form entry is validated
{
    // Insert full name into database
    $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
        or trigger_error("Error connecting to MySQL server.", E_USER_ERROR);

    $query = "INSERT INTO fullName (first_name, last_name) "
        . "VALUES ('$first_name', '$last_name')";
}
```
```

## Making the First and Last Name Fields Sticky

```
10. $result = mysqli_query($dbc, $query)
11.     or trigger_error('Error querying database.', E_USER_WARNING);
12.
13. if (!$result)
14. {
15.     echo("Query Error description: " . mysqli_error($dbc));
16. }
17.
18. mysqli_close($dbc);
19.
20. echo "<br/><br/>Hello $first_name $last_name Thanks for submitting your full name!";
21.
22. $output_form = false;
23. }
```

The last thing we should do in the above block is to set the $output_form variable to false to prevent outputting the form again.

## Making the First and Last Name Fields Sticky

Let's go back to the else block that follows the if (isset($_POST['submit'])):

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
```

We need to initialize $first_name and $last_name to empty strings. Then, when the user first navigates to the script, empty strings are displayed in the first_name and last_name form fields:

```
}
else
{
    $output_form = true;
    $first_name = "";
    $last_name = "";
}
```

The final thing we need to do is add conditional code following the previous else block that outputs the FullName form if the $output_form variable is set to true and make the first and last name fields sticky as in Listing 14.4.

## 14. VALIDATING FORM DATA AND CREATING STICKY FIELDS

### Listing 14.4.

```
```php
if ($output_form): ?>
<h2>Enter Full Name</h2>
<form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
    <div class="form-group">
    <label for="first_name">First Name</label>
    <input class="form-control" id="first_name" name="first_name"
    value="<?= $first_name ?>" placeholder="First Name">
    </div>
    <div class="form-group">
    <label for="last_name">Last Name</label>
    <input class="form-control" id="last_name" name="last_name"
    value="<?= $last_name ?>" placeholder="Last Name">
    </div>
    <button type="submit" class="btn btn-primary"
    name="submit">Submit Name</button>
</form>
<?php endif; ?>
```
```

Notice in the prior block of code that value attributes for the first_name and last_name form fields are filled in with whatever the user entered in from the previous post if validation does not pass, and we redisplay the form. Listing 14.5 shows what the complete code looks like.

### Listing 14.5.

```
```php
<?php
if (isset($_POST['submit']))
{
    $first_name = $_POST['first_name'];
    $last_name = $_POST['last_name'];

    // Validate first and last name fields
    if (empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name and last name</p>';
        $output_form = true;
    }
    else if (empty($first_name) && !empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name</p>';
        $output_form = true;
    }
    else if (!empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter last name</p>';
        $output_form = true;
    }
}
```
```

## Making the First and Last Name Fields Sticky

```
```php
23. else
24. {
25.     // Both first name AND last name are filled in, form entry is validated
26.     // Insert full name into database
27.     $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
28.         or trigger_error("Error connecting to MySQL server.", E_USER_ERROR);
29.
30.     $query = "INSERT INTO fullName (first_name, last_name) "
31.         . "VALUES ('$first_name', '$last_name')";
32.
33.     $result = mysqli_query($dbc, $query)
34.         or trigger_error('Error querying database.', E_USER_ERROR);
35.
36.     if (!$result)
37.     {
38.         echo("Query Error description: " . mysqli_error($dbc));
39.     }
40.
41.     mysqli_close($dbc);
42.
43.     echo "<br/><br/>Hello $first_name $last_name Thanks for submitting your full name!";
44.
45.     $output_form = false;
46. }
47. }
48. else
49. {
50.     $output_form = true;
51.     $first_name = "";
52.     $last_name = "";
53. }
54.
55. if ($output_form): ?>
56. <h2>Enter Full Name</h2>
57. <form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
58.     <div class="form-group">
59.         <label for="first_name">First Name</label>
60.         <input class="form-control" id="first_name" name="first_name"
61.             value="<?= $first_name ?>" placeholder="First Name">
62.     </div>
63.     <div class="form-group">
64.         <label for="last_name">Last Name</label>
65.         <input class="form-control" id="last_name" name="last_name"
66.             value="<?= $last_name ?>" placeholder="Last Name">
67.     </div>
68.     <button type="submit" class="btn btn-primary"
69.         name="submit">Submit Name</button>
70. </form>
71. <?php endif; ?>
```
