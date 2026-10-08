# ## Redirection and Referers

Intuitively, the `redirect` request option is used to set the maximum number of redi-rections to process before automatically terminating. Not so intuitively, it defaults to 0, which means that processing of redirections is disabled and you must explicitly set this request option to a value greater than 0 to enable it.

The `referer` request option can be used to set the value of the Referer request header. Alternatively, it can be set via the `headers` request option (more on that shortly) when using the procedural API or the setHeaders and addHeaders methods of the HttpRequest class when using the object-oriented API.

# ## Content Caching

The `lastmodified` request option accepts a UNIX timestamp to be used as the value for the If-Modified-Since or If-Unmodified-Since request header.

Likewise, the `etag` request option accepts a string to be used as the value for the If-Match or If-None-Match request header.

# ## User Agents

The `useragent` request option can be used to set a custom user agent string for the request.

# ## Byte Ranges

Like cURL, pecl_http includes request options for a single resume point and multiple byte ranges. The former is `resume` and accepts an integer for the starting point. The latter is `range` and is formatted as an array of enumerated arrays each containing a pair of integers representing a single byte range. What follows is an example of setting byte ranges within a request options array.

```
```php
<?php
$opts = array(
    'range' => array(
```