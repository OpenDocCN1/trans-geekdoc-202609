```
$result = mysql_query($query) or die(mysql_error());

if (mysql_num_rows($result) != 0) {
    <font color="#ff0000"><b>The Username, <?php echo $_POST['username'];?>, please choose another!</b></font><br>
    &nbsp;&nbsp; already in use<br>
    <form action="register.php" method="post">
    Username: <input type="text" name="username"><br>
    Password: <input type="password" name="password" value="<?php echo $_POST['password'];?>">r>
    Email: <input type="text" name="email" value="<?php echo $_POST['email'];?>">r>
    First Name: <input type="text" name="first_name" value="<?php echo $_POST['first_name'];?>">r>
    Last Name: <input type="text" name="last_name" value="<?php echo $_POST['last_name'];?>">r>
    City: <input type="text" name="city" value="<?php echo $_POST['city'];?>">r>
    State: <input type="text" name="state" value="<?php echo $_POST['state'];?>">r>
    Hobbies: <select name="hobbies" size="10" multiple>
    <option value="" echo selected;?></option>
    <option value="Golfing" <?php if(array("Golfing",$_POST['hobbies\'])) echo selected;?>>Golfing</option>
    <option value="Hunting" <?php if(array("Hunting",$_POST['hobbies\'])) echo selected;?>>Hunting</option>
    <option value="Reading" <?php if(array("Reading",$_POST['hobbies\'])) echo selected;?>>Reading</option>
    <option value="Dancing" <?php if(array("Dancing",$_POST['hobbies\'])) echo selected;?>>Dancing</option>
    <option value="Internet" <?php if(array("Internet",$_POST['hobbies\'])) echo selected;?>>Internet</option>
    <option value="Flying" <?php if(array("Flying",$_POST['hobbies\'])) echo selected;?>>Flying</option>
    <option value="Exercising" <?php if(array("Exercising",$_POST['hobbies\'])) echo selected;?>>Exercising</option>
    <option value="Computers" <?php if(array("Computers",$_POST['hobbies\'])) echo selected;?>>Computers</option>
    <option value="Traveling" <?php if(array("Traveling",$_POST['hobbies\'])) echo selected;?>>Traveling</option>
    <option value="Other Than" <?php if(array("Other Than",$_POST['hobbies\'])) echo selected;?>>Other Than Listed</option>
    </select><br>
    <input type="submit" name="submit" value="Register& &nbsp;<input type="reset" value="Clear">
</form>
<?php
} else {
    $query = "INSERT INTO user_info(username, password, email, first_name, last_name, city, state, hobbies) VALUES ('" . $_POST['username']",
```