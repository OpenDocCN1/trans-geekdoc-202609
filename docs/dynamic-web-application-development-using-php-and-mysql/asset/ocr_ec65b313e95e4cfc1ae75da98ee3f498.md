```
srand( (double) microtime() * 1000000);
$intPercentage = rand(0,99);

$dbWriteRecords = mysql_query("INSERT INTO percentageValues VALUES ('', '$intPercentage')", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );

$dbRecords = mysql_query("SELECT * FROM percentageValues", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );
$intCount = mysql_num_rows($dbRecords);
if ($intCount > 20) {
    $intStart = $intCount - 20;
    $dbRecords = mysql_query("SELECT * FROM percentageValues LIMIT $intStart,20", $dbLocalhost)
        or die("Problem reading table: " . mysql_error() );
}

$arrPercent = array (0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0);
$intSize = count($arrPercent);
$intCount = 0;

while ( ($arrRecords = mysql_fetch_array($dbRecords) ) ) {
    $arrPercent[$intCount++] = $arrRecords["Percentage"];
}
graph($arrPercent, $intSize);

function graph($arrData, $intSize) {
    $intBarWidth = 10;
    $intBarSpacing = 10;
    $intMultiplier = 1.5;

    $intSize=count($arrData);
    echo "<div id='graphScale'><img src='graphics/scale.gif' width='27' height='150' /></div>";
    echo "<div id='graphBars'>";
    echo "<img src='graphics/hiddenbar.gif' width='0' height=' " . 99 * $intMultiplier . "'>";
    for($intCount=0;$intCount<$intSize;$intCount++) {
        echo "<img src='graphics/redbar.gif' width='$intBarWidth' height=' " . $arrData[$intCount] * $intMultiplier . "'>";
    }
    echo "</div>";
}
?>
```

The script begins by forming a connection to database ‘graph’:

```
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("graph", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
```