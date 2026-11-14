```
3 <head>
4 <title> <?php // Use a default page title if one wasn't provided...
5 if (isset($page_title)) {
6 echo $page_title;
7 } else {
8 echo 'Coffee - Wouldn\'t You Love a Cup Right Now?'; 
9 }
10 ?> </title>
11 <meta http-equiv="Content-Type" content="text/html;
\charset=utf-8" />
12 <meta name="description" content="Place your description here" />
13 <meta name="keywords" content="put, your, keyword, here" />
14 <meta name="author" content="Templates.com - website templates provider" />
15 <link href="/css/style.css" rel="stylesheet" type="text/css" />
16 <!--[if lt IE 7]>
17 <script type="text/javascript" src="/js/ie_png.js"></script>
18 <script type="text/javascript">
19 ie_png.fix('.png, .logo h1, .box .left-top-corner, .box
.right-top-corner, .box .left-bot-corner, .box .right-bot-corner,
.box .border-left, .box .border-right, .box .border-top, .box
.border-bot, .box 20 .inner, .special dd, #contacts-form input,
#contacts-form textarea');
20 </script>
21 <![endif]-->
22 </head>
23
24 <body id="page1">
25 <!-- header -->
26 <div id="header">
27 <div class="container">
28 <div class="wrapper">
29 <ul class="top-links">
30 <li><a href="/index.php" class="first"><img alt=""
src="/images/icon-home.gif" /></a></li>
31 <li><a href="/cart.php"><img alt=""
src="/images/icon-cart.gif" /></a></li>
32 <li><a href="/contact.php"><img alt=""
src="/images/icon-mail.gif" /></a></li>
33 <li><a href="/sitemap.php"><img alt=""
src="/images/icon-map.gif" /></a></li>
(continues on next page)
```