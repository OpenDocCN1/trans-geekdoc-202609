```
}
?>
```

The start to any AMFPHP project should be the method table either included in the same service file or in a separate file that is included. The advantage to using the same file is you can quickly make changes and not have to maintain a different file.

The method table in this example is included in the service constructor function. The connection method is set to private to ensure a higher level of security.

```
function Albums()
{
    $this->methodTable = array
    (
        "connect" => array
        (
            "access" => "private"
        ),
        "getAlbumByGenreID" => array
        (
            "access" => "remote"
        )
    );
}
```

The connection method first checks for an existing connection to limit resources. If an existing connection is not found, a new one is created and stored in the private variable _connection.

```
/**
 * @access private
 * @desc Connect to database - **PRIVATE**
 */
function connect()
{
    if($this->_connection == null)
    {
        $this->_connection = mysql_connect(
            $this->dbHost,
            $this->dbUser,
            $this->dbPass
        );
        mysql_select_db($this->dbName, $this->_connection);
    }
}
```