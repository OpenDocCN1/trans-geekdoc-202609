# # Exercise 2 Solution

There are two obvious ways that you can graphically display disk space. The quickest and easiest way is to create a simple horizontal scale: a rectangular shape that is made up of two blocks of color, one color representing the used space on the disk and the other representing the free space. This gives you a nice quick overview of your disk usage. The code for doing this follows.

It's always good practice to store the width and height of your images in variables within the script. Then if you want to change the size of the image you can do so easily at the beginning of the script and any calculations you do with the image width and height are automatically updated.

```
```php
<?php
$iWidth = 500;
$iHeight = 50;
```
```

Create the image and allocate black and white. Because white is the first color allocated, it will be the background color of the image. Black will be used to add a border to the image.

```
```php
$myImage = imagecreate( $iWidth, $iHeight );
$white = imagecolorallocate( $myImage, 255, 255, 255 );
$black = imagecolorallocate( $myImage, 0, 0, 0 );
```
```

In this example solution, red and green are used to represent used disk space and free disk space, respectively. You can use any colors you like.

```
```php
$red = imagecolorallocate( $myImage, 255, 0, 0 );
$green = imagecolorallocate( $myImage, 0, 255, 0 );
```
```

Get the total amount of space on the disk and the amount of space that you have free. Both of these values are returned in bytes. The actual values are irrelevant — all you need them for is to get a proportion so that you can draw the bar.

```
```php
$diskTotal = disk_total_space( "/" );
$diskFree = disk_free_space( "/" );
```
```

Then draw a one-pixel black border around the outside of the image.

```
```php
imagerectangle( $myImage, 0, 0, $iWidth - 1, $iHeight - 1, $black );
```
```