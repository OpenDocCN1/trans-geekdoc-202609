Jane also checks out version 1.2 and amends it to read as follows:

```
1: <\?
2:   $strTime = time("Y-m-d");
3:   $strToPrint = "Goodbye World, it's $strDate";
4: \?>
5: <html>
6:   <body>
7:     <?php echo $strToPrint; ?>
8:     <br />\<br />
9:     <hr />
10:   </body>
11: </html>
```

The first check-in (whoever gets there first) will cause a version 1.3 to be created. Can you anticipate what will happen when the slower of the two developers checks his or her code in? A new line has been inserted in each case and an existing line modified. Although the version-control platform may well be able to combine the two new lines (by simply incorporating both), it will not know how to combine the changes made to the single line (line 3 in both cases). As PHP developers, you can see the resolution that is required — it's common sense:

```
3: $strToPrint = "Goodbye World, it's $strTime on $strDate";
```

The version-control platform, however, isn't quite as clever as the humans in question, so it raises an error informing the user of the conflict. It is then up to the developer whose most recent check-in attempt has caused the conflict to resolve it. In practice, the version-control system will create a temporary new version, 1.4, which contains details of the conflict. This temporary version will not be issued until the conflict is resolved and that version is made live. The last developer to check in the file will be notified of the conflict by the version-control platform, and invited to edit the temporary version to resolve the conflict. It is the responsibility of the latter of the two developers checking in to resolve the conflict, because the version-control platform views that developer as having caused the conflict.

The temporary version 1.4 created by the repository might look something like this:

```
1: <\?
2:   $strTime = time("Y-m-d");
<<<<<<< helloworld.php
3:   $strToPrint = "Goodbye World, it's $strTime";
=======
3:   $strToPrint = "Goodbye World, it's $strDate";
>>>>>>> 1.3
4: \?>
5: <html>
6:   <body>
7:     <?php echo $strToPrint; ?>
8:     <br />\<br />
9:     <hr />
10:   </body>
11: </html>
```

You can see the markup that the version-control platform has introduced to show the two different alternatives for line 3.