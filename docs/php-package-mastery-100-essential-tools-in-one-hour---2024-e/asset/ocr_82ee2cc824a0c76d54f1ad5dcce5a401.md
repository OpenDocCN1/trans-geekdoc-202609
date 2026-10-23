# Chapter 3 external library

# 1. Guzzle

Guzzle is a PHP HTTP client that makes it easy to send HTTP requests and trivial to integrate with web services.

Ex:Guzzle

```
require 'vendor/autoload.php';
$client = new \GuzzleHttp\Client();
$response = $client->request('GET',
'https://api.github.com/repos/guzzle/guzzle');
echo $response->getStatusCode(); // HTTP status code
echo $response->getBody(); // Body of the response
```

200

// The actual JSON response from GitHub about the Guzzle repository will be displayed here.