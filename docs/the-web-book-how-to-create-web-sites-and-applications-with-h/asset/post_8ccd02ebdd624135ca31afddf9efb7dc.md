
## Fonts

When you specify a font in your CSS file, the actual data (all those lines and curves) that make up the font don't get included in the page. All that makes it into the HTML is an instruction to the visitor's web browser to display your chosen text in your chosen font. Which only works if that font happens to be installed on the visitor's computer. If it's not, the browser will make a stab at choosing a font that looks vaguely similar, but the end results are rarely identical.

Because of this, it's always safest to ensure that you only specify fonts in your CSS files which are pretty much guaranteed to be installed as standard on most visitors' computers. Although there aren't many such fonts, they do provide a fairly wide cross-section of styles. The fonts in question are as follows, in their actual style so you can see what they look like:

- Arial
- Verdana
- Trebuchet MS
- Courier New
- Georgia
- Times New Roman

Note that these names are case-sensitive, so specifying `verdana` in a style definition isn't the same as `Verdana`, and probably won't work unless the visitor's web browser is feeling particularly forgiving at the time. Which most modern browsers never do.

These 6 fonts can be classified loosely into three categories. Arial, Verdana and Trebuchet MS are what's known as sans-serif fonts. Serifs are the embellishments on the ends of characters, and sans-serif fonts don't have them. Compare this with serif fonts such as Georgia (which is used throughout this book) and Times New Roman.

For body text, ie the main bulk of the text on your pages, sans-serif fonts tend to work best. For headlines and picture captions, serif fonts look good.

Courier New is an example of a fixed-width font. In this font, each character is the same width. So the word `RAILWAY` is the same width as the word `ILLICIT`, as they both contain 7 characters. Like this:

```
RAILWAY
ILLICIT
```

In fonts that aren't fixed-width, each letter is a different width. Like this:

```
RAILWAY ILLICIT
```

Such fonts are often known as proportionally-spaced fonts, as each character’s width on paper is proportional to its actual width.

Using a fixed-width, non-proportional font is useful in lists of numbers if you want all the columns to line up correctly. For just about all other purposes, proportional fonts tend to be more readable and look more professional. Unless you specifically want to create a web page that looks like it was produced on a typewriter.

## Classes

So far, in our discussion of CSS, we’ve talked about defining styles based on HTML tags. By creating a style definition for the `<p>` tag we can specify how all of the body paragraphs on our pages look. Equally, by creating a style called `ul`, we can style all of our unordered lists. If you were to add a style for the `h1` tag, you could change the look of all the level-1 headings on your pages.

As you might expect, there’s a lot more to CSS than letting you choose a font and a colour to be associated with HTML tags. Actually, CSS is hugely complicated, and is the bane of most professional web developers’ lives. A typical reference book on CSS runs to over 600 pages, but thankfully we’re not going to go into that much detail in this book. There is, though, one more highly useful feature of CSS that you’ll want to know about, and that’s classes.

A class is a style that you can use anywhere on a web page, rather than for a particular HTML tag. Rather than being named after a tag, you can name your classes as you see fit. For example, if you often find yourself mentioning the name of your favourite cheese on your web pages, you could create a class called `fave-cheese`. Then, wherever the name of that cheese appears, you assign it to that class. The text can be an entire paragraph, a few lines, or even just one word. Here’s how to create a CSS class and refer to it within a web page.

Make sure that Amaya is open, and that you have both your `index.html` and `style.css` files open in separate tabs. Now, in your style sheet file, add a new style as follows:

```css
.fave-cheese {
  color: yellow;
  font-family: Arial;
  font-size: 18px;
}
```

There are 2 differences between this style and the others that we have created. First, we chose our own name for the style, rather than using the name of an HTML tag. Second, the style name starts with a dot. The dot is what tells the browser that this is a class rather than an HTML tag style.

Save your css file (File, Save), then flip back to the index page. Notice the Apply Class area on the right hand side of the screen, which now lists your class.

Type some text onto the page, highlight it, then double-click your class name in the list. Your chosen text is now formatted according to your class. Highlight some more text and apply the class to it too.

Between them, tag styles and classes allow you to format your web pages just about any way you wish. If you want to style all instances of a particular tag, ie all of your `h1` headings or all of your paragraphs, use tag styles. Where you want to just style a few words or sentences here and there, use a class.

## Making Styles Work For You

The main benefit of using styles in HTML pages is that they make it easy to make wide-reaching changes to a web site with a single click. Just change a single entry in your css file and the entire site changes. However, if you are to gain the maximum benefit from using css there are two things you need to know about.

First, keep the number of styles (tag and class) to a minimum. If you find yourself creating 6 different versions of the `fave-cheese` class in order to fit the particular idiosyncrasies of your site's layout (eg one version for headings, one for picture captions etc), you lose much of the benefit of CSS because there are now 6 different things that you need to change if you want to alter the way that the names of your cheeses are displayed.

Second, choose your class names with care. Pick names based on what the class is used for, not what it looks like. Consider what would happen if I'd named my cheese class "arial-yellow" rather than "fave-cheese". If I ever redesign my site and decide that I want the cheese names in purple rather than yellow, I'll end up with a class called `arial-yellow` which actually displays in purple. This will make it much less obvious to me, or anyone else in the future, to remember what each class is used for.

## HTML Tags Names

To make the most of HTML tag styles, you obviously need to know what tag names are available to you. You can find a complete list on the internet (just type HTML Tags into Google), but here are a few to get you started:

- `<h1>` to `<h6>` Heading level 1 to 6
- `<table>` Used at the start of a table.
- `<tr>` Starts each row of a table.
- `<td>` Stands for Table Data. Used for each cell of the table.
- `<b>` Bold text.
- `<i>` Italic text.
- `<body>` The entire body of the web page.
- `<ul>` Unordered list, using bullets at the start of each item.
- `<ol>` Ordered (ie, numbered) list
- `<li>` A list item (used within ordered and unordered lists).
- `<a>` Anchor. Used to create hyperlinks.

## A Better CSS Editor

Style sheets are an incredibly powerful feature of modern web design, and there's absolutely no reason why you should use any other method to format your pages. Unfortunately, Amaya doesn't make it particularly easy to create and maintain CSS files. So far, you've created styles manually, line by line. This is slow, prone to errors, and only works if you happen to know the language of css (font-family, color, and so on).

Now that you understand the basics of what a css file is, and the sort of commands it contains, we need to find a better program for editing css files. Preferably one that's free. There are quite a few such programs available, downloadable from the internet. The best one, in my opinion, is Topstyle Lite. It's a cut-down version of a commercial product called Topstyle Pro, which offers even more features. But for anyone who needs a basic program to easily create and edit css files, Topstyle Lite is perfect.

Your next task, therefore, is to download and install Topstyle Lite. Close Amaya for the moment, but don't uninstall it. We'll continue to use Amaya for editing HTML pages.

To download Topstyle Lite, go to www.newsgator.com and follow the links to Topstyle and then to Topstyle Lite. Or type "topstyle lite" into Google. Once you have downloaded the installer file, double-click it to start the installation. The version of Topstyle Lite that we're using in this book is 3.5.
