The last else clause is where initial navigation to this page begins, so here is where we want to display our form for asking for a name with the code in Listing 21.2.

# Listing 21.2.

```
1. else
2. {
3.     ?>
4.     <form class="needs-validation" novalidate method="POST"
5.         action="<?php echo $_SERVER['PHP_SELF'] ?>"
6.         <div class="form-group">
7.             <label for="name"><h4>What is your name?</h4></label>
8.             <input type="test" class="form-control" id="entered_name"
9.                 name="entered_name" placeholder="Enter your name" required>
10.        </div>
11.        <button type="submit" class="btn btn-primary"
12.            name="name_submission">Submit</button>
13.    </form>
14.    <?php
15. }
```

Since this script contains multiple forms and they will all be POSTing to $_SERVER['PHP_SELF'], we use different name attributes for the submit button on each of the forms.

Once the user has submitted this form, execution starts up in the if clause where we will set a cookie for the entered name:

```
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
    setcookie('name', $_POST['entered_name']);
}
```

Following the setcookie() function in the if clause, we want to display the following form that asks the user for their favorite cookie. See Listing 21.3

# Listing 21.3.

```
1. if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
2. {
3.     setcookie('name', $_POST['entered_name']);
4.     ?>
5. <form class="needs-validation" novalidate method="POST"
6.     action="<?php echo $_SERVER['PHP_SELF'] ?>"
7.     <div class="form-group">
8.         <label for="name"><h4>What is your favorite cookie?</h4></label>
```