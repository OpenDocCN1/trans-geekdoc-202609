
The PEAR packages are usually installed in folders in your PEAR path:

- /usr/share/php if you’re running Ubuntu
- C:\wamp\bin\php\php5.2.6\PEAR or similar if you’re running WampServer
- /Applications/MAMP/bin/php5/lib/php or similar if you’re running MAMP

You should also find a doc folder inside this path. Most PEAR packages come with documentation and examples, which you’ll find inside this folder when the package has been installed. In addition, the PEAR Web site contains documentation for the majority of packages; to access it, find the package page and click the Documentation link in the page.

Depending on your setup and operating system, you may need to have access to the administrator or root user to install PEAR packages. This is because the PEAR path is often only writable by a user with administrative rights. On Ubuntu, Mac OS X, and other UNIX-like systems, you can usually use sudo to install packages (for example, sudo pear install Net_UserAgent_Detect) if administrative rights are required.

If you’re working on a shared server for which you don’t have root access, you can still install PEAR packages into your shared Web space. If you have SSH access to the server, you can install PEAR that way. If you only have FTP access, you can use an excellent tool called PEAR_RemoteInstaller that installs packages via FTP. Find out how to install via SSH or PEAR_RemoteInstaller at http://pear.php.net/manual/en/installation.shared.php.

## Installing Dependencies

Some PEAR packages require other packages to do their work. These packages are known as dependencies. By default, PEAR only installs the package (or packages) that you specify on the command line. However, you can get PEAR to install any dependencies as well by adding an --alldeps option to the command line. For example:

```
pear install --alldeps Net_UserAgent_Detect
```

--alldeps also installs optional packages that are related to the package you’re installing, but that are not required for the package to work. If you think this is more than you need, you can use --onlyreqdeps to install just the required dependencies.

## Uninstalling Packages

Removing a PEAR package is just as easy as installing. Simply run the package manager with the uninstall command, followed by the name of the package to uninstall:

```
$ pear uninstall Net_UserAgent_Detect
uninstall ok: channel://pear.php.net/Net_UserAgent_Detect-2.5.0
$
```

## Using a PEAR Package

To use a PEAR package in your script, you first need to include the package file in the script and then access the package’s classes and methods as required.

As mentioned earlier, PEAR package files are installed in the PEAR path. Usually your PHP include path contains the PEAR path, among others. This means that you can include a PEAR package simply by referencing the path to the package file relative to the PEAR path.

For example, the Net_UserAgent_Detect package is accessed by including the file Net/UserAgent/Detect.php:

```
require_once ( "Net/UserAgent/Detect.php" );
```

You can then create a new Net_UserAgent_Detect object with:

```
$detect = new Net_UserAgent_Detect();
```

Generally speaking, to get the path to the package file, replace any underscores (_) in the package name with slashes (/) and add .php to the end.

## Try It Out Detecting the Visitor's Browser

Now that you know how to install and access a PEAR package, try writing a script that uses a package. In this example you use the Net_UserAgent_Detect package to write a simple “browser sniffer” script that displays the user’s browser name and operating system name.

First, install the Net_UserAgent_Detect package, if you haven’t already, by following the instructions in the previous section. For example:

```
pear install --alldeps Net_UserAgent_Detect
```

Now save the following script as browser_sniffer.php in your document root folder.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
	<title>Browser Information</title>
	<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
	<h1>Browser Information</h1>

<?php
require_once ( "Net/UserAgent/Detect.php" );

$detect = new Net_UserAgent_Detect();
echo "<p>You are running " . $detect->getBrowserString();
echo ". Your operating system is " . $detect->getOSString() . ".</p>";
?>
</body>
</html>
```

Run the script by visiting its URL in your Web browser. You should see a result similar to Figure 15-1.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_486_0.png)

Figure 15-1

## How It Works

This simple script kicks off with the standard XHTML page header, then includes the Net_UserAgent_Detect package:

```
require_once( "Net/UserAgent/Detect.php" );
```

Next it creates a new Net_UserAgent_Detect object:

```
$detect = new Net_UserAgent_Detect();
```

The Net_UserAgent_Detect class contains a number of different methods for extracting browser information. In this script, the getBrowserString() method is used to retrieve the visitor's browser name and version as a text string, and getOSString() is called to return the visitor's operating system as a string. These strings are then displayed in the page:

```
echo "<p>You are running " . $detect->getBrowserString();
echo ". Your operating system is " . $detect->getOSString() . ".</p>";
```

## Creating HTML Tables with the HTML_Table Package

Now that you've installed and used a basic PEAR package, try something a little more involved. HTML_Table is a package that lets you generate HTML tables programmatically, rather than directly outputting HTML markup yourself. Not only does this result in neater PHP code, but it frees you up to concentrate on the PHP side of things, without having to fiddle with HTML. It also makes it easy for your script to go back and change the table at any time before it's rendered; for example, you can add a new row or column to the table at a later date.

The first thing to do is install the package. HTML_Table depends on another PEAR package, HTML_Common, to do its work, so you'll need to make sure HTML_Common is installed too. The easiest way to do that is to include the `--alldeps` option when installing HTML_Table.

Go ahead and install the HTML_Table and HTML_Common packages using the technique appropriate for your setup, as described earlier in the chapter. For example:

```
$ pear install --alldeps HTML_Table
downloading HTML_Table-1.8.2.tgz ...
Starting to download HTML_Table-1.8.2.tgz (16,988 bytes)
.....done: 16,988 bytes
downloading HTML_Common-1.2.4.tgz ...
Starting to download HTML_Common-1.2.4.tgz (4,519 bytes)
...done: 4,519 bytes
install ok: channel://pear.php.net/HTML_Common-1.2.4
install ok: channel://pear.php.net/HTML_Table-1.8.2
$
```

You can find documentation for HTML_Table on the PEAR Web site (http://pear.php.net/package/HTML_Table/docs), and there should be a couple of example scripts that show how to use HTML_Table in the doc/HTML_Table/docs folder in your PEAR path. Here's a quick overview of HTML_Table's most important methods:

| Method | Description |
|---|---|
| HTML_Table( $attrs, $tabOffset, $useTGroups ) | The HTML_Table constructor. All three arguments are optional. $attrs is an array of HTML attributes (as name/value pairs) to add to the opening `<table>` tag. $tabOffset specifies how many tabs to indent the markup for the table (the default is zero). $useTGroups specifies whether to use thead, tfoot, and tbody elements in the table (the default is false, which means they're not used). |
| `addRow( $contents, $attrs, $type, $inTR, $body )` | Adds a row of cells to the table. `$contents` holds the row data as an indexed array, where each element is the data for a single cell. The optional `$attrs` argument contains attributes to apply to the row, and the optional `$type` argument can be either "th" (for header cells) or "td" (for data cells) — the default is "td". Set the optional `$inTR` argument to `true` to apply the attributes to the `tr` element rather than the `td`/`th` elements (the default). Finally, if you’re using `tbody` elements, specify the `tbody` group number as the `$body` argument. (Use `addBody()` to add a new table body — see the online documentation for details.) |
| `addCol( $contents, $attrs, $type, $body )` | Adds a column of cells. The parameters work in the same way as `addRow()`. |
| `altRowAttributes( $start, $attrs1, $attrs2, $inTR, $body )` | Allows you to set different attributes for every other table row, so you can create alternating row styles. `$start` is the index of the row to start alternating, and `$attrs1` and `$attrs2` are associative arrays or strings holding the attributes to apply to each alternate row. The optional `$inTR` and `$body` arguments work in the same way as those in `addRow()`. |
| `setCellContents( $row, $col, $contents, $type, $body )` | Allows you to set or change the contents of an arbitrary cell in the table. The cell is specified by `$row` and `$col` (numeric indices starting from zero), and `$contents` contains the string to place in the cell. The optional `$type` and `$body` arguments work in the same way as those in `addRow()`. |
| `setHeaderContents( $row, $col, $contents, $body )` | Allows you to set or change a header cell. Works in a similar way to `setCellContents()`. |
| `setAutoGrow( $grow, $body )` | With `$grow` set to `true`, auto-grow is enabled. This means that, whenever you use `setCellContents()` or `setHeaderContents()` to populate non-existent cells, empty cells are created as necessary to fill in the gap between the existing cells and the new cells. The default value for `$grow` is false. The optional `$body` argument works like its counterpart in `addRow()`. |
