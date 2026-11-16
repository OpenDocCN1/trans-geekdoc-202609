```
```php
$strQuery .= ")");

unset($objStatement);
$objStatement = $this->objPDO->prepare($strQuery);
foreach ($this->arRelationMap as $key => $value) {
    eval('$actualVal = &$this->' . $value . ';');
    if (isset($actualVal)) {

    if (array_key_exists($value, $this->arModifiedRelations)) {
        if ((is_int($actualVal)) || ($actualVal == NULL)) {
            $objStatement->bindValue
                (':' . $value, $actualVal, PDO::PARAM_INT);
            } else {
            $objStatement->bindValue
                (':' . $value, $actualVal, PDO::PARAM_STR);
            }
        };
    };
};

$objStatement->execute();
$this->ID = $this->objPDO->lastInsertId($this->strTableName . "_id_seq");
}
}

public function MarkForDeletion() {
    $this->blForDeletion = true;
}

public function __destruct() {
    if (isset($this->ID)) {
        if ($this->blForDeletion == true) {
            $strQuery = 'DELETE FROM ' . $this->strTableName . ' WHERE
                "id" = :eid';
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindValue(':eid', $this->ID, PDO::PARAM_INT);
            $objStatement->execute();
        };
    }
}

public function __call($strFunction, $arArguments) {
    $strMethodType = substr($strFunction, 0, 3);
    $strMethodMember = substr($strFunction, 3);
    switch ($strMethodType) {
        case "set":
            return($this->SetAccessor($strMethodMember, $arArguments[0]));
            break;
        case "get":
            return($this->GetAccessor($strMethodMember));
    };
    return(false);
}
```
```