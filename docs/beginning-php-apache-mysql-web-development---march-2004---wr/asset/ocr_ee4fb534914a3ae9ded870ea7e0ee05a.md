# Creating a Bulletin Board System

```
case 'DELETEFORUM':
  $sql = 'SELECT * FROM forum where id=' . \_REQUEST['f'];
  $result = mysql_query($sql);
  $row = mysql_fetch_array($result);
  $msg = "If you delete this forum, all topics and replies will be\n      deleted as well. <formbr=" . $row['forum_name'] . '"></php>";
  echo "<div id=requestConfirm><a>
  echo "<<p><h2>DELETEFORUM</h2>";
  echo "<p>" . $msg . "</p>";
  echo "<input class='confirm' type='button' value='Delete ' ";
  echo "<onclick='deleteForum(' . \_REQUEST['f'] . ')'> ";
  echo "<input class='confirm' type='button' value='Cancel ' ";
  echo "<onclick='history.back()'></p>";
  echo "</div>";
default:
  require_once 'footer.php';
```

Excellent. You have used 1,180 lines of code without a single mistake. Let's move on to the application and see how it works, shall we?

# Try Out - The Bulletin Board Application

Let's work our way through a first installation of the Comic Book Appreciation Bulletin Board System. (That is a mouthful, so from now on, we'll refer to it as the "CBA board.")

Note that many screens are involved in this application. You have probably seen a bulletin board application before, so we are not going to show you each and every as we describe the application, just some of the more important screens.

If you have not done so, your first step should be to create the CBA board tables.

+   1. Load setup.php in your browser.

You should see a screen similar to Figure 15-1, informing you that the databases have been created and reminding you of your initial login e-mail and password.

If you downloaded the application from the Web, your screen should look very similar to Figure 15-1. However, if you entered the code from the book, it will look quite different. The reason for this is that you are missing a file, forum_styles.css, that modifies the way the page looks. You can-download this file from the Web if you would like to use it, although it is not required. All screenshots in this chapter utilize the forum_styles.css style sheet. Although CSS is beyond the scope of this book, we will discuss forum_styles.css briefly in the "How It Works" section that follows this "Try It Out" section.