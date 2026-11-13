```
// 'Status set to Re-opened by customer'.

$entry_type_id = entry_type_id('public');
$notes = "Status set to $new_status by ";
if ($entered_by != 'customer' && isset($GLOBALS['staff_name']))
{
    $notes .= $GLOBALS['staff_name'];
}
else
{
    $notes .= $entered_by;
}
.

history_entry($problem_id, $entry_type_id, $entered_by,
    'program', $notes);
}
```

# create_problem_code()

This function creates a unique and highly random 8-character alphanumeric code.

```
function create_problem_code()
{
    return substr(md5(uniqid(rand())),0,8);
}
```

# Scripts

Here are the pages that are actually called by URLs and include statements.

# problem.php

This page does little but call either the enter_problem() or update_problem() function.

```
require_once('header.php');

$params = $_REQUEST;
$params['entered_by'] = 'customer';
$params['source'] = 'web';

if (empty($params['problem_code']))
{
    enter_problem($params);
}
```