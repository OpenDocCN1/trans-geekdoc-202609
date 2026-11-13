Adjust the paths and filenames as necessary, and then set up Task Scheduler to run `generateindex.bat` every hour (in some versions of Windows, you'll need to set up 24 tasks to be run daily at the appropriate times). Done!

Under Linux (or other UNIX-based platforms) you can do a similar thing with `cron` -- a program installed on just about every UNIX system out there that lets you define tasks to be run at regular intervals. Ask your friendly neighborhood Linux know-it-all, check your favorite Linux Web site, or post a message on the SitePoint.com Forums (www.sitepointforums.com) if you need any help getting started with `cron`.

The task you'll set up `cron` to run will be very similar to the Windows task discussed above. The stand-alone version of PHP you'll need, however, doesn't come with the PHP Apache loadable module we compiled way back in Chapter 1. You'll need to compile it separately from the same package we used to compile the Apache module. Instructions for this are provided with the package and on the PHP Web site (www.php.net), but feel free to post in the SitePoint.com Forums (www.sitepointforums.com) if you need help!

For experienced `cron` users in a hurry, here's what the line in your crontab file should look like:

```
0 0-23 * * * php /path/to/generateindex.php > /dev/null
```

# # Handling File Uploads

All of our examples of database-driven Web sites in this series so far have dealt with sites based around textual data. Jokes, articles, authors... all of these things can be fully represented with strings of text. But what if you ran, say, an online digital photo gallery where people could upload pictures taken with digital cameras? For this to work, we need to be able to let visitors to our site upload their photos and we need to be able to keep track of them.

We'll start with the basics: let's write an HTML form that allows users to upload files. HTML makes this quite easy with its `<input type="file">` tag. By default, however, only the name of the file selected by the user is sent. To have the file itself submitted with the form data, we need to add `enctype="multipart/form-data"` to the `<form>` tag:

```
<form action="fileupload.php" method="post"
 enctype="multipart/form-data">
<p>Select file to upload: <input type="file"
 name="uploadedfile" /></p>
<p><input type="submit" name="submit" value="Submit" />
</p>
</form>
```

As we can see, a PHP script (`fileupload.php`) will handle the data submitted with the form above. And, as you'd expect, a PHP variable named