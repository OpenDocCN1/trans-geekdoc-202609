
password, just to make sure that the security is working properly. Performing such a test each time you install any new product on your server is always a good idea.

Once you're logged in, you'll see this screen:

![](img/50e1558b8202f19b96c1cc386ea5ec66_158_0.png)

Click the Browse button and navigate to an image file on your computer. Add a caption and a description (this is important, as you'll see later). Then choose which album you want to add your picture to. You'll probably want to create a new one rather than putting it in the test collection.

When everything's ready, click the Upload button and wait for the message that says your upload was successful.

When it's done, log out and surf to the public part of your site rather than the admin section. You should see your gallery displayed. To check that Plogger is correctly storing information in your MySQL database, use the search box. Just type a word or two from the caption or description, and check that Plogger finds your picture.

![](img/50e1558b8202f19b96c1cc386ea5ec66_159_0.png)

With everything working properly, you can now proceed to make your site look as you want it to. Log into the admin section again and explore the various features that are available.

## Avoiding Data Overload

When you sign up for a web hosting package, your account comes with a certain amount of disk space on the server to store your information. If you’re storing mostly text, you don’t need to worry about hitting your limit. But if you intend to store lots (as in, thousands) of pictures, be aware that they eat server space like nothing else. Especially if they are high-resolution multi-megapixel images, which can typically occupy up 10 MB each.

If you think this might be a problem for you, check the small print of your web hosting package to find out just how much server space you get. Remember, too, that people who view or download your pictures will use up your bandwidth allocation, so you may want to check that as well. For example, if you have a 10 MB picture on your site and 100 people download it, that’s 1 GB of bandwidth traffic from your server.

Equally, if you upload 100 pictures to your gallery, at 10 MB each, that’s 1 GB of traffic from your own broadband connection. Which, if you are paying for a broadband service that only allows you 2 GB a month, is a fairly large chunk. If this is the case, check whether your ISP allows free uploads overnight that don't count towards your monthly limit. If so, upload the pictures then, or downsample them (reduce their resolution and thus the size of the files) before uploading them.

### Installing the PSPad Editor

While Amaya is great for editing HTML files, it's not so good if you're writing JavaScript or PHP. The solution comes in the form of an excellent program called PSPad. It's a text editor with two features that make it ideal for writing programs. First, it understands the syntax of JavaScript and PHP, so it can alert you if you make a mistake. Second, it has a built-in FTP facility, thus making it easy to upload your programs to the web server if you need to do so. And like everything else we've used throughout this book, it's downloadable free of charge.

The following chapters cover how to write programs in JavaScript and PHP so, if you intend to follow them, you need to install PSPad now.

To obtain the program, visit **www.PSPad.com** and download the full installer. This will copy a small (only 4 MB or so) .EXE file to your computer. Double-click that file to begin the installation, accepting all of the default options (though you'll probably want to reject the offer of additional language support unless you really do want to have the option of seeing the PSPad menus in Indonesian and other non-English tongues). With the program installed, you should now see a PSPad icon on your desktop.

Double-click the PSPad icon to start the program, if it's not already started automatically after being installed. You'll see the main screen, which looks like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_162_0.png)

We now need to configure the program before we can use it. Mainly, this means setting up the FTP details so that PSPad knows how to copy files from our PC to the web server. First, though, you can turn off that confusing menu of assorted icons at the top of the screen, as you don't need them. To do this, just press the F2 key.

Now to configure the FTP site of things. Click the FTP tab on the left hand side of the screen, to get to PSPad's FTP facility:

![](img/50e1558b8202f19b96c1cc386ea5ec66_162_1.png)

Then click the connection icon:

![](img/50e1558b8202f19b96c1cc386ea5ec66_163_0.png)

A dialogue box will appear, into which you can enter the details of your FTP connection to the server. This is very similar to the process that we went through right at the start of this book, for configuring FileZilla.

![](img/50e1558b8202f19b96c1cc386ea5ec66_163_1.png)

For the Connection Name, just choose a name for this connection. This is purely for your benefit so that, if you configure PSPad to connect to multiple servers, you can choose one from a list. I'll call mine The Web Book.

Following the server-specific examples as per the earlier examples in this book, for the site at the-web-book.com which is hosted by hostmonster, the required details are the-web-book.com for the server, thewebbo for the username, and the password that I normally use for connecting to my web hosting space.

Enter just a `/` symbol for the remote directory. Leave everything else as it is, and press the OK button to finish. You'll return to a list of options that shows your list of available connections (just the one so far, namely the one you just created) and some buttons. Click the top button, labelled Connect, to connect to your web server. Assuming it works, you should see something like this, with the contents of your server listed down the left hand side.

![](img/50e1558b8202f19b96c1cc386ea5ec66_164_0.png)

That's all you need to do for now. With everything working, you can exit PSPad for the moment.

## Javascript

HTML is a very full-featured language. When coupled with CSS, it’s capable of producing just about every design of web page you could ever desire. But HTML is only a markup language, for specifying how pages should look. Which is just fine if you intend your web site to act as an electronic version of a newspaper, magazine, book or brochure. But sometimes you’ll want to create web sites that exploit the power of computers, including features that go above and beyond the capabilities of electronic publishing. For example animation, online databases, and so on.

To add such features to our sites, we need to leave the safe environment of HTML markup and enter the world of web-based programming. Once you know how to write programs, just about anything becomes possible.

The following chapters explain the basics of web programming using Javascript and PHP. I’ll show you how to create basic web applications (often known as Web 2.0 sites) using Javascript and PHP. But be aware that this is a complex subject which takes a couple of years to master, and this is best done by practising rather than reading. So now might be a good time to think of a Web 2.0 application that you’ve always wanted to write, in order that you can apply what you’re about to read to a real situation.

## Choose Your Side

There are two ways to write web-based programs, and understanding the difference between them is vital because each method is used for specific purposes. As a reminder, the following explanations use the term "visitor" to describe a person who visits your web site, ie who views it online by using a web browser such as Internet Explorer or Firefox.

The first programming method is called client-side programming. This means writing programs that will run on the visitor’s computer, within their web browser. Just about all modern web browsers support this, via a programming language called JavaScript. To write a JavaScript program, you include it within the body of a web page along with the HTML code. Note that JavaScript is not the same as Java, and you should never refer to it as such.

The second programming method is called server-side programming. Here, you write programs that run on the web server. The browser never gets to see the program code. It merely sees the results, which normally consist of HTML code that is sent to it. The fact that this code was generated by a program running on the server, rather than being stored in a pre-written .html file, is unknown to the browser. The most common languages for writing server-side programs are PHP, Perl, Python, Ruby and Java, as well as Microsoft’s proprietary languages ASP and ASP.NET.
