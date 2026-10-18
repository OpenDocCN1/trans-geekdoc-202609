# Exercises

5.1 Here is the XML document, from Section 5.4, that is not well formed:

```
<?xml version="1.0"?>
<climate>
    <average-winter-temperature>
    10
    <average-summer-temperature>
    20
    </average-summer-temperature>
</climate>
```

As we saw from the example, if you load this into a browser, an error message complains that the closing ‘average-winter-temperature’ tag is missing when it gets to the closing ‘climate’ tag. Why doesn’t it fail as soon as it gets to the opening ‘average-summer-temperature’ tag?

5.2 Here is a simple DTD:

```
<!ELEMENT building (address, value, construction)>
<!ELEMENT address (#PCDATA)>
<!ELEMENT value (#PCDATA)>
<!ELEMENT construction (#PCDATA)>
<!ATTLIST building rental (true|false) #REQUIRED>
```

Write an XML document that is valid against this DTD that describes an insured building, at 100 Seaview Road, worth £400,000, of brick and tile construction and used as a rental.

5.3 Earlier in this chapter, we saw the following XML document:

```
<?xml version="1.0"?>
<!-- File: Example5-2.xml -->
<weather-forecast>
    <today>
        <general>Rain</general>
        <temperature>
            <maximum>15</maximum>
            <minimum>11</minimum>
        </temperature>
    </today>
    <tomorrow>
        <general>Showers</general>
        <temperature>
            <maximum>20</maximum>
            <minimum>15</minimum>
        </temperature>
    </tomorrow>
    <long-range>Unsettled</long-range>
</weather-forecast>
```

Write a DTD against which this document would be valid.