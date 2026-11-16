validate() checks the submitted form for valid data and creates a new Privilege object depending on the results:

```
```
function validate()
{
    // Validate form data and set the global priv object

    global $Priv_id, $description, $oPriv;
```
```

If an ID is supplied and no Privilege with that ID exists, a new Privilege with that ID is created:

```
```
    if ($priv_id) {
        // Make sure it's a valid PrivID
        $oPriv = new Privilege((int)$priv_id);
        if (!$oPriv->privilegeExists) return 0;
```
```

If no ID is supplied, a blank Privilege is used:

```
```
    } else {
        $priv_id = 0;
        $oPriv = new Privilege();
    }
    return 1;
}
```
```

save() sets the description of the privilege before checking if the privilege to be saved exists. If it does then save() will try to update it in the database. If it does not exist, save() will try to create a brand new database entry:

```
```
function save()
{
    // Save the selected privilege

    global $oPriv, $description;

    $oPriv->setDescription(addslashes($description));
    if ($oPriv->privilegeExists) {
        if (!$oPriv->update()) return 0;
    } else {
        if (!$oPriv->create()) return 0;
    }
    return 1;
}
```
```

delete() removes the privilege specified:

```
```
function delete($oPriv)
{
    // Remove the selected privilege
```
```