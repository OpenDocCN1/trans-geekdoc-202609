```
<body>
    <!-- File: example7-7.htm -->
    <div>
        <a href="javascript:openWindow('about.htm')">open window</a>
    </div>
</body>
</html>
```

The effect of clicking the hyperlink in the page varies from browser to browser. In some cases, a new window is created and in others a new tab appears. Figure 7.6 shows how Internet Explorer 7 responds to the function, opening a new window.

# 7.3 Dynamic style sheets

As well as interacting with the DOM, another important feature of DHTML is the use of style sheets to dynamically change the presentation of the document. A commonly used example of this technique is to apply JavaScript and style sheets to show or hide parts of a page. This technique can be used, for example, to add expandable menus to web pages. To interact with styles inside our scripts, we can use the 'style' property of the elements in the DOM to dynamically apply styles to parts of the document. The CSS style property that we can use to show or hide parts of the page is 'display', which can have the value 'block' to make the content visible, or 'none' to make it invisible. The following function uses an 'if' statement to switch the display style of an element between 'none' and 'block'. In this example, 'element' is a variable that references an element node from the current document, identified by its 'id' attribute.

FIGURE 7.6 The effect of the 'openWindow' function in Internet Explorer 7, triggered by a JavaScript URL

![](bbox=[0.21, 0.61, 0.92, 0.93])