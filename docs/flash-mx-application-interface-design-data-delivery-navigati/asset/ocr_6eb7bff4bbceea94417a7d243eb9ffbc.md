Select the blank keyframe in the first frame of your code layer and open up your ActionScript editor. The first thing we will do in our code is set up a few variables for our movie. Go ahead and type:

```
stageWidth = 550;
stageHeight = 400;

moveWidth = stageWidth*.5;
moveHeight = stageHeight*.5;

totalY = logo._height;
totalX = logo._width;

totalLasers = 5;
```

stageWidth and stageHeight are the dimensions of our movie. Instead of hard coding these, you might want to use the width and height properties of the new Stage object. I have found, however, that at times during testing, the values are erroneous. If you're using _root_.width and _root_.height, you'll get the width of a bounding box around all the objects on the stage instead of the values you set in Movie Properties, (though it works fine when embedded in an HTML page), and so I prefer to hard code the dimensions in the first few lines of my code.

moveWidth and moveHeight are the maximum distance our lasers (the spheres that fire the beams) will travel as they move about the stage. We will actually center the lasers' movement around the logo, so these two variables will keep the lasers near the center of the screen.

totalX and totalY will be used for the mask that we will draw over our logo. It will be a rectangular mask, and these two variables hold the final size of that rectangle. If you select the logo movie clip on the stage, you will find that I have already given it the instance name logo.

Finally, totalLasers is a variable that holds the amount of lasers we will add to the stage. I found that five was a nice, processor-friendly number for me, but feel free to adjust this number as you test.

The next step is to create the empty movie clip that we will use to draw our logo's mask. Type this code after the preceding lines:

```
this.createEmptyMovieClip("mask", 100);
mask._x = logo._x;
mask._y = logo._y;
logo.setMask(mask);
```

In these lines we create a movie clip named mask and place it at the registration point of our logo (which you will notice is set at the top left of the symbol). We then use the new setMask method to enable it as a mask for our logo movie clip.

With these basic variables and the mask set up, let's write the function that we will call each frame to keep an eye on the loading status:

```
assessLoad = function(clip) {
// var kbLoaded = Math.floor
//•(clip.getBytesLoaded()/1024);
// var kbTotal = Math.floor
//•(clip.getBytesTotal()/1024);

// delete these two lines and uncomment
// the above lines upon publishing
var kbLoaded = Math.floor
•(getTimer()/200) + 2;
var kbTotal = 150;}
```

This is the heart and soul of our preloader. We are creating a function called assessLoad and sending it a reference to a movie clip (clip in the parameters). This will be the clip that we are checking the load status of. This can be the main movie, a movie clip or a level, depending on what we send the function. The first two lines that are commented out are what we would use if we were using this file online. For testing purposes, I've faked some variables in the following lines, which you would delete when you published the final version of this file. Let's take a look at what the commented out lines actually do for us.