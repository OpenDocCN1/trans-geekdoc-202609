```
}
?>>3</option>
<option value="4"<?php
if ($Number == "4") {
    echo " selected=\"selected\"";
}
?>>4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north"<?php
if (in_array("north", $Section)) {
    echo " selected=\"selected\"";
}
?>North</option>
<option value="south"<?php
if (in_array("south", $Section)) {
    echo " selected=\"selected\"";
}
?>South</option>
<option value="east"<?php
if (in_array("east", $Section)) {
    echo " selected=\"selected\"";
}
?>East</option>
<option value="west"<?php
if (in_array("west", $Section)) {
    echo " selected=\"selected\"";
}
?>West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"><?php
    echo htmlspecialchars($Comments);
?></textarea><br />
<input type="checkbox" name="Terms" value="ok" <?php
if ($Terms ! = "") {
    echo "checked=\"checked\" ";
}
?>/>
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
<?php
```