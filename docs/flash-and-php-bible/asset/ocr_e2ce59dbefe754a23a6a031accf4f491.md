Regardless of whether this is the first pass of the redraw method or not, the blocking clip needs to be repositioned. The login window is placed dead center, which means you can calculate the padding around it, multiply this to create a negative number, and place the blocking clip using that calculation.

```
// reverse the offset to position blocker
blocker.y = y * -1;
blocker.x = x * -1;
```

When all the calculations are complete, you can add the blocker MovieClip to the DisplayList, which makes it visible in the application.

```
addChild(blocker);
```

> NOTE Making all the position-based calculations before the clip is added to the display list minimizes flickering and jumping objects in your application.

# Swapping placement of two MovieClips

ActionScript 3 does not have any depth management like what is found in ActionScript 2 and its predecessors. The equivalent is taking the id of a clip and swapping it with another clip. This appears to be depth management, except for the very important fact that ActionScript takes care of the reordering when the children are swapped.

In this example, you want to make sure the login box is above the blocking clip because if it is placed below it, the user is not able to interact or log in to the application:

```
container.swapChildren(loginMC, blocker);
```

# Centering a MovieClip

The last step of the redraw method is to center the login box on the Stage to ensure it is always in the middle. This is constantly updated when the redraw method is called because resizing the stage would make the login box sit at a noncentered position.

```
loginMC.x = (stage.stageWidth / 2) - (loginMC.width / 2);
loginMC.y = (stage.stageHeight / 2) - (loginMC.height / 2);
```

The calculation uses the stage dimensions and login box dimensions to determine the middle point. This is where the loginMC MovieClip is placed when the calculation is completed.

# close method

The close method has one task: to remove the current login box and allow the application to be used once again. The removal process is achieved by removing the container child, which contains the login box and blocking MovieClip.

```
public function close():void
{
	container.parent.removeChild(container);
}
```