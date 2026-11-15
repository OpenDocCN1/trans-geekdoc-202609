
```php
if (@file_put_contents(
	"compress.zlib://test.gz",
	file_get_contents("test.txt")
)) {
echo "GZ file written.<br />";
} else {
echo "Error writing the GZ file.<br />";
}
if (@file_put_contents(
	"compress.bzip2://test.bz2",
	file_get_contents("test.txt")
)) {
echo "BZ2 file written.<br />";
} else {
echo "Error writing the BZ2 file.<br />";
}
?>
```

Listing 26.7 A File Is Compressed ("zip-write.php")

However, if you run the script in Windows, you will get the result shown in Figure 26.7. The reason: The BZ2 filter is not available there (when using Unix/Linux, the filter works if the respective library is installed on the system). To change this, you must add the following option to `php.ini`:

```
extension=bz2
```

GZ also works without `php.ini` settings on all systems. In the test, the `test.txt` file could be reduced from 362 bytes to 84 bytes.

![](img/ae7820c36e8f24c1623d26668b28e80e_737_0.png)

Figure 26.7 Here gzip Works, but bzip2 Does Not (without Appropriate Configuration)

Incidentally, you can also read compressed files back in with the same stream type. The following listing shows the corresponding code.

```php
if (file_exists("test.gz")) {
    echo "<h1>test.gz</h1><pre>";
    echo htmlspecialchars(
        file_get_contents("compress.zlib://test.gz")
    );
    echo "</pre>";
}
if (file_exists("test.bz2")) {
    echo "<h1>test.bz2</h1><pre>";
    echo htmlspecialchars(
        file_get_contents("compress.bzip2://test.bz2")
    );
    echo "</pre>";
}
?>
```

Listing 26.8 The Compressed Files Are Read In ("zip-read.php")

You will receive the contents of both files (see Figure 26.8)—or, if Windows is not configured accordingly, only the data in the GZ file. Unix/Linux users will see both archives.

![](img/ae7820c36e8f24c1623d26668b28e80e_738_0.png)

Figure 26.8 The Content of the Files in the Web Browser

> **Note**
> You can also try to open the PHP source code archive with streams—for example, the `php-8.x.y.tar.gz` file. However, your system may then quickly reach its (memory) limits. In addition, the file it contains is a TAR file that you cannot easily edit with PHP’s onboard tools.

## The FTP Functions of PHP

If you want to use FTP-specific functions, you must configure FTP specifically for this under Unix/Linux; the `--enable-ftp` switch for configure takes care of this. You then have a range of special FTP functions at your disposal that conveniently encapsulate all FTP commands. The following listing provides an illustrative example.

```php
<?php
$connection = ftp_connect("ftp.mozilla.org");
$login = ftp_login($connection, "anonymous", "guest@xy.zzz");
if ($connect && $login) {
    if (ftp_get(
        $connection,
        "README.txt",
        "/README",
        FTP_ASCII
    )) {
        echo "File <a href=\"README.txt\">saved</a>.";
    } else {
        echo "Error during download.";
    }
}
ftp_close($connection);
?>
```

Listing 26.9 The FTP Functions of PHP ("ftp.php")

The code in Listing 26.9 downloads the README file from Mozilla's FTP server (ftp.mozilla.org), which contains general information about the server. The file is saved locally and can be viewed there. The download mode selected is FTP_ASCII; for binary files, you need FTP_BINARY.

## 26.3 Fibers

With Fibers, a new feature was introduced in PHP 8.1 to perform several tasks simultaneously. Strictly speaking, Fibers are functions with a pause button: if desired, they can be interrupted and resumed later. This also results in the three main methods of an instance of the Fiber class:

- start()
  Starts a fiber function
- suspend()
  Pauses a fiber function
- resume()
  Resumes a paused fiber function

Why is this topic in a chapter that is primarily about network communication and HTTP? Because Fibers are a great way to perform parallel HTTP requests! To do this, we create several instances of the Fiber class. The constructor contains the code of the Fiber as an anonymous function. We then execute all Fibers in a loop by calling their start() method. Listing 26.10 shows the corresponding code.

```php
<?php
$urls = [
    "https://www.php.net/",
    "https://windows.php.net/",
    "https://pecl.php.net/"
];

$fibers = [];

foreach ($urls as $url) {
    array_push($fibers, new Fiber(function() use ($url) {
        $contents = file_get_contents($url);
    }));
}

foreach ($fibers as $fiber) {
    $data = $fiber->start();
}
?>
```

Listing 26.10 Parallel HTTP Requests with Fibers ("fibers.php")

Further, albeit rather brief, information about Fibers can be found in the PHP online documentation at www.php.net/fibers. For more detailed information about the implementation of Fibers, it is worth taking a look at the RFC for this feature (https://wiki.php.net/rfc/fibers).

## 26.4 Application Examples

You can create some useful applications with streams. This section gives you two suggestions that are suitable for further development.

### 26.4.1 Text Versions of Web Pages

First, let’s look at an approach to creating a text version of a web page. Although web-based browsers such as Lynx are getting better and better, in view of the fact that accessibility (accessible design) is becoming increasingly important, thinking about this project is a good idea.

How do we achieve this? With a special streams filter. The `string.strip_tags` filter is already quite good, but imagine we want to keep the content of `<p>` tags. We also want to prepare the output with `htmlspecialchars()`. String manipulation is then still necessary: Because the `<p>` tags (and their content) should be retained, we have to delete the tags themselves. In the self-written filter, the following instruction is the decisive one:

```
$bucket->data = htmlspecialchars(
    str_replace("<p>", "", strip_tags($bucket->data, "<p>"))
```

Listing 26.11 shows a small example: The user enters a web address, which is loaded and converted into a text version. Figure 26.9 shows the output.

```
<form method="post">
URL: <input type="text" name="url" value="<?php
    echo (isset($_POST["url"]) && is_string($_POST["url"])) ? htmlspecialchars($_POST["url"]) : "";
?>"/> <input type="submit" />
</form>
<hr />
<?php
if (isset($_POST["url"]) && is_string($_POST["url"])) {
    $url = $_POST["url"];
    class textversion_filter extends php_user_filter {
        function filter($in, $out, &$consumed, $closing): int
        {
            while ($bucket = stream_bucket_make_writeable($in)) {
                $bucket->data = htmlspecialchars(
                    str_replace("<p>", "", strip_tags($bucket->data, "<p>"))
                );
                $consumed += $bucket->datalen;
                stream_bucket_append($out, $bucket);
            }
            return PSFS_PASS_ON;
        }
    }
    stream_filter_register(
        "string.textversion",
        "textversion_filter"
    );
    echo "<pre>";
    echo file_get_contents(
        "php://filter/read=string.textversion/resource=$url"
    );
    echo "</pre>";
}
?>
```

Listing 26.11 A Simple Text Version of a Web Page ("textversion.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_742_0.png)

Figure 26.9 The Text Version of a “phpinfo()” Call

> **Note**
> 
> This application is not intended for internet use in its current form as you can enter any stream in the URL field, including a local file name such as /etc/passwd. If you integrate this text version into your website, you must make the script particularly secure (e.g., by only allowing URLs from a specific server).

### 26.4.2 Online Compressor

The second application shifts a special task—compressing a file—to the web server. Imagine that the user does not have gzip or bzip2. If you have your own, better compression algorithm, you can implement it as a separate stream and thus offer the service (but only internally, please). Even if the gzip algorithm is nothing special, the example still shows the potential of the special PHP streams.

The user transfers a file to the web server via <input type="file" />. After the usual checks with is_uploaded_file(), the file is first read in with file_get_contents() and then written with file_put_contents()—this time, compressed:

```
$tempfile = tempnam("/tmp", "php");
@file_put_contents(
    "compress.zlib://$tempfile",
```

