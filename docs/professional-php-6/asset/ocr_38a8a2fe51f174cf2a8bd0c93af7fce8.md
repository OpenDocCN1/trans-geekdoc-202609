You've added requests to a few new functions of the DataManager::getEntityData() and get[x]ObjectsForEntity(). getEntityData() returns the data required to instantiate an entity, just as functions you've already seen do for the contact types. The following shows the code for the new functions in class.DataManager.php:

```
// top of file omitted for brevity
...
die("Failed getting phone number data for phone $phoneID");
}
return pg_fetch_assoc($res);
}

public static function getEntityData($entityID) {
    $sql = "SELECT * FROM \"entity\" WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(! ($res & pg_num_rows($res))) {
        die("Failed getting entity $entityID");
    }
    return pg_fetch_assoc($res);
}
?>

```

To add the get[x]ObjectsForEntity() functions, place the following code at the end of class.DataManager.php, just after the getEntityData function:

```
public static function getAddressObjectsForEntity($entityID) {
    $sql = "SELECT \"addressid\" from \"entityaddress\" WHERE " .
        "\"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting address data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new Address($rec['addressid']);
        }
        return $objs;
    } else {
        return array();
    }
}

public static function getEmailObjectsForEntity($entityID) {
    $sql = "SELECT \"emailid\" from \"entityemail\""
    WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting email data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();

```