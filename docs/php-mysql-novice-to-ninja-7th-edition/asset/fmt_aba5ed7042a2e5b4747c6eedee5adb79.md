
Check if it works by filling out the form, submitting it and selecting all the records from the `author` table using MySQL Workbench. If you don’t see the data for the record you just added, double check all your code and try again.

We have a basic registration form working, but there are some problems with it in its current state. We need some control over what’s allowed in the database. There are some rules we probably want to enforce on the data before allowing the record to be inserted:

* All fields should actually contain some data, so no blank email or name.
* The email address should be a real email address. For example, `paul@example.org` is allowed, but `abc123` isn’t.
* The email address entered must not already belong to an existing account.

These validation rules need to be checked before the data is inserted, but also after the form is submitted. If there’s a problem with the submission, it’s good practice to show the form to the user again so they can fix their mistakes.

Each one of these validation rules needs to be applied in slightly different ways, but with a similar result. We’ll use `if` statements for each check and set a Boolean variable `$valid` to keep track of whether the data is valid or not. For example, to check that each field has a value inside it, we can use a series of `if` statements that set the `$valid` variable to false if one of the fields is empty:

```
public function registrationFormSubmit() {
  $author = $_POST['author'];

  // Assume the data is valid to begin with
  $valid = true;

  // But if any of the fields have been left blank, set $valid to false
  if (empty($author['name'])) {
    $valid = false;
  }

  if (empty($author['email'])) {
    $valid = false;
  }

  if (empty($author['password'])) {
    $valid = false;
  }

  // If $valid is still true, no fields were blank and the data can be added
  if ($valid == true) {
    $this->authorsTable->save($author);

    header('Location: /author/success');
  }
  else {
    // If the data is not valid, show the form again
    return ['template' => 'register.html.php',
          'title' => 'Register an account'];
  }
}
```

### Using `empty()`

I’ve used `empty($author['name'])` instead of `$author['name'] == ''` above, because this will also catch invalid form submissions without causing an error.

It’s possible for someone to submit a `POST` request without filling in your form! It’s likely they might not supply values (an empty string is still a value!) for some of the form fields. It’s better to avoid these kinds of errors than potentially alert malicious users to how the site works.

Try it yourself by submitting the form and leaving one or more fields blank. You should see the blank form again rather than the “Registration Successful” message.

If `$valid` has been set to false because one of the fields is empty, the form is shown again by returning a title and template. If you did try this for yourself, you’ll have immediately noticed that whatever you typed into the box was removed, with no indication of what went wrong.

To fix this, let’s first create a second array to keep a list of error messages to show to the user:

```
public function registrationFormSubmit() {
  $author = $_POST['author'];

  // Start with an empty array
  $errors = [];

  // But if any of the fields have been left blank, set $valid to false
  if (empty($author['name'])) {
    $errors[] = 'Name cannot be blank';
  }

  if (empty($author['email'])) {
    $errors[] = 'Email cannot be blank';
  }

  if (empty($author['password'])) {
    $errors[] = 'Password cannot be blank';
  }

  // If the $errors array is still empty, no fields were blank and the data can be added
  if (empty($errors)) {
    $this->authorsTable->save($author);

    header('Location: /author/success');
  }
  else {
    // If the data is not valid, show the form again
    return ['template' => 'register.html.php',
          'title' => 'Register an account'];
  }
}
```

Remember the `[] =` operator for arrays? This will be added to the end of the `$errors` array, so if the user leaves all three fields blank, all three error messages will be stored in the `$errors` array. These errors will need to be shown to the user by displaying them in the template.

Instead of having an `$errors` array and a `$valid` variable, I’ve removed the `$valid` variable. We can determine if any validation checks failed by checking to see whether the `$errors` array is still empty. If it’s empty, we know that no errors occurred.

When we created the joke list page, we supplied the template some variables using the `variables` key in the returned array. The same thing can be done here with the errors:

```
// If the data is not valid, show the form again
return ['template' => 'register.html.php',
  'title' => 'Register an account',
  'variables' => [
    'errors' => $errors
  ]
];
```

And now the `$errors` variable can be used in `register.html.php`:

```
<?php
if (!empty($errors)) :
    ?>
  <div class="errors">
    <p>Your account could not be created, please check the following:</p>
    <ul>
    <?php
            foreach ($errors as $error) :
                ?>
        <li><?= $error ?></li>
        <?php
            endforeach; ?>
    </ul>
  </div>
<?php
endif;
?>
<form action="" method="post">
  <label for="email">Your email address</label>
  <input name="author[email]" id="email" type="text">

  <label for="name">Your name</label>
  <input name="author[name]" id="name" type="text">

  <label for="password">Password</label>
  <input name="author[password]" id="password" type="password">

  <input type="submit" name="submit" value="Register account">
</form>
```

To make the errors look a bit nicer, let’s add the following to `jokes.css`:

```
.errors {
  padding: 1em;
  border: 1px solid red;
  background-color: lightyellow;
  color: red;
  margin-bottom: 1em;
  overflow: auto;
}
.errors ul {
  margin-left: 1em;
}
```

If there are any errors now, they’ll all be printed in a list at the top of the page before the form, and the user will know what went wrong.

To make things even easier, we’ll re-fill the form with the data from `$_POST` so that the user doesn’t have to retype everything into each box.

Firstly, let’s supply the `$author` information to the template by amending the `return` value:

```
return ['template' => 'register.html.php',
  'title' => 'Register an account',
  'variables' => [
    'errors' => $errors,
    'author' => $author
  ]
];
```

Now print the values in the form fields if they’re set. This is exactly the same approach we took in `editjoke.html.php` to fill the form with the information in the database.

Example: [Registration-Validation](https://github.com/spbooks/phpmysql7/tree/Registration-Validation)

```
<label for="email">Your email address</label>
<input name="author[email]" id="email" type="text" value="<?=$author['email'] ?? ''?>">

<label for="name">Your name</label>
<input name="author[name]" id="name" type="text" value="<?=$author['name'] ?? ''?>">

<label for="password">Password</label>
<input name="author[password]" id="password" type="password" value="<?=$author['password'] ?? ''?>">

<input type="submit" name="submit" value="Register account">
```

## Validating Email Addresses

The validation above will prevent someone from leaving the email address field blank. However, it doesn’t guarantee they’ve entered a valid email address. They can still enter “a” into the field and it will pass the validation.

To ensure they enter a valid email address, we need to do some checking. We could look at each character in the string and look for an “@” symbol, ensuring it’s not the first character, and perhaps also look for a “.” after the “@” to match “x@x.x”.

As for most common problems, PHP includes a method of validating email addresses that’s far more accurate and simpler to use than building your own. There’s no need to reinvent the wheel.
