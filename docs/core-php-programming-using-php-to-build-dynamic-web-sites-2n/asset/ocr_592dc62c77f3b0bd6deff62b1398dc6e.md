```
$ButtonLabel = "CLICK";

if(!isset($ButtonFont)) {
    $ButtonFont = 5;
}
```

```
//create image and colors
$image = imagecreate($ButtonWidth, $ButtonHeight);
$colorBody = imagecolorallocate($image, 0x99, 0x99);
$colorShadow = imagecolorallocate($image, 0x33, 0x33);
$colorHighlight = imagecolorallocate($image, 0xCC, 0xCC);
```

```
//create body of button
imagefilledrectangle($image, 1, 1, $ButtonWidth-2, $ButtonHeight-2, $colorBody);
```

```
//draw bottom shadow
imageline($image, 0, $ButtonHeight-1, $ButtonWidth-1, $colorShadow);
```

```
//draw right shadow
imageline($image, $ButtonWidth-1, 1, $ButtonWidth-1, $ButtonHeight-1, $colorShadow);
```

```
//draw top highlight
imageline($image, 0, 0, $ButtonWidth-1, 0, $colorHighlight);
```

```
//draw left highlight
imageline($image, 0, 0, 0, $ButtonHeight-2, $colorHighlight);
```

```
//determine label size
```