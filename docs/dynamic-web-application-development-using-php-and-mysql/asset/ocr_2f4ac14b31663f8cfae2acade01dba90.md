# 4.3 Style sheets

Using only in-line styles inside tags has no real benefit over using presentation elements and attributes from standard HTML. Although we are using a different syntax, we do not actually separate out structure and content from presentation, and do not gain any of the benefits of applying a generic style to a document. Styles only become useful when they are also applied to a whole document, so that we can, for example, apply a standard style to all H1 elements in a document rather than doing this on an individual basis. In this context, in-line styles are useful for fine-tuning the presentation but should not be used to style a whole document. Applying styles more generally is done using style sheets, either internal to the HTML page or as external documents, linked to the HTML page using the LINK element. First, we look at how to include a style sheet inside an HTML page.

# Internal style sheets

Internal style sheets are those that are included in the HEAD element of an HTML document using the STYLE element. This type of style sheet applies only to that document. For CSS, the value of the STYLE element’s ‘type’ attribute is set to ‘text/css’, as it is when using the META element for in-line styles.

```
<STYLE type="text/css">
...styles defined here
</STYLE>
```

The syntax for defining styles in a STYLE element is similar to the inline style, except that we must also specify to which element types we are applying styles. Each component of a style sheet is made up of three parts:

+   - The name of an HTML element type
+   - The name of a presentational property of that element
+   - The value of the property that is to be applied.

The property and its value appear inside braces (separated by a colon, as they are for inline styles):

```
element {property: value}
```

For example, if we want to change all of the H1 (main heading) elements so that they are styled in blue, we can add the following style element:

```
<STYLE type="text/css">
 h1 {color: blue}
</STYLE>
```

Note that we will be using lower case for element names in our CSS because we will be applying them to XHTML pages later. In XHTML, element names must be in lower case. For HTML, which is not case-sensitive, the case used in the style sheet does not matter.

The difference between our in-line example and this style is that this one will apply to all ‘h1’ elements in the page that is being formatted. Sometimes we will want to apply more than one style to a particular element type, in which case we can separate the different