```
$thumb_src = $file_src."_thumb".$file_ext;
$file_src .= $file_ext;
copy($this->imagefile, $file_src);
```

Now that we have a unique filename and the proper extension, we can put together filenames for both the main file and the thumbnail that we're going to make. Then the source file is copied from its temporary home to the full path on the filesystem, as indicated in $file_src.

```
if ($file_ext == ".jpg")
{
$cmd = "../catalog/makeimagethumb $file_src $thumb_src $this->thumb_width";
    $out = system($cmd,$err);
```

If the image is a jpg, we call a shell script, using the system() function. Here it is:

```
#!/bin/sh
PATH=/usr/local/bin:/usr/new/pbmplus:$PATH
export PATH
rm ./$2
djpeg ./$1 | pnmscale -xysize $3 $3 | pnmmargin -black 1 | cjpeg >
./$2
```

This script will be passed two text strings ($file_src and $thumb_src), which are assigned to variables $1 and $2. The shell script first removes the existing thumbnail (if it exists), and then goes about creating a new one. djped converts the jpg to the pbm format. The output of that is piped to pnmscale, which reduces the picture to a 50×50 px image; the output of that is piped to pnmmargin, which adds a black border. Finally, the resulting image is redirected to a file, as indicated by $2 (or $thumb_src).

![](bbox=[0.18, 0.7, 0.25, 0.78])

The previous shell script could have been kept within PHP. It could have been written more like this:

```
$path = "/path/to/pbmplus/";
$djpeg = $path . "djpeg";
$pnmscale = $path . "pnmscale";
$pnmmargin = $path . "pnmmargin";
$cjpeg = $path."cjpeg";
$cmd = " $djpeg $file_src | $pnmscale -xysize 50 50 | $pnmmargin -black 1 | $cjpeg > $thumb_src";
$out = system($cmd,$err);
```