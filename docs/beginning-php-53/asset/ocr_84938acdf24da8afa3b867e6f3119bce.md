# Enhancing the LogEntry Class to Record Page Views

Each time a member views a page in the members’ area, you’re going to record the event in the accessLog table. To do this, you need to add a method to the LogEntry class. Open your LogEntry. class.php file and add the following record() method to the end of the class, after the getLogEntries() method:

```
public function record() {
    $conn = parent::connect();
    $sql = "SELECT * FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId
    AND pageUrl = :pageUrl";
    try {
        $st = $conn->prepare( $sql );
        $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
        $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
        $st->execute();
        if ( $st->fetch() ) {
            $sql = "UPDATE " . TBL_ACCESS_LOG . " SET numVisits = numVisits + 1
            WHERE memberId = :memberId AND pageUrl = :pageUrl";
            $st = $conn->prepare( $sql );
            $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
            $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
            $st->execute();
        } else {
            $sql = "INSERT INTO " . TBL_ACCESS_LOG . " ( memberId, pageUrl,
            numVisits ) VALUES ( :memberId, :pageUrl, 1 ) ";
            $st = $conn->prepare( $sql );
            $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
            $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
            $st->execute();
        }
        parent::disconnect( $conn );
    } catch ( PDOException $e ) {
        parent::disconnect( $conn );
        die( "Query failed: " . $e->getMessage() );
    }
}
```

The record() method takes the member ID and page URL stored in the object’s memberId and pageUrl data fields, and uses them to record the page view in the accessLog table. If there’s already a row in the table for that particular member and page, its numVisits field is incremented using an UPDATE statement. If the row doesn’t exist, it’s created using an INSERT statement, setting numVisits to 1.