```
return $rows;

}

/**
 * List of albums for RecordSet
 * /
function getAlbumByGenreID_recordset($genreID)
{
    $this->connect();

    $sql = "SELECT g.name, a.artist, a.albumName
    FROM albums a, genre g
    WHERE a.genreID=g.id
    AND g.id=" . $genreID;

    return mysql_query($sql, $this->_connection);

}

?>

```

# ActionScript for AMFPHP integration

The next step is to build the Flash portion of the application, which is responsible for displaying
the album data in a prebuilt DataGrid component.

The only function changes are within the onResult function for this more complete example.

```
function onResult(responds:Object):void
{
    albumsDG.removeAll();
    for(var i:uint=0; i < responds.length; i++)
    {
        albumsDG.addItem(responds[i]);
    }

}
```

# Clearing old results

The onResult function clears any existing data in the DataGrid by making a call to the
removeAll method of the DataGrid component.

```
albumsDG.removeAll();
```