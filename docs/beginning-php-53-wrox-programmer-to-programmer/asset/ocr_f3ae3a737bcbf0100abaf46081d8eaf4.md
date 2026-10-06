# Chapter 13: Retrieving Data from MySQL With PHP

```
$members = array();
foreach ( $st->fetchAll() as $row ) {
    $members[] = new Member( $row );
}
$st = $conn->query(" SELECT count_rows() AS totalRows * ");
$row = $st->fetch(1);
parent::disconnect($conn);
nreturn array(\$members, $row["totalRows"]);
} catch ( PDOException $e ) {
    parent::disconnect($conn);
    die("Query failed: " . $e->getMessage());
}

public static function getMember($ $ id ) {
    $conn = parent::connect($conn);
    $sql = " SELECT FROM " . TBL_MEMBERS . " WHERE id = :id";

try {
    $st = $conn->prepare($sql);
    $st->bindValue(":id", $id, PDO::PARAM_INT);
    $st->execute();
    $row = $st->fetch(1);
    parent::disconnect($conn);
    if ( $row ) return new Member( $row );
} catch ( PDOException $e ) {
    parent::disconnect($conn);
    die("Query failed: " . $e->getMessage());
}

public function getGenderString() {
    return ($this->data["gender"] == "f" ) ? "Female" : "Male";
}

public function getFavoriteGenreString() {
    return ($this->_genres[$this->data["favoriteGenre\]] );
}

?
```

The first script includes the DataObject class so that it can derive the Member class from DataObject. The next sets use the $data array keys, initializing each value to an empty string. Only this list lets you see at-a-glance the Member class works with, but it also enables the DataObject class’s __construct method to validate each field name that’s passed to it when creating the object. If a field name is passed that isn't in the $data array, it's rejected.

The class also creates a private array, $_genres, to map the ENUM values of the favoriteGenre in the members table (for example, "nonfiction") to human-readable strings (such as "Non-Fiction").