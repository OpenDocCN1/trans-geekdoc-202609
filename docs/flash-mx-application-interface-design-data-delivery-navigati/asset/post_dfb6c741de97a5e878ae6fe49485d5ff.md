
However, if an image is already in cache – say another browser window has it open – then the image will load in. With this in mind, a JavaScript pop-up solution would work fine, that is, if you like windows popping up everywhere...

As you can guess, this all makes for a pretty ugly situation. If you are testing the SWF in a browser, don't hold your breath for a second image.

A known way to get around this caching is to send a query string with a random number to a server-side script, preventing IE from caching it explicitly.

## How it works

After all that evil, let's assess the functionality of the tool. The load JPG tool works by opening a dialog box, which requests the URL or location of a JPG image file. This location can be relative to the SWF's position, or absolute, with web prefixes.

![](img/50202c17d5022233f3e3ec60560e35aa_209_0.png)

If you are testing the SWF offline, just stick a JPG in the same folder as the SWF and call that in. It will save a bit of typing and downloading.

Once the GO button has been clicked, the image is fetched (if it exists) and the percentage loaded is displayed and updated.

When the image has fully loaded, the dialog disappears and the image is resized to 200 x 200 pixels, and positioned at the center of the t-shirt, regardless of its original size. The JPG scale tool was included to allow the user to resize the image.

The code is made up of two primary functions – funcLoadJPG and loadImage. The former performs all the graphic and progress duties, whilst the loadImage function does the loading and completion tasks.

There is quite a lot of code here, but nothing that we can't handle.

First of all, we declare the function and call up the dialog box:

```
funcLoadJPG = function () {
  _root.attachMovie("loadJPGBox",
    "loadJPGBox", 111111);
  _root.loadJPGBox._x = (Stage.width/2);
  _root.loadJPGBox._y = (Stage.height/2);
  Selection.setFocus
  ("_root.loadJPGBox.urlText");
}
```

loadJPGBox is pulled in from the Library and given the same name on the stage. It is then positioned on the screen.

The next line gives the urlText input field of the dialog box the text cursor's focus, using the Selection object. This object is pretty useful for any input situation, where normally the user would have to select a text box to proceed. This gives a degree of automation, and allows immediate typing from the user.

This next bit of code sets up the initial code for the GO button of the dialog box:

```
_root.loadJPGBox.goBut.onRelease = function() {
  JPG.unloadMovie();
  _root.loadImage(_root.loadJPGBox.urlText.text);
  _root.loadJPGBox.loadJPGBoxText.text = "Please
  wait... loading JPG\rIf nothing
  happens for a long time,\rplease
  hit Cancel and try another image";
  _root.loadJPGBox.goBut._visible =
  false;
}
```

The first thing that happens is that JPG is cleared. JPG is defined a little later, but is basically the container for our loadMovie calls. The next line calls the loadImage function – defined in a moment – sending the input of the dialog text box.

After this we set the text of the dialog box, informing the user of the current status. By the way, if you've ever wondered what the \r is here, it is basically a line break, the equivalent of <br> in HTML or \n in numerous other scripting languages.

The last line disappears the GO button – as we don't need it any longer. It has fulfilled its aim and reason for existence.

This next bit of code checks every frame to see if the image has loaded before resetting the buttons, switching on the pencil tool and removing the dialog box:

```
_root.loadJPGBox.onEnterFrame =
    function () {
    if (JPG.getBytesLoaded() ==
        JPG.getBytesTotal() &&
        JPG.getBytesTotal() != 0) {
        _root.allButsOff();
        _root.mainButDraw.gotoAndStop(2);
        _root.funcFreeDraw();
        _root.help.text = "Click and drag
        to draw pencil lines";
        removeMovieClip(_root.loadJPGBox);
    }
}
```

We reset to the pencil tool simply because that's the default tool, you could easily change it so that it defaulted to another tool such as the JPG move tool if you'd prefer.

The reason the conditional is like this:

```
if (JPG.getBytesLoaded() ==
    JPG.getBytesTotal() &&
    JPG.getBytesTotal() != 0) {
```

...is to check if the image has loaded and if getBytesTotal is not equal to zero. Flash is often likely to be a little slow on the uptake of the file coming in, and it might keep this value to zero for a while, until it realizes that a file is on its way.

We then need to set up the CANCEL button in the dialog box:

```
_root.loadJPGBox.cancelBut.onRelease
    = function() {
    _root.allButsOff();
    _root.mainButDraw.gotoAndStop(2);
    _root.funcFreeDraw();
    _root.freeDraw("");
    _root.help.text = "Click and drag to
    draw pencil lines";
    removeMovieClip(_root.loadJPGBox);
    JPG.unloadMovie();
}
```

If it's clicked, then the tools are reset, the pencil tool is activated, the dialog removed and the content of JPG is unloaded. Nothing too taxing here, but a necessary feature for the user.

Now we move on to the most important of the functions – the one that actually loads in the JPG:

```
loadImage = function (imageFileName) {
    JPG.loadMovie(imageFileName);
```

After the declaration here, the JPG global is told to load in an image with the argument imageFileName. When loading JPGs into Flash, the loadMovie command is used.

Then comes some code that will run every frame:

```
_root.onEnterFrame = function() {
if (JPG.getBytesLoaded() > 0) {
_root.loadBoxPerc.text =
(Math.floor((JPG.getBytesLoaded() /
JPG.getBytesTotal()) * 100)) + "%";
}
if (JPG.getBytesLoaded() ==
JPG.getBytesTotal() &&
JPG.getBytesTotal() != 0) {
```

It sets the percentage loaded text which appears in the dialog box, and checks if the image has fully loaded. The same conditional is performed here, to counteract Flash's slow pick up of files.

When the image is fully loaded, we then need some code to place it on the screen:

```
JPG._width = 200;
JPG._height = 200;
JPG._x = -JPG.width/2;
JPG._y = -JPG._height/2;
JPG._visible = true;
JPGContainer._x = _root.square._x;
JPGContainer._y = _root.square._y;
JPGContainer._xscale = 100;
JPGContainer._yscale = 100;

_root.onEnterFrame = undefined;
duplicateMovieClip(_root.tshirt,
"newtee", 600);
JPGContainer.setMask(_root.newtee);
```

The JPG movie clip is resized to the forced 200 x 200 pixels, and the image is repositioned so that it is centered on the registration point (when images are loaded they are positioned by default at an absolute position of 0,0). It is repositioned so that the JPG scale tool can scale it from the center outwards.

![](img/50202c17d5022233f3e3ec60560e35aa_211_0.png)

The next two lines of code position JPGContainer at the same position as square. square has a center registration point, so this action centers the JPG image in the middle of the t-shirt.

JPGContainer is then reset to a scale of 100%, to reset any previous manipulation.

The last couple of lines of code here set up a mask for the JPGContainer, so that the image doesn't cover the interface when it is moved around.

![](img/50202c17d5022233f3e3ec60560e35aa_211_1.png)

That's it for the JPG loading stuff.

The JPG element is extended later on in the chapter with the JPG scale tool and the dynamic masking...

## JPG masking

The appeal of the JPG masking in this application extends past the standard square or shape mask. In this application, the user is able to draw his own mask shape and then apply it to the loaded JPG.

This part will be split into two sections – the first covers the drawing of the mask, and the second applies the mask to the JPG image.

### Drawing the mask

![](img/50202c17d5022233f3e3ec60560e35aa_212_0.png)

You'll be glad to know that we have already covered the tool required to draw the mask. The mask drawing uses the fill draw tool code, but drawing to its own layer. The drawing movie clip for this tool is set-up in the initialization for the whole movie:

```
jamJar.createEmptyMovieClip("masker", 503);
```

This movie clip is made global there too:

```
_global.JPGM = jamJar.masker;
```

The reason the user is limited to using a fill draw-esque tool is because strokes cannot be used as masks, and therefore the line tool or pencil tool would be pretty useless, so I made the decision during development to limit the tool to this.

Not only did it save me some coding – making a new tool – but it also gets the user familiar with this and the fill draw tool at the same time. Neat deal.

Once you have a mask shape drawn, you'll need something for it to mask...

### Applying the mask to the JPG

![](img/50202c17d5022233f3e3ec60560e35aa_212_1.png)
![](img/50202c17d5022233f3e3ec60560e35aa_212_2.png)
![](img/50202c17d5022233f3e3ec60560e35aa_212_3.png)

The application of the mask to the image is switched on or off through one simple function.

The general strategy here is to use the setMask method, and to switch the mask on or off, depending on the last state. Here's the first bit of code:

```
funcApplyMask = function () {
  _root.allButsOff();
  _root.mainButDraw.gotoAndStop(2);
  _root.funcFreeDraw();
  _root.help.text = "Click and drag to
  draw pencil lines";
}
