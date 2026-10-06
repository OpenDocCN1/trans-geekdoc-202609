# Appendix A: Solutions to Exercises

```
</select>

<div style="clear: both;">
<input type="submit" name="submitButton" id="nextButton" value="Next
&gt; / />

<input type="submit" name="submitButton" id="backButton" value="&lt;
Back" style="margin-right: 20px;" />
</div>
</form>
<?php
}

function displayStep3() {
  displayHeader();
}
<h1>Member Signup: Step 3</h1>

<form action="exercise2.php" method="post">
<div style="width:30em;">
<input type="hidden" name="step" value="3" />

<label for="newsletter">Do you want to receive our newsletter?</label>
<input type="checkbox" name="newsletter" id="newsletter" value="yes"?php setChecked("newsletter", "yes") />

<label for="comments">Any comments?</label>
<textarea name="comments" id="comments" rows="4" cols="50">?php setValue("comments", )></textarea>

<div style="clear: both;">
<input type="submit" name="submitButton" id="nextButton" value="Next
&gt; / />

<input type="submit" name="submitButton" id="backButton" value="&lt;
Back" style="margin-right: 20px;" />
</div>
</form>
<?php
}

function displayThanks() {
  $_SESSION = array();
  displayHeader();
}

<h1>Thank You</h1>
<p>Thank you, your application has been received.</p>
<?php
}

function displayPageHeader() {
```