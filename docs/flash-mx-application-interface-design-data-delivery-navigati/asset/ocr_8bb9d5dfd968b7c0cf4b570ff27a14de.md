Although we can see the results of the video editing and the mask, at the moment this is all very linear. Sure we can watch our video play again and again, but what happens if we want to stop and study a particular stance, or we miss a section and want to see it again without waiting for the whole kata to play right the way through once more? We need control.

![](bbox=[0.09, 0.25, 0.51, 0.3])

We are going to give our movie some basic video player style controls, which will allow us to control the playback of our video clip and to analyze exactly what is going on at any time.

Create a new button movie clip and name it generic button. (Although it is ok to use any movie clip as a button in Flash MX, for simple controls such as this I still use the old style buttons, as I find them easier to create quickly.) Draw a square with rounded corners in the center of the stage. (Of course you could always just steal it from the library of the completed FLA in the download files.)

![](bbox=[0.43, 0.5, 0.5, 0.57])

Add a keyframe in the down frame and put the onion skin option on.

![](bbox=[0.18, 0.66, 0.43, 0.72])

The button in the down frame can now be scaled down, either dragged using the transform tool, or via the transform palette. The onion skin option allows us to monitor the difference between our up and down button states.

![](bbox=[0.09, 0.83, 0.51, 0.97])

To give another element of user feedback when pressing the button we can also add a little sound. Flash provides us with a wide assortment of sounds in its shared sounds library.

I decided that Switch Small Plastic had the right kind of feel to it. Add a second layer to the button timeline and insert a blank keyframe at the down state. We can then drag an instance of Switch Small Plastic directly into that frame. When the button is pressed it will now give us a 'click' noise.

![](bbox=[0.62, 0.32, 0.86, 0.37])

We will be able to use our newly created button for each of the video player functions. The scaling effect will give the impression of depth to our button by making it appear slightly further away when it is pressed, and the 'click' sound will add to this sense of reality.

We could then go ahead and drag all the buttons we are going to need onto the main stage, but let's plan ahead and think as to how our buttons will be used. With our buttons loose on the stage we would have seven movie clips to concern ourselves with. If though, we put these buttons within another new movie clip, we will have the power to reposition all buttons at once, and refer to them as a single element within our ActionScript.

Create another movie clip called controller. This will become our 'control panel' and house all the buttons that we are going to need to work with our video clip. In this new movie clip create a layer called buttons and drag an instance of our generic button onto the stage. We now need to duplicate this instance seven times using Cmd/CTRL-D.

![](bbox=[0.64, 0.82, 0.85, 0.97])