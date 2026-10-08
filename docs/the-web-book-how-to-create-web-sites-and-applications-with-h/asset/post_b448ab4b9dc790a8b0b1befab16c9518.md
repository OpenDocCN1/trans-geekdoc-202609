
web-based applications, including those that work in the same way as Facebook and all the other Web 2.0 sites mentioned above.

But if you want to create a Web 2.0 site that performs a common function, such as a blog, or a discussion forum, or a simple web site, or a picture gallery, then here’s the good news. There are lots of ready-made open source applications. Just install one or more of them on your hosting space and you’re ready to roll.

A Web 2.0 application that performs the basic functions of creating and maintaining a standard web site is known as a Content Management System, or CMS. Sometimes the term used is WCMS, or Web Content Management System. As I said, we’ll leave the precise details, including how to write one using PHP and MySQL, until later. For now, let me show you just how useful the existing, free, ready-made applications are, and how easy they are to get up and running.

Note that this chapter isn’t an in-depth tutorial on how to use the products mentioned. If you decide that any or all of them would be a useful addition to your site, use what follows as a starting point and then search online for documents and forums that help you get your system working (and properly secured) the way you want.

For the purposes of this chapter we’re going to install and configure 4 different products:

- Joomla - One of the leading free WCMS products
- Wordpress - Another leading CMS, especially good for blog sites
- phpBB - A discussion forum
- Plogger - A picture gallery

There are, of course, many other free, open source web applications in addition to those detailed here. There are literally hundreds available, in many other categories. If you want to sell things via your web site, for example, there’s a free e-commerce suite called oscommerce. If you want to set up your own version of wikipedia, there are dozens of free wiki applications available. One great place to find Web software is www.hotscripts.com, which offers ready-made applications in a number of categories. Here’s just one part of one of their menu screens, showing the huge number of programs available, all for free.

![](img/50e1558b8202f19b96c1cc386ea5ec66_119_0.png)

## CMSes and Templates

CMS products like Joomla and WordPress are template-based. You start with a basic template, or page layout, which contains common elements such as a logo, the site's title, the page footer and so on. The template also contains markers (called placeholders) to indicate where the unique content for each page should be inserted. For example, the main heading, the intro paragraph, the main body text, the name of the author, and so on.

Key to using a CMS is to create a template. Thankfully, there are lots of free ones available, which can change the look of your site instantly. But if you don't like any of the standard templates, you can edit the existing ones or design your own from scratch. Any HTML page can be turned into a CMS template — it's just a case of looking through the CMS documentation for details on how to insert those special markers at the point where you want each page's content to appear.

If you like designing HTML pages, perhaps to be used as CMS templates, one product that deserves a mention is Xara Web Designer. It's not free, but is only around £39 or $60. It contains more than 700 ready-made page templates, easily adaptable for use with any CMS, and it’s incredibly easy to use. It allows you to do things that no other HTML editor does. For example, here’s one of the program’s standard designs:

![](img/50e1558b8202f19b96c1cc386ea5ec66_120_0.png)

Now, just type over any of the text or buttons in order to customise the page. Or click one of the coloured diamonds to change the entire colour scheme. You can also click on any object (a paragraph, a picture, a button etc) and, with your mouse, move it, enlarge it, or rotate it, just like any PC-based drawing program. When you’re done, just save the file and you’ve got yourself an HTML page which can be used as-is on a site or converted to a CMS template.

Also, if you’re using Joomla or Wordpress, check out a commercial product called Artisteer, which makes it easy to create great-looking template files. You can read more, and see a demo video, at [www.artisteer.com](http://www.artisteer.com).

## Automatic Installers

In the chapters that follow, I’ll show you how to obtain, install and configure Joomla, Wordpress, phpBB, and Plogger. But before you read these sections in detail, check whether your web host offers you the use of an automatic installer such as Fantastico or SimpleScripts. If so, then your life just got even easier. These systems let you install many of the leading free web applications in seconds, with just a single click.

To sign up with the web hosting company featured in this book, please visit [www.the-web-book.com/hosts.html](http://www.the-web-book.com/hosts.html). It costs you just the same, but brings me a small commission that funds the development of this book. Thanks!

If the facility is available, and if you want to go down the easy route rather than learning how to install and configure the programs from scratch, then it makes good sense to use it. Just check on your web hosting control panel to see if the feature is available.

As an example, here’s the main SimpleScripts menu, which shows all of the applications that it can install. You can then install any of them into your hosting space with just one click, and be up and running in just seconds:

![](img/50e1558b8202f19b96c1cc386ea5ec66_121_0.png)

## Try Before You Install

To sign up with the web hosting company featured in this book, please visit www.the-web-book.com/hosts.html. It costs you just the same, but brings me a small commission that funds the development of this book. Thanks!

Although it's easy to install applications into your hosting space, and even more so if you use SimpleScripts or Fantastico, the process still takes time. Plus, if you don't like the application, you have to spend more time uninstalling it. The best way round this is to find a site that already has a copy of the application installed, and which allows you to log into it and use it for test purposes. Then, when you know it's what you want, you can set up your own copy in your own hosting space.

My favourite online resource for testing open source Web applications in this way is www.opensourcecms.com. Despite the name, it doesn't just cover CMSes. It also includes forums, wikis, and more. The site is completely free to use, and offers links to installed demo copies of dozens of products. You even get supplied with the admin passwords, so you can experience the installed product as an owner rather than just a user. Which means, for example, that you can create new pages on the CMS rather than just reading what's already there.

For obvious security reasons, a few features are automatically disabled, such as sending email or changing the admin password. Also, the entire system is automatically deleted and reinstalled every couple of hours so any malicious content won't be around for long. But opensourcecms.com should definitely be your first port of call if you're considering installing such a product into your hosting space.

If the product you want to install isn't listed on opensourcecms.com, all is not lost. Check out the product's home site on the Web. Many offer a test version that you can log into (look for a Demo or Online Demo link), and this often includes the admin passwords so you can check out the management facilities too.

## A Word about Patching

The key to security on any Windows PC is to ensure that automatic updates are enabled. Microsoft issues around 100 security fixes each year for Windows, many of which are for bugs that are so serious they could allow everyone in the world to access your files via the internet. By ensuring that these patches are downloaded and installed automatically, you prevent your PC from serious attack.

But Windows is not unique. Every program has security bugs, and every team of developers issues regular security patches for its products. The people who develop products such as Joomla, phpBB, and all of the other web-based software mentioned here, are no exception. The difference between Windows and these products, however, is that there's no Automatic Updates feature. Therefore, if you install a product on your Web server, it's vitally important that you check the product's web site every couple of months to find out whether any important security updates have been issued. If they have, you'll need to download them and
