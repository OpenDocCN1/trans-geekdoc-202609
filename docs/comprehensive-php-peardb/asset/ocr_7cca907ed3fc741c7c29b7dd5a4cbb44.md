| Method | Description |
|---|---|
| getAssoc() | Fetch the entire result set of a query and return it as an associative array using the first column as the key. If the result set contains more than two columns, the value is an array of the values from column 2-n. If the result set contains only two columns, the returned value will be a scalar with the value of the second column (unless forced to an array with the $force_array parameter). |
| getAll() | Fetch all the rows returned from a query. |
| autoCommit() | Enable automatic commit. |
| commit() | Starts a commit. |
| rollback() | Starts a rollback. |
| numRows() | Returns the number of rows in a result object. |
| affectedRows() | Returns the affected rows of a query. |
| errorNative() | Returns an error message, provided by the database. |
| nextId() | Returns the next free id of a sequence. |
| createSequence() | Creates a new sequence. |
| dropSequence() | Deletes a sequence. |
| tableInfo() | Returns meta data about the result set. |