```
a:hover {
    border-bottom: 1px dotted;
}

ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

/* Layout */

#container {
    width: 760px;
    margin: 20px auto;
    padding: 5px;
    border: 2px #eeeeee solid;
    text-align: left;
}

#links {
    width: 750px;
    padding: 5px;
    background-color: #2D3A5C;
}

#header {
    width: 760px;
    margin: 5px 0;
    height: 120px;
    background: url(images/header.jpg) no-repeat;
}

```

There are others, too, but this will suffice for the moment. Let’s take a look at some of these style definitions, and decipher what they mean.

First is the style for the contents of the <body> tag, which governs some of the overall look for the entire page. We can see, for example, that the background image is specified here. The "repeat" bit means that, although the image itself is small, it will be tiled across the entire page as needed.

Next, the file specifies that headings 1 to 4 have no margin or padding, and are in bold type.

Next, we set margins around each paragraph (ie, the <p> tag). But why 8px and 5px? You can specify up to 4 values in instances such as this, to affect margins, padding etc all around an item. The 4 values start from the top and work clockwise around it. So, for example, a margin of 4px 7px 10px 3px means 4 pixels at the top, 7 to the right, 10 underneath and 3 pixels to the left. In this case, only the first two values have been specified, so each paragraph will have an 8 pixel margin above it and 5 pixels to the right.

The <a> tag stands for "anchor", and is the one we use for creating hyperlinks. In the style definition for the <a> tag, text-decoration:none is how we remove the underline that