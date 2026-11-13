+   - the function that turns a world state into an image:

```
```
; ShotWorld -> Image
; adds the image of a shot for each y on w
; at {MID,y} to the background image
(define (to-image w) BACKGROUND)
```
```

because the problem demands a visual rendering;

+   - one for dealing with tick events:

```
```
; ShotWorld -> ShotWorld
; moves each shot on w up by one pixel
(define (tock w) w)
```
```

+   - and one function for dealing with key events:

```
```
; ShotWorld KeyEvent -> ShotWorld
; adds a shot to the world
; if the player presses the space bar
(define (keyh w ke) w)
```
```

Don't forget that in addition to the initial wish list, you also need to define a main function that actually sets up the world and installs the handlers. Figure 61 includes this one function that is not designed but defined as a modification of standard schema.