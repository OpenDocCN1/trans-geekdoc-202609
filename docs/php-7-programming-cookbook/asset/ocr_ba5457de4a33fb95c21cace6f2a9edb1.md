+   21. We then use the mapping array to retrieve values from the source table using keys expected in the destination table:

    ```php
    foreach ($mapping as $key => $value) {
        $entry[$value] = $result[$key] ?? NULL;
    }
    return $entry;
    }
    ```

+   22. The heart of this class is a getRandomEntry() method, which generates a single array of fake data. We loop through $mapping one entry at a time and examine the various parameters:

    ```php
    public function getRandomEntry()
    {
        $entry = array();
        foreach ($this->mapping as $key => $value) {
            if (isset($value['source'])) {
                switch ($value['source']) {
    ```

+   23. The source parameter is used to implement what effectively serves as a Strategy Pattern. We support four different possibilities for source, all defined as class constants. The first one is SOURCE_FILE. In this case, we use the getEntryFromFile() method discussed previously:

    ```php
    case self::SOURCE_FILE : 
        $entry[$key] = $this->getEntryFromFile(
            $value['name'], $value['type']);
        break;
    ```

+   24. The callback option returns a value according to the callback supplied in the $mapping array:

    ```php
    case self::SOURCE_CALLBACK : 
        $entry[$key] = $value['name']();
        break;
    ```

+   25. The SOURCE_TABLE option uses the database table defined in $mapping as a lookup. Note that getEntryFromTable(), discussed previously, is able to return an array of values, which means we need to use array_merge() to consolidate the results:

    ```php
    case self::SOURCE_TABLE : 
        $result = $this->getEntryFromTable(
            $value['name'],$value['idCol'],$value['mapping']);
        $entry = array_merge($entry, $result);
        break;
    ```