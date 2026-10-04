```
<table border=0 width=750*spacing=1 cellpadding=3 bgcolor="#353535*
align="center">
<tr>
<td bgcolor="#ffffff" width="30%">
Name
</td>
<td bgcolor="#ffffff" width="70%">
<INPUT type="TEXT" name="Name">
</td>
<tr>
<td bgcolor="#ffffff">
Item Type
</td>
<td bgcolor="#ffffff">
<INPUT type="radio" name="type" value="Movie:Movie" CHECKED
Movie<BR>
<INPUT type="radio" name="type" value="Person:Actor"
Actor<BR>
<INPUT type="radio" name="type" value="Person:Director"
Director<BR>
</td>
<tr>
<td bgcolor="#ffffff">\nMovie type (if applicable)
</td>
<td bgcolor="#ffffff">
<SELECT name="MovieType">
<option value="" SELECTED>Movie type...</option>
<option value="Action">Action</option>
<option value="Drama">Drama</option>
<option value="Comedy">Comedy</option>
<option value="Sci-Fi">Sci-Fi</option>
<option value="War">War</option>
<option value="Other">Other...</option>
</SELECT>
</td>
<tr>
<td bgcolor="#ffffff" width="50%">
Display Debug Dump
</td>
<td bgcolor="#ffffff" width="50%">
<INPUT type="checkbox" name="Debug" CHECKED
</td>
<tr>
<td bgcolor="#ffffff">
<INPUT type="SUBMIT" name="Submit" value="Search">
<INPUT type="SUBMIT" name="Submit" value="Add">
</td>
</tr>
</table>
```