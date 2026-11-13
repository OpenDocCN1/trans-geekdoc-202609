lists names for the current states. The second row enumerates names for the events that DrRacket encounters: e0, e1, and so on. Each ei might be a clock tick, a key press, or a mouse event. The next three rows specify the result of dealing with the event:

+   • If e0 is a clock tick, big-bang evaluates (tock cw0) to produce cw1.

+   • If e0 is a key event, (ke-h cw0 e0) is evaluated and yields cw1. The handler must be applied to the event itself because, in general, programs are going to react to each key differently.

+   • If e0 is a mouse event, big-bang runs (me-h cw0 e0 ...) to get cw1. The call is a sketch because a mouse event e0 is really associated with several pieces of data—its nature and its coordinates—and we just wish to indicate that much.

+   • Finally, render turns the current state into an image, which is indicated by the last row. DrRacket displays these images in the separate window.

| current state | cw0 | cw1 | ... |
|---|---|---|---|
| event | e0 | e1 | ... |
| on clock tick | (tock cw0) | (tock cw1) | ... |
| on keystroke | (ke-h cw0 e0) | (ke-h cw1 e1) | ... |
| on mouse event | (me-h cw0 e0 ...) | (me-h cw1 e1 ...) | ... |
| its image | (render cw0) | (render cw1) | ... |

Figure 13: How big-bang works

The column below cw1 shows how cw2 is generated, depending on what kind of event e1 takes place.

Let’s interpret this table with the specific sequence of events: the user presses the “a” key, then the clock ticks, and finally the user clicks the mouse to trigger a “button down” event at position (90,100). Then, in Racket notation,

+   1. cw1 is the result of (ke-h cw0 "a");
+   
+   2. cw2 is the result of (tock cw1); and
+   
+   3. cw3 is the result of (me-h cw2 90 100 "button-down").