```
```php
$member->getValueEncoded( "lastName" ) ?> />
<label for="joinDate"><php validateField( "joinDate",
$missingFields ) ?>>Joined on *</label>
<input type="text" name="joinDate" value="<?php echo
$member->getValueEncoded( "joinDate" ) ?> />
<label><?php validateField( "gender", $missingFields ) ?>>Gender
*/<label>
<label for="genderMale">Male</label>
<input type="radio" name="gender" id="genderMale" value="m"<?php
setChecked( $member, "gender", "m" ) ?>/>
<label for="genderFemale">Female</label>
<input type="radio" name="gender" id="genderFemale" value="f"<?php
setChecked( $member, "gender", "f" ) ?>/>
<label for="favoriteGenre">Favorite genre</label>
<select name="favoriteGenre" id="favoriteGenre" size="1">
<?php foreach ( $member->getGenres() as $value => $label ) { ?>
<option value="<?php echo $value ?>"<?php setSelected( $member,
"favoriteGenre", $value ) ?><?php echo $label ?></option>
<?php } ?>
</select>
<label for="otherInterests">Other interests</label>
<textarea name="otherInterests" id="otherInterests" rows="4"
cols="50"><?php echo $member->getValueEncoded( "otherInterests" ) ?></textarea>
<div style="clear: both;">
<input type="submit" name="action" id="saveButton" value="Save
Changes" />
<input type="submit" name="action" id="deleteButton" value="Delete
Member" style="margin-right: 20px;" />
</div>
</div>
</form>
<h2>Access log</h2>
<table cellspacing="0" style="width: 30em; border: 1px solid #666;">
<tr>
<th>Web page</th>
<th>Number of visits</th>
<th>Last visit</th>
</tr>
<?php
$rowCount = 0;
foreach ( $logEntries as $logEntry ) {
$rowCount++;
?>
<tr><?php if ( $rowCount % 2 == 0 ) echo ' class="alt"' ?>>
<td><?php echo $logEntry->getValueEncoded( "pageUrl" ) ?></td>
<td><?php echo $logEntry->getValueEncoded( "numVisits" ) ?></td>
<td><?php echo $logEntry->getValueEncoded( "lastAccess" ) ?></td>
</tr>
<?php
}
?>
```
```