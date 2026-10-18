![](bbox=[0.17, 0.04, 0.77, 0.18])

particular type of document. A DTD describes, among other things:

+   - What names can be used for element types
+   - How many times a given element may, or must, be used
+   - In what order elements at the same level of nesting may occur
+   - How elements can be nested
+   - The attributes that may, or must, be used with a specific element

An XML document can be linked to a DTD either by including the DTD mark-up inside the XML document itself or by referring to it externally using a URI.

# Defining elements in a DTD

For our first example DTD we will describe a simplified ‘weather-forecast’ XML document type. In this DTD, there are no attributes, we are simply describing elements. You will see from this example that DTD syntax is not the same as XML syntax. It does use angle brackets, but is otherwise quite different:

```
```dtd
<!ELEMENT weather-forecast (today, tomorrow, long-range)>
<!ELEMENT today (#PCDATA)>
<!ELEMENT tomorrow (#PCDATA)>
<!ELEMENT long-range (#PCDATA)>
```
```

The first line of the DTD indicates that the first element (weather-forecast) is the root. The other elements (today, tomorrow and long-range) are sub-elements of the root (i.e., they are nested inside it) and are defined in the order in which they must appear in a valid XML document. The remaining three lines indicate that each of these three nested elements contains parsed character data (#PCDATA). This means that the element will contain character data that an XML processor will parse as it reads through the document. Our first XML example (shown again here) would be valid against this DTD. We have the necessary root element, with the three nested elements in the correct order:

```
```xml
<?xml version="1.0"?>
<!-- File: Example5-1.xml -->
<weather-forecast>
    <today>
        rain
    </today>
    <tomorrow>
        showers
    </tomorrow>
```
```