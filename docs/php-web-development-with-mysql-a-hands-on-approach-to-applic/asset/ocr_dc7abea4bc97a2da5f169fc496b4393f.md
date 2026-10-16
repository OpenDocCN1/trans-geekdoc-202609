# 26. INTRODUCTION TO OBJECT-ORIENTED PROGRAMMING IN PHP

Listing 26.28 is an example of how we can use our readById() method. It produces this output in Figure 26.9.

# Listing 26.28.

```
```php
1. require_once('StudentManager.php');
2.
3. // Manage some Simpsons
4. $simpsons_manager = new StudentManager();
5.
6. $a_simpson = $simpsons_manager->readById(3);
7.
8. if ($a_simpson)
9. {
10. echo "First name: " . $a_simpson->getFirstName() . "<br/>";
11. echo "Last name: " . $a_simpson->getLastName() . "<br/>";
12. echo "Email: " . $a_simpson->getEmail() . "<br/>";
13. echo "<br/>";
14. }
```
```

![](bbox=[0.65, 0.12, 0.92, 0.22])

# Updating Database Entries Using PDO

Now we’ll create a method called update() that updates a row in the student table. See Listing 26.29.

# Listing 26.29.

```
```php
1. public function update($id, $first_name, $last_name, $email)
2. {
3.   $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);
4.
5.   // UPDATE a record with a given first name, last name, and email for a given id
6.   $sql = "UPDATE student SET `first_name`=:first_name, `last_name`=:last_name, "
7.     . " `email`=:email WHERE id=:id";
8.
9.   $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
10.
11.   try
12.   {
13.     $query = $db->prepare($sql);
14.     $query->bindParam(":id", $id, PDO::PARAM_INT);
15.     $query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
16.     $query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
17.     $query->bindParam(":email", $email, PDO::PARAM_STR);
18.     $query->execute();
19.     $rows_affected = $query->rowCount();
20.   }
```
```