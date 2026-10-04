# Chapter 12

```
<p>
Full name:<br />
<input type="text" class="txtinput" name="name" maxlength="*100"
value="<?php htmlspecialchars($name);?>" />
</p>
<p>
E-mail Address:<br />
<input type="text" class="txtinput" name="e-mail" maxlength="*255"
value="<?php htmlspecialchars($e-mail);?>" />
</p>
```

If the user has Admin access, do the following:

```
<?php
if (isset($_SESSION['access_lvl'])
and $_SESSION['access_lvl'] == 3)
{
```

While we do assume that most readers have a fundamental knowledge of HTML, you may not be familiar with <fieldset> and <legend>. We simply suggest you enter them and see how they are displayed on the page; using <fieldset> and <legend> is a great way to group many of your form fields.

We recommend you visit www.w3.org/TR/REC-html40/interact/forms.html#h-17.10 for more information.

```
echo "fieldset\n"
echo "<legend>Access Level</legend>\n"
```

First, get all of the access levels from the database:

```
$sql = "SELECT * FROM cms_access_levels ORDER BY access_lvl DESC";
$result = mysql_query($sql
```

Then cycle through each one, displaying as radio buttons on the page.

The next page requires the user ID. Because this is not entered in a form field, create a hidden field to carry the data over the transaction page.

410