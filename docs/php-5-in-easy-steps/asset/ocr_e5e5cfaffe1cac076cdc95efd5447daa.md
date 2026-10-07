# PHP and mobile devices

PHP can be used to supply appropriate content to the emerging range of mobile devices that can access the Internet.

![](bbox=[0.315, 0.103, 0.513, 0.532])

Commonly these have much smaller display areas than a PC monitor, so large images are not suitable. Also they often have reduced capabilities and may not be able to read web pages correctly. For instance, the i-mode standard favored by NTT DoCoMo uses Compact HTML (cHTML), which has only some of the tags available in HTML.

The example below searches the HTTP_USER_AGENT environment variable to identify the browser. If it finds the Pixo micro-browser used on some mobile devices it will supply a small image. Otherwise a large image is supplied.:

```
<html><head><title>Welcome Page</title></head><body>
<?php $browser = $_SERVER['HTTP_USER_AGENT'];

if (preg_match("/Pixo/i", "$browser")) {
	$img = "<img src="small-tux.gif" width="64" height="75" alt="tux">";
} else {
	$img = "<img src="large-tux.gif" width="320" height="375" alt="tux">";
}
echo ($img);
?>

</body>
</html>
```

![](bbox=[0.198, 0.595, 0.283, 0.678])

Alternatively, PHP could redirect the micro-browser to a cHTML page containing content appropriate for the device.

![](bbox=[0.052, 0.753, 0.143, 0.843])