NOTE Ideally, you want to replace YahooDemo with your Yahoo!-supplied application ID, although you can leave it as is if you don't plan to use this application in production or repeatedly.

After this code runs, $page contains the following XML result:

```
<?xml version="1.0"?>
<ResultSet xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="urn:yahoo:maps" xmlns:maps="http://api.local.yahoo.com/MapsService/V1/GeoCodeResponse.xsd">
<Result precision="address">
<Latitude>38.898563</Latitude>
<Longitude>-77.037223</Longitude>
<Address>1600 PENNSYLVANIA AVE NW</Address>
<City>WASHINGTON</City>
<State>DC</State>
<Zip>20006</Zip>
<Country>US</Country>
</Result>
</ResultSet>
```

So, to extract the latitude and longitude of the address, use the following PHP code:

```
$data = new SimpleXMLElement($page);
$lat1 = $data->Result->Latitude[0];
$lon1 = $data->Result->Longitude[0];
```

If all you wanted were the latitude and longitude of an address, you've now successfully used the web service. But let's do something a little more fun. First, assume that the script is called mapdemo.php, run from the following form:

```
<form action="mapdemo.php">
Street: <input type="text" name="street" /><br />
City: <input type="text" name="city" /><br />
State: <input type="text" name="state" /><br />
<input type="submit" /><br />
</form>
```

Add the following to mapdemo.php in order to extract a second geolocation from the arbitrary address entered in the preceding form:

```
$qs = http_build_query(array(
	"appid" => "YahooDemo",
	"street" => $_REQUEST["street"],
	"city" => $_REQUEST["city"],
	"state" => $_REQUEST["state"],
	));
```