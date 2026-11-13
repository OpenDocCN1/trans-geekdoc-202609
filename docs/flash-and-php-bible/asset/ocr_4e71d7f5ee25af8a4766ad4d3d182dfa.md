```
if($categoryID == -1 || strlen($categoryID) == 0)
{
trigger_error("Category ID required to return video list");
}
$vidSQL = "";
$rows = array();
// look for specific video?
if($videoID != -1 && strlen($videoID) != 0)
{
$vidSQL = " AND v.id=" . $videoID;
}
$link = $this->getConnection();
$query = sprintf("SELECT
v.name,
v.src,
v.id as 'vid',
c.name as 'cat',
v.description,
v.count
FROM categories c, videos v
WHERE v.catId=c.id
AND v.catId=%d
AND v.active=1 " . $vidSQL, $categoryID);
$result = mysql_query($query, $link);
if(mysql_num_rows($result) == 0)
{
trigger_error("No videos found");
return false;
}
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
array_push($rows, $row);
}
return $rows;
}
}
?>
```

The second class for this example is the Category class, which also has one method. This method is responsible for returning all of the active categories to the video player.