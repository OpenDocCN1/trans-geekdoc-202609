```
```php
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
            2 => ['ibl_team' => 'TEST', 'display_name'=> 'Larry'],
            3 => ['ibl_team' => 'TEST', 'display_name'=> 'Curly'],
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
```
```