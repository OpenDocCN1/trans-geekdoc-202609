Using the parameters just extracted, we make sure that the image is in an acceptable format, figure out what its suffix should be, and ensure that it is not too large:

```
/* Validate type. */
if (!file_types[$ufile_type]) {
    die("image must be in JPEG, GIF, or PNG format.");
} else {
    $file_suffix = $file_types[$ufile_type];
}
/* Validate size. */
if ($width > $max_width || $height > $max_height) {
    die("size $width x $height exceeds maximum $max_width x $max_height.");
}
```

Every now and then, someone uploads a file with an incorrect suffix. This isn't really that big of a deal, but it does mess up the MIME type when the server sends it. Because we now know the correct suffix, we coerce that suffix by chopping off any possible incorrect suffix and adding our own. Someone may also mistype a suffix, and this step also corrects that by simply tacking on the correct suffix. For example, foo.jpg might become foo.jpg.jpg. Although you also could try to correct for that, you would find yourself second-guessing users who really ought to learn how to type. After determining this final name for the uploaded file, we assign its full pathname to $new_fullpath:

```
/* Force file suffix. */
$newname = preg_replace('/\.(jpe?g|gif|png)$/i', "");
$newname .= $file_suffix;
$new_fullpath = "$root/$location/$newname";
```

Now that we have the final name, we can verify that the file does not already exist when set to no-overwrite mode:

```
if ((!$overwrite_images) && file_exists($new_fullpath)) {
    die("file exists; will not overwrite.");
}
```

Now it's time to copy the file into its final location and make sure the copy was successful:

```
/* Copy the file into final location. */
if (!copy($ufile, $new_fullpath)) {
    die("copy failed.");
}
```