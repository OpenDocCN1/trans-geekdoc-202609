```
$publish_dy = NULL;
$publish_dt = NULL;
$headline = NULL;
$subtitle = NULL;
$byline_prefix = NULL;
$summary = NULL;
$body = NULL;
$story_id = 'NULL';
$submit = NULL;
$author = NULL;
$author_id = NULL;

if (is_assoc($args))
{
    extract($args, EXTR_IF_EXISTS);
}
else
{
    $private_error = 'write_story: error: bad arguments: '
        . var_export($args, TRUE)
        ;
    user_error('Could not update story', E_USER_WARNING);
    return FALSE;
}

start_dbhandler();

// begin transaction
db_connect()->query('begin');

if (empty($story_id))
{
    // if we have no ID value, this is a new story.
    // get the ID value of a new record from story sequence
    $story_id = db_connect()->nextId('story');
    $result = db_connect()->query(
        'insert into stories (story_id,headline) values (?,?)'
        . array($story_id,'Not Yet Updated')
    );
    if (!$result)
    {
        db_connect()->query('rollback');
        user_error(
            'Could not insert new record into stories table'
```