```
<input type="submit" name="submitButton" id="backButton"
value=&lt; Back; style="margin-right: 20px;" />
</div>
</form>
```

```
<?php
function displayStep(3) {

<h1>Member Signup: Step 3</h1>
<form action="registration_multistep.php" method="post">
<div style="width:30em;">
<input type="hidden" name="step" value="3" />
<input type="hidden" name="firstName" value="<?php setValue ($firstName) ?>" />
<input type="hidden" name="lastName" value="<?php setValue ($lastName) ?>" />
<input type="hidden" name="gender" value="<?php setValue ($gender) ?>" />
<input type="hidden" name="favoriteWidget" value="<?php setValue($favoriteWidget) ?>" />
<label for="newsletter">Do you want to receive our newsletter?</label>
<input type="checkbox" name="newsletter" id="newsletter" value="yes"<?php setChecked("newsletter", "yes") ?> />
<label for="comments">Any comments?</label>
<textarea name="comments" rows="4" cols="50"><?php setValue ("comments") ?>></textarea>
<div style="clear:both;">
<input type="submit" name="submitButton" id="backButton" value=&lt; Next&gt; />
<input type="submit" name="submitButton" id="backButton" value=&lt; Back; style="margin-right: 20px;" />
</div>
</form>
?>

function displayThanks() {

<h1>Thank You</h1>
<p>Thank you, your application has been received.</p>
?>

</body>
</html>
```