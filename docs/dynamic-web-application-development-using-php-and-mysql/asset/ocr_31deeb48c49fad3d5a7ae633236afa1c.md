```
if (!$SESSION['strTextCol'])
    $_SESSION['strTextCol'] = "yellow";

if (isset($_POST["submit"]) ) {
    $strBgCol = $_POST["strNewBgCol"];
    $strTextCol = $_POST["strNewTextCol"];
    $_SESSION['strBgCol'] = $strBgCol;
    $_SESSION['strTextCol'] = $strTextCol;
}
else {
    $strBgCol = $_SESSION['strBgCol'];
    $strTextCol = $_SESSION['strTextCol'];
}

?>
<head>
<style type="text/css">
body {background-color: <?php echo $strBgCol ?>}
p {color: <?php echo $strTextCol ?>}
h2 {color: <?php echo $strTextCol ?>}
</style>
</head>
<body>
<h2>What Colors would you like?</h2>
<form action='<?php echo $_SERVER["PHP_SELF"] ?>' method='post'>
<p>
<label for="strNewBgCol">Background Color: </label>
<select name='strNewBgCol' id='strNewBgCol'>
    <option>red</option>
    <option>green</option>
    <option>blue</option>
    <option>cyan</option>
    <option>yellow</option>
</select></p>
<p>
<label for="strNewTextCol">Text Color: </label>
<select name='strNewTextCol' id='strNewTextCol'>
    <option>red</option>
    <option>green</option>
    <option>blue</option>
    <option>cyan</option>
    <option>yellow</option>
</select>
<input type='submit' name='submit'/>
</p>
</form>
</body>
```

The script begins by registering a session:

```
session_start();
```