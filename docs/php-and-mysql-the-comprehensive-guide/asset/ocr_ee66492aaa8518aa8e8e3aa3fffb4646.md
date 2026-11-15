# 13.2.1 The “Good” Old Days

Back to PHP. Form handling used to be extremely simple. Rasmus Lerdorf, the language inventor, thought to himself: How do I want to access the data in a form field that is called field (i.e., whose name attribute has the value “field”)? The answer, as simple as it was ingenious, was this: with $field.

And that's the whole trick: When a form is sent, PHP automatically creates variables with the names of the form fields used. It could hardly be simpler. The following script output (note the past tense!) all the form data. For you to see anything, you must of course first fill out the form and submit it.

```
<html>
<head>
<title>Order Form</title>
</head>
<body>
<h1>Form Data</h1>
<?php
echo "Salutation: $Salutation<br />";
echo "First name: $FirstName<br />";
echo "Last name: $LastName<br />";
echo "Email: $Email<br />";
echo "Promo code: $Promo<br />";
echo "Number of tickets: $Number<br />";
echo "Section: $Section<br />";
echo "Comments: $Comments<br />";
echo "Terms &amp; conditions: $Terms";
?>
```

```
<h1>World Cup Ticket Service</h1>
<form>
<input type="radio" name="Salutation" value="Mr."
/>Mr.
<input type="radio" name="Salutation" value="Ms."
/>Ms. <br />
First name <input type="text" name="FirstName" /><br />
Last name<input type="text" name="LastName" /><br />
Email address <input type="text" name="Email" /><br />
Promo code <input type="password" name="Promo" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
```