
# Authentication and Password Verification

The first option will give better performance, since the user’s credentials are only checked once—when the login form is submitted. The second option offers greater security, since the user’s credentials are checked against the database every time a sensitive page is requested.

In general, the more secure option is preferable, since it allows us to remove authors from the site even while they’re logged in. Otherwise, once a user is logged in, they’ll stay logged in for as long as their `PHP` session remains active. That’s a steep price to pay for a little extra performance.

The theory behind this is simple to implement, but it’s made more difficult because the password field in the database doesn’t store the password in plain text, as typed by the user. Instead, it stores a hashed password like this:

```
$2y$10$XPtbphrRABcV95GxoeAk.OeI8tPgaypkKicBUhX/YbC9QYSSoowRq
```

There’s no way to decrypt the password to do the comparison, but because we used `password_hash` to hash the password, we can use `password_verify` to check it.

`password_verify` takes two arguments: the plain text password to check and the hashed password from the database. It returns true or false depending on whether or not the password is correct.

To check the password, we’ll need the hash from the database before being able to use it with `password_verify`. Luckily, thanks to the `DatabaseTable` class and the existing `$authorsTable` variable, it’s easy for us to look up the hashed password of a user by using their email address:

```
$author = $authorsTable->find('email', strtolower($_POST['email']);
```

Once the user’s information is stored in `$author`, it’s possible to check the password using the `password_verify` function, like so:

```
if (!empty($author) && password_verify($_POST['password'], $author[0]['password'])) {
    // Login successful
}
else {
    // Passwords don't match, an error occurred
}
```

Note the `[0]` after `$author`. That’s because the `find()` function may return more than one record. We need to specifically read the first record returned.

The first condition in the `if` statement checks to see if an author has been retrieved from the database. If one has, the second condition will check that the password entered by the user matches the one in the database.

The order is important here. `PHP` will run and (`&&`) conditions left to right, and stop when one evaluates to false. If the order were reversed and the password check were done before `!empty($author)`, an error might occur, because `$author` might not contain an array with a `password` key! By putting the `!empty($author)` check first, we know that something is set in the `password` key for the `$author` array.

### Hashing

You may have thought we could use this:

```
if (password_hash($_POST['password'], PASSWORD_DEFAULT) == $author[0]['password']) { ...
```

However, `password_hash` creates a different hash each time it’s called, even if it’s called with the same password string! We must use `password_verify` to check the password.

Once the user has entered the email address and password, they can be logged in by setting the session variable.

After checking the password was correct using `password_verify`, it’s time to write some data to the session. There are various options here. We could just store the user ID or the email address of the person who’s been logged in.

However, it’s good practice to store both the login name and password in the session and check them both on each page view. That way, if the user is logged in on two different computers and the password is changed, they’ll be logged out and required to log back in.

This is a useful security feature for users, since if one of those logged-in locations wasn’t really the user—someone having managed to get unauthorized access to their account—the attacker would be logged out as soon as the password was changed. Without storing the password in the session, the attacker could log in once, and as long as the browser was left open, they’d maintain access to the user’s account.

One method of achieving this is to store both the email address and password in the session:

```
$_SESSION['email'] = $_POST['email'];
$_SESSION['password'] = $_POST['password'];
```

Then, on each page view, we’d check the information in the session against the database:

```
$author = $authorsTable->find('email', strtolower($_SESSION['email']))[0];

if (!empty($author) && password_verify($_SESSION['password'], $author['password'])) {
  // Display password protected content
}
else {
  // Display an error message and clear the session, logging the user out
}
```

This is theoretically what we want to do. With this approach, if the password is changed in the database, or the author is removed from the database, the user will be logged out.

However, there’s an obvious security issue here. Although sessions are stored on the server, if someone did gain access to our web server, they could see the plain text password of any logged-in users, completely forfeiting the benefit of hashing the password in the first place.

To avoid storing the plain text password of the logged-in users in the session, we’ll need to adjust the logic slightly.

Instead of storing the plain-text password in the session, it’s better to store the password hash from the database in the session. If someone is able to read the session data from the server, they’ll only see the hash, not the real password!

To store the hash in the session, we can use the following code:

```
$_SESSION['email'] = $_POST['email'];
$_SESSION['password'] = $author['password'];
```

With the email address and hash stored, we can check the values from the database, and if either the email address or password stored in the database have changed, the user can be logged out.

On each page, we’ll need to run this code:

```
$author = $authorsTable->find('email', strtolower($_SESSION['email']));

if (!empty($author) && $author[0]['password'] === $_SESSION['password']) {
    // Display password protected content
}
else {
    // Display an error message and log the user out
}
```

The code above does three things:

* It searches the database for the user with the email address from the session, which would have been set when the user submitted the login form.
* It checks a record has been retrieved from the database. After all, it’s possible the user entered an email address that doesn’t actually exist in the database.
* It compares the password in the session to the password that’s currently in the database. If it’s changed between logging in and viewing this page, the user will be logged out.

As this check will need to be done on every page we want to password protect, let’s move it into a class for easy reuse. We’ll need three methods:

* a method that’s called when the user tries to log in with an email address and password
* a method that will be called on each page to check whether the user is logged in or not (with the check that ensures the password hasn’t changed in the database)
* a method for logging out

Since this is something that’s going to be useful on any website we build, we’ll place it in the `Ninja` framework namespace:
