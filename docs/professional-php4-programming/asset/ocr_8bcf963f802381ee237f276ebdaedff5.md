Return the Music_Item object:

```
return new Function_Result(null, $item);
}
```

The function search() returns music items which contain $searchText in artist or title column:

```
function search($searchText)
{
```

SELECT statement to retrieve music items which contain $searchText in the artist or title column:

```
$searchStmt = "SELECT itemNo, itemType, price, title, artist FROM
MusicShop WHERE artist LIKE '%' . $searchText . '%'
OR title LIKE '%' . $searchText . '%' ";
```

Call getSearchResults() to execute the $searchStmt SQL query:

```
$funcResult = $this->getSearchResults($searchStmt);
```

Return the search result:

```
return $funcResult->returnValue;
}
```

The function searchByTitle() returns Music_Item objects which contain $searchText in title column:

```
function searchByTitle($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, artist
    FROM MusicShop
    WHERE title LIKE '%' . $searchText . '%' ";
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```

The function searchByArtist() returns music items which contain $searchText in the artist column:

```
function searchByArtist($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, artist
    FROM MusicShop
    WHERE artist LIKE '%' . $searchText . '%' ";
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```