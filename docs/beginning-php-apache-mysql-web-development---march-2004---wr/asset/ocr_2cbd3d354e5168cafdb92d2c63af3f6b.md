| <td bgcolor="#ffffff" width="30%">\nMovie Name\n</td>\n <td bgcolor="#ffffff" width="70%">\n<input type="text" name="movie_name" value="<?php echo $movie_name?>">
</td>\n</tr>\n <tr>\n <td bgcolor="#ffffff">\nMovie Type\n</td>\n <td bgcolor="#ffffff">\n<SELECT id="game" name="movie_type" style="width:150px">
<option value="** Select a type...
php$sql = SELECT \n'motietype_id',\n'motietype_label'\nFROM\n'motietype'\nORDER BY\n'motietype_label'\nn$result = mysqli_query($sql)\n or die(\<font color="#FF0000">?Query Error</font>).$mysql_error($result)) {\n while ($row = mysqli_fetch_array($result)) {\n if ($row['motietype_id'] == $movie_type){\n $selected = SELECTED;\n } else {\n $selected = **;\n }}\n echo \"<OPTION\nvalue="**'.$row['motietype_id'].'.'.$selected.'.$row['motietype_label'].'.</OPTION>\"\n\r\n";\n }
</SELECT>
</td>\n</tr>\n <tr>\n <td bgcolor="#ffffff">\nMovie Year\n</td>\n <td bgcolor="#ffffff">\n<SELECT name="**movie_year">
<option value="** Select a type..."
php\nfor ({$year=date('Y')); ;$year = 1970 ;$year-{\n if {$ Year == $movie_year}{\n $selected = SELECTED;\n } else {\n $selected = **;\n }}\n}

# Validating User Input

195