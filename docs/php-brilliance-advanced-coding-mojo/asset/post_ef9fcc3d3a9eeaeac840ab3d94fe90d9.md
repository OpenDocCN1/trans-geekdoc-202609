
## Instantiaphobia

Switch your attention back to the User class and you should see the immediate benefit. Our instances of the User class are no longer having to lug around a theoretically redundant static method with them and as a result, the memory footprint of our application is reduced, albeit marginally.

More importantly, our User class is fully testable. This singular piece of code allows us to instantiate user objects by providing mocks, stubs and dummy data to the constructor and subsequently test all of the object's methods without encountering a static method call or picking the database singleton on the way. Unit testing aficionados rejoice!

Let's look at again with some slightly different wording in order to reaffirm what we've just considered. The User class has slimmed down to only contain the methods that directly pertain to user object instances (granted, this is already a pretty slim object in our code right now).

Whilst I accidentally on purpose neglected to mention this downside to the factory method approach previously, it's worth just a quick peek at it now. Whenever you instantiate an object from a class that also contains static methods, the resulting object instance also carries with it those static methods.

Let's just illustrate that for the benefit of understanding.

```
// Pick up a user instance in the regular fashion
$fred = User::create(1);

// $fred also carries the create() method
$mary = $fred->create(2);

// So too does $mary
$jenny = $mary::create(3);
```

As you can see, our User instances are picking up that factory method and making it available for use. Or indeed, abuse, depending upon your point of view.

Of course they are.

That factory method is part of the class definition so it's only to be expected that each User instance also provides access to the create() method too.

This is one of the things that the transition to dedicated factories allows us to avoid. By moving the creational methods into their own dedicated class files, we no longer waste processor cycles and memory maintaining redundant methods on objects which, let's face it, are going to be used extensively throughout a bus busy application's day.

On top of that, there's no real reason for calling the factory method on a particular instance, not when the code declares its usage intent; being a statically invoked class method.

Which brings us back to the matter of providing dedicated factories for the objects in our system. If you're already at a senior level within your company, there's a very good chance that you are already familiar with the Factory Pattern and as such, you will quite likely be aware what I'm proposing here isn't a properly specified implementation of this pattern.

In common parlance, I've actually done here is to create something commonly referred to as a simple factory. In reality, all that has happened is that the factory method itself has as far as this principle of Instantiaphobia is concerned, that we are still successfully limiting the use of the new keyword to just a single location.

Let's look at that code again.

```
class UserFactory {
    public static function create($userId)
    {
        // Collect the role and account instances
        $userRole = UserRole::create($userId);
        $userAccount = UserAccount::create($userId);

        // Collect the actual user details
        $dbConn = Database::getInstance();
        $userData = $dbConn->query("SQL statement here");

        $user = new User($userData, $userRole, $userAccount);
        return $user;
    }
}

```

From a unit testing standpoint, this is still a nightmare, but we are at least making progress. You could elect to run the test suite that covers this and any other simple factories independently from the test suite that covers the core application code. It is worth bearing in mind that the corresponding User class no longer contains this dependency-laden static factory method and as such, can now be fully tested in its own right by passing mocks and stubs into the constructor as desired.

Our simple factory is still a bit of mess though. How should we go about cleaning it up?

For starters, we should turn our attention to the dependencies that are listed inside create() method. Here are the lines of code in question.

```
$userRole = UserRole::create($userId)
$userAccount = UserAccount::create($userId)
$dbConn = Database::getInstance();
```

The first two lines should clearly get the same “migrate the factory method to its own dedicated class”, allowing the User class to become fully-testable.

```
$userRole = UserRole::create($userId)
$userAccount = UserAccount::create($userId)
$dbConn = Database::getInstance();
```

The first two lines should clearly get the same “migrate the factory method to its own dedicated class”, allowing the User class to become fully-testable.

## Instantiaphobia

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

A static method that is fully-contained is one thing. A static method that calls other methods is another thing. A static method that relies on the database is the worst of all.

Rather than having our UserFactory reach out to the classes and objects upon which it depends, those dependencies are provided to the factory itself. Like this:

```php
class UserFactory {
    private $db;
    private $roleFactory;
    private $accountFactory;

    public function __construct(
        Database $db,
        UserRoleFactory $roleFactory,
        UserAccountFactory $accountFactory
    ) {

        $this->db = $db;
```

```php
        $this->roleFactory = $roleFactory;
        $this->accountFactory = $accountFactory;
    }
}
```

```php
    public function create($userId)
    {
      $role = $this->roleFactory->create($userId);
      $account = $this->accountFactory->create($userId);
      $userData = $this->db->query("SQL statement here");

      $user = new User($userData, $role, $account);
      return $user;
    }
}
```
