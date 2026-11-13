# Content Formatting and Submission

We're almost there. We've designed a database to store jokes, organize them into categories, and track their authors. We've learned how to create a Web page that displays this library of jokes to site visitors. We've even developed a set of Web pages that a site administrator can use to manage the joke library without having to know anything about databases.

In so doing, we've built a site where the resident Webmaster will no longer have to continually plug new content into tired HTML page templates, nor maintain an unmanageable mass of HTML files. The HTML is now kept completely separate from the data it displays. If you want to redesign the site, you simply have to make the changes to the HTML contained in the PHP files that site visitors see. A change to one file (e.g. changing a font) is immediately reflected in the page layouts of all jokes, because all jokes are displayed using that single PHP file. Only one task still requires HTML to enter into the equation that manages the content of the Web site: content formatting.

On any but the simplest of Web sites, it will be necessary to allow content (in our case study, jokes) to be formatted. In a simple case, this might merely be the ability to break text into paragraphs. Often, however, content providers will expect facilities such as boldfaced or italicized text, hyperlinks, etc.

Our current database and site design already supports all these requirements. A site administrator can include in the text of a joke HTML tags that will have their usual effects on the joke text when it's inserted into a page that a browser requests. However, to eliminate HTML from the system entirely, we must provide some other way to format text.

In this part of our series, we'll learn some new PHP functions that provide basic text formatting without the use of HTML. In so doing, we'll have completed a content management system that anyone with a Web browser can utilize. We'll then take full advantage of this ease of use, and allow site visitors to once again submit their own jokes -- this time without the risk that users might fill our site with inappropriate material.

# Out with the Old

Before we introduce a new method to format text, we should first disable the old one. A user with no knowledge of HTML might unknowingly include