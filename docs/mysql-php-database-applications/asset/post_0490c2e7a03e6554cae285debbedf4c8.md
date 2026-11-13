
```
check_session();
if (!isset($_SESSION))
    global $_SESSION;
```

That code looks for a variable called $_SESSION. If the variable isn't around, it creates a new instance of it, effectively putting the user into a new session for tracking purposes.

The function check_session() is interesting. It's one of a library of functions written expressly for this book. It makes sure the user's environment (a browser, typically) is set to support persistent cookies, and if so, it starts a session:

```
function &check_session()
{
    if (!isset($_SESSION))
    {
        trace('$_SESSION is not set');
        if (php_sapi_name() == 'cli')
        {
            global $_SESSION;
            $_SESSION = array();
            trace('can not use cookies, in CLI - set $_SESSION to array()');
        }
        else
        {
            trace('ok to use cookies, call session_start()');
            session_start();
        }
    }
    trace('results of check_session: $_SESSION=', $_SESSION);
    return $_SESSION;
}
```

If the browser does not support cookies, or the user has them turned off, then the code reacts politely, and other operations continue without session tracking.

## Authentication

Now you can have a look at the way the application handles user authentication. The file login.php handles the work of prompting the user for a username and password, using an HTML form. What's interesting is that this form makes use of the variables $_SERVER['PHP_AUTH_USER'] and $_SERVER['PHP_AUTH_PW'], which are PHP values that represent the username and password entered by the user. Alternatively, when the credentials are stored as part of a session, they can be referred to as $_SESSION['PHP_AUTH_USER'] and $_SESSION['PHP_AUTH_PW']. This capability of PHP means that it's possible to refer to the entered values with a little more security than might otherwise exist during the authentication transaction.

The login.php file is called by the session_auth() function (a general-purpose authorization function found in /book/functions/basic), which makes use of the validate_user() function:

```
function validate_user()
{
    static $_defaults = array(
        'username' => NULL
        . 'password' => NULL
    );
    static $_simple = array('username','password');
    $args = func_get_args();
    $p = parse_arguments($args, $_simple, $_defaults);

    session_user()->user = $p['username'];
    session_user()->password = $p['password'];
    return (bool)session_user()->validate();
}
```

validate_user() calls in its last line a method of the User class object returned by session_user() called validate(). The validate() method is where the actual database query (the interrogation of the users table) takes place. Have a look:

```
function validate()
{
    $query = 'select u.* from users u
        left join user_types ut
        on u.user_type_id = ut.user_type_id
        where u.user = ? and u.password = ? ';

    $bind = array($this->user, md5($this->password));
    if ($this->user_type())
    {
        $query .= ' and ut.user_type = ? ';
        $bind[] = $this->user_type();
    }
    $row = $this->dbh()->getRow($query,$bind,DB_FETCHMODE_ASSOC);
    if (count($row) > 0)
    {
        $this->build($row);
        return TRUE;
    }
    return FALSE;
}
```

There's some code to deal with encryption in there (the password is passed as a hash), but essentially that function determines whether the user credentials the user has sent as a result of the login attempt match an entry in the users table. The validate() function returns a Boolean value, to which the lower functions react.

## Viewing projects’ status

The main part of the project management application's user interface is contained in the file index.php. That file concerns itself with displaying status information and other details, including deadline information, about the projects with which the user is associated. In doing that, the main interface page must do a lot of database queries and a fair bit of text-formatting work. Much of this work is delegated to other functions (many of them in other PHP files), which makes the application more modular and easier to maintain.

In index.php you see a strategy that's commonplace across all the display scripts in this application (and, indeed, in most HTML-generating PHP scripts everywhere). Early on, the script calls the start_page() function, like this:

```
print start_page('Project Management Example');
```

That function, defined in an imported file, does the work of generating opening HTML. The argument is inserted as the HTML TITLE element.

With that done, the application proceeds to determine if the user accessing the page is an administrator:

```
if (!session_user()->is_admin())
```

If so, then the status of all current projects is displayed; if the current user is not an administrator, then only the projects to which that user is assigned are displayed.

To query the database, the application makes use of a function called dbh(), which is contained in base.class.php (imported everywhere). The dbh() function establishes the link to the database and enables queries to be run against it:

```
function dbh()
{
    static $dbh = NULL;
    if ($dbh == NULL)
    {
        $dbh = db_connect($this->appname);
        if ($dbh == NULL)
        {
            user_error('Received NULL db connection',
            E_USER_ERROR);
            return FALSE;
        }
        $dbh->setFetchMode(DB_FETCHMODE_ASSOC);
    }
    return $dbh;
}
```

With dbh() invoked, the index page can send a query to it:

```
$rows = session_user()->dbh()->getAll($query, $bind);
```

The index page gets a set of rows back. Those rows, looped through, form the bulk of what's on the index page. Here is the looping logic:

```
foreach ($rows as $row)
{
    extract($row, EXTR_OVERWRITE|EXTR_PREFIX_ALL, 'p');

    $tlinks = array();
    $tlinks[] = anchor_tag(
        'tasks/cal.php?project_id='.$p_project_id
        , 'Calendar'
    );
    $tlinks[] = anchor_tag(
        'tasks/list.php?project_id='.$p_project_id
        , 'Task List'
    );

    $query = 'select t.*, u.user as owner
        from tasks t left join users u on t.owner_id = u.user_id
        where t.project_id = ?
        and t.status_id <> ?
        and (t.due_dt >= curdate() - interval 3 day
        and t.due_dt <= curdate() + interval 3 day)
    ';
    $bind = array($p_project_id,$cancelled_id);
    $events = session_user()->dbh()->getAll($query,$bind);
    $elist = array();
    if (count($events) > 0)
    {
        $elinks = array();
        $today = strtotime(date('Y-m-d',strtotime('today')));
        foreach ($events as $e)
        {
            extract($e, EXTR_OVERWRITE|EXTR_PREFIX_ALL, 'e');
            session_user()->format_dt($e_due_dt);
            $e_task_tag = anchor_tag(
                'tasks/view_task.php?task_id='. $e_task_id
                , $e_task
            );
            $its_yours = FALSE;
            if ($e_owner_id == session_user()->user_id)
            {
                $e_owner = 'You';
                $its_yours = TRUE;
            }
            if ($e_status_id == $done_id)
            {
                $e_text = "$e_owner finished $e_task_tag on $e_due_dt";
            }
            elseif ($e_status_id == $slipped_id)
            {
                $e_text = "$e_owner slipped $e_task_tag to $e_due_dt";
            }
            else
            {
                $e_due_ts = strtotime($e_due_dt);
                $on_time = ($today <= $e_due_ts);
                if ($its_yours)
                {
                    $due_word = $on_time ? 'are' : 'were';
                }
                else
                {
                    $due_word = $on_time ? 'is' : 'was';
                }
                $e_text = "$e_owner $due_word supposed to finish $e_task_tag on $e_due_dt";
            }
            $elinks[] = $e_text;
        }
        $tlinks[] = '<b>Alerts:</b>'.ul_list($elinks);
    }
}

$links[] = anchor_tag(
    'project.php?project_id=' . $p_project_id
    , $p_project
)
. ul_list($tlinks);
```

Some of the most interesting calls there are the ones to cal.php and list.php. These files contain functions that generate information about the due date and about the task list associated with the project at hand, respectively. They handle some of the bothersome aspects of PHP dates.

It's worth noting, as well, how the project management application deals with projects. Consider the following, for example:

```
$links[] = anchor_tag(
    'project.php?project_id=' . $p_project_id
    , $p_project
)
. ul_list($tlinks);
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
            . 'values' => 'Error: No owner is associated with this project'
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
}
```
