# # Displaying the contents of a file

Our project management application needs to be able to display the files it's managing, which it does with the contents of displayfile.php, in which a named file is retrieved from the database:

```
$f = new File;
$f->build($_REQUEST);
$f->fetch_from_db();
if ($f->file)
{
    $f->display();
}
elseif ($f->fullpath)
{
    virtual($f->fullpath);
}
else
{
    print."<li>Duh, like what do I do now?\n";
}
unset($f);
```

That code segment, in turn, calls the display() function in the File class, defined in file.class.php. This function is a simple one:

```
function display()
{
    header('Content-type: '.$this->mimetype);
    echo gzinflate($this->file);
}
```

display() simply undoes the gzdeflate() function invoked at storage time and decompresses it after storage.

# ## Summary

In this chapter we designed and built an application that manages projects, files, users, deadlines, and notes by storing everything in a database and presenting a coherent, useful user interface.

This exercise enabled you to explore the way PHP manages sessions persistently and to see how it goes about stuffing files from a file system into a database. You also got a further look at object orientation in PHP and ended up with both a library of reusable functions and a simple project management application.