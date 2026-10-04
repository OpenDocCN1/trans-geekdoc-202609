# Creating a Bulletin System

You may assume we have a vast knowledge of MySQL; just because we know the error code for creating a table that already exists is 1050. The fact is, we did not know the code: We simply ran a CREATE query on a table we knew existed, and echoed the resulting mysql_errno to the screen. Then we knew the code and could trap it for.

Why do we give away a secret? Some may find yourself trying to trap a particular error in your code, and you won't know the code you are looking for. Rather than scouring the Internet hoping to find the code, you can usually induce the error number to the screen. Once you have the code number, you can trap it for, just as we did in the preceding code.

One comment about setup.php before we move on: You may notice that in some cases we used IF NOT EXISTS. If you do not need to know whether you are duplicating a table, then IF NOT EXISTS will work nicely. We included it in cases where we did not need to insert any.

Next, let's take a look at our login procedure. There isn't much new to see here, but it gives us a chance to discuss authentication with you for a moment.

# A Last Look at User Authentication

The CBA uses user authentication, but it is by no means totally. For a board application, it is probably secure enough. However, if there is human data containing sensitive information, you might want to make it a bit more secure.

> This book does not attempt to help you create a virtual Fort Knox. If you have such a need, we strongly suggest looking for a good book on security, and perhaps look at a few online resources. A good start is www.w3.org/Security/Faq/.

Let's take a look at our security model, and see there might be some places to improve it. If you look at the PHP pages that make up the application, you see where we check for a user's access level before displaying items. For example, take a look at header.php.

Because header.php is included at the top of almost every Web page, we do most of our authentication checking. By checking the existence of the user_id session variable, we know whether the user is logged in. By if access_lvl is greater than 2, we know whether the user has administrator access. This allows us to choose the main menu depending on whether the user is logged in, and what access level he or she possesses. It also allows us to access the user by name.

```
echo '<a href="index.php">Home</a>';
if (isset($_SESSION['user_id'])) {
		echo '<a href="login.php">Log In</a>';
		echo '<a href="useraccount.php">Register</a>';
} else {
		echo '<a href="trans-user.php?action=Logout">Logout</a>';
}
echo "Log out " . $_SESSION['name'] . " </a>";
if ($_SESSION['access_lvl'] > 2) {
		echo '<a href="admin.php">Admin</a>';
}
echo 'useraccount.php';
```

551