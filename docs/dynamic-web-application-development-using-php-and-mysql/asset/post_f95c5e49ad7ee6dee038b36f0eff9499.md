
## Exercises

### 5.1 Here is the XML document, from Section 5.4, that is not well formed:

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

### 5.2 Here is a simple DTD:

```
<!ELEMENT building (address, value, construction)>
<!ELEMENT address (#PCDATA)>
<!ELEMENT value (#PCDATA)>
<!ELEMENT construction (#PCDATA)>
<!ATTLIST building rental (true|false) #REQUIRED>
```

Write an XML document that is valid against this DTD that describes an insured building, at 100 Seaview Road, worth £400,000, of brick and tile construction and used as a rental.

### 5.3 Earlier in this chapter, we saw the following XML document:

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

### 5.4 Write a DTD against which this XML document would be valid

```
<policies>
<description>Policies taken out in January</description>
<policy type="contents">
<policy-number>1234557</policy-number>
<policy-holder>A. Liu</policy-holder>
</policy>
<policy type="buildings">
<policy-number>1234558</policy-number>
<policy-holder>C. Jones</policy-holder>
</policy>
<report-date>01/01/2008</report-date>
</policies>
```

Assume there can be zero or more ‘policy’ elements, and that the ‘type’ attribute is compulsory.

### 5.5 Write a DTD that encompasses these rules for elements and attributes

Elements:

- A ‘policy-report’ root element consists of an optional ‘description’ element, one or more ‘policy’ elements and a ‘report-dates’ element.
- ‘report-dates’ is an empty element.
- ‘policy’ elements consist of a ‘policy-number’ element, followed by either a ‘personal-customer’ element or a ‘corporate-customer’ element.
- ‘description’, ‘policy-number’, ‘personal-customer’ and ‘corporate-customer’ are parsed character data.

Attributes:

- ‘policy’ elements have a compulsory type attribute that can only have the value ‘buildings’ or ‘contents’.
- ‘report-dates’ has two attributes, a compulsory ‘start’ attribute and an optional ‘end’ attribute.

### 5.6 Now write an XML document that is valid against the DTD that you created for Exercise 5.5.

### 5.7 Take the HTML document from Example 4.12.htm, which demonstrates the three region layout, and convert it to valid XHTML. You will need to:

- Change the DOCTYPE
- Add the namespace and language to the opening HTML tag
- Change all the element names to lower case
- Make sure the empty elements are correctly terminated.

## SUMMARY

We began this chapter by describing the limitations of HTML in its role as a mark-up language that combines page content, structure and presentation. We introduced the concept of semi-structured data and saw how XML follows its principles. We looked at how XML is a metalanguage, able to be used to define any number of specific mark-up languages due to its extensible nature. We explored the concept of validation, both for XML and HTML, and finally XHTML, which is the evolutionary path that has seen the joining together of HTML and XML. Along the way we saw how document validation may be performed using DTDs, to ensure that our documents are structured correctly.

## References and further reading

- BBC (2005) Radio Times. http://www.radiotimes.com/
- Bray, T., Paoli, J., Sperberg-McQueen, C., Maler, E. and Yergeau, F. (2004) Extensible Markup Language (XML) 1.1. W3C. http://www.w3.org/TR/2004/REC-xml11-20040204/
- Bray, T., Paoli, J., Sperberg-McQueen, C., Maler, E. and Yergeau, F. (2006) Extensible Markup Language (XML) 1.0 (Fourth Edition). W3C http://www.w3.org/TR/REC-xml/#sec-origin-goals
- Eckstein, R. (2002) Java Enterprise Best Practices. Farnham: O'Reilly.
- Eden, R. (2005) XMLTV wiki. http://xmltv.org/
- Pemberton, S. (2007) XHTML2 Working Group Home Page. http://www.w3.org/MarkUp/
- Uniprot. (2005) The Universal Protein Resource. http://www.ebi.uniprot.org/index.shtml

## Introduction to JavaScript

### LEARNING OBJECTIVES

- To understand the role of client-side scripting languages in supporting application processes within the browser
- To understand the key features of the JavaScript language
- To be able to use the objects, properties and methods of the DOM to interact with browsers and HTML documents
- To be able to write simple scripts that manipulate JavaScript variables
- To understand how to write JavaScript functions and to put them into separate files that can be called from scripts in web pages

### INTRODUCTION

In this chapter, we introduce the JavaScript language, which can be used to write code that runs inside the browser. We apply some of the most important concepts in JavaScript, including the document object model (DOM) and the built-in JavaScript objects. Examples in this chapter show how to use the properties and methods of JavaScript objects, how to work with simple data types including numbers, strings, dates and arrays, and how to use the arithmetic operators. We explore the control structures of JavaScript programming and see how to write code in script elements, functions and external files.

### 6.1 JavaScript – what and why?

Scripting languages are lightweight programming languages that are usually interpreted rather than compiled and run inside a particular environment. ‘a client-side script is a program that may accompany an HTML document or be embedded directly in it’ (Ragget et al. 1999).

JavaScript is the most commonly used of a number of scripting languages that can run inside web browsers. JavaScript code can be embedded in, or called from, HTML
documents and these scripts can generate page content dynamically. In general, JavaScript is used for three main purposes:

- To improve the visual look and feel of the user’s experience using a browser-based application. For example, JavaScript can be used to create pop up windows and interactive menus, and to enable parts of the page, such as images, to respond to mouse events, such as the mouse pointer passing over them. JavaScript, combined with the DOM and cascading style sheets (CSS), is the basis for Dynamic HTML (DHTML), which enables browser-based applications to become more interactive.
- To offload some of the web application processing from the server to the client. A good example of this is the ability to perform client-side form validation, checking the contents of an HTML form before it is submitted to the server for further processing. Not all validation can be done on the client, but simple things like checking that required fields are not empty can still be very useful.
- To enable Asynchronous JavaScript and XML (Ajax) implementations to provide a more seamless interaction between client and server.

JavaScript was originally developed in 1995 by Netscape and introduced into Netscape Navigator 2.0. It was originally called ‘LiveScript’ but later became ‘JavaScript’, and is therefore often confused with Java, though there are many differences between them. Although the term ‘JavaScript’ is widely used, strictly speaking the name only applies to the Netscape version. The version that runs in Microsoft browsers is called ‘JScript’, and there is also a standard version of the language known as ‘ECMAScript’. ECMA is a European standards consortium that began as the European Computer Manufacturers’ Association, hence the acronym.

### 6.2 The document object model (DOM)

The DOM is a W3C specification that enables scripting languages, like JavaScript, to access and update the content, structure and style of documents, regardless of the platform or scripting language being used. The first DOM specification (level 1) was published in 1998, the second (level 2) in 2000 and the third (level 3) in 2004. The DOM consists of a set of core interfaces that apply to any structured document, with additional interfaces that are specifically intended for use with XML or HTML documents. As HTML has grown closer to XML with the XHTML specification, this distinction between XML and HTML has become less important. The term ‘DOM level 0’ is sometimes used to refer to the de facto object model that was used in browsers (such as Internet Explorer 3 and Netscape Navigator 3) prior to the first formal DOM specification. Some parts of the DOM API that relate specifically to HTML were included to ensure backward compatibility with these earlier document models.

The DOM represents a document as a hierarchy of nodes, some of which can have child nodes and some that are leaf nodes. You will recognize core aspects of the DOM from our prior discussions of the structure of XML documents. For example the document node can only have one child of type element (which of course is the root element of the document.) An element node, however, can have multiple child nodes, and these may also be elements. A text node is a leaf, meaning that it cannot have any child nodes. As we look at JavaScript, you will find that it has its own way of modelling the document object, some of which comes directly from the standard W3C DOM and some of which is specific to JavaScript.
