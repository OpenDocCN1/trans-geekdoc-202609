jamJar stores a reference to a movie clip that holds the mask and JPG movie clips:

```
```
_root.createEmptyMovieClip("JPGAndMaskHolder", 501);
_global.jamJar = _root.JPGAndMaskHolder;
```
```

Why jamJar you may well ask? Well, jam stands for JPG And Mask, and a jar is a holder. It's a little bit esoteric, but it was originally jamHolder and jamJar seemed so much nicer.

JPGContainer is the parent of the movie clip that loads in the JPG graphic:

```
```
jamJar.createEmptyMovieClip("JPGHolderHolder", 502);
_global.JPGContainer = jamJar.JPGHolderHolder;
```
```

JPGHolderHolder may seem like a daft name, but logically this movie clip is the holder of the movie clip that holds the JPG, so it kinda makes sense. Luckily, this name is only mentioned here, and from here on in, it's the much more palatable JPGContainer. The JPG graphic is nested within this movie for scaling and JPG manipulation. More on this later.

JPG is the movie where we load JPG images:

```
```
JPGContainer.createEmptyMovieClip("JPGHolder", 500);
_global.JPG = JPGContainer.JPGHolder;
```
```

JPGM stores a reference to the movie clip where a mask is drawn:

```
```
jamJar.createEmptyMovieClip("masker", 503);
_global.JPGM = jamJar.masker;
```
```

More on this later.

![](bbox=[0.63, 0.105, 0.89, 0.31])

![](bbox=[0.63, 0.315, 0.89, 0.51])

![](bbox=[0.63, 0.52, 0.89, 0.72])

![](bbox=[0.63, 0.735, 0.89, 0.94])