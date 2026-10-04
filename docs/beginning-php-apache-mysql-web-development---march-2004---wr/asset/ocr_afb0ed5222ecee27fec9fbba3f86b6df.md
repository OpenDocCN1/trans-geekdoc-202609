# Chapter 7

```
$peoplesql = *SELECT
  FROM
  'people'
;
$result = mysql_query($peoplesql)
or die("Invalid query: " . mysql_error());
while($row = mysql_fetch_array($result , MYSQL_ASSOC)) {
  $people['$row['people_id']'] = $row['people_fullname'];
}
```

```
switch($_GET['action']) {
case 'edit':
  $movies = *SELECT
  FROM
  'movie'
  WHERE
    'movie'.movie_id = '"$_GET['id'].""
  ;
$result = mysql_query($movies)
or die("Invalid query: " . mysql_error());
$row = mysql_fetch_array($result , MYSQL_ASSOC);
$movie_name = $row['movie_name'];
$movie_type = $row['movie_type'];
$movie_year = $row['movie_year'];
$movie_leadactor = $row['movie_leadactor'];
$movie_director = $row['movie_director'];
  break;
default:
  $movie_name = "";
  $movie_type = "";
  $movie_year = "";
  $movie_leadactor = "";
  $movie_director = "";
  break;
}
```

```
??>
<html>
<head>
<TITLE><?php echo $_GET['action']?> movie/</TITLE>
</head>
<body>
<form action="commit.php?action=<?php echo $_GET['action']?>&type=movie&id=<?php echo $_GET['id']?>" method="post">
<?php
if (!empty($_GET['error'])) {
  echo "<div align='center' style='color:#FFFFFF;background-color:#ff0000;font-weight:bold!'>"" . nl2br(urldecode($_GET['error'])) . "</div><div><br />";
}
?>
?>
php
```

<table border="0" width="750" cellspacing="1" cellpadding="3" bgcolor="#353535" align="center">
<tr>

194