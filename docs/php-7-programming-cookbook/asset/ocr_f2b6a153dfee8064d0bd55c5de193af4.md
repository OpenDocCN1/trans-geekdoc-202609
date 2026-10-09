+   The last approach we will consider will be to fetch the results in the form of an array, and manually hydrate the entity. Even though this approach is slightly more costly in terms of performance, it allows any potential entity constructor to run properly, and keeps properties safely defined as private or protected:

```
public function fetchById($id)
{
    $stmt = $this->connection->pdo
             ->prepare(Finder::select('customer')
                        ->where('id = :id')->getSql());
    $stmt->execute(['id' => (int) $id]);
    return Customer::arrayToEntity(
               $stmt->fetch(PDO::FETCH_ASSOC));
}
```

+   To process a query that produces multiple results, all we need to do is to produce an iteration of populated entity objects. In this example, we implement a `fetchByLevel()` method that returns all customers for a given level, in the form of `Application\Entity\Customer` instances:

```
public function fetchByLevel($level)
{
    $stmt = $this->connection->pdo->prepare(
            Finder::select('customer')
                    ->where('level = :level')->getSql());
    $stmt->execute(['level' => $level]);
    while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        yield Customer::arrayToEntity($row, new Customer());
    }
}
```

+   The next method we wish to implement is `save()`. Before we can proceed, however, some thought must be given to what value will be returned if an INSERT takes place.

+   Normally, we would return the newly completed entity class after an INSERT. There is a convenient `PDO::lastInsertId()` method which, at first glance, would seem to do the trick. Further reading of the documentation reveals, however, that not all database extensions support this feature, and the ones that do are not consistent in their implementation. Accordingly, it would be a good idea to have a unique column other than `$id` that can be used to uniquely identify the new customer.

+   In this example we have chosen the email column, and thus need to implement a `fetchByEmail()` service method:

```
public function fetchByEmail($email)
{
    $stmt = $this->connection->pdo->prepare(
            Finder::select('customer')
```