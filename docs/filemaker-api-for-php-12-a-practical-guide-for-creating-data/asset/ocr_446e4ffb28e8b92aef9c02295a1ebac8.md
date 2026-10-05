As we go through the code you'll notice that creating the links is essentially the same for each button. The only difference is figuring out when to display a plain button (i.e. no link) or a button with a link. The way we determine choice to make is by the skip value and the found count of records. After that it's as easy as using the URL link with the correct skip value and using the image resource for the correct image.

The go to first record image is displayed when the skip value is greater than zero. For the first record it would be appropriate to be able to go to the first record. If the skip value is zero, there is no reason to link to the record you are already on. The skip value for the first record is always zero. For some odd reason, PHP running on IIS 7.5 Server throws an error if you try to use the script first and assign default values to the variables for $firstName and $skip before they are used to generate the navigation links.

```
<table cellpadding="0" cellspacing="0">
<tr>
<td>
<?php
if (empty($_GET['FirstName'])) {
  $firstName='';
} else {
  $firstName=\$_GET['FirstName'];
}

if(empty($_GET['skip'])) {
  $skip='0';
} else {
  $skip=$_GET['skip'];
}

if ($skip > 0) {
  echo '<a href=\' . \$_SERVER['PHP_SELF'] . \'?skip=0&max=1&FirstName=\' . \$firstName . '\'><img src="Images/first_record.jpg" border=0/></a>';
} else {
  echo '<img src="Images/first_record.jpg" border=0/>';
}
?>
</td>
<td>
```

The go to previous record image is similar to the first record in that there's no reason to provide a link if you are already on the previous record. The skip value for the URL is calculated as the current skip value minus one you want to go back one record at a time.

```
<?php
$previous=$skip-1;
if ($skip > 0) {
  echo '<a href=\' . \$_SERVER['PHP_SELF'] . \'?skip=' . \$previous . '\&max=1&FirstName=\' . \$firstName . '\'><img src="Images/previous_record.jpg" border=0/></a>';
```