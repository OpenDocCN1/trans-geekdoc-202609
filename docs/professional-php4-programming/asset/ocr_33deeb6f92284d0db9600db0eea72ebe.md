![](bbox=[0.103, 0.083, 0.875, 0.485])

Note that this message is directed to users surfing to your web site, and you are the person responsible for maintaining this server. I suppose you could send yourself an e-mail to say that you haven't finished building your web site, but it would be much more useful to actually build it, wouldn't it?

You can try adding a couple of HTML files to your document root directory. In the default setup, this is usually C:\Program Files\Apache Group\Apache\htdocs\. You should see an index.html document, which contains the HTML for the above displayed page.

Once you get the hang of adding files to your web server, you can change your document root to any directory you like by editing httpd.conf, which is by default in C:\Program Files\Apache Group\Apache\conf\httpd.conf:
DocumentRoot "C:/Apache/htdocs"

Make a backup copy before you edit, however, since a simple typo in httpd.conf can make your web server display 500 Internal Server Error in your browser. Also, you need to restart Apache for changes to take effect. Make sure of Apache after each edit to httpd.conf and check that the settings you changed actually work.

If you chose to install Apache in a different location, you'll find the httpd.conf file and htdocs directory in that location specified. Note that when you change DocumentRoot in httpd.conf, you must also change the <Directory>... setting below that to match.