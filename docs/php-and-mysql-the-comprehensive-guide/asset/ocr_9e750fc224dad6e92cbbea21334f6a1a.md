```
$command = oci_parse($db, $sql);
oci_bind_by_name($command, ":Heading", $_POST["Heading"]);
oci_bind_by_name($command, ":Comment", $_POST["Comment"]);
oci_bind_by_name($command, ":Name", $_POST["Name"]);
oci_bind_by_name($command, ":Email", $_POST["Email"]);
oci_bind_by_name($command, ":Date", time());
if (oci_execute($command, OCI_DEFAULT)) {
  $sql_id = "SELECT guestbook_id.CURRVAL AS id FROM DUAL";
  $command_id = oci_parse($db, $sql_id);
  if (oci_execute($command_id, OCI_DEFAULT)) {
    oci_fetch($command_id);
    $id = oci_result($command_id, "id");
  } else {
    $id = "";
    echo "Error!";
  }
echo "Entry added.
<a href=\"gb-admin?id=$id\">Edit</a>";
} else {
echo "Error!";
}
oci_commit($db);
oci_close($db);
} else {
echo "Error!";
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

# Listing 22.12 Data Can Be Entered ("gb-enter.php")

# 22.3.3 Output Data

Reading out the guestbook is again easy to implement. As the date field is numerical and a later date also has a higher value, sorting by this field ensures that the entries can be output in reverse chronological order.