Well, that second one sure took less time than the first. Buuuut. . .two stumps is hardly enough to make a real voting consensus.

Let's say you want to shoot for 200 stumps in the ensemble model. All you have to do is repeat these steps another 198 times. I'll wait. . .

If you really did that 198 times, then I appreciate you (and maybe feel a bit sorry). We can save ourselves a ton of time by recording a macro. This shuffling operation is perfect for something like that. For those of you who have never recorded a macro, it's nothing more than recording a series of repetitive button clicks so you can play them back later instead of giving yourself carpal tunnel syndrome.

To record a new Macro, head over to the View Ribbon tab. On the far right you'll see the Macro dropdown button. Click on that and select “Record Macro. . . ”

A new window opens where you can name your macro something like GetBaggedStump. And for convenience’s sake, let’s associate a shortcut key with the macro. I’m going to throw in a G into the shortcut box for GetBaggedStump (see Figure 7.16). If I want to run this macro in the future, I can just press Ctrl+Shift+G. Note the sequence of key presses might be different if you’re on a Mac.

![](bbox=[0.13, 0.45, 0.48, 0.72])

Figure 7.16: Getting ready to record a macro

Click OK to get recording. Here are the steps that’ll record a full decision stump:

+   1. Go to the RandomSelection tab.
+   2. Right-click column P and insert a new blank column.
+   3. Select and copy the winning stump in O1:O2.
+   4. Use Paste Special to paste the values into P1:P2.
+   5. Click Refresh All on the Data tab to generate a new random sample.
+   6. At the bottom of the screen, in the status bar, there’s a square that’s next to a label that says “Ready.” Click that square – it’s actually a Stop icon – it stops the macro recording.