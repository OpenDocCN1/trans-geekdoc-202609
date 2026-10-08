# Listing 27.8 valid_email() Function from data_valid_fns.php—This Function Checks Whether an Email Address Is Valid

```
function valid_email($address) {
  // check email address is possibly valid
  if (preg_match('/^[a-zA-Z0-9_\.]+@[a-zA-Z0-9\-]+\.[a-zA-Z0-9\.-]+$/', $address)) {
    return true;
  } else {
    return false;
  }
}
```

The filled_out() expects to be passed an array of variables; in general, this is the $_POST or $_GET_array. It checks whether the form fields are all filled out, and returns true if they are and if they are not.

The valid_email() function uses a slightly more regular expression than the one developed in Chapter 4, "String Manipulation and Regular Expressions," for validating email addresses. It returns true if an appears valid and false if it does not.

After you've validated the input data, you can actually do this to register the user. If you look at Listing 27.6, you can see that you do this as follows:

```
register($username, $email, $password);
// register session variable
$_SESSION['valid_user'] = $username;
```

```
// link to members page
do_html_header('Registration successful');
echo 'Your registration was successful. Go to the members page to start
  setting up your bookmarks!';
do_html_url('member.php', 'Go to members page');
```

```
// end page
do_html_footer();
```

As you can see, you call the register() function with the username, email address, and password that were entered. If this call succeeds, you register the username as a session variable and provide the user with a link to the main members' page. If it fails, this function will throw an exception that can be caught in the catch block). The output is shown in Figure 27.S.