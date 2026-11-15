
![](img/1ddec54918a4802eb9b4febec3d4e7f6_464_0.png)

Figure 14-3

Navigate around the various members' area pages by clicking the links. Each time you view a page, the access is logged in the accessLog table. You can prove this to yourself by running the view_members.php script you created in the previous chapter, then clicking the username of the member you logged in as to view their access log, as shown in Figure 14-4.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_464_1.png)

| Web page | Number of visits | Last visit |
| :--- | :--- | :--- |
| index.php | 7 | 2008-11-24 17:14:08 |
| books.php | 2 | 2008-11-24 17:09:27 |
| contact.php | 1 | 2008-11-24 17:09:10 |
| diary.php | 3 | 2008-11-24 17:09:04 |

Figure 14-4

When you're finished browsing around the members' area, return to the members' area homepage, and click the Logout link to return to the login page.

In the last few sections, you've expanded your knowledge of MySQL and PDO, and created a password-protected members' area with access logging. Although this system is fairly simple, you can adapt the principles you've learned to a wide variety of database-driven applications and membership systems.

By the way, you've probably spotted an obvious security flaw in this application: anybody can run the `view_members.php` and `view_member.php` script to view member information! In a real-world situation, you could do the following:

- 1. Place the `view_members.php` and `view_member.php` scripts inside the members' area, so you need to be logged in to use them.
- 2. Create an additional BIT field, `admin`, in the `members` table. A value of 1 for this field signifies that the member is an administrator; 0 signifies the member is a regular user.
- 3. From within the `view_members.php` and `view_member.php` scripts, check the status of the `admin` field for the currently logged-in member. If it's set to 1, let them use the scripts; otherwise, redirect them to the members' area homepage.

## Creating a Member Manager Application

Your book club system can now register new members, allow members to log in to and log out of the members' area, and track page visits within the members' area. What's more, by combining these scripts with the member record viewer you created in the previous chapter, an administrator can view a list of all members in the system, as well as the details and access log of each member.

There's one more piece of the puzzle to build, and that's a facility to let the administrator manage members. In this section you enhance the `view_member.php` script to allow the administrator to edit each member's information, as well as remove members from the database.

## Adding Update and Delete Methods to the Member Class

So that the administrator can edit and delete members, you need to add a couple of methods to your `Member` class: `update()`, to allow a `Member` object's details to be updated in the `members` table, and `delete()`, for removing a `Member` object completely from the `members` table.

Open your `Member.class.php` file and add the following two methods after the `insert()` method:

```php
public function update() {
	$conn = parent::connect();
	$passwordSql = $this->data["password"] ? "password = password(:password)," : "";

	$sql = "UPDATE " . TBL_MEMBERS . " SET
    username = :username,
    $passwordSql
    firstName = :firstName,
    lastName = :lastName,
    joinDate = :joinDate,
    gender = :gender,
    favoriteGenre = :favoriteGenre,
    emailAddress = :emailAddress,
    otherInterests = :otherInterests
WHERE id = :id";

try {
    $st = $conn->prepare( $sql );
    $st->bindValue( ":id", $this->data["id"], PDO::PARAM_INT );
    $st->bindValue( ":username", $this->data["username"], PDO::PARAM_STR );
    if ( $this->data["password"] ) $st->bindValue( ":password", $this->data["password"], PDO::PARAM_STR );
    $st->bindValue( ":firstName", $this->data["firstName"], PDO::PARAM_STR );
    $st->bindValue( ":lastName", $this->data["lastName"], PDO::PARAM_STR );
    $st->bindValue( ":joinDate", $this->data["joinDate"], PDO::PARAM_STR );
    $st->bindValue( ":gender", $this->data["gender"], PDO::PARAM_STR );
    $st->bindValue( ":favoriteGenre", $this->data["favoriteGenre"], PDO::PARAM_STR );
    $st->bindValue( ":emailAddress", $this->data["emailAddress"], PDO::PARAM_STR );
    $st->bindValue( ":otherInterests", $this->data["otherInterests"], PDO::PARAM_STR );
    $st->execute();
    parent::disconnect( $conn );
} catch ( PDOException $e ) {
    parent::disconnect( $conn );
    die( "Query failed: " . $e->getMessage() );
}

public function delete() {
    $conn = parent::connect();
    $sql = "DELETE FROM " . TBL_MEMBERS . " WHERE id = :id";

    try {
    $st = $conn->prepare( $sql );
    $st->bindValue( ":id", $this->data["id"], PDO::PARAM_INT );
    $st->execute();
    parent::disconnect( $conn );
} catch ( PDOException $e ) {
    parent::disconnect( $conn );
    die( "Query failed: " . $e->getMessage() );
}
}
```

update() creates an SQL UPDATE statement to set the field values of an existing record in the members table to the values stored in the Member object. The password field is given special treatment: if it contains a password, it's encrypted and the relevant SQL is passed into the UPDATE statement via the $passwordSql string variable:

```php
$passwordSql = $this->data["password"] ? "password = password(:password)," : "";
```

In addition, the password field value is passed into the query with a call to bindValue():

```php
if ( $this->data["password"] ) $st->bindValue( ":password", $this->data["password"], PDO::PARAM_STR );
```

If instead the password field is blank, the method assumes the password doesn't need updating, and it's left out of the UPDATE statement.

delete() simply deletes the member record with the ID stored in the Member object's id field. To do this, it creates an SQL DELETE statement with the member's ID in a WHERE clause.

## Adding a Deletion Method to the LogEntry Class

When a member is removed from the system, you also want to remove all their associated log entries from the accessLog table. If you didn't, your database would no longer have integrity because the accessLog table would contain orphaned entries that point to a non-existent member record.

This is easily achieved by adding a method, deleteAllForMember(), to the LogEntry class. This method expects to be passed the ID of the member in question. It then runs a DELETE statement to remove the associated log entries.

Open your LogEntry.class.php file and add the following code after the existing record() method:

```php
public static function deleteAllForMember( $memberId ) {
$conn = parent::connect();
$sql = "DELETE FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId";
try {
$st = $conn->prepare( $sql );
$st->bindValue( ":memberId", $memberId, PDO::PARAM_INT );
$st->execute();
parent::disconnect( $conn );
} catch ( PDOException $e ) {
parent::disconnect( $conn );
die( "Query failed: " . $e->getMessage() );
}
}
```

## Tweaking the view_members.php Script

There's one small change to make to the member list viewer, view_members.php. Open this file and change the line highlighted in the following code snippet:

```php
<tr><?php if ( $rowCount % 2 == 0 ) echo ' class="alt"' ?>>
<td><a href="view_member.php?memberId=<?php echo $member->getValueEncoded( "id" ) ?>&amp;start=<?php echo $start ?>&amp;order=<?php echo $order ?>"><?php echo $member->getValueEncoded( "username" ) ?></a></td>
<td><?php echo $member->getValueEncoded( "firstName" ) ?></td>
<td><?php echo $member->getValueEncoded( "lastName" ) ?></td>
</tr>
```

The only change here is that the start and order query string parameters are now being passed through to the view_member.php script. This is so that the administrator can easily return to the same page in the members list, with the list still sorted by the correct column. You see how this is used in the view_member.php script in a moment.

## Creating the view_member.php Script

The last step to building your member manager is to create a new view_member.php script that allows the administrator to edit and delete members. The script is based on the view_member.php file that you created in the previous chapter. The main differences are that the member data is now displayed in a form, allowing it to be edited, and that the script includes functions for saving edits and deleting a member.

Open your existing view_member.php file and replace its code with the following:

```php
<?php
require_once( "common.inc.php" );
require_once( "config.php" );
require_once( "Member.class.php" );
require_once( "LogEntry.class.php" );

$memberId = isset( $_REQUEST["memberId"] ) ? (int)$_REQUEST["memberId"] : 0;

if ( !$member = Member::getMember( $memberId ) ) {
displayPageHeader( "Error" );
echo "<div>Member not found.</div>";
displayPageFooter();
exit;
}

if ( isset( $_POST["action"] ) and $_POST["action"] == "Save Changes" ) {
saveMember();
}
```
