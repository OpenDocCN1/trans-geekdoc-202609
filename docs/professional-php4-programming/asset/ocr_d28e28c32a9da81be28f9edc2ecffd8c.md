```
// Next remove from Privilege
$Sql->query("DELETE FROM Privilege WHERE priv_id=$iPrivilegeID");
$this->privilegeExists = 0;
}
function update()
{
    // Update the privilege in the database
    global $Sql;
    $iPrivilegeID = $this->getPriv_id();
    $sDescription = $this->getDescription();
    if (!$iPrivilegeID) return;
    $Sql->query("UPDATE Privilege SET description='$sDescription'
        WHERE priv_id=$iPrivilegeID");
}
```

Lastly, we have the getXxx() and setXxx() methods for Privilege's properties:

```
function getPriv_id()
{
    // Returns the property
    return $this->priv_id;
}
function setPriv_id($iVal)
{
    // Set the property
    $this->priv_id = (int)$iVal;
    return 1;
}
function getDescription()
{
    // Returns the property
    return $this->description;
}
function setDescription($sVal)
{
    // Set the property
    if (strlen ($sVal) > 50) return 0;
    $this->description = $sVal;
    return 1;
}
}
?>
```