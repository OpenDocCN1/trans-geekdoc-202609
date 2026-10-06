# Part III: Using PHP in Practice

# How It Works

As you can see, the process of capturing and displaying the submitted form data is really quite simple. Because the form is sent using the post method, the script extracts the form field values from the $_POST superglobal array, and displays each field value using echo (().

```
<dt>First name</dd><php echo $_POST['firstName']?></dt>
<dt>Last name</dd><php echo $_POST['lastName']?></dt>
<dt>Password</dd><php echo $_POST['password']?></dt>
<dt>Retyped password</dd><php echo $_POST['password2']?></dt>
<dt>Gender</dd><php echo $_POST['gender']?></dt>
<dt>Favorite widget</dd><php echo $_POST['favoriteWidget']?></dt>
<dt>Do you want to receive our newsletter?</dt><php echo $_POST['newsletter']?></dt>
<dt>Comments</dd><php echo $_POST['comments']?></dt>
```

By the way, the $_REQUEST superglobal contains both elements of $_GET and $_POST, you could also access the field value using the following:

```
<dt>First name</dd><php echo $_REQUEST['firstName']?></dt>
```

Generally speaking, if you know that your user data will come from a form with a get or a post method, it's best to use $_GET or $_POST rather than $_REQUEST. This reduces ambiguity and eliminates any risk of clashes between form fields and cookies; for example, there might be a cookie with the same name as one of your form fields.

# Dealing Securely with Form Data

Although the predicting script is just an example and is not designed for use in the real world, a couple of security issues with the script are worth pointing out. First of all, you wouldn't of course display the password that the user has just entered (which might send them their password in an email to remind them of).

Secondly, it's a bad idea to pass any user-entered data—such as the values in $_GET and $_POST—straight to a statement echo() or print() for displaying in a Web page. You should never trust user input on a public web site; a malicious user might be trying to break into the site. It's easy for a wrong-doer to submit form data that could be used to gain access to other users' credentials, for therefore you should always validate (that is, check) or filter user input to make sure it's safe before you display it in a Web page. You find out more about this topic in Chapter 20.

# Handling Empty Form Fields

The process_registration.php script assumes that the user has filled in all the fields in the form. However, users often forget to (or don't want to) fill in certain fields in a form. When this happens, some

234