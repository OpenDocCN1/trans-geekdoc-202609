
## FUNCTIONS FROM /CONTENT/FUNCTIONS.PHP

These will be used throughout the application. There will be many references to Chapter 9 in this section.

### LIST_STORIES()

As mentioned in Chapter 10, in MySQL version 3.23 you can work around MySQL's lack of support for unions by creating temporary tables. However, we developed all of the applications on this book using MySQL version 3.22, which does not support the create temporary table feature. This gets to be a problem when you need to print out the contents of two queries within a single table. If you look at the source code on the CD-ROM, you will see that the pages start by printing all of the stories currently within the workflow that the current user has access to. Following that, if the user has access to live stories, the live stories should be printed within the same table.

To create this table, we need to call this function twice, passing the result identifier of the query as the first argument. If the query has at least one row, the table header will be printed, and $in_table will be set to 1. The next time the function is called, the value of $in_table will be passed as the second argument. If the value of $in_table is 1 the header will not print.

Again, if you are using MySQL version 3.23, use the create temporary table feature.

```
function list_stories($result, $in_table="")
{
    if (empty($in_table)) { $in_table = 0; }
    while ($row = mysql_fetch_array($result))
    {
        if ($in_table == 0)
        {
            print subtitle("Edit Stories");
            print start_table();
            print table_row("<b>Stage</b>"
                , "<b>Story</b>"
                , "<b>Publish Date</b>"
            );
            $in_table = 1;
        }
        print table_row($row["stage"],
            anchor_tag("edit_story.php?story_id=".$row["story_id"]
                , $row["headline"]
            )
            , $row["publish_dt"]
        );
    }
    return $in_table;
}
```

### FETCH_STORY()

This function, like most of those in this section, makes use of the `fetch_record()` function, which is discussed in Chapter 9. In the call to the `fetch_record()`, a story_id, which is the primary key of the table, is specified. Therefore, you can be sure that the query created by fetch_record will have only one row. The query in fetch_record will get all columns for the story_id.

```
function fetch_story ($story_id="")
{
    $result = fetch_record("stories","story_id",$story_id);
    return $result;
}
```

Because there is only one row, the fetch_record will call the `set_result_variable()` function (also discussed in Chapter 9). That function will make all of the columns for that story_id available as globals. From the schema in Figure 11-7, you can see that those columns are story_id int, stage_id, publish_dt, headline, subtitle, byline_prefix, summary, and body.

So after running fetch_story you can access any of the columns as global variables.

```
fetch_story(1);
echo $headline;
```

![](img/de0823012275cf4ceebdb822a56e6b71_328_0.png)

The `fetch_record()` function is discussed in Chapter 9.

### FETCH_STORY_VERSION()

This function works almost identically to the `fetch_story()` function just described, the only difference being that multiple attributes are being passed to the fetch_record function. These are added to the SQL statement. Note that the modify_dt column is 14 digits (YYYYMMDDHHMMSS). The combination of a story_id and the second at which it was modified makes for a pretty good two-column primary key, so any query here should only return one row.

```
function fetch_story_version ($story_id="",$modify_dt="")
{
    $result = fetch_record("story_versions"
        ,array("story_id","modify_dt")
        ,array($story_id,$modify_dt)
    );
    return $result;
}
```

### FETCH_AUTHOR()

This function works similarly to the `fetch_story` function. It creates global variables from a row retrieved from the author table.

```
function fetch_author ($author_id="")
{
    $result = fetch_record("authors","author_id",$author_id);
    return $result;
}
```

### FETCH_CONTENT_USER()

This function also works identically to the `fetch_story` function. It creates global variables from the row retrieved from the content_user table.

```
function fetch_content_user ($user_id="")
{
    $result = fetch_record("content_users","user_id",$user_id);
    return $result;
}
```

### FETCH_CONTENT_STAGE()

Once again, this function works identically to `fetch_story`. It creates global variables from a row retrieved from the content_stages table.

```
function fetch_content_stage ($stage_id="")
{
    $result = fetch_record("content_stages","stage_id",$stage_id);
    return $result;
}
```

## Interesting Code Flow

Since most of the more complicated stuff in this application has to do with maintaining users and stages, we will start the breakdown of code with the pages that take care of these stages. Later we will move on to the other features performed by this application.

### content/authenticate.php

As we already mentioned, this application differs from the previous ones in that each user will be logging into the database with his or her own username and password. The script that performs this login will need to be just a touch more flexible than the one you used in the other applications.

This application is going to use the same 401-type authentication used in the previous examples, but here the values for $PHP_AUTH_USER and $PHP_AUTH_PW will also be the values used to log into the database.

![](img/de0823012275cf4ceebdb822a56e6b71_330_0.png)

> $PHP_AUTH_USER and $PHP_AUTH_PW are only available if PHP is installed as an Apache module. If you are working on Windows, you will not be able to use this type of authentication.

The header.php file, which is included in every page in the content management system, contains the following code:

```php
if ($authentication == "admin")
{
    include "admin_authenticate.php";
}
else
{
    include "authenticate.php";
}
$this_username = $PHP_AUTH_USER;
```

This if ... else block determines which authentication script will run. In pages that require administrative access you will see a variable assignment like the following prior to the include of header.php.

```php
$authentication = "admin";
```

If this does not exist, the authenticate.php will be included. Here are the contents of the authenticate.php file.

```php
$realm = "Netsloth Content";
$errmsg = "You must enter a valid name & password to access this function";
if (empty($PHP_AUTH_USER)
    || ( !empty($newuser) && $olduser == $PHP_AUTH_USER )
)
{
    $what = empty($PHP_AUTH_USER) ? "login" :
        "newuser($newuser,$olduser)";
    authenticate($realm,$errmsg. ":".$what);
}
```

```
$mylink = @mysql_connect("localhost", $PHP_AUTH_USER, $PHP_AUTH_PW)
    or authenticate
    ($realm,"Could not login to db as $PHP_AUTH_USER");

mysql_select_db("netsloth");
```

As you look at the preceding code, keep in mind that in this script people using the application need to be able to change the usernames and passwords that they are using to log into the application—i.e., log in as a different user. If you go through the script step by step, you should see how to do it. We'll go through it line-by-line after one quick explanation.

Within the index.php page, there is a submit button that, when pressed, will indicate that the user wants to login in under a different username and password. The following creates the form with the submit button.

```
print paragraph(
    start_form("index.php")
    , hidden_field("olduser",$PHP_AUTH_USER)
    , submit_field("newuser","Log In As New User")
    , end_form()
);
```

Using the functions described in Chapter 9, this code creates a form, that, if submitted, sends the variables $olduser and $newuser back to the index.php page. When the form is submitted and the variables are sent, they will hit this portion of the authenticate.php page.

```
if (empty($PHP_AUTH_USER)
    || ( !empty($newuser) && $olduser == $PHP_AUTH_USER )
)
```

The preceding if block will test true under two conditions. First, if the user has not yet logged in, because in that case $PHP_AUTH_USER will be empty. The other condition comes from the form we just discussed. If that submit button is pressed, $newuser will not be empty and $olduser will contain the value of $PHP_AUTH_USER, meaning the user wishes to change her login name and password. If either of these is true, the following code will run:

```
{
    $what = empty($PHP_AUTH_USER) ? "login" :
        "newuser($newuser,$olduser)";
    authenticate($realm,$errmsg.":".$what);
}
```
