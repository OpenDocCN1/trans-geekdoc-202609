# Letting the User Edit the Database

Movie Type
</td>
<td bgcolor="#ffffff">
<SELECT id="game" name="movie_type" style="width:150px"

```
<php
$sql = SELECT
  movietype_id,
  movietype_label
FROM
  movietype
ORDER BY
  movietype_label
  *;
$result = mysql_query($sql)
or die(\<font color="#FF0000">Query Error</FONT>;.mysql_error());
while ( \$row = mysql_fetch_array($result)) {
echo value=".\$row['movietype_id'].'..\$row['movietype_label'].'\</option>.\r\n";n}
```

</SELECT>
</td>
<tr>
<tr>
<td bgcolor="#ffffff">
Movie Year
</td>
<td bgcolor="#ffffff">
<SELECT name="movie_year">
<option value="">Select a year...</option>

```
<php
for ($year=date("Y"); $year >= 1970 ; $year--) {

<option value="<?php echo $year?"><?php echo $year?></option>
}
```

</SELECT>
</tr>
<tr>
<td bgcolor="#ffffff">
Lead Actor
</td>
<td bgcolor="#ffffff">
<SELECT name="movie_leadactor">
<option value="">Select an actor.../

```
<php
foreach(\$people as \$people_id => \$people_fullname) {

<option value="<?php echo \$people_id?>"><?php echo \$people_fullname?></option>
}
```

171