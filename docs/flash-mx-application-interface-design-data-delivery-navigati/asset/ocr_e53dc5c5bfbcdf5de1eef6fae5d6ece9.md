Here, we delete the last joke array that we have been using for the individual jokes. The last few lines take advantage of the built-in sorting method of the array object to randomize our array. We send with the sort call a compare function that returns either a 0 or 1, which the sort method uses to randomly shuffle the array. Usually when you use a compare function, the sort method will use it to compare two adjacent indices at a time and place them in an order determined by whatever the compare function returns, -1, 0, or 1. In our example, we simply send a 0 or 1 without a consideration as to the values of the indices themselves. Based on whether the number is 0 or 1 for a particular pair of indices, the sort method will swap the two or leave them in place. As it does this throughout the length of the array, the effect is a random shuffle.

With the set-up explained, let's get into the code that creates our joke dialog. Select the first frame of the code layer and type the following into the ActionScript editor:

```
jokeX = 200;
jokeY = 100;
currentJoke = 0;

jokeTF = new TextFormat();
jokeTF.font = "_sans";
jokeTF.size = 18;

this.createTextField("bubble", 0, jokeX, jokeY, 0, 0);
bubble.autoSize = "center";
bubble.setNewTextFormat(jokeTF);
bubble.selectable = 0;
```

The first three lines are variables we will be using in our code. jokeX and jokeY are the center coordinates position of our joke text field. currentJoke is the index number our current position in the jokes array. Next we create a new TextFormat object so that we can format our joke text field. We give it a system font choice of "_sans" and a point size of 18.

The last block creates a new text field called bubble (I was thinking of little comic dialog bubbles). The create line sets the text field's depth at 0, its _x and _y to equal the variables we set above, and its width and height to 0 pixels. We can do this because on the next line we set its autoSize property to be center, which means that the text field will automatically expand from center to contain whatever text we place inside it. On the final lines we set bubble's text format to be our jokeTF format and we disable its selectable property so that the user won't get an I bar when they place the mouse over the text field.

Let's continue. Place these lines after the previous code:

```
this.createEmptyMovieClip("speechLine", 1);
jokePeople.gotoAndStop("noTalk");
continue_btn._visible = 0;
```

Three straightforward lines for you. The first creates a new movie clip in which we will draw each character's speech line (the line that leads from the character to text field bubble). Next we send our jokePeople movie clip, which is the instance name of the jokePeople symbol on our stage, to its "noTalk" frame. Finally, we turn our continue_btn instance invisible, since it shouldn't be seen until the content has been fully loaded.