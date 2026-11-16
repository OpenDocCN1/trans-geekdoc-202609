+   - The <root> tag was not closed, and must be.
+   - The tags <title> and <name> are nested incorrectly. The <name> tags should have been closed before the <title> tag.
+   - There's no DTD so the sample can't be validated.

The following XML is well-formed but it is **not valid**:

```
```xml
<root>
    <title>
        <name>some text/<name>
    </title>
</root>
```
```

+   - The <root> tag is closed.
+   - The tags <title> and <name> are nested correctly.
+   - There's no DTD so the sample can't be validated.

The following XML is **well-formed and valid**:

```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
<!ELEMENT name (#PCDATA)>
<!ELEMENT root (title)>
<!ELEMENT title (name)>
]>
<root>
    <title>
        <name>some text/<name>
    </title>
</root>
```
```

+   - The <root> tag is closed.
+   - The tags <title> and <name> are nested correctly.
+   - There's a DTD so the sample can be validated. Note the XML file doesn't need to include the DTD, it can be referenced by replacing the <!DOCTYPE [ ]> with <!DOCTYPE root SYSTEM "root.dtd">, as long as the <!DOCTYPE [ ]> declaration is moved to root.dtd.