Before continuing, it's important to clarify that the template you are about to build is *not* a Dreamweaver Template file. Dreamweaver Templates is a special feature that enables designers to build page templates and then lock specified regions to prevent users from modifying their content. Other regions remain editable, so users can go in and change the content as needed without undermining the site look or navigation across pages. Dreamweaver Templates is a powerful feature, especially when combined with Macromedia Contribute, enabling non-technical content experts to take control over page content and maintenance, while minimizing both their need for Web development skills and the chance that they will mess up the code.

Though an interesting and useful feature, working with Dreamweaver Templates is beyond the scope of this book. Be sure to keep Dreamweaver Templates in mind whenever you are creating a large site, especially if you are working in a collaborative environment.

To conclude, the word *template* used in this lesson and throughout the book is used in the common sense, not in the specialized sense of the Dreamweaver Template feature.

+   1) Open about.htm.

To create the template, you'll strip out all of the unique content from one of the pages of your site. Obviously, the fastest way to do that is to begin with the page that has the least unique content. The file about.htm is the simplest page in the site, so it's a good place to start.

+   2) Choose File > Save As and save the file as *generic_template.htm*.

Before you start destroying the content of your file, you should save it under a new name. Sooner or later, if you wait until the end, you'll save over the source file and have to rebuild it from scratch.

+   3) Click to select the large photo of the French Alps and press Delete. Select the final two paragraphs of body text and the image caption, and press Delete.

All of this content is unique, so it needs to go. We'll deal with the title and the first paragraph of body text in a moment.

You may find that after Dreamweaver removed the content, it did not resize the table (although Macromedia Dreamweaver MX 2004 is much better at dealing with this problem than prior versions), resulting in an absurd amount of white space. However, this is not a code problem, but rather a screen refresh problem; it will display as you would expect it to in a browser.

If you experience this problem, simply click the `<table>` tag in the tag selector to force Dreamweaver to redraw the table.