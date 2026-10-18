submit for validation, for example:

```
c:\wamp\www\chapter19\example19-1.htm
```

This method of validation is very useful for a developer who is creating web documents on a local computer and wishes to validate them before placing them on a publicly viewable web space. The problem is that uploading documents for validation in this way does not allow you to check scripts which use PHP to generate XHTML/HTML output as these scripts would need to be parsed through a PHP interpreter for the output to be generated. Such scripts would need to be uploaded to a web space and then validated by supplying the URL of the web document.

The final method of validation is by directly entering the file markup that you wish to validate into a form textbox. This may be useful if you have a small amount of script to validate, although it would be just as easy to upload a local document.

> > **NOTE** The speed with which the on-line tool processes your script varies depending on how busy the service is.

Whichever way you choose to submit your document for validation the results can be one of only two outputs: either the document is valid or it is not. Let us begin by validating our simplest document:

```
Hello world!
```

If we validate this by typing it into the textarea box and clicking the Check button, the result is as illustrated in Figure 19.4.

We return to the initial validation screen and try validating the HTML 4.01 document we introduced earlier:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
<TITLE>HTML 4.01 Document</TITLE>
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=ISO-8859-1">
</HEAD>
<BODY>
<P>Hello world!
</BODY>
</HTML>
```

If we save this file and submit it via the file upload option, then the corresponding output is as illustrated in Figure 19.5.