
## Frames versus bytes

In Flash 4, preloaders were accomplished by using the _framesLoaded and _totalFrames properties of movie clips. By testing the amount of frames that were loaded into the player against the total amount of frames in the movie, you could determine how much was left to be loaded. The problem with this method occurred when the file size was not evenly distributed across frames, so if you had an exorbitant amount of data in the tenth frame of a ten frame movie, the preloader might say 90% loaded (since 90% of the frames had been loaded) when in fact only a small percentage of the total bytes for the entire site had been loaded, giving the user slightly misleading information.

A much more accurate way to determine the amount loaded into the player is by using the getBytesLoaded() and getBytesTotal() methods of a movie clip, which were introduced in Flash 5. These methods will, respectively, return the amount of information in bytes that has loaded into the player and the total bytes of the movie. To then convert these numbers into kilobytes, a unit much more comprehensible to our audience, you must divide the results by 1024, which is the number of bytes in a kilobyte.

We will exclusively use the bytes method over the frames method in our examples, as it gives the user much more accurate feedback and will allow us greater control.

## Compression

A minor stumbling block for preloaders has now been introduced in Flash MX with the introduction of the new compression applied during publishing. This wonderful addition to the program further compresses the already small SWFs, making them even tinier. Movies that contain a lot of text and code will benefit greatly from this extra compression (I've seen movies reduced 25-50% in file size, which is nothing to shrug at).

So what could possibly be the problem? Well, the getBytesLoaded() and getBytesTotal() methods actually return the uncompressed file size of the movie. This does not become an issue if you merely use these methods to return a percentage since the relationship between the two remains the same. However, if you wish to display the actual amount of bytes that are loading, or the total bytes that will be loaded, the uncompressed value will be inaccurate since it is the compressed amount that is being loaded into the player.

![](img/50202c17d5022233f3e3ec60560e35aa_13_0.png)

The fix for this is simple, taking little extra time, and really only becomes a nuisance upon updates to the movie. At the end of the first exercise I will demonstrate this fix for you so you may apply it to your own preloaders. Whether you see a need to use the compressed number will depend on your situation. If the difference between the compressed and uncompressed file sizes is merely a few kilobytes, then using the uncompressed value and saving the hassle would probably be preferable. My personal site, 27Bobs.com, which was 200kb when uncompressed, became 150kb after the compression. This tremendous difference was not something I could ignore and so I incorporated the fix.

## File size and exported symbols

One last thing to keep in mind is the file size of the preloader itself. Remember that its entire purpose is negated if it does not appear to the user almost immediately. This means that it is imperative to keep your preloader at a tiny size. Simple vectors, small bitmaps, limited sounds, and minimal code will all help ensure the file size remains what it needs to be (and, of course, *not* using sounds and bitmaps will help even more). The last thing you want to find yourself doing is providing a preloader for your preloader.

Sometimes, however, additional data is loaded before the preloader that can delay the appearance of your movie's first frame. If you have exported any symbols from your library, including movie clips, sounds or fonts, these will load by default before the first frame of your movie. It will only be after these symbols are fully loaded that your first frame, and your preloader, will be drawn. Obviously, if you have a lot of symbols exported, which you need to do if you intend to add these items to the stage using code, then this will have an adverse effect on your preloader.

There are several ways around this problem. One common solution is to have your main content load into a separate level after your preloader has loaded. By keeping all of your exported symbols in this separate movie, you can load your preloader almost immediately into a base layer and give the user feedback as the main content loads. A related solution is to load all of your content into movie clips in your main movie. This gets to be a bit more cumbersome, and I usually opt for the former solution of loading into levels.

Another solution, which has been introduced in Flash MX, is to deselect the "Export in first frame" default when creating a new symbol. What this means is that your symbol will not be automatically loaded before the first frame is drawn and will instead be loaded at the frame that you manually place it on the stage. If you do not actually place an instance of the symbol on the stage in the authoring environment before you publish the movie, then you will not be able to access it through code. Using this feature, you can still export the symbols, but you don't have to wait for them to load before the preloader appears.

![](img/50202c17d5022233f3e3ec60560e35aa_14_0.png)

There appears to be a bug with exported fonts in Flash MX, version 6.0. Deselecting "Export in first frame" in the font linkage dialog box does not in fact keep the font from being loaded in the first frame. As long as you have "Export for Actionscript" selected, the font will automatically be exported in the first frame no matter what.

In addition to that, if you have exported fonts for use with TextFormat objects in movies that you are intending to load into levels or movie clips, then these fonts will not appear unless you have exported them from your _level0 movie as well. This of course means that if your preloader is on _level0, as it commonly is, any exported fonts will need to load before the preloader appears.

Some possible solutions to this problem include:

- keeping your exported fonts to a minimum
- not exporting fonts containing an excessive amount of vector information
- not using TextFormat objects with exported fonts in loaded movies

Although the first two options are good to consider no matter what, the last limits you severely. Macromedia is aware of the problem and hopefully a solution will soon be found.

## Creating killer preloaders

For me, preloaders come in three flavors. First, we have textual information on the status of the load. This could be anything from displaying “loading…” to a constant feedback of numbers reporting loading statistics. Building on this idea, you can represent the progress of the load graphically to keep the user informed of the status. The most common example of this, and the most common preloader, is the loading bar. Finally, we can ignore loading status altogether and simply keep the user entertained during the load time. Two effective methods for doing this are providing the user with an animation to watch or a game to play.

Again, most preloaders will be a combination of these types, and the distinction for most is rather blurry. For instance, the very act of a loading bar animating across the screen to show the percentage loaded can be considered a base form of entertainment (that’s not to say that this is how you should spend your Saturday nights, but it is a kind of entertainment). Add some relevant numbers to give some textual feedback, and you have all three types rolled into one preloader. Of course, there’s nothing that says you have to create a loading bar like everyone else…

## Laser Logo

This first exercise is a variation on the classic loading bar and takes advantage of Flash MX’s new ability to draw dynamic masks. The idea is to have a logo slowly revealed through the course of the load. The amount that is seen will be the percentage of the total bytes that have been loaded.

![](img/50202c17d5022233f3e3ec60560e35aa_15_0.png)

A simple mask wiping across a logo does the trick, but to make it more interesting we will code lasers to actually appear as if they are drawing the logo onto the screen. Open up the file laserLogo.swf to see the end result. The accompanying FLA is fully commented.

Let’s go over how this effect was accomplished.

### Masking the logo

The first thing we will do is create and animate a rectangular dynamic mask for our logo. This is a new option for us in Flash MX thanks to the setMask method and the drawing API. Let’s see how it works!

Open up the file laserLogo_start.fla from the download files. This file has the main timeline already structured for you. You will see that it is a single frame movie with only a few layers. The base layer is simply a vertical rectangle outline. The second layer contains our logo set at center stage. The third layer has two dynamic text fields, both with _sans selected as the font. The two text fields have the instance names loaded and total, respectively. The final layer named code contains a blank keyframe. This is where we will be doing all of our work.

Save the movie with your own filename.

![](img/50202c17d5022233f3e3ec60560e35aa_15_1.png)
