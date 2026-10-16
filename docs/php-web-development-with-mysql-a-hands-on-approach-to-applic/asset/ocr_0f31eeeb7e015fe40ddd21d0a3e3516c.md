# 25. ADDING RESERVATION FEATURES

```
```php
// Reserve movie if it's reservable, update the number of reserved copies
// in movielisting for reserved movies, and add it to the cart
if (mysqli_num_rows($result) == 1 && isset($_SESSION['user_id'])) {
    $user_id = $_SESSION['user_id'];
    $query = "INSERT INTO reservation (user_id, movielisting_id) VALUES (?, ?)";
    $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_id);
    if (mysqli_errno($dbc)) {
        trigger_error('Error querying database movielisting.reservation', E_USER_ERROR);
    }
    $query = "UPDATE movielisting SET number_reserved = number_reserved + 1 WHERE id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $movie_id);
    if (mysqli_errno($dbc)) {
        trigger_error('Error querying database movielisting.reservation', E_USER_ERROR);
    }
    if (isset($_SESSION['cart'])) {
        array_push($_SESSION['cart'], $movie_id);
    } else {
        $_SESSION['cart'] = [$movie_id];
    }
}
header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;
elseif (isset($_GET['id_to_reserve'])):
?>
<h3 class="text-success">Confirm Reservation of the Following Movie:</h3><br/>
<?php
$id = $_GET['id_to_reserve'];
$query = "SELECT * FROM movielisting WHERE id = ?";
$result = parameterizedQuery($dbc, $query, 'i', $id);
if (mysqli_errno($dbc)) {
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}
```
```