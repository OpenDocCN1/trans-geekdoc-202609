
and downloads where we need to transfer a directory and its subdirectories from one system to another.

The following code, for example, connects to a remote directory on an FTP server and copies the contents, including subdirectories, to a directory on the local computer¹:

```php
<?php
// Set time limit to infinite
set_time_limit(0);

// Include PEAR::Net_FTP
require_once 'Net/FTP.php';

// Define server, username and password
$ftpServer = 'ftp.uselinux.org';
$ftpUser = 'anonymous';
$ftpPass = 'user@domain.com';

// Local Directory to place files
$localDir = 'ftpdownloads/';

// Remote Directory to fetch files from
$remoteDir = '/pub/software/web/html-utils/';

// Instantiate Net_FTP
$ftp = new Net_FTP();

// Set host and login details
$ftp->setHostname($ftpServer);
$ftp->setUsername($ftpUser);
$ftp->setPassword($ftpPass);

// Connect and login
$ftp->connect();
$ftp->login();

// Specify the extensions file
$ftp->getExtensionsFile('extensions.ini');

// Get the remote directory contents
if ($ftp->getRecursive($remoteDir, $localDir)) {
    echo 'Files transferred successfully';
} else {
    echo 'Transfer failed';
}
?>
```

¹Obviously, this isn't something you would want to place on your Website without some security protecting it.

Note that the getExtensionsFile method of Net_FTP allows you to specify a file that defines particular file extensions, such as .gif and .jpg, as binary or ASCII, ensuring that they will be transferred in the correct manner. The getRecursive method fetches the contents of the specified remote directory, including its subdirectories.

Assuming you have permission to place files on the server, the same operation can easily be applied in reverse using the putRecursive method. This can prove a helpful tool for transferring projects between your local development system and your Website, particularly if you're using PHP from the command line.

With the ability to transfer files correctly based on their extension, Net_FTP makes an excellent choice for individual “put” and “get” file operations as well, as it eliminates the need for you to get the file transfer mode correct.

## How do I manage file downloads with PHP?

A fairly common problem developers face in building sites that will publish files for download, is how to manage those files. Perhaps some of the files should not be publicly available. You may also only want to deliver the file after visitors have provided their details through a Web form. Dealing with downloads may involve more than simply storing your file in a public directory and linking to it from your site.

The trick to handling downloads is to get PHP to “serve” the file for you, using a few special HTTP headers:

```php
<?php
// Specify a file to download
$fileName = 'sample.zip';
$mimeType = 'application/zip';
if (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE 5') or
    strpos($_SERVER['HTTP_USER_AGENT'], 'Opera 7'])) {
    $mimeType = 'application/x-download';
}
// Tell the browser it's a file for downloading
header('content-disposition: attachment; filename=' . $fileName);
header('content-type: ' . $mimeType);
header('content-length: ' . filesize($fileName));

// Display the file
readfile($fileName);
?>
```

The content-disposition header tells the browser to treat the file as a download (i.e. not to display it in the browser window), and gives it the name of the file. The content-type header also tells the browser what type of file you’re sending it. In most cases, this should be chosen to match the type of file you are sending; however, Internet Explorer 5 and Opera browsers have a bad habit of displaying files of recognized types in the browser regardless of the content-disposition header, so we set the MIME type to the made-up value application/x-download for those browsers. Finally, the content-length header tells the browser the size of the file, so that it’s able to display a download progress bar.

## Send HTTP Headers First

Remember that headers must be delivered before any other content is sent to the browser.

Be aware that PHP’s output control functions can be helpful here, as they let you send things to the browser in the right order: you can “hold” content already sent to output by PHP while letting the headers pass. See Volume II, Chapter 5 for further details on output control.

Now that delivery of the file is under your control, you can fit this functionality into your authentication system, for example, to control who can download the file.

## File Distribution Strategy

One of the Internet’s unsolvable problems is how best to distribute files from a Website. If you sell artwork in JPEG format, for example, how will you handle the process of accepting payments from customers and then letting them download only the image they paid for? How can you make sure they don’t redistribute the images they buy? How many times will customers be allowed to download an image they’ve paid for?

There’s no perfect solution. What if people decide to make copies of the images they bought from you and redistribute those copies without your knowing? It’s almost impossible to prevent them doing so unless you provide files that have been modified especially for the purpose of distribution (for example, image files protected by watermarks).

Some of the different strategies for distribution are as follows:

- [ ] Send the file via email. This is good for small files as it practically guarantees delivery, but many email systems place a limit on the size of files a user can receive (typically one or two megabytes).

- [ ] Provide customers with a unique link that they can use to download the file for a limited time period, such as a week. If an attempted download fails (for example, the customers lose their Internet connection during the download) this strategy allows them to try again. A unique, random number can be generated and used in the URL for the download. This number corresponds with an entry in a database, which expires after a specified time period. This will at least limit the number of times the file is downloaded, and should help prevent redistribution of the file via the same URL. This approach is used by PayPal Antifraud[8], among others.

- [ ] Provide customers with user name and password combinations that they can use to log into the site and download their own files. This approach has proven particularly effective for the PHP Architect[9] site, where it’s used to distribute the PHP Architect magazine in Adobe Acrobat format. The Acrobat files are generated “on the fly”, and secured with the same password the customer used to log in to the site. This obviously discourages customers from redistributing the magazine, as they’d have to give away their password to do so.

As I said, there’s no perfect solution to this problem. However, greater protection can be achieved if some form of security is built into the file that’s being downloaded, such as a license key in the case of software.

## How do I create compressed ZIP/TAR files with PHP?

Perhaps you have a directory that contains many files, or different types of files, as well as subdirectories. There may well be situations in which you need to create a download of the whole directory that preserves its original structure. The typical command line approach to achieving this on Unix-based systems is first to create an “archive” file such as a .tar file (.tar files are “Tape Archives” and were originally conceived to help back up a file system onto tape), and then compress that file with gzip or bzip2. If you had a directory called mywork that you wanted to store as a single compressed file, you might enter the following into the command line:

```
tar cvf mywork.tar ./mywork
gzip mywork.tar
```

This gives you a file called mywork.tar.gz. To unzip and extract the file you could type:

```
gunzip mywork.tar.gz
tar xvf mywork.tar
```

This recreates the mywork directory below your current working directory. Note that you can perform the above examples in a single line on a typical Linux distribution, if you use the ’z’ flag to compress tar zcvf mywork.tar.gz ./mywork and extract tar zxvf mywork.tar.gz.

Using PHP's system function, you could execute these commands from a PHP script, assuming your Web server has permissions to use the tar and gzip/bzip2 executables (which it probably won’t). How would you create archives from data stored in your database, or from nodes in an XML document for that matter?

Thanks to PEAR::Archive_Tar[10], it’s all possible. The basic functionality allows you to build .tar files; provided you have the zlib or bz2 extensions installed, you can also compress the file.

Let’s create an archive from some of the files we were working with earlier in the chapter:

[10] http://pear.php.net/Archive_Tar
