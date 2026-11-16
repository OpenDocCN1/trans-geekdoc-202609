member variable, ‘id’. The constructor also sets up the relation map, which maps relation names to member variable names.

In addition, notice the use of a `Save()` method to commit changes (`INSERT` or `UPDATE`, as required); and a `MarkForDeletion()` method to allow destruction.

# Meet the Code

You can enter the following code for the class and save it as `userv2.php`. It’s a long piece of code, so be careful to ensure that you don’t accidentally introduce any carriage returns or linefeeds where code spans the width of this book’s page:

```
<?php
class User {
    private $ID;
    private $objPDO;
    private $strTableName;
    private $arRelationMap;
    private $blForDeletion;
    private $FirstName;
    private $LastName;
    private $Username;
    private $Password;
    private $EmailAddress;
    private $DateLastLogin;
    private $TimeLastLogin;
    private $DateAccountCreated;
    private $TimeAccountCreated;
    public function __construct(PDO $objPDO, $id = NULL) {
        $this->strTableName = "system_user";
        $this->arRelationMap = array(
            "id" => "ID",
            "first_name" => "FirstName",
            "last_name" => "LastName",
            "username" => "Username",
            "md5_pw" => "Password",
            "email_address" => "EmailAddress",
            "date_last_login" => "DateLastLogin",
            "time_last_login" => "TimeLastLogin",
            "date_account_created" => "DateAccountCreated",
            "time_account_created" => "TimeAccountCreated");
        $this->objPDO = $objPDO;
        if (isset($id)) {
            $this->ID = $id;
            $strQuery = "SELECT ";
            foreach ($this->arRelationMap as $key => $value) {
                $strQuery .= "\\" . $key . "\\",";
```