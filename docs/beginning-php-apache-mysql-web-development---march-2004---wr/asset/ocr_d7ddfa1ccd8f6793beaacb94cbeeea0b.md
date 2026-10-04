```
$pcount = <br /><span class='textsmall'>Posts: * 
  ($row['postcount']==)?"0":$row['postcount']) . "</span>";
  $date = $row['date_posted'];
  $sig = ($row['sig']!=)?"<p class='sig">
    bbcode(nl2br($row['sig']));
" . "</p>";
} else {
  $body = trimBody($body);
}
  $rowclass = ($row == "row1")?"row2":"row1";
  echo "<td class='$rowclass">";
  echo "<td class='author"> . $row['author'];";
  echo $pcount;
  echo "<td class='post'> . $post . '</p>";
  if (isset($_SESSION['user_id']))
  and (isset($_SESSION['last_login']) < $row['date_posted]))
    echo NEW_POST . " ";
  if (isset($_GET['page']))$pagelink = "&page=" . $_GET['page'];
  echo "<a name=" . $row['id'] . '">" 
    'href="viewtopic.php?" . $topicid . $pagelink . "#post" . $row['id'] . '\'>" . $row['subject'] . "</a>";
  if (isset($row['subject']))
    echo "<strong>" . $row['subject'] . "</strong>";
  echo "<p>" . bbcode(nl2br(htmlspecialchars($body))) . "</p>";
  echo $sig;
  echo $lastupdate;
  echo "</td class='$rowclass'>><td class='authorfooter">";
  echo " .</td><td class='threadfooter">";
  echo $replylink;
  echo $editlink;
  echo $dellink;
  echo "</td></tr>\n";
}
  echo "</table>";
  echo $pagelinks;
  echo "<p>" . NEW_POST . " = New Post&nbsp;&nbsp;&nbsp;&nbsp;"
  echo $POSTLINK. . " Post link (use to bookmark)</p>";
}

function isParent($page) {
  $currentpage = $_SERVER['PHP_SELF'];
  if (strpos($currentpage, $page) === false) {
    return FALSE;
  } else {
    return TRUE;
  }
}

function replyBar($topicid, $forum, $pos="right") {
  $html = "<p class='buttonBar ' . $pos . '">";
  if ($topicid > 0)
```