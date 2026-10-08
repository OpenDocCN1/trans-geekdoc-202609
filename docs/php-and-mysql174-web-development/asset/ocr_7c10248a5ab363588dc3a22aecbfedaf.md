```
$result = $db_conn->query($query);
if ($result->num_rows)
{
    // if they are in the database register the user
    $_SESSION['valid_user'] = $userid;
}
$db_conn->close();
?>
<!DOCTYPE html>
<html>
<head>
  <title>Home Page</title>
  <style type="text/css*>
  fieldset {
    width: 50%;
    border: 2px solid #ff0000;
  }
  legend {
    font-weight: bold;
    font-size: 125%;
  }
  label {
    width: 125px;
    float: left;
    text-align: left;
    font-weight: bold;
  }
  input {
    border: 1px solid #000;
    padding: 3px;
  }
  button {
    margin-top: 12px;
  }
  </style>
</head>
<body>
  <h1>Home Page</h1>
<?php
if (isset($_SESSION['valid_user']))
{
    echo '<p>You are logged in as: '.$SESSION['valid_user'].'<br />';
    echo '<a href="logout.php">Log out</a></p>';
}
?>
```