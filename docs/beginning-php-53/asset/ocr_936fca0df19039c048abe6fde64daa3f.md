```
```php
<select name="favoriteGenre" id="favoriteGenre" size="1">
<?php foreach ( $member->getGenres() as $value => $label ) { ?>
<option value="<?php echo $value ?>"><?php setSelected( $member,
    "favoriteGenre", $value ) ?><?php echo $label ?></option>
<?php } ?>
</select>

<label for="otherInterests">What are your other interests?</label>
<textarea name="otherInterests" id="otherInterests" rows="4"
cols="50"><?php echo $member->getValueEncoded( "otherInterests" )
?>/</textarea>

<div style="clear: both;">
<input type="submit" name="submitButton" id="submitButton"
value="Send Details" />
<input type="reset" name="resetButton" id="resetButton"
value="Reset Form" style="margin-right: 20px;" />
</div>

</div>
</form>
<?php
displayPageFooter();
}
```
```

```
```php
function processForm() {
$requiredFields = array( "username", "password", "emailAddress",
    "firstName", "lastName", "gender" );
$missingFields = array();
$errorMessages = array();

$member = new Member( array(
    "username" => isset( $_POST["username"] ) ? preg_replace
    ( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["username"] ) : "",
    "password" => isset( $_POST["password1"] ) and isset
    ( $_POST["password2"] ) and $_POST["password1"] == $_POST["password2"] ) ?
    preg_replace ( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["password1"] ) : "",
    "firstName" => isset( $_POST["firstName"] ) ? preg_replace
    ( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["firstName"] ) : "",
    "lastName" => isset( $_POST["lastName"] ) ? preg_replace
    ( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["lastName"] ) : "",
    "gender" => isset( $_POST["gender"] ) ? preg_replace( "/[^mf]/",
    "", $_POST["gender"] ) : "",
    "favoriteGenre" => isset( $_POST["favoriteGenre"] ) ? preg_replace
    ( "/[^a-zA-Z]/", "", $_POST["favoriteGenre"] ) : "",
    "emailAddress" => isset( $_POST["emailAddress"] ) ? preg_replace
    ( "/[^\ \@\.\\_a-zA-Z0-9]/", "", $_POST["emailAddress"] ) : "",
    "otherInterests" => isset( $_POST["otherInterests"] ) ? preg_replace
    ( "/[^\ \'\,\.\-\a-zA-Z0-9]/", "", $_POST["otherInterests"] ) : "",
    "joinDate" => date( "Y-m-d" )
) );

foreach ( $requiredFields as $requiredField ) {
```
```