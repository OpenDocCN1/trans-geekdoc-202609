```
echo '<td>' . date( "M j, Y H:i:s", filemtime( $filepath ) ) .
'</td></tr>';
}
}

$dir->close();
?>
</table>
<h2>...or create a new file:</h2>
<form action="text_editor.php" method="post">
<div style="width: 20em;">
<label for="filename">Filename</label>
<div style="float: right; width: 7%; margin-top: 0.7em;">
<input type="text" name="filename" id="filename" style="width: 50%;"
value="" />
<div style="clear: both;">
<input type="submit" name="createFile" value="Create File" />
</div>
</div>
</form>
</body>
</html>
<?php
}
function displayEditForm( $filename="" ) {
if ( !$filename ) $filename = basename( $_GET["filename"] );
if ( !$filename ) die( "Invalid filename" );
$filepath = PATH_TO_FILES . "/$filename";
if ( !file_exists( $filepath ) ) die( "File not found" );
displayPageHeader();
?>
<h2>Editing <?php echo $filename ?> </h2>
<form action="text_editor.php" method="post">
<div style="width: 40em;">
<input type="hidden" name="filename" value="<?php echo $filename ?>" />
<textarea name="fileContents" id="fileContents" rows="20" cols="80"
style="width: 100%;"><?php
echo htmlspecialchars( file_get_contents( $filepath ) )
?></textarea>
<div style="clear: both;">
<input type="submit" name="saveFile" value="Save File" />
<input type="submit" name="cancel" value="Cancel" style=
"margin-right: 20px;" />
</div>
</div>
</form>
</body>
</html>
<?php
}
function saveFile() {
$filename = basename( $_POST["filename"] );
```