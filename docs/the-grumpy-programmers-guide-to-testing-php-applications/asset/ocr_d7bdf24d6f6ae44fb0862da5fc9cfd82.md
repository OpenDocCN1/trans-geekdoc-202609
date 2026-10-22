```
```php
$expected = 'Trades Moe, Larry, Curly to TESTMORE';
$tradePartner = 'TESTMORE';
$tradeComment = 'Trade TESTMORE 01/01';

// Data contains compound ID's of <trade partner 1>_<player_id>
$data = ['team1_1', 'team1_2', 'team1_3'];
$rm = $this->prophesize(Roster::class);
$playerIds = [1, 2, 3];

// Mock our getById() calls
$rm->getById($playerIds[0])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name' => 'Moe']);
$rm->getById($playerIds[1])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name'=> 'Larry']);
$rm->getById($playerIds[2])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name'=> 'Curly']);

// Create our updatePlayerTeam test spies
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[0],
    $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[1],
    $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[2],
    $tradeComment)->shouldBeCalled();

$rm->makeInactive($playerIds[0])->shouldBeCalled();
$rm->makeInactive($playerIds[1])->shouldBeCalled();
$rm->makeInactive($playerIds[2])->shouldBeCalled();

$tm = new Transaction($rm->reveal());
$tm->transactionDate = '01/01';

// Act
$response = $tm->generateTradeLogEntry(
    $data, $tradePartner);
```
```