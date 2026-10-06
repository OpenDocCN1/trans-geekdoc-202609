# Part III: Using PHP in Practice

```
foreach ($errorMessages as $errorMessage ) {
necho $errorMessage;
}
} else {
?>
```

<p>Thanks for choosing to join our book club. below and Click Send Details.</p>
<p>To register, please fill in your details below marked with an asterisk (*) are required.</p>

```
<form action="register.php" method="post" style="margin-bottom: 50px;">
  <div style="width:300px">
    <input type="hidden" name="action" value="register" />
    <label for="username">?php validate("username", $missingFields) echo ?>Choose a username </label>
    <input type="text" name="username" id="username" value="<?php echo
$member->getValueEncoded($username) ?> />
    <label for="password">?php if ($missingFields) echo '
class="error"' ?>Choose a password </label>
    <input type="password" name="password1" id="password1" value="" />
    <label for="password2">?php if ($missingFields) echo '
class="error"' ?>Retrieve password </label>
    <input type="password" name="password2" id="password2" value="" />
    <label for="emailAddress">?php validate("emailAddress", $missingFields) ?>Email Address,
    <input type="text" name="emailAddress" id="emailAddress" value="<?php
echo $member->getValueEncoded("emailaddress") ?>" />
    <label for="firstName">?php validate("firstName", $missingFields) ?>First Name </label>
    <input type="text" name="firstName" id="firstName" value="<?php echo
$member->getValueEncoded("firstName") ?>" />
    <label for="lastName">?php validate("lastName", $missingFields) ?>Last Name </label>
    <input type="text" name="lastName" id="lastName" value="<?php echo
$member->getValueEncoded("lastName") ?>" />
    <label for="gender">?php validate("gender", $missingFields) ?>Your gender: </label>
    <input type="radio" name="gender" id="genderMale" value="m" <?<?php
setChecked($member, $gender, "m") ?>?>
    <label for="genderFemale">Female</label>
    <input type="radio" name="gender" id="genderFemale" value="f" <?phpphp
setChecked($member, $gender, "f") ?>?>
    <label for="favoriteGenre">What's your favorite genre?</label>
```

412