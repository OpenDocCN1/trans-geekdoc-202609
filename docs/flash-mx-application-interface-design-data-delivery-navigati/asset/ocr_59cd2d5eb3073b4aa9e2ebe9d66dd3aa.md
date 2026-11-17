This next function is the core functionality center of the FileInfoComponent. This function, called handleFile, is responsible for performing the appropriate action associated with each type of file when it is double-clicked. In essence, this decides how to activate, or handle, the file when the user chooses to activate it.

```
FileInfoClass.prototype.handleFile =
    function()
{
    stopDrag();
    if (this.picFrame == 1)
    {
        _root.parentdir[_root.dirlevel++] =
            _root.matchDir;
        _root.matchDir += this.fileName add
            "/";
        _root.loader2.load(_root.baseURL add
            "dirstuff.php?matchExt=" add
            _root.matchExt add "&matchDir="
            add _root.matchDir);
    }
    else
    {
        var tname = this.fileName.toUpperCase();
        if (tname.indexOf(".JPG") > -1)
        {
            _root.viewwindow.visible = true;
            var destfile = this.filePath add
                this.fileName;
            _root.viewwindow.blankmc.
                createEmptyMovieClip("holdermc", 0);
            _root.viewwindow.blankmc.holdermc.
                _y = 14;
            _root.viewwindow.blankmc.holdermc.
                loadMovie(destfile);
            _root.viewwindow.destfile =
                destfile;
            _root.viewwindow.jpgtitle.text =
                this.filename;
            _root.busy = true;
        }
        else if (tname.indexOf(".TXT") > -1)
        {
            txt = new XML();
            txt.onData = function(dat)
            {
```

```
_root.textfilecontentmc.
    textfilecontent.text = dat;
_root.textfilecontentmc._visible =
    true;
_root.busy = true;
}
var destfile = this.filePath add
    this.fileName;
_root.textfilecontentmc.destfile =
    destfile;
txt.load(destfile);
}
else if (tname.indexOf(".MP3") > -1)
{
    _root.mp3player._visible = true;
    var destfile = this.filePath add
        this.fileName;
    _root.mp3player.streamSound
        (destfile);
}
else
{
    var destfile = this.filePath add
        this.fileName;
    getURL (destfile, "_blank");
}
}
```

This function looks at the type of file associated with this FileInfoComponent instance, and then responds to it accordingly.

The first type it looks for is a folder. If an instance is set to be a folder, then it’s handled by forcing the entire window to be redrawn, with the new path. First, we check to see that the file type is a folder.

If it is, then we specify the new path by adding / and this.fileName onto the current path, which is stored in the variable _root.matchDir. We also store the name of the previous path (where we are moving from) in an array called _root.parentdir. As we navigate deeper, we need to always know the name of the previous path. So, we add it into this array, and then incrementing a counter called _root.dirlevel. This way, we’re keeping a history of previous locations.