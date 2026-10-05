```
$this->seed();
}
```

This controller checks to ensure it is being run from the CLI, and the all() method runs migrations, and executes seeder files that have the suffix Seeder .php in the application/database/seeder directory.

# # 10.6 Test Case for the News Controller

We wrote a test case for the News controller in Chapter 7, Test Case for the News Controller. Now, we'll write the same tests with Codeception.

```
tests/acceptance/NewsScept.php
<?php
$I = new AcceptanceTester($scenario);
$I->wantTo('ensure that News works');
```

# # Database Fixtures

Before running tests, we have to prepare our database. We have already made the Dbfxture controller to help us do this. How do we run the controller from our Codeception tests?
We run it with the system()* function in PHP.

```
tests/acceptance/NewsScept.php
<?php
system("CI_ENV=testing php index.php dbfxture all");
$I = new AcceptanceTester($scenario);
$I->wantTo('ensure that News works');
```

> To Composer users
If you installed CodeIgniter via Composer, the path of index.php is different.


```
system("CI_ENV=testing php public/index.php dbfxture all");
```

*http://php.net/en/system