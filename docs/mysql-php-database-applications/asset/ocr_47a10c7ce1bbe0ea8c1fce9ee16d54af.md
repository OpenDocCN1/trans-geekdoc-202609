We've added another variable ($level) to this function to keep track of the level. The default value is 1, and it is incremented each time through. The first time through the subject is printed, but in subsequent iterations it is not.

Recursion can be an expensive process: It takes up quite a bit of processor time if it goes too far. To prevent a system from being overwhelmed, you might want to limit the depth of any topic.

Armed with this information, you should be able to get through the display_kids() function. A lot of info is in there to ensure good layout, but other than that it's all pretty readable. Some comments help you get through.

In the code that follows, note the line
$topic_id = (int)$topic_id;

This is an example of casting to an int value. Casting to an int is an easy way of adding safety to your application — you're always sure you'll get an int to work with.

```
function display_kids ($topic_id=0, $level=0)
{
    $topic_id = (int)$topic_id;
    $level = (int)$level;

    // make sure that we aren't caught in some terrible loop
    if ($level > 50)
    {
        $private_error = "trying to display topic $topic_id, level
        is $level - bailing";
        user_error("Error: Recursion too deep". E_USER_ERROR);
        exit;
    }

    // retrieve topic records from the MySQL database having
    // this topic_id value in their parent_id column (i.e. those
    // for whom this topic is the parent_topic

    $query =
    "select topic_id, name, author
    , date_format(create_dt,'%b %e %Y %r') as create_dt
```