```
// Check for errors
if (!$tempfile) {
    echo("<p>Unable to open temporary file ".
    "($tempfilename) for writing. Static page ".
    "update aborted!</p>");
    exit();
}

// Write the data for the static page into the
// temporary file
fwrite($tempfile, $htmlData);

// Close the temporary file, now that we're done
// writing to it.
fclose($tempfile);

// If we got this far, then the temporary file
// was successfully written, and we can now copy
// it on top of the static page.
$ok = copy($tempfilename, $targetfilename);

// Finally, delete the temporary file.
unlink($tempfilename);
```

```
?>
<p>Static page successfully updated!</p>
</body>
</html>
```

The above code only looks daunting because of the large comments I've included. Remove them, and you'll see it's actually a fairly simple script.

Now, whenever generateindex.php is executed (say, when a browser requests it), a fresh copy of index.html will be generated from index.php. If we move index.php and generateindex.php into a restricted-access directory, you can make sure that only site administrators have the ability to update the front page of your site in this way. Expand this script to generate all semi-dynamic pages on your site, and add an "update semi-dynamic pages" link to your content management system!

If you'd rather have your front page updated automatically, you'll need to set up your server to run generateindex.php at regular intervals (say, every hour). Under recent versions of Windows 9x, you can use the Task Scheduler (System Agent in older versions of Windows equipped with MS Plus Pack) to automatically run php.exe (a stand-alone version of PHP included with the Windows PHP distribution) every hour. Just create a batch file called generateindex.bat that contains this line of text:

```
C:\PHP\php.exe C:\www\generateindex.php
```