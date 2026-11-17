Once we have got to the end of our video clip, inserting instructions as we go, we can press the export button to have the array we need generated in the output window. This should then be copied to your clipboard. We need to create a file that includes this information that our playback movie will be able to make use of. The recommended file extension for saving ActionScript is .as. Using TextEdit on a Mac, or Notepad on a PC, paste the contents of the clipboard into an empty document and save this as kata.as. This should be in the same folder as the FLA and SWF files we are creating.

![](bbox=[0.07, 0.33, 0.47, 0.42])

The playback movie can utilize some of the elements we created for the recording movie. The video movie clip, mat and feet all remain the same and the video control elements of the controller movie clip will still be needed to play back our now diagram-enhanced video.

There are a number of ways in which we can make constructing the playback movie simpler. Perhaps the easiest is to save our first movie, kata_record under a new name, kata_play, and then delete the aspects we no longer require and adapt the others. This is the technique we will document here.

We can safely delete the buttons that are linked to the record functions – that's insert code, move, rotate and export, plus all the code that accompanies them. The fast rewind and forward buttons will be superfluous too. We also don't need the info box or the ability to drag the video clip, so again any symbols or code associated with this can be removed.

What we do need are some new buttons in the controller movie clip. These are going to move us forward and back one step, and toggle between the side video we prepared earlier and the front video we have used until now. These buttons should have instance names of forwardBut, backwardsBut and toggleBut respectively. Our new slimmed down controller should look something like this.

![](bbox=[0.56, 0.25, 0.87, 0.39])

We need to import our side view video. We do this just as we did the original one, through the File > Import to library menu option. We should import this with identical settings to the first video we brought into Flash.

As with the front video, the side one needs to be housed in a symbol. If we duplicate our current video symbol, calling it video side, we can replace the video on the video layer with our freshly imported side view video.

Back on the main timeline, insert a new layer above the current video layer. Drag an instance of video side to the stage, aligning it exactly with the existing video clip. Call this instance videoside. We now need to add a function to our toggle button so as to see either one view or the other. This is the code:

```
controls.toggleBut.onRelease = function() {
 if (_root.fvvis == false) {
 video._visible = true;
 videoside._visible = false;
 fvvis = true;
 } else {
 video._visible = false;
 videoside._visible = true;
 _root.fvvis = false;
 }
};
```