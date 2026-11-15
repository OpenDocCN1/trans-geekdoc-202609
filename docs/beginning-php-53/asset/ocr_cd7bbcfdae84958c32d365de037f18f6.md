+   - Because your template designers have access to your PHP code, it’s possible for them to inadvertently (or deliberately) alter your application code, creating all sorts of potential security and stability problems for your application

+   - Unit testing a piece of application logic that also contains presentation logic is tricky. (See the next section for more on unit testing.) It’s much easier to test a piece of pure application code

A better approach is to keep all your application code separate from your presentation code. There are many ways to do this, but a common technique is to keep all markup in separate template files. Your application code can then concentrate on the business logic of your application, and can include a template file whenever it wants to display output to the user.

# Separate Application and Presentation Code

To illustrate this technique, rewrite the Widget Club member registration form script, `registration.php`, from Chapter 9 so that the markup is kept separate from the application logic. First, create a `templates` folder in your document root folder. This is to hold the template files — that is, the presentation logic. Next, create global page header and footer templates that can be included in every page. Create the following two files inside your `templates` folder:

# page_header.php:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title><?php echo $results["pageTitle"] ?><?/title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
.error { background: #d33; color: white; padding: 0.2em; }
</style>
</head>
<body>
```

# page_footer.php:

```
</body>
</html>
```

Now you can create the templates to display the registration form and the thank-you page. First, the registration form, `registration_form.php`:

```
<?php include "page_header.php" ?>

<h1>Membership Form<h1>

<?php if ( $results["missingFields"] ) { ?>
<p class="error">There were some problems with the form you submitted.
Please complete the fields highlighted below and click Send Details to resend
the form.</p>
<?php } else { ?>
<p>Thanks for choosing to join The Widget Club. To register,
please fill in your details below and click Send Details. Fields
marked with an asterisk (*) are required.</p>
```