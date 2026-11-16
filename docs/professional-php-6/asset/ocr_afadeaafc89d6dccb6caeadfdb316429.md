The final line makes requests to / (for example, http://www.example.com/) direct to the “starting” servlet for your application — normally called Home.

# Working with Ulysses

With Ulysses installed on your Web server, it’s available to all of your PHP projects from this point on — you don’t have to install it ever again. It’s now time to start making use of the code base it has to offer.

Create a project folder for your example application. In the virtual host example cited earlier, you’ve used /home/ed/public_html/newsletter — so just create a folder that matches the virtual host you’ve created for your application.

Although Ulysses doesn’t enforce an especially rigid directory structure, there are a few folders you must create:

+   /your/web/root/tpl
+   /your/web/root/phpm
+   /your/web/root/phpm/business
+   /your/web/root/phpm/utility
+   /your/web/root/phpm/controls
+   /your/web/root/phpm/custom
+   /your/web/root/phpm/settings

Any other folders you might create (for images, CSS stylesheets, JavaScript, and so forth) are entirely up to you.

However, keep in mind the following:

+   - [ ] You must place your page templates (which normally contain HTML) under tpl.
+   - [ ] You must place your business objects under phpm/business, and utility classes under phpm/utility.
+   - [ ] You must place your application settings under phpm/settings.

Keep to these simple rules and you should be fine.

# Setting Up

There are a few files you’ll need to create under phpm/settings. These define the root database for your application (although you can define as many as you want), and the directory location in which the in-built session class will save its sessions.

Create phpm/settings/constants.phpm as shown here:

```
<\?
define("BASE_SESSION_PATH", "/tmp");
\?>
```