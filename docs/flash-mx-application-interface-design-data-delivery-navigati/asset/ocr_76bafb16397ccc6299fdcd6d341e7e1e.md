# Creating killer preloaders

For me, preloaders come in three flavors. First, we have textual information on the status of the load. This could be anything from displaying “loading…” to a constant feedback of numbers reporting loading statistics. Building on this idea, you can represent the progress of the load graphically to keep the user informed of the status. The most common example of this, and the most common preloader, is the loading bar. Finally, we can ignore loading status altogether and simply keep the user entertained during the load time. Two effective methods for doing this are providing the user with an animation to watch or a game to play.

Again, most preloaders will be a combination of these types, and the distinction for most is rather blurry. For instance, the very act of a loading bar animating across the screen to show the percentage loaded can be considered a base form of entertainment (that’s not to say that this is how you should spend your Saturday nights, but it is a kind of entertainment). Add some relevant numbers to give some textual feedback, and you have all three types rolled into one preloader. Of course, there’s nothing that says you have to create a loading bar like everyone else…

# Laser Logo

This first exercise is a variation on the classic loading bar and takes advantage of Flash MX’s new ability to draw dynamic masks. The idea is to have a logo slowly revealed through the course of the load. The amount that is seen will be the percentage of the total bytes that have been loaded.

![](bbox=[0.12, 0.75, 0.44, 0.99])

A simple mask wiping across a logo does the trick, but to make it more interesting we will code lasers to actually appear as if they are drawing the logo onto the screen. Open up the file laserLogo.swf to see the end result. The accompanying FLA is fully commented.

Let’s go over how this effect was accomplished.

# Masking the logo

The first thing we will do is create and animate a rectangular dynamic mask for our logo. This is a new option for us in Flash MX thanks to the setMask method and the drawing API. Let’s see how it works!

Open up the file laserLogo_start.fla from the download files. This file has the main timeline already structured for you. You will see that it is a single frame movie with only a few layers. The base layer is simply a vertical rectangle outline. The second layer contains our logo set at center stage. The third layer has two dynamic text fields, both with _sans selected as the font. The two text fields have the instance names loaded and total, respectively. The final layer named code contains a blank keyframe. This is where we will be doing all of our work.

Save the movie with your own filename.

![](bbox=[0.52, 0.62, 0.93, 0.99])