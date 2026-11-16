# # Properties

The Content-Type header field value for textual data is set to "text/plain; charset=us-ascii" by default:

```
var $type = 'text/plain';
var $charset = 'us-ascii';
```

The Content-Transfer-Encoding header is also set to its default value in its absence:

```
var $encoding = '7bit';
```

We need a flag indicating whether the message has attachment(s):

```
var $has_attach = 0;
```

Files to be attached go into the $files array as elements. $files is a two-dimensional array with each element holding an associative array containing information on each file. For example, the following code snippet extracts information on the first file in the array:

```
$file1 = $files[0]["file"]; // path of the file
$filename1 = $files[0]["filename"]; // name of the file
$filesize1 = $files[0]["filesize"]; // size of the file
$filetype1 = $files[0]["filetype"]; // type of the file
```

With this array, we can attach as many files as needed to an e-mail message:

```
var $files = array();
```

The default content type for attached files is application/octet-stream. You may create an array holding extensions of well known file types and set the content type of a file according to its extension:

```
var $mime_type = 'application/octet-stream';
```

The MIME-Version header field value and a warning for non-conformant e-mail clients are defined as the following:

```
var $mime_version = "MIME-Version: 1.0";
var $mime_msg = "This is a multi-part message in MIME format.";
```

We'll be using the "X-Mailer" custom header field:

```
var $mailer = 'My Mime Mailer 1.0';
```

The boundary delimiter placeholder:

```
var $boundary = '';
```