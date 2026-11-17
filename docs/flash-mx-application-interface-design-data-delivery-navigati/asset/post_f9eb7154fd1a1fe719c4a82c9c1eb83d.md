
The next piece of code creates an onEnterFrame method for the flower movie clip:

```
this[name].onEnterFrame = function() {
if(this._xscale < 50) {
this._xscale = this._yscale++;
}
}
```

Inside this onEnterFrame method we then write an if statement that says to the flower: if the _xscale of the movie clip is less than 50%, make both the _xscale and the _yscale 1% larger, so that the flower will appear to grow in size over a few seconds in time.

The original code used to draw the flower with the API makes the flower quite large, as it was simply too difficult working out the curves for the flower petals on a really small scale, so we make the flower start out at a scale of 1% of what it really is, then make it grow from within the onEnterFrame method up to 50%.

A quick note on the onEnterFrame method as it's being used in this example – those of you who are upgrading your skills from Flash 5 will recall that onEnterFrame clip events had to be written on the movie clip itself. This method is discouraged in MX, as you can now more conveniently put all of your code within the one frame on your timeline, and not on the individual symbol. This allows us to put all the ActionScript for an entire movie on one location on the timeline, and it saves us from having to click all over the stage on different buttons and movie clips in search of code that we want to change.

Back to the onEnterFrame method of our flower movie clip, we then have another if statement that looks like:

```
if (this.clicked == true) {
this._x = xPos + (this.startX + (30 *
Math.sin(this.num)) );
this.num += 0.1;
this._y += 2;
this._rotation += 2;
}
```

What this little piece of code does is waits until the flower is clicked on, then moves the x position of the flower to the left or right of its original starting position. The code in the second line of this if statement keeps generating a series of numbers that varies between a negative and a positive number, which we add to the original x position of the flower, thereby making it sway from left to right.

As we do all this, we increase the y position by 2 pixels each time, so that the flower appears to fall down to the bottom of the stage. We also increase the _rotation property of the flower by 2 degrees, just to create a slightly more organic motion as the flower falls.

The next if statement in our makeFlower function is written like so:

```
if (this._y > (movieHeight-6)) {
this.clicked = false;
this.enabled = false;
}
}
```

All this does is tell the flower that if its y position is greater than the height of the plant movie clip, it should stop falling and stay still. It does this by changing the value of clicked back to false again. Remember that all the code responsible for making the flower fall is inside the previous if statement that only executes if the value of clicked is set to true. If you made your movie so that the plant looked like it was sitting on a ledge or table, and the ground was a lot further down than the height of the movie clip, just simply add the extra distance from the ledge to the ground to the variable movieHeight. By setting this.enabled to false in the last line of the above if statement, we effectively stop the flower from having the ability to be clicked on any more so that it can't try and move again. Once a flower has come to rest you'll see that it can't be clicked on any more.

After the makeFlower function, there's an action that looks like:

```
stop();
```

Now let me tell you all about the stop action... only joking! That's it, we're done. Our plant grows smoothly, elegantly, and changes size and color according to how often we visit the site, and we've built it in such a way that we can easily change the colors of all the parts of the movie and add or remove leaves as we see fit. Nice work all round I say!

![](img/50202c17d5022233f3e3ec60560e35aa_182_0.png)

## A note about testing and debugging this movie

You may or may not have noticed that inside the plant movie clip where all our code is, there is a layer called debug between the Plant Actions layer and the Date Actions layer, and that the layer has been turned into a Guide Layer. To better understand what I'm about to talk about, un-check the guide layer option by right-clicking/CTRL-clicking the layer and un-checking the Guide option.

If you run your movie again, you'll see several text fields on the stage that display some pertinent information. Of course I'm well aware that the trace action can be used to display the output of variables, and also that MX has some very complex debugging devices built in to the Player in the authoring environment – but none of these options work when viewing a SWF in a browser window or an .exe file. I like to output variables I want to watch into dynamic text fields on screen so I can trace the variables in a browser window. And once I've finished debugging my movie, all I have to do is turn the layer with the text fields into a Guide layer and the movie displays as per normal. This way I don't have to keep adding and removing text fields every time I want to debug the movie.

One more thing. If you wish to avoid opening, closing, and re-opening the plant movie in order to see it grow, there's a line of code in the Date Actions layer on line 55 (//plantSize=26;) which you can uncomment and change the value of plantSize to between 0 and 50 if you want to see how the plant looks when it starts out and when it is at full growth. This won't affect any of the values inside your stored sharedObject as the line is written after the sharedObject data is stored on your computer.

There's also some code on line 20 (//daysSinceLastVisit = 2;) that you can uncomment and change to force your plant to shrink in size (this will affect the data written to the sharedObject file on your computer). Doing this simulates not visiting the site for the amount of days you specify as the value of the variable daysSinceLastVisit. Just make sure line 55 is commented out if you do this, otherwise there might be some conflict in what you are hoping to see.

## Other things to do with this concept

This book is all about providing some inspiration when you design your interfaces. So please take some time after you've read this chapter to let all the code and concepts sink in, and try to come up with some of your own ideas about how to represent user-stickiness in your movies.

One idea I had while building this FLA for the book was to use the plant not to represent individual user stickiness, but use it as a kind of graph that represented overall viewer statistics. Flash MX has some awesome new built-in features that allow you to easily detect all sorts of information about a user viewing your site. Using the built-in System Object, you can detect such things as: the language installed on the users' computer (to give you a rough idea of what country users are coming from), the operating system they're using, their screen resolution (very handy, that one), and many other user settings.

You could also use a PHP script to fairly easily tell which browser and version that a user is running, as well as the URL they came from before visiting your site and a whole host of other information relevant to collecting global user statistics about your site. Your Flash movie could call the PHP script to retrieve this information in combination with settings gathered from the Flash System Object, and then send that information to a database for permanent storage on the server-side. Your plant could then retrieve this global information and act as a graph to display the statistics.

If you ever decide to build something like this based on what you've learned in this chapter, please let me know as I'd love to see what you've done with the concept.

## A T-SHIRT DESIGNER

All people can be creative, but I think a lot of people are scared to be. When faced with a blank canvas, a brush, and a selection of paints, a lot of people just freeze up. There's something intimidating about the purity of a white page, and the permanence of putting paint on it.

![](img/50202c17d5022233f3e3ec60560e35aa_184_0.png)

I wanted to create an application that would encourage people to play around with design in an informal environment. Rather than start from a white square then, I decided to begin with the familiar shape of a t-shirt, on which users could experiment with drawing a design of their choice. I chose a t-shirt because it's somewhere where you often see photos, patterns, and logos, and it just happened to make nice pictures too.

![](img/50202c17d5022233f3e3ec60560e35aa_184_1.png)

The end result is an application that I'm extremely proud of, providing the ability for all to create, and an interface that doesn't take a manual to learn (of course, I could have included a manual...). The simplicity of the interface was one of the key considerations here, as I wanted it to appeal to a wide web audience of varying ability.
