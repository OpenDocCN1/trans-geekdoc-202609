
# Creating a Logout Function

As well as being able to log in to the members' area, members need to be able to logout when they've finished their session. To do this, create a simple script that clears the $_SESSION["member"] variable. Save the following file as logout.php in your members folder:

```php
<?php
require_once("../common.inc.php");
session_start();
$_SESSION["member"] = "";
displayPageHeader("Logged out", true);
?>
<p>Thank you, you are now logged out. <a href="login.php">Login again</a></a></p>
<?php
displayPageFooter();
?>
```

When viewed, this page immediately logs the member out, and displays a thank-you message, with a link inviting them to log in.

# Creating the Pages for the Members' Area

You've now built the nuts and bolts of your members' area. The only thing left to do is to create dummy pages for the members' area. Create the following four pages in the members folder that you created earlier.

index.php:

```php
<?php
require_once("../common.inc.php");
checkLogin();
displayPageHeader("Welcome to the Members' Area", true);
?>
<p>Welcome, <?php echo $_SESSION["member"]->getValue("firstName") ?>!Please choose an option below:</p>
<ul>
<li><a href="diary.php">Upcoming events</a></li>
<li><a href="books.php">Current reading list</a></li>
<li><a href="contact.php">Contact the book club</a></li>
<li><a href="logout.php">Logout</a></li>
</ul>
<?php displayPageFooter(); ?>
```

# Chapter 14: Manipulating MySQL Data with PHP

books.php:

```php
<?php
require_once("../common.inc.php");
checkLogin();
displayPageHeader("Our reading list", true);
?>
<dl>
<dt>Moby Dick</dt>
<dd>Herman Melville</dd>
<dt>Down in Paris and London</dt>
<dd>George Orwell</dd>
<dt>The Grapes of Wrath</dt>
<dd>John Steinbeck</dd>
</dl>
<p><a href="index.php?Members">Members' area home page</a></p>
<?php displayPageFooter(); ?>
```

contact.php:

```php
<?php
require_once("../common.inc.php");
checkLogin();
displayPageHeader("Contact the book club", true);
?>
<p>You can contact Marian, the organizer of the book club, on <strong>email.</strong></strong></p>
<p><a href="index.php?Members">Members' area home page</a></p>
<?php displayPageFooter(); ?>
```

diary.php:

```php
<?php
require_once("../common.inc.php");
checkLogin();
displayPageHeader("Upcoming events", true);
?>
<dl>
<dt>September 23</dt>
<dd>Book reading by Billy Pierce</dd>
<dt>October 3</dt>
<dd>Club outing to Yellowstone</dd>
<dt>October 17</dt>
<dd>Book signing by Valerie Wordsworth at the local bookstore</dd>
</dl>
<p><a href="index.php?Members">Members' area home page</a></p>
<?php displayPageFooter(); ?>
```

# Part III: Using PHP

These four pages are fairly simple. In each case, common.inc.php is included to load all the common code and files. Then, the checkLogin() function in common.inc.php is called to verify the user trying to view the page is logged in as a member. Remember that if the user isn't logged in, checkLogin() redirects to the login page and exits the application.

After calling checkLogin(), each script outputs the XHTML page header by calling displayPageHeader(), then outputs the page content, and finally outputs the page footer with displayPageFooter().

Notice index.php retrieves the logged-in member's first name with $_SESSION['member']->getValue("firstName") and displays it. The logged-in member is stored in the PHP session, so the member's details are accessible from any script in the application. index.php also includes a Logout option that simply links to logout.php script you created earlier.

# Testing the Members' Area

To try out your new password-protected area, try visiting the book_club/members/index.php page in your Web browser. If you're not logged in, you'll be redirected to the login form (Figure 14-2). Enter a username (for example, "sparky") and password (such as "mypass") for a member stored in your table, and click the Login button. If you entered the correct details, you should see the thank-you page appear, with a link to view the members' area homepage, index.php, as shown in Figure 14-3.

![](img/ede05b7b7968b2cbd9a51312fb183_463_0.png)

Figure 14-2

# Welcome to the Members' Area

Welcome, John! Please choose an option below:

- Upcoming events
- Current reading list
- Contact the book club
- Logout

Figure 14-3

Navigate around the various members' area pages by clicking the links. Each time you view a page, the access is logged in the accessLog table. You can prove this to yourself by running the view_members.php script you created in the previous chapter, then clicking the username of the member you logged in as to view their log, John in Figure 14-4.

![](img/ede05b7b7968b2cbd9a51312fb183_464_1.png)

# View member: John Sparks

| Username | sparky |
| --- | --- |
| First name | John |
| Last name | Sparks |
| Joined | 2007-11-13 |
| Gender | Male |
| Favorite genre | Crimo |
| Email address | jsparks@example.com |
| Other interests | Football, fishing and gardening |

# Access log

| Web page | Number of visits | Last visit |
| --- | --- | --- |
| index.php | 7 | 2007-11-14 |
| books.php | 2 | 2007-11-27 |
| contact.php | 1 | 2007-11-10 |
| diary.php | 3 | 2007-11-04 |

# Part III: Using PHP

When you're finished browsing the members' area, you can navigate around the members' area pages by clicking the links. Each time you view a page, the access is logged in the accessLog table. You can prove this to yourself by running the view_members.php script you created in the previous chapter, then clicking the username of the member you logged in as to view their log, John in Figure 14-4.

By expanding the members' area, you can now add more features to your application. For example, you could allow members to update their profile information, manage their reading list, or even leave reviews for books. This will require you to use more PHP and SQL to interact with the database more effectively.

The logged-in member is stored in the PHP session, so the member's details are accessible from any script in the application. index.php also includes a Logout option that simply links to logout.php script you created earlier.

# Testing the Members' Area

To try out your new password-protected area, try visiting the book_club/members/index.php page in your Web browser. If you're not logged in, you'll be redirected to the login form (Figure 14-2). Enter a username (for example, "sparky") and password (such as "mypass") for a member stored in your table, and click the Login button. If you entered the correct details, you should see the thank-you page appear, with a link to view the members' area homepage, index.php, as shown in Figure 14-3.

# Adding Update and Delete Methods to the Member Class

So that the administrator can edit and delete members, you need to add couple of methods. Open your Member.php file and add the following methods after the insert() method:

```php
public function update() {
  $conn = parent::connect();
  $passwordSql = $this->data["password"] ? "password = :password" : ""
}
```

```php
$sql = "UPDATE TBL_MEMBERS SET\nusername = :username,\n$passwordSql,\nfirstName = :firstName,\nlastName = :lastName,\njoinDate = :joinDate,\ngender = :gender,\nfavoriteGenre = :favoriteGenre,\nemailAddress = :emailAddress,\notherInterests = :otherInterests\nWHERE id = :id";
```

```php
try {
  $st = $conn->prepare($sql)\n$st->bindValue(":id", $this->data["id"], PDO::PARAM_INT);
  $st->bindValue(":username", $this->data["username"], PDO_STR);
  if ($this->data["password"]) $st->bindValue(":password", $this->data["password"], PDO_STR);
  $st->bindValue(":firstName", $this->data["firstName"], PDO_STR);
  $st->bindValue(":lastName", $this->data["lastName"], PDO_STR);
  $st->bindValue(":joinDate", $this->data["joinDate"], PDO_STR);
  $st->bindValue(":gender", $this->data["gender"], PDO_STR);
  $st->bindValue(":favoriteGenre", $this->data["favoriteGenre"], PDO_STR);
  $st->bindValue(":emailAddress", $this->data["emailAddress"], PDO_STR);
  $st->bindValue(":otherInterests", $this->data["otherInterests"], PDO_STR);
  $st->execute();
} catch (PDOException $e) {
  $parent::disconnect();
  die("Query failed: " . $e->getMessage());
}
```

```php
public function delete() {
  $conn = parent::connect();
  $sql = "DELETE FROM TBL_MEMBERS WHERE id = :id";
```

```php
try {
  $st = $conn->prepare($sql)\n$st->bindValue(":id", $this->data["id"], PDO::PARAM_INT);
  $st->execute();
} catch (PDOException $e) {
  $parent::disconnect();
  die("Query failed: " . $e->getMessage());
}
```
