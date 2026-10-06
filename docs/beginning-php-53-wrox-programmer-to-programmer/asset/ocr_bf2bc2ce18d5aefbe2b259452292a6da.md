# Part III: Using PHP Practice

These three DTDs complement your HTML counterparts, are, in fact, quite similar. If you enter these URLs in your browser, you'll actually see the DTD in plain text. (You might need to download the DTD file and open it in your editor)

Here is a portion of the XHTML Strict DTD showing how the img (image) element is declared:

```
<--
To avoid accessibility problems for people who aren't
able to see the image, you should provide a text
description using the alt and longdesc attributes.
In addition, the use of server-side image maps.
Note that in this DTD there is no name attribute. That
is only available in the transitional and frameset DTD.
-->

<!ELEMENT img EMPTY>
<!ATTLIST img
%attrs;
  src           #REQUIRED
  %Text          #REQUIRED
  alt           #IMPLIED
  longdesc      #IMPLIED
  height        #IMPLIED
  width         #IMPLIED
  usemap        %URI#IMPLIED
  ismap         (ismap)#IMPLIED
>
<!-- usepoints to map a map element which may be in this document
or or an external document, although the latter is not widely supported -->
```

On the first line following the comment, the img element is declared EMPTY (that is, it contains no
content, only attributes). Following the ELEMENT line is a list of attributes that may be included inside the
img tag in an XHTML document. Those of you with HTML and XHTML do not recognize
tsrc attribute in an XML document that specifies the location of the image file; this attribute is REQUIRED.

On this portion of the DTD for XML documents, it is possible to include img elements
in documents. If the DTD is referenced in an XML document, the document includes an img
element with an optional src attribute, the document could be said to be valid (at least as far as
im is considered). However, if you tried to use an element name imge or image or images,
validating XML parser would produce an error, because according to the DTD such elements are not
declared, and the document is not valid.

# Referencing DTDs

To reference an external DTD, you use DOCTYPE declaration. This declaration indicates the name and
t location of the DTD. For example, this line shows how to reference the XHTML Strict DTD:

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml-strict.dtd">
```