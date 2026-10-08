```
?>
```

Open your web browser and surf to **www.yoursite.com/custlist.php** and you should see the following:

![](bbox=[0.135, 0.236, 0.874, 0.611])

For simplicity, I haven't generated <HTML>, <body> and <p> tags. Technically, therefore, the HTML page is not valid code. However, it keeps things simple for now, and just about every browser will allow it. When you come to develop real applications, make sure that you generate valid HTML pages which contain all the necessary tags.

Let's look at this code in detail.

The first 6 lines are used to connect to your database. You need to ensure that these lines are present at the start of every PHP program you write, if you intend to access a database. The first 4 lines are where you specify the hostname, database name, username and password (use the same password and username that you use for accessing phpMyAdmin or your web hosting control panel). The hostname will probably be “localhost” unless your web hosting provider stores its databases on a server other than the web server. If this is the case, you