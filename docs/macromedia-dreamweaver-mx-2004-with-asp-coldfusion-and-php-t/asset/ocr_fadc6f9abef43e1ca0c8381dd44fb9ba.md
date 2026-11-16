When you look in code view, you will see that Dreamweaver this time added a <br /> tag beside the <br> tag it added earlier. Remember, the <br /> syntax is used for empty elements; it is equivalent to <br></br>, and is not simply a closing </br> tag. This proves that Dreamweaver knows that the document is an XHTML document, and you can be assured that henceforth Dreamweaver will not add any non-XHTML-compliant tags to your code.

**NOTE** Dreamweaver may still add <font> tags, depending on how you format text. It's best to discipline yourself not to format text using the Property inspector for such attributes as color and size. Instead, rely on CSS as much as possible.

![](bbox=[0.07, 0.29, 0.73, 0.445])

Changing the document type information at the top ensures that new tags are XHTML-compliant. Of course, it does nothing about the existing tags. You'll have to fix those yourself.

+   12) Remove the two line breaks, if you like, and save the file.

Any time you make a significant change, you should save index.htm. You don't need to save any of the closed files—as soon as Dreamweaver replaced the document type information, it saved those files.

# REPLACING STRINGS IN SOURCE CODE

In this task, you will replace a handful of simple tags. For example, you will replace all instances of <br> with <br />. These changes are straightforward, because there are no attributes or variations to throw off the search. (In contrast, tags such as <img src="images/imagename.gif"> are going to be a little more work, thanks to their attributes; we'll wrestle with these harder ones shortly.)

+   1) Choose Edit > Find and Replace to open the dialog once again.

This time, rather than pasting information in, you can just type directly in the text areas.