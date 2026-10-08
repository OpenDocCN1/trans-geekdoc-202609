# Interacting with the File System and the Server

In Chapter 2, “Storing and Retrieving Data,” you saw how to read data from and write data to files on the web server. This chapter covers other PHP functions that enable you to interact with the file system on the web server.

Key topics covered in this chapter include

+   - Uploading files with PHP
- Using directory functions
- Interacting with files on the server
- Executing programs on the server
- Using server environment variables

To discuss the uses of these functions, we look at an example. Consider a situation in which you would like to be able to upload images to be included in a website’s content (or maybe you want a friendlier interface than FTP or SCP for yourself). One approach is to upload the files directly through a form on your site, perhaps one that is locked down to administrator access only. Once those files are uploaded, you can use them however you fit.

Before we dive into the file system functions, let’s briefly look at how file upload works.

# Uploading Files

One useful piece of PHP functionality is support for uploading files. Instead of files coming from the server to the browser using HTTP, they go in the opposite direction—that is, from the browser to the server. Usually, you implement this configuration with an HTML form interface. The one used in this example is shown in Figure 17.1.