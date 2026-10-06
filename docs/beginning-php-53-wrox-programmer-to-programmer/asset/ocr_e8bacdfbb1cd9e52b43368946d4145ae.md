# Part III: Using PHP Practice

update() creates an SQL UPDATE statement to set the field values of an existing record in the members table to the values stored in the Member object. The password field is given special treatment: if it contains a password, it is encrypted and the relevant SQL is passed into the UPDATE statement via the $passwordSql variable:

```
$passwordSql = $this->data['password'] ? :password = password(:password);
" : "";
```

In addition, the password field value is passed to the query call with bindValue():

```
if ($this->data['password']) $st->bindValue(":password",
$this->data['password'], PDO::PARAM_STR
```

If the password field is left, the method assumes the password doesn't need updating, and it's left out of the UPDATE statement.

delete() simply deletes the member record with the ID stored in the Member object's id field. To do this, it creates an SQL DELETE statement with the member's ID in a WHERE clause.

# Adding a Deletion to the LogEntry Class

When a member is removed from the system, you also want to remove all their associated log entries from the accessLog table. If you didn't, your database would no longer have integrity because the accessLog table would contain orphaned entries pointing to a non-existent member.

This is easily achieved by adding a method, deleteAllMember(), to the LogEntry class. This method expects to pass the ID of the member in question. It runs a DELETE statement to remove the associated log entries.

Open LogEntry.class file and add the following code after the existing record($id) method:

```
public static function deleteAllMember($memberId) {
$conn = parent::connect();
$sql = "DELETE FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId";

try {
$st = $conn->prepare($sql);
$st->bindValue(":memberId", $memberId, PDO::PARAM_INT);
$st->execute();
} catch (PDOException $e) {
parent::disconnect($conn);
die("Query failed: " . $e->getMessage());
}
}
```

430