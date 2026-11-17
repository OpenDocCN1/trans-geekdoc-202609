# Further thoughts

So now we have a fully working interface. At this stage it would seem appropriate to discuss its strengths and weaknesses.

I would say that in a number of senses it is successful as a navigation device. It is easy to use while still providing novelty. While the user might at first be unsure of what is going to happen when they click on one of the tags, it is fairly apparent that that is what they have to do. Upon clicking, the motion that ensues might initially feel odd, but I think that the logic of it shines through. Motion is the key to this. The transition between states underlines the logic of the interface. It feels quite solid and predictable, like a machine. The user is generally aware of both where they are and the alternative routes they could have taken.

While looking at how the interface succeeds, it's important to also acknowledge where the interface fails. While the interface can cope with most structures, if you needed to include 20 categories within another category, you'd quickly encounter problems with the labels overlapping each other. Already one can see this with some of the longer category names. You could try and circumvent this by having each node swapDepths when the user rolls over it, but that might look slightly odd and would not meet our aim of legibility.

Also if the interface were more than four levels deep at any point, it would begin to move off the right of the screen. A fairly simple way of solving this would be to have whatever node is currently open centered on stage, and this might also be a fairly pleasing effect visually, adding to the sense of progression. I've included a basic file, called spinner_centered.fla, in the download files, demonstrating this with comments wherever I've added any code.

A bigger concern is perhaps the size of the interface. With any interface occupying that much space on the screen, you're in danger of detracting from whatever content there may be. This could possibly work if the content one was dealing with was in floating windows, or you could have the interface fold away when not in use. It would be possible, for instance, to have the subnodes that were not chosen fade out or retract when the navigation is not in use, leaving the nodes that were chosen as a breadcrumb.

The beauty of this interface, as it stands, is that you could easily modify it to suit your own purposes, and that the aesthetics are separate from the data content. It shows how the use of XML can bring data dynamically into your interfaces, allowing you to play with the structure as much as you want.

![](bbox=[0.015, 0.655, 0.99, 0.985])