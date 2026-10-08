```
$data = array(
        'param1' => 'value1',
        'param2' => 'value2',
        'file1' => '@/path/to/file',
        'file2' => '@/path/to/other/file'
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://localhost.example/process');
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
?>
```

Here are the differences between this example and the previous one.

+   - The URL is passed using the curl_setopt function this time, just to show how to do it without passing it to the curl_init function. This is important when reusing cURL session handles with different URLs.

+   - CURLOPT_POST is set to true to change the request method to POST.

+   - CURLOPT_POSTFIELDS is an associative array or preformatted query string to be used as the data for the request body. Files can be uploaded by specifying a value where the first character is @ and the remainder of the value is a filesystem path to the file intended for upload.

Here are a few other cURL configuration setting constants related to the request method.

+   - CURLOPT_HTTPGET: Boolean that, when set to true, explicitly resets the request method to GET if it’s been changed from the default.

+   - CURLOPT_NOBODY: Boolean that, when set to true, excludes the body from the response by changing the request method to HEAD.