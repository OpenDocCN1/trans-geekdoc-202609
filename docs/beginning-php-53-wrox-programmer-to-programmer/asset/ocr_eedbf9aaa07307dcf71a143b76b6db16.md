# Part III: Using PHP in Practice

```
<input type="text" name="lastName" id="lastName" value="
<?php echo setvalue("lastName") ?>"

<div style="clear:both;">
  <input type="submit" name="submitButton" id="nextButton" value="
Next &gt;" />
</div>
</div>
</form>
<?php
function displayStep2() {
n?>
<h2>Member Signup: Step 2</h2>

<form action="registration_multistep.php" method="post">
  <div style="width:30em;">
    <input type="hidden" name="step" value="2" />
    <input type="hidden" name="firstName" value="<?php setvalue("firstName") ?>"
    <input type="hidden" name="lastName" value="<?php setvalue("lastName") ?>"
    <input type="hidden" name="newsletter" value="<?php setvalue("newsletter") ?>"
    <input type="hidden" name="comments" value="<?php setvalue("comments") ?>"
    <label for="gender">Gender:</label>
    <label for="genderMale">Male</label>
    <input type="radio" name="gender" id="genderMale" value="M" <?php if setchecked($gender, "M")) ?> />
    <label for="genderFemale">Female</label>
    <input type="radio" name="gender" id="genderFemale" value="F" <?php if setchecked($gender, "F")) ?> />
    <label for="favoriteWidget">What's your favorite widget?</label>
    <select name="favoriteWidget" id="favoriteWidget" size="1">
      <option value="superWidget" <?php setSelected("favoriteWidget", "superWidget") ?>>SuperWidget</option>
      <option value="megaWidget" <?php setSelected("favoriteWidget", "megaWidget") ?>>MegaWidget</option>
      <option value="wonderWidget" <?php setSelected("favoriteWidget", "wonderWidget") ?>>WonderWidget</option>
    </select>

  <div style="clear:both;">
    <input type="submit" name="submitButton" id="nextButton" value="
Next &gt;" />
  </div>
```

252