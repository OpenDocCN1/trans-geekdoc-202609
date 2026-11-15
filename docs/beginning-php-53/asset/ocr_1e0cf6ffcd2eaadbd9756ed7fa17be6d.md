```
<dt>Retyped password</dt><dd>?php echo $_POST["password2"] ?</dd>
<dt>Gender</dt><dd>?php echo $_POST["gender"] ?</dd>
<dt>Favorite widgets</dt><dd>?php echo $favoriteWidgets? </dd>
<dt>You want to receive the following newsletters:</dt><dd>?php echo $newsletters? </dd>
<dt>Comments</dt><dd>?php echo $_POST["comments"] ?</dd>
</dl>
```

# Generating Web Forms with PHP

So far, the forms you’ve created have been embedded in static HTML pages. However, because PHP scripts can contain and output HTML, it’s perfectly possible to combine both the form and the form handler in a single PHP file. Doing this gives you a couple of advantages. First, if the users haven’t filled in the form correctly, you can redisplay the form to them so they can correct the errors. Second, because the form is created from within a PHP script, you can dynamically set various parts of the form at the time the script is run, adding a lot of power and flexibility to your forms.

As with generating any HTML markup, you can use two common approaches to generate a form within PHP: you can use echo or print statements to write out the markup for the form, or you can separate the PHP code from the form markup using the `<?php` and `?>` tags. You can also use a mixture of the two techniques within the same script.

# Try It Out Create an Interactive Form with PHP

The following all-in-one PHP script does the following things:

+   - It displays a registration form for the user to fill out. Certain fields are required to be filled in; these are labeled with asterisks in the form. The remaining fields are optional
+   - When the form is sent, the script checks that the required fields have been filled in
+   - If all required fields are filled, the script displays a thank-you message
+   - If one or more required fields are missing, the script redispays the form with an error message, and highlights the fields that still need to be filled in. The script remembers which fields the user already filled in, and preflils those fields in the new form

To try out the script, first save the following code as registration.php in your document root folder:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Membership Form</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
.error { background: #d33; color: white; padding: 0.2em; }
```