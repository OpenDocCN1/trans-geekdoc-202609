# 7. Test-After Development by Example

This is a point where I am making a judgment call about how much extra work I wish to do. This code is using the getById() method I refactored to make sure it was correctly adding the uncarded indicator to players’ info. Do I really need to create a separate object which processes an array of player details and creates the log entry, which is, in turn, handed over to by transaction_log() function? I think I am better served going through any code generating transaction log entries and make sure they are using RosterModel methods that are tested.

Searching some more, I found this code snippet that is being used whenever one or more players are being released from a team.

```
```php
1. if (isset($_POST['release'])) { $release = true; }
2.
3. if ($release === true) {
4.   $release_list = $_POST['release'];
5.   $released_players = [];
6.
7. /** @var array $release_list */
8. foreach ($release_list as $player_id) {
9.   $info = $roster->getById($player_id);
10.   $player_name = trim($info['tig_name']);
11.
12.   if ($roster->isUncarded($player_name)) {
13.     $uc_value = $roster->getUncardedValue($player_name);
14.     $player_name .= " [UC {$uc_value}]";
15.   }
16.
17.   $released_players[] = $player_name;
18. }
19.
20. $log_entry = 'Releases ' .implode(', ', $released_players);
21. transaction_log($tbl_team, $log_entry, $db);
22. $roster->releasePlayerByList($release_list);
23. include 'templates/modify_roster/release.php';
24. }
```
```

I think I can refactor this code to use a different method, and be confident it is doing the correct thing when generating the log entry.