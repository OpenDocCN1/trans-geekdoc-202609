
## PHPUnit Test Cases

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function firstTestCase()
    {
        $this->assertTrue(False);
    }
}
```

The test runner tells you...

```
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

W 1 / 1 (100%)

Time: 109 ms, Memory: 12.00 MB

There was 1 warning:

1) Warning
No tests found in class "BasicTestCase".

WARNINGS!
Tests: 1, Assertions: 0, Warnings: 1.
```

...it did not find any tests. If you ever find yourself scratching your head as to why PHPUnit didn't find our test, the first place to look is at the names of your test methods and if you are using annotations or not.

I have covered the basics of how PHPUnit works. In the next chapter, I will show you a test design pattern I like to use to organize my tests to provide clarity and keep me focused on what I'm doing.

## Chapter 5: Test Double

### What Is a Test Double?

Test doubles are a concept that generates the most arguments between people discussing testing. They are a concept you have to understand to really have an opinion on them, but we all know that never stops people from arguing.

Wikipedia has a definition that gets right to the heart of the matter:

> “In automated unit testing, it may be necessary to use objects or procedures that look and behave like their release-intended counterparts, but are actually simplified versions that reduce the complexity and facilitate testing. A test double is a generic (meta) term used for these objects or procedures.”

Test doubles are a tool we can use to represent dependencies we need for a given testing scenario. In the PHP world, they are commonly referred to as mocks, but I want to get you into the habit of using the correct word for it. You’ll see why in a little bit.

At a high level, I will use a double to represent some dependency I need for a test when, for whatever reason, I am not using the real thing. There can be lots of reasons not to use the “real” dependency. The most common reasons are “it talks to a database” or “it talks to a remote API.”

Before I go further, I want to be clear there are no right or wrong approaches to using test doubles. Some programming communities advocate using doubles for all dependencies. Some advocate never using a double. Other programming communities that use languages where objects and functions can be modified at run time (commonly referred to as “monkey patching”) use that technique instead of doubles.

In this chapter, I want to show you the different types of test doubles available to PHP programmers and let you make up your own mind. My approach is to use the real dependency when possible unless there is significant overhead. Dependencies that use a database are the usual culprit for me or “request” objects used in frameworks.

In this chapter, I will be using the test doubling framework Prophecy[1], which has been available in PHPUnit since version 4.5. I’ve also used Mockery[2] and liked its syntax, too. There is no “right” one to use — you can even use PHPUnit’s built-in test doubling tools. Pick one you like and stick with it; those who have to maintain the tests after you will thank you for being consistent.

In these examples, I will be using code that is being used in production for an application that helps track transactions in a simulation baseball league.

- [1] Prophecy: https://github.com/phpspec/prophecy
- [2] Mockery: https://github.com/mockery/mockery

### Dummies

Dummies are the first test double you might need. With Wikipedia as our guide:

> “...used when a parameter is needed for the tested method but without actually needing to use the parameter.”

In practical use, you will want to use a dummy when the code you are testing needs a dependency, but the dependency itself will never be used during the test. With PHP moving towards type hints and return types being used more and more, dummies are of limited use because creating a dependency without a type will likely cause PHP to complain. If you are using older codebases where types are not being used, you can create a dummy by using PHP’s built-in stdClass object.

So let’s say you are writing a test that needs to use this particular bit of code:

```php
class Roster
{
    public $_db;
    public $pdo;
    public $previous_season;
    public $current_season;

    /**
     * Constructor for class
     *
     * @param Aura\SqlQuery\QueryFactory $db
     */
    public function __construct($db)
    {
        $this->_db = $db;
        $this->pdo = new PDO(
            'pgsql:host=localhost;dbname=user=;password=' );
    }

    // Other code snipped out
}
```

But your test doesn’t need to do anything with it. You’d be okay creating a dummy without a type to satisfy the condition of needing “a RosterModel object.”

```php
// Create a dummy of our database and pass it to our Roster model
$db = new stdClass();
$rm = new Roster($db);
```

### Test Stub

In our world of typed PHP code, the dummy will get upgraded to the test stub. Again, using Wikipedia as our guide, we get the following definition:

> “used for providing the tested code with ‘indirect input.’”

This is a shorter way of saying an object with the same class signature as our dependency but with no expectations that any methods of that object will be called during the test.

So, using the same code you’re trying to test, but now you are type-hinting on what the $db parameter is supposed to be, so you need to create that as a test stub. This time you are using Prophecy to do so.

```php
// Create a stub of the QueryFactory object the constructor needs
$db = $this->prophesize(QueryFactory::class);
$db->reveal();
$rm = new Roster($db);
```

In more clear language, what these two lines do is:

- Create a test double object with the same class signature as a QueryFactory (so it is of the correct type)
- Activate the double
- Create a Roster object that accepts our test double as a constructor parameter

### Mock Objects and Test Spies

In this section, I am going to combine two types of test doubles because they are both going to be used in this test scenario.

First, we have a mock object which is used for verifying “indirect output” of the tested code by first defining the expectations before the tested code is executed.

A mock is the most common test double you will be using in your tests when you need a test double. Mocks are where we end up with very large amounts of code that is part of our arrange step.

Second, we have a test spy, used for verifying “indirect output” of the tested code, by asserting the expectations afterward, without having defined the expectations before the tested code is executed. It helps in recording information about the indirect object created.

Spies are used when you are expecting a method on a mock is going to be called, but you don’t need to worry about any side effects (meaning actions the code in question takes) that happen.

In this example, you’re writing a test for some code that generates entries in our “transaction log.” This is code I have broken multiple times because I did not initially write tests for it. After some refactoring, here is the code you are going to test:

```php
<?php
use Roster;

class Transaction
{
    protected $rosterModel;

    public function __construct(Roster $rosterModel)
    {
        $this->rosterModel = $rosterModel;
    }

    public function generateTradeLogEntry($data, $tradePartner): string
    {
        $tradeDate = date('m/y');
        $tradedPlayers = [];

        foreach ($data as $playerInfo) {
            [$tmp, $playerId] = explode('_', $playerInfo);
            $playerInfo = $this->rosterModel->getById($playerId);
            $comment = "Trade {$tradePartner} {$tradeDate}";
            if ($playerInfo['ibl_team'] !== $tradePartner) {
                $tradedPlayers[] = trim($playerInfo['display_name']);
                $this->rosterModel
                    ->updatePlayerTeam($tradePartner, $playerId, $comment);
                $this->rosterModel->makeInactive($playerId);
            }
        }

        return 'Trades ' . implode(', ', $tradedPlayers) . ' to ' . $tradePartner;
    }
}
```

So the first step is to identify dependencies. You have:

- A date that we cannot override (maybe refactor that later to avoid weird edge cases)
- A Roster object that calls getById()
- A Roster object that calls updatePlayerTeam()
- A Roster object that calls makeInactive()

What is your test scenario? First, you build a test skeleton with the scenario in it.
