

```php
$pos = $tmp;
$trimmed = TRUE;
} else {
    $pos = strlen($theText);
    $trimmed = FALSE;
    break;
}
$theText = substr($theText, 0, $pos);

if (strlen($theText) > $lmt) {
    $theText = substr($theText, 0, $lmt);
    $theText = substr($theText, 0, strrpos($theText, ' '));
    $trimmed = TRUE;
}

if ($trimmed) {
    $theText = '...';
    return $theText;
}
```

```php
function msgBox($m, $t, $d="*index.php", $s="Info") {
    $theMsg = "<div id='requestConfirmation" . $s . "'>";
    $theMsg = "<h2>" . $t . "</h2>\n";
    $theMsg = "<p>" . $s . "</p>\n";
    $theMsg = "<a href=" . $d . " * ";
    $theMsg = "<span class='buttonlink'>";
    $theMsg = "Yes</a>";
    $theMsg = "<a href=index.php class='buttonlink'>";
    $theMsg = "No</a></p>";
    $theMsg = "</div>";
    return $theMsg;
}
```

```php
function getForm($id) {
    $sql = "SELECT forum_name as name, forum_desc as description, " .
    "forum_moderator as mod " .
    "FROM forum_forum " .
    "WHERE id = " . $id . ";
    $result = mysql_query($sql)
    or die(mysql_error()) . "<br>";
    $row = mysql_fetch_array($result);
    return $row;
}
```

```php
function getForumID($topicid) {
    $sql = "SELECT forum_id FROM forum_posts WHERE id=$topicid";
    $result = mysql_query($sql)
    or die(mysql_error()) . "<br>";
    $row = mysql_fetch_array($result);
    return $row['forum_id'];
}
```

```php
function breadcrumb($id, $getfrom="F") {
    $sep = "<span class='bcsep'>";
    if ($getfrom == "p") {
        $sql = "SELECT forum_id, subject FROM forum_posts WHERE id = " . $id . ";";
        $result = mysql_query($sql)
        or die(mysql_error()) . "<br>";
        $row = mysql_fetch_array($result);
        $id = $row['forum_id'];
        $topic = $row['subject'];
    }
    $row = getForm($id);
    $bc = "<a href=index.php?Home</a>$sep";
    switch ($getfrom) {
        case "P":
            $bc = "<a href=forum.php?f=$id'>" . $row['name'] . "</a>$sep";
            break;
        case "F":
            $bc = $row['name'];
            break;
        default:
            return "<h4 class='breadcrumb'>" . $bc . "</h4>";
    }
}

function showTopic($topicid, $showfull=TRUE) {
    global $conn;
    global $userid;
    global $limit;
    if (isset($_GET['page'])) {
        $page = $_GET['page'];
    } else {
        $page = 1;
    }
    if ($limit == "*") $limit = 25;
    $start = ($page - 1) * $limit;
    if (isset($_SESSION['user_id'])) {
        echo topicBar($topicid, getForumID($topicid), "right");
    }
    $sql = "SELECT SQL_CALC_ROWS p.id, p.subject, p.body, p.date_posted, p.date_update, u.name as author, u.id as author_id, u.signature as signature, c.count as postcount, p.forum_id as forum_id, u2.moderator as mod, p.update_id, u2.name as updated_by
    FROM forum_forum f
    JOIN forum_posts p ON f.id = p.forum_id
    JOIN forum_users u ON u.id = p.author_id
    LEFT JOIN postcount c ON u.id = c.user_id
    LEFT JOIN forum_users u2 ON u.id = p.update_id
    WHERE (p.post_id = $topicid OR p.topicid = $topicid)
    ORDER BY p.post_id, p.date_posted
    LIMIT $start, $limit";
    $result = mysql_query($sql, $conn);
    if (mysql_error($conn)) {
        echo $sql;
    }
    $pagelink = paginate($limit);
    if (mysql_num_rows($result) == 0) {
        $msg = "There are currently no posts. Would you like to be the first person to create a thread?";
        $title = "No Posts...";
        $dest = "compose.php?formid=" . $formid;
        $sev = "Info";
        $message = msgbox($msg, $title, $sev);
    } else {
        echo "<table class='formtable' cellspacing='0'>";
        echo "<td cellpadding='2'><tr>";
        echo "<th class='author'>Author</th>";
        echo "<th class='post'>Post</th>";
        echo "</tr></tr>td";
        while ($row = mysql_fetch_array($result)) {
            $lastupdate = "";
            $editlink = "";
            $dellink = "";
            $replylink = "&nbsp;";
            $postcount = "";
            $date = "";
            $sig = "";
            if ($showfull) {
                echo "<tr class='body'>";
                if (isset($_SESSION['user_id'])) {
                    $replylink = "<a href='compose.php?formid=" . $row['id'] . "&topicid=$topicid&rid=" . $row['id'] . "'> class='button'>Reply</a>&nbsp;";
                } else {
                    $replylink = "";
                }
                if ($row['update_id'] > 0) {
                    $lastupdate = "<p class='smallNote'>Last updated: " . $row['date_updated'] . " by " . $row['update_by'] . "</p>";
                }
                if (($userid == $row['author_id']) || ($userid == $row['mod']) || ($_SESSION['acl_1'] == 2)) {
                    $editlink = "<a href='compose.php?formid=" . $row['id'] . "&edit&post=" . $row['id'] . "'> class='button'>EDIT</a>&nbsp;";
                    $dellink = "<a href='trans-affirm.php?id=" . $row['id'] . "'> class='button'>DELETE</a>&nbsp;";
                }
            }
        }
    }
}
```

