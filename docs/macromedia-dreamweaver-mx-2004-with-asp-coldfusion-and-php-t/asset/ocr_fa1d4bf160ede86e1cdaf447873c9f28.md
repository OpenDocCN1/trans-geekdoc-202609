![](bbox=[0.063, 0.072, 0.723, 0.453])

# 7) Amend the block of code you added in step 6 so that it incorporates a looping structure.

In ASP:

```
<%
Do Until rs_regions.EOF
   Response.Write("<option value="" & rs_regions("regionID") & "">" &
   =>rs_regions("regionName") & "</option>")
   rs_regions.MoveNext
Loop
%>
```

In ColdFusion:

```
<cfoutput query="rs_regions">
<option value="#rs_regions.regionID#">#rs_regions.regionName#</option>
</cfoutput>
```