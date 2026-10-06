# Chapter 11: Working with Files and Directories

```
echo '<td>' . filesize($filepath) . '</td>';
echo '<td>' . date('M j, H:i:s', filetime($filepath)) . '</td>';
t</tr>;
)
```

To display each file in the table, the script wraps a link for the user to edit the file. The link's URL contains the query string "filename=" followed by the name of the file to edit. Notice that the filename is encoded in the query string, passing it through the urlencode() function. The script also displays the file's size by calling the filesize() function. Finally, the file's "last modified" time is displayed by calling the filetime() function and passing the resulting timestamp using the date() function to format it.

Find out about urlencode() in Chapter 10, and date() in Chapter 16.

Once the loop is finished, the function clears the directory and displays the form for creating a new file. The form includes a filename text field and a createFile button.

# The displayEditForm() Function

When the user clicks a file to edit, the displayEditForm() function is called to display the file contents for editing. It can take an optional $filename argument containing the filename of the file to edit; if this isnt passed, it looks up the filename in the query string, using basename() to ensure that no absolute path information is in the filename; this is a good security measure, because it thwarts any attempt to edit files outside the designated folder. Furthermore, if the filename is empty for some reason, the script exits with an error:

```
function displayEditForm($filename=" )
if (!$filename) $filename = basename($_GET["filename"]);
if (!$filename) die("Invalid filename");
```

The next function stores the full path to the file in a $filepath variable (because this path is needed many times in the function), and checks to make sure the file to edit exists — if it doesn't, it exits with a "File not found"

```
$filepath = PATH_TO_FILES . "./$filename";nif (!file_exists($filepath)) die("File not found ");
```

The rest of the function calls displayPageHeader() to output the standard page header markup, displays the name of the file being edited, as well as the HTML form for editing the file. The form consists of a hidden field storing the filename of the file being edited; a text area for the file contents; Save File and Cancel buttons. The file's contents are displayed in the text area by calling file_get_contents() and outputting the result.