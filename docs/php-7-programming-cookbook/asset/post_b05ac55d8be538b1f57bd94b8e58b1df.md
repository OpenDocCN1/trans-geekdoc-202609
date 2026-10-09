
## 15. As the name implies, delete() removes a customer entry:

```php
public function delete(Request $request, Response $response)
{
    $id = $request->getDataByKey(self::ID_FIELD) ?? 0;
    $cust = $this->service->fetchById($id);
    if ($cust && $this->service->remove($cust)) {
        $response->setData(['success' => self::SUCCESS_DELETE,
                          'id' => $id]);
        $response->setStatus(Request::STATUS_200);
    } else {
        $response->setData([self::ERROR_NOT_FOUND]);
        $response->setStatus(Request::STATUS_500);
    }
}
```

## 16. Finally, we define authenticate() to provide, in this example, a low-level mechanism to protect API usage:

```php
public function authenticate(Request $request)
{
    $authToken = $request->getDataByKey(self::TOKEN_FIELD)
        ?? FALSE;
    if (in_array($authToken, $this->registeredKeys, TRUE)) {
        return TRUE;
    } else {
        return FALSE;
    }
}
```

### How it works...

Define the following classes, which were discussed in the previous recipe:

- Application\Web\AbstractHttp
- Application\Web\Request
- Application\Web\Response

You can then define the following classes, described in this recipe, summarized in this table:

| Class | Discussed in these steps |
| :--- | :--- |
| Application\Web\Response | 2 |
| Application\Web\Rest\Server | 3 - 8 |
| Application\Web\Rest\AbstractApi | 9 |
| Application\Web\Rest\ApiInterface | 10 |
| Application\Web\Rest\CustomerApi | 11 - 16 |

You are now free to develop your own API class. If you choose to follow the illustration `Application\Web\Rest\CustomerApi`, however, you will need to also be sure to implement these classes, covered in Chapter 5, *Interacting with a Database*:

- Application\Entity\Customer
- Application\Database\Connection
- Application\Database\CustomerService

You can now define a `chap_07_simple_rest_server.php` script that invokes the REST server:

```php
<?php
$dbParams = include __DIR__ . '/../../config/db.config.php';
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Web\Rest\Server;
use Application\Web\Rest\CustomerApi;
$apiKey = include __DIR__ . '/api_key.php';
$server = new Server(new CustomerApi($apiKey), $dbParams, 'id');
$server->listen();
```

You can then use the built-in PHP 7 development server to listen on port `8080` for REST requests:

```
php -S localhost:8080 chap_07_simple_rest_server.php
```

### Accessing Web Services

To test your API, use the `Application\Web\Rest\AbstractApi::generateToken()` method to generate an authentication token that you can place in an `api_key.php` file, something like this:

```php
<?php return '79e9b5211bbf2458a4085707ea378129';
```

You can then use a generic API client (such as the one described in the previous recipe), or a browser plugin such as RESTClient by Chao Zhou (see `http://restclient.net/` for more information) to generate sample requests. Make sure you include the token for your request, otherwise the API as defined will reject the request.

Here is an example of a POST request for `ID 1`, which sets the `balance` field to a value of `888888`:

![](img/39390f6d56c5a83b28db083a8bd5185c_268_0.png)

### There's more...

There are a number of libraries that help you implement a REST server. One of my favorites is an example implementing a REST server in a single file: `https://www.leaseweb.com/labs/2015/10/creating-a-simple-rest-api-in-php/`

Various frameworks, such as CodeIgniter and Zend Framework, also have REST server implementations.

### How to do it...

Using SOAP, in contrast to the process of implementing a REST client or server, is quite easy as there is a PHP SOAP extension that provides both capabilities.

![](img/39390f6d56c5a83b28db083a8bd5185c_269_0.png)

> A frequently asked question is "what is the difference between SOAP and REST?" SOAP uses XML internally as its data format. SOAP uses HTTP but only for transport, and otherwise has no awareness of other HTTP methods. REST directly operates HTTP, and can use anything for data formats, but JSON is preferred. Another key difference is that SOAP can operate in conjunction with a WSDL, which makes the service self-describing, thus more publicly available. Thus, SOAP services are often offered by public institutions such as national health organizations.

For this example, we will make a SOAP request for an existing SOAP service offered by the United States National Weather service:

1. The first consideration is to identify the **WSDL** document. The WSDL is an XML document that describes the service:

   ```php
   $wsdl = 'http://graphical.weather.gov/xml/SOAP_server/'
           . 'ndfdXMLserver.php?wsdl';
   ```

2. Next, we create a *soap* client instance using the WSDL:

   ```php
   $soap = new SoapClient($wsdl, array('trace' => TRUE));
   ```

3. We are then free to initialize some variables in anticipation of a weather forecast request:

   ```php
   $units = 'm';
   $params = '';
   $numDays = 7;
   $weather = '';
   $format = '24 hourly';
   $startTime = new DateTime();
   ```

4. We can then make a `LatLonListCityNames()` SOAP request, identified as an operation in the WSDL, for a list of cities supported by the service. The request is returned in XML format, which suggests creating a `SimpleXMLElement` instance:

   ```php
   $xml = new SimpleXMLElement($soap->LatLonListCityNames());
   ```

5. Unfortunately, the list of cities and their corresponding latitude and longitude are in separate XML nodes. Accordingly, we use the `array_combine()` PHP function to create an associative array where latitude/longitude is the key, and the city name is the value. We can then later use this to present an HTML SELECT drop-down list, using `asort()` to alphabetize the list:

   ```php
   $cityNames = explode('|', $xml->cityNameList);
   $latLonCity = explode(' ', $xml->latLonList);
   $cityLatLon = array_combine($latLonCity, $cityNames);
   asort($cityLatLon);
   ```

6. We can then get city data from a web request as follows:

   ```php
   $currentLatLon = (isset($_GET['city']) ? strip_tags(
     urldecode($_GET['city'])) : '' ;
   ```

7. The SOAP call we wish to make is `NDFDgenByDay()`. We can determine the nature of the parameters supplied to the SOAP server by examining the WSDL:

   ```xml
   <message name="NDFPDgenByDayRequest">
     <part name="latitude" type="xsd:decimal"/>
     <part name="longitude" type="xsd:decimal"/>
     <part name="startDate" type="xsd:date"/>
     <part name="numDays" type="xsd:integer"/>
     <part name="Unit" type="xsd:string"/>
     <part name="format" type="xsd:string"/>
   </message>
   ```

8. If the value of `$currentLatLon` is set, we can process the request. We wrap the request in a `try {} catch {}` block in case any exceptions are thrown:

   ```php
   if ($currentLatLon) {
     list($lat, $lon) = explode(',', $currentLatLon);
     try {
       $weather = $soap->NDFDgenByDay($lat, $lon,
         $startTime->format('Y-m-d'), $numDays, $unit, $format);
     } catch (Exception $e) {
       $weather = PHP_EOL;
       $weather .= 'Latitude: ' . $lat . ' | Longitude: ' . $lon;
       $weather .= 'ERROR' . PHP_EOL;
       $weather = $e->getMessage() . PHP_EOL;
       $weather .= $soap->__getLastResponse() . PHP_EOL;
     }
   }
   ```

### How it works...

Copy all the preceding code into a `chap_07_simple_soap_client_weather_service.php` file. You can then add view logic that displays a form with the list of cities, as well as the results:

```html
<form method="get" name="forecast">
<br> City List:
<select name="city">
<?php foreach ($cityLatLon as $latLon => $city) : ?>
<?php $select = ($currentLatLon == $latLon) ? ' selected' : '' ?>
<option value="<? echo urlencode($latLon) ?>" <? echo $select ?>>
<? echo $city ?>
</option>
<?php endforeach; ?>
</select>
<br><input type="submit" value="OK"><br>
</form>
<pre>
<?php var_dump($weather); ?>
</pre>
```

Here is the result, in a browser, of requesting the weather forecast for Cleveland, Ohio:

![](img/39390f6d56c5a83b28db083a8bd5185c_271_0.png)
