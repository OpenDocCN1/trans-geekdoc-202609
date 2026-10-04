# Building a Content Management System

And they all lived happily ever after. The End.

```
Next comes pending.php:<input type="hidden" name="article"
value="<?php echo $_GET['article'] ?> * / />
</p>

</form>

<?php require_once 'footer.php'; ?>
```

Feeling a little déjà vu? Good.

```
<php
require_once 'conn.php';
require_once 'header.php';
```

Oooh... an associative array. Other server-side scripting languages like ASP/VBScript do not use associative arrays, and we think they are very useful things. What are you going to use this one for? Read on, dear reader, and we'll show you.

```
$a_ArtTypes = array(
"Pending" => "submitted",
"Published" => "published"
);
```

The following is where you use your associative array. You are displaying, or submitted, articles, and then displaying ones. In the interests of convenience (because we're lazy, remember?), you loop through the array and substitute the appropriate values where necessary. The $k holds the key value. We also set $i to -1 because it will be incremented immediately inside the loop:

```
echo "<h2>Article Availability</h2>\n";n$i=-1;
foreach ($a_ArtTypes as $k => $v) {
	...right here. $i++;
```

Here's your first use of the array key. This first pass through, it will read "Pending Articles". Next time through, it will read "Published Articles". Clever

```
echo "<h3> $k . " Articles</h3>\n";
```

Notice that we use $v in what follows to create the field date_submitted in the first loop, and date_published in the second. We are also using $i to first compare is_published to 0, and then to 1 in the next loop.

```
echo "<p\n"
echo " <div class='scroller'>\n"

$sql = "SELECT article_id, title, date.".$v
	FROM cms_articles *"
	"WHERE is_published=". $i
```