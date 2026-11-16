```
$objStatement->execute();
} else {
    $strValueList = "";
    $strQuery = 'INSERT INTO ' . $this->strTableName . "'(";
    foreach ($this->arRelationMap as $key => $value) {
        eval('$actualVal = &$this->' . $value . ';');
        if (isset($actualVal)) {
            $strQuery .= ". $key . ", '";
            $strValueList .= ":$value, ";
        }
    };
    $strQuery = substr($strQuery, 0, strlen($strQuery) - 2);
    $strValueList = substr($strValueList, 0, strlen($strValueList) - 2);
    $strQuery .= ") VALUES (";
    $strQuery .= $strValueList;
    $strQuery .= ");";
    unset($objStatement);
    $objStatement = $this->objPDO->prepare($strQuery);
    foreach ($this->arRelationMap as $key => $value) {
        eval('$actualVal = &$this->' . $value . ';');
        if (isset($actualVal)) {
            if ((is_int($actualVal)) ||
                ($actualVal == NULL)) {
                $objStatement->bindValue(
                    ':' . $value, $actualVal, PDO::PARAM_INT
                ) else {
                $objStatement->bindValue(
                    ':' . $value, $actualVal, PDO::PARAM_STR
                );
            }
        }
    };
    $objStatement->execute();
    $this->ID = $this->objPDO->lastInsertId
        ($this->strTableName . "_id_seq");
}

public function MarkForDeletion() {
    $this->blForDeletion = true;
}

public function __destruct() {
    if (isset($this->ID)) {
        if ($this->blForDeletion == true) {
            $strQuery = 'DELETE FROM ' .
                $this->strTableName . ' WHERE "id" = :eid';
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindValue(
                ':eid', $this->ID, PDO::PARAM_INT);
            $objStatement->execute();
        }
    }
}
```