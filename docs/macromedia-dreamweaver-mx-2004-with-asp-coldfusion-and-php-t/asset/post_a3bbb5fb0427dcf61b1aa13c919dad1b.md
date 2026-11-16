
**TIP** You can toggle these icons on or off by checking or unchecking View > Visual Aids > Invisible Elements.

ANCHOR ICON

![](img/43fd0127a958864ab2d93e28efe683e7_109_0.png)

IMAGE MAP ICON

4) In the code half of split view, click anywhere inside the <img> tag immediately below the opening <body> tag.

Notice that the Property inspector updates to show the options for this image.

![](img/43fd0127a958864ab2d93e28efe683e7_109_1.png)

5) In the Alt field of the Property inspector, type *Skip to main page content*.
You are using the alt attribute to provide directions to the user.

6) In the Link field, type #top.
This option creates a link to the named anchor you entered a few minutes ago.

7) In the Align drop-down menu, choose Left as the alignment.
This setting causes the table to appear beside the 1-pixel graphic. The default setting causes the table to start a line lower, and introduces unwanted white space at the top of the page.

![](img/43fd0127a958864ab2d93e28efe683e7_110_0.png)

8) Save generic_template.htm.
The template is ready to use.

9) In the code half of split view, copy the entire line below the <body> tag, which should include both the <a> and <img> tags that create the accessibility feature.
Though the template is ready for reproduction, the existing pages lack the accessibility feature that you just created. You can replicate it easily enough by pasting this line of code into each of the existing pages and inserting a named anchor at the top of each page.

**TIP** The following steps walk you through copying and pasting this line in each of the five existing files. But you should know a better way: If you are up to it, skip the remaining steps and use Find and Replace to update all five of the pages in one try. Also remember to use Find and Replace to insert the anchor tag as well.

![](img/43fd0127a958864ab2d93e28efe683e7_110_1.png)

10) Open about.htm, click anywhere inside the main table on the page, select <table> from the tag selector, and press the left arrow key once. Choose Edit > Paste.
This pastes the accessibility spacer graphic into the correct place on the page.
Because it is invisible, you won’t see it in design view.

11) In Design view (or the design half of split view) position the insertion point just to the left of the page title, and press Ctrl+Alt+A (Windows) or Command+Option+A (Macintosh) to insert a named anchor. Once again, name it top, and click OK.
Obviously, for the link to work, the named anchor needs to be inserted!

12) Repeat steps 10 and 11 for each of the remaining pages, except index.htm.
Index.htm has a different structure, so it won’t work the same way. If you want to insert the accessibility spacer anyway, go ahead, but it’s optional on this page.

## WHAT YOU HAVE LEARNED

In this lesson, you have:

- Used Cascading Style Sheets to redefine several HTML tags used in the site (pages 80–89)
- Created custom CSS styles, or classes, and applied them to specific places on the page (pages 89–95)
- Created a generic template that you can use to generate future pages in the site (pages 95–97)
- Added an accessibility spacer image to enable users with screen readers to skip the navigation bar (pages 98–102)

## dynamic web sites

## LESSON 4

You have reached a significant milestone in the revision of the Newland Tours site. You have upgraded to XHTML, stripped out inefficient presentation code, created a cascading style sheet for the entire site, built a template, and enhanced the site’s accessibility. Glancing at the site in a browser, it may not seem like you’ve accomplished three lessons’ worth of work. But you know what important things are going on behind the screen: You’ve laid the foundations for a standards-compliant, future-proof, maintainable site.

Beginning with this lesson, you’ll cast aside (for the most part) traditional, static Web development, and move into database-driven, interactive, dynamic site development. Before you can start developing, though, you need to work through some prerequisites, of both a conceptual nature and a technical nature. By the end of this lesson, you’ll have an idea of how dynamic sites work, and what they are created to do; you’ll have Dreamweaver configured to work with dynamic data; and you’ll have created your first page that uses dynamic content.

![](img/43fd0127a958864ab2d93e28efe683e7_113_0.png)

Developing dynamic Web pages often means mixing and matching regular text with placeholder variables.

## WHAT YOU WILL LEARN

In this lesson, you will:

- Learn foundational dynamic site concepts
- Choose a server model (ASP, ColdFusion, or PHP)
- Configure your computer to run a Web server with a server model (optional)
- Reconfigure the Newland Tours site definition for dynamic Web site production
- Develop a simple dynamic application

## APPROXIMATE TIME

This lesson takes approximately one hour to complete.

## LESSON FILES

### Starting Files:

- Lesson04/Start/newland/about.htm
- Lesson04/Start/newland/contact.htm
- Lesson04/Start/newland/css/newland.css
- Lesson04/Start/newland/generic_template.htm
- Lesson04/Start/newland/index.htm
- Lesson04/Start/newland/profiles.htm
- Lesson04/Start/newland/tours.htm

### Completed Files:

- Lesson04/Complete/newland-asp/about.asp
- Lesson04/Complete/newland-asp/contact.asp
- Lesson04/Complete/newland-asp/css/newland.css
- Lesson04/Complete/newland-asp/generic_template.asp
- Lesson04/Complete/newland-asp/index.asp
- Lesson04/Complete/newland-asp/profiles.asp
- Lesson04/Complete/newland-asp/test_form.asp
- Lesson04/Complete/newland-asp/test_form_processor.asp
- Lesson04/Complete/newland-asp/tours.htm

**NOTE** If you are using ColdFusion or PHP, and you want to access the completed files, then use the mirror folder (newland_cf or newland_php) included on the CD. All of the file names are the same, except the extension is .cfm or .php rather than .asp.

## DYNAMIC WEB SITE BASICS

Setting aside, for a moment, the specifics of the Newland Tours site, in the preceding lessons you explored several concepts that are critical to dynamic site development. One of these is the separation of logic and presentation. The site logic at this point is handled exclusively by XHTML, while the presentation is handled by the cascading style sheet. You have also explored the concept of merging two different documents (an HTML page and a CSS) on the fly to create something different than either of the two source documents alone. These concepts are fundamental to creating dynamic Web sites.

To understand these interactions, and to prepare you for the tasks ahead, let's take a moment to analyze the relationship among the three different major sources of information that make up every Web page: the content (text, images, etc.), the logic (the document hierarchy, such as headings and body text), and the presentation (the colors, font sizes, positioning, and other cosmetic effects).

In earlier versions of HTML, text, markup, and presentation code all exist in the same place: the HTML document itself. In a meaningful way, the document that a developer creates on her or his hard drive is the same as the document viewed in a browser by the site visitor. This simple relationship is shown in the following figure.

![](img/43fd0127a958864ab2d93e28efe683e7_115_0.png)

As a result of the upgrades you made in Lessons 2 and 3, the relationships have changed: You have separated a document’s presentation from its logic and content. Presentation information is now stored in the CSS. Document content is stored as text within the XHTML markup, which also provides the document logic. Only when the XHTML document and the CSS are merged is the “real” page created. This new relationship is represented in the following figure.

![](img/43fd0127a958864ab2d93e28efe683e7_116_0.png)

Beginning with this lesson, you are going to add yet another layer of sophistication to this relationship—one that’s more profound and more powerful even than migrating from HTML to XHTML and CSS. Specifically, when you add database content to the site, you will separate the content from the logic. What this means is that all three levels—presentation, logic, and content—are quasi-independent of each other, which means you can make radical changes to one without needing to make changes to another. The relationship—and the basic blueprint for the rest of the book—is shown in the following figure.

![](img/43fd0127a958864ab2d93e28efe683e7_116_1.png)
