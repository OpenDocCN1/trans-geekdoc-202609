# Importing and masking a JPG

When I think back to why I thought of making this drawing app, I suppose the new JPG loading functionality of MX inspired me. Although I think the ability to load JPGs on the fly makes Flash MX ‘mature’, the way that it works with them leaves a lot to be desired. Of all the functionality of the application, the JPG took the most testing – at times the head was banging against the wall.....

# Load JPG tool

![](bbox=[0.197, 0.278, 0.257, 0.326])

![](bbox=[0.065, 0.346, 0.455, 0.655])

![](bbox=[0.065, 0.666, 0.455, 0.976])

There isn’t much to this tool on the face of things, but a great deal goes on here.

# Issues with dynamic image loading

Before we get onto the code for the load JPG tool, it’s worth looking at some of the issues with the dynamic image loading.

+   1. Flash MX will only load non-progressive JPGs.

That’s right, Flash refuses to work with progressive JPGs – it will load them but not display them – and any other standard image formats such as GIF or PNG.

I know the reason behind this is down to the size of the Flash 6 plugin. The more formats supported, the bigger the plugin, and it is Macromedia’s intention to keep it small. Great for the consumer, a little disappointing for Flash developers.

A way of getting around this is by using a server-side script to process the inputted JPG and re-export it as a non-progressive JPG image. This might involve some copyright issues though as you will have to fetch the image from the original URL location and place it on your server.

+   2. Flash MX dynamic JPG loading seems to have issues with browser cache.

During the testing phase of the application, I noticed that Flash seems to sometimes refuse to load JPGs when embedded in a browser.

Even though Flash’s Test Movie mode and the Flash Player seem to work fine, when the Flash SWF is embedded in HTML and run in Internet Explorer, it seems to load one image and then refuses to load another image afterwards. Netscape seemed to work fine in tests though.

I think this might be down to a problem caused by Internet Explorer’s caching system, and the fact that you can’t turn off caching on a PC. The reason I say this is because I tested the SWF on Mac IE 5 with the cache set to 0MB, and the whole thing worked fine, any higher and the issue returns.