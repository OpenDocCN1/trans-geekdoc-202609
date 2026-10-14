
Now that we know the issue, it’s much easier to solve. We need to speed up `flock` (or avoid it all together) so that the during a deploy, we don’t have 256 PHP-FPM workers all competing on trying to update the same files. There are a couple of different ways to do solve this problem, and I’ll quickly cover which one I used (and the ones that failed).

#### Screw files, use Memcache!

My first reaction was to just use Memcache. Remember earlier we talked about the pluggable backend for the CakePHP system cache? Well one of the backends is Memcache, so screw it, let’s just use that. I modified the configuration, plugged in my memcache server details, and it all seemed to work. But, curiosity got the best of me, and I wondered how much extra traffic this was adding to the Memcached server.

So I removed the change, and used `ifstat` to get a baseline for network traffic on this app server…

```
1 $ ifstat -i eth0
2 KB/s in  KB/s out
3 3154.15  2660.01
4 3003.02  2561.97
```

Ok, about 3MB/s in and out. Next, I re-enabled the memcached backend in CakePHP and checked again.

```
1 $ ifstat -i eth0
2 KB/s in  KB/s out
3 41931.34 33154.11
4 39129.12 31929.23
```

Oh wow, we added almost 40MB/s of traffic to and from our memcache server by using it for the CakePHP system cache. FOR ONE SERVER. Multiply it across all of our app servers and wow, it quickly becomes unsustainable. The CakePHP cache is only a couple of kilobytes but it needs to read it out and write back out the full contents for each request. Bummer, memcached isn’t go to work for this.

#### APCu, the userland cache for PHP 5.5

Next up, I found [APCu](http://pecl.php.net/package/APCu), the userland part of APC reimplemented for PHP 5.5. I tested this, and while it worked just fine, it felt dirty to me. This is a beta-level package, without much history or testing, and who knows if it will continously be updated to work with PHP 5.6, 5.7, and so on. Might as well make the clean cut instead of hacking the functionality back in with a legacy module. I will say this— out of all the solutions, this was probably the easiest and most straightforward. APC worked great for this solution in PHP 5.3 and 5.4.

#### An independent cache for each PHP-FPM worker

I had to wake up at 4:45AM on a Saturday morning to catch a flight to San Francisco. As I was flossing in my bathroom, it hit me in the face. Instead of relying on a *global* CakePHP system cache for all 256 of my PHP-FPM workers, why don’t I have a unique file cache per-worker? This will get rid of the competition for the file lock, since each worker is single threaded and can only serve one web request at a time.

It gets even easier— it would only require one change:

```
1 <?php
2 // Old Configuration
3 Cache::config('_cake_core_', array('prefix' => 'cake_core'));
4 
5 // New Configuration
6 Cache::config('_cake_core_', array('prefix' => getmypid() . 'cake_core'));
```

All we did was add `getmypid()` to the filename of the CakePHP framework cache— since each PHP-FPM worker runs as a child processes and has its own process id, each PHP-FPM worker gets its own unique cache.

The best ideas come when you’re flossing.

I was excited to land on the west coast and test my theory. Within minutes of landing, I tested my theory, and it worked. Except for a small problem. When I checked filesystem usage with `iostat`, I was saturating the disks! It was too much load on the disk to have 256 independent PHP-FPM caches! Blah!

```
1 $ iostat /dev/xvdb -x 1
2 Device:         rrqm/s   wrqm/s     r/s     w/s      svctm  %util
3 xvdb            1273.00  893.00     1263.00 893.00   1.21   100.00
```

Instead of going back to the drawing board AGAIN, I just iterated on this solution. The cache files were pretty small, less than 50KB each, so even with 256 independent caches we are only talking about 15MB or so— it’s just getting read and re-written several thousand times per second.

I created an in-memory filesystem with `tmpfs` and mounted it in the location of my cache directory— giving CakePHP the *illusion* of using the filesysem, while really storing the cache in memory. This solved all of the problems and was ultimately the solution I used.

```
1 $ mount -t tmpfs -o size=1000M,mode=0755 tmpfs /tmp/cache
```

What a ride it was. I hope this case study showed you some real-world debugging, reasons to floss your teeth, and why at scale, sometimes even the obvious solutions don’t always go as planned :)

## Case Study: Optimizing image handling in PHP

As you can probably imagine, resizing images is a huge part of the workload that our systems spend time on at Twitpic. With the 8MP camera in an iPhone 5 (and up to 13MP in some of the newer Android phones), even mobile users are capable of snapping and uploading pictures that easily exceed 10MB.

Almost anytime an image is uploaded by a user into a web application, it needs to be resized and post-processed for a few different reasons.

1.  Reduce the file size, sending a 10MB image to the browser is *not* a best practice :)

2.  Standardize on a dimension size. For Twitpic, it’s 600px wide

3.  Standardize on a particular image format (usually, but not always, JPEG)

4.  Generate multiple image versions (several thumbnails, retina versions)

5.  Rotate the image to align it with the orientation of the camera when it was taken

6.  Strip out EXIF, Camera Model, GPS Coordinates, and other sensitive information from headers

Processing images in your stack can be tricky, though, since post-processing and resizing tend to be CPU intensive and moving large files around consumes a noticeable amount of Disk I/O and Network Bandwidth.

### The naive “PHP Tutorial” way

If you look for information on basic image processing in PHP, you’ll almost exclusively find references telling you that you should be using [ImageMagick](http://www.imagemagick.org/script/index.php)— and for good reason! ImageMagick is a very robust, well-supported library can convert, resize, and modify almost any *any* image format. It’s like Adobe Photoshop™ for the command-line.

What does the naive, unoptimized image upload and resizing code look like with ImageMagick? The example below shows you some example code to receive a file upload, scale it to a 600px JPEG, and create a 150x150 thumbnail.

```
 1 <?php
 2 
 3 class Image_Controller extends Controller {
 4 
 5   // Image upload is posted to this method
 6   public function create() {
 7   
 8     if (isset($_FILES["upload"])) {
 9     
10     	$tmp = $_FILES["upload"]["tmp_file"];
11     
12         // Create the Scaled 600x400 Size
13         exec("convert -resize 600x400 {$tmp} /u/scaled.jpg");
14         
15         // Create the 150x150 Thumbnail
16         exec("convert -thumbnail x300 -resize 150x< -resize 50% 
17                       -gravity center -crop 150x150+0+0 +repage
18                       {$tmp} /u/thumbnail.jpg");
19                       
20         // Delete the temporary file  
21         @unlink($tmp);
22     }
23   }
24 }
```

Well, what’s so bad about this code? It’s just taking the raw image (from `$tmp`) and running some ImageMagick commands on it. Performance-wise, there are a handful of problems wrong with the code. Can you guess them?

1.  Image resizing is a CPU-heavy and slow process, especially on big images. If possible, resizing and post-processing should be moved to a Resque worker. Admittedly, in most scenarios the user expects the image to be resized and available immediately, so a background worker is not always possible. We’ll assume, for the rest of this case study, that using a Resque worker is not an option.
