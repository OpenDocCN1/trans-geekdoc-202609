```
echo ' selected="selected"';
}
?>>PHP 5.2</option>
<option value="php53"><?php
if (in_array('php53', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>>PHP 5.3</option>
<option value="php54"><?php
if (in_array('php54', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>>PHP 5.4</option>
</select><br />
<input type="submit" />
</form>
</body>
</html>
```

# Processing Graphical Submit Buttons

```
<?php
if (isset($_POST['Submit_x']) &&
isset($_POST['Submit_y'])) {
    printf('<h1>You clicked at the following
coordinates: x-%s, y-%s</h1>',
        htmlspecialchars($_POST['Submit_x']),
        htmlspecialchars($_POST['Submit_y'])
    );
} else {
?>
```