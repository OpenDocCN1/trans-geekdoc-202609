The BODY element represents the page content that is shown in a browser window. Here is an HTML document with this minimal set of elements:

```
<HTML>
    <HEAD>
        <TITLE> The title of the web page </TITLE>
    </HEAD>
    <BODY> body content of the web page </BODY>
</HTML>
```

# Content types

Within the document body, the content is frequently organized into blocks of textual information, such as headings, paragraphs, lists and tables. There may also be other media types in the body, such as images, sound clips and movies. A media type is some kind of Multipurpose Internet Mail Extension (MIME) type that defines a particular type of file that can be used on the Internet. Since HTML 4, the preferred term is content type, since media type is more properly applied to types of output device. Regardless, the type of an HTML document is 'text/html', but such documents may contain references to content that is of a different type. HTML provides a large number of tags for organising the structure of a document's content, including all the other content types that may be included inside it. In this chapter we look at the main organising elements: headings, paragraphs, lists, tables and forms.

# Text elements

Much of the content of web pages is based on the management of text. The structure of the text can be organized using headings, subheadings and paragraphs. Some other types of content can usefully be structured in terms of lists (which may be ordered in some way) or tables. There are also certain semantic aspects of text that can be included in mark-up, to provide emphasis or indicate quotations, for example. In this section, we look at some of the basic structural elements that assist in organising content in HTML pages.

A very common way of organising text-based content is to use headings, subheadings and paragraphs. The H1, H2, H3, H4, H5 and H6 elements can be used for various levels of heading and subheading. H1 is the largest heading and H6 the smallest. Because a heading is generally larger than the text that follows, it may not be sensible to use more than the first two or three levels of heading. In many browsers, the smallest heading types are smaller than standard paragraph text.

As we have already seen, the HTML syntax for a paragraph element is <P>. You should also add the closing </P> tag at the end of each paragraph to make the element 'well formed', though most browsers will still display the page correctly without the closing tag. This is an aspect of minimisation, a feature of SGML, which means that not all elements need to have closing tags, if the end of an element can be inferred from other parts of the document structure, such as the beginning of another paragraph inferring the end of the previous one. Browsers generally leave a blank line before a paragraph element. In the example below, we use an H1 element for a main heading and H2 elements as subheadings, with the main body of the text in paragraphs, surrounded by <P> ... </P> tags.