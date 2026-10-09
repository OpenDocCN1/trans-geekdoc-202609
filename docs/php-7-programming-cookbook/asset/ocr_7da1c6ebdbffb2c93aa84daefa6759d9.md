```
use Application\Database\Connection;
$conn = new Connection(include _DIR_ . DB_CONFIG_FILE);
$sql = 'SELECT c.id, c.name, c.balance, c.email, f.phone, '
         'u.transaction, u.date, u.quantity, u.sale_price, r.title '
         'FROM customer AS c '
         'JOIN profile AS f '
         'ON f.id = c.id '
         'JOIN purchases AS u '
         'ON u.customer_id = c.id '
         'JOIN products AS r '
         'ON u.product_id = r.id '
         'WHERE c.id >= :min AND c.id < :max '
         'ORDER BY c.id ASC, u.date DESC ';
```

+   2. Next we can implement a form of pagination, based on restrictions on the customer ID, using simple $\_GET parameters. Note that we add an extra check to make sure the value of $prev does not go below zero. You might consider adding another control that ensures the value of $next does not go beyond the last customer ID. In this illustration, we just allow it to increment:

```
$page = $_GET['page'] ?? 1;
$page = (int) $page;
$next = $page + 1;
$prev = $page - 1;
$prev = ($prev >= 0) ? $prev : 0;
```

+   3. We then calculate the values for $min and $max, and prepare and execute the SQL statement:

```
$min = $prev * ITEMS_PER_PAGE;
$max = $page * ITEMS_PER_PAGE;
$stmt = $conn->pdo->prepare($sql);
$stmt->execute(['min' => $min, 'max' => $max]);
```

+   4. A while() loop can be used to fetch results. We use a simple fetch mode of PDO::FETCH\_ASSOC for the purpose of this example. Using the customer ID as a key, we store basic customer information as array parameters. We then store an array of purchase information in a sub-array, $results[$key]['purchases'][] . When the customer ID changes, it's a signal to store the same information for the next customer. Note that we accumulate totals per customer in an array key total:

```
$custId = 0;
$result = array();
$grandTotal = 0.0;
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    if ($row['id'] != $custId) {
        $custId = $row['id'];
        $result[$custId] = [
```