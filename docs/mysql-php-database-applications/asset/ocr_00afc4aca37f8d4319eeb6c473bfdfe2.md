```
, $p_project
)
. ul_list($tlinks)
:
]
```

Some of the most interesting calls there are the ones to cal.php and list.php. These files contain functions that generate information about the due date and about the task list associated with the project at hand, respectively. They handle some of the bothersome aspects of PHP dates.

It's worth noting, as well, how the project management application deals with projects. Consider the following, for example:

```
$links[] = anchor_tag(
'project.php?project_id=' . $p_project_id
. $p_project
)
. ul_list($tlinks)
:
```

The call to project.php guarantees that the call to the database is made—the details of the project the user is interested in are retrieved and populated into a local object, which can then be manipulated. Here is that code:

```
$fetch_ok = TRUE;
if ($submit == 'Save')
{
 if (empty($p->owner_id))
 {
 print paragraph(array(
 'style' => 'color:red'
 . 'values' => 'Error: No owner is associated with this
 project'
 ));
 $fetch_ok = FALSE;
 }
 else
 {
 $p->write_to_db();
 }
}
if ($fetch_ok)
{
 $p->fetch_from_db();
}]
```