# Chapter 15 Building a Secure Web Application

We might find ourselves somewhat confused later on. A much better strategy is to actually verify that the incoming value is actually one of the expected/permitted values, as shown in Listing 15.2:

# Listing 15.2 submit_form.php—Verifying Form Input

```
<?php
switch ($_POST['gender']) {
    case 'male':
    case 'female':
    case 'other':
        echo "<h1>Congratulations!<br>\n        You are: " .$_POST['gender'] . "</h1>";
        break;
    default:
        echo "<h1><span style=\"color: red;">WARNING:</span><br>\n        Invalid input value specified.</h1>";
        break;
}
?
```

There is a little more code involved—setting up the list of valid input—but we can at be sure we are getting correct values, and this becomes a lot more important when we start handling data values financially sensitive than a user’s selected gender. As a rule, we cannot ever assume that a value from form will be within a set of expected values—we must check first.

# Filtering Even Basic Values

HTML elements have no types associated with them and most simply pass strings (which in, turn, represent such as dates, times, or numbers) to the server. Even if you have a numeric field, you cannot assume or trust that it was entered correctly. In environments where particularly powerful client-side code try to make sure that the value entered is of a particular type, there is no guarantee that the values will not be sent to the server directly, as we saw in the previous section.

An easy way to make sure that a value is of the expected type is to cast or convert it to that type and then use that value, as follows:

```
$number_of_nights = (int)$_POST['num_nights'];
if ($number_of_nights == 0) {
    echo "ERROR: Invalid number of nights for the room!";
}
```