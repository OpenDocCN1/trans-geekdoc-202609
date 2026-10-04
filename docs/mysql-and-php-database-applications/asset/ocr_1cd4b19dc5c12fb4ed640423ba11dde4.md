# Part IV: Not So Simple Applications

FETCH_STORY() This function, like most of those in this section, makes use of the fetch_record() function, which is discussed in Chapter 9. In the call to the fetch_record(), a story_id, which is the primary key of the table, is specified. Therefore, you can be sure that the query created by fetch_record will have only one row. The query in fetch_record will get all columns for the story_id.

```
function fetch_story($story_id=""
{
  $result = fetch_record("stories","story_id",$story_id);
  return $result;
}
```

Because there is only one row, the fetch_record will call the set_result_variable() function (also discussed in Chapter 9). That function will make all of the columns for story_id available as globals. From the schema in Figure 11-7, you can see that columns are story_id int, stage_id, publish_dt, headline, subtitle, inline_prefix, and body.
After running fetch_story you can access any of the columns as global variables.

```
fetch_story(1);
echo $headline;
```

> The fetch_record() function is discussing in Chapter 9.

![](bbox=[0.167, 0.552, 0.227, 0.592])

FETCH_STORY_VERSION() This function works almost identically to the fetch_story() function just described, the only difference is that multiple attributes are being passed to the fetch_record function. These are added to the SQL statement. Note that the modify_dt column is 14 digits (YYYYMMDDHHMMSS). The combination of story_id and the second at which was modified for a pretty good two-column primary key, so any query here should return one row.

```
function fetch_story_version($story_id="",$modify_dt=""
{
  $result = fetch_record("story_versions")
  array("story_id","'$modify_dt")
);
  return $result;
```