# Creating Parameterized Queries Using OOP

If the SQL statement is malformed, an exception is thrown. Then, the error is echoed on line 36 with a call to the getMessage() method of the exception object passed into the catch block:

```
catch(Exception $ex)
{
    echo $ex->getMessage() . "<br/>";
}
```

If everything works as planned, we can return the primary key of the newly inserted row into the student table to the caller by calling the PDO object's lastInsertId() method:

```
return $db->lastInsertId(); // Returns the primary key of this INSERT
```

Listing 26.23 is an example of using this method by creating several entries using a pre-populated array of associative arrays.

# Listing 26.23.

```
1. <?php
2. require_once('StudentManager.php');
3. 
4. // Manage some Simpsons
5. $simpsons_manager = new StudentManager();
6. 
7. $simpsons = [];
8. 
9. $simpsons[] = [
10.     'first_name' => 'Bart',
11.     'last_name' => 'Simpson',
12.     'email' => 'kowabungadude@simpsons.com'
13. ];
14. 
15. $simpsons[] = [
16.     'first_name' => 'Lisa',
17.     'last_name' => 'Simpson',
18.     'email' => 'lisa@simpsons.com'
19. ];
20. 
21. $simpsons[] = [
22.     'first_name' => 'Marge',
23.     'last_name' => 'Simpson',
24.     'email' => 'marge@simpsons.com'
25. ];
26. 
27. $simpsons[] = [
28.     'first_name' => 'Homer',
29.     'last_name' => 'Simpson',
30.     'email' => 'ilovedonuts@simpsons.com'
31. ];
32.
```