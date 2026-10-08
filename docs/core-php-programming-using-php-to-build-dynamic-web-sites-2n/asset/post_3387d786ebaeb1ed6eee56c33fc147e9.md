
The xml_set_object function associates an object with a parser. You must pass the parser identifier and a reference to an object. This is best done within the object using this variable. After using this function, PHP will call methods of the object instead of the functions in the global scope when you name handlers.

```php
<?php
class myParser
{
    var $parser;

    function parse($filename)
    {
        //create parser
        if(!$this->parser = xml_parser_create())
        {
            print("Could not create parser!<BR>\n");
            exit();
        }

        //associate parser with this object
        xml_set_object($this->parser, &$this);

        //register handlers
        xml_set_character_data_handler($this->parser, "cdataHandler");
        xml_set_element_handler($this->parser, "startHandler", "endHandler");

        /*
         ** Parse file
         */
        if($fp = fopen($filename, "r"))
        {
            print("Couldn't open example.xml!<BR>\n");
            xml_parser_free($this->parser);
            return;
        }

        while($line = fread($fp, 1024))
        {
            xml_parse($this->parser, $line);
        }
        feof($fp);
    }

    //destroy parser
    xml_parser_free($this->parser);
}
function cdataHandler($parser, $data) {
    print($data);
}
function startHandler($parser, $name, $attributes) {
    switch ($name) {
        case 'EXAMPLE':
            print("<HR>\n");
            break;
        case 'TITLE':
            print("<B>\n");
            break;
        case 'CODE':
            print("<PRE>\n");
            break;
        default:
            //ignore other tags
    }
}
function endHandler($parser, $name) {
    switch ($name) {
        case 'EXAMPLE':
            print("<HR>\n");
            break;
        case 'TITLE':
            print("</B>\n");
            break;
        case 'CODE':
            print("</PRE>\n");
            break;
        default:
            //ignore other tags
    }
}

$p = new myParser;
$p->parse("example.xml");
?>
```

# Core PHP Programming

# xml_parser_set_option(integer parser, integer option, value data)

Use xml_parser_set_option to change the value of an option. Table 14.14 lists the available options.

Table 14.14. XML Option Constants

| Column |
| :--- |
| XML OPTION CASE_FOLDING |
| XML OPTION SKIP_TAGSTART |
| XML OPTION_SKIP WHITE |
| XML OPTION_TARGET_ENCODING |

# boolean xml_set_character_data_handler(integer parser, string function)

Character data is the text that appears between tags, and xml_set_character_data_handler sets the function executes when it is encountered. Character data may span many lines and may cause several events. PHP will not concatenate the data for you.

The function specified in the function argument must take two arguments. The first is the parser identifier, an integer. The second is a string containing the character data.

# boolean xml_set_default_handler(integer parser, string function)

The xml_set_default_handler captures any text not handled by the other handlers. This includes the DTD declaration and the XML tag.

The function specified in the function argument must take two arguments. The first is the parser identifier, an integer. The second is a string containing the data.

# boolean xml_set_element_handler(integer parser, string start, string end)

Use xml_set_element_handler to assign the two functions that handle start tags and end tags.

# Core PHP Programming

The start argument must name a function you've created that takes three arguments. The first function is the name of the start tag found. The third is an array of the attributes for the start tag. The indices of this array are the attribute names. The elements are in the same order as they appeared in the XML.

The second function handles end tags. It takes two arguments, the first of which is the parser identifier. The other is not the name of the tag.

# boolean xml_set_external_entity_ref_handler(integer parser, string function)

XML entities follow the form of HTML entities. They start with an ampersand and end with a semicolon. Between these two characters is the name of the entity. An external entity is defined in other file. This takes the <!ENTITY externalEntity SYSTEM "entities.xml"> in your file. Each time the entity appears in the body of the file, the handler you specify in xml_set_external_entity_ref_handler is called.

The handler function must take five arguments. First is the parser identifier. Next is a string containing the names of the entities for this parser. Then come the base, the system ID, and the public ID.

# boolean xml_set_notation_decl_handler(integer parser, string function)

The handler registered with xml_set_notation_decl_handler receives notification declarations. These are formed like <!NOTATION jpg SYSTEM "/usr/local/bin/jview"> and are meant to suggest a program for handling a data type.

The handler must take five arguments, the first of which is the parser identifier. The second is the name of the notation entity. The rest are base, system ID, and public ID, in that order.

# boolean xml_set_processing_instruction_handler(integer parser, string function)

The xml_set_processing_instruction_handler function registers the handler tags of the following form: <?target data?>. This may be familiar; it's how PHP code is embedded in the files. The target identifies the type of data inside the tag. Everything else is data.

The function argument must specify a function that takes three arguments. The first is the parser identifier. The second is the target. The third is the data.

# boolean xml_set_unparsed_entity_decl_handler(integer parser, string function)

This function specifies a handler for external entities that contain an NDATA element. These take the form of <!ENTITY php-pic SYSTEM "php.jpg" NDATA jpg>, and they specify an external file.

# Part III: ALGORITHMS

An algorithm is a recipe for solving a problem. This section discusses broad problems in computer science and how to solve them, all in the context of PHP. These problems are inherent in any programming endeavor, but in most cases PHP makes handling them easier. However, the particular circumstances of the Web offer the seasoned programmer a new set of challenges. This section will bring these issues to your attention.

**Chapter 15** examines sorting and searching, along with a related topic, random numbers. Although PHP has built-in functions for sorting data, this chapter explores the theory behind sorting and develops sorting algorithms in PHP. This gives you the knowledge to code custom sorting functions when the need arises.

**Chapter 16** discusses parsing and string evaluation. Much of this chapter is about regular expressions, a powerful way to describe patterns that are compared to strings. These are useful for validating user input.

**Chapter 17** describes integrating PHP with a database. MySQL is used in the examples because it's Open Source. Databases allow you to manipulate data in powerful ways and are necessary for many Web applications.

**Chapter 18** is about network issues, such as sending HTTP headers. Because PHP scripts execute as Web pages, network issues appear frequently.

**Chapter 19** explores generating graphics with PHP. It develops examples that create buttons and graphs dynamically.

# Chapter 15. SORTING, SEARCHING, AND RANDOM NUMBERS

Sorting

Bubble Sort

Quicksort

Built-In Sorting Functions

Sorting with a Comparison Function

Searching

Indexing

Random Numbers

Random Identifiers

Choosing Banner Ads

Sorting

To means to put a set of items into order. The rules of ordering can be simple, such as strings sorted by the order of the alphabet. They could be complex, such as sorting addresses first by country, then by state, then by city. The process of sorting can
