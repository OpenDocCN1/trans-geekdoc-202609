
## 2. STATIC CODE ANALYSIS TOOLING

Also, you now see PHPStan offering suggestions on how to solve some of the issues at this level. It seems like it is highlighting the same problem. I’ll go and read the page that URL points to.

Okay, the first one:

```text
Line    src/Model/Table/GamesTable.php
143     Method App\Model\Table\GamesTable::findAllByTeams() has parameter
        $teams with no value type specified in iterable type array.
        □ See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type/
```

Here’s the code it doesn’t like:

```php
public function findAllByTeams(int $week, array $teams): Query
```

It wants to know what is inside $teams. I believe it is an integer, so I can create a docblock for that method, make sure to add that in there, and then I can re-run PHPStan.

```php
1.  /**
2.  * @param int $week
3.  * @param array<int> $teams
4.  * @return Query
5.  */
6.  public function findAllByTeams(int $week, array $teams): Query
7.  {
8.      return $this->find()
9.          ->where(['week <=' => $week])
10.         ->contain('HomeTeams, AwayTeams', function (Query $q) use ($teams) {
11.             /** @phpstan-ignore-next-line */
12.             return $q->where('HomeTeams in', $teams)
13.                     ->orWhere('AwayTeams in', $teams);
14.         });
15.  }
```

The next problem PHPStan is complaining about is that it wants to know what is inside that Query collection the findAllByTeams() method is returning. The answer is to change the return type to say it is returning GamesTable objects in that Query collection. With that change, here’s the whole method.

### How Do I Do It?

```php
1.   /**
2.     * @param int $week
3.     * @param array<int, Team>
4.     * @return Query<GameTable>
5.     */
6.   public function findAllByTeams(int $week, array $teams): Query
7.   {
8.       return $this->find()
9.            ->where(['week <='=> $week])
10.          ->contain(['HomeTeams, AwayTeams', function (Query $q) use ($teams) {
11.              /** @phpstan-ignore-next-line */
12.              return $q->where('HomeTeams in', $teams)
13.                       ->orWhere('AwayTeams in', $teams);
14.          });
15.   }
```

So what was the point of this other than just making PHPStan happy? As mentioned earlier in this chapter, many IDEs can look at those document blocks and the code itself and make code completion easier. If other code is iterating over the collection of objects being returned by that method, it can verify what methods are available on those objects.

All of this static analysis has one goal—code that is clearer in intent, easier to debug, and less likely to behave in unexpected ways.

There are only two more sets of errors left at this level. I want to fix this one:

```text
Line           src/Model/Table/TeamsTable.php
104  Method App\Model\Table\TeamsTable::findByConference() return type has no value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
```

This is a similar issue to the one I just fixed. Similar solution:

```php
1.   /**
2.     * @param string $conference
3.     * @return Query<TeamTable>
4.     */
5.   public function findByConference(string $conference): Query
6.   {
7.       return $this->find()
8.            ->contain('Divisions')
9.            ->where(['Divisions.conference' => $conference]);
10.   }
```

One last set of problems to fix!

```text
Line src/Util/Boxscore.php
12 Property App\Util\Boxscore::$schedule has no typehint specified.
13 Property App\Util\Boxscore::$teams has no typehint specified.
14 Property App\Util\Boxscore::$games has no typehint specified.
```

Just missing some type hints. Looking at the code, I know what type it should be. The updated code should look like this:

```php
1. <?php
2.
3. declare(strict_types=1);
4.
5. namespace App\Util;
6.
7. use Cake\ORM\Locator\TableLocator;
8. use Cake\ORM\Table;
9.
10. class Boxscore
11. {
12.
13.     public Table $games;
14.     public Table $schedule;
15.     public Table $teams;
16.
17.
18.     public function __construct()
19.     {
20.         $this->schedule = (new TableLocator())->get('Schedule');
21.         $this->teams = (new TableLocator())->get('Teams');
22.         $this->games = (new TableLocator())->get('Games');
23.     }
24.
25.    /**
26.     * @param int $slackerWeek
27.     * @return array<string, mixed>
28.     */
29.    public function getMissing(int $slackerWeek): array
30.    {
31.        if ($slackerWeek === 0) {
32.            return [];
33.        }
34. 
35.        $missingBoxes = [];
36. 
37.        // Build an array of teams with codes
38.        $results = $this->teams->find()
39.            ->select(['tbl', 'code'])
40.            ->all();
41.        $teams = [];
42. 
43.        foreach ($results as $result) {
44.            $teams[$result->code] = $result->tbl;
45.        }
46. 
47.        $results = $this->schedule
48.            ->find()
49.            ->contain('Teams')
50.            ->where([
51.                'Schedule.status' => 0,
52.                'Schedule.week <=' => $slackerWeek
53.            ])->order('Schedule.week, Teams.tbl');
54. 
55.        foreach ($results as $result) {
56.            $key = $result->week . $teams[$result->home];
57.            $missingBoxes[$key] =
58.                "wk{$result->week} {$teams[$result->away]}@{$teams[$result->home]}";
59.        }
60. 
61.        ksort($missingBoxes, SORT_NATURAL);
62.        return $missingBoxes;
63.    }
64. }
```

Now I set the PHPStan analysis level to 7 and see what problems it reports.

```text
Line   src/Console/Installer.php
----------------------------------------
148  Parameter #1 $array of function array_diff expects array, array<int,
string>|false given.
180  Parameter #3 $subject of function str_replace expects array|string,
string|false given.
```

This is code I didn’t write; it was created by the framework. I’ll tell PHPStan to ignore it.

```yaml
1. parameters:
2.     bootstrapFiles:
3.         - config/bootstrap.php
4.     level: 7
5. paths:
6.     - src
7.     - tests
8.     excludePaths:
9.         analyse:
10.        - src/View
11.        - src/Console/Installer.php
```

The final result is that PHPStan no longer complains about anything!

### Bonus Round!

PHPStan revealed a small number of problems with the codebase. What if you have a much less-structured application? I happen to have one like that too! There is another application that could be considered a “companion” to the one I have been sharing samples from. It has almost no structure to it at all. Let’s say I want to start applying static analysis to this codebase at its highest level. What would it say?

The first step is to create a PHPStan configuration file:

```yaml
1. parameters:
2. bootstrapFiles:
3. - vendor/autoload.php
4. level: 7
5. paths:
6. - .
7. excludePaths:
8. analyse:
9. - vendor
```

How bad could it be?

```text
[ERROR] Found 312 errors
```

Maybe that’s pretty bad. Now, chances are that if this was some kind of paid project instead of a hobbyist one I might not want to spend all that developer time fixing older problems. Instead, I want to make sure all new code I write can be analyzed by PHPStan but accept the current state of the codebase.

For this, PHPStan has the concept of “setting a baseline” Using the `--generate-baseline` switch from the command line, PHPStan generates a file that contains all the errors it finds.

Here’s what I saw when I ran that command:

```bash
./vendor/bin/phpstan --generate-baseline
```

```text
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [#################] 100%

[OK] Baseline generated with 312 errors
```

Then, according to the instructions, I add a reference to this file in my phpstan.neon configuration file.

```yaml
1. includes:
2.      - phpstan-baseline.neon
3.
4. parameters:
5.     bootstrapFiles:
6.      - vendor/autoload.php
7.      level: 7
8.      paths:
9.      - .
10.     excludePaths:
11.        analyse:
12.      - vendor
```

Having done this, I should not see any errors the next time I ask PHPStan to analyze my code:

```text
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [████████████████████████████] 100%

[OK] No errors
```

Now I can start refactoring or adding code to the project, and PHPStan will only report on errors it hasn’t already seen. This is a very handy tool for large legacy projects.
