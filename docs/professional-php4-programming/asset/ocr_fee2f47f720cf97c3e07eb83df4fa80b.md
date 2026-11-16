The populatePrivilege() method uses the supplied ID to pull the details of the appropriate privilege from the database:

```
```php
function populatePrivilege($iPrivilegeID)
{
    // Populate the data for this privilege
    global $sql;
    $sql->query("SELECT * FROM Privilege WHERE priv_id=$iPrivilegeID");
    $row = $sql->fetchObject();
    $this->setDescription($row->description);
    $this->privilegeExists = 1;
    $this->setPriv_id($iPrivilegeID);
    return $this->privilegeExists;
}
```
```

create() adds a new privilege to the database. Only the description is necessary for this method as the primary key (the privilege ID) is added automatically as one greater than the highest current ID:

```
```php
function create()
{
    // Add the new privilege to the database
    global $sql;
    $sDescription = $this->getDescription();
    $sql->query("INSERT INTO Privilege (description) VALUES ('$sDescription')");
}
```
```

The next two functions are straightforward. delete() deletes the privilege from the database, and sets a flag to tell the current object to ignore this privilege, while update() updates the privilege's description in the database:

```
```php
function delete()
{
    // Delete the privilege from the database
    global $sql;
    $iPrivilegeID = $this->getPriv_id();
    if (!$iPrivilegeID) return;
    // First remove from UserPrivilege
    $sql->query("DELETE FROM UserPrivilege WHERE priv_id=$iPrivilegeID");
```
```