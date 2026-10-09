
## Who Should Be Using It?

Developers should be using static code analysis tools while doing their coding work, hopefully before they attempt to commit their code to their version control system.

If you have some reluctant developers, you could always rely on the commit hooks for your version control system and add it there. My own recommendation is to create it as a pre-commit hook-no commit goes through unless the static analysis tool is happy!

Just remember that any use of a tool like this also needs to be accompanied by code reviews to make sure that some of the techniques you can use to make PHPStan “happy” are being correctly applied.

## How Do I Do It?

The configuration file for PHPStan (called `phpstan.neon`) contains the minimal amount of options:

```yaml
parameters:
    bootstrapFiles:
        - config/bootstrap.php
    level: max
    paths:
        - src
        - tests
```

PHPStan’s documentation covers these options and more, but I want to talk about the ones I am using.

The framework for this application (CakePHP[6]) uses a bootstrap file, so I tell PHPStan to use it so it can see things like framework-related configuration values and any custom values I might be using. Depending on the underlying framework, I might not need this at all.

[5] https://docs.phpdoc.org/latest/guide/guides/docblocks.html

[6] https://cakephp.org

I can also tell it what paths I want it to scan. I definitely don't want to be doing any analysis of third-party code in the `vendor` directory created by installing packages via Composer.

PHPStan also uses the concept of an "analysis level". This tells PHPStan just how strict to be in its analysis of your code. I went with `max` (which is an alias for 7) and the range is 0 to 7. By default, it goes with 0. What if I go with level 0?

```
Note: Using configuration file /Users/chartjes/Sites/ibl/phpstan.neon.
51/51 ██████████████████ 100%
------------------------------------
Line    src/Shell/ConsoleShell.php
------------------------------------
60      Method App\Shell\ConsoleShell::main() should return int|null but return statement is missing.
------------------------------------
```

Okay, just one error. I should be using return type hints and PHPStan tells me to add one. Once I do that, PHPStan reports no errors.

I continue raising the level until I get a new set of errors. At the second level, I get:

```
1.  Note: Using configuration file /Users/chartjes/Sites/ibl/phpstan.neon.
2.  51/51 ██████████████████ 100%
3.  ------------------------------------
4.  Line    src/Controller/Component/StandingsComponent.php
5.  ------------------------------------
6.  514     Comparison operation ">=" between (array|float|int) and 13 results in an error.
7.  525     Comparison operation "<=" between (array|float|int) and 5 results in an error.
8.  ------------------------------------
9.
10.
11. Line    src/Model/Table/GamesTable.php
12. ------------------------------------
13. 143     Call to an undefined method Cake\ORM\Query::orWhere().
14. ------------------------------------
15.
16.
17. Line    src/Util/Rosters.php
18. ------------------------------------
19. 15      Call to an undefined method Cake\ORM\Table::generateListByNicknameName().
20. ------------------------------------
21.
22.
23. Line    src/View/AjaxView.php
24. ------------------------------------
25. 48      Call to an undefined method Cake\Http\Response::type().
26. ------------------------------------
27.
28. [ERROR] Found 5 errors
```

Now it seems like PHPStan is definitely getting stricter and pointing out things in my code that, while it works, could potentially cause problems down the road. A summary of its complaints could be:

- I need to deliberately cast some values in comparisons.
- I need to specifically tell PHPStan what some classes in use are rather than assume magic.

Okay, I'll make some changes and explain why they are necessary. Here's a line of code it's complaining about:

```php
if (($result->home_score + $result->away_score) >= 13)
```

PHPStan is looking at this and saying, "I'm not 100% sure what could be in `$result->home_score` or `$result->away_score` so can you clear things up?"

I think that is a fair question. A revised line could look like this:

```php
if ((int)($result->home_score + $result->away_score) >= 13)
```

Another way to do it would be even stricter and cast both values to be integers.

```php
if ((int)$result->home_score + (int)$result->away_score >= 13)
```

A developer friend of mine has said on more than one occasion that code that uses static analysis tools "no longer looks like PHP". Which is to say, "It no longer looks like PHP code the way a lot of people write it." PHP is incredibly forgiving in many cases due to its dynamic typing capabilities. It tries to figure out what your intent is. Maybe those `home_score` and `away_score` class attributes are always going to be integers. By deliberately casting them as integers, I am 100% making sure that comparison does not cause a PHP-related error. Hopefully, those two attributes never have incorrect values!

So at level 2, it says there are four more errors. I'll fix the other math-related one and then turn my attention to those other reported problems.

| Line | File | Description |
| :--- | :--- | :--- |
| 143 | `src/Model/Table/GamesTable.php` | Call to an undefined method `Cake\ORM\Query::orWhere()`. |

This error is because PHPStan cannot understand where that `orWhere()` method comes from. Is this really an error? No. The code clearly works, so I could tell PHPStan to ignore this problem. According to the documentation I could add a PHPStan-specific annotation to tell it to ignore the error coming from that line.

Let's do that--some tools can definitely report false positives and I feel like this is one of them. This is what the updated code looks like now:

```php
return $this->find()
    ->where([ 'week <=' => $week ])
    ->contain('HomeTeams, AwayTeams', function ( Query $sq ) use ( $teams ) {
        /** @phpstan-ignore-next-line */
        return $sq->where('HomeTeams in', $teams)
            ->orWhere('AwayTeams in', $teams);
    });
```

Down to just two errors. The next one is this:

```
Line  src/Util/Rosters.php
15      Call to an undefined method Cake\ORM\Table::generateListByNicknameName().
```

Hrm. I did a search of the codebase, and that method doesn't exist at all. Is this dead code? An experiment I was doing and never finished? More searching makes me believe that it is, in fact, code that is not being used. Manual testing of the page that displays rosters verifies this is the case.

Okay, down to one last error:

```
Line  src/View/AjaxView.php
48      Call to an undefined method Cake\Http\Response::type().
```

I suspect this is code that older versions of the framework used, but along the upgrade path, it's stuck around. I could delete the file, but I do not have enough test coverage to feel comfortable doing it. Instead, I am going to add some details to the `phpstan.neon` file that tells it to ignore this file.

```yaml
parameters:
  bootstrapFiles:
    - config/bootstrap.php
  level: 2
  paths:
    - src
    - tests
  excludePaths:
    - src/View
```

No more errors! I have to increase the analysis level to six before I get another set of problems to review:

```
Note: Using configuration file /Users/chartjes/Sites/tbl/phpstan.neon.
48/48 [||||||||||||||||||||||||||] 100%
-----------------------------------------
Line   src/Model/Table/GamesTable.php
   143  Method App\Model\Table\GamesTable::findAllByTeams() has parameter
   $teams with no value type specified in iterable type array.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
   143  Method App\Model\Table\GamesTable::findAllByTeams() return type has no
   value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
-----------------------------------------
   Line   src/Model/Table/TeamsTable.php
   104  Method App\Model\Table\TeamsTable::findByConference() return type has
   no value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
-----------------------------------------
   Line   src/Util/Boxscore.php
   12  Property App\Util\Boxscore::$schedule has no typehint specified.
   13  Property App\Util\Boxscore::$teams has no typehint specified.
   14  Property App\Util\Boxscore::$games has no typehint specified.
-----------------------------------------
[ERROR] Found 6 errors
```
