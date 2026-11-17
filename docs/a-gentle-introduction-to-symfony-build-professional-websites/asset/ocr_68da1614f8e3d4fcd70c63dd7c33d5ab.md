```
```php
// isPathAbsolute()
$t->diag('isPathAbsolute()');
foreach ($testCases as $case)
{
    $t->is(sfToolkit::isPathAbsolute($case['input']),
    $case['output'],$case['comment']);
}
```
```

# Unit testing ORM classes

Testing Propel or Doctrine classes is a bit more involving as the generated objects rely on a long cascade of classes. Moreover, you need to provide a valid database connection to Propel and you also need to feed the database with some test data.

Thankfully, it is quite easy as symfony already provides everything you need:

+   * To get autoloading, you need to initialize a configuration object
+   * To get a database connection, you need to initialize the sfDatabaseManager class
+   * To load some test data, you can use the sfPropelData class

A typical Propel test file is shown in Listing 15-9.

# Listing 15-9 - Testing Propel classes

```
```php
<?php
include dirname(__FILE__).'./../bootstrap/unit.php';

new sfDatabaseManager($configuration);
$loader = new sfPropelData();
$loader->loadData(sfConfig::get('sf_data_dir').'/fixtures');

$t = new lime_test(1, new lime_output_color());

// begin testing your model class
$t->diag('->retrieveByUsername()');
$user = UserPeer::retrieveByUsername('fabien');
$t->is($user->getLastName(), 'Potencier', '->retrieveByUsername() returns the User for the given username');
```
```

A typical Doctrine test file is shown in Listing 15-10.

# Listing 15-10 - Testing Doctrine classes

```
```php
<?php
include dirname(__FILE__).'./../bootstrap/unit.php';

new sfDatabaseManager($configuration);
Doctrine_Core::loadData(sfConfig::get('sf_data_dir').'/fixtures');

$t = new lime_test(1, new lime_output_color());

// begin testing your model class
$t->diag('->retrieveByUsername()');
$user = Doctrine::getTable('User')->findOneByUsername('fabien');
$t->is($user->getLastName(), 'Potencier', '->findOneByUsername() returns the User for the given username');
```
```