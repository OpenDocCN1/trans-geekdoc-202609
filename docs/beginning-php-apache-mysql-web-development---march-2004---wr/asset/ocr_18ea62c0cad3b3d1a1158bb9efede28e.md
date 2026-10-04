```
<option value="Traveling"?php if (in_array("Traveling", $hobbies)) echo 
selected;?>>Traveling</option>
<option value="Exercising"?php if (in_array("Exercising", $hobbies)) echo 
selected;?>>Exercising</option>
<option value="Computers"?php if (in_array("Computers", $hobbies)) echo *
selected;?>>Computers</option>
<option value="Other Listed"?php if (in_array("Other Listed", 
hobbies)) echo * selected;?>>Other Listed</option>
<br>
<input type="submit" name="submit" value="Update">
</form>


<?php
elelse {
    $query = "SELECT * FROM user_info WHERE id = '" . $_GET['id'] . "'";
    $result = mysqli_fetch_array($result);
    $hobbies = explode("*", $row['hobbies']);
    <form action="update_user.php" method="post">
    <input type="hidden" name="id"?php echo $_GET['id'];?>
    Username:<input type="text" name="username" value="?php Echo 
$row['username'];"?><br>
    Password:<input type="text" name="password" value="""> Not displayed<br>
    First Name:<input type="text" name="first_name" value="?php Echo 
$row['first_name'];"?><br>
    Last Name:<input type="text" name="last_name" value="?php Echo 
$row['last_name'];"?><br>
    Email:<input type="text" name="email" value="?php echo $row['email'];"?><br>
    City:<input type="text" name="city" value="?php echo $row['city'];"?><br>
    State:<input type="text" name="state" value="?php echo $row['state'];"?><br>
    Interests:(choose at least one)<br>
    <select name="hobbies" size="10">
    <option value="Golfing"?php if (in_array("Golfing", $hobbies)) echo 
selected;?>>Golfing</option>
    <option value="Hunting"?php if (in_array("Hunting", $hobbies)) echo 
selected;?>>Hunting</option>
    <option value="Reading"?php if (in_array("Reading", $hobbies)) echo 
selected;?>>Reading</option>
    <option value="Dancing"?php if (in_array("Dancing", $hobbies)) echo 
selected;?>>Dancing</option>
    <option value="Internet"?php if (in_array("Internet", $hobbies)) echo 
selected;?>>Internet</option>
    <option value="Flying"?php if (in_array("Flying", $hobbies)) echo 
selected;?>>Flying</option>
    </select>
?>
```