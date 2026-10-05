# StoreLocator (FMS11v2 - Testing Server)

# PHP Store Locator using Google GeoCoding

Instructions

| Name | Aardwork Pizza & Sub |
| Address | 306A Caribou St |
| City | Banff |
| State | AB |
| Marker/Title | Aardwork Pizza & Sub |
| Marker/Description | Dine and Dish Magazine call it the best pizza |
| Lat | 51.766996 |
| Lon | -115.50362 |
| Search | |
| Search | |
| Distance | 621.8 |
| RecordID | 40 |

Figure 7-109: Use the sample records to find restaurants within the specified distance.

The math for the Distance calculation involves some fairly nasty Trigonometry. Since a math lesson isn't of this lesson I'll investigate the math on your own, knowing that you can use the calculation as is and will work correctly. The only thing I will say about the Distance calculation is that it calculates the distance in miles. If it is in kilometers, you can change the constant in the calculation from 3959 to 6371.

The general steps in the process are as follows: the user submits the form with their current address or zip code and the distance. Next, the PHP class converts the address or zip code to Latitude and Longitude values. The more specific your address, the more accurate the lat/lon values. Hopefully that's obvious. These values, along with the user's requested distance, are submitted to the Store Locator in the database. The script inserts these values into the SearchLat, SearchLon, and Distance fields to acquire a found set of records. The records are then sorted by the distance, returned to the web page, and finally displayed to the user with a map and for each record.

There are two main processes to make this solution work. First is the PHP page. Second is the Store Locator script. It is more efficient to describe each one separately, so we'll start with the MapMarkers.php page away by connecting to the database.

```
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', StoreLocator);\n$fm->setProperty('hostspec', 'http://127.0.0.1');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
```