First we should see if we can open the file to manipulate the counter:

```
if (!$filePointer = fopen($fileName, "r+")) {
echo("Error opening file $fileName\n");
exit;
}
```

Next, we get the number of hits from the log file:

```
if (!$hits = fread($filePointer, filesize($fileName))) {
echo("Error reading hits from $fileName\n");
exit;
}
//Increment the number of hits
$hits++;
//Rewind the file for a clean write
if (rewind($filePointer) == 0) {
echo("Couldn't rewind file");
exit;
}
```

Write the updated number of hits to the file, if that file is not being written to already. We use flock() to make sure that no other processes are using the file at the same time, ensuring accuracy:

```
if (flock($filePointer, 2)) {
if (!fwrite($filePointer, $hits, strlen($hits))) {
echo("Couldn't write updated hits to $fileName");
exit;
}
}
flock($filePointer, 3);
```

Now we generate the image the function described below:

```
$image = makeImage($hits);
```

Finally, we create the  tag for the calling page, and make it friendly for non-graphical browsers:

```
$counter = "<img src=\"$image\" alt=\"Hits: $hits\">";
return $counter;
}
```

Now, we need to make a function that will create our dynamic image and return the path to it:

```
function makeImage($number)
{
```