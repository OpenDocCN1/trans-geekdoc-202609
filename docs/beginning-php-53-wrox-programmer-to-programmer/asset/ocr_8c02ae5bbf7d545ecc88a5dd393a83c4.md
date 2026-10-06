# Appendix A: Solutions to Exercises

The $threshold variable will be used to mark the position on the x-axis where you move from the used disk space to the free disk space in your diagram. Because used disk space is usually represented on the left side of such diagrams, you need to calculate that space — it is the disk space minus the free disk space. Divide by the total amount of disk space to get a number between 0 and 1, which you then multiply by the width of the image. Subtract 2 from the width of the image because you already used 2 pixels drawing the image border; add 1 to the overall threshold because pixels start at 0.

```
$threshold = intval( ( ($diskTotal - $diskFree) / $diskTotal )
* ($Width-2) + 1;
```

For example, if your disk was 400 bytes and had 200 bytes, you divided 400 equals 0.5. If your image width was 500 pixels, you would multiply the 0.5 and 498 (width minus 2 for the border) to get 249. Then you'd add 1 to 250: the x position that is halfway across the image.

Fill with a red rectangle that extends right from the left-hand side to the threshold to represent the used disk space:

```
imagefilledrectangle($myImage, 1, 1, $threshold, ($iHeight-2 ), $red);
```

And a green rectangle from the threshold onward for the free disk space:

```
imagefilledrectangle($myImage, ($threshold + 1), 1, ($iWidth - 2 ),
$iHeight-2, $green );
```

Finish the script in the usual manner.

```
header( "Content-type: image/png"; );
imagepng($myImage);
imagedestroy($myImage);
?
```

Figure A-2 shows an example result.

![](bbox=[0.132, 0.672, 0.757, 0.863])

Figure A-2

710