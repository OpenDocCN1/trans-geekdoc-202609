At this point, cURL accesses the page and returns the page data, which PHP assigns to $page_data. Finally, clean up after the connection with curl_close():

```
curl_close($c);
```

This is a good start; you can now access web data via the GET method.
But what if you need to use the POST method to submit form data? In this
case, you need to set more options with curl_setopt(). Let’s build a function
called retrieve_page() that can access pages with the GET or POST methods.

The function takes two arguments: a URL to access and an optional
array of POST parameters (the array has parameter names as keys and
the parameter values as its values). If it doesn’t receive this second argument,
the function uses the GET method. The first part of the function builds a query
string from the parameter array in the form param1=value1&param2=value2[...],
much like it would appear in a GET query, except that it does not include
the leading question mark. Fortunately, PHP has a built in http_build_query()
function to create a query string from an array, so all we really need to do is
verify the parameter array:

```
function retrieve_page($url, $post_parameters = null) {
/* Connects to a site using POST or GET; fetches data */
$query_string = null;
if (!is_null($post_parameters)) {
    if (!is_array($post_parameters)) {
        die("POST parameters not in array format");
    }
    /* Build query string. */
    $query_string = http_build_query($post_parameters);
}
```

Now it’s time to set up the cURL connection handle. If there is a query
string at this point, we know that we’re using the POST method, so we
configure the connection in that manner and use the query string as the
POST data:

```
$ch = curl_init();
if ($query_string) {
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $query_string);
}
```

From this point on, we configure the connection as we did before,
execute the query, and return the data:

```
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HEADER, false);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$return_data = curl_exec($ch);
curl_close($ch);
```