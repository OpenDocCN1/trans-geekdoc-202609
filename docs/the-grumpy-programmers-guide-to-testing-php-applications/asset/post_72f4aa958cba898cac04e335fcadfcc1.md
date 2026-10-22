
## 5. Test Double

```php
// Assert
$this->assertEquals($expected, $response);
}
}
```

### Fakes

Fakes are an often under-utilized tool for testing purposes. Instead of using a mock created with the testing framework’s tools, you instead create your own object that does the same thing you are expecting from your dependency. Using the example of the test we just wrote above, what would it look like if I decided I wanted to use a fake instead of what Prophecy can provide me.

There are a few ways you can approach this. You could create a standalone object outside of the test that extends the methods we are creating doubles for. That might look like this:

```php
<?php
declare(strict_types=1);

class FakeRosterModel
{
    public function getById($id): array
    {
        $responses = [
            0 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
            1 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
            2 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
        ];

        return $responses[$id];
    }

    public function updatePlayerTeam(
        $iblTeam, $playerId, $comments = ""): bool
    {
        return true;
    }

    public function makeInactive($player_id): bool
    {
        return true;
    }
}
```

The big issue is the Transaction object is expecting a typed Roster object in the constructor. There is no easy way to fix this. I could extend this object from Roster and pass it a QueryFactory but do nothing with it. That seems like the path of least resistance if I really wanted to use a fake instead of Prophecy for the Roster object. So I will do that. The fake now looks like this:

```php
<?php
declare(strict_types=1);

require_once __DIR__ . '/../models/rosters.php';

class FakeRosterModel extends Roster
{
    public function __construct($db)
    {
        $this->db = $db;
    }

    public function getById($id): array
    {
        $responses = [
            1 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
            2 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
            3 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
        ];

        return $responses[$id];
    }

    public function updatePlayerTeam(
        $iblTeam, $playerId, $comments = ''): bool
    {
        return true;
    }

    public function makeInactive($player_id): bool
    {
        return true;
    }
}
```

And my test using the fake looks like this:

```php
/**
 * @test
 */
public function it_generates_proper_transaction_info_for_a_trade_using_fakes(): void
{
    /**
     * Given I have an array that contains players
     * When I submit a list of players
     * And I submit a transaction description
     * Then I should get a one-line transaction being generated
     */

    // Arrange
    $expected = 'Trades Moe, Larry, Curly to TESTMORE';
    $tradePartner = 'TESTMORE';

    // Data contains compound ID's of <trade partner 1>_<player_id>
    $data = ['team1_1', 'team1_2', 'team1_3'];
    $db = new \Aura\SqlQuery\QueryFactory('sqlite');

    $rm = new class($db) extends Roster {
        public function __construct(\Aura\SqlQuery\QueryFactory $db)
        {
            $this->db = $db;
        }
        public function getById($id): array
        {
            $responses = [
                1 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
                2 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
                3 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
            ];
            return $responses[$id];
        }
        public function updatePlayerTeam($iblTeam, $playerId, $comments = ''): bool
        {
            return true;
        }
        public function makeInactive($player_id): bool
        {
            return true;
        }
    };

    $tm = new Transaction($rm);
    $tm->transactionDate = '01/01';

    // Act
    $response = $tm->generateTradeLogEntry($data, $tradePartner);

    // Assert
    $this->assertEquals($expected, $response);
}
```

Whatever path you decide to go, it is good to know you can create a double of something that perhaps is a lot of work to duplicate using test doubling tools. Think about things that send emails when you do not want emails to be sent at all as part of the test. You can create a fake object that uses all the same methods but never sends it.

My preference when it comes to fakes is to use anonymous classes in the test cases unless you are 100% sure the fake you are creating can be reused by other tests. Remember, the same rules about reusing code and trying not to repeat yourself apply to your tests!

### Final Thoughts

Tests are all about scenarios where you control the state of all your dependencies. Sometimes you can use the “real” dependency–other times you will need to create a double. You have multiple doubles to choose, depending on what you need:

- Dummies if you’re not using type-hinted code and need a dependency that you’re not going to be calling any methods on in your test
- Test stubs if you need a dummy, but your code is type-hinted
- Spies if you need a stub where some methods are going to be called, but you don’t need to worry if the method does anything
- Mocks if you need a dependency with specific methods being called and those methods need to return something or perform an action required by the test

Test doubles are definitely the number one thing testing practitioners argue about—the next being how many assertions should be in each test. This chapter should give you the confidence to determine when test doubles are appropriate and which ones to choose.

## Chapter 6: Test-Driven Development by Example

In an idealized world of software development, you would be writing all the code for your applications using Test-Driven Development (TDD), implementing features, and deciding on APIs and interfaces one test at a time. The way I use TDD follows this type of workflow:

- Create an empty test that fails
- Write out my testing scenario as pseudocode
- Turn the pseudocode into a PHPUnit test
- Run the test
- If it fails, keep writing code until the behavior I am testing passes

My experiences over the years have been that a lot of programmers can benefit from both the structure and the discipline that TDD forces upon you. I like how focusing on one test at a time keeps my mind from wandering and thinking too far ahead. Of course, I am always thinking about what I am doing from a high level, but I work very hard to implement the simplest solution to make the test pass, knowing I can use the test to verify I do not break anything when I go back and refactor the code.

In this example, I’m going to be solving the following problem:

> *Write some code that takes any Arabic number and turns it into its Roman numeral equivalent for any number up to 100.*

This is a good problem because it is one that has a known solution (easier to write tests for) and requires you to have a good grasp of several common programming techniques and structures.

### Tooling

I worked on these examples on my late 2016 MacBook Pro laptop, running macOS 10.14.6. I use PhpStorm (with Vim bindings enabled because I am a supporter of the One True Editor) to write my PHP code. I am using PHP 7.3.6 installed using Homebrew and have installed the PHAR version of PHPUnit as per the instructions on the PHPUnit website.

The specifics of what I am using don’t really matter! You don’t have to copy what I am doing to write tests. Just make sure you have a stable version of PHP installed and PHPUnit available to you.

### Getting Started

I’ve created an empty directory to put my code in. I will have my code in the src directory and my tests in the tests directory. Due to PHP and PHPUnit’s flexibility, you can organize these things whatever way you want as long as you handle your paths correctly.

First, let’s talk about how to solve this problem. Roman numerals consist of creating a string consisting of symbols that together represent positive Arabic integer values. You read the result from left to right. So what are the base symbols we need to worry about?

- I -> 1
- V -> 5
- X -> 10
