# 5. Test Double

```
```php
<?php
declare(strict_types=1);
use Aura\SqlQuery\QueryFactory;

require __DIR__ . '../models/rosters.php';
require __DIR__ . '../models/transactions.php';

class TransactionsTests extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function it_generates_proper_transaction_info_for_a_trade(): void
    {
        /**
         * Given I have an array that contains players
         * When I submit a list of players
         * And I submit a transaction description
         * Then I should get a one-line transaction being generated
         */

        // Assert
        $this->assertTrue(false);
    }
}
```
```

Time to create the data you need for the test and a mock of the Roster object and then run your test. Remember to do this after every change to help you isolate any problems you run into!

```
```php
// Arrange
$expected = 'Trades Moe, Larry, Curly to TEST';
$tradePartner = 'TEST';

// Data contains compound ID's of <trade partner 1>_<player_id>
$data = ['team1_1', 'team1_2', 'team1_3'];

$rm = $this->prophesize(Roster::class);
$tm = new Transaction($rm->reveal());
```
```