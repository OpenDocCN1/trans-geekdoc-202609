```
unset($pass);
unset($database);
?>
```

After the database connection is set you can continue the development of the monitor.php file.
The $action is passed along the URL, but needs to be valid in order for the script to know which
state it should be running in.

```
$action = (isset($_GET['action'])) ? $_GET['action'] : "";
```

Assuming the action is valid and the value is getsites, which is set up to return a listing of the
sites that are being monitored. The process of retrieving the site list is accomplished using a loop
that loads the information from the MySQL database. The site list is returned to Flash as an XML
object defining each of the sites and where they are located.

The SQL to retrieve the list is set up to load all entries where the active value is equal to 1.

```
SELECT * FROM siteMonitor WHERE active=1
```

After the SQL data is retrieved, it is passed to a while loop, which is responsible for grabbing
each row and building a line of XML defining the site information.

```
$result = mysql_query("SELECT * FROM siteMonitor WHERE
active=1");
$xml = "<?xml version=\"1.0\" ?>\n";
$xml .= "<sites>\n";
while($row = mysql_fetch_array($result))
{
  ...
}
$xml .= "</sites>";
```

The line of XML is built using the $row data, which is passed into the sprint() function. The
sprintf is used to automatically fill in the necessary XML attributes using the SQL row data.

```
$xml .= sprintf("\t<site name=\"%s\" uri=\"%s\" />\n",
$row['name'],
$row['uri']);
```

Now that the XML data is built, it is sent out to the browser and returned to Flash. This is done by
setting the content-type of the response to text/xml, which is the MIME type of XML. Then
the last step is to use a print statement to actually output the data.

```
header("Content-type: text/xml");
print $xml;
```