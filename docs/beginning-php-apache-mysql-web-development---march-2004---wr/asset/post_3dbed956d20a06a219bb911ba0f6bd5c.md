
## Chapter 12

2. Now you need to create your database tables. You can do this on your MySQL server, or you can simply use the following cmstables.php file. It will create your tables, as well insert your first user so that you can begin admining the site immediately.

```php
<?php
require_once 'conn.php';

$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_access_levels (
access_lvl1 tinyint(4) NOT NULL auto_increment,
access_name varchar(50) NOT NULL default '',
PRIMARY KEY (access_lvl1)
EOS;
$result = mysql_query($sql) or die(mysql_error());

$sql = "INSERT IGNORE INTO cms_access_levels\nVALUES (1, 'User');";
$result = mysql_query($sql) or die(mysql_error());
$sql = "INSERT IGNORE INTO cms_access_levels\nVALUES (2, 'Moderator');";
$result = mysql_query($sql) or die(mysql_error());
$sql = "INSERT IGNORE INTO cms_access_levels\nVALUES (3, 'Administrator');";
$result = mysql_query($sql) or die(mysql_error());

$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_articles (
article_id int(11) NOT NULL auto_increment,
author_id int(11) NOT NULL default '0',
is_published tinyint(1) NOT NULL default '0',
date_submitted datetime NOT default '0000-00-00 00:00:00',
date_published datetime NOT default '0000-00-00 00:00:00',
title varchar(255) NOT NULL default '',
body text NULL,
PRIMARY KEY (article_id),
KEY IdArticle (author_id,date_submitted),
FULLTEXT KEY IdText (title,body)
EOS;
$result = mysql_query($sql) or die(mysql_error());

$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_comments (
comment_id int(11) NOT NULL auto_increment,
article_id int(11) NOT NULL default '0',
date datetime NOT default '0000-00-00 00:00:00',
user_id int(11) NOT NULL default '0',
comment text NULL,
PRIMARY KEY (comment_id),
KEY IdComment (article_id)
EOS;
$result = mysql_query($sql) or die(mysql_error());

$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_users (
  user_id int(11) NOT NULL auto_increment,
  email varchar(255) NOT NULL default '',
  passwd varchar(50) NOT NULL default '',
  name varchar(100) NOT NULL default '',
  access_lvl tinyint(4) NOT NULL default '1',
  PRIMARY KEY (user_id),
  UNIQUE KEY uniq_email (email)
)
EOS;
$result = mysql_query($sql) or die(mysql_error());

$admin_mail = "admin@yoursite.com";
$admin_pass = "admin";
$admin_name = "Admin";

$sql = "INSERT IGNORE INTO cms_users VALUES ('$admin_mail', '$admin_pass', '$admin_name', 3);";
$result = mysql_query($sql) or die(mysql_error());

echo "<head><title>CMS Tables</title></head><body>";
echo "CMS Tables created. Here is your login information:";
echo "<ul><li><strong>login:</strong> " . $admin_mail . "</li>";
echo "<li><strong>password:</strong> " . $admin_pass . "</li>";
echo "</ul><a href='login.php'>Login</a> to the site now.";
echo "</body>";
?>
```

3. Some functions are used on many pages. Those are included in the file output.php, which is included at the top of each appropriate page:

```php
<?php
function trimBody($text, $lmt=500, $s_char="\n", $s_cnt=2) {
  $pos = 0;
  $trimmed = FALSE;
  for ($i=1; $i <= $s_cnt; $i++) {
    if ($tmp = strpos($text, $s_char, $pos)) {
      $pos = $tmp;
      $trimmed = TRUE;
    } else {
      $pos = strlen($text) - 1;
      $trimmed = FALSE;
      break;
    }
  }
  $text = substr($text, 0, $pos);

  if (strlen($text) > $lmt) {
    $text = substr($text, 0, $lmt);
    $theText = substr($text, 0, strrpos($text, '\''));
    $trimmed = TRUE;
  }
  if ($trimmed) $text .= '...';
  return $text;
}

function outputStory($article, $only_snippet=FALSE) {
  global $conn;

  if ($article) {
    $sql = 'SELECT ar.*, us.name * 
            FROM cms_articles ar 
            LEFT OUTER JOIN cms_users us 
            ON ar.author_id = us.user_id 
            WHERE ar.article_id = ' . $article . ';';
    $result = mysql_query($sql, $conn);

    if ($row = mysql_fetch_array($result)) {
      echo '<h3>' . htmlspecialchars($row['title']) . '</h3>';
      echo '<h5 class="byline">:' . htmlspecialchars($row['name']) . '</h5>';
      echo '<div class="pubdate">';
      if (date("F Y", strftime($row['date_published'])) == 1) {
      } else {
        echo 'not yet published';
      }
      echo '</div>';

      if ($only_snippet) {
        echo '<p>';
        echo nl2br(htmlspecialchars(trim($row['body'])));
        echo '</p>';
        echo '<h5><a href="viewarticle.php?article=' . $row['article_id'] . '">Full Story...</a></h5>';
      } else {
        echo '<p>';
        echo nl2br(htmlspecialchars($row['body']));
        echo '</p>';
      }
    }
  }
}

function showComments($article, $show_link=TRUE) {
  global $conn;
  if ($article) {
    $sql = "SELECT co.*, user.name, user.email 
            FROM comments co 
            LEFT OUTER JOIN cms_users user 
            ON co.user_id = user.user_id 
            WHERE co.article_id = " . $article . " 
            ORDER BY co.comment_date DESC";
    $result = mysql_query($sql, $conn);
    if (!$result) {
      die("Could not look up comments: " . mysql_error($conn));
    }

    if (mysql_num_rows($result)) {
      echo '<h4>';
      if ($show_link && isset($_SESSION['user_id'])) {
        echo '<a href='comment.php?article=' . $article . '">Add one?</a>';
      }
      echo '</h4>';
      echo '<div class="scroller">';
      while ($row = mysql_fetch_array($result)) {
        echo '<span>' . htmlspecialchars($row['name']) . '</span>';
        echo '<span class="commentDate">' . date("F j, Y, H:i:s", strtotime($row['comment_date'])) . '</span>';
        echo '<p>' . nl2br(htmlspecialchars($row['commentText'])) . '</p>';
      }
      echo '</div>';
    }
  }
}
?>
```

## Building a Management System

4. Two files are included in various pages, header.php and footer.php. Enter next.

```php
<?php
session_start(); ?>
<html>
<head>
<title>BFAM CMS</title>
</head>
<body>
<div id="header">
  <div id="logo">
    <h1>Comic Book Appreciation</h1>
  </div>
  <?php
  if (isset($_SESSION['name'])) {
    echo '<div id="welcome">Currently logged in as: ' . $_SESSION['name'];
    echo '</div>';
  }
  ?>
</div>
<div id="navright">
  <form method="get" action="search.php">
    <p class="head">Search</p>
    <p>
    <input id="keywords" type="text" name="keywords">
    <?php
    if (isset($_GET['keywords'])) {
      echo 'value=\'' . htmlspecialchars($_GET['keywords']) . '\';
    }
    ?>
    <input id="searchbutton" class="submit" type="submit" value="Search" />
    </p>
  </form>
</div>
<div id="maincolumn">
  <div id="navigation">
    <?php
    echo '<a href="index.php">Articles</a>';
    if (!isset($_SESSION['user_id'])) {
      echo ' | <a href="login.php">Login</a>';
    } else {
      echo ' | <a href="compose.php">Compose</a>';
    }

    if ($_SESSION['access_lvl1'] > 1) {
      echo ' | <a href="pending.php">Review</a>';
    }

    if ($_SESSION['access_lvl1'] > 2) {
      echo ' | <a href="admin.php">Admin</a>';
    }
    echo ' | <a href="cpanel.php">Control Panel</a>';
    echo ' | <a href="transact-user.php?action=Logout">Logout</a>';
    ?>
  </div>
</div>
<div id="articles">
```

5. And now enter footer.php. (This one's a tough. You might want to take a break first.)

```php
</div>
</div>
</body>
</html>
```

6. Now another big one, http.php. This one is used for redirections:

```php
<?php
function redirect($url) {
    if (!headers_sent()) {
        header('Location: http://' . $_SERVER['HTTP_HOST'] .
        dirname($_SERVER['PHP_SELF']) . '/' . $url);
    } else {
        die('Could not redirect; Headers already sent (output).');
    }
}
?>
```

Whew. All this coding, and nothing yet to show on the screen! There are two more files to go that don't output anything. The workhorses of the application, they are a bit longer than the rest.

7. First, create transact-user.php:

```php
<?php
require_once 'conn.php';
require_once 'http.php';

if (isset($_REQUEST['action'])) {
    switch ($_REQUEST['action']) {
        case 'Login':
            if (isset($_POST['e-mail'])
            and isset($_POST['password'])) {
                $sql = "SELECT user_id,access_lvl1,name * 
                FROM cms_users WHERE email = '" . $_POST['e-mail'] . "' 
                AND password='" . $_POST['password'] . "';";
                $result = mysql_query($sql,$conn);
                if (!$result) die('Could not look up user information: ' . mysql_error($conn));

                if ($row = mysql_fetch_array($result)) {
                    session_start();
                    $_SESSION['user_id'] = $row['user_id'];
                    $_SESSION['access_lvl1'] = $row['access_lvl1'];
                    $_SESSION['name'] = $row['name'];
                }
                redirect('index.php');
            break;

        case 'Logout':
                session_start();
                session_unset();
                session_destroy();
                redirect('index.php');
                break;
    }
}
?>
```
