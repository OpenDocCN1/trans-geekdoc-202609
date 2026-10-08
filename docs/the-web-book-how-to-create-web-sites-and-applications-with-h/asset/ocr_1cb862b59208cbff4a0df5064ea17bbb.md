![](bbox=[0.13, 0.1, 0.82, 0.4])

Note the references to **Local site** and **Remote site**. The former shows the files on your computer, while the latter shows files on the web server. Or at least, they will when we have configured the program.

From the File menu, choose Site Manager and then click the **New Site** button. Choose a name for the server you want to connect to, and press Return. Web Work is a suitable choice, or perhaps use the name of the site you intend to create. FTP programs allow you to create multiple connections like this, each with their own name, so that you can upload files to different servers (or different folders on the same server) if you wish.

Having named your connection, look under the General tab and enter the host name. That's FileZilla's term for the address of your web server. In this case, I'll use **theweb-book.com** because that's what the account information sent by the hosting company tells me to use. Change the Logon type to Normal and enter your server username (thewebbo in my case) and password.

Now click on the Advanced tab. In the Default Local Directory box, click the Browse button and select the Web Work folder you made earlier. For the default remote directory, just type a `/` (forward-slash) character.

That's all there is to it, so click the **OK** button. FileZilla is now configured to connect to our web server.

We can now test that it works so, from the File menu, choose Site Manager again. Click on the name of your server and then click the **Connect** button. After a few moments, you should