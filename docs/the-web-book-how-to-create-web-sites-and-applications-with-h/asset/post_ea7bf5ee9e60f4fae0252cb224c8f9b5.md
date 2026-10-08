
## Image Maps

On page 84 we saw how to add a picture, or image, to a Web page using the `<img>` tag. In the same chapter, we saw how images can also be used as hyperlinks, so that a visitor to your site can click on an image, just like some text, to be taken to another part of the Web.

Now that you know about images and links, we can introduce another, advanced feature of HTML which is known as an image map. This allows you to divide an image into a number of separate areas, and specify a different link destination for each area.

For example, let’s say that you are creating a web site that offers various items of clothing for sale. You place a picture on your home page that shows someone dressed in shoes, trousers, t-shirt, scarf and hat. You want to allow your visitors to click on part of the picture and be taken to different pages of your web site, namely shoes.html, trousers.html, tshirts.html, scarves.html or hats.html.

You might think that achieving this feat involves loading the picture into an image editing program and dividing it into five separate files, but actually you’d be wrong. The picture can remain intact. What you need to create is an Image Map, which is a special collection of data items which specify the boundary co-ordinates of each clickable area of the image, as well as details of the link destination. For example, "if someone clicks within the square that starts in the top left-hand corner and whose lower right hand corner is 38 pixels down and 29 pixels across, take them to trousers.html".

You then include this image map data within the HTML code of your Web page, and the image can now be clicked in different areas for different results.

Unfortunately Amaya can't create image maps, but there are a few free programs on the internet that can. One such program is called Handly Image Mapper. There's a link on [http://silveragesoftware.com/handytools.html](http://silveragesoftware.com/handytools.html) which allows you to download it, and the good news is that, like all of the software mentioned in this book, it's free.

Once you've download the file and installed it, you can run it. Start by clicking on its folder icon to open one of your pictures. Then click on the shapes to define areas of the screen, and enter the URLs that correspond to the intended web destinations. When you're finished, click the Place On Clipboard button, which creates the map data and copies it to the Windows clipboard. You can then paste it into your web page.

The HTML code for using an image map looks like this:

```
<IMG SRC="computer.jpg" USEMAP="#computer">
```

As you can see, it's all pretty straightforward. Add a USEMAP parameter to the `<img>` tag, which names the image map to be used. Then place the map data somewhere on the page between a `<map>` tag and a `</map>` tag. The map data can simply be pasted from the clipboard, having been generated with Handy Image Mapper as described above.

Here's how Handy Image Mapper looks during use, once you've loaded a picture:

![](img/50e1558b8202f19b96c1cc386ea5ec66_111_0.png)

In this example, I’ve loaded computer.jpg and, using the controls at the top of the right-hand column, created a square area that links to screen.html and a round area that links to mouse.html.

With this done, I can paste the map data into Amaya. The map data, in case you’re interested, consists of:

```
<MAP NAME="map1">
<AREA SHAPE="RECT" COORDS="25,8,51,52" HREF="screen.html" TITLE="">
<AREA SHAPE="CIRCLE" COORDS="69,104,16" HREF="mouse.html" TITLE="">
</MAP>
```

Obviously you’ll need to change the name from map1 to match whatever you have specified in the picture’s `<img>` tag.

## Password-Protecting your Web Pages

Most web sites are openly available to anyone who knows, or finds, the URL. Most of the time, that's the way you want it to be. But occasionally you will want to password-protect some or all of your pages. For example, if you run the web site for a club or a school, you'll want to restrict certain areas to members or students only. Or perhaps your site contains information that has a value, such as documents or pictures, and you need to ensure that it's only viewable to your paying customers.

Password-protecting one or more areas on your web site is actually a fairly easy task to accomplish, because there's a facility built into most web servers. You don't even need to do any programming.

The key to protecting your pages in this way is to know about two special text files called .htaccess and .htpasswd. The first file, .htaccess, contains some special commands for the web server which basically say “please don't show anyone the pages in this folder unless they enter a correct username and password. And here is where you'll find the list of usernames and passwords”. As you've probably guessed, the second file, .htpasswd, contains the actual list of usernames and passwords. All that you need to do in order to protect your site, therefore, is to create these two files and then use your FTP program to upload them to the web server.

Almost all web servers support this feature. If you're not sure whether yours does, you've nothing to lose by trying. If your web browser pops up a username and password box at the appropriate point, you're in business. If it doesn't, and simply shows you the pages without asking you to log in, it's back to square one. Or you need to ask your hosting company to enable the facility, as some of them don't turn it on by default.

The remainder of this chapter shows you how to create the .htaccess and .htpasswd files. Note, by the way, the dot at the front of the filename. You're probably used to seeing dots in filenames, such as letter.doc or finances.xls, but these two files are special as there's nothing before the dot. Web servers generally won't object to filenames in this format, but some desktop computers might. If yours does, and you have trouble creating files with these weird names, just call them something a little less weird when you first create them on your PC. Then, once they've uploaded to the web server, use your FTP program to rename the uploaded versions in situ.

## The .htaccess File

The .htaccess file is used to provide special instructions to a web server. It can be used for many purposes. For example, you can use a .htaccess file to customise the error messages
