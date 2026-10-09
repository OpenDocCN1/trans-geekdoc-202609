# How it works...

First of all, make sure the classes developed in *Chapter 4, Working with PHP Object-Oriented Programming*, have been created. These include the Application\Generic\CountryList and Application\Generic\CustomerList classes discussed in *Chapter 4, Working with PHP Object-Oriented Programming*, in the recipe *Using interfaces*. Save each class in a new file in the Application\Generic folder as CountryListUsingTrait.php and CustomerListUsingTrait.php. Be sure to change the class names to match the new names of the files!

As discussed in step 3, remove the list() method from both CountryListUsingTrait.php and CustomerListUsingTrait.php list classes, and Add use ListTrait; in place of the method removed. Place the removed code into a separate file, in the same folder, called ListTrait.php.

You will also notice further duplication of code between the two list classes, in this case the setConnection() method. This calls for another trait!

Cut the setConnection() method out of both CountryListUsingTrait.php and CustomerListUsingTrait.php list classes, and place the removed code into a separate file called ConnectTrait.php. As this trait is logically related to ConnectionAwareInterface and Connection, it makes sense to place the file in the Application\Database folder, and to specify its namespace accordingly.

Finally, define Application\Database\ConnectionAwareInterface as discussed in step 6. Here is the final Application\Generic\CustomerListUsingTrait class after all changes:

```
```php
<?php
namespace Application\Generic;
use PDO;
use Application\Database\Connection;
use Application\Database\ConnectTrait;
use Application\Database\ConnectionAwareInterface;
class CustomerListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;
    use ConnectTrait;

    protected $key = 'id';
    protected $value = 'name';
    protected $table = 'customer';
}
```
```