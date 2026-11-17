
The filetypes that this version has icons for are GIF, JPEG, MP3, PHP, HTML, XML, TXT, ZIP, FLA, SWF, AS (ActionScript file), and directory, which uses an icon of a folder. Any other file type uses a generic unknown icon.

The main magic comes from the code that's attached to the Actions layer. Once we have our directory read, and all our FileInfoComponents placed, it's up to each instance to handle its own behaviors. Let's look at the functionality of the FileInfoComponent itself, and then in the next section, we'll look at how it's all put together, and how all the instances are created from the directory information returned by the PHP script.

## The FileInfoComponent actions

All the code in this section comes from the Actions layer in the FileInfoComponent component itself. Since we're creating a component, we need to define a base class that will handle all the methods and properties associated with each instance. We're going to tie this class to the physical FileInfoComponent movie clip, to ultimately create FFileInfoComponent – notice the extra F at the beginning to denote our entire component, rather than the instance.

The code begins like so:

```
#initclip
function FileInfoClass ()
{
    this.autoparse();
    this.update();
    this.amSelected = false;
    this.selectedBox._visible = false;
    this.doubleclickspeed = 300;
}
```

This is the constructor function, which is also used to define the name of the class that we're tying to our movie clip. In this case, the class is called FileInfoClass. Think of it like creating a new base object, like String, Array, or Math – this class is FileInfoClass. We're using the #initclip action to specify that we only want this definition code to be run once, when the component itself is first loaded in the library, and not every time an instance is created.

We'll see later that when each instance of the FileInfoComponent is created, several variables are passed into it. These are:

- xpos – the x position of the instance.
- ypos – the y position of the instance.
- filename – the actual name of the file, for example picture.jpg, mysong.mp3.
- filePath – the absolute path of the file, for example http://www.mysite.com/files/mysong.mp3
- fileSize – the size of the file in bytes.

Since these variables are passed in when the instance itself is created, the variables therefore exist when the constructor function is called. There is also one more variable, picFrame, which is assigned by default when the instance is created. In fact, if we look at the library again, right click on the FileInfoComponent and choose Component Definition, we can see that four variables are defined by default.

The variables filename, filePath, picFrame and fileSize are set to default.txt, /, 1 and 0 respectively. However, these will not normally be used, as they're overwritten in the attachMovie code that is used to create each instance. We'll look more at this in the next section.

So, when an instance of the FileInfoComponent is created, there are several initialization steps that we must perform, as we saw in the constructor function.

First, we're calling an internal method called autoparse. This is responsible for analyzing the associated filename, and then setting the value of the picFrame parameter to the correct frame of the fileInfoIcon movie clip.

Once we've got a value for picFrame, we call update. This is a short function, and it simply tells the fileInfoIcon to gotoAndStop at picFrame. This function also tells the instance to set its _x and _y parameters to the xpos and ypos that were set upon initialization. This will physically move the instance on screen. Finally, update sets the value of the label to be the filename, stored in the fileName variable.

When a FileInfoComponent instance is clicked on, it becomes the selected file. We have a flag attached to each instance called amSelected. Here, we're setting it to false, indicating that it's not selected. This code will make more sense shortly. Next, we're setting the visibility of the selectedBox to false, and setting the parameter doubleclickspeed to 300. The selectedBox is used to indicate which file is currently selected, and the doubleclickspeed is used to indicate the maximum amount of time allowed for the second click to follow after the first click, in order for it to be considered a successful double-click.

The next line of code, after the constructor function, is this:

```
FileInfoClass.prototype = new MovieClip();
```

This is necessary in order for the class to inherit all the events of the MovieClip object. Without doing this, there'd be no tie between our class, and events like onMouseDown, and onMouseMove.

Next, we have the autoparse function:

```
FileInfoClass.prototype.autoparse = function ()
{
    this.fTypes = new Object();
    this.fTypes["BAK"] = 10;
    this.fTypes["JPG"] = 2;
    this.fTypes["JPEG"] = 2;
    this.fTypes["GIF"] = 2;
    this.fTypes["HTM"] = 3;
    this.fTypes["HTML"] = 3;
    this.fTypes["XML"] = 3;
    this.fTypes["TXT"] = 4;
    this.fTypes["PHP"] = 5;
    this.fTypes["SWF"] = 6;
    this.fTypes["AS"] = 6;
    this.fTypes["FLA"] = 7;
    this.fTypes["MP3"] = 8;
    this.fTypes["ZIP"] = 9;
    this.fTypes["FOLDER"] = 1;

    var tExt = this.fileName.toUpperCase().
    split(".")[1];
    if (tExt == undefined &&
    (this.filesize % 512) == 0) tExt = "FOLDER";

    this.picFrame = this.fTypes[tExt];

    if (isNaN(this.picFrame) ||
    this.picFrame == undefined)
    this.picFrame = 10;
}
```

This function creates an object called fTypes with several properties. Each property is actually a file extension (for example GIF, HTML, ZIP, MP3) and each one has a value that corresponds to a frame in the fileInfoIcon movie clip. (Note that I have included BAK for future compatibility – we may later decide to include a BAK icon). What we do here is set tExt to be the uppercase extension of the filename attached to this instance.

If the file has no extension, and its file size is an even division of 512, then it is most likely a folder. (This is to do with the way folders are stored...they're not files, so they need only a fixed amount of room. In cases like this, they're usually rounded up to the closest number that's a power of 2, such as 128, 256, 512, so that the storage takes up a whole even number of bytes.) In that case, we set the extension to FOLDER, so that we have something to compare with in the fTypes object.

We're then setting the picFrame property based on the extension with:

```
this.picFrame = this.fTypes[tExt];
```

In the case where there's no matching extension, we set the picFrame to 10, because that's the general image we use for an unknown file type.

Next comes the other function we mentioned earlier, update:

```
FileInfoClass.prototype.update = function () {
this.fileInfoIcon.gotoAndStop(this.picFrame);
this._x = this.xpos;
this._y = this.ypos;
this.label.text = this.fileName;
}
```

The update function, as discussed before, simply tells the fileInfoIcon to gotoAndStop(this.picFrame), sets the _x and _y position of the component, and sets the label to this.fileName.

These functions are only ever declared once, because of the #initclip action, and therefore, all our functions are declared on the prototype object of the FileInfoClass class, hence the FileInfoClass.prototype before each function name.

The next line of code, after this, is:

```
Object.registerClass("FFileInfoComponent",
FileInfoClass);
```

This is where we tie our new class, FileInfoClass, to the actual component movie clip from the library. In the library, our component is configured to export with the linkage ID FFileInfoComponent. Here, we're tying the class and the movie clip together, by using the registerClass method of the Object object. This is an important line of code. Without this, none of our instances would be alive – their code would not work. They would merely be static movie clips.

Next, we have two functions, doSelect and doDeselect. As you might have guessed, these are responsible for setting the state of this instance to appear selected, or to remove this state by deselecting it:

```
FileInfoClass.prototype.doSelect =
function ()
{
this.amSelected = true;
this.selectedBox._visible = true;
_root.titleBar.fileSize.text =
(this.fileSize) add " bytes";
}
```

```
FileInfoClass.prototype.doDeselect =
function ()
{
this.amSelected = false;
this.selectedBox._visible = false;
}
```
