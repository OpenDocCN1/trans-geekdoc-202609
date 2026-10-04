# Validating User Input

```
$selected = **;
}
echo '<OPTION
value=".'$row['motype_id'].'.**'.$selected.'.'.$row['motype_label'].'</OPTION>'
"\r\n";
}?>
</SELECT>
</td>
<tr>
<tr>
<td bgcolor="#ffffff">
Movie Year
</td>
<td bgcolor="#ffffff">
<SELECT name="movie_year">
<option value="** SELECTED>Select a year...</option>
<?php
for ($year=date('Y'); $year >= 1970; $year--){
    if ($year == $movie_year) {
        $selected = " SELECTED";
    } else {
        $selected = " **";
    }
}?>
<option value="<?php echo $year?>"><?php echo $selected?>>$php echo
$year?></option>
}</SELECT>
</td>
<tr>
<td bgcolor="#ffffff">
Lead Actor
</td>
<td bgcolor="#ffffff">
<SELECT name="movie_leaderactor">
<option value="** SELECTED>Select an actor...</option>
<?php
foreach($people as $people_id => $people_fullname) {
    if ($people_id == $movie_leaderactor) {
        $selected = " SELECTED";
    } else {
        $selected = " **";
    }

} else
?>
<option value="<?php echo $people_id?>"><?php echo $selected?>>$php echo
$people_fullname?></option>
<?php
}
?>
```

205