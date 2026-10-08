```
echo   "<tr>" ;
    echo   "<td>Surname</td>" ;
    echo   "<td><input  value=""   .  $row["surname"]   .  ""   type="text "  ";
    echo   "name="tb_surname"  size="25"></td>" ;
    echo   "</tr>" ;
    echo   "<tr>" ;
    echo   "<td>Title</td>" ;
    echo   "<td><input  value=""   .  $row["title"]   .  ""   type="text "  ";
    echo   "name="tb_title""  size="25"></td>" ;
    echo   "</tr>" ;
    echo   "<tr>" ;
    echo   "<td>Address</td>" ;
    echo   "<td><textarea  rows="2""  name="ta_address""  cols="20"></td>" ;
    echo   $row["address"] ;
    echo   "</textarea></td>" ;
    echo   "</tr>" ;
    echo   "<tr>" ;
    echo   "<td>Phone</td>" ;
    echo   "<td><input  value=""   .  $row["phone"]   .  ""   type="text "  ";
    echo   "name="tb_phone""  size="25"></td>" ;
    echo   "</tr>" ;
    echo   "<tr>" ;
    echo   "<td>Email</td>" ;
    echo   "<td><input  value=""   .  $row["email"]   .  ""   type="text "  ";
    echo   "name="tb_email""  size="25"></td>" ;
    echo   "</tr>" ;
    echo   "</table>" ;
    echo   "<br>" ;
    echo   "<input  type="submit""  value="Save""  name="button">" ;
    echo   "</p>" ;
```

# Pass the id along to the next routine in a hidden field

```
echo   "<input  type="hidden""  name="id2edit""  value=""   .  $id2edit   .  "">" ;
```

```
echo   "</form>" ;
    echo   "</body>" ;
    echo   "</HTML>" ;
    exit( ) ;
    }   # action = show_record
```

```
if  ($action == "store_record")
    {
```