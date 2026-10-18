DTD is separate from the XML file, then the value of the ‘standalone’ attribute should be ‘no’ instead of ‘yes’, as it was in the previous example. Since the default value for this attribute is ‘no’, it is not actually essential here.

```
<?xml version="1.0" standalone="no"?>
<!-- File Example5-7.xml -->
<!DOCTYPE weather-forecast SYSTEM "forecast.dtd">
<weather-forecast>
    <today>
        Rain
    </today>
    <tomorrow>
        Showers
    </tomorrow>
    <long-range>
        Unsettled
    </long-range>
</weather-forecast>
```

In this document, the DTD for the weather forecast (‘forecast.dtd’) is assumed to be stored in the same folder of local file system as the XML file.

# Element declarations in DTDs

As we have seen from our first DTD example, the general form of an element declaration is

```
<!ELEMENT element-name (regular-expression)>
```

The ‘regular-expression’ describes the way the element can be used. A list of comma-separated element names defines the order in which those elements may occur, as we saw with the nested tags inside the weather forecast:

```
<!ELEMENT weather-forecast (today, tomorrow, long-range)>
```

In contrast, an element that is defined as #PCDATA will not contain any nested elements:

```
<!ELEMENT today (#PCDATA)>
```

So far we have looked at a simple example where just a sequence of elements was defined by the DTD. However, as we discussed in the context of XML, semi-structured data does not necessarily need to have such a predictable structure, but we would still like to be able to validate XML documents that exhibit semi-structured characteristics, such as optional elements, elements appearing in different orders and elements appearing many times in the same document. To explore validation of these types of document we will use a slightly more complex example. Let us assume that WebHomeCover wants to manage information about job applicants in some kind of candidate management system. This information would contain data about candidates’ qualifications, skills, experience etc, but this information is likely to vary widely between different candidates. They may have different types and numbers of qualifications, have held varying numbers of previous jobs and have a wide variation in their skill sets. To store such data in XML we have to be able to take advantage of its semi-structured properties to cater for these variations in data structure.