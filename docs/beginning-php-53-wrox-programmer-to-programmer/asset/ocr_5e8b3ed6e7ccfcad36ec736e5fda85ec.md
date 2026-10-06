# Chapter 13: Retrieving Data from MySQL with PHP

```
"memberId" => "",
"pageUrl" => "",
"numVisits" => "",
"lastAccess" => ""
);

public static function getLogEntries($memberId) {
    $conn = parent::connect();
    $sql = "SELECT * FROM TBL_ACCESS_LOG WHERE memberId = :memberId
        ORDER BY lastAccess DESC";

    try {
        $stmt = $conn->prepare($sql);
        $stmt->bindValue(":memberId", $memberId, PDO::PARAM_INT);
        $logEntries = array();
        foreach ($stmt->fetchAll() as $row) {
            $logEntries[] = new LogEntry($row);
        }
        parent::disconnect($conn);
        return $logEntries;
    } catch (PDOException $e) {
        parent::disconnect($conn);
        die("Query failed: " . $e->getMessage());
    }
}
?
```

As Member, the LogEntry class derives from the DataObject abstract class. Its protected $data array contains the field names from theLog table: memberId, pageUrl, numVisits, and lastAccess.

LogEntry contains just one method, getLogEntries(), which retrieves a list of all accessLog records for a particular member (specified by $memberId) as LogEntry objects. The query sorts the entries in descending order of access date — that is, newest first.

```
$sql = "SELECT * FROM TBL_ACCESS_LOG WHERE memberId = :memberId
    ORDER BY lastAccess DESC";
```

The rest of the method is similar to Member::getMembers($). The statement is prepared, the $memberId parameter is bound to the $memberId, and the query is run. The result is returned as an array of associative arrays using PDOStatement::fetchAll(), and each associative array is used to create a new LogEntry object, which is then added to an array. The method returns the array of LogEntries to the calling code.

# Creating the view_members.php Script

Now you've laid all the foundations for your member viewer application; in fact you've already done most of the hard work. Now it's just a case of writing two scripts: one to display the list of members, and another to display details of an individual member.