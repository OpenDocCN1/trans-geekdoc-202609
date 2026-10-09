# ## 2. STATIC CODE ANALYSIS TOOLING

Also, you now see PHPStan offering suggestions on how to solve some of the issues at this level. It seems like it is highlighting the same problem. I’ll go and read the page that URL points to.

Okay, the first one:

```
```
Line    src/Model/Table/GamesTable.php
143     Method App\Model\Table\GamesTable::findAllByTeams() has parameter
        $teams with no value type specified in iterable type array.
        □ See: https://phpstan.org/blog/solving-phpstan-no-value-type-speci-
        fied-in-iterable-type/
```
```

Here’s the code it doesn’t like:

```
```php
public function findAllByTeams(int $week, array $teams): Query
```
```

It wants to know what is inside $teams. I believe it is an integer, so I can create a docblock for that method, make sure to add that in there, and then I can re-run PHPStan.

```
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
```

The next problem PHPStan is complaining about is that it wants to know what is inside that Query collection the findAllByTeams() method is returning. The answer is to change the return type to say it is returning GamesTable objects in that Query collection. With that change, here’s the whole method.