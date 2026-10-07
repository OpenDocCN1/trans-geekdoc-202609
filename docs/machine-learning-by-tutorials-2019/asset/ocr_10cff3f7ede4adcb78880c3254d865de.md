# Machine Learning

# Chapter 13: Sequence Classification

Add the following constant to the Config struct, which defines the size of the buffer
you'll create:

```
static let bufferSize =
windowSize + windowOffset * (numWindows - 1)
```

You define a buffer large enough to hold one full window plus the space taken
by the offsets for the other windows. So for the settings you've used so far, Gesture
It will be 35 samples. Don't worry if it's not clear why this is the right
size — you'll see.

Add now the following properties to manage the buffer. Put them with the ML-
related properties in GameViewController:

```
let dataBuffer: MLMultiArray =
GameViewController.makeMLMultiArray(numSamples:
var bufferIndex = 0
var isDataAvailable = false
```

You create dataBuffer using the convenience method you wrote earlier. As new
motion arrives from the device, you'll use bufferIndex to determine where to
store data within the buffer. You'll set the isDataAvailable to true once
the buffer contains data to perform its first prediction.

For the remainder of this discussion, please refer to the following diagram,
shows the buffer's contents at each period over the first 40 steps:

| T1- | T20 T21- | T15 | Pred. 1 at T20 with values from T1 to T20 |
| T21—T25,T6— | T20 T21—T25,T6— | T15 | Pred. 2 at T25 with values from T6 to T25 |
| T21— | T30,T31— | T21—T30,T31—|T15 | Pred. 3 at T30 with values from T11 to T30 |
| T21— | T35,T16—T20 T21— | T35 | Pred. 4 at T35 with values from T16 to T35 |
| T21— | T40 T21— | T35 | Pred. 5 at T40 with values from T21 to T40 |

# Buffer contents over time

Think of the buffer as having two halves, with a full prediction window on the left
 auxiliary storage on the right. The second "half" isn't a true half in this case,
because it's smaller than the first, but won't be a problem.

You'll increment bufferIndex as new data arrives, moving across the first half of
the buffer, you'll reset it to the beginning whenever it reaches the buffer's
midpoint. That is, bufferIndex will always point to the next location to find within

![](bbox=[0.162, 0.923, 0.355, 0.958])

432