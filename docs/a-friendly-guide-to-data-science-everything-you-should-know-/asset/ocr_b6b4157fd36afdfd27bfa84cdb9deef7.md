# CHAPTER 1 WORKING WITH NUMBERS: WHAT IS DATA, REALLY?

Finally, representing this data means that we've lost a lot of information—such as the data the sections appear in, in a given paper. We'll address unstructured data in later chapters, but the takeaway here is some data has more inherent structure than other data.

It's usually pretty clear if data is structured or not, but semi-structured data is in-between. XML, HTML, and JSON have some structure, but not enough that it can be considered true structured data. However, it's easier and more intuitive to convert it into tabular format than unstructured data. See Figure 1-4 for examples of these three formats.

| XML | HTML | JSON |
| --- | --- | --- |
| <animals> | <html> | { |
| <animal> | <head> | 'animals': { |
| <id>id</id> | <title>Two Cats</title> | 'id': '1', |
| <species>species</species> | <body> | 'species': 'cat', |
| <name>Marvin</name> | <p>Cat to Know the Cats|</p> | 'name': 'Marvin', |
| <age>14</age> | <h2>Madox</h2> | 'age': '14', |
| <age_unit>age_unit</age_unit> | <p>Marvin is a great cat even though he has health problems.</p> | 'age_unit': 'years', |
| <sex>male</sex> | <paragraph>8-year-oldold Siamese cat likes to bite hard things like metal chair legs</paragraph> | 'sex': 'neutral male', |
| <breed>domestic</breed> | <h2>Madox</h2> | 'breed': 'domestic', |
| <colors> | <paragraph>Madox is a slightly obnoxious</paragraph> | 'colors': { |
| <color1>tabby</color1> | </body> | 'color1': 'tabby', |
| <color2>brown</color2> | </html> | 'color2': 'brown', |
| <color3>white</color3> | | }, |
| <deceased>deceased</deceased> | | 'deceased': true |
| <animal> | | } |
| <animal> | | { |
| <id>2</id> | | 'id': '2', |
| <species>cat</species> | | 'species': 'cat', |
| <name>Madox</name> | | 'name': 'Madox', |
| <age>8</age> | | 'age': 8, |
| <age_unit>years</age_unit> | | 'age_unit': 'years', |
| <sex>male</sex> | | 'sex': 'neutral male', |
| <breed>Siamese</breed> | | 'breed': 'Siamese', |
| <colors> | | 'colors': { |
| <color1>seal-point</color1> | | 'color1': 'seal-point', |
| <colors> | | } |
| <animal> | | } |
| <animal> | | { |
| <id>3</id> | | 'id': '3, |
| <name>Pelusa</name> | | 'name': 'Pelusa' |
| <animal> | | } |

**Figure 1-4. XML, HTML, and JSON**

The example XML and JSON in Figure 1-4 represent the exact same on three different formats. HTML-style formatting that serves a specific purpose, telling a web browser how to