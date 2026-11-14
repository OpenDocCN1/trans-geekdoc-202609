then execute it directly. That's a two-step process. Protecting against such an attempt is also, therefore, a two-step process:

+   1. Do everything you can to prevent dangerous code from being placed on the server.

+   2. Make it difficult, if not impossible, to directly execute dynamically added content.

For the first step, it's largely a matter of validating uploaded content: making sure it's of an acceptable type. For the second step, the best solution is to store uploaded content in a directory outside the Web root directory. In such a case, if bad person Bob (on the Internet, not on your server) can trick your system into uploading some dangerous script, he still could not execute that script, as there would be no way to invoke it if it's not in the Web root directory.

tip
Ways to use the Web server to protect directories are discussed in Chapter 7, “Second Site: Structure and Design.”

If that's not possible (for example, some shared hosts don't allow you to put content above the Web directory), you should create a non-obvious folder within the Web directory. This folder will still require the open permissions, but you should password-protect the directory so that it's only available (over HTTP) to authorized users. You can do this using your Web host's control panel.

tip
In Chapter 3, “First Site: Structure and Design,” I talked about the server's organization and where the pdfs directory should ideally go.

Once you've created the pdfs directory with open permissions, and protected it appropriately if you had to place it in the Web root directory, you can create the PHP script that will upload a PDF file to that folder. But first, I would recommend creating another constant in the configuration file that is an absolute path to this folder:

tip
Change the value of PDFS_DIR so that it's correct for your server.

```
// In config.inc.php:
define('PDFS_DIR', BASE_URI . 'pdfs/');
```

# Creating the PHP Script

This PHP script has the same basic structure as all the other forms: The form is first displayed; the data is validated after the user submits the form; and the form is displayed again with its current values indicated should there be any errors. But this particular process will be trickier than the other forms in that it's also dealing with an uploaded file. The file input cannot be made sticky and, more importantly, the actual file on the server must be addressed when the form is being redisplayed because of other errors. I'll explain all the corresponding logic in the following steps.

+   1. Create a new PHP script in your text editor or IDE to be named add_pdf.php and stored in the Web root directory.