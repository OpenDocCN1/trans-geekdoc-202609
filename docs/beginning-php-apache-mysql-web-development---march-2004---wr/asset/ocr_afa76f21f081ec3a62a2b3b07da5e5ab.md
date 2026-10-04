# Chapter 10

2. Start up your favorite PHP editor, and type the following code. Make sure you enter your own server, username, password, and database name:

```
<?php
$conn = mysql_connect('yourserver', 'joeuser', 'yourpass');
mysql_select_db("yourdatabase", $conn);
?>
```

3. Save this file as conn_comic.php in the includes/ folder.
nYou can call it whatever you like, but we are going to include it in other files using the require() function, so you'll have to remember the filename you came up with. Or, you could go with the name we came up with, because we took the time to come up with such a clever name, and have used it in several PHP pages.

Enter the following code, and save it as db_inserts.php.
If you used the four pictures we provided and put them in the postcards/ folder, do not change this file. If you are using a different number of postcards, or created your own, make sure to change your code to reflect the change. And, if you have the name conn_comic.inc file something that is more clever than our name, make sure you make that change.

```
<?php
require('../includes/conn_comic.php');
$path = "http://" . ($_SERVER['HTTPS'] == "on" ? "https" : "http") . ":/" . $_SERVER['SERVER_NAME']\nstrev(strtr($_SERVER['SERVER_SELF']),'/'));
$imagepath = $path . "postcards/";
$imgURL = array(\'punyeearth.gif', 'grebenok.gif', 'sympathy.gif', 'congrats.gif');
$imgDESC = array(\'Wish you were here!', 'See you soon!', 'Our Sympathies', 'Congratulations!');

for ($i=0; $i<4; $i++) {
	$sql = "INSERT INTO images (images.img_url, images.img_desc) \nVALUES (\$imagepath$imgURL[$i], \$imgDESC[$i])";
	sccess = mysql_query($sql, $conn) or die(mysql_error($conn));
}
echo "done.";
?>
```

# How Works

Connect to the server using the correct username and password.



Create the database. Call it "postcard". If it is successful, "Database created" to the screen and move on.

```
$sql = "CREATE DATABASE postcard";
$success = mysql_query($sql, $conn) or die(mysql_error($conn));
echo "database created. ";
```

298