```
```php
<?php

$GLOBALS['sess_server'] = 'localhost';
$GLOBALS['sess_db'] = 'sessions';
$GLOBALS['sess_username'] = 'user';
$GLOBALS['sess_password'] = 'pass';

function sess_open() {
    $GLOBALS['sess_mysqli'] = mysqli_connect(
        $GLOBALS['sess_server'],
        $GLOBALS['sess_username'],
        $GLOBALS['sess_password']
    );
    mysqli_select_db($GLOBALS['sess_mysqli'],
    $GLOBALS['sess_db']);
}

function sess_close() {
    mysqli_close($GLOBALS['sess_mysqli']);
}

function sess_read($id) {
    $result = mysqli_query(
        $GLOBALS['sess_mysqli'],
        sprintf('SELECT data FROM sessiondata WHERE id
    = \'%\'',
        mysqli_real_escape_string($GLOBALS
['sess_mysqli'], $id))
    );
    if ($row = mysqli_fetch_object($result)) {
        $ret = $row->data;
        mysqli_query(
            $GLOBALS['sess_mysqli'],
            sprintf('UPDATE sessiondata SET
    access=\'%\' WHERE id=\'\'',
            date('YmdHis'),
```
```