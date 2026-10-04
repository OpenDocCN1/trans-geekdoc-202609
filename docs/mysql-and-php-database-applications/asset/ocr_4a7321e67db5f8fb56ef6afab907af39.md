# Chapter 10: Catalog 271

```
$thumb_src = $file_src."$thumb".$file_ext;
$file_src = $file_ext;
copy($this->imagefile, $file_src);
```

Now that we have a unique filename and the proper extension, we can put together filenames for both the main file and the thumbnail we're going to make. The source file is copied from its temporary home to the full path on the filesystem, as indicated in $file_src.

```
if ($file_ext == ".jpg")n{
$cmd = "../catalog/makeimagthumb $file_src $thumb_src $this-\nthumb_width";

$out = system($cmd,$err);
```

If the image is a jpg, we will call a shell script, using the system() function. Here is it:

```
#!/bin/sh
PATH=/usr/local/bin:/usr/new/pmbmplus:$PATH
export PATH
rm /$2
djpeg /$1 | pnmscale -xsize $3 $3 | pnmmargin -black 1 | cjpeg
/$2
```

This script will be passed strings ($file_src and $thumb_src), which are assigned to variables $1 and $2. The shell script first removes the existing thumbnail (if it exists), and then goes about creating a new one. djpeg converts the jpg to pbm format. The output of that is piped to pnmscale, which scales the picture to a 50x50 px image; the output of piped to pnmmargin adds a black border. Finally, the resulting image is redirected to a file, as indicated by $2 (or $thumb_src).

The previous script could have been kept in PHP. It could have been written like this:

![](bbox=[0.181, 0.703, 0.245, 0.755])

```
$path = "/path/to/pmbmplus/";
$djpeg = $path . "djpeg";n$pnmscale = $path . "pnmscale";n$pnmmargin = $path . "pnmmargin";n$cjpeg = $path . "cjpeg";n$cmd = "$djpeg $file_src | $pnmscale -xsize 50 50 |\npnmmargin -black 1 | $cjpeg > $thumb_src";
$out = system($cmd,$err);
```