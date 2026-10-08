
CSS is so much part of web design nowadays, that it's rare for anyone to create a new site from scratch which uses the old `<font>` tags. That's not to say that there aren't millions of old-fashioned pages still around, but CSS is definitely a better way of doing things, so that's the method that we'll cover in this book.

## About DOCTYPEs

Before we start with CSS, a word about document types. You'll have noticed, above the `<head>` section in the HTML code shown on page 53, a line that starts with the word DOCTYPE. In full, the line is:

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

This is known as DTD, or Document Type Definition.

HTML is continually evolving. As mentioned above, for example, the advent of CSS now means that you are advised not to use `<font>` tags. The DOCTYPE is a way for you to tell the visitor's web browser which version of HTML you'll be using. With this information, the browser can ensure that your page displays correctly.

The two main document types that you'll see used most are XHTML 1.0 Strict and XHTML 1.0 Transitional. Transitional is the version that allows both new-style CSS as well as old-fashioned `<font>` tags. "Strict" mode doesn't allow `<font>` tags. If you specify a Strict document type, and then proceed to use `<font>` tags, you are technically producing invalid HTML which the browser might well reject.

The simplest option is therefore always to use a Transitional doctype, but to adhere to the latest standards and techniques.

## Getting Started with CSS

If Amaya isn't already open on your computer, open it now. Then load your index.html home page. The quickest way to do this is to use the right-hand menu pane, which is not something we've covered before.

The right-hand side of your Amaya screen probably looks, right now, something like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_60_0.png)

There are various menu options that can be opened and closed on this panel, each of which is preceded by a ▶ character, such as Elements, Style, List of style sheets, Files, Attributes, and so on. When a menu set is visible, the prefix shows as ▼. When it’s hidden, the character shows as ▶ instead. You can show or hide these sections by clicking on the arrow characters.

Perhaps the most useful of these sections is Files, which brings up a simple file manager that makes it quick and easy to open any of your existing web pages. The Apply Class box is also useful, for reasons that we’ll come to shortly.

So, click on the arrow characters to close all of the sections, then open the Files section and the Apply Class section. Your screen should now look thus:

![](img/50e1558b8202f19b96c1cc386ea5ec66_61_0.png)

Note, by the way, that the Style section is nothing to do with CSS. It’s a built-in feature of Amaya that uses a non-standard way of changing the look of web pages, so we won’t be using it.

Now it’s time to open your index.html page. Use your newly-found file manager to browse to your Web Work folder, and double-click on index.html. Or, if you prefer, go to the File menu on the top line and then use the Open Document option. Either way, you’ll end up with your index.html page open and ready for editing.

We now need to create the style sheet file for our site. From the File menu on the top of the screen, choose New, then New Style Sheet. Use the folder button to browse to your Web Work folder if it’s not already shown. Amaya wants to name the file New.css but this is unwise. It is conventional to name the main style sheet file style.css and not to include any capital letters in the name. So change New.css to style.css in the New CSS Style Sheet box.

In the same box, select the **In New Tab** radio button for where to open the file, then click Create.

You will see that there are now 2 (or maybe 3) tabs open in Amaya. One is your index page, and the other is your css file. You can click on the tabs to switch between files.

In the previous chapter, we learned about HTML tags. Now, we can start to create a style sheet that applies particular formatting to particular tags.

Into your blank css file, type the following:

```css
p {
font-family: Verdana;
color: red
}
```

Your screen will look like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_62_0.png)

We’ve now created the first entry for our site’s style sheet. This specifies that all <p> tags should use the Verdana font and should be coloured red.

The format of a CSS file is fairly easy to understand, once you know the basics. On the first line of each entry goes the name of the HTML tag that you want to specify a style for, followed by a curly bracket. On subsequent lines, specify the various aspects of that style, such as font-family and color. I'll explain later how to find out what other style aspects are available.

Each style aspect ends with a semi-colon. Finally comes a closing curly bracket.

Note that the semicolon on the final style characteristic is optional, as you can see from the way that it's not been included in the examples on the illustration below. However, it's generally good practice to get into the habit of always including the semicolon at the end of every line. Otherwise, if you add new style options below what is currently the last line in a style definition, and you forget to add the semicolon to what is no longer the last line, your style sheet file won't work properly because the web browser won't always know where one line ends and the next one begins.

While we're here, let's add another style definition to our CSS file, this time for the <ul> tag which defines a bulleted list (ul stands for Unordered List, in contrast to a numbered list which uses the <ol> tag for an ordered list).

So, add a new section to the CSS screen as follows:

```css
ul {
color: green;
}
```

Your CSS file should now look like this:

![](img/50e1558b8202f19b96c1cc386ea5ec66_64_0.png)

Flip back to your index.html page by clicking on its tab. Has anything changed? Are your paragraphs now in Verdana and coloured red? Sadly not, for one very good reason. Although you’ve created a style sheet, we haven’t yet added the necessary command to our index page to specify where it should get its style information from. So let’s change that.

First we need to save the style sheet that we were working on. So flip to the style sheet tab and, from the File menu, choose Save. Now flip back to the index.html page tab.

From the Format menu, choose Style Sheets and then the Link option. In the box, just type style.css and press the Confirm button. There’s no need to specify the full path, because both your index.html page and your style.css file are in the same folder.

And now, as if by magic, your index page has changed. Your paragraphs of text are now, as requested, using the Verdana font and are red.

We also specified a style for our unordered lists, so let’s see if that works too. First, type a few short paragraphs into your index page like this:

This is my index page, ie the home page of the site.

![](img/50e1558b8202f19b96c1cc386ea5ec66_65_0.png)

As expected, they will be red and Verdana because that’s what the style sheet says that paragraphs should be. But that’s about to change.

Select your entries, using the keyboard or mouse. Then, from the Insert menu, choose List, then Unordered List. Here’s what the screen should look like now:

![](img/50e1558b8202f19b96c1cc386ea5ec66_66_0.png)

Your list uses `<ul>` tags, and your style sheet says that `<ul>` tags should be green. So they are.

The list items aren't using the Verdana font, though, because your ul tag style didn't say that they should. But we can fix that quickly and easily. Flip back to your css file by clicking on its tab. Add a new line to the ul tag style to specify font-family: Verdana. Save the css file and then flip back to the index page, and you should find that the font used by your list has now changed.

The ability to change one, or indeed hundreds, of pages by making a single change to a single style sheet file is what makes CSS so useful. If all of the pages in your site are linked to the same style sheet, changing the CSS file changes all of the pages instantly.

## A Word About Fonts

You probably have one or two hundred fonts installed on your computer. Most people do. Every time you install a new program, it frequently comes with a selection of new fonts that are installed. If you look at the list of available fonts in Microsoft Word, or whatever word processor you happen to use, the list will be enormous. However, that doesn't mean that you can use all of them on your Web pages.
