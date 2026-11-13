# Developing the PHP

At this point the ActionScript code is complete and you can focus on the PHP The ads.php file is made up of two global variables and a function.

The first global variable is the directory where the ad images are located. The second variable is the array containing the ad data.

```
$adImageDir = "./adImages/";
$bannerAds = array (
    array( 'Banner Name', 'randomimage1.jpg', 'http://localhost/' ),
    array( 'Banner Name', 'randomimage2.jpg', 'http://localhost/' ),
 );
```

The getBannerAd function assigns the two variables as globals so they are accessible within this function.

# Random selection

The single banner ad is chosen from the array by using a random key. This random key is generated using the mt_rand() function and the length of the $bannerAds array.

```
$random = (mt_rand() % count($bannerAds));
```

The XML file is built by outputting a single line of image data that ActionScript will process.

```
function getBannerAd()
{
    ...

    $xml .= " <banner id=\"" . 0 .
        \"" dir=\"" . $adImageDir .
        \"" url=\"" . $bannerAds[$random][2] .
        \"" name=\"" . $bannerAds[$random][0] .
        \"" src=\"" . $bannerAds[$random][1] . \"" />\n";

    $xml .= "</banners>";

    return $xml;
}

print getBannerAd();
```

The PHP responsible for loading the banner ad is now complete. As you can see, the amount of code needed to create this application is fairly small. This basic example can easily be extended to add in categories or even multiple images that transition as the movie sits on a browser.