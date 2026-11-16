# 7) Create the static HTML structure using placeholders for the content inside the <td> tags.

```
<td>Country Name</td>
<td><a href="admin_cp_update.asp?countryID=CountryID">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.asp?countryID=CountryID">Delete</a></td>
```

This code is the same for both ASP and ColdFusion (except that the file extensions in the href attribute for ColdFusion/PHP should be .cfm/.php rather than .asp), because it is merely static HTML. We're using placeholders here to ensure that we get the HTML syntax right, before adding the dynamic code.

![](bbox=[0.25, 0.29, 0.92, 0.47])

# 8) Replace the three placeholders with dynamic output, as follows.

# In ASP:

```
<td><%=rs_countries("countryName")%></td>
<td><a href="admin_cp_update.asp?countryID=<%=rs_countries"countryID)%>">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.asp?countryID=<%=rs_countries("countryID)%>">Delete</a></td>
```

# In ColdFusion:

```
<td>#countryName#</td>
<td><a href="admin_cp_update.cfm?countryID=#countryID#">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.cfm?countryID=#countryID#">Delete</a></td>
```

# In PHP:

```
<td><?php echo $row_rs_countries['countryName']; ?></td>
<td><a href="admin_cp_update.php?countryID=<?php echo $row_rs_countries['countryID']; ?>">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.php?countryID=<?php echo $row_rs_countries['countryID']; ?>">Delete</a></td>
```