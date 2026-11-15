Consider the following complete listing.

```
<?php
class htmlspecialchars_filter extends php_user_filter {
    function filter($in, $out, &$consumed, $closing): int
    {
        while ($bucket = stream_bucket_make_writeable($in)) {
            $bucket->data = htmlspecialchars($bucket->data);
            $consumed += $bucket->datalen;
            stream_bucket_append($out, $bucket);
        }
        return PSFS_PASS_ON;
    }
}
stream_filter_register(
    "string.htmlspecial",
    "htmlspecialchars_filter"
);
echo "<h1>Filter</h1><pre>";
echo htmlspecialchars(print_r(stream_get_filters(), true));
echo "</pre><h1>Result</h1><pre>";
echo file_get_contents(
    "php://filter/read=string.toupper|string.htmlspecial/resource=test.txt"
);
echo "</pre>";
?>
```

# Listing 26.6 The Custom Filter in Use ("filter-2.php")

> **Note**
> 
> With `stream_filter_append()`, you can also append a filter to a stream using a function—with `stream_filter_prepend()`, even to the beginning of the filter list.

# 26.2.4 Compression Streams

The last stream types that we will present deal with compressed data. The two supported file formats are the same as those in which the PHP source code is currently published: gzip and bzip2. There are separate functions in PHP for both archiving methods, but when using streams you have standardized access.

Writing data works very simply—as usual, with the file functions of PHP. The following script opens (again) the `test.txt` file and saves it in GZ and BZ2 format.