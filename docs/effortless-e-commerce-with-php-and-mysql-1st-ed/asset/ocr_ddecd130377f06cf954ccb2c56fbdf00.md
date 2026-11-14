# 9. Validate the file's type:

```
$allowed_mime = array('image/gif', 'image/pjpeg', 'image/jpeg',
    'image/JPG', 'image/X-PNG', 'image/PNG', 'image/png',
    'image/x-png');
$allowed_extensions = array ('.jpg', '.gif', '.png', 'jpeg');
$image_info = getimagesize($file['tmp_name']));$ext = substr($file['name'], -4);
if ( (!in_array($file['type'], $allowed_mime))
  || (!in_array($image_info['mime'], $allowed_mime) )
  || (!in_array($ext, $allowed_extensions) )
) {
    $add_product_errors['image'] = 'The uploaded file was not of the
    proper type.';
}
```

Again, this is similar to the process for uploading PDFs. First, an array of allowed MIME types is defined. Then an array of allowed extensions is defined. Third, the getimagesize() function is invoked, which can be used as a good server-based confirmation of an image’s properties. Fourth, the last four characters in the uploaded file’s name are retrieved, in order to be compared against the allowed extensions.

The code then creates an error if any of three conditions are false. The first is that the browser-supplied MIME type is appropriate. The second is that the server-supplied MIME type (from the getimagesize() function call) is acceptable. The third is that the file’s extension is on the approved list.

# 10. Move the file to its final destination:

```
if (array_key_exists('image', $add_product_errors)) {
    $new_name = (string) sha1($file['name'] . uniqid('', true));
    $new_name .= ((substr($ext, 0, 1) != '.' ? '.' : '{$ext}"; : $ext);
    $dest = "./../products/$new_name";
    if (move_uploaded_file($file['tmp_name'], $dest)) {
        $SESSION['image']['new_name'] = $new_name;
        $SESSION['image']['file_name'] = $file['name}';
        echo '<h4>The file has been uploaded!</h4>';
    } else {
        trigger_error('The file could not be moved.');
        unlink($file['tmp_name']);
    }
} // End of array_key_exists() IF.
```