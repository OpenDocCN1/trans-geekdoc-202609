?>

See Section 3.6.1 and Appendix 19.4.6 of RFC 2616 for more information on chunked transfer encoding.

# ## Content Encoding

If the zlib extension is loaded (which can be checked using the extension_loaded function or executing `php -m` from command line), the client can optionally include an `Accept-Encoding` header with a value of `gzip, deflate` in its request. If the server supports content compression, it will include a `Content-Encoding` header in its response with a value indicating which of the two compression schemes it used on the response body before sending it.

The purpose of this is to reduce the amount of data being sent to reduce bandwidth consumption and increase throughput (assuming that compression and de-compression takes less time than data transfer, which is generally the case). Upon receiving the response, the client must decompress the response using the original scheme used by the server to compress it.

```
```php
<?php
// If Content-Encoding is gzip...
$decoded = gzinflate(substr($body, 10));

// If Content-Encoding is deflate...
$decoded = gzuncompress($body);
?>
```
```

+   - Yes, the function names are correct. One would think that `gzinflate` would be used to decode a body encoded using the `deflate` encoding scheme. Apparently this is just an oddity in the naming scheme used by the zlib library.

+   - When the encoding scheme is `gzip`, a GZIP header is included in the response. `gzinflate` does not respond well to this. Hence, the header (contained in the first 10 bytes of the body) is stripped before the body is passed to `gzinflate`.