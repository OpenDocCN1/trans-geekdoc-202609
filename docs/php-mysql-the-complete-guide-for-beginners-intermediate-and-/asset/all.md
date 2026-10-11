![](Image01745.jpg)

  

Contents

 [About](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX)

[Chapter 1: Getting started with PHP](#text00000.html#_Toc756132)

[Section 1.1: HTML output from web server](#text00000.html#_Toc756133)

[Section 1.2: Hello, World!](#text00000.html#_Toc756134)

[Section 1.3: Non-HTML output from web server](#text00000.html#_Toc756135)

[Section 1.4: PHP built-in server](#text00000.html#_Toc756136)

[Section 1.5: PHP CLI](#text00000.html#_Toc756137)

[Section 1.6: Instruction Separation](#text00000.html#_Toc756138)

[Section 1.7: PHP Tags](#text00000.html#_Toc756139)

[Chapter 2: Variables](#text00000.html#_Toc756140)

[Section 2.1: Accessing A Variable Dynamically By Name (Variable variables)](#text00000.html#_Toc756141)

[Section 2.2: Data Types](#text00000.html#_Toc756142)

[Section 2.3: Global variable best practices](#text00000.html#_Toc756143)

[Section 2.4: Default values of uninitialized variables](#text00000.html#_Toc756144)

[Section 2.5: Variable Value Truthiness and Identical Operator](#text00000.html#_Toc756145)

[Chapter 3: Variable Scope](#text00000.html#_Toc756146)

[Section 3.1: Superglobal variables](#text00000.html#_Toc756147)

[Section 3.2: Static properties and variables](#text00000.html#_Toc756148)

[Section 3.3: User-defined global variables](#text00000.html#_Toc756149)

[Chapter 4: Superglobal Variables PHP](#text00000.html#_Toc756150)

[Section 4.1: Suberglobals explained](#text00000.html#_Toc756151)

[Section 4.2: PHP5 SuperGlobals](#text00000.html#_Toc756152)

[Chapter 5: Outputting the Value of a Variable](#text00000.html#_Toc756153)

[Section 5.1: echo and print](#text00000.html#_Toc756154)

[Section 5.2: Outputting a structured view of arrays and objects](#text00000.html#_Toc756155)

[Section 5.3: String concatenation with echo](#text00000.html#_Toc756156)

[Section 5.4: printf vs sprintf](#text00000.html#_Toc756157)

[Section 5.5: Outputting large integers](#text00000.html#_Toc756158)

[Section 5.6: Output a Multidimensional Array with index and value and print into the table](#text00000.html#_Toc756159)

[Chapter 6: Constants](#text00000.html#_Toc756160)

[Section 6.1: Defining constants](#text00000.html#_Toc756161)

[Section 6.2: Class Constants](#text00000.html#_Toc756162)

[Section 6.3: Checking if constant is defined](#text00000.html#_Toc756163)

[Section 6.4: Using constants](#text00000.html#_Toc756164)

[Section 6.5: Constant arrays](#text00000.html#_Toc756165)

[Chapter 7: Magic Constants](#text00000.html#_Toc756166)

[Section 7.1: Dierence between \_\_FUNCTION\_\_ and \_\_METHOD\_\_](#text00000.html#_Toc756167)

[Section 7.2: Dierence between \_\_CLASS\_\_, get\_class() and get\_called\_class()](#text00000.html#_Toc756168)

[Section 7.3: File & Directory Constants](#text00000.html#_Toc756169)

[Chapter 8: Comments](#text00000.html#_Toc756170)

[Section 8.1: Single Line Comments](#text00000.html#_Toc756171)

[Section 8.2: Multi Line Comments](#text00000.html#_Toc756172)

[Chapter 9: Types](#text00000.html#_Toc756173)

[Section 9.1: Type Comparison](#text00000.html#_Toc756174)

[Section 9.2: Boolean](#text00000.html#_Toc756175)

[Section 9.3: Float](#text00000.html#_Toc756176)

[Section 9.4: Strings](#text00000.html#_Toc756177)

[Section 9.5: Callable](#text00000.html#_Toc756178)

[Section 9.6: Resources](#text00000.html#_Toc756179)

[Section 9.7: Type Casting](#text00000.html#_Toc756180)

[Section 9.8: Type Juggling](#text00000.html#_Toc756181)

[Section 9.9: Null](#text00000.html#_Toc756182)

[Section 9.10: Integers](#text00000.html#_Toc756183)

[Chapter 10: Operators](#text00000.html#_Toc756184)

[Section 10.1: Null Coalescing Operator (??)](#text00000.html#_Toc756185)

[Section 10.2: Spaceship Operator (<=>)](#text00000.html#_Toc756186)

[Section 10.3: Execution Operator (\`\`)](#text00000.html#_Toc756187)

[Section 10.4: Incrementing (++) and Decrementing Operators (--)](#text00000.html#_Toc756188)

[Section 10.5: Ternary Operator (?:)](#text00000.html#_Toc756189)

[Section 10.6: Logical Operators (&&/AND and ||/OR)](#text00000.html#_Toc756190)

[Section 10.7: String Operators (. and .=)](#text00000.html#_Toc756191)

[Section 10.8: Object and Class Operators](#text00000.html#_Toc756192)

[Section 10.9: Combined Assignment (+= etc)](#text00000.html#_Toc756193)

[Section 10.10: Altering operator precedence (with parentheses)](#text00000.html#_Toc756194)

[Section 10.11: Basic Assignment (=)](#text00000.html#_Toc756195)

[Section 10.12: Association](#text00000.html#_Toc756196)

[Section 10.13: Comparison Operators](#text00000.html#_Toc756197)

[Section 10.14: Bitwise Operators](#text00000.html#_Toc756198)

[Section 10.15: instanceof (type operator)](#text00000.html#_Toc756199)

[Chapter 11: References](#text00000.html#_Toc756200)

[Section 11.1: Assign by Reference](#text00000.html#_Toc756201)

[Section 11.2: Return by Reference](#text00000.html#_Toc756202)

[Section 11.3: Pass by Reference](#text00000.html#_Toc756203)

[Chapter 12: Arrays](#text00000.html#_Toc756204)

[Section 12.1: Initializing an Array](#text00000.html#_Toc756205)

[Section 12.2: Check if key exists](#text00000.html#_Toc756206)

[Section 12.3: Validating the array type](#text00000.html#_Toc756207)

[Section 12.4: Creating an array of variables](#text00000.html#_Toc756208)

[Section 12.5: Checking if a value exists in array](#text00000.html#_Toc756209)

[Section 12.6: ArrayAccess and Iterator Interfaces](#text00000.html#_Toc756210)

[Chapter 13: Array iteration](#text00000.html#_Toc756211)

[Section 13.1: Iterating multiple arrays together](#text00000.html#_Toc756212)

[Section 13.2: Using an incremental index](#text00000.html#_Toc756213)

[Section 13.3: Using internal array pointers](#text00000.html#_Toc756214)

[Section 13.4: Using foreach](#text00000.html#_Toc756215)

[Section 13.5: Using ArrayObject Iterator](#text00000.html#_Toc756216)

[Chapter 14: Executing Upon an Array](#text00000.html#_Toc756217)

[Section 14.1: Applying a function to each element of an array](#text00000.html#_Toc756218)

[Section 14.2: Split array into chunks](#text00000.html#_Toc756219)

[Section 14.3: Imploding an array into string](#text00000.html#_Toc756220)

[Section 14.4: "Destructuring" arrays using list()](#text00000.html#_Toc756221)

[Section 14.5: array\_reduce](#text00000.html#_Toc756222)

[Section 14.6: Push a Value on an Array](#text00000.html#_Toc756223)

[Chapter 15: Manipulating an Array](#text00000.html#_Toc756224)

[Section 15.1: Filtering an array](#text00000.html#_Toc756225)

[Section 15.2: Removing elements from an array](#text00000.html#_Toc756226)

[Section 15.3: Sorting an Array](#text00000.html#_Toc756227)

[Section 15.4: Whitelist only some array keys](#text00000.html#_Toc756228)

[Section 15.5: Adding element to start of array](#text00000.html#_Toc756229)

[Section 15.6: Exchange values with keys](#text00000.html#_Toc756230)

[Section 15.7: Merge two arrays into one array](#text00000.html#_Toc756231)

[Chapter 16: Processing Multiple Arrays Together](#text00000.html#_Toc756232)

[Section 16.1: Array intersection](#text00000.html#_Toc756233)

[Section 16.2: Merge or concatenate arrays](#text00000.html#_Toc756234)

[Section 16.3: Changing a multidimensional array to associative array](#text00000.html#_Toc756235)

[Section 16.4: Combining two arrays (keys from one, values from another)](#text00000.html#_Toc756236)

[Chapter 17: Datetime Class](#text00000.html#_Toc756237)

[Section 17.1: Create Immutable version of DateTime from Mutable prior PHP 5.6](#text00000.html#_Toc756238)

[Section 17.2: Add or Subtract Date Intervals](#text00000.html#_Toc756239)

[Section 17.3: getTimestamp](#text00000.html#_Toc756240)

[Section 17.4: setDate](#text00000.html#_Toc756241)

[Section 17.5: Create DateTime from custom format](#text00000.html#_Toc756242)

[Section 17.6: Printing DateTimes](#text00000.html#_Toc756243)

[Chapter 18: Working with Dates and Time](#text00000.html#_Toc756244)

[Section 18.1: Getting the dierence between two dates / times](#text00000.html#_Toc756245)

[Section 18.2: Convert a date into another format](#text00000.html#_Toc756246)

[Section 18.3: Parse English date descriptions into a Date format](#text00000.html#_Toc756247)

[Section 18.4: Using Predefined Constants for Date Format](#text00000.html#_Toc756248)

[Chapter 19: Control Structures](#text00000.html#_Toc756249)

[Section 19.1: if else](#text00000.html#_Toc756250)

[Section 19.2: Alternative syntax for control structures](#text00000.html#_Toc756251)

[Section 19.3: while](#text00000.html#_Toc756252)

[Section 19.4: do-while](#text00000.html#_Toc756253)

[Section 19.5: goto](#text00000.html#_Toc756254)

[Section 19.6: declare](#text00000.html#_Toc756255)

[Section 19.7: include & require](#text00000.html#_Toc756256)

[Section 19.8: return](#text00000.html#_Toc756257)

[Section 19.9: for](#text00000.html#_Toc756258)

[Section 19.10: foreach](#text00000.html#_Toc756259)

[Section 19.11: if elseif else](#text00000.html#_Toc756260)

[Section 19.12: if](#text00000.html#_Toc756261)

[Section 19.13: switch](#text00000.html#_Toc756262)

[Chapter 20: Loops](#text00000.html#_Toc756263)

[Section 20.1: continue](#text00000.html#_Toc756264)

[Section 20.2: break](#text00000.html#_Toc756265)

[Section 20.3: foreach](#text00000.html#_Toc756266)

[Section 20.4: do...while](#text00000.html#_Toc756267)

[Section 20.5: for](#text00000.html#_Toc756268)

[Section 20.6: while](#text00000.html#_Toc756269)

[Chapter 21: Functions](#text00000.html#_Toc756270)

[Section 21.1: Variable-length argument lists](#text00000.html#_Toc756271)

[Section 21.2: Optional Parameters](#text00000.html#_Toc756272)

[Section 21.3: Passing Arguments by Reference](#text00000.html#_Toc756273)

[Section 21.4: Basic Function Usage](#text00000.html#_Toc756274)

[Section 21.5: Function Scope](#text00000.html#_Toc756275)

[Chapter 22: Functional Programming](#text00000.html#_Toc756276)

[Section 22.1: Closures](#text00000.html#_Toc756277)

[Section 22.2: Assignment to variables](#text00000.html#_Toc756278)

[Section 22.3: Objects as a function](#text00000.html#_Toc756279)

[Section 22.4: Using outside variables](#text00000.html#_Toc756280)

[Section 22.5: Anonymous function](#text00000.html#_Toc756281)

[Section 22.6: Pure functions](#text00000.html#_Toc756282)

[Section 22.7: Common functional methods in PHP](#text00000.html#_Toc756283)

[Section 22.8: Using built-in functions as callbacks](#text00000.html#_Toc756284)

[Section 22.9: Scope](#text00000.html#_Toc756285)

[Section 22.10: Passing a callback function as a parameter](#text00000.html#_Toc756286)

[Chapter 23: Alternative Syntax for Control Structures](#text00000.html#_Toc756287)

[Section 23.1: Alternative if/else statement](#text00000.html#_Toc756288)

[Section 23.2: Alternative for statement](#text00000.html#_Toc756289)

[Section 23.3: Alternative while statement](#text00000.html#_Toc756290)

[Section 23.4: Alternative foreach statement](#text00000.html#_Toc756291)

[Section 23.5: Alternative switch statement](#text00000.html#_Toc756292)

[Chapter 24: String formatting](#text00000.html#_Toc756293)

[Section 24.1: String interpolation](#text00000.html#_Toc756294)

[Section 24.2: Extracting/replacing substrings](#text00000.html#_Toc756295)

[Chapter 25: String Parsing](#text00000.html#_Toc756296)

[Section 25.1: Splitting a string by separators](#text00000.html#_Toc756297)

[Section 25.2: Substring](#text00000.html#_Toc756298)

[Section 25.3: Searching a substring with strpos](#text00000.html#_Toc756299)

[Section 25.4: Parsing string using regular expressions](#text00000.html#_Toc756300)

[Chapter 26: Classes and Objects](#text00000.html#_Toc756301)

[Section 26.1: Class Constants](#text00000.html#_Toc756302)

[Section 26.2: Abstract Classes](#text00000.html#_Toc756303)

[Section 26.3: Late static binding](#text00000.html#_Toc756304)

[Section 26.4: Namespacing and Autoloading](#text00000.html#_Toc756305)

[Section 26.5: Method and Property Visibility](#text00000.html#_Toc756306)

[Section 26.6: Interfaces](#text00000.html#_Toc756307)

[Section 26.7: Final Keyword](#text00000.html#_Toc756308)

[Section 26.8: Autoloading](#text00000.html#_Toc756309)

[Section 26.9: Calling a parent constructor when instantiating a child](#text00000.html#_Toc756310)

[Section 26.10: Dynamic Binding](#text00000.html#_Toc756311)

[Section 26.11: $this, self and static plus the singleton](#text00000.html#_Toc756312)

[Section 26.12: Defining a Basic Class](#text00000.html#_Toc756313)

[Section 26.13: Anonymous Classes](#text00000.html#_Toc756314)

[Chapter 27: Namespaces](#text00000.html#_Toc756315)

[Section 27.1: Declaring namespaces](#text00000.html#_Toc756316)

[Section 27.2: Referencing a class or function in a namespace](#text00000.html#_Toc756317)

[Section 27.3: Declaring sub-namespaces](#text00000.html#_Toc756318)

[Section 27.4: What are Namespaces?](#text00000.html#_Toc756319)

[Chapter 28: Sessions](#text00000.html#_Toc756320)

[Section 28.1: session\_start() Options](#text00000.html#_Toc756321)

[Section 28.2: Session Locking](#text00000.html#_Toc756322)

[Section 28.3: Manipulating session data](#text00000.html#_Toc756323)

[Section 28.4: Destroy an entire session](#text00000.html#_Toc756324)

[Section 28.5: Safe Session Start With no Errors](#text00000.html#_Toc756325)

[Section 28.6: Session name](#text00000.html#_Toc756326)

[Chapter 29: Cookies](#text00000.html#_Toc756327)

[Section 29.1: Modifying a Cookie](#text00000.html#_Toc756328)

[Section 29.2: Setting a Cookie](#text00000.html#_Toc756329)

[Section 29.3: Checking if a Cookie is Set](#text00000.html#_Toc756330)

[Section 29.4: Removing a Cookie](#text00000.html#_Toc756331)

[Section 29.5: Retrieving a Cookie](#text00000.html#_Toc756332)

[Chapter 30: Output Buering](#text00000.html#_Toc756333)

[Section 30.1: Basic usage getting content between buers and clearing](#text00000.html#_Toc756334)

[Section 30.2: Processing the buer via a callback](#text00000.html#_Toc756335)

[Section 30.3: Nested output buers](#text00000.html#_Toc756336)

[Section 30.4: Running output buer before any content](#text00000.html#_Toc756337)

[Section 30.5: Stream output to client](#text00000.html#_Toc756338)

[Section 30.6: Using Output buer to store contents in a file, useful for reports, invoices etc](#text00000.html#_Toc756339)

[Section 30.7: Typical usage and reasons for using ob\_start](#text00000.html#_Toc756340)

[Section 30.8: Capturing the output buer to re-use later](#text00000.html#_Toc756341)

[Chapter 31: JSON](#text00000.html#_Toc756342)

[Section 31.1: Decoding a JSON string](#text00000.html#_Toc756343)

[Section 31.2: Encoding a JSON string](#text00000.html#_Toc756344)

[Section 31.3: Debugging JSON errors](#text00000.html#_Toc756345)

[Section 31.4: Using JsonSerializable in an Object](#text00000.html#_Toc756346)

[Section 31.5: Header json and the returned response](#text00000.html#_Toc756347)

[Chapter 32: SOAP Client](#text00000.html#_Toc756348)

[Section 32.1: WSDL Mode](#text00000.html#_Toc756349)

[Section 32.2: Non-WSDL Mode](#text00000.html#_Toc756350)

[Section 32.3: Classmaps](#text00000.html#_Toc756351)

[Section 32.4: Tracing SOAP request and response](#text00000.html#_Toc756352)

[Chapter 33: Using cURL in PHP](#text00000.html#_Toc756353)

[Section 33.1: Basic Usage (GET Requests)](#text00000.html#_Toc756354)

[Section 33.2: POST Requests](#text00000.html#_Toc756355)

[Section 33.3: Using Cookies](#text00000.html#_Toc756356)

[Section 33.4: Using multi\_curl to make multiple POST requests](#text00000.html#_Toc756357)

[Section 33.5: Sending multi-dimensional data and multiple files with CurlFile in one request](#text00000.html#_Toc756358)

[Section 33.6: Creating and sending a request with a custom method](#text00000.html#_Toc756359)

[Section 33.7: Get and Set custom http headers in php](#text00000.html#_Toc756360)

[Chapter 34: Reflection](#text00000.html#_Toc756361)

[Section 34.1: Feature detection of classes or objects](#text00000.html#_Toc756362)

[Section 34.2: Testing private/protected methods](#text00000.html#_Toc756363)

[Section 34.3: Accessing private and protected member variables](#text00000.html#_Toc756364)

[Chapter 35: Dependency Injection](#text00000.html#_Toc756365)

[Section 35.1: Constructor Injection](#text00000.html#_Toc756366)

[Section 35.2: Setter Injection](#text00000.html#_Toc756367)

[Section 35.3: Container Injection](#text00000.html#_Toc756368)

[Chapter 36: XML](#text00000.html#_Toc756369)

[Section 36.1: Create a XML using DomDocument](#text00000.html#_Toc756370)

[Section 36.2: Read a XML document with DOMDocument](#text00000.html#_Toc756371)

[Section 36.3: Leveraging XML with PHP's SimpleXML Library](#text00000.html#_Toc756372)

[Section 36.4: Create an XML file using XMLWriter](#text00000.html#_Toc756373)

[Section 36.5: Read a XML document with SimpleXML](#text00000.html#_Toc756374)

[Chapter 37: SimpleXML](#text00000.html#_Toc756375)

[Section 37.1: Loading XML data into simplexml](#text00000.html#_Toc756376)

[Chapter 38: Parsing HTML](#text00000.html#_Toc756377)

[Section 38.1: Parsing HTML from a string](#text00000.html#_Toc756378)

[Section 38.2: Using XPath](#text00000.html#_Toc756379)

[Section 38.3: SimpleXML](#text00000.html#_Toc756380)

[Chapter 39: Regular Expressions (regexp/PCRE)](#text00000.html#_Toc756381)

[Section 39.1: Global RegExp match](#text00000.html#_Toc756382)

[Section 39.2: String matching with regular expressions](#text00000.html#_Toc756383)

[Section 39.3: Split string into array by a regular expression](#text00000.html#_Toc756384)

[Section 39.4: String replacing with regular expression](#text00000.html#_Toc756385)

[Section 39.5: String replace with callback](#text00000.html#_Toc756386)

[Chapter 40: Traits](#text00000.html#_Toc756387)

[Section 40.1: What is a Trait?](#text00000.html#_Toc756388)

[Section 40.2: Traits to facilitate horizontal code reuse](#text00000.html#_Toc756389)

[Section 40.3: Conflict Resolution](#text00000.html#_Toc756390)

[Section 40.4: Implementing a Singleton using Traits](#text00000.html#_Toc756391)

[Section 40.5: Traits to keep classes clean](#text00000.html#_Toc756392)

[Section 40.6: Multiple Traits Usage](#text00000.html#_Toc756393)

[Section 40.7: Changing Method Visibility](#text00000.html#_Toc756394)

[Chapter 41: Composer Dependency Manager](#text00000.html#_Toc756395)

[Section 41.1: What is Composer?](#text00000.html#_Toc756396)

[Section 41.2: Autoloading with Composer](#text00000.html#_Toc756397)

[Section 41.3: Dierence between 'composer install' and 'composer update'](#text00000.html#_Toc756398)

[Section 41.4: Composer Available Commands](#text00000.html#_Toc756399)

[Section 41.5: Benefits of Using Composer](#text00000.html#_Toc756400)

[Section 41.6: Installation](#text00000.html#_Toc756401)

[Chapter 42: Magic Methods](#text00000.html#_Toc756402)

[Section 42.1: \_\_call() and \_\_callStatic()](#text00000.html#_Toc756403)

[Section 42.2: \_\_get(), \_\_set(), \_\_isset() and \_\_unset()](#text00000.html#_Toc756404)

[Section 42.3: \_\_construct() and \_\_destruct()](#text00000.html#_Toc756405)

[Section 42.4: \_\_toString()](#text00000.html#_Toc756406)

[Section 42.5: \_\_clone()](#text00000.html#_Toc756407)

[Section 42.6: \_\_invoke()](#text00000.html#_Toc756408)

[Section 42.7: \_\_sleep() and \_\_wakeup()](#text00000.html#_Toc756409)

[Section 42.8: \_\_debugInfo()](#text00000.html#_Toc756410)

[Chapter 43: File handling](#text00000.html#_Toc756411)

[Section 43.1: Convenience functions](#text00000.html#_Toc756412)

[Section 43.2: Deleting files and directories](#text00000.html#_Toc756413)

[Section 43.3: Getting file information](#text00000.html#_Toc756414)

[Section 43.4: Stream-based file IO](#text00000.html#_Toc756415)

[Section 43.5: Moving and Copying files and directories](#text00000.html#_Toc756416)

[Section 43.6: Minimize memory usage when dealing with large files](#text00000.html#_Toc756417)

[Chapter 44: Streams](#text00000.html#_Toc756418)

[Section 44.1: Registering a stream wrapper](#text00000.html#_Toc756419)

[Chapter 45: Type hinting](#text00000.html#_Toc756420)

[Section 45.1: Type hinting classes and interfaces](#text00000.html#_Toc756421)

[Section 45.2: Type hinting scalar types, arrays and callables](#text00000.html#_Toc756422)

[Section 45.3: Nullable type hints](#text00000.html#_Toc756423)

[Section 45.4: Type hinting generic objects](#text00000.html#_Toc756424)

[Section 45.5: Type Hinting No Return(Void)](#text00000.html#_Toc756425)

[Chapter 46: Filters & Filter Functions](#text00000.html#_Toc756426)

[Section 46.1: Validating Boolean Values](#text00000.html#_Toc756427)

[Section 46.2: Validating A Number Is A Float](#text00000.html#_Toc756428)

[Section 46.3: Validate A MAC Address](#text00000.html#_Toc756429)

[Section 46.4: Sanitze Email Addresses](#text00000.html#_Toc756430)

[Section 46.5: Sanitize Integers](#text00000.html#_Toc756431)

[Section 46.6: Sanitize URLs](#text00000.html#_Toc756432)

[Section 46.7: Validate Email Address](#text00000.html#_Toc756433)

[Section 46.8: Validating A Value Is An Integer](#text00000.html#_Toc756434)

[Section 46.9: Validating An Integer Falls In A Range](#text00000.html#_Toc756435)

[Section 46.10: Validate a URL](#text00000.html#_Toc756436)

[Section 46.11: Sanitize Floats](#text00000.html#_Toc756437)

[Section 46.12: Validate IP Addresses](#text00000.html#_Toc756438)

[Section 46.13: Sanitize filters](#text00000.html#_Toc756439)

[Chapter 47: Generators](#text00000.html#_Toc756440)

[Section 47.1: The Yield Keyword](#text00000.html#_Toc756441)

[Section 47.2: Reading a large file with a generator](#text00000.html#_Toc756442)

[Section 47.3: Why use a generator?](#text00000.html#_Toc756443)

[Section 47.4: Using the send()-function to pass values to a generator](#text00000.html#_Toc756444)

[Chapter 48: UTF-8](#text00000.html#_Toc756445)

[Section 48.1: Input](#text00000.html#_Toc756446)

[Section 48.2: Output](#text00000.html#_Toc756447)

[Section 48.3: Data Storage and Access](#text00000.html#_Toc756448)

[Chapter 49: Unicode Support in PHP](#text00000.html#_Toc756449)

[Section 49.1: Converting Unicode characters to “\\uxxxx” format using PHP](#text00000.html#_Toc756450)

[Section 49.2: Converting Unicode characters to their numeric value and/or HTML entities using PHP](#text00000.html#_Toc756451)

[Section 49.3: Intl extention for Unicode support](#text00000.html#_Toc756452)

[Chapter 50: URLs](#text00000.html#_Toc756453)

[Section 50.1: Parsing a URL](#text00000.html#_Toc756454)

[Section 50.2: Build an URL-encoded query string from an array](#text00000.html#_Toc756455)

[Section 50.3: Redirecting to another URL](#text00000.html#_Toc756456)

[Chapter 51: How to break down an URL](#text00000.html#_Toc756457)

[Section 51.1: Using parse\_url()](#text00000.html#_Toc756458)

[Section 51.2: Using explode()](#text00000.html#_Toc756459)

[Section 51.3: Using basename()](#text00000.html#_Toc756460)

[Chapter 52: Object Serialization](#text00000.html#_Toc756461)

[Section 52.1: Serialize / Unserialize](#text00000.html#_Toc756462)

[Section 52.2: The Serializable interface](#text00000.html#_Toc756463)

[Chapter 53: Serialization](#text00000.html#_Toc756464)

[Section 53.1: Serialization of dierent types](#text00000.html#_Toc756465)

[Section 53.2: Security Issues with unserialize](#text00000.html#_Toc756466)

[Chapter 54: Closure](#text00000.html#_Toc756467)

[Section 54.1: Basic usage of a closure](#text00000.html#_Toc756468)

[Section 54.2: Using external variables](#text00000.html#_Toc756469)

[Section 54.3: Basic closure binding](#text00000.html#_Toc756470)

[Section 54.4: Closure binding and scope](#text00000.html#_Toc756471)

[Section 54.5: Binding a closure for one call](#text00000.html#_Toc756472)

[Section 54.6: Use closures to implement observer pattern](#text00000.html#_Toc756473)

[Chapter 55: Reading Request Data](#text00000.html#_Toc756474)

[Section 55.1: Reading raw POST data](#text00000.html#_Toc756475)

[Section 55.2: Reading POST data](#text00000.html#_Toc756476)

[Section 55.3: Reading GET data](#text00000.html#_Toc756477)

[Section 55.4: Handling file upload errors](#text00000.html#_Toc756478)

[Section 55.5: Passing arrays by POST](#text00000.html#_Toc756479)

[Section 55.6: Uploading files with HTTP PUT](#text00000.html#_Toc756480)

[Chapter 56: Type juggling and Non-Strict Comparison Issues](#text00000.html#_Toc756481)

[Section 56.1: What is Type Juggling?](#text00000.html#_Toc756482)

[Section 56.2: Reading from a file](#text00000.html#_Toc756483)

[Section 56.3: Switch surprises](#text00000.html#_Toc756484)

[Section 56.4: Strict typing](#text00000.html#_Toc756485)

[Chapter 57: Sockets](#text00000.html#_Toc756486)

[Section 57.1: TCP client socket](#text00000.html#_Toc756487)

[Section 57.2: TCP server socket](#text00000.html#_Toc756488)

[Section 57.3: UDP server socket](#text00000.html#_Toc756489)

[Section 57.4: Handling socket errors](#text00000.html#_Toc756490)

[Chapter 58: PDO](#text00000.html#_Toc756491)

[Section 58.1: Preventing SQL injection with Parameterized Queries](#text00000.html#_Toc756492)

[Section 58.2: Basic PDO Connection and Retrieval](#text00000.html#_Toc756493)

[Section 58.3: Database Transactions with PDO](#text00000.html#_Toc756494)

[Section 58.4: PDO: connecting to MySQL/MariaDB server](#text00000.html#_Toc756495)

[Section 58.5: PDO: Get number of aected rows by a query](#text00000.html#_Toc756496)

[Section 58.6: PDO::lastInsertId()](#text00000.html#_Toc756497)

[Chapter 59: PHP MySQLi](#text00000.html#_Toc756498)

[Section 59.1: Close connection](#text00000.html#_Toc756499)

[Section 59.2: MySQLi connect](#text00000.html#_Toc756500)

[Section 59.3: Loop through MySQLi results](#text00000.html#_Toc756501)

[Section 59.4: Prepared statements in MySQLi](#text00000.html#_Toc756502)

[Section 59.5: Escaping Strings](#text00000.html#_Toc756503)

[Section 59.6: Debugging SQL in MySQLi](#text00000.html#_Toc756504)

[Section 59.7: MySQLi query](#text00000.html#_Toc756505)

[Section 59.8: How to get data from a prepared statement](#text00000.html#_Toc756506)

[Section 59.9: MySQLi Insert ID](#text00000.html#_Toc756507)

[Chapter 60: SQLite3](#text00000.html#_Toc756508)

[Section 60.1: SQLite3 Quickstart Tutorial](#text00000.html#_Toc756509)

[Section 60.2: Querying a database](#text00000.html#_Toc756510)

[Section 60.3: Retrieving only one result](#text00000.html#_Toc756511)

[Chapter 61: Using MongoDB](#text00000.html#_Toc756512)

[Section 61.1: Connect to MongoDB](#text00000.html#_Toc756513)

[Section 61.2: Get multiple documents - find()](#text00000.html#_Toc756514)

[Section 61.3: Get one document - findOne()](#text00000.html#_Toc756515)

[Section 61.4: Insert document](#text00000.html#_Toc756516)

[Section 61.5: Update a document](#text00000.html#_Toc756517)

[Section 61.6: Delete a document](#text00000.html#_Toc756518)

[Chapter 62: mongo-php](#text00000.html#_Toc756519)

[Section 62.1: Everything in between MongoDB and Php](#text00000.html#_Toc756520)

[Chapter 63: Using Redis with PHP](#text00000.html#_Toc756521)

[Section 63.1: Connecting to a Redis instance](#text00000.html#_Toc756522)

[Section 63.2: Installing PHP Redis on Ubuntu](#text00000.html#_Toc756523)

[Section 63.3: Executing Redis commands in PHP](#text00000.html#_Toc756524)

[Chapter 64: Sending Email](#text00000.html#_Toc756525)

[Section 64.1: Sending Email - The basics, more details, and a full example](#text00000.html#_Toc756526)

[Section 64.2: Sending HTML Email Using mail()](#text00000.html#_Toc756527)

[Section 64.3: Sending Email With An Attachment Using mail()](#text00000.html#_Toc756528)

[Section 64.4: Sending Plain Text Email Using PHPMailer](#text00000.html#_Toc756529)

[Section 64.5: Sending HTML Email Using PHPMailer](#text00000.html#_Toc756530)

[Section 64.6: Sending Email With An Attachment Using PHPMailer](#text00000.html#_Toc756531)

[Section 64.7: Sending Plain Text Email Using Sendgrid](#text00000.html#_Toc756532)

[Section 64.8: Sending Email With An Attachment Using Sendgrid](#text00000.html#_Toc756533)

[Chapter 65: Using SQLSRV](#text00000.html#_Toc756534)

[Section 65.1: Retrieving Error Messages](#text00000.html#_Toc756535)

[Section 65.2: Fetching Query Results](#text00000.html#_Toc756536)

[Section 65.3: Creating a Connection](#text00000.html#_Toc756537)

[Section 65.4: Making a Simple Query](#text00000.html#_Toc756538)

[Section 65.5: Invoking a Stored Procedure](#text00000.html#_Toc756539)

[Section 65.6: Making a Parameterised Query](#text00000.html#_Toc756540)

[Chapter 66: Command Line Interface (CLI)](#text00000.html#_Toc756541)

[Section 66.1: Handling Program Options](#text00000.html#_Toc756542)

[Section 66.2: Argument Handling](#text00000.html#_Toc756543)

[Section 66.3: Input and Output Handling](#text00000.html#_Toc756544)

[Section 66.4: Return Codes](#text00000.html#_Toc756545)

[Section 66.5: Restrict script execution to command line](#text00000.html#_Toc756546)

[Section 66.6: Behavioural dierences on the command line](#text00000.html#_Toc756547)

[Section 66.7: Running your script](#text00000.html#_Toc756548)

[Section 66.8: Edge Cases of getopt()](#text00000.html#_Toc756549)

[Section 66.9: Running built-in web server](#text00000.html#_Toc756550)

[Chapter 67: Localization](#text00000.html#_Toc756551)

[Section 67.1: Localizing strings with gettext()](#text00000.html#_Toc756552)

[Chapter 68: Headers Manipulation](#text00000.html#_Toc756553)

[Section 68.1: Basic Setting of a Header](#text00000.html#_Toc756554)

[Chapter 69: Coding Conventions](#text00000.html#_Toc756555)

[Section 69.1: PHP Tags](#text00000.html#_Toc756556)

[Chapter 70: Asynchronous programming](#text00000.html#_Toc756557)

[Section 70.1: Advantages of Generators](#text00000.html#_Toc756558)

[Section 70.2: Using Icicle event loop](#text00000.html#_Toc756559)

[Section 70.3: Spawning non-blocking processes with proc\_open()](#text00000.html#_Toc756560)

[Section 70.4: Reading serial port with Event and DIO](#text00000.html#_Toc756561)

[Section 70.5: HTTP Client Based on Event Extension](#text00000.html#_Toc756562)

[Section 70.6: HTTP Client Based on Ev Extension](#text00000.html#_Toc756563)

[Section 70.7: Using Amp event loop](#text00000.html#_Toc756564)

[Chapter 71: How to Detect Client IP Address](#text00000.html#_Toc756565)

[Section 71.1: Proper use of HTTP\_X\_FORWARDED\_FOR](#text00000.html#_Toc756566)

[Chapter 72: Create PDF files in PHP](#text00000.html#_Toc756567)

[Section 72.1: Getting Started with PDFlib](#text00000.html#_Toc756568)

[Chapter 73: YAML in PHP](#text00000.html#_Toc756569)

[Section 73.1: Installing YAML extension](#text00000.html#_Toc756570)

[Section 73.2: Using YAML to store application configuration](#text00000.html#_Toc756571)

[Chapter 74: Image Processing with GD](#text00000.html#_Toc756572)

[Section 74.1: Image output](#text00000.html#_Toc756573)

[Section 74.2: Creating an image](#text00000.html#_Toc756574)

[Section 74.3: Image Cropping and Resizing](#text00000.html#_Toc756575)

[Chapter 75: Imagick](#text00000.html#_Toc756576)

[Section 75.1: First Steps](#text00000.html#_Toc756577)

[Section 75.2: Convert Image into base64 String](#text00000.html#_Toc756578)

[Chapter 76: SOAP Server](#text00000.html#_Toc756579)

[Section 76.1: Basic SOAP Server](#text00000.html#_Toc756580)

[Chapter 77: Machine learning](#text00000.html#_Toc756581)

[Section 77.1: Classification using PHP-ML](#text00000.html#_Toc756582)

[Section 77.2: Regression](#text00000.html#_Toc756583)

[Section 77.3: Clustering](#text00000.html#_Toc756584)

[Chapter 78: Cache](#text00000.html#_Toc756585)

[Section 78.1: Caching using memcache](#text00000.html#_Toc756586)

[Section 78.2: Cache Using APC Cache](#text00000.html#_Toc756587)

[Chapter 79: Autoloading Primer](#text00000.html#_Toc756588)

[Section 79.1: Autoloading as part of a framework solution](#text00000.html#_Toc756589)

[Section 79.2: Inline class definition, no loading required](#text00000.html#_Toc756590)

[Section 79.3: Manual class loading with require](#text00000.html#_Toc756591)

[Section 79.4: Autoloading replaces manual class definition loading](#text00000.html#_Toc756592)

[Section 79.5: Autoloading with Composer](#text00000.html#_Toc756593)

[Chapter 80: SPL data structures](#text00000.html#_Toc756594)

[Section 80.1: SplFixedArray](#text00000.html#_Toc756595)

[Chapter 81: IMAP](#text00000.html#_Toc756596)

[Section 81.1: Connecting to a mailbox](#text00000.html#_Toc756597)

[Section 81.2: Install IMAP extension](#text00000.html#_Toc756598)

[Section 81.3: List all folders in the mailbox](#text00000.html#_Toc756599)

[Section 81.4: Finding messages in the mailbox](#text00000.html#_Toc756600)

[Chapter 82: HTTP Authentication](#text00000.html#_Toc756601)

[Section 82.1: Simple authenticate](#text00000.html#_Toc756602)

[Chapter 83: WebSockets](#text00000.html#_Toc756603)

[Section 83.1: Simple TCP/IP server](#text00000.html#_Toc756604)

[Chapter 84: BC Math (Binary Calculator)](#text00000.html#_Toc756605)

[Section 84.1: Using bcmath to read/write a binary long on 32-bit system](#text00000.html#_Toc756606)

[Section 84.2: Comparison between BCMath and float arithmetic operations](#text00000.html#_Toc756607)

[Chapter 85: Docker deployment](#text00000.html#_Toc756608)

[Section 85.1: Get docker image for php](#text00000.html#_Toc756609)

[Section 85.2: Writing dockerfile](#text00000.html#_Toc756610)

[Section 85.3: Building image](#text00000.html#_Toc756611)

[Section 85.4: Starting application container](#text00000.html#_Toc756612)

[Chapter 86: APCu](#text00000.html#_Toc756613)

[Section 86.1: Iterating over Entries](#text00000.html#_Toc756614)

[Section 86.2: Simple storage and retrieval](#text00000.html#_Toc756615)

[Section 86.3: Store information](#text00000.html#_Toc756616)

[Chapter 87: PHP Built in server](#text00000.html#_Toc756617)

[Section 87.1: Running the built in server](#text00000.html#_Toc756618)

[Section 87.2: built in server with specific directory and router script](#text00000.html#_Toc756619)

[Chapter 88: PSR](#text00000.html#_Toc756620)

[Section 88.1: PSR-4: Autoloader](#text00000.html#_Toc756621)

[Section 88.2: PSR-1: Basic Coding Standard](#text00000.html#_Toc756622)

[Chapter 89: PHPDoc](#text00000.html#_Toc756623)

[Section 89.1: Describing a variable](#text00000.html#_Toc756624)

[Section 89.2: Adding metadata to functions](#text00000.html#_Toc756625)

[Section 89.3: Describing parameters](#text00000.html#_Toc756626)

[Section 89.4: Collections](#text00000.html#_Toc756627)

[Section 89.5: Adding metadata to files](#text00000.html#_Toc756628)

[Section 89.6: Inheriting metadata from parent structures](#text00000.html#_Toc756629)

[Chapter 90: Design Patterns](#text00000.html#_Toc756630)

[Section 90.1: Method Chaining in PHP](#text00000.html#_Toc756631)

[Chapter 91: Compile PHP Extensions](#text00000.html#_Toc756632)

[Section 91.1: Compiling on Linux](#text00000.html#_Toc756633)

[Chapter 92: Common Errors](#text00000.html#_Toc756634)

[Section 92.1: Call fetch\_assoc on boolean](#text00000.html#_Toc756635)

[Section 92.2: Unexpected $end](#text00000.html#_Toc756636)

[Chapter 93: Compilation of Errors and Warnings](#text00000.html#_Toc756637)

[Section 93.1: Parse error: syntax error, unexpected T\_PAAMAYIM\_NEKUDOTAYIM](#text00000.html#_Toc756638)

[Section 93.2: Notice: Undefined index](#text00000.html#_Toc756639)

[Section 93.3: Warning: Cannot modify header information - headers already sent](#text00000.html#_Toc756640)

[Chapter 94: Exception Handling and Error Reporting](#text00000.html#_Toc756641)

[Section 94.1: Setting error reporting and where to display them](#text00000.html#_Toc756642)

[Section 94.2: Logging fatal errors](#text00000.html#_Toc756643)

[Chapter 95: Debugging](#text00000.html#_Toc756644)

[Section 95.1: Dumping variables](#text00000.html#_Toc756645)

[Section 95.2: Displaying errors](#text00000.html#_Toc756646)

[Section 95.3: phpinfo()](#text00000.html#_Toc756647)

[Section 95.4: Xdebug](#text00000.html#_Toc756648)

[Section 95.5: Error Reporting (use them both)](#text00000.html#_Toc756649)

[Section 95.6: phpversion()](#text00000.html#_Toc756650)

[Chapter 96: Unit Testing](#text00000.html#_Toc756651)

[Section 96.1: Testing class rules](#text00000.html#_Toc756652)

[Section 96.2: PHPUnit Data Providers](#text00000.html#_Toc756653)

[Section 96.3: Test exceptions](#text00000.html#_Toc756654)

[Chapter 97: Performance](#text00000.html#_Toc756655)

[Section 97.1: Profiling with Xdebug](#text00000.html#_Toc756656)

[Section 97.2: Memory Usage](#text00000.html#_Toc756657)

[Section 97.3: Profiling with XHProf](#text00000.html#_Toc756658)

[Chapter 98: Multiprocessing](#text00000.html#_Toc756659)

[Section 98.1: Multiprocessing using built-in fork functions](#text00000.html#_Toc756660)

[Section 98.2: Creating child process using fork](#text00000.html#_Toc756661)

[Section 98.3: Inter-Process Communication](#text00000.html#_Toc756662)

[Chapter 99: Multi Threading Extension](#text00000.html#_Toc756663)

[Section 99.1: Getting Started](#text00000.html#_Toc756664)

[Section 99.2: Using Pools and Workers](#text00000.html#_Toc756665)

[Chapter 100: Secure Remeber Me](#text00000.html#_Toc756666)

[Section 100.1: “Keep Me Logged In” - the best approach](#text00000.html#_Toc756667)

[Chapter 101: Security](#text00000.html#_Toc756668)

[Section 101.1: PHP Version Leakage](#text00000.html#_Toc756669)

[Section 101.2: Cross-Site Scripting (XSS)](#text00000.html#_Toc756670)

[Section 101.3: Cross-Site Request Forgery](#text00000.html#_Toc756671)

[Section 101.4: Command Line Injection](#text00000.html#_Toc756672)

[Section 101.5: Stripping Tags](#text00000.html#_Toc756673)

[Section 101.6: File Inclusion](#text00000.html#_Toc756674)

[Section 101.7: Error Reporting](#text00000.html#_Toc756675)

[Section 101.8: Uploading files](#text00000.html#_Toc756676)

[Chapter 102: Cryptography](#text00000.html#_Toc756677)

[Section 102.1: Symmetric Encryption and Decryption of large Files with OpenSSL](#text00000.html#_Toc756678)

[Section 102.2: Symmetric Cipher](#text00000.html#_Toc756679)

[Chapter 103: Password Hashing Functions](#text00000.html#_Toc756680)

[Section 103.1: Creating a password hash](#text00000.html#_Toc756681)

[Section 103.2: Determine if an existing password hash can be upgraded to a stronger algorithm](#text00000.html#_Toc756682)

[Section 103.3: Verifying a password against a hash](#text00000.html#_Toc756683)

[Chapter 104: Contributing to the PHP Manual](#text00000.html#_Toc756684)

[Section 104.1: Improve the ocial documentation](#text00000.html#_Toc756685)

[Section 104.2: Tips for contributing to the manual](#text00000.html#_Toc756686)

[Chapter 105: Contributing to the PHP Core](#text00000.html#_Toc756687)

[Section 105.1: Setting up a basic development environment](#text00000.html#_Toc756688)

[Appendix A: Installing a PHP environment on Windows](#text00000.html#_Toc756689)

[Section A.1: Download, Install and use WAMP](#text00000.html#_Toc756690)

[Section A.2: Install PHP and use it with IIS](#text00000.html#_Toc756691)

[Section A.3: Download and Install XAMPP](#text00000.html#_Toc756692)

[Appendix B: Installing on Linux/Unix Environments](#text00000.html#_Toc756693)

[Section B.1: Command Line Install Using APT for PHP 7](#text00000.html#_Toc756694)

[Section B.2: Installing in Enterprise Linux distributions (CentOS, Scientific Linux, etc)](#text00000.html#_Toc756695)

[Credits](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX)

[You may also like](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX)

  

# Chapter 1: Getting started with PHP

## Section 1.1: HTML output from web server

PHP can be used to add content to HTML files. While HTML is processed directly by a web browser, PHP scripts are executed by a web server and the resulting HTML is sent to the browser.

 
| Hello World ! |
| --- |

The following HTML markup contains a PHP statement that will add  to the output:

![](Image00000.jpg)

When this is saved as a PHP script and executed by a web server, the following HTML will be sent to the user's browser:

![](Image00001.jpg)

![](Image00002.jpg)

PHP 5.x Version ≥ 5.4

echo also has a shortcut syntax, which lets you immediately print a value. Prior to PHP 5.4.0, this short syntax only works with the [short\_open\_tag](http://php.net/manual/en/ini.core.php#ini.short-open-tag) configuration setting enabled.

For example, consider the following code:

![](Image00003.jpg)

Its output is identical to the output of the following:

![](Image00004.jpg)

In real-world applications, all data output by PHP to an HTML page should be properly escaped to prevent XSS (Cross-site scripting) attacks or text corruption.

 
| <?= ... ?> |
| --- |

See also: Strings and [PSR-1](http://www.php-fig.org/psr/psr-1/) , which describes best practices, including the proper use of short tags ().

## Section 1.2: Hello, World!

The most widely used language construct to print output in PHP is echo :

![](Image00005.jpg)

Alternatively, you can also use print :

![](Image00006.jpg)

Both statements perform the same function, with minor differences:

![](Image00007.jpg)echo has a void return, whereas print returns an int with a value of 1

echo can take multiple arguments (without parentheses only), whereas print only takes one argument echo is [slightly faster](http://www.phpbench.com/) than print

Both echo and print are language constructs, not functions. That means they do not require parentheses around their arguments. For cosmetic consistency with functions, parentheses can be included. Extensive examples of the use of echo and print are available elsewhere.

C-style printf and related functions are available as well, as in the following example:

![](Image00008.jpg)

See Outputting the value of a variable for a comprehensive introduction of outputting variables in PHP.

## Section 1.3: Non-HTML output from web server

In some cases, when working with a web server, overriding the web server's default content type may be required.

There may be cases where you need to send data as plain text , JSON , or XML , for example.

 
| [heade](http://php.net/manual/en/function.header.php) [r](http://php.net/manual/en/function.header.php) || [(](http://php.net/manual/en/function.header.php) [)](http://php.net/manual/en/function.header.php) function can send a raw HTTP header. You can add the || Content || \- || Type |
| --- | --- | --- | --- | --- |

The  header to notify the browser of the content we are sending.

 
| Content || \- || Type || as || text || / || plain |
| --- | --- | --- | --- | --- | --- | --- |

Consider the following code, where we set :

![](Image00009.jpg)

This will produce a plain text document with the following content:

![](Image00010.jpg)Hello World

 
| application || / || json |
| --- | --- | --- |

To produce [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) content, use the  content type instead:

![](Image00011.jpg)

 
| application || / || json |
| --- | --- | --- |

This will produce a document of type  with the following content:

![](Image00012.jpg)              {"response":"Hello World"}

 
| header |
| --- |

Note that the () function must be called before PHP produces any output, or the web server will have already sent headers for the response. So, consider the following code:

![](Image00013.jpg)

This will produce a warning:

![](Image00014.jpg)Warning: Cannot modify header information - headers already sent by (output started at /dir/example.php:2) in /dir/example.php on line 3

 
| header |
| --- |

When using () , its output needs to be the first byte that's sent from the server. For this reason it's important to not have empty lines or spaces in the beginning of the file before the PHP opening tag <?php . For the same reason, it is considered best practice (see [PSR-2](http://www.php-fig.org/psr/psr-2/#2-2-files) ) to omit the PHP closing tag ?> from files that contain only PHP and from blocks of PHP code at the very end of a file.

View the output buffering section to learn how to 'catch' your content into a variable to output later, for example, after outputting headers.

## Section 1.4: PHP built-in server

PHP 5.4+ comes with a built-in development server. It can be used to run applications without having to install a production HTTP server such as nginx or Apache. The built-in server is only designed to be used for development and testing purposes.

It can be started by using the \-S flag: ![](Image00015.jpg)php \- S < host / ip \>:< port \> Example usage

 
| index || . || php |
| --- | --- | --- |

1.    Create an  file containing:

![](Image00016.jpg)

 
| php || \- || S localhost || : || 8080 |
| --- | --- | --- | --- | --- |

2.    Run the command  from the command line. Do not include http://

. This will start a web server listening on port 8080 using the current directory that you are in as the document root.

 
| http || : || //localhost:8080 |
| --- | --- | --- |

3.    Open the browser and navigate to . You should see your "Hello World" page.

Configuration

To override the default document root (i.e. the current directory), use the \-t flag:

![](Image00017.jpg)

 
| public || / directory in your project you can serve your project from that directory using || php |
| --- | --- | --- |

E.g. if you have a \- S

 
| localhost || : || 8080 || \- || t public |
| --- | --- | --- | --- | --- |

/ .

Logs

Every time a request is made from the development server, a log entry like the one below is written to the command line.

![](Image00018.jpg)

## Section 1.5: PHP CLI

PHP can also be run from command line directly using the CLI (Command Line Interface).

CLI is basically the same as PHP from web servers, except some differences in terms of standard input and output. Triggering

The PHP CLI allows four ways to run PHP code:

1.    Standard input. Run the php command without any arguments, but pipe PHP code into it: echo '<?php echo "Hello world!";' | php

2.    Filename as argument. Run the php command with the name of a PHP source file as the first argument: php hello\_world.php

3.    Code as argument. Use the \-r option in the php command, followed by the code to run. The <?php open tags are not required, as everything in the argument is considered as PHP code: php -r 'echo "Hello world!";'

4.    Interactive shell. Use the \-a option in the php command to launch an interactive shell. Then, type (or paste) PHP code and hit return : $ php -a Interactive mode enabled php > echo "Hello world!"; Hello world!

Output

All functions or controls that produce HTML output in web server PHP can be used to produce output in the stdout stream (file descriptor 1), and all actions that produce output in error logs in web server PHP will produce output in the stderr stream (file descriptor 2).

![](Image00019.jpg)

Shell command line

![](Image00020.jpg)

Input

See: Command Line Interface (CLI)

## Section 1.6: Instruction Separation

Just like most other C-style languages, each statement is terminated with a semicolon. Also, a closing tag is used to terminate the last line of code of the PHP block.

 
| echo "No error" |
| --- |

If the last line of PHP code ends with a semicolon, the closing tag is optional if there is no code following that final line of code. For example, we can leave out the closing tag after ; in the following example:

![](Image00021.jpg) <?php echo "No error" ; // no closing tag is needed as long as there is no code below

However, if there is any other code following your PHP code block, the closing tag is no longer optional:

![](Image00022.jpg)

![](Image00023.jpg)

We can also leave out the semicolon of the last statement in a PHP code block if that code block has a closing tag:

![](Image00024.jpg)

It is generally recommended to always use a semicolon and use a closing tag for every PHP code block except the last PHP code block, if no more code follows that PHP code block.

So, your code should basically look like this:

![](Image00025.jpg)

## Section 1.7: PHP Tags

There are three kinds of tags to denote PHP blocks in a file. The PHP parser is looking for the opening and (if present) closing tags to delimit the code to interpret.

Standard Tags

These tags are the standard method to embed PHP code in a file.

![](Image00026.jpg)

PHP 5.x Version ≥ 5.4

Echo Tags

These tags are available in all PHP versions, and since PHP 5.4 are always enabled. In previous versions, echo tags could only be enabled in conjunction with short tags.

![](Image00027.jpg)

Short Tags

You can disable or enable these tags with the option short\_open\_tag .

![](Image00028.jpg)

Short tags:

![](Image00029.jpg)are disallowed in all major PHP [coding standards](http://www.php-fig.org/psr/psr-1/) are discouraged in [the official documentation](https://secure.php.net/manual/en/language.basic-syntax.phptags.php) are disabled by default in most distributions interfere with inline XML's processing instructions

are not accepted in code submissions by most open source projects

PHP 5.x Version ≤ 5.6 ASP Tags

By enabling the asp\_tags option, ASP-style tags can be used.

![](Image00030.jpg)

These are an historic quirk and should never be used. They were removed in PHP 7.0.

  

# Chapter 2: Variables

## Section 2.1: Accessing A Variable Dynamically By Name (Variable variables)

Variables can be accessed via dynamic variable names. The name of a variable can be stored in another variable, allowing it to be accessed dynamically. Such variables are known as variable variables.

To turn a variable into a variable variable, you put an extra $ put in front of your variable.

![](Image00031.jpg)

Variable variables are useful for mapping function/method calls:

![](Image00032.jpg)

This becomes particularly helpful in PHP classes:

![](Image00033.jpg)

It is possible, but not required to put $variableName between {} :

![](Image00034.jpg)

The following examples are both equivalent and output "baz":

![](Image00035.jpg)

![](Image00036.jpg)

Using {} is only mandatory when the name of the variable is itself an expression, like this:

![](Image00037.jpg)

It is nevertheless recommended to always use {} , because it's more readable.

While it is not recommended to do so, it is possible to chain this behavior:

$$$$$$$$DoNotTryThisAtHomeKids \= $value ;

![](Image00038.jpg) It's important to note that the excessive usage of variable variables is considered a bad practice by many developers. Since they're not well-suited for static analysis by modern IDEs, large codebases with many variable variables (or dynamic method invocations) can quickly become difficult to maintain.

Differences between PHP5 and PHP7

Another reason to always use {} or () , is that PHP5 and PHP7 have a slightly different way of dealing with dynamic variables, which results in a different outcome in some cases.

In PHP7, dynamic variables, properties, and methods will now be evaluated strictly in left-to-right order, as opposed to the mix of special cases in PHP5. The examples below show how the order of evaluation has changed.

 
| $$foo || \[ || 'bar' || \]\[ || 'baz' |
| --- | --- | --- | --- | --- |

Case 1 : \]

 
| $foo || \[ || 'bar' || \]\[ || 'baz' |
| --- | --- | --- | --- | --- |

 
| $$foo || )\[ || 'bar' || \]\[ || 'baz' |
| --- | --- | --- | --- | --- |

![](Image00039.jpg)PHP5 interpretation : $ {\]}

PHP7 interpretation : (\]

 
| $foo \-> $bar || \[ || 'baz' |
| --- | --- | --- |

Case 2 : \]

 
| $foo \-> || { || $bar || \[ || 'baz' |
| --- | --- | --- | --- | --- |

 
| $foo \-> $bar || )\[ || 'baz' |
| --- | --- | --- |

![](Image00040.jpg)PHP5 interpretation : \]}

PHP7 interpretation : (\]

 
| $foo \-> $bar || \[ || 'baz' |
| --- | --- | --- |

Case 3 : \]()

 
| $foo \-> || { || $bar || \[ || 'baz' |
| --- | --- | --- | --- | --- |

 
| $foo \-> $bar || )\[ || 'baz' |
| --- | --- | --- |

![](Image00041.jpg)PHP5 interpretation : \]}()

PHP7 interpretation : (\]()

 
| Foo :: $bar || \[ || 'baz' |
| --- | --- | --- |

Case 4 : \]()

 
| Foo :: || { || $bar || \[ || 'baz' |
| --- | --- | --- | --- | --- |

 
| Foo :: $bar || )\[ || 'baz' |
| --- | --- | --- |

![](Image00042.jpg)PHP5 interpretation : \]}()

PHP7 interpretation : (\]()

## Section 2.2: Data Types

There are different data types for different purposes. PHP does not have explicit type definitions, but the type of a variable is determined by the type of the value that is assigned, or by the type that it is casted to. This is a brief overview about the types, for a detailed documentation and examples, see the PHP types topic.

There are following data types in PHP: null, boolean, integer, float, string, object, resource and array.

Null

Null can be assigned to any variable. It represents a variable with no value.

![](Image00043.jpg)

This invalidates the variable and it's value would be undefined or void if called. The variable is cleared from memory and deleted by the garbage collector.

Boolean

This is the simplest type with only two possible values.

![](Image00044.jpg)

Booleans can be used to control the flow of code.

![](Image00045.jpg)

Integer

An integer is a whole number positive or negative. It can be in used with any number base. The size of an integer is platform-dependent. PHP does not support unsigned integers.

![](Image00046.jpg)

Float

Floating point numbers, "doubles" or simply called "floats" are decimal numbers.

![](Image00047.jpg)

Array

An array is like a list of values. The simplest form of an array is indexed by integer, and ordered by the index, with the first element lying at index 0.

$foo \= array (1, 2, 3); // An array of integers

![](Image00048.jpg) $bar \= \[ "A" , true , 123 \=> 5\]; // Short array syntax, PHP 5.4+

![](Image00049.jpg)

Arrays can also associate a key other than an integer index to a value. In PHP, all arrays are associative arrays behind the scenes, but when we refer to an 'associative array' distinctly, we usually mean one that contains one or more keys that aren't integers.

![](Image00050.jpg)

String

A string is like an array of characters.

![](Image00051.jpg)

Like an array, a string can be indexed to return its individual characters:

![](Image00052.jpg)

Object

An object is an instance of a class. Its variables and methods can be accessed with the \-> operator.

![](Image00053.jpg)

Resource

Resource variables hold special handles to opened files, database connections, streams, image canvas areas and the like (as it is stated in the [manual](https://secure.php.net/manual/en/language.types.resource.php#language.types.resource.casting) ).

![](Image00054.jpg) $fp \= fopen ( 'file.ext' , 'r' ); // fopen() is the function to open a file on disk as a resource. var\_dump ( $fp ); // output: resource(2) of type (stream)

 
| gettype |
| --- |

To get the type of a variable as a string, use the () function:

![](Image00055.jpg)

## Section 2.3: Global variable best practices

We can illustrate this problem with the following pseudo-code

![](Image00056.jpg)

Your first question here is an obvious one

![](Image00057.jpg)Where did $bob come from?

Are you confused? Good. You've just learned why globals are confusing and considered a bad practice .

If this were a real program, your next bit of fun is to go track down all instances of $bob and hope you find the right one (this gets worse if $bob is used everywhere). Worse, if someone else goes and defines $bob (or you forgot and reused that variable) your code can break (in the above code example, having the wrong object, or no object at all, would cause a fatal error).

 
| include || ( || 'file.php' |
| --- | --- | --- |

Since virtually all PHP programs make use of code like ); your job maintaining code like this becomes exponentially harder the more files you add.

Also, this makes the task of testing your applications very difficult. Suppose you use a global variable to hold your database connection:

![](Image00058.jpg)

In order to unit test this function, you have to override the global $dbConnector variable, run the tests and then reset it to its original value, which is very bug prone:

![](Image00059.jpg)

How do we avoid Globals?

The best way to avoid globals is a philosophy called Dependency Injection . This is where we pass the tools we need into the function or class.

![](Image00060.jpg)

This is much easier to understand and maintain. There's no guessing where $bob was set up because the caller is responsible for knowing that (it's passing us what we need to know). Better still, we can use [type declarations](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) to restrict what's being passed.

So we know that $bob is either an instance of the Bar class, or an instance of a child of Bar , meaning we know we can use the methods of that class. Combined with a standard autoloader (available since PHP 5.3), we can now go track down where Bar is defined. PHP 7.0 or later includes expanded type declarations, where you can also use scalar types (like int or string ).

Version = 4.1

Superglobal variables

Super globals in PHP are predefined variables, which are always available, can be accessed from any scope throughout the script.

There is no need to do global $variable; to access them within functions/methods, classes or files.

These PHP superglobal variables are listed below:

![](Image00061.jpg)[$GLOBALS](http://php.net/manual/en/reserved.variables.globals.php)

[$\_SERVER](http://php.net/manual/en/reserved.variables.server.php)

[$\_REQUEST](http://php.net/manual/en/reserved.variables.request.php)

[$\_POST](http://php.net/manual/en/reserved.variables.post.php)

[$\_GET](http://php.net/manual/en/reserved.variables.get.php)

[$\_FILES](http://php.net/manual/en/reserved.variables.files.php)

[$\_ENV](http://php.net/manual/en/reserved.variables.environment.php)

[$\_COOKIE](http://php.net/manual/en/reserved.variables.cookies.php)

[$\_SESSION](http://php.net/manual/en/reserved.variables.session.php)

## Section 2.4: Default values of uninitialized variables

Although not necessary in PHP however it is a very good practice to initialize variables. Uninitialized variables have a default value of their type depending on the context in which they are used:

Unset AND unreferenced

![](Image00062.jpg)

Boolean

![](Image00063.jpg)

String

![](Image00064.jpg)

Integer

![](Image00065.jpg)

Float/double

![](Image00066.jpg)

Array

![](Image00067.jpg)

Object

$unset\_obj \-> foo \= 'bar' ;

![](Image00068.jpg) var\_dump ( $unset\_obj ); // Outputs: object(stdClass)#1 (1) {  \["foo"\]=>  string(3) "bar" }

Relying on the default value of an uninitialized variable is problematic in the case of including one file into another which uses the same variable name.

## Section 2.5: Variable Value Truthiness and Identical Operator

In PHP, variable values have an associated "truthiness" so even non-boolean values will equate to true or false . This allows any variable to be used in a conditional block, e.g.

![](Image00069.jpg)

Here are some fundamental rules for different types of variable values:

![](Image00070.jpg)

![](Image00071.jpg)

 
| floatval || ( || '0' || ) ||   \== floatval || ( || '-0' |
| --- | --- | --- | --- | --- | --- | --- |

in its double-precision floating-point, i.e. ) is true .

![](Image00072.jpg)

IDENTICAL OPERATOR

In the [PHP Documentation for Comparison Operators](http://php.net/manual/en/language.operators.comparison.php) , there is an Identical Operator \=== . This operator can be used to check whether a variable is identical to a reference value:

![](Image00073.jpg)

It has a corresponding not identical operator !== :

![](Image00074.jpg)

 
| is\_null |
| --- |

The identical operator can be used as an alternative to language functions like () .

 
| strpos |
| --- |

USE CASE WITH ()

 
| strpos || ( || $haystack || , ||   $needle |
| --- | --- | --- | --- | --- |

The ) language function is used to locate the index at which $needle occurs in

 
| strpos |
| --- |

$haystack , or whether it occurs at all. The () function is case sensitive; if case-insensitive find is what you

 
| stripos || ( || $haystack || , ||   $needle |
| --- | --- | --- | --- | --- |

need you can go with )

The strpos & stripos function also contains third parameter offset (int) which if specified, search will start this number of characters counted from the beginning of the string. Unlike strrpos and strripos, the offset cannot be negative

The function can return:

![](Image00075.jpg)0 if $needle is found at the beginning of $haystack ; a non-zero integer specifying the index if $needle is found somewhere other than the beginning in

$haystack ; and value false if $needle is not found anywhere in $haystack .

 
| strpos |
| --- |

Because both 0 and false have truthiness false in PHP but represent distinct situations for () , it is important to distinguish between them and use the identical operator \=== to look exactly for false and not just a value that equates to false .

![](Image00076.jpg)

Alternatively, using the not identical operator:

![](Image00077.jpg)

# Chapter 3: Variable Scope

Variable scope refers to the regions of code where a variable may be accessed. This is also referred to as visibility . In PHP scope blocks are defined by functions, classes, and a global scope available throughout an application.

## Section 3.1: Superglobal variables

Superglobal variables are defined by PHP and can always be used from anywhere without the global keyword.

![](Image00078.jpg)

## Section 3.2: Static properties and variables

Static class properties that are defined with the public visibility are functionally the same as global variables. They can be accessed from anywhere the class is defined.

![](Image00079.jpg)

Functions can also define static variables inside their own scope. These static variables persist through multiple function calls, unlike regular variables defined in a function scope. This can be a very easy and simple way to implement the Singleton design pattern:

class Singleton {     public static function getInstance () {

![](Image00080.jpg)         // Static variable $instance is not deleted when the function ends         static $instance ;

        // Second call to this function will not get into the if-statement,

        // Because an instance of Singleton is now stored in the $instance

        // variable and is persisted through multiple calls         if (! $instance ) {

            // First call to this function will reach this line,

            // because the $instance has only been declared, not initialized

            $instance \= new Singleton ();

        }

![](Image00081.jpg)

## Section 3.3: User-defined global variables

The scope outside of any function or class is the global scope. When a PHP script includes another (using include or require ) the scope remains the same. If a script is included outside of any function or class, it's global variables are included in the same global scope, but if a script is included from within a function, the variables in the included script are in the scope of the function.

Within the scope of a function or class method, the global keyword may be used to create an access user-defined global variables.

![](Image00082.jpg)

A second way to access variables from the global scope is to use the special PHP-defined $GLOBALS array.

The $GLOBALS array is an associative array with the name of the global variable being the key and the contents of that variable being the value of the array element. Notice how $GLOBALS exists in any scope, this is because $GLOBALS is a superglobal.

 
| log\_message |
| --- |

This means that the () function could be rewritten as:

function log\_message ( $message ) {

    // Access the global $amount\_of\_log\_calls variable via the

![](Image00083.jpg)     // $GLOBALS array. No need for 'global $GLOBALS;', since it

![](Image00084.jpg)

One might ask, why use the $GLOBALS array when the global keyword can also be used to get a global variable's value? The main reason is using the global keyword will bring the variable into scope. You then can't reuse the same variable name in the local scope.

  

# Chapter 4: Superglobal Variables PHP

Superglobals are built-in variables that are always available in all scopes.

 
| global $variable |
| --- |

Several predefined variables in PHP are "superglobals", which means they are available in all scopes throughout a script. There is no need to do ; to access them within functions or methods.

## Section 4.1: Suberglobals explained

Introduction

Put simply, these are variables that are available in all scope in your scripts.

This means that there is no need to pass them as parameters in your functions, or store them outside a block of code to have them available in different scopes.

What's a superglobal??

If you're thinking that these are like superheroes - they're not.

As of PHP version 7.1.3 there are 9 superglobal variables. They are as follows:

![](Image00085.jpg)$GLOBALS \- References all variables available in global scope

$\_SERVER \- Server and execution environment information

$\_GET \- HTTP GET variables

$\_POST \- HTTP POST variables

$\_FILES \- HTTP File Upload variables

$\_COOKIE \- HTTP Cookies

$\_SESSION \- Session variables

$\_REQUEST \- HTTP Request variables

$\_ENV \- Environment variables

See the [documentation](http://php.net/manual/en/language.variables.superglobals.php) .

Tell me more, tell me more

I'm sorry for the Grease reference! [Link](https://www.youtube.com/watch?v=ZW0DfsCzfq4)

Time for some explanation on these superheroesglobals.

$GLOBALS

![](Image00086.jpg)An associative array containing references to all variables which are currently defined in the global scope of the script. The variable names are the keys of the array.

Code

![](Image00087.jpg)

![](Image00088.jpg)

Output

![](Image00089.jpg)

 
| test |
| --- |

In the above example $myLocal is not displayed the second time because it is declared inside the () function and then destroyed after the function is closed.

Becoming global

To remedy this there are two options.

![](Image00090.jpg)

The global keyword is a prefix on a variable that forces it to be part of the global scope.

Note that you cannot assign a value to a variable in the same statement as the global keyword. Hence, why I had to assign a value underneath. (It is possible if you remove new lines and spaces but I don't think it is neat. global

 
| $myLocal || ; ||   $myLocal || \= ||   "local" |
| --- | --- | --- | --- | --- |

).

![](Image00091.jpg)

 
| $GLOBAL || \[ || "myLocal" |
| --- | --- | --- |

In this example I reassigned $myLocal the value of \] since I find it easier writing a variable name rather than the associative array.

$\_SERVER

![](Image00092.jpg)$\_SERVER is an array containing information such as headers, paths, and script locations. The entries in this array are created by the web server. There is no guarantee that every web server will provide any of these; servers may omit some, or provide others not listed here. That said, a large number of these ![](Image00093.jpg)              variables are accounted for in the [CGI/1.1 specification](http://www.faqs.org/rfcs/rfc3875) , so you should be able to expect those.

An example output of this might be as follows (run on my Windows PC using WAMP)

C : \\wamp64\\www\\test . php :2:

array ( size \=36)     'HTTP\_HOST' \=> string 'localhost' ( length \=9)

    'HTTP\_CONNECTION' \=> string 'keep-alive' ( length \=10)

    'HTTP\_CACHE\_CONTROL' \=> string 'max-age=0' ( length \=9)

![](Image00094.jpg)     'HTTP\_UPGRADE\_INSECURE\_REQUESTS' \=> string '1' ( length \=1)     'HTTP\_USER\_AGENT' \=> string 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Safari/537.36' ( length \=110)

    'HTTP\_ACCEPT' \=> string

'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,\*/\*;q=0.8' ( length \=74)

    'HTTP\_ACCEPT\_ENCODING' \=> string 'gzip, deflate, sdch, br' ( length \=23)

    'HTTP\_ACCEPT\_LANGUAGE' \=> string 'en-US,en;q=0.8,en-GB;q=0.6' ( length \=26)

    'HTTP\_COOKIE' \=> string 'PHPSESSID=0gslnvgsci371ete9hg7k9ivc6' ( length \=36)

    'PATH' \=> string 'C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;C:\\Program Files

(x86)\\Intel\\iCLS Client\\;C:\\Program Files\\Intel\\iCLS

Client\\;C:\\ProgramData\\Oracle\\Java\\javapath;C:\\WINDOWS\\system32;C:\\WINDOWS;C:\\WINDOWS\\System32\\Wbem

;C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\;E:\\Program Files\\ATI Technologies\\ATI.ACE\\Core-

Static;E:\\Program Files\\AMD\\ATI.ACE\\Core-Static;C:\\Program Files (x86)\\AMD\\ATI.ACE\\Core-

Static;C:\\Program Files (x86)\\ATI Technologies\\ATI.ACE\\Core-Static;C:\\Program Files\\Intel\\Intel(R) Managemen' ... ( length \=1169)

    'SystemRoot' \=> string 'C:\\WINDOWS' ( length \=10)

    'COMSPEC' \=> string 'C:\\WINDOWS\\system32\\cmd.exe' ( length \=27)

    'PATHEXT' \=> string '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.PY' ( length \=57)

    'WINDIR' \=> string 'C:\\WINDOWS' ( length \=10)

    'SERVER\_SIGNATURE' \=> string '<address>Apache/2.4.23 (Win64) PHP/7.0.10 Server at localhost

Port 80</address>' ( length \=80)

    'SERVER\_SOFTWARE' \=> string 'Apache/2.4.23 (Win64) PHP/7.0.10' ( length \=32)

    'SERVER\_NAME' \=> string 'localhost' ( length \=9)

    'SERVER\_ADDR' \=> string '::1' ( length \=3)

    'SERVER\_PORT' \=> string '80' ( length \=2)

    'REMOTE\_ADDR' \=> string '::1' ( length \=3)

    'DOCUMENT\_ROOT' \=> string 'C:/wamp64/www' ( length \=13)

    'REQUEST\_SCHEME' \=> string 'http' ( length \=4)

    'CONTEXT\_PREFIX' \=> string '' ( length \=0)

    'CONTEXT\_DOCUMENT\_ROOT' \=> string 'C:/wamp64/www' ( length \=13)

    'SERVER\_ADMIN' \=> string 'wampserver@wampserver.invalid' ( length \=29)

    'SCRIPT\_FILENAME' \=> string 'C:/wamp64/www/test.php' ( length \=26)

    'REMOTE\_PORT' \=> string '5359' ( length \=4)

    'GATEWAY\_INTERFACE' \=> string 'CGI/1.1' ( length \=7)

    'SERVER\_PROTOCOL' \=> string 'HTTP/1.1' ( length \=8)

    'REQUEST\_METHOD' \=> string 'GET' ( length \=3)

    'QUERY\_STRING' \=> string '' ( length \=0)

    'REQUEST\_URI' \=> string '/test.php' ( length \=13)

    'SCRIPT\_NAME' \=> string '/test.php' ( length \=13)

    'PHP\_SELF' \=> string '/test.php' ( length \=13)     'REQUEST\_TIME\_FLOAT' \=> float 1491068771.413

    'REQUEST\_TIME' \=> int 1491068771

There is a lot to take in there so I will pick out some important ones below. If you wish to read about them all then consult the [indices section](http://php.net/manual/en/reserved.variables.server.php#refsect1-reserved.variables.server-indices) of the documentation.

I might add them all below one day. Or someone can edit and add a good explanation of them below? Hint, hint ;) For all explanations below, assume the URL is [http://www.example.com/index.php](http://www.example.com/index.php)

![](Image00095.jpg)HTTP\_HOST \- The host address.

 
| www || . || example || . || com |
| --- | --- | --- | --- | --- |

This would return

 
| 93 || . || 184 || . || 216 || . || 34 |
| --- | --- | --- | --- | --- | --- | --- |

 
| index || . || php |
| --- | --- | --- |

![](Image00096.jpg)HTTP\_USER\_AGENT \- Contents of the user agent. This is a string which contains all the information about the client's browser, including operating system.

HTTP\_COOKIE \- All cookies in a concatenated string, with a semi-colon delimiter.

SERVER\_ADDR \- The IP address of the server, of which the current script is running.

This would return

PHP\_SELF \- The file name of the currently executed script, relative to document root.

This would return /

REQUEST\_TIME\_FLOAT \- The timestamp of the start of the request, with microsecond precision. Available since PHP 5.4.0.

REQUEST\_TIME \- The timestamp of the start of the request. Available since PHP 5.1.0.

$\_GET

![](Image00097.jpg)              An associative array of variables passed to the current script via the URL parameters.

$\_GET is an array that contains all the URL parameters; these are the whatever is after the ? in the URL.

 
| $\_GET || \[ || "myVar" |
| --- | --- | --- |

Using [http://www.example.com/index.php?myVar=myVal](http://www.example.com/index.php?myVar=myVal) as an example. This information from this URL can be obtained by accessing in this format \] and the result of this will be myVal .

Using some code for those that don't like reading.

// URL = http://www.example.com/index.php?myVar=myVal

![](Image00098.jpg) echo $\_GET \[ "myVar" \] \== "myVal" ? "true" : "false" ; // returns "true"

The above example makes use of the ternary operator.

This shows how you can access the value from the URL using the $\_GET superglobal.

Now another example! gasp

![](Image00099.jpg)

It is possible to send multiple variables through the URL by separating them with an ampersand ( & ) character.

Security risk

It is very important not to send any sensitive information via the URL as it will stay in history of the computer and will be visible to anyone that can access that browser.

$\_POST

![](Image00100.jpg)An associative array of variables passed to the current script via the HTTP POST method when using application/x-www-form-urlencoded or multipart/form-data as the HTTP Content-Type in the request.

Very similar to $\_GET in that data is sent from one place to another.

I'll start by going straight into an example. (I have omitted the action attribute as this will send the information to the page that the form is in).

![](Image00101.jpg)

Above is a basic form for which data can be sent. In an real environment the value attribute would not be set meaning the form would be blank. This would then send whatever information is entered by the user.

![](Image00102.jpg)

Security risk

Sending data via POST is also not secure. Using HTTPS will ensure that data is kept more secure.

$\_FILES

![](Image00103.jpg)An associative array of items uploaded to the current script via the HTTP POST method. The structure of this array is outlined in the [POST method uploads](http://php.net/manual/en/features.file-upload.post-method.php) section.

Let's start with a basic form.

![](Image00104.jpg)

 
| enctype || \= || "multipart/form-data" |
| --- | --- | --- |

Note that I omitted the action attribute (again!). Also, I added , this is important to any form that will be dealing with file uploads.

![](Image00105.jpg)

This is used to upload one file. Sometimes you may wish to upload more than one file. An attribute exists for that, it's called multiple .

There's an attribute for just about anything . [I'm sorry](https://www.youtube.com/watch?v=szrsfeyLzyg) Below is an example of a form submitting multiple files.

![](Image00106.jpg)

Note the changes made here; there are only a few.

![](Image00107.jpg)The input name has square brackets. This is because it is now an array of files and so we are telling the form

 
| $\_FILES || \[ || "myVar" |
| --- | --- | --- |

to make an array of the files selected. Omitting the square brackets will result in the latter most file being set to \] .

![](Image00108.jpg)

This is a very simple example and doesn't handle problems such as file extensions that aren't allowed or files named with PHP code (like a PHP equivalent of an SQL injection). See the documentation.

The first process is checking if there are any files, and if so, set the total number of them to $total .

Using the for loop allows an iteration of the $\_FILES array and accessing each item one at a time. If that file doesn't encounter a problem then the if statement is true and the code from the single file upload is run.

If an problem is encountered the switch block is executed and an error is presented in accordance with the error for that particular upload.

$\_COOKIE

![](Image00109.jpg)              An associative array of variables passed to the current script via HTTP Cookies.

Cookies are variables that contain data and are stored on the client's computer.

Unlike the aforementioned superglobals, cookies must be created with a function (and not be assigning a value). The convention is below.

![](Image00110.jpg)

In this example a name is specified for the cookie (in this example it is "myVar"), a value is given (in this example it is "myVal", but a variable can be passed to assign its value to the cookie), and then an expiration time is given (in this example it is one hour since 3600 seconds is a minute).

Despite the convention for creating a cookie being different, it is accessed in the same way as the others.

![](Image00111.jpg)

To destroy a cookie, setcookie must be called again, but the expiration time is set to any time in the past. See below.

![](Image00112.jpg)

This will unset the cookies and remove it from the clients computer.

$\_SESSION

![](Image00113.jpg)An associative array containing session variables available to the current script. See the [Session functions](http://php.net/manual/en/ref.session.php) documentation for more information on how this is used.

Sessions are much like cookies except they are server side.

 
| session\_start |
| --- |

To use sessions you must include () at the top of your scripts to allow sessions to be utilised.

Setting a session variable is the same as setting any other variable. See example below.

![](Image00114.jpg)

 
| session\_id |
| --- |

When starting a session a random ID is set as a cookie and called "PHPSESSID" and will contain the session ID for that current session. This can be accessed by calling the () function.

 
| unset || ( || $\_SESSION || \[ || "myVar" |
| --- | --- | --- | --- | --- |

It is possible to destroy session variables using the unset function (such that \]) would destroy that variable).

 
| session\_destory |
| --- |

The alternative is to call () . This will destroy the entire session meaning that all session variables will no longer exist.

$\_REQUEST

![](Image00115.jpg)An associative array that by default contains the contents of [$\_GET](http://php.net/manual/en/reserved.variables.get.php) , [$\_POST](http://php.net/manual/en/reserved.variables.post.php) and [$\_COOKIE](http://php.net/manual/en/reserved.variables.cookies.php) .

As the PHP documentation states, this is just a collation of $\_GET , $\_POST , and $\_COOKIE all in one variable.

 
| php || . || ini |
| --- | --- | --- |

Since it is possible for all three of those arrays to have an index with the same name, there is a setting in the  file called request\_order which can specify which of the three has precedence.

For instance, if it was set to "GPC" , then the value of $\_COOKIE will be used, as it is read from left to right meaning the $\_REQUEST will set its value to $\_GET , then $\_POST , and then $\_COOKIE and since $\_COOKIE is last that is the value that is in $\_REQUEST . See [this question](http://stackoverflow.com/questions/43157933/what-is-the-request-precedence) . $\_ENV

![](Image00116.jpg)An associative array of variables passed to the current script via the environment method.

These variables are imported into PHP's global namespace from the environment under which the PHP parser is running. Many are provided by the shell under which PHP is running and different systems are likely running different kinds of shells, a definitive list is impossible. Please see your shell's documentation for a list of defined environment variables.

Other environment variables include the CGI variables, placed there regardless of whether PHP is running as a server module or CGI processor.

Anything stored within $\_ENV is from the environment from which PHP is running in.

 
| php || . || ini |
| --- | --- | --- |

$\_ENV is only populated if  allows it.

See [this answer](http://stackoverflow.com/questions/3780866/why-is-my-env-empty/27077452#27077452) for more information on why $\_ENV is not populated.

## Section 4.2: PHP5 SuperGlobals

Below are the PHP5 SuperGlobals

![](Image00117.jpg)$GLOBALS

$\_REQUEST

$\_GET

$\_POST

$\_FILES

$\_SERVER

$\_ENV

$\_COOKIE

$\_SESSION

$GLOBALS : This SuperGlobal Variable is used for accessing globals variables.

![](Image00118.jpg)

![](Image00119.jpg)

$\_REQUEST : This SuperGlobal Variable is used to collect data submitted by a HTML Form.

![](Image00120.jpg)

$\_GET : This SuperGlobal Variable is used to collect data submitted by HTML Form with get method.

![](Image00121.jpg)

$\_POST : This SuperGlobal Variable is used to collect data submitted by HTML Form with post method.

![](Image00122.jpg)

$\_FILES : This SuperGlobal Variable holds the information of uploaded files via HTTP Post method.

![](Image00123.jpg)

![](Image00124.jpg)

$\_SERVER : This SuperGlobal Variable holds information about Scripts, HTTP Headers and Server Paths.

![](Image00125.jpg)

$\_ENV : This SuperGlobal Variable Shell Environment Variable details under which the PHP is running. $\_COOKIE : This SuperGlobal Variable is used to retrieve Cookie value with given Key.

![](Image00126.jpg)

$\_SESSION : This SuperGlobal Variable is used to Set and Retrieve Session Value which is stored on Server.

![](Image00127.jpg)

# Chapter 5: Outputting the Value of a Variable

To build a dynamic and interactive PHP program, it is useful to output variables and their values. The PHP language allows for multiple methods of value output. This topic covers the standard methods of printing a value in PHP and where these methods can be used.

## Section 5.1: echo and print

 
| echo || ( || "test" |
| --- | --- | --- |

[echo](http://php.net/manual/en/function.echo.php) and [print](http://php.net/manual/en/function.print.php) are language constructs, not functions. This means that they don't require parentheses around the argument like a function does (although one can always add parentheses around almost any PHP expression and thus ) won't do any harm either). They output the string representation of a variable, constant, or expression. They can't be used to print arrays or objects.

![](Image00128.jpg)

Shorthand notation for echo

When [outside of PHP tags](http://php.net/manual/en/language.basic-syntax.phpmode.php) , a shorthand notation for echo is available by default, using <?= to begin output and ?> to end it. For example:

![](Image00129.jpg)

Note that there is no terminating ; . This works because the closing PHP tag acts as the terminator for the single statement. So, it is conventional to omit the semicolon in this shorthand notation.

Priority of print

Although the print is language construction it has priority like operator. It places between \= += \-= \*= \*\*= /= .= %= &= and and operators and has left association. Example:

![](Image00130.jpg)

Same example with brackets: ![](Image00131.jpg)echo '1' . print ( '2' + 3); //output 511 Differences between echo and print

In short, there are two main differences:

![](Image00132.jpg)print only takes one parameter, while echo can have multiple parameters. print returns a value, so can be used as an expression.

## Section 5.2: Outputting a structured view of arrays and objects

 
| [print\_r](http://php.net/manual/en/function.print-r.php) |
| --- |

[()](http://php.net/manual/en/function.print-r.php) \- Outputting Arrays and Objects for debugging

[print\_r](http://php.net/manual/en/function.print-r.php) will output a human readable format of an array or object.

You may have a variable that is an array or object. Trying to output it with an echo will throw the error:

 
| Notice || : ||   Array to string conversion |
| --- | --- | --- |

. You can instead use the print\_r function to dump a human readable

format of this variable.

![](Image00133.jpg)

![](Image00134.jpg)

![](Image00135.jpg)

Further, the output from print\_r can be captured as a string, rather than simply echoed. For instance, the following code will dump the formatted version of $myarray into a new variable:

![](Image00136.jpg)

Note that if you are viewing the output of PHP in a browser, and it is interpreted as HTML, then the line breaks will not be shown and the output will be much less legible unless you do something like

![](Image00137.jpg)

Alternatively you can tell the browser that what you're outputting is plain text, and not HTML:

![](Image00138.jpg)

 
| [var\_dum](http://php.net/manual/en/function.var-dump.php) [p](http://php.net/manual/en/function.var-dump.php) |
| --- |

[(](http://php.net/manual/en/function.var-dump.php) [)](http://php.net/manual/en/function.var-dump.php) \- Output human-readable debugging information about content of the argument(s) including its type and value

The output is more detailed as [compared](http://stackoverflow.com/questions/3406171/php-var-dump-vs-print-r/3406224#3406224) to print\_r because it also outputs the type of the variable along with its value and other information like object IDs, array sizes, string lengths, reference markers, etc.

You can use [var\_dump](http://php.net/manual/en/function.var-dump.php) to output a more detailed version for debugging.

![](Image00139.jpg)

Output is more detailed:

![](Image00140.jpg)

Note : If you are using xDebug in your development environment, the output of var\_dump is limited / truncated by default. See the [official documentation](https://xdebug.org/docs/display) for more info about the options to change this.

 
| [var\_export](http://php.net/manual/en/function.var-export.php) |
| --- |

[(](http://php.net/manual/en/function.var-export.php) [)](http://php.net/manual/en/function.var-export.php) \- Output valid PHP Code

 
| [var\_export](http://php.net/manual/en/function.var-export.php) |
| --- |

[(](http://php.net/manual/en/function.var-export.php) [)](http://php.net/manual/en/function.var-export.php) dumps a PHP parseable representation of the item.

![](Image00141.jpg)

![](Image00142.jpg)

To put the content into a variable, you can do this:

![](Image00143.jpg)

After that, you can output it like this:

![](Image00144.jpg) printf ( '$myarray = %s; %s' , $array\_export , PHP\_EOL ); printf ( '$mystring = %s; %s' , $string\_export , PHP\_EOL ); printf ( '$myint = %s; %s' , $int\_export , PHP\_EOL ); This will produce the following output:

![](Image00145.jpg)

## Section 5.3: String concatenation with echo

You can use [concatenation to join strings](https://secure.php.net/manual/en/language.operators.string.php) "end to end" while outputting them (with echo or print for example).

You can concatenate variables using a . (period/dot).

![](Image00146.jpg)

Similar to concatenation, echo (when used without parentheses) can be used to combine strings and variables together (along with other arbitrary expressions) using a comma (,).

![](Image00147.jpg)

![](Image00148.jpg)

String concatenation vs passing multiple arguments to echo

Passing multiple arguments to the echo command is more advantageous than string concatenation in some circumstances. The arguments are written to the output in the same order as they are passed in.

![](Image00149.jpg)

The problem with the concatenation is that the period . takes precedence in the expression. If concatenated, the above expression needs extra parentheses for the correct behavior. The precedence of the period affects ternary operators too.

![](Image00150.jpg)

## Section 5.4: printf vs sprintf

[printf](http://php.net/manual/en/function.printf.php) will output a formatted string using placeholders

![](Image00151.jpg)

It is also possible to format a number with these 2 functions. This can be used to format a decimal value used to represent money so that it always has 2 decimal digits.

![](Image00152.jpg)

The two functions [vprintf](http://php.net/manual/en/function.vprintf.php) and [vsprintf](http://php.net/manual/en/function.vsprintf.php) operate as [printf](http://php.net/manual/en/function.printf.php) and [sprintf](http://php.net/manual/en/function.sprintf.php) , but accept a format string and an array of values, instead of individual variables.

## Section 5.5: Outputting large integers

On 32-bits systems, integers larger than PHP\_INT\_MAX are automatically converted to float. Outputting these as integer values (i.e. non-scientific notation) can be done with printf , using the float representation, as illustrated below:

![](Image00153.jpg)

    echo "  " , $i , " \\n " ; }

// outputs:

![](Image00154.jpg) pow (1024,   1)   integer                 1024                                    1024   1024 pow (1024,   2)   integer              1048576                                 1048576   1048576 pow (1024,   3)   integer           1073741824                              1073741824   1073741824 pow (1024,   4)    double        1099511627776                           1099511627776   1099511627776 pow (1024,   5)    double  1.1258999068426E+15                        1125899906842624 1.1258999068426E+15 pow (1024,   6)    double  1.1529215046068E+18                     1152921504606846976 1.1529215046068E+18 pow (1024,   9)    double  1.2379400392854E+27            1237940039285380274899124224 1.2379400392854E+27 pow (1024, 12)    double  1.3292279957849E+36   1329227995784915872903807060280344576 1.3292279957849E+36

Note: watch out for float precision, which is not infinite!

While this looks nice, in this contrived example the numbers can all be represented as a binary number since they are all powers of 1024 (and thus 2). See for example:

![](Image00155.jpg)

## Section 5.6: Output a Multidimensional Array with index and value and print into the table

![](Image00156.jpg)

![](Image00157.jpg)

Output Multidimensional Array with index and value in table

![](Image00158.jpg)

  

# Chapter 6: Constants

## Section 6.1: Defining constants

Constants are created using the const statement or the define function. The convention is to use UPPERCASE letters for constant names. ![](Image00159.jpg)define ( "BETTER\_APP\_LANGUAGES" , \[ "lu" , "de" \]); // arrays Define constant using another constant if you have one constant you can define another one based on it:

![](Image00160.jpg) const TAU \= PI \* 2; define ( "EARTH\_IS\_ROUND" , ! EARTH\_IS\_FLAT ); define ( "MORE\_UNKNOWN" , UNKNOWN ); define ( "APP\_ENV\_UPPERCASE" , strtoupper ( APP\_ENV )); // string manipulation is ok too // the above example (a function call) does not work with const: // const TIME = time(); # fails with a fatal error! Not a constant scalar expression define ( "MAX\_SESSION\_TIME\_IN\_MINUTES" , MAX\_SESSION\_TIME / 60); const APP\_FUTURE\_LANGUAGES \= \[-1 \=> "es" \] + APP\_LANGUAGES ; // array manipulations define ( "APP\_BETTER\_FUTURE\_LANGUAGES" , array\_merge (\[ "fr" \], APP\_BETTER\_LANGUAGES ));

Reserved constants

Some constant names are reserved by PHP and cannot be redefined. All these examples will fail:

define ( "true" , false ); // internal constant define ( "false" , true ); // internal constant

![](Image00161.jpg) define ( "CURLOPT\_AUTOREFERER" , "something" ); // will fail if curl extension is loaded And a Notice will be issued:

![](Image00162.jpg)

Conditional defines

If you have several files where you may define the same variable (for example, your main config then your local config) then following syntax may help avoiding conflicts:

![](Image00163.jpg) defined ( "PI" ) || define ( "PI" , 3.1415 ); // "define PI if it's not yet defined" const vs define define is a runtime expression while const a compile time one.

Thus define allows for dynamic values (i.e. function calls, variables etc.) and even dynamic names and conditional definition. It however is always defining relative to the root namespace.

const is static (as in allows only operations with other constants, scalars or arrays, and only a restricted set of them, the so called constant scalar expressions , i.e. arithmetic, logical and comparison operators as well as array dereferencing), but are automatically namespace prefixed with the currently active namespace.

const only supports other constants and scalars as values, and no operations.

## Section 6.2: Class Constants

Constants can be defined inside classes using a const keyword.

![](Image00164.jpg)

This is useful to store types of items.

![](Image00165.jpg)

## Section 6.3: Checking if constant is defined

Simple check

To check if constant is defined use the defined function. Note that this function doesn't care about constant's value, it only cares if the constant exists or not. Even if the value of the constant is null or false the function will still return true .

![](Image00166.jpg)

![](Image00167.jpg)

Note that constant becomes "visible" in your code only after the line where you have defined it:

![](Image00168.jpg)

Getting all defined constants

To get all defined constants including those created by PHP use the get\_defined\_constants function:

![](Image00169.jpg)

To get only those constants that were defined by your app call the function at the beginning and at the end of your script (normally after the bootstrap process):

![](Image00170.jpg)

It's sometimes useful for debugging

## Section 6.4: Using constants

To use the constant simply use its name:

![](Image00171.jpg)

or if you don't know the name of the constant in advance, use the constant function:

![](Image00172.jpg)

## Section 6.5: Constant arrays

Arrays can be used as plain constants and class constants from version PHP 5.6 onwards:

![](Image00173.jpg)

![](Image00174.jpg)const ANSWER \= \[2,4\];

Also from version PHP 7.0 this functionality was ported to the [define](http://php.net/manual/en/function.define.php) function for plain constants.

![](Image00175.jpg)

# Chapter 7: Magic Constants

## Section 7.1: Dierence between \_\_FUNCTION\_\_ and \_\_METHOD\_\_

\_\_FUNCTION\_\_ returns only the name of the function whereas \_\_METHOD\_\_ returns the name of the class along with the name of the function:

![](Image00176.jpg)

## Section 7.2: Dierence between \_\_CLASS\_\_, get\_class() and get\_called\_class()

 
| get\_class () |
| --- |

\_\_CLASS\_\_ magic constant returns the same result as  function called without parameters and they both return the name of the class where it was defined (i.e. where you wrote the function call/constant name ).

 
| get\_class ( $this ) || and || get\_called\_class () |
| --- | --- | --- |

In contrast,  functions call, will both return the name of the actual class which was instantiated:

![](Image00177.jpg)

![](Image00178.jpg)

## Section 7.3: File & Directory Constants

Current file

You can get the name of the current PHP file (with the absolute path) using the \_\_FILE\_\_ magic constant. This is most often used as a logging/debugging technique.

![](Image00179.jpg)

Current directory

To get the absolute path to the directory where the current file is located use the \_\_DIR\_\_ magic constant.

![](Image00180.jpg)

 
| dirname || ( || \_\_FILE\_\_ |
| --- | --- | --- |

To get the absolute path to the directory where the current file is located, use ) .

![](Image00181.jpg)

Getting current directory is often used by PHP frameworks to set a base directory:

![](Image00182.jpg)

![](Image00183.jpg)

Besides magic constants PHP also adds some fixed constants for working with paths:

![](Image00184.jpg) DIRECTORY\_SEPARATOR constant for separating directories in a path. Takes value / on \*nix, and \\ on Windows. The example with views can be rewritten with:

$view \= 'page' ;

$viewFile \= BASEDIR . DIRECTORY\_SEPARATOR . 'views' . DIRECTORY\_SEPARATOR . $view ;

Rarely used PATH\_SEPARATOR constant for separating paths in the $PATH environment variable. It is ; on

Windows, : otherwise

# Chapter 8: Comments

## Section 8.1: Single Line Comments

The single line comment begins with "//" or "#". When encountered, all text to the right will be ignored by the PHP interpreter.

![](Image00185.jpg)

## Section 8.2: Multi Line Comments

The multi-line comment can be used to comment out large blocks of code. It begins with /\* and ends with \*/ .

![](Image00186.jpg)

  

# Chapter 9: Types

## Section 9.1: Type Comparison

There are two types of [comparison](http://php.net/manual/en/types.comparisons.php) : loose comparison with \== and strict comparison with \=== . Strict comparison ensures both the type and value of both sides of the operator are the same.

![](Image00187.jpg)

You can also use strong comparison to check if type and value don't match using !== .

A typical example where the \== operator is not enough, are functions that can return different types, like [strpos](http://php.net/manual/en/function.strpos.php) , which returns false if the searchword is not found, and the match position ( int ) otherwise:

if ( strpos ( 'text' , 'searchword' ) \== false )

  // strpos returns false, so == comparison works as expected here, BUT:

if ( strpos ( 'text bla' , 'text' ) \== false )

  // strpos returns 0 (found match at position 0) and 0==false is true.

  // This is probably not what you expect!

if ( strpos ( 'text' , 'text' ) \=== false )

![](Image00188.jpg)   // strpos returns 0, and 0===false is false, so this works as expected.

## Section 9.2: Boolean

[Boolean](http://php.net/manual/en/language.types.boolean.php) is a type, having two values, denoted as true or false .

This code sets the value of $foo as true and $bar as false :

![](Image00189.jpg)

true and false are not case sensitive, so TRUE and FALSE can be used as well, even FaLsE is possible. Using lower case is most common and recommended in most code style guides, e.g. [PSR-2](http://www.php-fig.org/psr/psr-2/) .

Booleans can be used in if statements like this:

![](Image00190.jpg)

Due to the fact that PHP is weakly typed, if $foo above is other than true or false , it's automatically coerced to a boolean value.

The following values result in false :

![](Image00191.jpg)a zero value: 0 (integer), 0.0 (float), or '0' (string) an empty string '' or array \[\]

null (the content of an unset variable, or assigned to a variable)

Any other value results in true .

To avoid this loose comparison, you can enforce strong comparison using \=== , which compares value and type . See Type Comparison for details.

 
| bool || ) or ( || boolean |
| --- | --- | --- |

To convert a type into boolean, you can use the () cast before the type.

![](Image00192.jpg)

or call the [boolval](http://php.net/manual/en/function.boolval.php) function:

![](Image00193.jpg)

Boolean conversion to a string (note that false yields an empty string):

![](Image00194.jpg)

Boolean conversion to an integer:

![](Image00195.jpg)

Note that the opposite is also possible:

![](Image00196.jpg)

Also all non-zero will return true:

![](Image00197.jpg)

## Section 9.3: Float

![](Image00198.jpg)

Floats are floating point numbers, which allow more output precision than plain integers.

Floats and integers can be used together due to PHP's loose casting of variable types:

![](Image00199.jpg)

php does not show float as float number like other languages, for example:

![](Image00200.jpg)

Warning

Floating point precision

(From the [PHP manual page](http://php.net/manual/en/language.types.float.php) )

![](Image00201.jpg)Floating point numbers have limited precision. Although it depends on the system, PHP typically give a maximum relative error due to rounding in the order of 1.11e-16. Non elementary arithmetic operations may give larger errors, and error propagation must be considered when several operations are compounded.

Additionally, rational numbers that are exactly representable as floating point numbers in base 10, like 0.1 or 0.7, do not have an exact representation as floating point numbers in base 2 (binary), which is used internally, no matter the size of the mantissa. Hence, they cannot be converted into their internal binary counterparts without a small loss of precision. This can lead to confusing results: for example, floor((0.1+0.7)\*10) will usually return 7 instead of the expected 8, since the internal representation will be something like 7.9999999999999991118....

So never trust floating number results to the last digit, and do not compare floating point numbers directly for equality. If higher precision is necessary, the arbitrary precision math functions and gmp functions are available.

## Section 9.4: Strings

A string in PHP is a series of single-byte characters (i.e. there is no native Unicode support) that can be specified in four ways:

Single Quoted

Displays things almost completely "as is". Variables and most escape sequences will not be interpreted. The exception is that to display a literal single quote, one can escape it with a back slash ', and to display a back slash, one can escape it with another backslash \\

![](Image00202.jpg)

Double Quoted

Unlike a single-quoted string, simple variable names and [escape sequences](http://php.net/manual/en/language.types.string.php#language.types.string.syntax.double) in the strings will be evaluated. Curly braces (as in the last example) can be used to isolate complex variable names.

![](Image00203.jpg)

Heredoc

 
| <<< identifier |
| --- |

In a heredoc string, variable names and escape sequences are parsed in a similar manner to double-quoted strings, though braces are not available for complex variable names. The start of the string is delimited by , and the end by identifier , where identifier is any valid PHP name. The ending identifier must appear on a line by itself. No whitespace is allowed before or after the identifier, although like any line in PHP, it must also be terminated by a semicolon.

![](Image00204.jpg)

Nowdoc

A nowdoc string is like the single-quoted version of heredoc, although not even the most basic escape sequences are evaluated. The identifier at the beginning of the string is wrapped in single quotes.

PHP 5.x Version ≥ 5.3

$my\_string \= <<< 'EOF'

![](Image00205.jpg) A similar syntax to heredoc but, similar to single quoted strings, nothing is parsed (not even escaped apostrophes \\' and backslashes \\\\.)

![](Image00206.jpg)

## Section 9.5: Callable

Callables are anything which can be called as a callback. Things that can be termed a "callback" are as follows:

![](Image00207.jpg)Anonymous functions

Standard PHP functions (note: not language constructs ) Static Classes non-static Classes ( using an alternate syntax )

Specific Object/Class Methods

Objects themselves, as long as the object is found in key 0 of an array Example Of referencing an object as an array element:

![](Image00208.jpg)

Callbacks can be denoted by callable type hint as of PHP 5.4.

![](Image00209.jpg)

## Section 9.6: Resources

A [resource](https://secure.php.net/manual/en/language.types.resource.php) is a special type of variable that references an external resource, such as a file, socket, stream, document, or connection.

![](Image00210.jpg)

 
| [get\_resource\_type](https://secure.php.net/manual/en/function.get-resource-type.php) |
| --- |

There are different (sub-)types of resource. You can check the resource type using [(](https://secure.php.net/manual/en/function.get-resource-type.php) [)](https://secure.php.net/manual/en/function.get-resource-type.php) :

![](Image00211.jpg)

![](Image00212.jpg)

You can find a complete list of built-in resource types [here](https://secure.php.net/manual/en/resource.php) .

## Section 9.7: Type Casting

PHP will generally correctly guess the data type you intend to use from the context it's used in, however sometimes it is useful to manually force a type. This can be accomplished by prefixing the declaration with the name of the required type in parenthesis:

![](Image00213.jpg)

But be careful: not all type casts work as one might expect:

![](Image00214.jpg) // below 3 statements hold for 32-bits systems (PHP\_INT\_MAX=2147483647) // an integer value bigger than PHP\_INT\_MAX is automatically converted to float: var\_dump (        999888777666 ); // float(999888777666) // forcing to (int) gives overflow: var\_dump (( int )   999888777666 ); // int(-838602302) // but in a string it just returns PHP\_INT\_MAX var\_dump (( int ) "999888777666" ); // int(2147483647)

var\_dump (( bool ) \[\]);       // bool(false) (empty array) var\_dump (( bool ) \[ false \]); // bool(true)  (non-empty array)

## Section 9.8: Type Juggling

PHP is a weakly-typed language. It does not require explicit declaration of data types. The context in which the variable is used determines its data type; conversion is done automatically:

![](Image00215.jpg)

![](Image00216.jpg)

## Section 9.9: Null

PHP represents "no value" with the [null](http://php.net/manual/en/language.types.null.php) keyword. It's somewhat similar to the null pointer in C-language and to the NULL value in SQL.

Setting the variable to null:

![](Image00217.jpg)

Checking if the variable was set to null:

![](Image00218.jpg)

Null vs undefined variable

 
| Notice || : || Undefined variable || : || nullvar |
| --- | --- | --- | --- | --- |

If the variable was not defined or was unset then any tests against the null will be successful but they will also generate a :

![](Image00219.jpg)

![](Image00220.jpg) Therefore undefined values must be checked with [isset](http://php.net/manual/en/function.isset.php) : if (! isset ( $nullvar )) {   /\* variable is null or is not even defined \*/   }

## Section 9.10: Integers

Integers in PHP can be natively specified in base 2 (binary), base 8 (octal), base 10 (decimal), or base 16 (hexadecimal.)

![](Image00221.jpg)

Integers are 32 or 64 bits long, depending on the platform. The constant PHP\_INT\_SIZE holds integer size in bytes.

PHP\_INT\_MAX and (since PHP 7.0) PHP\_INT\_MIN are also available.

![](Image00222.jpg) printf ( "Integers are %d bits long" . PHP\_EOL , PHP\_INT\_SIZE \* 8); printf ( "They go up to %d " . PHP\_EOL , PHP\_INT\_MAX );

Integer values are automatically created as needed from floats, booleans, and strings. If an explicit typecast is

![](Image00223.jpg)

Integer overflow will be handled by conversion to a float:

![](Image00224.jpg)

There is no integer division operator in PHP, but it can be simulated using an implicit cast, which always 'rounds' by just discarding the float-part. As of PHP version 7, an integer division function was added.

![](Image00225.jpg)

  

# Chapter 10: Operators

An operator is something that takes one or more values (or expressions, in programming jargon) and yields another value (so that the construction itself becomes an expression).

Operators can be grouped according to the number of values they take.

## Section 10.1: Null Coalescing Operator (??)

Null coalescing is a new operator introduced in PHP 7. This operator returns its first operand if it is set and not NULL . Otherwise it will return its second operand.

The following example:

![](Image00226.jpg)

is equivalent to both:

![](Image00227.jpg)

and:

![](Image00228.jpg)

This operator can also be chained (with right-associative semantics):

![](Image00229.jpg)

which is an equivalent to:

![](Image00230.jpg)

Note:

When using coalescing operator on string concatenation don't forget to use parentheses ()

![](Image00231.jpg)

This will output John only, and if its $firstName is null and $lastName is Doe it will output Unknown Doe . In order to output John Doe , we must use parentheses like this.

![](Image00232.jpg)

![](Image00233.jpg) echo ( $firstName ?? "Unknown" ) . " " . ( $lastName ?? "" );

This will output John Doe instead of John only.

## Section 10.2: Spaceship Operator (<=>)

PHP 7 introduces a new kind of operator, which can be used to compare expressions. This operator will return -1, 0 or 1 if the first expression is less than, equal to, or greater than the second expression.

![](Image00234.jpg)

Objects are not comparable, and so doing so will result in undefined behaviour.

 
| <= |
| --- |

![](Image00235.jpg) This operator is particularly useful when writing a user-defined comparison function using usort , uasort , or uksort . Given an array of objects to be sorted by their weight property, for example, an anonymous function can use \> to return the value expected by the sorting functions. usort ( $list , function ( $a , $b ) { return $a \-> weight <=> $b \-> weight ; }); In PHP 5 this would have required a rather more elaborate expression.

![](Image00236.jpg)

## Section 10.3: Execution Operator (\`\`)

The PHP execution operator consists of backticks (\`\`) and is used to run shell commands. The output of the command will be returned, and may, therefore, be stored in a variable.

![](Image00237.jpg)

 
| [shell\_exec](http://php.net/manual/en/function.shell-exec.php) |
| --- |

Note that the execute operator and [(](http://php.net/manual/en/function.shell-exec.php) [)](http://php.net/manual/en/function.shell-exec.php) will give the same result.

## Section 10.4: Incrementing (++) and Decrementing Operators (--)

Variables can be incremented or decremented by 1 with ++ or \-- , respectively. They can either precede or succeed variables and slightly vary semantically, as shown below.

![](Image00238.jpg)

More information about incrementing and decrementing operators can be found in the [official documentation](http://php.net/manual/en/language.operators.increment.php) .

## Section 10.5: Ternary Operator (?:)

The ternary operator can be thought of as an inline if statement. It consists of three parts. The operator , and two outcomes. The syntax is as follows:

![](Image00239.jpg)

 
| <true value |
| --- |

 
| <false value |
| --- |

If the operator is evaluated as true , the value in the first block will be returned ( \> ), else the value in the second block will be returned ( \> ). Since we are setting $value to the result of our ternary operator it will store the returned value.

Example:

![](Image00240.jpg)

 
| empty || ( || $\_POST || \[ || 'action' |
| --- | --- | --- | --- | --- |

 
| $\_POST || \[ || 'action' |
| --- | --- | --- |

$action would contain the string 'default' if \]) evaluates to true. Otherwise it would contain the value of \] .

 
| expr3 |
| --- |

 
| expr1 || ) || ? || ( || expr2 |
| --- | --- | --- | --- | --- |

![](Image00241.jpg) The expression () : () evaluates to expr2 if expr1 evaluates to true , and expr3 if expr1 evaluates to false .

 
| expr1 ? || : || expr3 |
| --- | --- | --- |

It is possible to leave out the middle part of the ternary operator. Expression  returns expr1 if expr1 evaluates to TRUE, and expr3 otherwise. ?: is often referred to as Elvis operator.

This behaves like the Null Coalescing operator ?? , except that ?? requires the left operand to be exactly null while ?: tries to resolve the left operand into a boolean and check if it resolves to boolean false .

Example:

![](Image00242.jpg)

In this example, setWidth accepts a width parameter, or default 0, to change the width session value. If $width is 0

 
| getDefaultWidth |
| --- |

 
| getDefaultWidth |
| --- |

(if $width is not provided), which will resolve to boolean false, the value of () is used instead. The () function will not be called if $width did not resolve to boolean false.

Refer to Types for more information about conversion of variables to boolean.

## Section 10.6: Logical Operators (&&/AND and ||/OR)

In PHP, there are two versions of logical AND and OR operators.

Operator True if

 
| $a and $b |
| --- |

Both $a and $b are true

 
| $a && $b |
| --- |

Both $a and $b are true

 
| $a or $b |
| --- |

Either $a or $b is true

 
| $a || $b |
| --- |

Either $a or $b is true

Note that the && and || opererators have higher [precedence](http://php.net/manual/en/language.operators.precedence.php) than and and or . See table below:

Evaluation Result of $e Evaluated as

 
| $e \= ( false || true ) |
| --- |

 
| $e \= false || true |
| --- |

True

 
| ( $e \= false ) or true |
| --- |

 
| $e \= false or true |
| --- |

False

Because of this it's safer to use && and || instead of and and or .

## Section 10.7: String Operators (. and .=)

![](Image00243.jpg)

## Section 10.8: Object and Class Operators

Members of objects or classes can be accessed using the object operator ( \-> ) and the class operator ( :: ).

![](Image00244.jpg)

![](Image00245.jpg)

 
| $object \-> || a instead of || $object \-> $a |
| --- | --- | --- |

Note that after the object operator, the $ should not be written (). For the class operator, this is not the case and the $ is necessary. For a constant defined in the class, the $ is never used.

 
| var\_dump || ( || MyClass :: |
| --- | --- | --- |

Also note that d ()); is only allowed if the function d () does not reference the object:

![](Image00246.jpg)

This causes a 'PHP Fatal error: Uncaught Error: Using $this when not in object context' These operators have left associativity, which can be used for 'chaining':

![](Image00247.jpg)

These operators have the highest precedence (they are not even mentioned in the manual), even higher that clone . Thus:

![](Image00248.jpg)

The value of $o1 is added to before the object is cloned!

Note that using parentheses to influence precedence did not work in PHP version 5 and older (it does in PHP 7):

![](Image00249.jpg)

## Section 10.9: Combined Assignment (+= etc)

The combined assignment operators are a shortcut for an operation on some variable and subsequently assigning this new value to that variable.

Arithmetic:

![](Image00250.jpg)

Processing Multiple Arrays Together

![](Image00251.jpg)

Combined concatenation and assignment of a string:

![](Image00252.jpg)

Combined binary bitwise assignment operators:

$a \= 0b00101010 ;   // $a now is 42

![](Image00253.jpg) $a &= 0b00001111 ; // $a now is (00101010 & 00001111) => 00001010 (bitwise and) $a |= 0b00100010 ; // $a now is (00001010 | 00100010) => 00101010 (bitwise or)

$a ^ \= 0b10000010 ; // $a now is (00101010 ^ 10000010) => 10101000 (bitwise xor)

$a \>>= 3;          // $a now is (10101000 >> 3) => 00010101 (shift right by 3)

$a <<= 1;          // $a now is (00010101 << 1) => 00101010 (shift left by 1)

## Section 10.10: Altering operator precedence (with parentheses)

The order in which operators are evaluated is determined by the operator precedence (see also the Remarks section).

![](Image00254.jpg)

The precedence can be altered using parentheses: in

![](Image00255.jpg)

## Section 10.11: Basic Assignment (=)

![](Image00256.jpg)

results in $a having the value some string .

The result of an assignment expression is the value being assigned. Note that a single equal sign \= is NOT for comparison!

![](Image00257.jpg)

does the following:

1.    Line 1 assigns 3 to $a .

2.    Line 2 assigns 5 to $a . This expression yields value 5 as well.

3.    Line 2 then assigns the result of the expression in parentheses ( 5 ) to $b .

Thus: both $a and $b now have value 5 .

## Section 10.12: Association

Left association

If the preceedence of two operators is equal, the associativity determines the grouping (see also the Remarks section):

![](Image00258.jpg)

\* and % have equal precedence and left associativity. Because the multiplication occurs first (left), it is grouped.

![](Image00259.jpg)

Now, the modulus operator occurs first (left) and is thus grouped.

Right association

![](Image00260.jpg)

 
| $b += |
| --- |

Both $a and $b now have value 2 because 1 is grouped and then the result ( $b is 2 ) is assigned to $a .

## Section 10.13: Comparison Operators

Equality

For basic equality testing, the equal operator \== is used. For more comprehensive checks, use the identical operator \=== .

The identical operator works the same as the equal operator, requiring its operands have the same value, but also requires them to have the same data type.

For example, the sample below will display 'a and b are equal', but not 'a and b are identical'.

![](Image00261.jpg)

When using the equal operator, numeric strings are cast to integers.

Comparison of objects

 
| new stdClass || () ||   \=== |
| --- | --- | --- |

\=== compares two objects by checking if they are exactly the same instance . This means that

 
| new stdClass |
| --- |

() resolves to false, even if they are created in the same way (and have the exactly same values).

 
| $a \== $b |
| --- |

\== compares two objects by recursively checking if they are equal ( deep equals ). That means, for , if $a and $b are:

1.                      of the same class

2.                      have the same properties set, including dynamic properties

 
| $a \-> property \== $b \-> property |
| --- |

3.                      for each property $property set,  is true (hence recursively checked). Other commonly used operators

They include:

1.    Greater Than ( \> )

2.    Lesser Than ( < )

3.    Greater Than Or Equal To ( \>= )

4.    Lesser Than Or Equal To ( <= )

5.    Not Equal To ( != )

6.    Not Identically Equal To ( !== )

 
| $a || \> ||   $b |
| --- | --- | --- |

1.    Greater Than : , returns true if $a 's value is greater than of $b , otherwise returns false.

Example :

![](Image00262.jpg)

 
| $a || < ||   $b |
| --- | --- | --- |

2.    Lesser Than : , returns true if $a 's value is smaller that of $b , otherwise returns false.

Example :

![](Image00263.jpg)

 
| $a \>= $b |
| --- |

3.    Greater Than Or Equal To : , returns true if $a 's value is either greater than of $b or equal to $b , otherwise returns false .

Example :

![](Image00264.jpg)

 
| $a <= $b |
| --- |

4.    Smaller Than Or Equal To : , returns true if $a 's value is either smaller than of $b or equal to $b , otherwise returns false .

Example :

![](Image00265.jpg)

5/6. Not Equal/Identical To: To rehash the earlier example on equality, the sample below will display 'a and b are not identical', but not 'a and b are not equal'.

![](Image00266.jpg)

## Section 10.14: Bitwise Operators

Prefix bitwise operators

Bitwise operators are like logical operators but executed per bit rather than per boolean value.

![](Image00267.jpg)

Bitmask-bitmask operators

Bitwise AND & : a bit is set only if it is set in both operands

![](Image00268.jpg)

Bitwise OR | : a bit is set if it is set in either or both operands

![](Image00269.jpg)

Bitwise XOR ^ : a bit is set if it is set in one operand and not set in another operand, i.e. only if that bit is in different state in the two operands

![](Image00270.jpg)

Example uses of bitmasks

These operators can be used to manipulate bitmasks. For example:

![](Image00271.jpg)

Here, the | operator is used to combine the two bitmasks. Although + has the same effect, | emphasizes that you are combining bitmasks, not adding two normal scalar integers.

![](Image00272.jpg)

This example (assuming $option always only contain one bit) uses:

the ^ operator to conveniently toggle bitmasks.

![](Image00273.jpg) the | operator to set a bit neglecting its original state or other bits the ~ operator to convert an integer with only one bit set into an integer with only one bit not set the & operator to unset a bit, using these properties of & :

 
|   \=== |
| --- |

 
|   \=== |
| --- |

![](Image00274.jpg) ![](Image00275.jpg) Since &= with a set bit will not do anything ( (1 & 1)1 , (0 & 1)0 ), doing &= with an integer with only one bit not set will only unset that bit, not affecting other bits.

 
|   \=== |
| --- |

 
|   \=== |
| --- |

&= with an unset bit will unset that bit ( (1 & 0)0 , (0 & 0)0 )

Using the & operator with another bitmask will filter away all other bits not set in that bitmask.

If the output has any bits set, it means that any one of the options are enabled.

If the output has all bits of the bitmask set, it means that all of the options in the bitmask are enabled.

 
| <= |
| --- |

Bear in mind that these comparison operators: ( < \> <= \>= \== \=== != !== < \> \> ) have higher precedence than these bitmask-bitmask operators: ( | ^ & ). As bitwise results are often compared using these comparison operators, this is a common pitfall to be aware of.

Bit-shifting operators

Bitwise left shift << : shift all bits to the left (more significant) by the given number of steps and discard the bits exceeding the int size

<< $x is equivalent to unsetting the highest $x bits and multiplying by the $x th power of 2

![](Image00276.jpg)

 
| \>> $x |
| --- |

Bitwise right shift \>> : discard the lowest shift and shift the remaining bits to the right (less significant)  is equivalent to dividing by the $x th power of 2 and discard the non-integer part

![](Image00277.jpg)

Example uses of bit shifting:

 
| /= 16 |
| --- |

Fast division by 16 (better performance than )

![](Image00278.jpg)

On 32-bit systems, this discards all bits in the integer, setting the value to 0. On 64-bit systems, this unsets the most significant 32 bits and keep the least

![](Image00279.jpg)

 
| $x || & ||   0xFFFFFFFF |
| --- | --- | --- |

significant 32 bits, equivalent to

 
| printf || ( " || %'06b |
| --- | --- | --- |

Note: In this example, " ) is used. It outputs the value in 6 binary digits.

## Section 10.15: instanceof (type operator)

For checking whether some object is of a certain class, the (binary) instanceof operator can be used since PHP version 5.

The first (left) parameter is the object to test. If this variable is not an object, instanceof always returns false . If a constant expression is used, an error is thrown.

The second (right) parameter is the class to compare with. The class can be provided as the class name itself, a string variable containing the class name (not a string constant!) or an object of that class.

![](Image00280.jpg)

instanceof can also be used to check whether an object is of some class which extends another class or implements some interface:

![](Image00281.jpg)

To check whether an object is not of some class, the not operator ( ! ) can be used:

![](Image00282.jpg)

 
| $o instanceof MyClass |
| --- |

Note that parentheses around  are not needed because instanceof has higher precedence than ! , although it may make the code better readable with parentheses.

Caveats

If a class does not exist, the registered autoload functions are called to try to define the class (this is a topic outside the scope of this part of the Documentation!). In PHP versions before 5.1.0, the instanceof operator would also trigger these calls, thus actually defining the class (and if the class could not be defined, a fatal error would occur). To avoid this, use a string:

![](Image00283.jpg)

As of PHP version 5.1.0, the registered autoloaders are not called anymore in these situations.

Older versions of PHP (before 5.0)

In older versions of PHP (before 5.0), the is\_a function can be used to determine wether an object is of some class. This function was deprecated in PHP version 5 and undeprecated in PHP version 5.3.0.

  

# Chapter 11: References

## Section 11.1: Assign by Reference

This is the first phase of referencing. Essentially when you [assign by reference](http://php.net/manual/en/language.references.whatdo.php#language.references.whatdo.assign) , you're allowing two variables to share the same value as such.

![](Image00284.jpg)

$foo and $bar are equal here. They do not point to one another. They point to the same place ( the "value" ).

 
| array |
| --- |

You can also assign by reference within the () language construct. While not strictly being an assignment by reference.

![](Image00285.jpg)

Assigning by reference is not only limited to variables and arrays, they are also present for functions and all "passby-reference" associations.

![](Image00286.jpg)

 
| bar |
| --- |

Assignment is key within the function definition as above. You can not pass an expression by reference, only a value/variable. Hence the instantiation of $a in () .

## Section 11.2: Return by Reference

Occasionally there comes time for you to implicitly return-by-reference.

![](Image00287.jpg)Returning by reference is useful when you want to use a function to find to which variable a reference should be bound. Do not use return-by-reference to increase performance. The engine will automatically optimize this on its own. Only return references when you have a valid technical reason to do so.

Taken from the [PHP Documentation for Returning By Reference](http://php.net/manual/en/language.references.return.php) .

There are many different forms return by reference can take, including the following example:

![](Image00288.jpg)

Return by reference is not only limited to function references. You also have the ability to implicitly call the function:

![](Image00289.jpg)

 
| echo || & || myFunction |
| --- | --- | --- |

You cannot directly reference a function call, it has to be assigned to a variable before harnessing it. To see how that works, simply try (); .

Notes

![](Image00290.jpg)You are required to specify a reference ( & ) in both places you intend on using it. That means, for your

 
| ... |
| --- |

 
| function || & || myFunction |
| --- | --- | --- |

![](Image00291.jpg) function definition ( () { ) and in the calling reference ( function

 
| callFunction || (& || $variable |
| --- | --- | --- |

 
| ... || or & || myFunction |
| --- | --- | --- |

![](Image00292.jpg) ) {(); ).

 
| Notice || : || Only |
| --- | --- | --- |

![](Image00293.jpg)You can only return a variable by reference. Hence the instantiation of $a in the example above. This means you can not return an expression, otherwise an E\_NOTICE PHP error will be generated (

 
| variable references should be returned by reference in ...... |
| --- |

).

![](Image00294.jpg)Return by reference does have legitimate use cases, but I should warn that they should be used sparingly, only after exploring all other potential options of achieving the same goal.

## Section 11.3: Pass by Reference

This allows you to pass a variable by reference to a function or element that allows you to modify the original variable.

Passing-by-reference is not limited to variables only, the following can also be passed by reference:

 
| foo || ( || new SomeClass |
| --- | --- | --- |

![](Image00295.jpg)New statements, e.g. )

References returned from functions

Arrays

 
| $myElement |
| --- |

A common use of ["passing-by-reference"](http://php.net/manual/en/language.references.pass.php) is to modify initial values within an array without going to the extent of creating new arrays or littering your namespace. Passing-by-reference is as simple as preceding/prefixing the variable with an & \=> & .

Below is an example of harnessing an element from an array and simply adding 1 to its initial value.

![](Image00296.jpg)

Now when you harness any element within $arr , the original element will be updated as the reference was increased. You can verify this by:

![](Image00297.jpg)

Functions

Another common usage for passing-by-reference is within functions. Modifying the original variable is as simple as:

![](Image00298.jpg)

Which can be verified by echo 'ing the original variable.

![](Image00299.jpg)

There are various restrictions around functions, as noted below from the PHP docs:

![](Image00300.jpg)![](Image00301.jpg)Note: There is no reference sign on a function call - only on function definitions. Function definitions alone are enough to correctly pass the argument by reference. As of PHP 5.3.0, you will get a warning saying that "call-time pass-by-reference" is deprecated when you use & in foo(&$a);. And as of PHP 5.4.0, call-time pass-by-reference was removed, so using it will raise a fatal error.

  

# Chapter 12: Arrays

Parameter Detail

The key is the unique identifier and index of an array. It may be a string or an integer . Therefore,

 
| 'foo' || , ||   '5' || , ||   10 || , ||   'a2b' || , ||   ... |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

Key valid keys would be

For each key there is a corresponding value ( null otherwise and a notice is emitted upon access ). The

Value value has no restrictions on the input type.

An array is a data structure that stores an arbitrary number of values in a single value. An array in PHP is actually an ordered map, where map is a type that associates values to keys.

## Section 12.1: Initializing an Array

An array can be initialized empty:

![](Image00302.jpg)

An array can be initialized and preset with values:

![](Image00303.jpg)

An array can also be initialized with custom indexes (also called an associative array) :

![](Image00304.jpg)

If the variable hasn't been used before, PHP will create it automatically. While convenient, this might make the code harder to read:

![](Image00305.jpg)

![](Image00306.jpg)

The index will usually continue where you left off. PHP will try to use numeric strings as integers:

$foo \= \[2 \=> 'apple' , 'melon' \];   // Array( \[2\] => apple, \[3\] => melon )

$foo \= \[ '2' \=> 'apple' , 'melon' \]; // same as above

![](Image00307.jpg) $foo \= \[2 \=> 'apple' , 'this is index 3 temporarily' , '3' \=> 'melon' \]; // same as above! The last entry will overwrite the second!

To initialize an array with fixed size you can use [SplFixedArray](https://secure.php.net/manual/en/class.splfixedarray.php) :

![](Image00308.jpg)

Note: An array created using SplFixedArray has a reduced memory footprint for large sets of data, but the keys must be integers.

To initialize an array with a dynamic size but with n non empty elements (e.g. a placeholder) you can use a loop as follows:

![](Image00309.jpg)

 
| [array\_fill](https://secure.php.net/manual/en/function.array-fill.php) |
| --- |

If all your placeholders are the same then you can also create it using the function [(](https://secure.php.net/manual/en/function.array-fill.php) [)](https://secure.php.net/manual/en/function.array-fill.php) :

![](Image00310.jpg)              array array\_fill ( int $start\_index , int $num , mixed $value )

This creates and returns an array with num entries of value , keys starting at start\_index .

Note: If the start\_index is negative it will start with the negative index and continue from 0 for the following elements.

![](Image00311.jpg) $a \= array\_fill (5, 6, 'banana' ); // Array ( \[5\] => banana, \[6\] => banana, ..., \[10\] => banana)

$b \= array\_fill (-2, 4, 'pear' ); // Array ( \[-2\] => pear, \[0\] => pear, ..., \[2\] => pear)

 
| [array\_fil](https://secure.php.net/manual/en/function.array-fill.php) [l](https://secure.php.net/manual/en/function.array-fill.php) |
| --- |

Conclusion: With [(](https://secure.php.net/manual/en/function.array-fill.php) [)](https://secure.php.net/manual/en/function.array-fill.php) you are more limited for what you can actually do. The loop is more flexible and opens you a wider range of opportunities.

 
| [range](https://secure.php.net/manual/en/function.range.php) |
| --- |

Whenever you want an array filled with a range of numbers (e.g. 1-4) you could either append every single element to an array or use the [(](https://secure.php.net/manual/en/function.range.php) [)](https://secure.php.net/manual/en/function.range.php) function:

![](Image00312.jpg)              array range ( mixed $start , mixed $end \[, number $step = 1 \] )

This function creates an array containing a range of elements. The first two parameters are required, where they set the start and end points of the (inclusive) range. The third parameter is optional and defines the size of the steps being taken. Creating a range from 0 to 4 with a stepsize of 1 , the resulting array would consist of the following elements: ![](Image00313.jpg)0 , 1 , 2 , 3 , and 4 . If the step size is increased to 2 (i.e. (0, 4, 2) ) then the resulting array range can work with integers, floats, booleans (which become casted to integers), and strings. Caution should be taken, however, when using floats as arguments due to the floating point precision problem.

## Section 12.2: Check if key exists

![](Image00314.jpg)

 
| isset || () treats a null valued element as non-existent. Whereas ! || empty |
| --- | --- | --- |

 
| empty |
| --- |

Note that () does the same for any element that equals false (using a weak comparision; for example, null , '' and 0 are all treated as false by !() ).

 
| isset || ( || $map || \[ || 'foobar' || \]); is true , ! || empty || ( || $map || \[ || 'foobar' |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

 
| empty |
| --- |

While \]) is false . This can lead to mistakes (for example, it is easy to forget that the string '0' is treated as false) so use of !() is often frowned upon.

 
| isset || () and ! || empty |
| --- | --- | --- |

Note also that () will work (and return false) if $map is not defined at all. This makes them somewhat error-prone to use:

// Note "long" vs "lang", a tiny typo in the variable name.

![](Image00315.jpg) $my\_array\_with\_a\_long\_name \= \[ 'foo' \=> true \]; array\_key\_exists ( 'foo' , $my\_array\_with\_a\_lang\_name ); // shows a warning isset ( $my\_array\_with\_a\_lang\_name \[ 'foo' \]); // returns false

You can also check for ordinal arrays:

![](Image00316.jpg)

 
| isset || () has better performance than || array\_key\_exists |
| --- | --- | --- |

Note that () as the latter is a function and the former a language construct.

 
| [key\_exists](http://php.net/manual/en/function.key-exists.php) || [(](http://php.net/manual/en/function.key-exists.php) [)](http://php.net/manual/en/function.key-exists.php) , which is an alias for || array\_key\_exists |
| --- | --- | --- |

You can also use () .

## Section 12.3: Validating the array type

 
| [is\_array](http://php.net/manual/en/function.is-array.php) |
| --- |

The function [(](http://php.net/manual/en/function.is-array.php) [)](http://php.net/manual/en/function.is-array.php) returns true if a variable is an array.

![](Image00317.jpg)

You can type hint the array type in a function to enforce a parameter type; passing anything else will result in a fatal error.

![](Image00318.jpg)

![](Image00319.jpg)

## Section 12.4: Creating an array of variables

![](Image00320.jpg)

This method is often used in frameworks to pass an array of variables between two components.

## Section 12.5: Checking if a value exists in array

 
| [in\_array](http://php.net/manual/en/function.in-array.php) |
| --- |

The function [(](http://php.net/manual/en/function.in-array.php) [)](http://php.net/manual/en/function.in-array.php) returns true if an item exists in an array.

![](Image00321.jpg)

![](Image00322.jpg)

 
| [array\_search](http://php.net/manual/en/function.array-search.php) |
| --- |

You can also use the function [(](http://php.net/manual/en/function.array-search.php) [)](http://php.net/manual/en/function.array-search.php) to get the key of a specific item in an array.

![](Image00323.jpg)

PHP 5.x Version ≥ 5.5

 
| [array\_colum](http://php.net/manual/en/function.array-column.php) [n](http://php.net/manual/en/function.array-column.php) || [(](http://php.net/manual/en/function.array-column.php) [)](http://php.net/manual/en/function.array-column.php) in conjunction with || array\_search |
| --- | --- | --- |

In PHP 5.5 and later you can use () .

This is particularly useful for [checking if a value exists in an associative array](http://stackoverflow.com/questions/6990855/php-check-if-value-and-key-exist-in-multidimensional-array/37935356#37935356) :

![](Image00324.jpg)

## Section 12.6: ArrayAccess and Iterator Interfaces

Another useful feature is accessing your custom object collections as arrays in PHP. There are two interfaces available in PHP (>=5.0.0) core to support this: ArrayAccess and Iterator . The former allows you to access your custom objects as array.

ArrayAccess

Assume we have a user class and a database table storing all the users. We would like to create a UserCollection class that will:

1.    allow us to address certain user by their username unique identifier

2.    perform basic (not all CRUD, but at least Create, Retrieve and Delete) operations on our users collection

Consider the following source (hereinafter we're using short array creation syntax \[\] available since version 5.4):

![](Image00325.jpg)

![](Image00326.jpg)

then we can:

$users \= new UserCollection ();

var\_dump ( empty ( $users \[ 'testuser' \]), isset ( $users \[ 'testuser' \])); $users \[ 'testuser' \] \= \[ 'username' \=> 'testuser' ,

![](Image00327.jpg)                       'password' \=> 'testpassword' ,                       'email'     \=> 'test@test.com' \]; var\_dump ( empty ( $users \[ 'testuser' \]), isset ( $users \[ 'testuser' \]), $users \[ 'testuser' \]); unset ( $users \[ 'testuser' \]); var\_dump ( empty ( $users \[ 'testuser' \]), isset ( $users \[ 'testuser' \]));

which will output the following, assuming there was no testuser before we launched the code:

![](Image00328.jpg)

IMPORTANT: offsetExists is not called when you check existence of a key with array\_key\_exists function. So the following code will output false twice:

var\_dump ( array\_key\_exists ( 'testuser' , $users )); $users \[ 'testuser' \] \= \[ 'username' \=> 'testuser' ,

![](Image00329.jpg)                       'password' \=> 'testpassword' ,                       'email'     \=> 'test@test.com' \]; var\_dump ( array\_key\_exists ( 'testuser' , $users ));

Iterator

Let's extend our class from above with a few functions from Iterator interface to allow iterating over it with foreach and while .

First, we need to add a property holding our current index of iterator, let's add it to the class properties as $\_position :

![](Image00330.jpg)

Second, let's add Iterator interface to the list of interfaces being implemented by our class:

![](Image00331.jpg)

then add the required by the interface functions themselves:

![](Image00332.jpg)

![](Image00333.jpg)

So all in all here is complete source of the class implementing both interfaces. Note that this example is not perfect, because the IDs in the database may not be sequential, but this was written just to give you the main idea: you can address your objects collections in any possible way by implementing ArrayAccess and Iterator interfaces:

![](Image00334.jpg)

and a foreach looping through all user objects:

![](Image00335.jpg)

which will output something like

![](Image00336.jpg)

# Chapter 13: Array iteration

## Section 13.1: Iterating multiple arrays together

Sometimes two arrays of the same length need to be iterated together, for example:

![](Image00337.jpg)

array\_map is the simplest way to accomplish this:

![](Image00338.jpg)

which will output:

![](Image00339.jpg)

This can be done through a common index:

![](Image00340.jpg)

 
| array\_values || ( || $array || )\[ || $i || \] can be used to replace || $array || \[ || $i |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

If the two arrays don't have the incremental keys, \] .

If both arrays have the same order of keys, you can also use a foreach-with-key loop on one of the arrays:

![](Image00341.jpg)

Separate arrays can only be looped through if they are the same length and also have the same key name. This means if you don't supply a key and they are numbered, you will be fine, or if you name the keys and put them in the same order in each array.

You can also use array\_combine .

$combinedArray \= array\_combine ( $people , $foods );

![](Image00342.jpg) // $combinedArray = \['Tim' => 'chicken', 'Tony' => 'beef', 'Turanga' => 'slurm'\];

Then you can loop through this by doing the same as before:

![](Image00343.jpg)

## Section 13.2: Using an incremental index

This method works by incrementing an integer from 0 to the greatest index in the array.

![](Image00344.jpg)

This also allows iterating an array in reverse order without using array\_reverse , which may result in overhead if the array is large.

![](Image00345.jpg)

You can skip or rewind the index easily using this method.

![](Image00346.jpg)

Output:

For arrays that do not have incremental indices (including arrays with indices in reverse order, e.g. ![](Image00347.jpg)\[1

 
| \=> "bar" || \] , \[ || "foo" \=> "f" || , ||   "bar" \=> "b" |
| --- | --- | --- | --- | --- |

\] ), this cannot be done directly. array\_values or array\_keys can be

used instead:

![](Image00348.jpg)

## Section 13.3: Using internal array pointers

Each array instance contains an internal pointer. By manipulating this pointer, different elements of an array can be retrieved from the same call at different times.

Using [each](http://php.net/each)

 
| each |
| --- |

Each call to () returns the key and value of the current array element, and increments the internal array pointer.

![](Image00349.jpg)

Using [next](http://php.net/next)

![](Image00350.jpg)

Note that this example assumes no elements in the array are identical to boolean false . To prevent such assumption, use [key](http://php.net/key) to check if the internal pointer has reached the end of the array:

![](Image00351.jpg)

This also facilitates iterating an array without a direct loop:

![](Image00352.jpg)

## Section 13.4: Using foreach

Direct loop

![](Image00353.jpg)

Loop with keys

![](Image00354.jpg)

Loop by reference

In the foreach loops in the above examples, modifying the value ( $color or $food ) directly doesn't change its value in the array. The & operator is required so that the value is a reference pointer to the element in the array.

![](Image00355.jpg)

![](Image00356.jpg)

This is similar to:

![](Image00357.jpg)

Concurrency

PHP arrays can be modified in any ways during iteration without concurrency problems (unlike e.g. Java List s). If the array is iterated by reference, later iterations will be affected by changes to the array. Otherwise, the changes to the array will not affect later iterations (as if you are iterating a copy of the array instead). Compare looping by value:

![](Image00358.jpg)

Output:

![](Image00359.jpg)

But if the array is iterated with reference,

![](Image00360.jpg)

Output:

![](Image00361.jpg)

 
|   \=> || 5 is no longer iterated, and 6 ||   \=> || 7 is changed to 6 ||   \=> 17 |
| --- | --- | --- | --- | --- |

The key-value set of 4 .

## Section 13.5: Using ArrayObject Iterator

Php arrayiterator allows you to modify and unset the values while iterating over arrays and objects.

Example:

![](Image00362.jpg)

Output:

![](Image00363.jpg)

  

# Chapter 14: Executing Upon an Array

## Section 14.1: Applying a function to each element of an array

 
| array\_map |
| --- |

To apply a function to every item in an array, use () . This will return a new array.

![](Image00364.jpg)

Instead of using an anonymous function, you could use a named function. The above could be written like:

![](Image00365.jpg)

If the named function is a class method the call of the function has to include a reference to a class object the method belongs to:

![](Image00366.jpg)

 
| array\_walk || () and || array\_walk\_recursive |
| --- | --- | --- |

Another way to apply a function to every item in an array is () . The

callback passed into these functions take both the key/index and value of each array item. These functions will not return a new array, instead a boolean for success. For example, to print every element in a simple array:

![](Image00367.jpg)

The value parameter of the callback may be passed by reference, allowing you to change the value directly in the original array:

![](Image00368.jpg)

 
| array |
| --- |

$array now is (2,3,4,5,6);

 
| array\_walk\_recursive |
| --- |

For nested arrays, () will go deeper into each sub-array:

![](Image00369.jpg)

Note : array\_walk and array\_walk\_recursive let you change the value of array items, but not the keys. Passing the keys by reference into the callback is valid but has no effect.

## Section 14.2: Split array into chunks

[array\_chunk()](http://php.net/manual/en/function.array-chunk.php) splits an array into chunks

Let's say we've following single dimensional array,

![](Image00370.jpg)

Now using array\_chunk() on above PHP array,

![](Image00371.jpg)

Above code will make chunks of 2 array elements and create a multidimensional array as follow.

![](Image00372.jpg)

If all the elements of the array is not evenly divided by the chunk size, last element of the output array will be remaining elements.

If we pass second argument as less then 1 then E\_WARNING will be thrown and output array will be NULL .

 
| Parameter || Details |
| --- | --- |
| $array (array) || Input array, the array to work on |
| $size (int) || Size of each chunk ( Integer value) |

$preserve\_keys (boolean) (optional) If you want output array to preserve the keys set it to TRUE otherwise FALSE .

## Section 14.3: Imploding an array into string

 
| implode |
| --- |

() combines all the array values but looses all the key info:

![](Image00373.jpg)

 
| array\_keys |
| --- |

Imploding keys can be done using () call:

![](Image00374.jpg)

Imploding keys with values is more complex but can be done using functional style:

![](Image00375.jpg)

## Section 14.4: "Destructuring" arrays using list()

Use [list()](http://php.net/manual/en/function.list.php) to quick assign a list of variable values into an array. See also compact()

![](Image00376.jpg)

With PHP 7.1 (currently in beta) you will be able to use [short list syntax](https://wiki.php.net/rfc/short_list_syntax) :

![](Image00377.jpg)

## Section 14.5: array\_reduce

array\_reduce reduces array into a single value. Basically, The array\_reduce will go through every item with the result from last iteration and produce new value to the next iteration.

 
| array\_reduce || ( || $array || , ||   function || ( || $carry || , ||   $item || ){ || ... || }, ||   $defaul\_value\_of\_first\_carry |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Usage: )

![](Image00378.jpg)$carry is the result from the last round of iteration. $item is the value of current position in the array.

Sum of array

![](Image00379.jpg)

![](Image00380.jpg)

result: 15

The largest number in array

![](Image00381.jpg)

result: 211

Is all item more than 100

![](Image00382.jpg) $result \= array\_reduce (\[101, 230, 210, 341, 251\], function ( $carry , $item ){         return $carry && $item \> 100;

}, true ); //default value must set true result: true

Is any item less than 100

![](Image00383.jpg) $result \= array\_reduce (\[101, 230, 21, 341, 251\], function ( $carry , $item ){         return $carry || $item < 100;

}, false ); //default value must set false result: true

Like implode($array, $piece)

![](Image00384.jpg)

result: "hello-world-PHP-language" if make a implode method, the source code will be:

![](Image00385.jpg)

## Section 14.6: Push a Value on an Array

 
| $array |
| --- |

![](Image00386.jpg) There are two ways to push an element to an array: array\_push and \[\] \= The [array\_push](http://php.net/manual/fr/function.array-push.php) is used like this:

$array \= \[1,2,3\];

![](Image00387.jpg) $newArraySize \= array\_push ( $array , 5, 6); // The method returns the new size of the array print\_r ( $array ); // Array is passed by reference, therefore the original array is modified to

![](Image00388.jpg)

![](Image00389.jpg)

![](Image00390.jpg)

# Chapter 15: Manipulating an Array

## Section 15.1: Filtering an array

In order to filter out values from an array and obtain a new array containing all the values that satisfy the filter condition, you can use the array\_filter function.

Filtering non-empty values

The simplest case of filtering is to remove all "empty" values:

$my\_array \= \[1,0,2, null ,3, '' ,4,\[\],5,6,7,8\];

![](Image00391.jpg) $non\_empties \= array\_filter ( $my\_array ); // $non\_empties will contain \[1,2,3,4,5,6,7,8\];

Filtering by callback

This time we define our own filtering rule. Suppose we want to get only even numbers:

![](Image00392.jpg)

The array\_filter function receives the array to be filtered as its first argument, and a callback defining the filter predicate as its second.

Version ≥ 5.6

Filtering by index

A third parameter can be provided to the array\_filter function, which allows to tweak which values are passed to the callback. This parameter can be set to either ARRAY\_FILTER\_USE\_KEY or ARRAY\_FILTER\_USE\_BOTH , which will result in the callback receiving the key instead of the value for each element in the array, or both value and key as its arguments. For example, if you want to deal with indexes istead of values:

![](Image00393.jpg)

Note that array\_filter preserves the original array keys. A common mistake would be to try an use for loop over the filtered array:

![](Image00394.jpg)

![](Image00395.jpg)

This happens because the values which were on positions 1 (there was 0 ), 3 ( null ), 5 (empty string '' ) and 7 (empty array \[\] ) were removed along with their corresponding index keys.

If you need to loop through the result of a filter on an indexed array, you should first call array\_values on the result of array\_filter in order to create a new array with the correct indexes:

![](Image00396.jpg)

## Section 15.2: Removing elements from an array

To remove an element inside an array, e.g. the element with the index 1.

![](Image00397.jpg)

This will remove the apples from the list, but notice that unset does not change the indexes of the remaining elements. So $fruit now contains the indexes 0 and 2 .

For associative array you can remove like this:

![](Image00398.jpg)

Now $fruit is

![](Image00399.jpg)

Note that

![](Image00400.jpg)

unsets the variable and thus removes the whole array, meaning none of its elements are accessible anymore. Removing terminal elements

[array\_shift()](http://php.net/manual/en/function.array-shift.php) \- Shift an element off the beginning of array.

Example:

![](Image00401.jpg)

Output:

![](Image00402.jpg)

[array\_pop()](http://php.net/manual/en/function.array-pop.php) \- Pop the element off the end of array.

Example:

![](Image00403.jpg)

Output:

![](Image00404.jpg)

## Section 15.3: Sorting an Array

There are several sort functions for arrays in php: sort()

Sort an array in ascending order by value.

![](Image00405.jpg)

results in

![](Image00406.jpg)

rsort()

Sort an array in descending order by value.

![](Image00407.jpg)

results in

![](Image00408.jpg)

asort()

Sort an array in ascending order by value and preserve the indices.

![](Image00409.jpg)

results in

![](Image00410.jpg)

arsort()

Sort an array in descending order by value and preserve the indices.

![](Image00411.jpg)

results in

![](Image00412.jpg)

ksort()

Sort an array in ascending order by key

![](Image00413.jpg)

results in

![](Image00414.jpg)

krsort()

Sort an array in descending order by key.

![](Image00415.jpg)

results in

![](Image00416.jpg)

natsort()

Sort an array in a way a human being would do (natural order).

![](Image00417.jpg)

results in

![](Image00418.jpg)

![](Image00419.jpg)

natcasesort()

Sort an array in a way a human being would do (natural order), but case intensive

![](Image00420.jpg)

results in

![](Image00421.jpg)

shuffle()

Shuffles an array (sorted randomly).

![](Image00422.jpg)

As written in the description it is random so here only one example in what it can result

![](Image00423.jpg)

usort()

Sort an array with a user defined comparison function.

![](Image00424.jpg)

results in

![](Image00425.jpg)

![](Image00426.jpg)

uasort()

Sort an array with a user defined comparison function and preserve the keys.

![](Image00427.jpg)

results in

![](Image00428.jpg)

uksort()

Sort an array by keys with a user defined comparison function.

![](Image00429.jpg)

results in

![](Image00430.jpg)

## Section 15.4: Whitelist only some array keys

When you want to allow only certain keys in your arrays, especially when the array comes from request parameters, you can use array\_intersect\_key together with array\_flip .

$parameters \= \[ 'foo' \=> 'bar' , 'bar' \=> 'baz' , 'boo' \=> 'bam' \];

$allowedKeys \= \[ 'foo' , 'bar' \];

![](Image00431.jpg) $filteredParameters \= array\_intersect\_key ( $parameters , array\_flip ( $allowedKeys ));

// $filteredParameters contains \['foo' => 'bar', 'bar' => 'baz\]

If the parameters variable doesn't contain any allowed key, then the filteredParameters variable will consist of an empty array.

Since PHP 5.6 you can use [array\_filter](http://php.net/manual/en/function.array-filter.php#refsect1-function.array-filter-changelog) for this task too, passing the [ARRAY\_FILTER\_USE\_KEY](http://php.net/manual/en/array.constants.php#constant.array-filter-use-key) flag as the third parameter:

![](Image00432.jpg)

 
| array\_intersect\_key || () combined with || array\_flip |
| --- | --- | --- |

Using array\_filter gives the additional flexibility of performing an arbitrary test against the key, e.g. $allowedKeys could contain regex patterns instead of plain strings. It also more explicitly states the intention of the code than () .

## Section 15.5: Adding element to start of array

 
| [array\_unshift](http://php.net/array_unshift) |
| --- |

Sometimes you want to add an element to the beginning of an array without modifying any of the current elements ( order ) within the array . Whenever this is the case, you can use [(](http://php.net/array_unshift) [)](http://php.net/array_unshift) .

() prepends passed elements to the front of the array. Note that the list of elements is

 
| array\_unshift |
| --- |

![](Image00433.jpg)prepended as a whole, so that the prepended elements stay in the same order. All numerical array keys will be modified to start counting from zero while literal keys won't be touched.

 
| array\_unshift |
| --- |

Taken from the [PHP documentation](http://php.net/array_unshift#refsect1-function.array-unshift-description) for () .

If you'd like to achieve this, all you need to do is the following:

![](Image00434.jpg)

This will now add 4 as the first element in your array. You can verify this by:

![](Image00435.jpg)

 
| n +1 |
| --- |

Since array\_unshift forces the array to reset the key-value pairs as the new element let the following entries have the keys  it is smarter to create a new array and append the existing array to the newly created array.

Example:

![](Image00436.jpg)

Output ($joinedArray):

![](Image00437.jpg) Array ( \[0\] \=> oranges \[1\] \=> apples \[2\] \=> bananas \[3\] \=> pears )

[Eaxmple/Demo](http://www.tehplayground.com/#egwNCrZgr)

## Section 15.6: Exchange values with keys

array\_flip function will exchange all keys with its elements.

![](Image00438.jpg)

## Section 15.7: Merge two arrays into one array

![](Image00439.jpg)

Associative array:

![](Image00440.jpg)

1.    Merges the elements of one or more arrays together so that the values of one are appended to the end of

the previous one. It returns the resulting array.

2.    If the input arrays have the same string keys, then the later value for that key will overwrite the previous one. If, however, the arrays contain numeric keys, the later value will not overwrite the original value, but will be appended.

3.    Values in the input array with numeric keys will be renumbered with incrementing keys starting from zero in the result array.

  

# Chapter 16: Processing Multiple Arrays Together

## Section 16.1: Array intersection

The array\_intersect function will return an array of values that exist in all arrays that were passed to this function.

![](Image00441.jpg)

Array keys are preserved. Indexes from the original arrays are not.

array\_intersect only check the values of the arrays. array\_intersect\_assoc function will return intersection of arrays with keys.

$array\_one \= \[1 \=> 'one' ,2 \=> 'two' ,3 \=> 'three' \];

$array\_two \= \[1 \=> 'one' , 2 \=> 'two' , 3 \=> 'two' , 4 \=> 'three' \];

$array\_three \= \[1 \=> 'one' , 2 \=> 'two' \];

![](Image00442.jpg) $intersect \= array\_intersect\_assoc ( $array\_one , $array\_two , $array\_three ); // $intersect contains \[1 =>'one',2 => 'two'\] array\_intersect\_key function only check the intersection of keys. It will returns keys exist in all arrays.

![](Image00443.jpg)

## Section 16.2: Merge or concatenate arrays

![](Image00444.jpg)

Note that array\_merge will change numeric indexes, but overwrite string indexes

![](Image00445.jpg)

array\_merge overwrites the values of the first array with the values of the second array, if it cannot renumber the index.

You can use the + operator to merge two arrays in a way that the values of the first array never get overwritten, but it does not renumber numeric indexes, so you lose values of arrays that have an index that is also used in the first array.

![](Image00446.jpg)

## Section 16.3: Changing a multidimensional array to associative array

If you have a multidimensional array like this:

![](Image00447.jpg)

And you want to change it to an associative array like this:

![](Image00448.jpg)

You can use this code:

![](Image00449.jpg)

Or, you can skip setting $associativeArrayKeys and $associativeArrayValues and use this simple one liner:

![](Image00450.jpg) $associativeArray \= array\_combine ( array\_column ( $multidimensionalArray , 0), array\_column ( $multidimensionalArray , 1));

## Section 16.4: Combining two arrays (keys from one, values from another)

The following example shows how to merge two arrays into one associative array, where the key values will be the items of the first array, and the values will be from the second:

![](Image00451.jpg)

![](Image00452.jpg)

  

# Chapter 17: Datetime Class

## Section 17.1: Create Immutable version of DateTime from Mutable prior PHP 5.6

To create \\DateTimeImmutable in PHP 5.6+ use:

![](Image00453.jpg)

Prior PHP 5.6 you can use:

![](Image00454.jpg) \\DateTimeImmutable :: createFromFormat ( \\DateTime :: ISO8601 , $mutable \-> format ( \\DateTime :: ISO8601 ), $mutable \-> getTimezone ());

## Section 17.2: Add or Subtract Date Intervals

We can use the class [DateInterval](http://php.net/manual/pt_BR/class.dateinterval.php) to add or subtract some interval in a DateTime object.

See the example below, where we are adding an interval of 7 days and printing a message on the screen:

$now \= new DateTime (); // empty argument returns the current date

$interval \= new DateInterval ( 'P7D' ); //this objet represents a 7 days interval

$lastDay \= $now \-> add ( $interval ); //this will return a DateTime object

![](Image00455.jpg) $formatedLastDay \= $lastDay \-> format ( 'Y-m-d' ); //this method format the DateTime object and returns a String

echo "Samara says: Seven Days. You'll be happy on $formatedLastDay ." ; This will output (running on Aug 1st, 2016):

![](Image00456.jpg)              Samara says: Seven Days. You'll be happy on 2016-08-08.

We can use the sub method in a similar way to subtract dates

![](Image00457.jpg)

This will output (running on Aug 1st, 2016):

![](Image00458.jpg)              Samara says: Seven Days. You were happy last on 2016-07-25.

## Section 17.3: getTimestamp

getTimeStemp is a unix representation of a datetime object.

![](Image00459.jpg)

this will out put an integer indication the seconds that have elapsed since 00:00:00 UTC, Thursday, 1 January 1970.

## Section 17.4: setDate

setDate sets the date in a DateTime object.

![](Image00460.jpg)

this example sets the date to be the twenty-fifth of July, 2015, it will produce the following result:

![](Image00461.jpg)

## Section 17.5: Create DateTime from custom format

PHP is able to parse [a number of date formats](https://secure.php.net/manual/en/datetime.formats.php) . If you want to parse a non-standard format, or if you want your

 
| [DateTime](https://php.net/manual/en/datetime.createfromformat.php) [::](https://php.net/manual/en/datetime.createfromformat.php) [createFromFormat](https://php.net/manual/en/datetime.createfromformat.php) |
| --- |

code to explicitly state the format to be used, then you can use the static  method:

Object oriented style

![](Image00462.jpg)

Procedural style

![](Image00463.jpg)

## Section 17.6: Printing DateTimes

PHP 4+ supplies a method, format that converts a DateTime object into a string with a desired format. According to PHP Manual, this is the object oriented function:

![](Image00464.jpg)

The function date() takes one parameters - a format, which is a string

Format

The format is a string, and uses single characters to define the format:

![](Image00465.jpg)Y : four digit representation of the year (eg: 2016) y : two digit representation of the year (eg: 16) m : month, as a number (01 to 12)

M : month, as three letters (Jan, Feb, Mar, etc) j : day of the month, with no leading zeroes (1 to 31) D : day of the week, as three letters (Mon, Tue, Wed, etc) h : hour (12-hour format) (01 to 12)

H : hour (24-hour format) (00 to 23) A : either AM or PM i : minute, with leading zeroes (00 to 59) s : second, with leading zeroes (00 to 59) The complete list can be found [here](http://php.net/manual/en/function.date.php) Usage

These characters can be used in various combinations to display times in virtually any format. Here are some examples:

![](Image00466.jpg)

Procedural

The procedural format is similar:

![](Image00467.jpg)

![](Image00468.jpg)

# Chapter 18: Working with Dates and Time

## Section 18.1: Getting the dierence between two dates / times

The most feasible way is to use, the DateTime class.

An example:

![](Image00469.jpg)

Also, comparing two dates is much easier, just use the Comparison operators , like:

<?php

// Create a date time object, which has the value of ~ two years ago

$twoYearsAgo \= new DateTime ( "2014-01-18 20:05:56" );

// Create a date time object, which has the value of ~ now

![](Image00470.jpg) $now \= new DateTime ( "2016-07-21 02:55:07" ); var\_dump ( $now \> $twoYearsAgo ); // prints bool(true) var\_dump ( $twoYearsAgo \> $now ); // prints bool(false) var\_dump ( $twoYearsAgo <= $twoYearsAgo ); // prints bool(true) var\_dump ( $now \== $now ); // prints bool(true)

## Section 18.2: Convert a date into another format

The Basics

 
| [strtotime](http://docs.php.net/manual/en/function.strtotime.php) [(](http://docs.php.net/manual/en/function.strtotime.php) [)](http://docs.php.net/manual/en/function.strtotime.php) || with || [date](http://docs.php.net/manual/en/function.date.php) [(](http://docs.php.net/manual/en/function.date.php) [)](http://docs.php.net/manual/en/function.date.php) || . || strtotime () |
| --- | --- | --- | --- | --- |

The simplist way to convert one date format into another is to use  will

 
| date () |
| --- |

convert the date into a [Unix Timestamp](http://en.wikipedia.org/wiki/Unix_time) . That Unix Timestamp can then be passed to  to convert it to the new format.

![](Image00471.jpg)

![](Image00472.jpg)

Or as a one-liner:

![](Image00473.jpg) $new\_date\_format \= date ( 'Y-m-d H:i:s' , strtotime ( '2008-07-01T22:35:17.02' ));

 
| strtotime |
| --- |

 
| strtotime |
| --- |

Keep in mind that () requires the date to be in a [valid format](https://php.net/manual/en/datetime.formats.php) . Failure to provide a valid format will result in () returning false which will cause your date to be 1969-12-31.

 
| DateTime |
| --- |

Using ()

 
| [DateTime](http://docs.php.net/manual/en/class.datetime.php) |
| --- |

 
| DateTime |
| --- |

As of PHP 5.2, PHP offered the [(](http://docs.php.net/manual/en/class.datetime.php) [)](http://docs.php.net/manual/en/class.datetime.php) class which offers us more powerful tools for working with dates (and time). We can rewrite the above code using () as so:

![](Image00474.jpg)

Working with Unix timestamps

 
| date |
| --- |

() takes a Unix timestamp as its second parameter and returns a formatted date for you:

![](Image00475.jpg)

DateTime() works with Unix timestamps by adding an @ before the timestamp:

![](Image00476.jpg)

If the timestamp you have is in milliseconds (it may end in 000 and/or the timestamp is thirteen characters long) you will need to convert it to seconds before you can can convert it to another format. There's two ways to do this:

 
| [substr](http://php.net/manual/en/function.substr.php) |
| --- |

![](Image00477.jpg)Trim the last three digits off using [(](http://php.net/manual/en/function.substr.php) [)](http://php.net/manual/en/function.substr.php)

 
| substr |
| --- |

Trimming the last three digits can be achieved several ways, but using () is the easiest:

![](Image00478.jpg)

You can also convert the timestamp into seconds by dividing by 1000. Because the timestamp is too large for 32 bit systems to do math on you will need to use the [BCMath](http://php.net/manual/en/book.bc.php) library to do the math as strings:

![](Image00479.jpg)

 
| strtotime |
| --- |

To get a Unix Timestamp you can use () which returns a Unix Timestamp:

![](Image00480.jpg)

 
| [DateTime](http://php.net/manual/en/datetime.gettimestamp.php) [::](http://php.net/manual/en/datetime.gettimestamp.php) [getTimestamp](http://php.net/manual/en/datetime.gettimestamp.php) |
| --- |

With DateTime() you can use [(](http://php.net/manual/en/datetime.gettimestamp.php) [)](http://php.net/manual/en/datetime.gettimestamp.php)

![](Image00481.jpg)

If you're running PHP 5.2 you can use the U formatting option instead:

![](Image00482.jpg)

Working with non-standard and ambiguous date formats

Unfortunately not all dates that a developer has to work with are in a standard format. Fortunately PHP 5.3

 
| [DateTime](http://docs.php.net/manual/en/datetime.createfromformat.php) [::](http://docs.php.net/manual/en/datetime.createfromformat.php) [createFromFormat](http://docs.php.net/manual/en/datetime.createfromformat.php) |
| --- |

provided us with a solution for that. [(](http://docs.php.net/manual/en/datetime.createfromformat.php) [)](http://docs.php.net/manual/en/datetime.createfromformat.php) allows us to tell PHP what format a date string is in so it can be successfully parsed into a DateTime object for further manipulation.

![](Image00483.jpg) $date \= DateTime :: createFromFormat ( 'F-d-Y h:i A' , 'April-18-1973 9:48 AM' );

$new\_date\_format \= $date \-> format ( 'Y-m-d H:i:s' );

 
| DateTime |
| --- |

In PHP 5.4 we gained the ability to do class member access on instantiation has been added which allows us to turn our () code into a one-liner:

![](Image00484.jpg) $new\_date\_format \= ( new DateTime ( '2008-07-01T22:35:17.02' ))-> format ( 'Y-m-d H:i:s' );

 
| DateTime :: createFromFormat |
| --- |

Unfortunately this does not work with () yet.

## Section 18.3: Parse English date descriptions into a Date format

 
| [strtotim](https://secure.php.net/manual/en/function.strtotime.php) [e](https://secure.php.net/manual/en/function.strtotime.php) || [(](https://secure.php.net/manual/en/function.strtotime.php) [)](https://secure.php.net/manual/en/function.strtotime.php) function combined with || [date](https://secure.php.net/manual/en/function.date.php) |
| --- | --- | --- |

Using the [(](https://secure.php.net/manual/en/function.date.php) [)](https://secure.php.net/manual/en/function.date.php) you can parse different English text descriptions to dates:

![](Image00485.jpg) // Gets the current date echo date ( "m/d/Y" , strtotime ( "now" )), " \\n " ; // prints the current date echo date ( "m/d/Y" , strtotime ( "10 September 2000" )), " \\n " ; // prints September 10, 2000 in the m/d/Y format echo date ( "m/d/Y" , strtotime ( "-1 day" )), " \\n " ; // prints yesterday's date echo date ( "m/d/Y" , strtotime ( "+1 week" )), " \\n " ; // prints the result of the current date + a week echo date ( "m/d/Y" , strtotime ( "+1 week 2 days 4 hours 2 seconds" )), " \\n " ; // same as the last example but with extra days, hours, and seconds added to it echo date ( "m/d/Y" , strtotime ( "next Thursday" )), " \\n " ; // prints next Thursday's date echo date ( "m/d/Y" , strtotime ( "last Monday" )), " \\n " ; // prints last Monday's date echo date ( "m/d/Y" , strtotime ( "First day of next month" )), " \\n " ; // prints date of first day of next month echo date ( "m/d/Y" , strtotime ( "Last day of next month" )), " \\n " ; // prints date of last day of next month echo date ( "m/d/Y" , strtotime ( "First day of last month" )), " \\n " ; // prints date of first day of last month echo date ( "m/d/Y" , strtotime ( "Last day of last month" )), " \\n " ; // prints date of last day of last month

## Section 18.4: Using Predefined Constants for Date Format

 
| date |
| --- |

We can use Predefined Constants for Date format in () instead of the conventional date format strings since PHP 5.1.0.

Predefined Date Format Constants Available

DATE\_ATOM \- Atom (2016-07-22T14:50:01+00:00)

DATE\_COOKIE \- HTTP Cookies (Friday, 22-Jul-16 14:50:01 UTC)

DATE\_RSS \- RSS (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_W3C \- World Wide Web Consortium (2016-07-22T14:50:01+00:00)

DATE\_ISO8601 \- ISO-8601 (2016-07-22T14:50:01+0000)

DATE\_RFC822 \- RFC 822 (Fri, 22 Jul 16 14:50:01 +0000)

DATE\_RFC850 \- RFC 850 (Friday, 22-Jul-16 14:50:01 UTC)

DATE\_RFC1036 \- RFC 1036 (Fri, 22 Jul 16 14:50:01 +0000)

DATE\_RFC1123 \- RFC 1123 (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_RFC2822 \- RFC 2822 (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_RFC3339 \- Same as DATE\_ATOM (2016-07-22T14:50:01+00:00)

Usage Examples

![](Image00486.jpg)

  

# Chapter 19: Control Structures

## Section 19.1: if else

The if statement in the example above allows to execute a code fragment, when the condition is met. When you want to execute a code fragment, when the condition is not met you extend the if with an else .

![](Image00487.jpg)

[PHP Manual - Control Structures - Else](http://php.net/manual/en/control-structures.else.php)

The ternary operator as shorthand syntax for if-else

The [ternary operator](http://php.net/manual/de/language.operators.comparison.php#language.operators.comparison.ternary) evaluates something based on a condition being true or not. It is a comparison operator and often used to express a simple if-else condition in a shorter form. It allows to quickly test a condition and often replaces a multi-line if statement, making your code more compact.

 
| $a || \=1; ||   $b |
| --- | --- | --- |

This is the example from above using a ternary expression and variable values: \=2;

![](Image00488.jpg) echo ( $a \> $b ) ? "a is greater than b" : "a is NOT greater than b" ;

Outputs: a is NOT greater than b .

## Section 19.2: Alternative syntax for control structures

PHP provides an alternative syntax for some control structures: if , while , for , foreach , and switch .

 
| endif || ; , || endwhile || ; , || endfor || ; , || endforeach || ; , or || endswitch |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

When compared to the normal syntax, the difference is, that the opening brace is replaced by a colon ( : ) and the closing brace is replaced by ; , respectively. For individual examples, see the topic on alternative syntax for control structures.

![](Image00489.jpg)

Multiple elseif statements using short-syntax:

![](Image00490.jpg)

[PHP Manual - Control Structures - Alternative Syntax](http://php.net/manual/en/control-structures.alternative-syntax.php)

## Section 19.3: while

while loop iterates through a block of code as long as a specified condition is true.

![](Image00491.jpg)

Output:

123456789

For detailed information, see the Loops topic.

## Section 19.4: do-while

 
| do || \- || while |
| --- | --- | --- |

loop first executes a block of code once, in every case, then iterates through that block of code as long as

a specified condition is true.

![](Image00492.jpg)

For detailed information, see the Loops topic.

## Section 19.5: goto

The goto operator allows to jump to another section in the program. It's available since PHP 5.3.

 
| goto MyLabel |
| --- |

The goto instruction is a goto followed by the desired target label: ; .

 
| MyLabel |
| --- |

The target of the jump is specified by a label followed by a colon: : .

 
| Hello World |
| --- |

This example will print ! :

![](Image00493.jpg)

## Section 19.6: declare

declare is used to set an execution directive for a block of code.

The following directives are recognized:

![](Image00494.jpg)[ticks](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.ticks) [encoding](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.encoding) [strict\_types](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)

For instance, set ticks to 1:

![](Image00495.jpg)

To enable strict type mode, the declare statement is used with the strict\_types declaration:

![](Image00496.jpg)

## Section 19.7: include & require

require

require is similar to include , except that it will produce a fatal E\_COMPILE\_ERROR level error on failure. When the require fails, it will halt the script. When the include fails, it will not halt the script and only emit E\_WARNING .

![](Image00497.jpg)

[PHP Manual - Control Structures - Require](http://php.net/manual/en/function.require.php) include

![](Image00498.jpg)

Be careful with this approach, since it is considered a [code smell](https://en.wikipedia.org/wiki/Code_smell) , because the included file is altering amount and content of the defined variables in the given scope.

You can also include file, which returns a value. This is extremely useful for handling configuration arrays:

![](Image00499.jpg)

![](Image00500.jpg)

This approach will prevent the included file from polluting your current scope with changed or added variables. [PHP Manual - Control Structures - Include](http://php.net/manual/en/function.include.php) include & require can also be used to assign values to a variable when returned something by file.

Example : include1.php file :

![](Image00501.jpg)

index.php file :

![](Image00502.jpg)

## Section 19.8: return

The return statement returns the program control to the calling function.

When return is called from within a function, the execution of the current function will end.

![](Image00503.jpg)

 
| returnEndsFunctions |
| --- |

When you run (); you'll get the output This is executed ;

When return is called from within a function with and argument, the execution of the current function will end and the value of the argument will be returned to the calling function.

## Section 19.9: for

for loops are typically used when you have a piece of code which you want to repeat a given number of times.

![](Image00504.jpg)

Outputs:

123456789

For detailed information, see the Loops topic.

## Section 19.10: foreach

foreach is a construct, which enables you to iterate over arrays and objects easily.

![](Image00505.jpg)

Outputs:

123

.

To use foreach loop with an object, it has to implement [Iterator](http://php.net/manual/en/class.iterator.php) interface.

When you iterate over associative arrays:

![](Image00506.jpg)

Outputs: color: red

For detailed information, see the Loops topic.

## Section 19.11: if elseif else

elseif elseif combines if and else . The if statement is extended to execute a different statement in case the original if expression is not met. But, the alternative expression is only executed, when the elseif conditional expression is met.

The following code displays either "a is bigger than b", "a is equal to b" or "a is smaller than b":

![](Image00507.jpg)

Several elseif statements

You can use multiple elseif statements within the same if statement:

![](Image00508.jpg)

![](Image00509.jpg)

## Section 19.12: if

The if construct allows for conditional execution of code fragments.

![](Image00510.jpg)

[PHP Manual - Control Structures - If](http://php.net/manual/en/control-structures.if.php)

## Section 19.13: switch

The switch structure performs the same function as a series of if statements, but can do the job in fewer lines of code. The value to be tested, as defined in the switch statement, is compared for equality with the values in each of the case statements until a match is found and the code in that block is executed. If no matching case statement is found, the code in the default block is executed, if it exists.

Each block of code in a case or default statement should end with the break statement. This stops the execution of the switch structure and continues code execution immediately afterwards. If the break statement is omitted, the next case statement's code is executed, even if there is no match . This can cause unexpected code execution if the break statement is forgotten, but can also be useful where multiple case statements need to share the same code.

![](Image00511.jpg)

In addition to testing fixed values, the construct can also be coerced to test dynamic statements by providing a boolean value to the switch statement and any expression to the case statement. Keep in mind the first matching value is used, so the following code will output "more than 100":

![](Image00512.jpg)

![](Image00513.jpg)

For possible issues with loose typing while using the switch construct, see Switch Surprises

  

# Chapter 20: Loops

Loops are a fundamental aspect of programming. They allow programmers to create code that repeats for some given number of repetitions, or iterations . The number of iterations can be explicit (6 iterations, for example), or continue until some condition is met ('until Hell freezes over').

This topic covers the different types of loops, their associated control statements, and their potential applications in PHP.

## Section 20.1: continue

![](Image00514.jpg)The continue keyword halts the current iteration of a loop but does not terminate the loop.

Just like the break statement the continue statement is situated inside the loop body. When executed, the continue statement causes execution to immediately jump to the loop conditional.

In the following example loop prints out a message based on the values in an array, but skips a specified value.

![](Image00515.jpg)

The expected output is:

![](Image00516.jpg)

The continue statement may also be used to immediately continue execution to an outer level of a loop by specifying the number of loop levels to jump. For example, consider data such as

Fruit Color Cost

Apple Red 1

Banana Yellow 7

Cherry Red 2

Grape Green 4

In order to only make pies from fruit which cost less than 5

![](Image00517.jpg)

![](Image00518.jpg)

 
| continue || 2 statement is executed, execution immediately jumps back to || $data as $fruit |
| --- | --- | --- |

When the  continuing the outer loop and skipping all other code (including the conditional in the inner loop.

## Section 20.2: break

![](Image00519.jpg)The break keyword immediately terminates the current loop.

Similar to the continue statement, a break halts execution of a loop. Unlike a continue statement, however, break causes the immediate termination of the loop and does not execute the conditional statement again.

![](Image00520.jpg)

This code will produce

![](Image00521.jpg)

but will not execute the case where $i is 0, which would result in a fatal error due to division by 0.

The break statement may also be used to break out of several levels of loops. Such behavior is very useful when executing nested loops. For example, to copy an array of strings into an output string, removing any # symbols, until the output string is exactly 160 characters

![](Image00522.jpg)

 
| break |
| --- |

The 2 command immediately terminates execution of both the inner and outer loops.

## Section 20.3: foreach

![](Image00523.jpg)The foreach statement is used to loop through arrays.

For each iteration the value of the current array element is assigned to $value variable and the array pointer is moved by one and in the next iteration next element will be processed.

The following example displays the items in the array assigned.

![](Image00524.jpg)

The expected output is:

![](Image00525.jpg)

You can also access the key / index of a value using foreach:

![](Image00526.jpg)

By default $value is a copy of the value in $list , so changes made inside the loop will not be reflected in $list afterwards.

![](Image00527.jpg)

To modify the array within the foreach loop, use the & operator to assign $value by reference. It's important to unset the variable afterwards so that reusing $value elsewhere doesn't overwrite the array.

![](Image00528.jpg)

You can also modify the array items within the foreach loop by referencing the array key of the current item.

![](Image00529.jpg)

## Section 20.4: do...while

![](Image00530.jpg)

 
| do ... while |
| --- |

![](Image00531.jpg)The  statement will execute a block of code at least once - it then will repeat the loop as long as a condition is true.

The following example will increment the value of $i at least once, and it will continue incrementing the variable $i as long as it has a value of less than 25;

![](Image00532.jpg)

The expected output is:

![](Image00533.jpg)

## Section 20.5: for

![](Image00534.jpg)The for statement is used when you know how many times you want to execute a statement or a block of statements.

The initializer is used to set the start value for the counter of the number of loop iterations. A variable may be declared here for this purpose and it is traditional to name it $i .

The following example iterates 10 times and displays numbers from 0 to 9.

![](Image00535.jpg)

The expected output is:

![](Image00536.jpg)

## Section 20.6: while

![](Image00537.jpg)The while statement will execute a block of code if and as long as a test expression is true.

If the test expression is true then the code block will be executed. After the code has executed the test expression will again be evaluated and the loop will continue until the test expression is found to be false.

The following example iterates till the sum reaches 100 before terminating.

![](Image00538.jpg)

The expected output is:

![](Image00539.jpg)

  

# Chapter 21: Functions

## Section 21.1: Variable-length argument lists

Version ≥ 5.6

PHP 5.6 introduced variable-length argument lists (a.k.a. varargs, variadic arguments), using the ... token before the argument name to indicate that the parameter is variadic, i.e. it is an array including all supplied parameters from that one onward.

![](Image00540.jpg)

Type names can be added in front of the ... :

![](Image00541.jpg)

The & reference operator can be added before the ... , but after the type name (if any). Consider this example:

![](Image00542.jpg)

Output:

![](Image00543.jpg)

On the other hand, an array (or Traversable ) of arguments can be unpacked to be passed to a function in the form of an argument list:

![](Image00544.jpg)

Output:

![](Image00545.jpg)

Compare with this snippet without using ... :

![](Image00546.jpg)

Output:

![](Image00547.jpg)

Therefore, redirect functions for variadic functions can now be easily made, for example:

![](Image00548.jpg)

Apart from arrays, Traversable s, such as Iterator (especially many of its subclasses from SPL) can also be used. For example:

![](Image00549.jpg) $iterator \= new LimitIterator ( new ArrayIterator (\[0, 1, 2, 3, 4, 5, 6\]), 2, 3); echo bin2hex ( pack ( "c\*" , ... $it )); // Output: 020304

If the iterator iterates infinitely, for example:

![](Image00550.jpg)

Different versions of PHP behave differently:

From PHP 7.0.0 up to PHP 7.1.0 (beta 1):

A segmentation fault will occur

![](Image00551.jpg) The PHP process will exit with code 139 In PHP 5.6:

A fatal error of memory exhaustion ("Allowed memory size of %d bytes exhausted") will be shown. The PHP process will exit with code 255

![](Image00552.jpg)Note: HHVM (v3.10 - v3.12) does not support unpacking Traversable s. A warning message "Only containers may be unpacked" will be shown in this attempt.

## Section 21.2: Optional Parameters

Functions can have optional parameters, for example:

![](Image00553.jpg)

![](Image00554.jpg)

## Section 21.3: Passing Arguments by Reference

Function arguments can be passed "By Reference", allowing the function to modify the variable used outside the function:

![](Image00555.jpg)

Object arguments are always passed by reference:

![](Image00556.jpg)

To avoid implicit passing an object by reference, you should clone the object.

![](Image00557.jpg) Passing by reference can also be used as an alternative way to return parameters. For example, the socket\_getpeername function: bool socket\_getpeername ( resource $socket , string & $address \[, int & $port \] )

This method actually aims to return the address and port of the peer, but since there are two values to return, it chooses to use reference parameters instead. It can be called like this:

![](Image00558.jpg)

The variables $address and $port do not need to be defined before. They will:

1.    be defined as null first,

2.    then passed to the function with the predefined null value

3.    then modified in the function

4.    end up defined as the address and port in the calling context.

## Section 21.4: Basic Function Usage

A basic function is defined and executed like this:

![](Image00559.jpg)

## Section 21.5: Function Scope

Variables inside functions is inside a local scope like this

![](Image00560.jpg)

# Chapter 22: Functional Programming

PHP's functional programming relies on functions. Functions in PHP provide organized, reusable code to perform a set of actions. Functions simplify the coding process, prevent redundant logic, and make code easier to follow. This topic describes the declaration and utilization of functions, arguments, parameters, return statements and scope in PHP.

## Section 22.1: Closures

A closure is an anonymous function that can't access outside scope.

When defining an anonymous function as such, you're creating a "namespace" for that function. It currently only has access to that namespace.

![](Image00561.jpg)

 
| use |
| --- |

It doesn't have access to any external variables. To grant this permission for this namespace to access external variables, you need to introduce it via closures ( () ).

![](Image00562.jpg)

This is heavily attributed to PHP's tight variable scoping - If a variable isn't defined within the scope, or isn't brought in with global then it does not exist.

Also note:

![](Image00563.jpg)Inheriting variables from the parent scope is not the same as using global variables. Global variables exist in the global scope, which is the same no matter what function is executing.

The parent scope of a closure is the function in which the closure was declared (not necessarily the function it was called from).

Taken from the [PHP Documentation for Anonymous Functions](http://php.net/manual/en/functions.anonymous.php)

In PHP, closures use an early-binding approach. This means that variables passed to the closure's namespace using use keyword will have the same values when the closure was defined.

To change this behavior you should pass the variable by-reference .

![](Image00564.jpg)

![](Image00565.jpg)

Default arguments are not implicitly required when defining anonymous functions with/without closures.

![](Image00566.jpg)

## Section 22.2: Assignment to variables

[Anonymous functions](http://php.net/manual/en/functions.anonymous.php) can be assigned to variables for use as parameters where a callback is expected:

![](Image00567.jpg)

These variables can also be used as standalone function calls:

![](Image00568.jpg)

## Section 22.3: Objects as a function

![](Image00569.jpg)

An object with an \_\_invoke method can be used exactly as any other function.

The \_\_invoke method will have access to all properties of the object and will be able to call any methods.

## Section 22.4: Using outside variables

The use construct is used to import variables into the anonymous function's scope:

![](Image00570.jpg)

Variables can also be imported by reference:

![](Image00571.jpg)

## Section 22.5: Anonymous function

An anonymous function is just a function that doesn't have a name.

![](Image00572.jpg)

In PHP, an anonymous function is treated like an expression and for this reason, it should be ended with a semicolon ; .

An anonymous function should be assigned to a variable.

![](Image00573.jpg)

Or it should be passed as parameter of another function.

![](Image00574.jpg)

![](Image00575.jpg)

Or even been returned from another function.

Self-executing anonymous functions:

![](Image00576.jpg)

Passing an argument into self-executing anonymous functions:

![](Image00577.jpg)

## Section 22.6: Pure functions

A pure function is a function that, given the same input, will always return the same output and are side-effect free.

![](Image00578.jpg)

Some side-effects are changing the filesystem , interacting with databases , printing to the screen .

![](Image00579.jpg)

## Section 22.7: Common functional methods in PHP

Mapping

Applying a function to all elements of an array:

![](Image00580.jpg)

Be aware that this is the only method of the list where the callback comes first.

Reducing (or folding)

Reducing an array to a single value:

![](Image00581.jpg)

Filtering

Returns only the array items for which the callback returns true :

![](Image00582.jpg)

## Section 22.8: Using built-in functions as callbacks

In functions taking callable as an argument, you can also put a string with PHP built-in function. It's common to use trim as array\_map parameter to remove leading and trailing whitespace from all strings in the array.

![](Image00583.jpg)

## Section 22.9: Scope

In PHP, an anonymous function has its own scope like any other PHP function.

In JavaScript, an anonymous function can access a variable in outside scope. But in PHP, this is not permitted.

![](Image00584.jpg)

## Section 22.10: Passing a callback function as a parameter

There are several PHP functions that accept user-defined callback functions as a parameter, such as:

 
| [call\_user\_func](https://secure.php.net/manual/en/function.call-user-func.php) || [(](https://secure.php.net/manual/en/function.call-user-func.php) [)](https://secure.php.net/manual/en/function.call-user-func.php) , || [usort](https://secure.php.net/manual/en/function.usort.php) || [(](https://secure.php.net/manual/en/function.usort.php) [)](https://secure.php.net/manual/en/function.usort.php) and || [array\_map](https://secure.php.net/manual/en/function.array-map.php) |
| --- | --- | --- | --- | --- |

[(](https://secure.php.net/manual/en/function.array-map.php) [)](https://secure.php.net/manual/en/function.array-map.php) .

Depending on where the user-defined callback function was defined there are different ways to pass them:

Procedural style:

![](Image00585.jpg)

Object Oriented style:

![](Image00586.jpg)

Object Oriented style using a static method:

![](Image00587.jpg)

# Chapter 23: Alternative Syntax for Control Structures

## Section 23.1: Alternative if/else statement

![](Image00588.jpg)

## Section 23.2: Alternative for statement

![](Image00589.jpg)

## Section 23.3: Alternative while statement

![](Image00590.jpg)

## Section 23.4: Alternative foreach statement

![](Image00591.jpg)

![](Image00592.jpg)

## Section 23.5: Alternative switch statement

![](Image00593.jpg)

# Chapter 24: String formatting

## Section 24.1: String interpolation

You can also use interpolation to interpolate ( insert ) a variable within a string. Interpolation works in double quoted strings and the heredoc syntax only.

![](Image00594.jpg)

The [complex (curly) syntax](http://php.net/manual/en/language.types.string.php#language.types.string.parsing.complex) format provides another option which requires that you wrap your variable within curly braces {} . This can be useful when embedding variables within textual content and helping to prevent possible ambiguity between textual content and variables.

![](Image00595.jpg)

The {} syntax only interpolates variables starting with a $ into a string. The {} syntax does not evaluate arbitrary PHP expressions.

![](Image00596.jpg)

However, the {} syntax does evaluate any array access, property access and function/method calls on variables, array elements or properties:

![](Image00597.jpg) // Example accessing a value from an array — multidimensional access is allowed $companions \= \[0 \=> \[ 'name' \=> 'Amy Pond' \], 1 \=> \[ 'name' \=> 'Dave Random' \]\]; echo "The best companion is: {$companions\[0\]\['name'\]} " ;

![](Image00598.jpg)

Notice that the dollar $ sign can appear after the opening curly brace { as the above examples, or, like in Perl or Shell Script, can appear before it:

![](Image00599.jpg)

## Section 24.2: Extracting/replacing substrings

Single characters can be extracted using array (square brace) syntax as well as curly brace syntax. These two syntaxes will only return a single character from the string. If more than one character is needed, a function will be required, i.e.- [substr](http://php.net/manual/en/function.substr.php)

![](Image00600.jpg)

Strings can also be changed one character at a time using the same square brace and curly brace syntax. Replacing more than one character requires a function, i.e.- [substr\_replace](http://php.net/manual/en/function.substr-replace.php)

![](Image00601.jpg)

![](Image00602.jpg) substr\_replace ( $foo , 'W' , 6, 1); // also results in $foo = 'Hello World' substr\_replace ( $foo , 'Whi' , 6, 2); // results in 'Hello Whirled'

// note that the replacement string need not be the same length as the substring replaced

  

# Chapter 25: String Parsing

## Section 25.1: Splitting a string by separators

[explode](http://php.net/explode) and [strstr](http://php.net/strstr) are simpler methods to get substrings by separators.

A string containing several parts of text that are separated by a common character can be split into parts with the [explode](http://php.net/explode) function.

$fruits \= "apple,pear,grapefruit,cherry" ;

![](Image00603.jpg) print\_r ( explode ( "," , $fruits )); // \['apple', 'pear', 'grapefruit', 'cherry'\] The method also supports a limit parameter that can be used as follow:

![](Image00604.jpg)

![](Image00605.jpg) If the limit parameter is zero, then this is treated as 1. print\_r ( explode ( ',' , $fruits ,0)); // \['apple,pear,grapefruit,cherry'\]

![](Image00606.jpg) If limit is set and positive, the returned array will contain a maximum of limit elements with the last element containing the rest of string. print\_r ( explode ( ',' , $fruits ,2)); // \['apple', 'pear,grapefruit,cherry'\]

If the limit parameter is negative, all components except the last -limit are returned.

![](Image00607.jpg) print\_r ( explode ( ',' , $fruits ,-1)); // \['apple', 'pear', 'grapefruit'\]

explode can be combined with [list](http://php.net/list) to parse a string into variables in one line:

![](Image00608.jpg)

However, make sure that the result of explode contains enough elements, or an undefined index warning would be triggered. strstr strips away or only returns the substring before the first occurrence of the given needle.

![](Image00609.jpg)

## Section 25.2: Substring

Substring returns the portion of string specified by the start and length parameters.

![](Image00610.jpg)

If there is a possibility of meeting multi-byte character strings, then it would be safer to use mb\_substr.

![](Image00611.jpg)

Another variant is the substr\_replace function, which replaces text within a portion of a string.

![](Image00612.jpg) var\_dump ( substr\_replace ( "Boo" , "0" , 1, 1)); // string(3) "B0o" var\_dump ( substr\_Replace ( "Boo" , "ts" , strlen ( "Boo" ))); // string(5) "Boots" Let's say you want to find a specific word in a string - and don't want to use Regex.

$hi \= "Hello World!" ; $bye \= "Goodbye cruel World!" ;

var\_dump ( strpos ( $hi , " " )); // int(5) var\_dump ( strpos ( $bye , " " )); // int(7)

var\_dump ( substr ( $hi , 0, strpos ( $hi , " " ))); // string(5) "Hello" var\_dump ( substr ( $bye , \-1 \* ( strlen ( $bye ) \- strpos ( $bye , " " )))); // string(13) " cruel World!"

![](Image00613.jpg) // If the casing in the text is not important, then using strtolower helps to compare strings var\_dump ( substr ( $hi , 0, strpos ( $hi , " " )) \== 'hello' ); // bool(false) var\_dump ( strtolower ( substr ( $hi , 0, strpos ( $hi , " " ))) \== 'hello' ); // bool(true)

Another option is a very basic parsing of an email.

![](Image00614.jpg)

![](Image00615.jpg) if ( $wld \== "co.uk" ) var\_dump ( " $wrong is a UK address" ); if ( $nld \== "co.uk" ) var\_dump ( " $notld is a UK address" );

Or even putting the "Continue reading" or "..." at the end of a blurb

![](Image00616.jpg)

## Section 25.3: Searching a substring with strpos

strpos can be understood as the number of bytes in the haystack before the first occurrence of the needle.

![](Image00617.jpg) var\_dump ( strpos ( "haystack" , "hay" )); // int(0) var\_dump ( strpos ( "haystack" , "stack" )); // int(3) var\_dump ( strpos ( "haystack" , "stackoverflow" ); // bool(false)

Checking if a substring exists

Be careful with checking against TRUE or FALSE because if a index of 0 is returned an if statement will see this as FALSE.

![](Image00618.jpg)

Output of the whole example:

![](Image00619.jpg)

Search starting from an offset

![](Image00620.jpg)

![](Image00621.jpg)

![](Image00622.jpg)

## Section 25.4: Parsing string using regular expressions

preg\_match can be used to parse string using regular expression. The parts of expression enclosed in parenthesis are called subpatterns and with them you can pick individual parts of the string.

![](Image00623.jpg)

Output

![](Image00624.jpg)

# Chapter 26: Classes and Objects

Classes and Objects are used to to make your code more efficient and less repetitive by grouping similar tasks.

A class is used to define the actions and data structure used to build objects. The objects are then built using this predefined structure.

## Section 26.1: Class Constants

Class constants provide a mechanism for holding fixed values in a program. That is, they provide a way of giving a name (and associated compile-time checking) to a value like 3.14 or "Apple" . Class constants can only be defined with the const keyword - the [define](http://php.net/define) function cannot be used in this context.

As an example, it may be convenient to have a shorthand representation for the value of π throughout a program. A class with const values provides a simple way to hold such values.

![](Image00625.jpg)

 
| MathValues :: PI |
| --- |

![](Image00626.jpg) Class constants may be accessed by using the double colon operator (so-called the scope resolution operator) on a class, much like static variables. Unlike static variables, however, class constants have their values fixed at compile time and cannot be reassigned to (e.g. \= 7 would produce a fatal error).

Class constants are also useful for defining things internal to a class that might need changing later (but do not change frequently enough to warrant storing in, say, a database). We can reference this internally using the self scope resolutor (which works in both instanced and static implementations)

![](Image00627.jpg)

Class constants can only contain scalar values in versions < 5.6

As of PHP 5.6 we can use expressions with constants, meaning math statements and strings with concatenation are acceptable constants

![](Image00628.jpg)

As of PHP 7.0, constants declared with define may now contain arrays.

![](Image00629.jpg)

Class constants are useful for more than just storing mathematical concepts. For example, if preparing a pie, it might be convenient to have a single Pie class capable of taking different kinds of fruit.

![](Image00630.jpg)

We can then use the Pie class like so

![](Image00631.jpg)

The problem that arises here is, when instantiating the Pie class, no guidance is provided as to the acceptable values. For example, when making a "boysenberry" pie, it might be misspelled "boisenberry". Furthermore, we might not support a plum pie. Instead, it would be useful to have a list of acceptable fruit types already defined somewhere it would make sense to look for them. Say a class named Fruit :

![](Image00632.jpg)

 
| new Pie || ( || 'aple' |
| --- | --- | --- |

 
| Pie || ( || 'apple' || ) are both acceptable to the compiler, || new Pie || ( || Fruit :: APLE |
| --- | --- | --- | --- | --- | --- | --- |

Listing the acceptable values as class constants provides a valuable hint as to the acceptable values which a method accepts. It also ensures that misspellings cannot make it past the compiler. While ) and new ) will produce a compiler error.

Finally, using class constants means that the actual value of the constant may be modified in a single place, and any code using the constant automatically has the effects of the modification.

 
| MyClass :: CONSTANT\_NAME |
| --- |

Whilst the most common method to access a class constant is , it may also be accessed by:

![](Image00633.jpg)

Class constants in PHP are conventionally named all in uppercase with underscores as word separators, although any valid label name may be used as a class constant name.

As of PHP 7.1, class constants may now be defined with different visibilities from the default public scope. This means that both protected and private constants can now be defined to prevent class constants from unnecessarily leaking into the public scope (see Method and Property Visibility ). For example:

![](Image00634.jpg)

![](Image00635.jpg)

define vs class constants

Although this is a valid construction:

![](Image00636.jpg)

If you try to do the same with class constants, you'll get an error:

![](Image00637.jpg)

But you can do:

![](Image00638.jpg)

For more information, see [constants in the manual](http://php.net/manual/en/language.constants.php) .

Using ::class to retrieve class's name

 
| :: class |
| --- |

PHP 5.5 introduced the  syntax to retrieve the full class name, taking namespace scope and use statements into account.

![](Image00639.jpg)

The above works even if the classes are not even defined (i.e. this code snippet works alone).

This syntax is useful for functions that require a class name. For example, it can be used with class\_exists to check a class exists. No errors will be generated regardless of return value in this snippet:

![](Image00640.jpg)

## Section 26.2: Abstract Classes

An abstract class is a class that cannot be instantiated. Abstract classes can define abstract methods, which are methods without any body, only a definition:

![](Image00641.jpg)

![](Image00642.jpg)

Abstract classes should be extended by a child class which can then provide the implementation of these abstract methods.

The main purpose of a class like this is to provide a kind of template that allows children classes to inherit from, "forcing" a structure to adhere to. Lets elaborate on this with an example:

In this example we will be implementing a Worker interface. First we define the interface:

![](Image00643.jpg)

 
| run |
| --- |

To ease the development of further Worker implementations, we will create an abstract worker class that already provides the () method from the interface, but specifies some abstract methods that need to be filled in by any child class:

![](Image00644.jpg)

 
| getMemoryLimit |
| --- |

First of all, we have provided an abstract method () . Any class extending from AbstractWorker needs to provide this method and return its memory limit. The AbstractWorker then sets the memory limit and logs it.

 
| prepareMain || () and || main |
| --- | --- | --- |

Secondly the AbstractWorker calls the () methods, after logging that they have been called.

Finally, all of these method calls have been grouped in a try \- catch block. So if any of the abstract methods defined by the child class throws an exception, we will catch that exception, log it and rethrow it. This prevents all child classes from having to implement this themselves.

Now lets define a child class that extends from the AbstractWorker :

![](Image00645.jpg)

As you can see, the TransactionProcessorWorker was rather easy to implement, as we only had to specify the memory limit and worry about the actual actions that it needed to perform. No error handling is needed in the TransactionProcessorWorker because that is handled in the AbsractWorker .

Important Note

![](Image00646.jpg)When inheriting from an abstract class, all methods marked abstract in the parent's class declaration must be defined by the child (or the child itself must also be marked abstract); additionally, these methods must be defined with the same (or a less restricted) visibility. For example, if the abstract method is defined as protected, the function implementation must be defined as either protected or public, but not private.

Taken from the [PHP Documentation for Class Abstraction](http://php.net/manual/en/language.oop5.abstract.php) .

If you do not define the parent abstract classes methods within the child class, you will be thrown a Fatal PHP Error like the following.

![](Image00647.jpg)Fatal error: Class X contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (X::x) in

## Section 26.3: Late static binding

 
| self :: |
| --- |

In PHP 5.3+ and above you can utilize [late static binding](http://php.net/manual/en/language.oop5.late-static-bindings.php) to control which class a static property or method is called from. It was added to overcome the problem inherent with the  scope resolutor. Take the following code

![](Image00648.jpg)

 
| whatToSay |
| --- |

You would expect that the MrEd class will override the parent () function. But when we run this we get something unexpected

![](Image00649.jpg)

 
| self :: whatToSay |
| --- |

 
| static :: |
| --- |

The problem is that (); can only refer to the Horse class, meaning it doesn't obey MrEd . If we switch to the  scope resolutor, we don't have this problem. This newer method tells the class to obey the instance calling it. Thus we get the inheritance we're expecting

![](Image00650.jpg)

## Section 26.4: Namespacing and Autoloading

Technically, autoloading works by executing a callback when a PHP class is required but not found. Such callbacks usually attempt to load these classes.

Generally, autoloading can be understood as the attempt to load PHP files (especially PHP class files, where a PHP source file is dedicated for a specific class) from appropriate paths according to the class's fully-qualified name (FQN) when a class is needed.

Suppose we have these classes:

Class file for application\\controllers\\Base :

![](Image00651.jpg)

Class file for application\\controllers\\Control :

![](Image00652.jpg)

Class file for application\\models\\Page :

![](Image00653.jpg)

Under the source folder, these classes should be placed at the paths as their FQNs respectively:

![](Image00654.jpg)

This approach makes it possible to programmatically resolve the class file path according to the FQN, using this function:

![](Image00655.jpg) function getClassPath ( string $sourceFolder , string $className , string $extension \= ".php" ) {     return $sourceFolder . "/" . str\_replace ( " \\\\ " , "/" , $className ) . $extension ; // note that "/" works as a directory separator even on Windows }

The spl\_autoload\_register function allows us to load a class when needed using a user-defined function:

![](Image00656.jpg)

This function can be further extended to use fallback methods of loading:

![](Image00657.jpg)

![](Image00658.jpg)

Note that PHP doesn't attempt to load the classes whenever a file that uses this class is loaded. It may be loaded in the middle of a script, or even in shutdown functions . This is one of the reasons why developers, especially those who use autoloading, should avoid replacing executing source files in the runtime, especially in phar files.

## Section 26.5: Method and Property Visibility

There are three visibility types that you can apply to methods ( class/object functions ) and properties ( class/object variables ) within a class, which provide access control for the method or property to which they are applied.

You can read extensively about these in the [PHP Documentation for OOP Visibility](http://php.net/manual/en/language.oop5.visibility.php) .

Public

Declaring a method or a property as public allows the method or property to be accessed by:

![](Image00659.jpg)The class that declared it.

The classes that extend the declared class.

Any external objects, classes, or code outside the class hierarchy.

An example of this public access would be:

![](Image00660.jpg)

Protected

Declaring a method or a property as protected allows the method or property to be accessed by:

![](Image00661.jpg)The class that declared it.

The classes that extend the declared class.

This does not allow external objects, classes, or code outside the class hierarchy to access these methods or properties. If something using this method/property does not have access to it, it will not be available, and an error will be thrown. Only instances of the declared self (or subclasses thereof) have access to it.

An example of this protected access would be:

![](Image00662.jpg)

![](Image00663.jpg)

The example above notes that you can only access the protected elements within it's own scope. Essentially: "What's in the house can only be access from inside the house."

Private

Declaring a method or a property as private allows the method or property to be accessed by:

![](Image00664.jpg)The class that declared it Only (not subclasses).

A private method or property is only visible and accessible within the class that created it.

Note that objects of the same type will have access to each others private and protected members even though they are not the same instances.

![](Image00665.jpg)

![](Image00666.jpg)

As noted, you can only access the private method/property from within it's defined class.

## Section 26.6: Interfaces

Introduction

Interfaces are definitions of the public APIs classes must implement to satisfy the interface. They work as "contracts", specifying what a set of subclasses does, but not how they do it.

Interface definition is much alike class definition, changing the keyword class to interface :

![](Image00667.jpg)

Interfaces can contain methods and/or constants, but no attributes. Interface constants have the same restrictions as class constants. Interface methods are implicitly abstract:

![](Image00668.jpg)

Note: interfaces must not declare constructors or destructors, since these are implementation details on the class level.

Realization

Any class that needs to implement an interface must do so using the implements keyword. To do so, the class needs to provide a implementation for every method declared in the interface, respecting the same signature.

A single class can implement more than one interface at a time.

![](Image00669.jpg)

![](Image00670.jpg)

When abstract classes implement interfaces, they do not need to implement all methods. Any method not implemented in the base class must then be implemented by the concrete class that extends it:

![](Image00671.jpg)

Notice that interface realization is an inherited characteristic. When extending a class that implements an interface, you do not need to redeclare it in the concrete class, because it is implicit.

![](Image00672.jpg)Note: Prior to PHP 5.3.9, a class could not implement two interfaces that specified a method with the same name, since it would cause ambiguity. More recent versions of PHP allow this as long as the duplicate methods have the same signature [\[1\]](http://php.net/manual/en/language.oop5.interfaces.php) .

Inheritance

Like classes, it is possible to establish an inheritance relationship between interfaces, using the same keyword extends . The main difference is that multiple inheritance is allowed for interfaces:

![](Image00673.jpg)

Examples

In the example bellow we have a simple example interface for a vehicle. Vehicles can go forwards and backwards.

![](Image00674.jpg)

Then we create two classes that implement the interface: Bike and Car. Bike and Car internally are very different, but both are vehicles, and must implement the same public methods that VehicleInterface provides.

Typehinting allows methods and functions to request Interfaces. Let's assume that we have a parking garage class, which contains vehicles of all kinds.

![](Image00675.jpg)

![](Image00676.jpg)

Because addVehicle requires a $vehicle of type VehicleInterfac e — not a concrete implementatio n— we can input both Bikes and Cars, which the ParkingGarage can manipulate and use.

## Section 26.7: Final Keyword

Def: Final Keyword prevents child classes from overriding a method by prefixing the definition with final. If the class itself is being defined final then it cannot be extended

Final Method

![](Image00677.jpg)

Final Class:

![](Image00678.jpg)

Final constants: Unlike Java, the final keyword is not used for class constants in PHP. Use the keyword const instead.

Why do I have to use final ?

1.    Preventing massive inheritance chain of doom

2.    Encouraging composition

3.    Force the developer to think about user public API

4.    Force the developer to shrink an object's public API

5.    A final class can always be made extensible

6.    extends breaks encapsulation

7.    You don't need that flexibility

8.    You are free to change the code

When to avoid final : Final classes only work effectively under following assumptions:

1.    There is an abstraction (interface) that the final class implements

2.    All of the public API of the final class is part of that interface

## Section 26.8: Autoloading

Nobody wants to require or include every time a class or inheritance is used. Because it can be painful and is easy to forget, PHP is offering so called autoloading. If you are already using Composer, read about autoloading using Composer.

What exactly is autoloading?

The name basically says it all. You do not have to get the file where the requested class is stored in, but PHP auto matically load s it.

How can I do this in basic PHP without third party code?

There is the function [\_\_autoload](https://secure.php.net/manual/function.autoload.php) , but it is considered better practice to use [spl\_autoload\_register](https://secure.php.net/manual/function.spl-autoload-register.php) . These functions will be considered by PHP every time a class is not defined within the given space. So adding autoload to an existing project is no problem, as defined classes (via require i.e.) will work like before. For the sake of preciseness, the following examples will use anonymous functions, if you use PHP < 5.3, you can define the function and pass it's name as argument to spl\_autoload\_register .

Examples

![](Image00679.jpg)

 
| FooBar || . || php |
| --- | --- | --- |

The code above simply tries to include a filename with the class name and the appended extension ".php" using [sprintf](https://secure.php.net/sprintf) . If FooBar needs to be loaded, it looks if  exists and if so includes it.

Of course this can be extended to fit the project's individual need. If \_ inside a class name is used to group, e.g.

User\_Post and User\_Image both refer to User , both classes can be kept in a folder called "User" like so:

![](Image00680.jpg)

The class User\_Post will now be loaded from "User/Post.php", etc.

spl\_autoload\_register can be tailored to various needs. All your files with classes are named

"class.CLASSNAME.php"? No problem. Various nesting ( User\_Post\_Content \=> "User/Post/Content.php")? No problem either.

If you want a more elaborate autoloading mechanism - and still don't want to include Composer - you can work without adding third party libraries.

![](Image00681.jpg)

Using autoloaders like this, you can happily write code like this:

![](Image00682.jpg)

Using classes:

![](Image00683.jpg)

 
| foo || / || bar || . || php || , || foo || . || php || , || hello || / || world || . || php || and || demo || / || classes || . || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

These examples will be include classes from .

## Section 26.9: Calling a parent constructor when instantiating a child

 
| \_\_construct |
| --- |

 
| \_\_construct || () method from it's child. If you need to do that, then you will need to use the || [parent](http://php.net/manual/en/keyword.parent.php) [::](http://php.net/manual/en/keyword.parent.php) |
| --- | --- | --- |

A common pitfall of child classes is that, if your parent and child both contain a constructor( () ) method, only the child class constructor will run . There may be occasions where you need to run the parent  scope resolutor:

![](Image00684.jpg)

Now harnessing that within a real-world situation would look something like:

![](Image00685.jpg)

 
| \_\_construct |
| --- |

The above will run the parent () resulting in the echo being run.

## Section 26.10: Dynamic Binding

Dynamic binding, also referred as method overriding is an example of run time polymorphism that occurs when multiple classes contain different implementations of the same method, but the object that the method will be called on is unknown until run time .

This is useful if a certain condition dictates which class will be used to perform an action, where the action is named the same in both classes.

![](Image00686.jpg)

![](Image00687.jpg)

 
| Dog || | || Cat |
| --- | --- | --- |

In the above example, the Animal class () which will makeNoise is unknown until run time depending on the property within the User class.

## Section 26.11: $this, self and static plus the singleton

 
| $this \-> member || for non-static members, use || self :: $member |
| --- | --- | --- |

![](Image00688.jpg)Use $this to refer to the current object. Use self to refer to the current class. In other words, use  for static members.

 
| sayHello || () and || sayGoodbye |
| --- | --- | --- |

In the example below, () are using self and $this difference can be observed here.

![](Image00689.jpg)

![](Image00690.jpg)

static refers to whatever class in the hierarchy you called the method on. It allows for better reuse of static class properties when classes are inherited.

Consider the following code:

![](Image00691.jpg)

This doesn't produce the result you want:

![](Image00692.jpg)unknown unknown unknown

 
| brand |
| --- |

That's because self refers to the Car class whenever method () is called.

To refer to the correct class, you need to use static instead:

![](Image00693.jpg)

![](Image00694.jpg)

This does produce the desired output:

![](Image00695.jpg)unknown

BMW

Mercedes

See also Late static binding

The singleton

If you have an object that's expensive to create or represents a connection to some external resource you want to reuse, i.e. a database connection where there is no connection pooling or a socket to some other system, you can use the static and self keywords in a class to make it a singleton. There are strong opinions about whether the singleton pattern should or should not be used, but it does have its uses.

![](Image00696.jpg)

As you can see in the example code we are defining a private static property $instance to hold the object reference. Since this is static this reference is shared across ALL objects of this type.

 
| getInstance |
| --- |

The () method uses a method know as lazy instantiation to delay creating the object to the last possible moment as you do not want to have unused objects lying around in memory never intended to be used. It also saves time and CPU on page load not having to load more objects than necessary. The method is checking if the object is set, creating it if not, and returning it. This ensures that only one object of this kind is ever created.

We are also setting the constructor to be private to ensure that no one creates it with the new keyword from the outside. If you need to inherit from this class just change the private keywords to protected .

To use this object you just write the following:

![](Image00697.jpg)

Now I DO implore you to use dependency injection where you can and aim for loosely coupled objects, but sometimes that is just not reasonable and the singleton pattern can be of use.

## Section 26.12: Defining a Basic Class

An object in PHP contains variables and functions. Objects typically belong to a class, which defines the variables and functions that all objects of this class will contain.

The syntax to define a class is:

![](Image00698.jpg)

Once a class is defined, you can create an instance using:

![](Image00699.jpg)

Variables and functions on the object are accessed like this:

![](Image00700.jpg)

Constructor

 
| \_\_construct |
| --- |

Classes can define a special () method, which is executed as part of object creation. This is often used to specify the initial values of an object:

![](Image00701.jpg)

Extending Another Class

Class definitions can extend existing class definitions, adding new variables and functions as well as modifying those defined in the parent class.

Here is a class that extends the previous example:

![](Image00702.jpg)

![](Image00703.jpg)

The Square class contains variables and behavior for both the Shape class and the Square class:

![](Image00704.jpg)

## Section 26.13: Anonymous Classes

Anonymous classes were introduced into PHP 7 to enable for quick one-off objects to be easily created. They can take constructor arguments, extend other classes, implement interfaces, and use traits just like normal classes can.

In its most basic form, an anonymous class looks like the following:

![](Image00705.jpg)

Nesting an anonymous class inside of another class does not give it access to private or protected methods or properties of that outer class. Access to protected methods and properties of the outer class can be gained by extending the outer class from the anonymous class. Access to private properties of the outer class can be gained by passing them through to the anonymous class's constructor.

For example:

![](Image00706.jpg)

![](Image00707.jpg)

  

# Chapter 27: Namespaces

## Section 27.1: Declaring namespaces

A namespace declaration can look as follows:

 
| namespace MyProject |
| --- |

 
| namespace MyProject\\Security\\Cryptography |
| --- |

 
| namespace MyProject || { ||   ... |
| --- | --- | --- |

![](Image00708.jpg); \- Declare the namespace MyProject

; \- Declare a nested namespace } \- Declare a namespace with enclosing brackets.

It is recommended to only declare a single namespace per file, even though you can declare as many as you like in a single file:

![](Image00709.jpg)

Every time you declare a namespace, classes you define after that will belong to that namespace:

![](Image00710.jpg)

 
| namespace MyProject\\Shapes |
| --- |

A namespace declaration can be used multiple times in different files. The example above defined three classes in the MyProject\\Shapes namespace in a single file. Preferably this would be split up into three files, each starting with ; . This is explained in more detail in the PSR-4 standard example.

## Section 27.2: Referencing a class or function in a namespace

As shown in Declaring Namespaces, we can define a class in a namespace as follows:

![](Image00711.jpg)

To reference this class the full path (including the namespace) needs to be used:

![](Image00712.jpg)

This can be shortened by importing the class via the use \-statement:

![](Image00713.jpg)

As for PHP 7.0 you can group various use \-statements in one single statement using brackets:

![](Image00714.jpg)

Sometimes two classes have the same name. This is not a problem if they are in a different namespace, but it could become a problem when attempting to import them with the use \-statement:

![](Image00715.jpg)

This can be solved by defining a name for the alias yourself using the as keyword:

![](Image00716.jpg)

To reference a class outside the current namespace, it has to be escaped with a \\ , otherwise a relative namespace path is assumed from the current namespace:

![](Image00717.jpg)

## Section 27.3: Declaring sub-namespaces

To declare a single namespace with hierarchy use following example:

![](Image00718.jpg)

![](Image00719.jpg)

The above example creates:

constant MyProject\\Sub\\Level\\CONNECT\_OK class MyProject\\Sub\\Level\\Connection and function MyProject\\Sub\\Level\\connect

## Section 27.4: What are Namespaces?

The PHP community has a lot of developers creating lots of code. This means that one librar y’ s PHP code may use the same class name as another library. When both libraries are used in the same namespace, they collide and cause trouble.

Namespaces solve this problem. As described in the PHP reference manual, namespaces may be compared to operating system directories that namespace files; two files with the same name may co-exist in separate directories. Likewise, two PHP classes with the same name may co-exist in separate PHP namespaces.

It is important for you to namespace your code so that it may be used by other developers without fear of colliding with other libraries.

  

# Chapter 28: Sessions

## Section 28.1: session\_start() Options

 
| [ph](http://php.net/manual/en/ini.list.php) [p](http://php.net/manual/en/ini.list.php) || [.](http://php.net/manual/en/ini.list.php) || [in](http://php.net/manual/en/ini.list.php) [i](http://php.net/manual/en/ini.list.php) |
| --- | --- | --- |

Starting with PHP Sessions we can pass an array with [session-based](http://php.net/manual/en/ini.list.php) [options](http://php.net/manual/en/ini.list.php) to the session\_start function.

Example

![](Image00720.jpg)

 
| php || . || ini || setting named || session || . || lazy\_write |
| --- | --- | --- | --- | --- | --- | --- |

This feature also introduces a new , which defaults to true and means that session data is only rewritten, if it changes.

Referencing: [https://wiki.php.net/rfc/session-lock-ini](https://wiki.php.net/rfc/session-lock-ini)

## Section 28.2: Session Locking

 
| session\_start |
| --- |

 
| session\_start |
| --- |

As we all are aware that PHP writes session data into a file at server side. When a request is made to php script which starts the session via () , PHP locks this session file resulting to block/wait other incoming requests for same session\_id to complete, because of which the other requests will get stuck on ()

until or unless the session file locked is not released

The session file remains locked until the script is completed or session is manually closed. To avoid this situation i.e. to prevent multiple requests getting blocked , we can start the session and close the session which will release the lock from session file and allow to continue the remaining requests.

![](Image00721.jpg)

Now one will think if session is closed how we will read the session values, beautify even after session is closed, session is still available. So, we can still read the session data.

![](Image00722.jpg)

In php >= 7.0 , we can have read\_only session, read\_write session and lazy\_write session, so it may not required

 
| session\_write\_close |
| --- |

to use ()

## Section 28.3: Manipulating session data

The $\_SESSION variable is an array, and you can retrieve or manipulate it like a normal array.

![](Image00723.jpg)

Also see Manipulating an Array for more reference how to work on an array.

Note that if you store an object in a session, it can be retrieved gracefully only if you have an class autoloader or you have loaded the class already. Otherwise, the object will come out as the type \_\_PHP\_Incomplete\_Class , which may later lead to [crashes](http://stackoverflow.com/q/1055728/3990767) . See Namespacing and Autoloading about autoloading.

Warning:

Session data can be hijacked. This is outlined in: [Pro PHP Security: From Application Security Principles to the](https://books.google.com.au/books?id=EUc6NlZRDqcC&pg=PA97#v=onepage&q&f=false)

[Implementation of XSS Defense - Chapter 7: Preventing Session Hijacking](https://books.google.com.au/books?id=EUc6NlZRDqcC&pg=PA97#v=onepage&q&f=false) So it can be strongly recommended to never store any personal information in $\_SESSION . This would most critically include credit card numbers , government issued ids , and passwords ; but would also extend into less assuming data like names , emails , phone numbers , etc which would allow a hacker to impersonate/compromise a legitimate user. As a general rule, use worthless/nonpersonal values, such as numerical identifiers, in session data.

## Section 28.4: Destroy an entire session

 
| [session\_destroy](http://php.net/session_destroy) |
| --- |

If you've got a session which you wish to destroy, you can do this with [(](http://php.net/session_destroy) [)](http://php.net/session_destroy)

![](Image00724.jpg)

![](Image00725.jpg)

 
| session\_destroy || () is different to using something like || $\_SESSION || \= ||   array |
| --- | --- | --- | --- | --- |

Using (); which will remove all of the values stored in the SESSION superglobal but it will not destroy the actual stored version of the session.

 
| $\_SESSION || \= ||   array || (); instead of || session\_unset |
| --- | --- | --- | --- | --- |

Note : We use () because [the manual](http://php.net/session_destroy) stipulates:

![](Image00726.jpg)              Only use session\_unset() for older deprecated code that does not use $\_SESSION.

## Section 28.5: Safe Session Start With no Errors

Many developers have this problem when they work on huge projects, especially if they work on some modular CMS on plugins, addons, components etc. Here is solution for safe session start where if first checked PHP version to cover all versions and on next is checked if session is started. If session not exists then I start session safe. If session exists nothing happen.

![](Image00727.jpg)

## Section 28.6: Session name

Checking if session cookies have been created

Session name is the name of the cookie used to store sessions. You can use this to detect if cookies for a session have been created for the user:

![](Image00728.jpg)

Note that this method is generally not useful unless you really don't want to create cookies unnecessarily.

Changing session name

 
| session\_name |
| --- |

You can update the session name by calling () .

![](Image00729.jpg)

 
| session\_name |
| --- |

If no argument is provided into () then the current session name is returned.

![](Image00730.jpg)It should contain only alphanumeric characters; it should be short and descriptive (i.e. for users with enabled cookie warnings). The session name can't consist of digits only, at least one letter must be present. Otherwise a new session id is generated every time.

  

# Chapter 29: Cookies

parameter detail

The name of the cookie. This is also the key you can use to retrieve the value from the $\_COOKIE super

 
| name || global. This is the only required parameter |
| --- | --- |
| value || The value to store in the cookie. This data is accessible to the browser so don't store anything sensitive here. |
| expire || A Unix timestamp representing when the cookie should expire. If set to zero the cookie will expire at the end of the session. If set to a number less than the current Unix timestamp the cookie will expire immediately. |

 
| some |
| --- |

The scope of the cookie. If set to / the cookie will be available within the entire domain. If set to /-

 
| path |
| --- |

path / then the cookie will only be available in that path and descendants of that path. Defaults to the current path of the file that the cookie is being set in.

 
| stackoverflow || . || com |
| --- | --- | --- |

 
| meta || . || stackoverflow || . || com |
| --- | --- | --- | --- | --- |

The domain or subdomain the cookie is available on. If set to the bare domain then the cookie will be available to that domain and all subdomains. If set to a subdomain domain  then the cookie will be available only on that subdomain, and all sub-

 
|   || subdomains. |
| --- | --- |
| secure || When set to TRUE the cookie will only be set if a secure HTTPS connection exists between the client and the server. |
| httponly || Specifies that the cookie should only be made available through the HTTP/S protocol and should not |

be available to client side scripting languages like JavaScript. Only available in PHP 5.2 or later.

An HTTP cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing.

## Section 29.1: Modifying a Cookie

The value of a cookie can be modified by resetting the cookie

![](Image00731.jpg)

## Section 29.2: Setting a Cookie

 
| setcookie |
| --- |

A cookie is set using the () function. Since cookies are part of the HTTP header, you must set any cookies before sending any output to the browser.

![](Image00732.jpg) Example: setcookie ( "user" , "Tom" , time () + 86400, "/" ); // check syntax for function params

Description:

![](Image00733.jpg)Creates a cookie with name user

(Optional) Value of the cookie is Tom

(Optional) Cookie will expire in 1 day (86400 seconds)

(Optional) Cookie is available throughout the whole website /

(Optional) Cookie is only sent over HTTPS

(Optional) Cookie is not accessible to scripting languages such as JavaScript

A created or modified cookie can only be accessed on subsequent requests (where path and domain matches) as the superglobal $\_COOKIE is not populated with the new data immediately.

## Section 29.3: Checking if a Cookie is Set

 
| isset |
| --- |

Use the () function upon the superglobal $\_COOKIE variable to check if a cookie is set.

Example:

![](Image00734.jpg)

## Section 29.4: Removing a Cookie

To remove a cookie, set the expiry timestamp to a time in the past. This triggers the browser's removal mechanism:

![](Image00735.jpg)

It is also a good idea to unset the $\_COOKIE value in case the current page uses it:

![](Image00736.jpg)

## Section 29.5: Retrieving a Cookie

Retrieve and Output a Cookie Named user

The value of a cookie can be retrieved using the global variable $\_COOKIE . example if we have a cookie named user we can retrieve it like this

![](Image00737.jpg)

# Chapter 30: Output Buering

Function Details

 
| ob\_start |
| --- |

ob\_start() Starts the output buffer, any output placed after this will be captured and not displayed ob\_get\_contents() Returns all content captured by () ob\_end\_clean()              Empties the output buffer and turns it off for the current nesting level

 
| ob\_get\_contents || () and || ob\_end\_clean |
| --- | --- | --- |

ob\_get\_clean() Triggers both ()

ob\_get\_level() Returns the current nesting level of the output buffer ob\_flush() Flush the content buffer and send it to the browser without ending the buffer ob\_implicit\_flush() Enables implicit flushing after every output call. ob\_end\_flush()              Flush the content buffer and send it to the browser also ending the buffer

## Section 30.1: Basic usage getting content between buers and clearing

Output buffering allows you to store any textual content (Text, HTML ) in a variable and send to the browser as one piece at the end of your script. By default, php sends your content as it interprets it.

![](Image00738.jpg)

 
| ob\_start || () and || ob\_get\_clean |
| --- | --- | --- |

Any content outputted between () will be captured and placed into the variable

$content .

 
| ob\_get\_clean || () triggers both || ob\_get\_contents || () and || ob\_end\_clean |
| --- | --- | --- | --- | --- |

Calling () .

## Section 30.2: Processing the buer via a callback

 
| ob\_start |
| --- |

You can apply any kind of additional processing to the output by passing a callable to () .

![](Image00739.jpg)

![](Image00740.jpg)

Output:

![](Image00741.jpg) <h1> LoremIpsum </h1><p><strong> Pellentesquehabitantmorbitristique </strong> senectusetnetusetmalesuada famesacturpisegestas. < ahref \= "#" \> Donecnonenim </a> inturpispulvinarfacilisis. </p><h2> HeaderLevel2 </h2> <ol><li> Loremipsumdolorsitamet,consectetueradipiscingelit. </li><li> Aliquamtinciduntmauriseurisus. </ li></ol>

## Section 30.3: Nested output buers

 
| ob\_get\_level () |
| --- |

You can nest output buffers and fetch the level for them to provide different content using the function.

![](Image00742.jpg)

![](Image00743.jpg)

Outputs:

![](Image00744.jpg)

## Section 30.4: Running output buer before any content

![](Image00745.jpg)

In this example we assume $users to be a multidimensional array, and we loop through it to find all users with an access level of 7.

If there are no results, we redirect to an error page.

 
| header |
| --- |

We are using the output buffer here because we are triggering a () redirect based on the result of the loop

## Section 30.5: Stream output to client

![](Image00746.jpg)

## Section 30.6: Using Output buer to store contents in a file, useful for reports, invoices etc

![](Image00747.jpg)

 
| echo $html ; |
| --- |

This example takes the complete document, and writes it to file, it does not output the document into the browser, but do by using

## Section 30.7: Typical usage and reasons for using ob\_start

ob\_start is especially handy when you have redirections on your page. For example, the following code won't work:

![](Image00748.jpg)

 
| headers already sent by < xxx \> on line < xxx \> |
| --- |

The error that will be given is something like: .

In order to fix this problem, you would write something like this at the start of your page:

![](Image00749.jpg)

And something like this at the end of your page:

![](Image00750.jpg)

This stores all generated content into an output buffer, and displays it in one go. Hence, if you have any redirection calls on your page, those will trigger before any data is sent, removing the possibility of a headers already sent error occurring.

## Section 30.8: Capturing the output buer to re-use later

In this example, we have an array containing some data.

We capture the output buffer in $items\_li\_html and use it twice in the page.

![](Image00751.jpg)

 
| output\_buffer || . || php || and run it via || php output\_buffer || . || php |
| --- | --- | --- | --- | --- | --- | --- |

Save the above code in a file .

You should see the 2 list items we created above with the same list items we generated in PHP using the output buffer:

![](Image00752.jpg)

![](Image00753.jpg)

  

# Chapter 31: JSON

Parameter Details json\_encode value The value being encoded. Can be any type except a resource. All string data must be UTF-8 encoded.

Bitmask consisting of JSON\_HEX\_QUOT, JSON\_HEX\_TAG, JSON\_HEX\_AMP, JSON\_HEX\_APOS,

JSON\_NUMERIC\_CHECK, JSON\_PRETTY\_PRINT, JSON\_UNESCAPED\_SLASHES, JSON\_FORCE\_OBJECT, options

JSON\_PRESERVE\_ZERO\_FRACTION, JSON\_UNESCAPED\_UNICODE, JSON\_PARTIAL\_OUTPUT\_ON\_ERROR. The behaviour of these constants is described on the [JSON constants](http://php.net/manual/en/json.constants.php) page.

depth Set the maximum depth. Must be greater than zero.

json\_decode json The json string being decoded. This function only works with UTF-8 encoded strings.

assoc Should function return associative array instead of objects.

Bitmask of JSON decode options. Currently only JSON\_BIGINT\_AS\_STRING is supported (default is to options cast large integers as floats)

[JSON](http://www.json.org/) ( [JavaScript Object Notation](https://en.wikipedia.org/wiki/JSON) ) is a platform and language independent way of serializing objects into plaintext. Because it is often used on web and so is PHP, there is a [basic extension](https://secure.php.net/manual/en/book.json.php) for working with JSON in PHP.

## Section 31.1: Decoding a JSON string

 
| [json\_decod](http://php.net/manual/en/function.json-decode.php) [e](http://php.net/manual/en/function.json-decode.php) |
| --- |

The [(](http://php.net/manual/en/function.json-decode.php) [)](http://php.net/manual/en/function.json-decode.php) function takes a JSON-encoded string as its first parameter and parses it into a PHP variable.

 
| json\_decode |
| --- |

Normally, () will return an object of [\\stdClass](http://php.net/manual/en/reserved.classes.php) if the top level item in the JSON object is a dictionary or an indexed array if the JSON object is an array. It will also return scalar values or NULL for certain scalar values, such as simple strings, "true" , "false" , and "null" . It also returns NULL on any error.

// Returns an object (The top level item in the JSON string is a JSON dictionary)

$json\_string \= '{"name": "Jeff", "age": 20, "active": true, "colors": \["red", "blue"\]}' ;

![](Image00754.jpg) $object \= json\_decode ( $json\_string ); printf ( 'Hello %s, You are %s years old.' , $object \-> name , $object \-> age ); #> Hello Jeff, You are 20 years old.

// Returns an array (The top level item in the JSON string is a JSON array)

$json\_string \= '\["Jeff", 20, true, \["red", "blue"\]\]' ;

$array \= json\_decode ( $json\_string );

printf ( 'Hello %s, You are %s years old.' , $array \[0\], $array \[1\]);

 
| [var\_dump](http://php.net/manual/en/function.var-dump.php) |
| --- |

Use [(](http://php.net/manual/en/function.var-dump.php) [)](http://php.net/manual/en/function.var-dump.php) to view the types and values of each property on the object we decoded above.

![](Image00755.jpg)

Output (note the variable types):

![](Image00756.jpg)

![](Image00757.jpg)

Note: The variable types in JSON were converted to their PHP equivalent.

 
| json\_decode |
| --- |

To return an [associative array](http://php.net/manual/en/language.types.array.php) for JSON objects instead of returning an object, pass true as the [second parameter](http://php.net/manual/en/function.json-decode.php#refsect1-function.json-decode-parameters) to () .

$json\_string \= '{"name": "Jeff", "age": 20, "active": true, "colors": \["red", "blue"\]}' ;

![](Image00758.jpg) $array \= json\_decode ( $json\_string , true ); // Note the second parameter var\_dump ( $array );

Output (note the array associative structure):

![](Image00759.jpg)

The second parameter ( $assoc ) has no effect if the variable to be returned is not an object.

 
| json\_encode |
| --- |

Note: If you use the $assoc parameter, you will lose the distinction between an empty array and an empty object. This means that running () on your decoded output again, will result in a different JSON structure.

 
| json\_decode |
| --- |

If the JSON string has a "depth" more than 512 elements ( 20 elements in versions older than 5.2.3, or 128 in version 5.2.3 ) in recursion, the function () returns NULL . In versions 5.3 or later, this limit can be controlled using the third parameter ( $depth ), as discussed below.

According to the manual:

![](Image00760.jpg)PHP implements a superset of JSON as specified in the original [»](http://www.faqs.org/rfcs/rfc4627) [RFC 4627](http://www.faqs.org/rfcs/rfc4627) \- it will also encode and decode scalar types and NULL. RFC 4627 only supports these values when they are nested inside an array or an object. Although this superset is consistent with the expanded definition of "JSON text" in the newer [»](http://www.faqs.org/rfcs/rfc7159) [RFC 7159](http://www.faqs.org/rfcs/rfc7159) (which aims to supersede RFC 4627) and [»](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) , this may cause interoperability issues with older JSON parsers that adhere strictly to RFC 4627 when encoding a single scalar value.

This means, that, for example, a simple string will be considered to be a valid JSON object in PHP:

![](Image00761.jpg)

Output:

![](Image00762.jpg)

But simple strings, not in an array or object, are not part of the [RFC 4627](http://www.faqs.org/rfcs/rfc4627) standard. As a result, such online checkers as [JSLint](http://www.jslint.com/) , [JSON Formatter & Validator](https://jsonformatter.curiousconcept.com/) (in RFC 4627 mode) will give you an error.

There is a third $depth parameter for the depth of recursion (the default value is 512 ), which means the amount of nested objects inside the original object to be decoded.

There is a fourth $options parameter. It currently accepts only one value, JSON\_BIGINT\_AS\_STRING . The default behavior (which leaves off this option) is to cast large integers to floats instead of strings.

![](Image00763.jpg)              Invalid non-lowercased variants of the true, false and null literals are no longer accepted as valid input.

So this example:

![](Image00764.jpg) var\_dump ( json\_decode ( 'tRue' ), json\_last\_error\_msg ()); var\_dump ( json\_decode ( 'tRUe' ), json\_last\_error\_msg ()); var\_dump ( json\_decode ( 'tRUE' ), json\_last\_error\_msg ()); var\_dump ( json\_decode ( 'TRUe' ), json\_last\_error\_msg ()); var\_dump ( json\_decode ( 'TRUE' ), json\_last\_error\_msg ()); var\_dump ( json\_decode ( 'true' ), json\_last\_error\_msg ()); Before PHP 5.6:

![](Image00765.jpg)

And after:

![](Image00766.jpg)

Similar behavior occurs for false and null .

 
| json\_decode |
| --- |

Note that () will return NULL if the string cannot be converted.

![](Image00767.jpg)

![](Image00768.jpg)

 
| json\_decode |
| --- |

It is not safe to rely only on the return value being NULL to detect errors. For example, if the JSON string contains nothing but "null" , () will return null , even though no error occurred.

## Section 31.2: Encoding a JSON string

The [json\_encode](http://php.net/manual/en/function.json-encode.php) function will convert a PHP array (or, since PHP 5.4, an object which implements the

JsonSerializable interface) to a JSON-encoded string. It returns a JSON-encoded string on success or FALSE on failure.

![](Image00769.jpg)

During encoding, the PHP data types string, integer, and boolean are converted to their JSON equivalent. Associative arrays are encoded as JSON objects, and – when called with default arguments – indexed arrays are encoded as JSON arrays. (Unless the array keys are not a continuous numeric sequence starting from 0, in which case the array will be encoded as a JSON object.)

![](Image00770.jpg)

Output:

![](Image00771.jpg) { "name" : "Jeff" , "age" : 20 , "active" : true , "colors" :\[ "red" , "blue" \], "values" :{ "0" : "foo" , "3" : "bar" }}

Arguments

Since PHP 5.3, the second argument to json\_encode is a bitmask which can be one or more of the following.

As with any bitmask, they can be combined with the binary OR operator | .

PHP 5.x Version ≥ 5.3 [JSON\_FORCE\_OBJECT](http://php.net/manual/en/json.constants.php#constant.json-force-object)

Forces the creation of an object instead of an array

![](Image00772.jpg)

Output:

![](Image00773.jpg)

[JSON\_HEX\_TAG](http://php.net/manual/en/json.constants.php#constant.json-hex-tag) , [JSON\_HEX\_AMP](http://php.net/manual/en/json.constants.php#constant.json-hex-amp) , [JSON\_HEX\_APOS](http://php.net/manual/en/json.constants.php#constant.json-hex-apos) , [JSON\_HEX\_QUOT](http://php.net/manual/en/json.constants.php#constant.json-hex-quot)

Ensures the following conversions during encoding:

Constant Input Output

 
| JSON\_HEX\_TAG < || \\u003C |
| --- | --- |
| JSON\_HEX\_TAG \> || \\u003E |
| JSON\_HEX\_AMP & || \\u0026 |
| JSON\_HEX\_APOS' || \\u0027 |
| JSON\_HEX\_QUOT " || \\u0022 |

![](Image00774.jpg) $array \= \[ "tag" \=> "<>" , "amp" \=> "&" , "apos" \=> "'" , "quot" \=> " \\" " \]; echo json\_encode ( $array );

echo json\_encode ( $array , JSON\_HEX\_TAG | JSON\_HEX\_AMP | JSON\_HEX\_APOS | JSON\_HEX\_QUOT ); Output:

{ "tag" : "<>" , "amp" : "&" , "apos" : "'" , "quot" : " \\" " }

![](Image00775.jpg) { "tag" : "\\u003C\\u003E" , "amp" : "\\u0026" , "apos" : "\\u0027" , "quot" : "\\u0022" }

PHP 5.x Version ≥ 5.3 [JSON\_NUMERIC\_CHECK](http://php.net/manual/en/json.constants.php#constant.json-numeric-check)

Ensures numeric strings are converted to integers.

![](Image00776.jpg)

Output:

![](Image00777.jpg)\[ "23452" ,23452\]    

\[23452,23452\]

PHP 5.x Version ≥ 5.4 [JSON\_PRETTY\_PRINT](http://php.net/manual/en/json.constants.php#constant.json-pretty-print)

Makes the JSON easily readable

![](Image00778.jpg)

Output:

![](Image00779.jpg)

Includes unescaped / forward slashes in the output

![](Image00780.jpg)

Output:

![](Image00781.jpg) { "filename" : "example.txt" , "path" : "\\/full\\/path\\/to\\/file" }

{ "filename" : "example.txt" , "path" : "/full/path/to/file" }

[JSON\_UNESCAPED\_UNICODE](http://php.net/manual/en/json.constants.php#constant.json-unescaped-unicode)

Includes UTF8-encoded characters in the output instead of \\u \-encoded strings

![](Image00782.jpg)

Output:

![](Image00783.jpg)

PHP 5.x Version ≥ 5.5

[JSON\_PARTIAL\_OUTPUT\_ON\_ERROR](http://php.net/manual/en/json.constants.php#constant.json-partial-output-on-error)

Allows encoding to continue if some unencodable values are encountered.

![](Image00784.jpg)

Output:

![](Image00785.jpg){ "file" : null , "name" : "foo.txt" }

PHP 5.x Version ≥ 5.6

[JSON\_PRESERVE\_ZERO\_FRACTION](http://php.net/manual/en/json.constants.php#constant.json-preserve-zero-fraction)

Ensures that floats are always encoded as floats.

![](Image00786.jpg)

Output:

![](Image00787.jpg)

PHP 7.x Version ≥ 7.1

[JSON\_UNESCAPED\_LINE\_TERMINATORS](http://php.net/manual/en/json.constants.php#constant.json-unescaped-line-terminators)

When used with JSON\_UNESCAPED\_UNICODE , reverts to the behaviour of older PHP versions, and does not escape the characters U+2028 LINE SEPARATOR and U+2029 PARAGRAPH SEPARATOR. Although valid in JSON, these characters are not valid in JavaScript, so the default behaviour of JSON\_UNESCAPED\_UNICODE was changed in version 7.1.

![](Image00788.jpg) $array \= \[ "line" \=> " \\xe2\\x80\\xa8 " , "paragraph" \=> " \\xe2\\x80\\xa9 " \]; echo json\_encode ( $array , JSON\_UNESCAPED\_UNICODE );

echo json\_encode ( $array , JSON\_UNESCAPED\_UNICODE | JSON\_UNESCAPED\_LINE\_TERMINATORS ); Output:

![](Image00789.jpg)

![](Image00790.jpg)

## Section 31.3: Debugging JSON errors

When json\_encode or json\_decode fails to parse the string provided, it will return false . PHP itself will not raise any errors or warnings when this happens, the onus is on the user to use the [json\_last\_error()](http://php.net/manual/en/function.json-last-error.php) and [json\_last\_error\_msg()](http://php.net/manual/en/function.json-last-error-msg.php) functions to check if an error occurred and act accordingly in your application (debug it, show an error message, etc.).

The following example shows a common error when working with JSON, a failure to decode/encode a JSON string (due to the passing of a bad UTF-8 encoded string, for example) .

![](Image00791.jpg)

[json\_last\_error\_msg](http://php.net/manual/en/function.json-last-error-msg.php)

 
| [json\_last\_error\_ms](http://php.net/manual/en/function.json-last-error-msg.php) [g](http://php.net/manual/en/function.json-last-error-msg.php) |
| --- |

[(](http://php.net/manual/en/function.json-last-error-msg.php) [)](http://php.net/manual/en/function.json-last-error-msg.php) returns a human readable message of the last error that occurred when trying to

encode/decode a string.

![](Image00792.jpg)This function will always return a string , even if no error occurred.

The default non-error string is No Error

It will return false if some other (unknown) error occurred

Careful when using this in loops, as [json\_last\_error\_msg](http://php.net/manual/en/function.json-last-error-msg.php) will be overridden on each iteration.

You should only use this function to get the message for display, not to test against in control statements.

![](Image00793.jpg)

This function doesn't exist before PHP 5.5. Here is a polyfill implementation:

![](Image00794.jpg) if (! function\_exists ( 'json\_last\_error\_msg' )) {     function json\_last\_error\_msg () {         static $ERRORS \= array (             JSON\_ERROR\_NONE \=> 'No error' ,

            JSON\_ERROR\_DEPTH \=> 'Maximum stack depth exceeded' ,

            JSON\_ERROR\_STATE\_MISMATCH \=> 'State mismatch (invalid or malformed JSON)' ,

            JSON\_ERROR\_CTRL\_CHAR \=> 'Control character error, possibly incorrectly encoded' ,

            JSON\_ERROR\_SYNTAX \=> 'Syntax error' ,

            JSON\_ERROR\_UTF8 \=> 'Malformed UTF-8 characters, possibly incorrectly encoded'         );

        $error \= json\_last\_error ();

![](Image00795.jpg)

[json\_last\_error](http://php.net/manual/en/function.json-last-error.php)

 
| [json\_last\_error](http://php.net/manual/en/function.json-last-error.php) |
| --- |

[(](http://php.net/manual/en/function.json-last-error.php) [)](http://php.net/manual/en/function.json-last-error.php) returns an integer mapped to one of the pre-defined constants provided by PHP.

 
| Constant || Meaning |
| --- | --- |
| JSON\_ERROR\_NONE || No error has occurred |
| JSON\_ERROR\_DEPTH || The maximum stack depth has been exceeded |
| JSON\_ERROR\_STATE\_MISMATCH || Invalid or malformed JSON |
| JSON\_ERROR\_CTRL\_CHAR || Control character error, possibly incorrectly encoded |
| JSON\_ERROR\_SYNTAX || Syntax error (since PHP 5.3.3) |
| JSON\_ERROR\_UTF8 || Malformed UTF-8 characters, possibly incorrectly encoded (since PHP 5.5.0) |
| JSON\_ERROR\_RECURSION || One or more recursive references in the value to be encoded |
| JSON\_ERROR\_INF\_OR\_NAN || One or more NAN or INF values in the value to be encoded |

JSON\_ERROR\_UNSUPPORTED\_TYPE A value of a type that cannot be encoded was given

## Section 31.4: Using JsonSerializable in an Object

PHP 5.x Version ≥ 5.4

When you build REST API's, you may need to reduce the information of an object to be passed to the client application. For this purpose, this example illustrates how to use the JsonSerialiazble interface.

In this example, the class User actually extends a DB model object of a hypotetical ORM.

![](Image00796.jpg)

 
| jsonSerialize |
| --- |

Add JsonSerializable implementation to the class, by providing the () method.

![](Image00797.jpg)

 
| json\_encode |
| --- |

 
| jsonSerialize |
| --- |

Now in your application controller or script, when passing the object User to () you will get the return json encoded array of the () method instead of the entire object.

![](Image00798.jpg)

Will return:

![](Image00799.jpg)

properties values example.

This will both reduce the amount of data returned from a RESTful endpoint, and allow to exclude object properties from a json representation.

 
| json\_encode |
| --- |

Using Private and Protected Properties with ()

 
| json\_encode |
| --- |

To avoid using JsonSerializable, it is also possible to use private or protected properties to hide class information from () output. The Class then does not need to implement \\JsonSerializable.

![](Image00800.jpg)

![](Image00801.jpg)

## Section 31.5: Header json and the returned response

By adding a header with content type as JSON:

![](Image00802.jpg)

![](Image00803.jpg)

The header is there so your app can detect what data was returned and how it should handle it. Note that: the content header is just information about type of returned data.

If you are using UTF-8, you can use:

![](Image00804.jpg)

Example jQuery:

![](Image00805.jpg)

  

# Chapter 32: SOAP Client

Parameter Details

$wsdl URI of WSDL or NULL if using non-WSDL mode

Array of options for SoapClient. Non-WSDL mode requires location and uri to set, all other options

$options

are optional. See table below for possible values.

## Section 32.1: WSDL Mode

First, create a new SoapClient object, passing the URL to the WSDL file and optionally, an array of options.

![](Image00806.jpg)

![](Image00807.jpg)

## Section 32.2: Non-WSDL Mode

This is similar to WSDL mode, except we pass NULL as the WSDL file and make sure to set the location and uri options.

![](Image00808.jpg)

## Section 32.3: Classmaps

When creating a SOAP Client in PHP, you can also set a classmap key in the configuration array. This classmap defines which types defined in the WSDL should be mapped to actual classes, instead of the default StdClass . The reason you would want to do this is because you can get auto-completion of fields and method calls on these classes, instead of having to guess which fields are set on the regular StdClass .

![](Image00809.jpg)

![](Image00810.jpg)

After configuring the classmap, whenever you perform a certain operation that returns a type Address or Book , the SoapClient will instantiate that class, fill the fields with the data and return it from the operation call.

![](Image00811.jpg)

## Section 32.4: Tracing SOAP request and response

Sometimes we want to look at what is sent and received in the SOAP request. The following methods will return the XML in the request and response:

![](Image00812.jpg)

For example, suppose we have an ENVIRONMENT constant and when this constant's value is set to DEVELOPMENT we want to echo all information when the call to getAddress throws an error. One solution could be:

![](Image00813.jpg)

![](Image00814.jpg)

  

# Chapter 33: Using cURL in PHP

Parameter Details

curl\_init \-- Initialize a cURL session url The url to be used in the cURL request curl\_setopt \-- Set an option for a cURL transfer

 
| ch || The cURL handle (return value from curl\_init() ) |
| --- | --- |
| option || CURLOPT\_XXX to be set - see [PHP documentation](http://php.net/manual/en/function.curl-setopt.php) for the list of options and acceptable values |
| value || The value to be set on the cURL handle for the given option |
| curl\_exec || \-- Perform a cURL session |
| ch || The cURL handle (return value from curl\_init() ) |
| curl\_close || \-- Close a cURL session |
| ch || The cURL handle (return value from curl\_init() ) |

## Section 33.1: Basic Usage (GET Requests)

cURL is a tool for transferring data with URL syntax. It support HTTP, FTP, SCP and many others(curl >= 7.19.4). Remember, you need to [install and enable the cURL extension](http://php.net/manual/en/curl.installation.php) to use it.

![](Image00815.jpg)

## Section 33.2: POST Requests

If you want to mimic HTML form POST action, you can use cURL.

![](Image00816.jpg)

![](Image00817.jpg)

## Section 33.3: Using Cookies

cURL can keep cookies received in responses for use with subsequent requests. For simple session cookie handling in memory, this is achieved with a single line of code:

![](Image00818.jpg)

In cases where you are required to keep cookies after the cURL handle is destroyed, you can specify the file to store them in:

![](Image00819.jpg)

Then, when you want to use them again, pass them as the cookie file:

![](Image00820.jpg)

Remember, though, that these two steps are not necessary unless you need to carry cookies between different cURL handles. For most use cases, setting CURLOPT\_COOKIEFILE to the empty string is all you need.

Cookie handling can be used, for example, to retrieve resources from a web site that requires a login. This is typically a two-step procedure. First, POST to the login page.

![](Image00821.jpg)

The second step (after standard error checking is done) is usually a simple GET request. The important thing is to reuse the existing cURL handle for the second request. This ensures the cookies from the first response will be automatically included in the second request.

![](Image00822.jpg)

This is only intended as an example of cookie handling. In real life, things are usually more complicated. Often you must perform an initial GET of the login page to pull a login token that needs to be included in your POST. Other sites might block the cURL client based on its User-Agent string, requiring you to change it.

## Section 33.4: Using multi\_curl to make multiple POST requests

Sometimes we need to make a lot of POST requests to one or many different endpoints. To deal with this scenario, we can use multi\_curl .

First of all, we create how many requests as needed exactly in the same way of the simple example and put them in an array.

We use the curl\_multi\_init and add each handle to it.

In this example, we are using 2 different endpoints:

![](Image00823.jpg)

![](Image00824.jpg)

Then, we use curl\_multi\_exec to send the requests

![](Image00825.jpg)

A possible return for this example could be:

![](Image00826.jpg)The request to ' [http://www.example.com](http://www.example.com/) ' returned 'fruits' in 2 seconds.

The request to ' [http://www.example2.com](http://www.example2.com/) ' returned 'seafood' in 5 seconds.

## Section 33.5: Sending multi-dimensional data and multiple files with CurlFile in one request

Let's say we have a form like the one below. We want to send the data to our webserver via AJAX and from there to a script running on an external server.

![](Image00827.jpg)

So we have normal inputs, a multi-select field and a file dropzone where we can upload multiple files.

Assuming the AJAX POST request was successful we get the following data on PHP site:

![](Image00828.jpg)

and the files should look like this

![](Image00829.jpg)

![](Image00830.jpg)

So far, so good. Now we want to send this data and files to the external server using cURL with the CurlFile Class

Since cURL only accepts a simple but not a multi-dimensional array, we have to flatten the $\_POST array first.

To do this, you could use [this function for example](http://codereview.stackexchange.com/a/14685) which gives you the following:

![](Image00831.jpg)

The next step is to create CurlFile Objects for the uploaded files. This is done by the following loop:

![](Image00832.jpg)

curl\_file\_create is a helper function of the CurlFile Class and creates the CurlFile objects. We save each object in the $files array with keys named "upload\[0\]" and "upload\[1\]" for our two files.

We now have to combine the flattened post array and the files array and save it as $data like this:

![](Image00833.jpg)

The last step is to send the cURL request:

![](Image00834.jpg)

Since $data is now a simple (flat) array, cURL automatically sends this POST request with Content Type: multipart/form-data

In upload.php on the external server you can now get the post data and files with $\_POST and $\_FILES as you would normally do.

## Section 33.6: Creating and sending a request with a custom method

By default, PHP Curl supports GET and POST requests. It is possible to also send custom requests, such as DELETE , PUT or PATCH (or even non-standard methods) using the CURLOPT\_CUSTOMREQUEST parameter.

![](Image00835.jpg)

## Section 33.7: Get and Set custom http headers in php

Sending The Request Header

![](Image00836.jpg)

Reading the custom header

![](Image00837.jpg)

Output:

![](Image00838.jpg)

We can also send the header using below syntax:

![](Image00839.jpg)

  

# Chapter 34: Reflection

## Section 34.1: Feature detection of classes or objects

Feature detection of classes can partly be done with the property\_exists and method\_exists functions.

![](Image00840.jpg)

$r \= new ReflectionClass ( 'MyClass' );

$check \= $r \-> hasProperty ( 'public\_field' );   // true

![](Image00841.jpg) $check \= $r \-> hasMethod ( 'public\_function' ); // true $check \= $r \-> hasConstant ( 'CONSTANT' );       // true

// also works for protected, private and/or static members.

Note: for property\_exists and method\_exists , also an object of the class of interest can be provided instead of the class name. Using reflection, the ReflectionObject class should be used instead of ReflectionClass .

## Section 34.2: Testing private/protected methods

Sometimes it's useful to test private & protected methods as well as public ones.

![](Image00842.jpg)

![](Image00843.jpg)

Easiest way to test drive method is using reflection

![](Image00844.jpg)

If the method is static you pass null in the place of the class instance

![](Image00845.jpg)

![](Image00846.jpg)

## Section 34.3: Accessing private and protected member variables

Reflection is often used as part of software testing, such as for the runtime creation/instantiation of mock objects. It's also great for inspecting the state of an object at any given point in time. Here's an example of using Reflection in a unit test to verify a protected class member contains the expected value.

Below is a very basic class for a Car. It has a protected member variable that will contain the value representing the color of the car. Because the member variable is protected we cannot access it directly and must use a getter and setter method to retrieve and set its value respectively.

![](Image00847.jpg)

 
| Car :: setColor |
| --- |

 
| Car :: getColor |
| --- |

To test this many developers will create a Car object, set the car's color using () , retrieve the color using () , and compare that value to the color they set:

![](Image00848.jpg)

 
| Car :: getColor |
| --- |

 
| Car :: $color |
| --- |

On the surface this seems okay. After all, all () does is return the value of the protected member variable . But this test is flawed in two ways:

 
| Car :: getColor |
| --- |

1.    It exercises () which is out of the scope of this test

 
| Car :: getColor |
| --- |

2.    It depends on () which may have a bug itself which can make the test have a false positive or negative

 
| Car :: getColor |
| --- |

 
| Car :: getColor |
| --- |

Let's look at why we shouldn't use () in our unit test and should use Reflection instead. Let's say a developer is assigned a task to add "Metallic" to every car color. So they attempt to modify the () to prepend "Metallic" to the car's color:

![](Image00849.jpg)

 
| Car :: getColor |
| --- |

 
| Car :: setColor |
| --- |

 
| Car :: setColor |
| --- |

Do you see the error? The developer used a semi-colon instead of the concatenation operator in an attempt to prepend "Metallic" to the car's color. As a result, whenever () is called, "Metallic " will be returned regardless of what the car's actual color is. As a result our () unit test will fail even though () works perfectly fine and was not affected by this change .

 
| Car :: $color || contains the value we are setting via || Car :: setColor |
| --- | --- | --- |

So how do we verify () ? We can use Refelection to

inspect the protected member variable directly. So how do we do that ? We can use Refelection to make the protected member variable accessible to our code so it can retrieve the value.

Let's see the code first and then break it down:

![](Image00850.jpg)

 
| Car :: $color |
| --- |

Here is how we are using Reflection to get the value of  in the code above:

1.    We create a new [ReflectionObject](http://php.net/manual/en/class.reflectionobject.php) representing our Car object

 
| Car :: $color || (this "represents" the || Car :: $color |
| --- | --- | --- |

2.    We get a [ReflectionProperty](http://php.net/manual/en/class.reflectionproperty.php) for  variable)

 
| Car :: $color |
| --- |

3.    We make  accessible

 
| Car :: $color |
| --- |

4.    We get the value of

 
| Car :: $color || without having to call || Car :: getColor |
| --- | --- | --- |

As you can see by using Reflection we could get the value of () or

 
| Car :: setColor |
| --- |

any other accessor function which could cause invalid test results. Now our unit test for () is safe and accurate.

# Chapter 35: Dependency Injection

Dependency Injection (DI) is a fancy term for "passing things in" . All it really means is passing the dependencies of an object via the constructor and / or setters instead of creating them upon object creation inside the object. Dependency Injection might also refer to Dependency Injection Containers which automate the construction and injection.

## Section 35.1: Constructor Injection

Objects will often depend on other objects. Instead of creating the dependency in the constructor, the dependency should be passed into the constructor as a parameter. This ensures there is not tight coupling between the objects, and enables changing the dependency upon class instantiation. This has a number of benefits, including making code easier to read by making the dependencies explicit, as well as making testing simpler since the dependencies can be switched out and mocked more easily.

In the following example, Component will depend on an instance of Logger , but it doesn't create one. It requires one to be passed as argument to the constructor instead.

![](Image00851.jpg)

Without dependency injection, the code would probably look similar to:

![](Image00852.jpg)

Using new to create new objects in the constructor indicates that dependency injection was not used (or was used incompletely), and that the code is tightly coupled. It is also a sign that the code is incompletely tested or may have brittle tests that make incorrect assumptions about program state.

In the above example, where we are using dependency injection instead, we could easily change to a different Logger if doing so became necessary. For example, we might use a Logger implementation that logs to a different location, or that uses a different logging format, or that logs to the database instead of to a file.

## Section 35.2: Setter Injection

Dependencies can also be injected by setters.

![](Image00853.jpg)

![](Image00854.jpg)

This is especially interesting when the core functionality of the class does not rely on the dependency to work.

Here, the only needed dependency is the DatabaseConnection so it's in the constructor. The Logger dependency is optional and thus does not need to be part of the constructor, making the class easier to use.

Note that when using setter injection, it's better to extend the functionality rather than replacing it. When setting a dependency, there's nothing confirming that the dependency won't change at some point, which could lead in unexpected results. For example, a FileLogger could be set at first, and then a MailLogger could be set. This breaks encapsulation and makes logs hard to find, because we're replacing the dependency.

To prevent this, we should add a dependency with setter injection, like so:

![](Image00855.jpg)

![](Image00856.jpg)

Like this, whenever we'll use the core functionality, it won't break even if there is no logger dependency added, and any logger added will be used even though another logger could've been added. We're extending functionality instead of replacing it.

## Section 35.3: Container Injection

Dependency Injection (DI) in the context of using a Dependency Injection Container (DIC) can be seen as a superset of constructor injection. A DIC will typically analyze a class constructor's typehints and resolve its needs, effectively injecting the dependencies needed for the instance execution.

The exact implementation goes well beyond the scope of this document but at its very heart, a DIC relies on using the signature of a class...

![](Image00857.jpg)

... to automatically instantiate it, relying most of the time on an autoloading system.

![](Image00858.jpg)

If you are using PHP in version at least 5.5 and want to get a name of a class in a way that's being shown above, the correct way is the second approach. That way you can quickly find usages of the class using modern IDEs, which will greatly help you with potential refactoring. You do not want to rely on regular strings.

In this case, the Documentation\\Example knows it needs a Meaning , and a DIC would in turn instantiate a Meaning type. The concrete implementation need not depend on the consuming instance.

Instead, we set rules in the container, prior to object creation, that instructs how specific types should be instantiated if need be.

This has a number of advantages, as a DIC can

![](Image00859.jpg)Share common instances

Provide a factory to resolve a type signature

Resolve an interface signature

If we define rules about how specific type needs to be managed we can achieve fine control over which types are shared, instantiated, or created from a factory.

# Chapter 36: XML

## Section 36.1: Create a XML using DomDocument

To create a XML using DOMDocument,basically, we need to create all the tags and attributes using the

 
| createElement () || and || createAttribute () || methods and them create the XML structure with the || appendChild () |
| --- | --- | --- | --- | --- |

.

The example below includes tags, attributes, a CDATA section and a different namespace for the second tag:

![](Image00860.jpg)

This will output the following XML:

![](Image00861.jpg)

## Section 36.2: Read a XML document with DOMDocument

Similarly to the SimpleXML, you can use DOMDocument to parse XML from a string or from a XML file

1. From a string

![](Image00862.jpg)

2. From a file

![](Image00863.jpg)

Example of parsing

Considering the following XML:

![](Image00864.jpg)

This is a example code to parse it

$books \= $doc \-> getElementsByTagName ( 'book' ); foreach ( $books as $book ) {

    $title \= $book \-> getElementsByTagName ( 'name' )-> item (0)-> nodeValue ;

![](Image00865.jpg)     $price \= $book \-> getElementsByTagName ( 'price' )-> item (0)-> nodeValue ;     $id \= $book \-> getElementsByTagName ( 'id' )-> item (0)-> nodeValue ;     print\_r ( "The title of the book $id is $title and it costs $price ." . " \\n " ); }

This will output:

![](Image00866.jpg)The title of the book 1 is PHP - An Introduction and it costs $5.95.

The title of the book 2 is PHP - Advanced and it costs $25.00.

## Section 36.3: Leveraging XML with PHP's SimpleXML Library

SimpleXML is a powerful library which converts XML strings to an easy to use PHP object.

The following assumes an XML structure as below.

![](Image00867.jpg)

Read our data in to SimpleXML

To get started, we need to read our data into SimpleXML. We can do this in 3 different ways. Firstly, we can [load our](http://php.net/manual/en/function.simplexml-import-dom.php) [data from a DOM node.](http://php.net/manual/en/function.simplexml-import-dom.php)

![](Image00868.jpg)

Our next option is to [load our data from an XML file.](http://php.net/manual/en/function.simplexml-load-file.php)

![](Image00869.jpg)

Lastly, we can [load our data from a variable.](http://php.net/manual/en/function.simplexml-load-string.php)

![](Image00870.jpg)

Whether you've picked to load from [a DOM Element](http://php.net/manual/en/function.simplexml-import-dom.php) , from [a file](http://php.net/manual/en/function.simplexml-load-file.php) or from [a string](http://php.net/manual/en/function.simplexml-load-string.php) , you are now left with a SimpleXMLElement variable called $xmlElement . Now, we can start to make use of our XML in PHP.

Accessing our SimpleXML Data

The simplest way to access data in our SimpleXMLElement object is to [call the properties directly](http://php.net/manual/en/simplexml.examples-basic.php#example-6325) . If we want to access our first bookName, StackOverflow SimpleXML Example , then we can access it as per below.

![](Image00871.jpg)

At this point, SimpleXML will assume that because we have not told it explicitly which book we want, that we want the first one. However, if we decide that we do not want the first one, rather that we want Another SimpleXML Example , then we can access it as per below.

![](Image00872.jpg)

It is worth noting that using \[0\] works the same as not using it, so

![](Image00873.jpg)

works the same as

![](Image00874.jpg)

Looping through our XML

There are many reasons you may wish to [loop through XML](http://php.net/manual/en/simplexml.examples-basic.php#example-6327) , such as that you have a number of items, books in our case, that we would like to display on a webpage. For this, we can use a [foreach loop](http://php.net/manual/en/control-structures.foreach.php) or a standard [for loop](http://php.net/manual/en/control-structures.for.php) , taking advantage of [SimpleXMLElement's count function.](http://php.net/manual/en/simplexmlelement.count.php) .

![](Image00875.jpg)

or

![](Image00876.jpg)

Handling Errors

Now we have come so far, it is important to realise that we are only humans, and will likely encounter an error eventually - especially if we are playing with different XML files all the time. And so, we will want to handle those errors.

Consider we created an XML file. You will notice that while this XML is much alike what we had earlier, the problem with this XML file is that the final closing tag is /doc instead of /document.

![](Image00877.jpg)

![](Image00878.jpg)

Now, say, we load this into our PHP as $file.

![](Image00879.jpg)

We will be greeted with the following

![](Image00880.jpg)

However as soon as we fix this problem, we are presented with "Happy Days".

## Section 36.4: Create an XML file using XMLWriter

Instantiate a XMLWriter object:

![](Image00881.jpg)

 
| var || / || www || / || example || . || com || / || xml || / || output || . || xml |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Next open the file to which you want to write. For example, to write to / , use:

![](Image00882.jpg)

To start the document (create the XML open tag):

![](Image00883.jpg)

This will output:

![](Image00884.jpg)

Now you can start writing elements:

![](Image00885.jpg)

This will generate the XML:

![](Image00886.jpg)

If you need something a little more complex than simply nodes with plain values, you can also "start" an element and add attributes to it before closing it:

![](Image00887.jpg)

This will output:

![](Image00888.jpg)

## Section 36.5: Read a XML document with SimpleXML

You can parse XML from a string or from a XML file

1. From a string

![](Image00889.jpg)

2. From a file

![](Image00890.jpg)

Example of parsing

Considering the following XML:

![](Image00891.jpg)

This is a example code to parse it

![](Image00892.jpg)

This will output:

![](Image00893.jpg)The title of the book 1 is PHP - An Introduction and it costs $5.95. The title of the book 2 is PHP - Advanced and it costs $25.00.

  

# Chapter 37: SimpleXML

## Section 37.1: Loading XML data into simplexml

Loading from string

Use simplexml\_load\_string to create a SimpleXMLElement from a string:

$xmlString \= "<?xml version='1.0' encoding='UTF-8'?>" ;

![](Image00894.jpg) $xml \= simplexml\_load\_string ( $xmlString ) or die ( "Error: Cannot create object" );

Note that or not || must be used here because the precedence of or is higher than \= . The code after or will only be executed if $xml finally resolves to false.

Loading from file

Use simplexml\_load\_file to load XML data from a file or a URL:

![](Image00895.jpg)

The URL can be of any [schemes that PHP supports](http://php.net/wrappers) , or custom stream wrappers.

  

# Chapter 38: Parsing HTML

## Section 38.1: Parsing HTML from a string

PHP implements a [DOM Level 2](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/http://) compliant parser, allowing you to work with HTML using familiar methods like

 
| getElementById () || or || appendChild () |
| --- | --- | --- |

.

![](Image00896.jpg)

Outputs:

![](Image00897.jpg)

 
| [libxml\_use\_internal\_errors](http://php.net/manual/en/function.libxml-use-internal-errors.php) [(](http://php.net/manual/en/function.libxml-use-internal-errors.php) [)](http://php.net/manual/en/function.libxml-use-internal-errors.php) || before importing your HTML. You can then use || [libxml\_get\_errors](http://php.net/manual/en/function.libxml-get-errors.php) [(](http://php.net/manual/en/function.libxml-get-errors.php) [)](http://php.net/manual/en/function.libxml-get-errors.php) |
| --- | --- | --- |

Note that PHP will emit warnings about any problems with the HTML, especially if you are importing a document fragment. To avoid these warnings, tell the DOM library (libxml) to handle its own errors by calling  to handle errors if needed.

## Section 38.2: Using XPath

![](Image00898.jpg)

Outputs:

![](Image00899.jpg)

## Section 38.3: SimpleXML

Presentation

![](Image00900.jpg)SimpleXML is a PHP library which provides an easy way to work with XML documents (especially reading and iterating through XML data).

![](Image00901.jpg)The only restraint is that the XML document must be well-formed.

![](Image00902.jpg)

![](Image00903.jpg)

Parsing XML using OOP approach

![](Image00904.jpg)

Accessing Children and Attributes

![](Image00905.jpg)When SimpleXML parses an XML document, it converts all its XML elements, or nodes, to properties of the resulting SimpleXMLElement object

In addition, it converts XML attributes to an associative array that may be accessed from the property to which they belong.

![](Image00906.jpg)

attribute in the XML document.

When you don't know their names (or you don't want to know them):

![](Image00907.jpg)

# Chapter 39: Regular Expressions (regexp/PCRE)

Parameter Details

$pattern a string with a regular expression (PCRE pattern)

## Section 39.1: Global RegExp match

A global RegExp match can be performed using preg\_match\_all . preg\_match\_all returns all matching results in the subject string (in contrast to preg\_match , which only returns the first one).

The preg\_match\_all function returns the number of matches. Third parameter $matches will contain matches in format controlled by flags that can be given in fourth parameter.

If given an array, $matches will contain array in similar format yo u’ d get with preg\_match , except that preg\_match stops at first match, where preg\_match\_all iterates over the string until the string is wholly consumed and returns result of each iteration in a multidimensional array, which format can be controlled by the flag in fourth argument.

The fourth argument, $flags , controls structure of $matches array. Default mode is PREG\_PATTERN\_ORDER and possible flags are PREG\_SET\_ORDER and PREG\_PATTERN\_ORDER .

![](Image00908.jpg)

The first var\_dump from PREG\_SET\_ORDER gives this output:

![](Image00909.jpg)

![](Image00910.jpg)

$matches has three nested arrays. Each array represents one match, which has the same format as the return result of preg\_match .

The second var\_dump ( PREG\_PATTERN\_ORDER ) gives this output:

![](Image00911.jpg)

When the same regexp is run through preg\_match , following array is returned:

![](Image00912.jpg)

## Section 39.2: String matching with regular expressions

preg\_match checks whether a string matches the regular expression.

![](Image00913.jpg)

If you pass in a third parameter, it will be populated with the matching data of the regular expression:

![](Image00914.jpg) preg\_match ( '%^(\[a-zA-Z\]+): (\[0-9\]+)$%' , 'This is a string which contains numbers: 12345' , $matches );

// $matches now contains results of the regular expression matches in an array. echo json\_encode ( $matches ); // \["numbers: 12345", "numbers", "12345"\]

$matches contains an array of the whole match then substrings in the regular expression bounded by parentheses, in the order of open parenthesis's offset. That means, if you have / z ( a ( b ))/ as the regular expression, index 0 contains the whole substring zab , index 1 contains the substring bounded by the outer parentheses ab and index 2

contains the inner parentheses b .

## Section 39.3: Split string into array by a regular expression

![](Image00915.jpg)

Output:

![](Image00916.jpg)

 
| preg\_split |
| --- |

To split a string into a array simply pass the string and a regexp for (); to match and search, adding a third parameter ( limit ) allows you to set the number of "matches" to perform, the remaining string will be added to the end of the array.

The fourth parameter is ( flags ) here we use the PREG\_SPLIT\_NO\_EMPTY which prevents our array from containing any empty keys / values.

## Section 39.4: String replacing with regular expression

$string \= "a;b;c \\n d;e;f" ;

![](Image00917.jpg) // $1, $2 and $3 represent the first, second and third capturing groups echo preg\_replace ( "(^(\[^;\]+);(\[^;\]+);(\[^;\]+)$)m" , " $3 ; $2 ; $1 " , $string );

Outputs

![](Image00918.jpg)

Searches for everything between semicolons and reverses the order.

## Section 39.5: String replace with callback

preg\_replace\_callback works by sending every matched capturing group to the defined callback and replaces it with the return value of the callback. This allows us to replace strings based on any kind of logic.

![](Image00919.jpg)

![](Image00920.jpg)

  

# Chapter 40: Traits

## Section 40.1: What is a Trait?

PHP only allows single inheritance. In other words, a class can only extend one other class. But what if you need to include something that doesn't belong in the parent class? Prior to PHP 5.4 you would have to get creative, but in 5.4 Traits were introduced. Traits allow you to basically "copy and paste" a portion of a class into your main class

![](Image00921.jpg)

So here we have MrEd , which is already extending Horse . But not all horses Talk , so we have a Trait for that. Let's note what this is doing

First, we define our Trait. We can use it with autoloading and Namespaces (see also Referencing a class or function in a namespace). Then we include it into our MrEd class with the keyword use .

You'll note that MrEd takes to using the Talk functions and variables without defining them. Remember what we said about copy and paste ? These functions and variables are all defined within the class now, as if this class had defined them.

 
| new Trait |
| --- |

Traits are most closely related to Abstract classes in that you can define variables and functions. You also cannot instantiate a Trait directly (i.e. () ). Traits cannot force a class to implicitly define a function like an

Abstract class or an Interface can. Traits are only for explicit definitions (since you can implement as many Interfaces as you want, see Interfaces).

When should I use a Trait?

The first thing you should do, when considering a Trait, is to ask yourself this important question

![](Image00922.jpg)              Can I avoid using a Trait by restructuring my code?

More often than not, the answer is going to be Yes . Traits are edge cases caused by single inheritance. The temptation to misuse or overuse Traits can be high. But consider that a Trait introduces another source for your code, which means there's another layer of complexity. In the example here, we're only dealing with 3 classes. But Traits mean you can now be dealing with far more than that. For each Trait, your class becomes that much harder to deal with, since you must now go reference each Trait to find out what it defines (and potentially where a collision happened, see Conflict Resolution). Ideally, you should keep as few Traits in your code as possible.

## Section 40.2: Traits to facilitate horizontal code reuse

Let's say we have an interface for logging:

![](Image00923.jpg)

Now say we have two concrete implementations of the Logger interface: the FileLogger and the ConsoleLogger .

![](Image00924.jpg)

Now if you define some other class Foo which you also want to be able to perform logging tasks, you could do something like this:

![](Image00925.jpg)

 
| setLogger |
| --- |

Foo is now also a Logger , but its functionality depends on the Logger implementation passed to it via () . If we now want class Bar to also have this logging mechanism, we would have to duplicate this piece of logic in the Bar class.

Instead of duplicating the code, a trait can be defined:

![](Image00926.jpg)

Now that we have defined the logic in a trait, we can use the trait to add the logic to the Foo and Bar classes:

![](Image00927.jpg)

![](Image00928.jpg)

## Section 40.3: Conflict Resolution

Trying to use several traits into one class could result in issues involving conflicting methods. You need to resolve such conflicts manually.

For example, let's create this hierarchy:

![](Image00929.jpg)

Now, let's try to create the following class:

![](Image00930.jpg)

The php interpreter will return a fatal error:

![](Image00931.jpg)

![](Image00932.jpg)Fatal error: Trait method say has not been applied, because there are collisions with other trait methods on TalkingParrot

![](Image00933.jpg)

![](Image00934.jpg)Meow

Woof

## Section 40.4: Implementing a Singleton using Traits

Disclaimer : In no way does this example advocate the use of singletons. Singletons are to be used with a lot of care.

In PHP there is quite a standard way of implementing a singleton:

![](Image00935.jpg)

To prevent code duplication, it is a good idea to extract this behaviour into a trait.

![](Image00936.jpg)

Now any class that wants to function as a singleton can simply use the trait:

![](Image00937.jpg)

Even though it is now impossible to serialize a singleton, it is still useful to also disallow the deserialize method.

## Section 40.5: Traits to keep classes clean

Over time, our classes may implement more and more interfaces. When these interfaces have many methods, the total number of methods in our class will become very large.

For example, let's suppose that we have two interfaces and a class implementing them:

![](Image00938.jpg)

Instead of implementing all the interface methods inside the Article class, we could use separate Traits to implement these interfaces, keeping the class smaller and separating the code of the interface implementation from the class.

From example, to implement the Printable interface we could create this trait:

![](Image00939.jpg)

and make the class use the trait:

![](Image00940.jpg)

The primary benefits would be that our interface-implementation methods will be separated from the rest of the class, and stored in a trait who has the sole responsibility to implement the interface for that particular type of object.

## Section 40.6: Multiple Traits Usage

![](Image00941.jpg)

The above example will output:

![](Image00942.jpg)

## Section 40.7: Changing Method Visibility

![](Image00943.jpg)

![](Image00944.jpg)

Running this example:

![](Image00945.jpg)

 
| trait HelloWorld |
| --- |

So be aware that in the last example in MyClass2 the original un-aliased method from  stays accessible as-is.

  

# Chapter 41: Composer Dependency Manager

Parameter Details

 
| license || Defines the type of license you want to use in the Project. |
| --- | --- |
| authors || Defines the authors of the project, as well as the author details. |
| support || Defines the support emails, irc channel, and various links. |
| require || Defines the actual dependencies as well as the package versions. |
| require-dev || Defines the packages necessary for developing the project. |
| suggest || Defines the package suggestions, i.e. packages which can help if installed. |
| autoload || Defines the autoloading policies of the project. |

autoload-dev Defines the autoloading policies for developing the project.

[Composer](https://getcomposer.org/) is PHP's most commonly used dependency manager. It's analogous to npm in Node, pip for Python, or NuGet for .NET.

## Section 41.1: What is Composer?

[Composer](https://getcomposer.org/) is a dependency/package manager for PHP. It can be used to install, keep track of, and update your project dependencies. Composer also takes care of autoloading the dependencies that your application relies on, letting you easily use the dependency inside your project without worrying about including them at the top of any given file.

 
| composer || . || json |
| --- | --- | --- |

Dependencies for your project are listed within a  file which is typically located in your project root. This file holds information about the required versions of packages for production and also development.

 
| composer || . || json |
| --- | --- | --- |

A full outline of the  schema can be found on the [Composer Website](https://getcomposer.org/doc/04-schema.md) .

 
| composer require || < || package || \> or || composer require || \- || dev || < || package |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

This file can be edited manually using any text-editor or automatically through the command line via commands such as \> .

 
| composer || . || json |
| --- | --- | --- |

 
| laravel || / || laravel |
| --- | --- | --- |

To start using composer in your project, you will need to create the  file. You can either create it manually or simply run composer init . After you run composer init in your terminal, it will ask you for some basic information about your project: Package name ( vendor/package \- e.g. ), Description \- optional , Author and some other information like Minimum Stability, License and Required Packages.

 
| composer || . || json |
| --- | --- | --- |

The require key in your  file specifies Composer which packages your project depends on. require takes an object that maps package names (e.g. monolog/monolog ) to version constraints (e.g. 1.0. \*).

![](Image00946.jpg)

To install the defined dependencies, you will need to run the composer install command and it will then find the defined packages that matches the supplied version constraint and download it into the vendor directory. It's a convention to put third party code into a directory named vendor .

 
| composer || . || lock |
| --- | --- | --- |

You will notice the install command also created a  file.

 
| composer || . || lock |
| --- | --- | --- |

A  file is automatically generated by Composer. This file is used to track the currently installed versions and state of your dependencies. Running composer install will install packages to exactly the state stored in the lock file.

## Section 41.2: Autoloading with Composer

While composer provides a system to manage dependencies for PHP projects (e.g. from [Packagist](https://packagist.org/) ), it can also notably serve as an autoloader, specifying where to look for specific namespaces or include generic function files.

 
| composer || . || json |
| --- | --- | --- |

It starts with the  file:

![](Image00947.jpg)

 
| functions || . || php |
| --- | --- | --- |

This configuration code ensures that all classes in the namespace MyVendorName\\MyProject are mapped to the src directory and all classes in MyVendorName\\MyProject\\Tests to the tests directory (relative to your root directory). It will also automatically include the file .

 
| composer || . || json |
| --- | --- | --- |

 
| autoload || . || php |
| --- | --- | --- |

 
| composer install \-- no || \- || dev || . The || autoload || . || php |
| --- | --- | --- | --- | --- | --- | --- |

 
| composer || . || json |
| --- | --- | --- |

After putting this in your  file, run composer update in a terminal to have composer update the dependencies, the lock file and generate the  file. When deploying to a production environment you would use  file can be found in the vendor directory which should be generated in the directory where  resides.

You should require this file early at a setup point in the lifecycle of your application using a line similar to that below.

![](Image00948.jpg)

 
| autoload || . || php |
| --- | --- | --- |

Once included, the  file takes care of loading all the dependencies that you provided in your

 
| composer || . || json |
| --- | --- | --- |

file.

Some examples of the class path to directory mapping:

 
| src || / || Shapes || / || Square || . || php |
| --- | --- | --- | --- | --- | --- | --- |

 
| tests || / || Shapes || / || Square || . || php |
| --- | --- | --- | --- | --- | --- | --- |

![](Image00949.jpg)MyVendorName\\MyProject\\Shapes\\Square ➔ .

MyVendorName\\MyProject\\Tests\\Shapes\\Square ➔ .

## Section 41.3: Dierence between 'composer install' and 'composer update'

 
| composer || . || json |
| --- | --- | --- |

composer update composer update will update our dependencies as they are specified in .

For example, if our project uses this configuration:

![](Image00950.jpg)

Supposing we have actually installed the 2 . 0 . 1 version of the package, running composer update will cause an upgrade of this package (for example to 2 . 0 . 2 , if it has already been released).

In detail composer update will:

 
| composer || . || json |
| --- | --- | --- |

 
| composer || . || json |
| --- | --- | --- |

 
| composer || . || lock |
| --- | --- | --- |

![](Image00951.jpg)Read

Remove installed packages that are no more required in

Check the availability of the latest versions of our required packages

Install the latest versions of our packages Update  to store the installed packages version composer install

 
| composer || . || lock |
| --- | --- | --- |

composer install will install all of the dependencies as specified in the  file at the version specified (locked), without updating anything.

In detail:

 
| composer || . || lock |
| --- | --- | --- |

 
| composer || . || lock |
| --- | --- | --- |

![](Image00952.jpg)Read  file Install the packages specified in the  file

![](Image00953.jpg)When to install and when to update composer update is mostly used in the 'development' phase, to upgrade our project packages.

 
| composer || . || lock |
| --- | --- | --- |

composer install is primarily used in the 'deploying phase' to install our application on a production server or on a testing environment, using the same dependencies stored in the  file created by composer update .

## Section 41.4: Composer Available Commands

 
| Command || Usage |
| --- | --- |
| about || Short information about Composer |
| archive || Create an archive of this composer package |
| browse || Opens the package's repository URL or homepage in your browser. |
| clear-cache || Clears composer's internal package cache. |
| clearcache || Clears composer's internal package cache. |
| config || Set config options |
| create-project || Create new project from a package into given directory. |
| depends || Shows which packages cause the given package to be installed |
| diagnose || Diagnoses the system to identify common errors. |

dump-autoload Dumps the autoloader dumpautoload Dumps the autoloader exec Execute a vendored binary/script global              Allows running commands in the global composer dir ($COMPOSER\_HOME).

help Displays help for a command home Opens the package's repository URL or homepage in your browser.

 
| info || Show information about packages |
| --- | --- |
| init || Creates a basic composer.json file in current directory. |
| install || Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json. |
| licenses || Show information about licenses of dependencies |
| list || Lists commands |
| outdated || Shows a list of installed packages that have updates available, including their latest version. |
| prohibits || Shows which packages prevent the given package from being installed |
| remove || Removes a package from the require or require-dev |
| require || Adds required packages to your composer.json and installs them |
| run-script || Run the scripts defined in composer.json. |
| search || Search for packages |
| self-update || Updates composer.phar to the latest version. |
| selfupdate || Updates composer.phar to the latest version. |
| show || Show information about packages |
| status || Show a list of locally modified packages |
| suggests || Show package suggestions |
| update || Updates your dependencies to the latest version according to composer.json, and updates the composer.lock file. |
| validate || Validates a composer.json and composer.lock |
| why || Shows which packages cause the given package to be installed |
| why-not || Shows which packages prevent the given package from being installed |

## Section 41.5: Benefits of Using Composer

 
| composer || . || lock |
| --- | --- | --- |

Composer tracks which versions of packages you have installed in a file called , which is intended to be committed to version control, so that when the project is cloned in the future, simply running composer install will download and install all the project's dependencies.

Composer deals with PHP dependencies on a per-project basis. This makes it easy to have several projects on one machine that depend on separate versions of one PHP package.

Composer tracks which dependencies are only intended for dev environments only

![](Image00954.jpg)

Composer provides an autoloader, making it extremely easy to get started with any package. For instance, after

 
| composer require fabpot || / || goutte |
| --- | --- | --- |

installing [Goutte](https://github.com/FriendsOfPHP/Goutte) with , you can immediately start to use Goutte in a new project:

![](Image00955.jpg)

Composer allows you to easily update a project to the latest version that is allowed by your composer.json. EG.

 
| composer update fabpot || / || goutte |
| --- | --- | --- |

, or to update each of your project's dependencies: composer update .

## Section 41.6: Installation

You may install Composer locally, as part of your project, or globally as a system wide executable.

Locally

To install, run these commands in your terminal.

php \- r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

![](Image00956.jpg) \# to check the validity of the downloaded installer, check here against the SHA-384: # https://composer.github.io/pubkeys.html php composer \- setup . php

php \- r "unlink('composer-setup.php');"

 
| composer || . || phar |
| --- | --- | --- |

 
| composer || . || phar |
| --- | --- | --- |

This will download  (a PHP Archive file) to the current directory. Now you can run php to use Composer, e.g.

![](Image00957.jpg)

Globally

To use Composer globally, place the composer.phar file to a directory that is part of your PATH

![](Image00958.jpg)

 
| php composer || . || phar |
| --- | --- | --- |

Now you can use composer anywhere instead of , e.g.

![](Image00959.jpg)

  

# Chapter 42: Magic Methods

## Section 42.1: \_\_call() and \_\_callStatic()

 
| \_\_call () || and || \_\_callStatic () |
| --- | --- | --- |

are called when somebody is calling nonexistent object method in object or static

context.

![](Image00960.jpg)

![](Image00961.jpg)

Example:

![](Image00962.jpg)

## Section 42.2: \_\_get(), \_\_set(), \_\_isset() and \_\_unset()

Whenever you attempt to retrieve a certain field from a class like so:

![](Image00963.jpg)

 
| \_\_get || ( || $name |
| --- | --- | --- |

PHP invokes the magic method ) , with $name equal to "height" in this case. Writing to a class field like so:

![](Image00964.jpg)

 
| \_\_set || ( || $name || , ||   $value |
| --- | --- | --- | --- | --- |

Will invoke the magic method ) , with $name equal to "height" and $value equal to 10 .

 
| isset || () , which check if a variable exists, and || unset |
| --- | --- | --- |

PHP also has two built-in functions () , which destroys a variable.

Checking whether a objects field is set like so:

![](Image00965.jpg)

 
| \_\_isset || ( || $name |
| --- | --- | --- |

Will invoke the ) function on that object. Destroying a variable like so:

![](Image00966.jpg)

 
| \_\_unset || ( || $name |
| --- | --- | --- |

Will invoke the ) function on that object.

Normally, when you don't define these methods on your class, PHP just retrieves the field as it is stored in your class. However, you can override these methods to create classes that can hold data like an array, but are usable like an object:

![](Image00967.jpg)

![](Image00968.jpg)

empty() function and magic methods

 
| [empty](http://php.net/manual/en/function.empty.php) || [(](http://php.net/manual/en/function.empty.php) [)](http://php.net/manual/en/function.empty.php) on a class attribute will invoke || \_\_isset |
| --- | --- | --- |

Note that calling () because as the PHP manual states:

![](Image00969.jpg)empty() is essentially the concise equivalent to !isset($var) || $var == false

## Section 42.3: \_\_construct() and \_\_destruct()

 
| \_\_construct |
| --- |

() is the most common magic method in PHP, because it is used to set up a class when it is initialized.

 
| \_\_construct || () method is the || \_\_destruct |
| --- | --- | --- |

The opposite of the () method. This method is called when there are no

more references to an object that you created or when you force its deletion. PHP's garbage collection will clean up the object by first calling its destructor and then removing it from memory.

![](Image00970.jpg)

![](Image00971.jpg)

## Section 42.4: \_\_toString()

 
| \_\_toString |
| --- |

Whenever an object is treated as a string, the () method is called. This method should return a string representation of the class.

![](Image00972.jpg)

## Section 42.5: \_\_clone()

\_\_clone is invoked by use of the clone keyword. It is used to manipulate object state upon cloning, after the object has been actually cloned.

![](Image00973.jpg)

Example:

![](Image00974.jpg)

## Section 42.6: \_\_invoke()

This magic method is called when user tries to invoke object as a function. Possible use cases may include some approaches like functional programming or some callbacks.

![](Image00975.jpg)

![](Image00976.jpg)

## Section 42.7: \_\_sleep() and \_\_wakeup()

\_\_sleep and \_\_wakeup are methods that are related to the serialization process. serialize function checks if a class has a \_\_sleep method. If so, it will be executed before any serialization. \_\_sleep is supposed to return an array of the names of all variables of an object that should be serialized.

\_\_wakeup in turn will be executed by unserialize if it is present in class. It's intention is to re-establish resources and other things that are needed to be initialized upon unserialization.

![](Image00977.jpg)

## Section 42.8: \_\_debugInfo()

![](Image00978.jpg)

Version ≤ 5.6

![](Image00979.jpg)

The above example will output:

![](Image00980.jpg)

Version ≥ 5.6

![](Image00981.jpg)

The above example will output:

![](Image00982.jpg)

  

# Chapter 43: File handling

Parameter Description filename The filename being read.

You can use the optional second parameter and set it to TRUE, if you want to search for the file use\_include\_path

in the include\_path, too.

context A context stream resource.

## Section 43.1: Convenience functions

Raw direct IO [file\_get\_contents](http://php.net/manual/en/function.file-get-contents.php) and [file\_put\_contents](http://php.net/manual/en/function.file-put-contents.php) provide the ability to read/write from/to a file to/from a PHP string in a single call. [file\_put\_contents](http://php.net/manual/en/function.file-put-contents.php) can also be used with the FILE\_APPEND bitmask flag to append to, instead of truncate and overwrite, the file. It can be used along with LOCK\_EX bitmask to acquire an exclusive lock to the file while proceeding to writing. Bitmask flags can be joined with the | bitwise-OR operator.

![](Image00983.jpg)

![](Image00984.jpg) FILE\_APPEND is handy for appending to log files while LOCK\_EX helps prevent race condition of file writing from multiple processes. For example, to write to a log file about the current session: file\_put\_contents ( "logins.log" , "{ $\_SESSION \[" username "\]} logged in" , FILE\_APPEND | LOCK\_EX );

CSV IO

![](Image00985.jpg)

The [fgetcsv](http://php.net/fgetcsv) parses line from open file checking for csv fields. It returns CSV fields in an array on success or FALSE on failure.

By default, it will read only one line of the CSV file.

![](Image00986.jpg)

 
| contacts || . || csv |
| --- | --- | --- |

![](Image00987.jpg)

Output:

![](Image00988.jpg)

![](Image00989.jpg)

Reading a file to stdout directly [readfile](http://php.net/readfile) copies a file to the output buffer. readfile() will not present any memory issues, even when sending large files, on its own.

![](Image00990.jpg)

Or from a file pointer

Alternatively, to seek a point in the file to start copying to stdout, use [fpassthru](http://php.net/fpassthru) instead. In the following example, the last 1024 bytes are copied to stdout:

![](Image00991.jpg)

[file](http://php.net/manual/en/function.file.php) returns the lines in the passed file in an array. Each element of the array corresponds to a line in the file, with the newline still attached.

![](Image00992.jpg)

 
| test || . || txt |
| --- | --- | --- |

![](Image00993.jpg)

Output:

![](Image00994.jpg)

## Section 43.2: Deleting files and directories

Deleting files

The [unlink](http://php.net/unlink) function deletes a single file and returns whether the operation was successful.

![](Image00995.jpg)

Deleting directories, with recursive deletion

On the other hand, directories should be deleted with [rmdir](http://php.net/rmdir) . However, this function only deletes empty directories. To delete a directory with files, delete the files in the directories first. If the directory contains subdirectories, recursion may be needed.

The following example scans files in a directory, deletes member files/directories recursively, and returns the number of files (not directories) deleted.

![](Image00996.jpg)

## Section 43.3: Getting file information

Check if a path is a directory or a file

The [is\_dir](http://php.net/is-dir) function returns whether the argument is a directory, while [is\_file](http://php.net/is-file) returns whether the argument is a file. Use [file\_exists](http://php.net/file-exists) to check if it is either.

![](Image00997.jpg)

$file \= "/this/is/a/file.txt" ;

![](Image00998.jpg) echo is\_dir ( $dir ) ? " $dir is a directory" : " $dir is not a directory" , PHP\_EOL ,     is\_file ( $dir ) ? " $dir is a file" : " $dir is not a file" , PHP\_EOL ,     file\_exists ( $dir ) ? " $dir exists" : " $dir doesn't exist" , PHP\_EOL ,     is\_dir ( $file ) ? " $file is a directory" : " $file is not a directory" , PHP\_EOL ,     is\_file ( $file ) ? " $file is a file" : " $file is not a file" , PHP\_EOL ,     file\_exists ( $file ) ? " $file exists" : " $file doesn't exist" , PHP\_EOL ;

This gives:

![](Image00999.jpg)

Checking file type

Use [filetype](http://php.net/filetype) to check the type of a file, which may be:

![](Image01000.jpg)fifo char dir block link file socket unknown

Passing the filename to the [filetype](http://php.net/filetype) directly:

![](Image01001.jpg)

Note that filetype returns false and triggers an E\_WARNING if the file doesn't exist.

Checking readability and writability

Passing the filename to the [is\_writable](http://php.net/is-writable) and [is\_readable](http://php.net/is-readable) functions check whether the file is writable or readable respectively.

The functions return false gracefully if the file does not exist.

Checking file access/modify time

Using [filemtime](http://php.net/filemtime) and [fileatime](http://php.net/fileatime) returns the timestamp of the last modification or access of the file. The return value is a Unix timestamp -- see Working with Dates and Time for details.

![](Image01002.jpg) echo "File was last modified on " . date ( "Y-m-d" , filemtime ( "file.txt" )); echo "File was last accessed on " . date ( "Y-m-d" , fileatime ( "file.txt" ));

![](Image01003.jpg)

![](Image01004.jpg)

This example will output:

![](Image01005.jpg)

![](Image01006.jpg)

$path The full path of the file to be parsed

One of four available options \[PATHINFO\_DIRNAME, PATHINFO\_BASENAME, PATHINFO\_EXTENSION or $option

PATHINFO\_FILENAME\]

 
| image || . || jpg || . || png || would be . || png |
| --- | --- | --- | --- | --- | --- | --- |

![](Image01007.jpg)If an option (the second parameter) is not passed, an associative array is returned otherwise a string is returned.

Does not validate that the file exists.

Simply parses the string into parts. No validation is done on the file (no mime-type checking, etc.)

 
| jpg |
| --- |

The extension is simply the last extension of $path The path for the file  even if it technically a . file. A file without an extension will not return an extension element in the array.

## Section 43.4: Stream-based file IO

Opening a stream [fopen](http://php.net/fopen) opens a file stream handle, which can be used with various functions for reading, writing, seeking and other functions on top of it. This value is of resource type, and cannot be passed to other threads persisting its functionality.

![](Image01008.jpg) $f \= fopen ( "errors.log" , "a" ); // Will try to open errors.log for writing

The second parameter is the mode of the file stream:

Mode Description

r Open in read only mode, starting at the beginning of the file

r+ Open for reading and writing, starting at the beginning of the file open for writing only, starting at the beginning of the file. If the file exists it will empty the file. If it doesn't

w exist it will attempt to create it. open for reading and writing, starting at the beginning of the file. If the file exists it will empty the file. If it

w+ doesn't exist it will attempt to create it.

a open a file for writing only, starting at the end of the file. If the file does not exist, it will try to create it open a file for reading and writing, starting at the end of the file. If the file does not exist, it will try to create

a+

it

x create and open a file for writing only. If the file exists the fopen call will fail

x+ create and open a file for reading and writing. If the file exists the fopen call will fail open the file for writing only. If the file does not exist it will try to create it. It will start writing at the

c

beginning of the file, but will not empty the file ahead of writing open the file for reading and writing. If the file does not exist it will try to create it. It will start writing at the

c+

beginning of the file, but will not empty the file ahead of writing

 
| \\n || " line endings to " || \\r\\n |
| --- | --- | --- |

Adding a t behind the mode (e.g. a + b , wt , etc.) in Windows will translate "" when working with the file. Add b behind the mode if this is not intended, especially if it is a binary file.

The PHP application should close streams using [fclose](http://php.net/fclose) when they are no longer used to prevent the Too many open files error. This is particularly important in CLI programs, since the streams are only closed when the runtime shuts down -- this means that in web servers, it may not be necessary (but still should , as a practice to prevent resource leak) to close the streams if you do not expect the process to run for a long time, and will not open many streams.

Reading

Using [fread](http://php.net/fread) will read the given number of bytes from the file pointer, or until an EOF is met.

Reading lines

Using [fgets](http://php.net/fgets) will read the file until an EOL is reached, or the given length is read.

Both [fread](http://php.net/fread) and [fgets](http://php.net/fgets) will move the file pointer while reading.

Reading everything remaining

Using [stream\_get\_contents](http://php.net/stream-get-contents) will all remaining bytes in the stream into a string and return it.

Adjusting file pointer position

Initially after opening the stream, the file pointer is at the beginning of the file (or the end, if the mode a is used). Using the [fseek](http://php.net/fseek) function will move the file pointer to a new position, relative to one of three values:

![](Image01009.jpg)SEEK\_SET : This is the default value; the file position offset will be relative to the beginning of the file.

SEEK\_CUR : The file position offset will be relative to the current position.

SEEK\_END : The file position offset will be relative to the end of the file. Passing a negative offset is the most common use for this value; it will move the file position to the specified number of bytes before the end of file.

 
| SEEK\_SET |
| --- |

 
| fseek || ( || $fh |
| --- | --- | --- |

![](Image01010.jpg) [rewind](http://php.net/rewind) is a convenience shortcut of , 0,) .

Using [ftell](http://php.net/ftell) will show the absolute position of the file pointer.

For example, the following script reads skips the first 10 bytes, reads the next 10 bytes, skips 10 bytes, reads the next 10 bytes, and then the last 10 bytes in file.txt:

![](Image01011.jpg)

![](Image01012.jpg)

Writing

Using [fwrite](http://php.net/fwrite) writes the provided string to the file starting at the current file pointer.

![](Image01013.jpg)

## Section 43.5: Moving and Copying files and directories

Copying files [copy](http://php.net/copy) copies the source file in the first argument to the destination in the second argument. The resolved destination needs to be in a directory that is already created.

![](Image01014.jpg)

Copying directories, with recursion

Copying directories is pretty much similar to deleting directories, except that for files [copy](http://php.net/copy) instead of [unlink](http://php.net/unlink) is used, while for directories, [mkdir](http://php.net/mkdir) instead of [rmdir](http://php.net/rmdir) is used, at the beginning instead of being at the end of the function.

![](Image01015.jpg)

Renaming/Moving

Renaming/Moving files and directories is much simpler. Whole directories can be moved or renamed in a single call, using the [rename](http://php.net/rename) function.

 
| rename || ( || "~/file.txt" || , ||   "~/file.html" |
| --- | --- | --- | --- | --- |

![](Image01016.jpg));

 
| rename || ( || "~/dir" || , ||   "~/old\_dir" |
| --- | --- | --- | --- | --- |

 
| rename || ( || "~/dir/file.txt" || , ||   "~/dir2/file.txt" |
| --- | --- | --- | --- | --- |

![](Image01017.jpg));

);

## Section 43.6: Minimize memory usage when dealing with large files

If we need to parse a large file, e.g. a CSV more than 10 Mbytes containing millions of rows, some use file or file\_get\_contents functions and end up with hitting memory\_limit setting with

![](Image01018.jpg)              Allowed memory size of XXXXX bytes exhausted

error. Consider the following source (top-1m.csv has exactly 1 million rows and is about 22 Mbytes of size)

![](Image01019.jpg)

This outputs:

![](Image01020.jpg)

because the interpreter needed to hold all the rows in $arr array, so it consumed ~200 Mbytes of RAM. Note that we haven't even done anything with the contents of the array.

Now consider the following code:

![](Image01021.jpg)

which outputs

![](Image01022.jpg)

so we don't use a single extra byte of memory, but parse the whole CSV and save it to another file reversing the value of the 2nd column. That's because fgetcsv reads only one row and $row is overwritten in every loop.

# Chapter 44: Streams

Parameter Name Description

 
| <scheme> :// <target> |
| --- |

Stream Resource The data provider consisting of the  syntax

## Section 44.1: Registering a stream wrapper

A stream wrapper provides a handler for one or more specific schemes.

The example below shows a simple stream wrapper that sends PATCH HTTP requests when the stream is closed.

![](Image01023.jpg)

![](Image01024.jpg)

This example only shows some examples of what a generic stream wrapper would contain. These are not all methods available. A full list of methods that can be implemented can be found at [http://php.net/streamWrapper](http://php.net/streamWrapper) .

  

# Chapter 45: Type hinting

## Section 45.1: Type hinting classes and interfaces

Type hinting for classes and interfaces was added in PHP 5.

Class type hint

![](Image01025.jpg)

The above script outputs:

![](Image01026.jpg)              Chris is being enrolled at University of Edinburgh

Interface type hint

![](Image01027.jpg)

![](Image01028.jpg)

The above example outputs the same as before:

![](Image01029.jpg)              Chris is being enrolled at University of Edinburgh

Self type hints

The self keyword can be used as a type hint to indicate that the value must be an instance of the class that declares the method.

## Section 45.2: Type hinting scalar types, arrays and callables

Support for type hinting array parameters (and return values after PHP 7.1) was added in PHP 5.1 with the keyword array . Any arrays of any dimensions and types, as well as empty arrays, are valid values.

 
| is\_callable |
| --- |

 
| array || ( || class\_name || | || object |
| --- | --- | --- | --- | --- |

Support for type hinting callables was added in PHP 5.4. Any value that () is valid for parameters and return values hinted callable , i.e. Closure objects, function name strings and ,

 
| method\_name |
| --- |

) .

 
| is\_callable |
| --- |

If a typo occurs in the function name such that it is not () , a less obvious error message would be displayed:

![](Image01030.jpg)

Nonstatic methods can also be passed as callables in static format, resulting in a deprecation warning and level E\_STRICT error in PHP 7 and 5 respectively.

Method visibility is taken into account. If the context of the method with the callable parameter does not have access to the callable provided, it will end up as if the method does not exist.

![](Image01031.jpg)

![](Image01032.jpg)

Output:

![](Image01033.jpg)              Fatal error: Uncaught TypeError: Argument 1 passed to r() must be callable, array given

Support for type hinting scalar types was added in PHP 7. This means that we gain type hinting support for

By default, PHP will attempt to cast any provided argument to match its type hint. Changing the call to ![](Image01034.jpg)gives exactly the same output, since the float 1.5 was cast to int by PHP.

 
| declare || ( || strict\_types |
| --- | --- | --- |

To stop this behavior, one must add \=1); to the top of every PHP source file that requires it.

![](Image01035.jpg)

The above script now produces a fatal error:

![](Image01036.jpg)              Fatal error: Uncaught TypeError: Argument 1 passed to add() must be of the type integer, float given

An Exception: Special Types

Some PHP functions may return a value of type resource . Since this is not a scalar type, but a special type, it is not possible to type hint it.

 
| curl\_init || () will return a resource , as well as || fopen |
| --- | --- | --- |

As an example, () . Of course, those two resources aren't compatible to each other. Because of that, PHP 7 will always throw the following TypeError when type hinting resource explicitly:

![](Image01037.jpg)              TypeError: Argument 1 passed to sample() must be an instance of resource, resource given

## Section 45.3: Nullable type hints

Parameters

Nullable type hint was added in PHP 7.1 using the ? operator before the type hint.

![](Image01038.jpg)

Before PHP 7.1, if a parameter has a type hint, it must declare a default value null to accept null values.

![](Image01039.jpg)

Return values

In PHP 7.0, functions with a return type must not return null.

In PHP 7.1, functions can declare a nullable return type hint. However, the function must still return null, not void (no/empty return statements).

![](Image01040.jpg)

## Section 45.4: Type hinting generic objects

Since PHP objects don't inherit from any base class (including stdClass ), there is no support for type hinting a generic object type.

For example, the below will not work.

![](Image01041.jpg)

And will throw a fatal error:

![](Image01042.jpg)Fatal error: Uncaught TypeError: Argument 1 passed to doSomething() must be an instance of object, instance of OperationOne given

A workaround to this is to declare a degenerate interface that defines no methods, and have all of your objects implement this interface.

![](Image01043.jpg)

## Section 45.5: Type Hinting No Return(Void)

In PHP 7.1, the void return type was added. While PHP has no actual void value, it is generally understood across programming languages that a function that returns nothing is returning void . This should not be confused with returning null , as null is a value that can be returned.

![](Image01044.jpg)

Note that if you declare a void return, you cannot return any values or you will get a fatal error:

![](Image01045.jpg)

However, using return to exit the function is valid:

![](Image01046.jpg)

# Chapter 46: Filters & Filter Functions

Parameter Details

 
| variable || Value to filter. Note that scalar values are converted to string internally before they are filtered. |
| --- | --- |
| \------ || \------ |
| filter || The ID of the filter to apply. The Types of filters manual page lists the available filters.If omitted,FILTER\_DEFAULT will be used, which is equivalent to FILTER\_UNSAFE\_RAW. This will result in no filtering taking place by default. |
| \------ || \------ |
| options || Associative array of options or bitwise disjunction of flags. If filter accepts options, flags can be provided in "flags" field of array. For the "callback" filter, callable type should be passed. The callback must accept one argument, the value to be filtered, and return the value after filtering/sanitizing it. |

This extension filters data by either validating or sanitizing it. This is especially useful when the data source contains unknown (or foreign) data, like user supplied input. For example, this data may come from an HTML form.

## Section 46.1: Validating Boolean Values

![](Image01047.jpg) var\_dump ( filter\_var ( true , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // true var\_dump ( filter\_var ( false , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var (1, FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // true var\_dump ( filter\_var (0, FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var ( '1' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // true var\_dump ( filter\_var ( '0' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var ( '' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var ( ' ' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var ( 'true' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // true var\_dump ( filter\_var ( 'false' , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false var\_dump ( filter\_var (\[\], FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // NULL var\_dump ( filter\_var ( null , FILTER\_VALIDATE\_BOOLEAN , FILTER\_NULL\_ON\_FAILURE )); // false

## Section 46.2: Validating A Number Is A Float

Validates value as float, and converts to float on success.

![](Image01048.jpg) var\_dump ( filter\_var (1, FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( 1.0 , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( 1.0000 , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( 1.00001 , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1.0' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1.0000' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1.00001' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1,000' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1,000.0' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1,000.0000' , FILTER\_VALIDATE\_FLOAT )); var\_dump ( filter\_var ( '1,000.00001' , FILTER\_VALIDATE\_FLOAT ));

![](Image01049.jpg) var\_dump ( filter\_var (1, FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.0 , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.0000 , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.00001 , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.0' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.0000' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.00001' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.0' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.0000' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.00001' , FILTER\_VALIDATE\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND ));

Results

![](Image01050.jpg)

## Section 46.3: Validate A MAC Address

Validates a value is a valid MAC address

![](Image01051.jpg) var\_dump ( filter\_var ( 'FA-F9-DD-B2-5E-0D' , FILTER\_VALIDATE\_MAC )); var\_dump ( filter\_var ( 'DC-BB-17-9A-CE-81' , FILTER\_VALIDATE\_MAC )); var\_dump ( filter\_var ( '96-D5-9E-67-40-AB' , FILTER\_VALIDATE\_MAC )); var\_dump ( filter\_var ( '96-D5-9E-67-40' , FILTER\_VALIDATE\_MAC )); var\_dump ( filter\_var ( '' , FILTER\_VALIDATE\_MAC )); Results:

![](Image01052.jpg)

## Section 46.4: Sanitze Email Addresses

Remove all characters except letters, digits and !#$%&'\*+-=?^\_\`{|}~@.\[\].

![](Image01053.jpg) ![](Image01054.jpg) var\_dump ( filter\_var ( 'john@example.com' , FILTER\_SANITIZE\_EMAIL )); var\_dump ( filter\_var ( "!#$%&'\*+-=?^\_\`{|}~.\[\]@example.com" , FILTER\_SANITIZE\_EMAIL )); var\_dump ( filter\_var ( 'john/@example.com' , FILTER\_SANITIZE\_EMAIL )); var\_dump ( filter\_var ( 'john\\@example.com' , FILTER\_SANITIZE\_EMAIL )); var\_dump ( filter\_var ( 'joh n@example.com' , FILTER\_SANITIZE\_EMAIL )); Results:

![](Image01055.jpg)

## Section 46.5: Sanitize Integers

Remove all characters except digits, plus and minus sign.

![](Image01056.jpg) var\_dump ( filter\_var (1, FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var (-1, FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var (+1, FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( 1.00 , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var (+ 1.00 , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var (- 1.00 , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '1' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '-1' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '+1' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '1.00' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '+1.00' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '-1.00' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '1 unicorn' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '-1 unicorn' , FILTER\_SANITIZE\_NUMBER\_INT )); var\_dump ( filter\_var ( '+1 unicorn' , FILTER\_SANITIZE\_NUMBER\_INT ));

var\_dump ( filter\_var ( "!#$%&'\*+-=?^\_\`{|}~@.\[\]0123456789abcdefghijklmnopqrstuvwxyz" , FILTER\_SANITIZE\_NUMBER\_INT )); Results:

![](Image01057.jpg)

## Section 46.6: Sanitize URLs

Sanitze URLs

Remove all characters except letters, digits and $-\_.+!\*'(),{}|\\^~\[\]\`<>#%";/?:@&=

![](Image01058.jpg) var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_SANITIZE\_URL )); var\_dump ( filter\_var ( "http://www.example.com/path/to/dir/index.php?test=y!#$%&'\*+-=?^\_\`{|}~.\[\]" , FILTER\_SANITIZE\_URL ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=a b c' , FILTER\_SANITIZE\_URL )); Results:

![](Image01059.jpg) string (51) "http://www.example.com/path/to/dir/index.php?test=y" string (72) "http://www.example.com/path/to/dir/index.php?test=y!#$%&'\*+-=?^\_\`{|}~.\[\]" string (53) "http://www.example.com/path/to/dir/index.php?test=abc"

## Section 46.7: Validate Email Address

 
| filter\_var |
| --- |

When filtering an email address () will return the filtered data, in this case the email address, or false if a valid email address cannot be found:

![](Image01060.jpg) var\_dump ( filter\_var ( 'john@example.com' , FILTER\_VALIDATE\_EMAIL )); var\_dump ( filter\_var ( 'notValidEmail' , FILTER\_VALIDATE\_EMAIL )); Results:

![](Image01061.jpg)

 
| xn \-- |
| --- |

This function doesn't validate not-latin characters. Internationalized domain name can be validated in their form.

Note that you cannot know if the email address is correct before sending an email to it. You may want to do some extra checks such as checking for a MX record, but this is not necessary. If you send a confirmation email, don't forget to remove unused accounts after a short period.

## Section 46.8: Validating A Value Is An Integer

 
| filter\_var |
| --- |

When filtering a value that should be an integer () will return the filtered data, in this case the integer, or false if the value is not an integer. Floats are not integers:

![](Image01062.jpg) var\_dump ( filter\_var ( '10' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( 'a10' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( '10a' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( ' ' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( '10.00' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( '10,000' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( '-5' , FILTER\_VALIDATE\_INT )); var\_dump ( filter\_var ( '+7' , FILTER\_VALIDATE\_INT ));

Results:

![](Image01063.jpg)

![](Image01064.jpg)

If you are expecting only digits, you can use a regular expression:

![](Image01065.jpg)

If you convert this value into an integer, you don't have to do this check and so you can use filter\_var .

## Section 46.9: Validating An Integer Falls In A Range

When validating that an integer falls in a range the check includes the minimum and maximum bounds:

![](Image01066.jpg)

Results:

![](Image01067.jpg)

## Section 46.10: Validate a URL

 
| filter\_var |
| --- |

When filtering a URL () will return the filtered data, in this case the URL, or false if a valid URL cannot be found:

 
| example || . || com |
| --- | --- | --- |

URL:

![](Image01068.jpg) var\_dump ( filter\_var ( 'example.com' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED )); var\_dump ( filter\_var ( 'example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED )); var\_dump ( filter\_var ( 'example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED )); var\_dump ( filter\_var ( 'example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

![](Image01069.jpg)

 
| http || : || //example.com |
| --- | --- | --- |

URL:

![](Image01070.jpg) var\_dump ( filter\_var ( 'http://example.com' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'http://example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED )); var\_dump ( filter\_var ( 'http://example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED )); var\_dump ( filter\_var ( 'http://example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED )); var\_dump ( filter\_var ( 'http://example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

![](Image01071.jpg)

 
| http || : || //www.example.com |
| --- | --- | --- |

URL:

![](Image01072.jpg) var\_dump ( filter\_var ( 'http://www.example.com' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'http://www.example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED )); var\_dump ( filter\_var ( 'http://www.example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED )); var\_dump ( filter\_var ( 'http://www.example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED )); var\_dump ( filter\_var ( 'http://www.example.com' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

![](Image01073.jpg)

 
| http || : || //www.example.com/path/to/dir/ |
| --- | --- | --- |

URL:

![](Image01074.jpg) var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

![](Image01075.jpg)

 
| http || : || //www.example.com/path/to/dir/index.php |
| --- | --- | --- |

URL:

![](Image01076.jpg) var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED )); var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED ));

![](Image01077.jpg) var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

 
| http || : || //www.example.com/path/to/dir/index.php?test=y |
| --- | --- | --- |

![](Image01078.jpg) string (44) "http://www.example.com/path/to/dir/index.php" string (44) "http://www.example.com/path/to/dir/index.php" string (44) "http://www.example.com/path/to/dir/index.php" string (44) "http://www.example.com/path/to/dir/index.php" bool ( false ) URL:

![](Image01079.jpg) var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_VALIDATE\_URL )); var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_SCHEME\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_HOST\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_PATH\_REQUIRED ));

var\_dump ( filter\_var ( 'http://www.example.com/path/to/dir/index.php?test=y' , FILTER\_VALIDATE\_URL , FILTER\_FLAG\_QUERY\_REQUIRED )); Results:

![](Image01080.jpg) string (51) "http://www.example.com/path/to/dir/index.php?test=y" string (51) "http://www.example.com/path/to/dir/index.php?test=y" string (51) "http://www.example.com/path/to/dir/index.php?test=y" string (51) "http://www.example.com/path/to/dir/index.php?test=y" string (51) "http://www.example.com/path/to/dir/index.php?test=y"

Warning : You must check the protocol to protect you against an XSS attack:

![](Image01081.jpg) var\_dump ( filter\_var ( 'javascript://comment%0Aalert(1)' , FILTER\_VALIDATE\_URL ));

// string(31) "javascript://comment%0Aalert(1)"

## Section 46.11: Sanitize Floats

Remove all characters except digits, +- and optionally .,eE.

![](Image01082.jpg) var\_dump ( filter\_var (1, FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( 1.0 , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( 1.0000 , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( 1.00001 , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1,000' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1,000.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1,000.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1,000.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT )); var\_dump ( filter\_var ( '1.8281e-009' , FILTER\_SANITIZE\_NUMBER\_FLOAT ));

Results:

![](Image01083.jpg)

With the FILTER\_FLAG\_ALLOW\_THOUSAND option:

![](Image01084.jpg) var\_dump ( filter\_var (1, FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.0 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.0000 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( 1.00001 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1,000.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); var\_dump ( filter\_var ( '1.8281e-009' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_THOUSAND )); Results:

![](Image01085.jpg)

With the FILTER\_FLAG\_ALLOW\_SCIENTIFIC option:

![](Image01086.jpg) ![](Image01087.jpg) var\_dump ( filter\_var (1, FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( 1.0 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( 1.0000 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( 1.00001 , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1,000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1,000.0' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1,000.0000' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1,000.00001' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); var\_dump ( filter\_var ( '1.8281e-009' , FILTER\_SANITIZE\_NUMBER\_FLOAT , FILTER\_FLAG\_ALLOW\_SCIENTIFIC )); Results:

![](Image01088.jpg)

## Section 46.12: Validate IP Addresses

Validates a value is a valid IP address

![](Image01089.jpg) var\_dump ( filter\_var ( '185.158.24.24' , FILTER\_VALIDATE\_IP )); var\_dump ( filter\_var ( '2001:0db8:0a0b:12f0:0000:0000:0000:0001' , FILTER\_VALIDATE\_IP )); var\_dump ( filter\_var ( '192.168.0.1' , FILTER\_VALIDATE\_IP )); var\_dump ( filter\_var ( '127.0.0.1' , FILTER\_VALIDATE\_IP )); Results:

![](Image01090.jpg)

Validate an valid IPv4 IP address:

![](Image01091.jpg) var\_dump ( filter\_var ( '185.158.24.24' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV4 )); var\_dump ( filter\_var ( '2001:0db8:0a0b:12f0:0000:0000:0000:0001' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV4 )); var\_dump ( filter\_var ( '192.168.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV4 )); var\_dump ( filter\_var ( '127.0.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV4 )); Results:

![](Image01092.jpg)

Validate an valid IPv6 IP address:

![](Image01093.jpg) var\_dump ( filter\_var ( '185.158.24.24' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV6 )); var\_dump ( filter\_var ( '2001:0db8:0a0b:12f0:0000:0000:0000:0001' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV6 )); var\_dump ( filter\_var ( '192.168.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV6 )); var\_dump ( filter\_var ( '127.0.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_IPV6 ));

Results:

![](Image01094.jpg)

Validate an IP address is not in a private range:

![](Image01095.jpg) var\_dump ( filter\_var ( '185.158.24.24' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_PRIV\_RANGE )); var\_dump ( filter\_var ( '2001:0db8:0a0b:12f0:0000:0000:0000:0001' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_PRIV\_RANGE )); var\_dump ( filter\_var ( '192.168.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_PRIV\_RANGE )); var\_dump ( filter\_var ( '127.0.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_PRIV\_RANGE ));     Results:

![](Image01096.jpg)

Validate an IP address is not in a reserved range:

![](Image01097.jpg) var\_dump ( filter\_var ( '185.158.24.24' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_RES\_RANGE )); var\_dump ( filter\_var ( '2001:0db8:0a0b:12f0:0000:0000:0000:0001' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_RES\_RANGE )); var\_dump ( filter\_var ( '192.168.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_RES\_RANGE )); var\_dump ( filter\_var ( '127.0.0.1' , FILTER\_VALIDATE\_IP , FILTER\_FLAG\_NO\_RES\_RANGE ));     Results:

![](Image01098.jpg)

## Section 46.13: Sanitize filters

we can use filters to sanitize our variable according to our need.

Example

![](Image01099.jpg)

above will remove the html tags from $string variable.

# Chapter 47: Generators

## Section 47.1: The Yield Keyword

A yield statement is similar to a return statement, except that instead of stopping execution of the function and returning, yield instead returns a [Generator](http://php.net/manual/en/class.generator.php) object and pauses execution of the generator function.

Here is an example of the range function, written as a generator:

![](Image01100.jpg)

You can see that this function returns a [Generator](http://php.net/manual/en/class.generator.php) object by inspecting the output of var\_dump :

![](Image01101.jpg)

Yielding Values

The [Generator](http://php.net/manual/en/class.generator.php) object can then be iterated over like an array.

![](Image01102.jpg)

The above example will output:

![](Image01103.jpg)

Yielding Values with Keys

In addition to yielding values, you can also yield key/value pairs.

![](Image01104.jpg)

The above example will output:

![](Image01105.jpg)

## Section 47.2: Reading a large file with a generator

One common use case for generators is reading a file from disk and iterating over its contents. Below is a class that allows you to iterate over a CSV file. The memory usage for this script is very predictable, and will not fluctuate depending on the size of the CSV file.

![](Image01106.jpg)

## Section 47.3: Why use a generator?

Generators are useful when you need to generate a large collection to later iterate over. They're a simpler alternative to creating a class that implements an [Iterator](http://php.net/manual/en/class.iterator.php) , which is often overkill.

For example, consider the below function.

![](Image01107.jpg)

All this function does is generates an array that's filled with random numbers. To use it, we might do

 
| randomNumbers || ( || 10 |
| --- | --- | --- |

) , which will give us an array of 10 random numbers. What if we want to generate one million

 
| randomNumbers || ( || 1000000 |
| --- | --- | --- |

random numbers? ) will do that for us, but at a cost of memory. One million integers stored in an array uses approximately 33 megabytes of memory.

![](Image01108.jpg)

This is due to the entire one million random numbers being generated and returned at once, rather than one at a time. Generators are an easy way to solve this issue.

## Section 47.4: Using the send()-function to pass values to a generator

 
| send |
| --- |

Generators are fast coded and in many cases a slim alternative to heavy iterator-implementations. With the fast implementation comes a little lack of control when a generator should stop generating or if it should generate something else. However this can be achieved with the usage of the () function, enabling the requesting function to send parameters to the generator after every loop.

![](Image01109.jpg)

Resulting in this Output:

![](Image01110.jpg)

  

# Chapter 48: UTF-8

## Section 48.1: Input

![](Image01111.jpg)You should verify every received string as being valid UTF-8 before you try to store it or use it anywhere.

 
| [mb\_check\_encoding](http://php.net/manual/en/function.mb-check-encoding.php) |
| --- |

PHP's [(](http://php.net/manual/en/function.mb-check-encoding.php) [)](http://php.net/manual/en/function.mb-check-encoding.php) does the trick, but you have to use it consistently. There's really no way around this, as malicious clients can submit data in whatever encoding they want.

![](Image01112.jpg)

 
| accept || \- || charset || attribute to all of your || <form |
| --- | --- | --- | --- | --- |

in UTF-8. The only reliable way to do this is to add the \> tags like so:

![](Image01113.jpg)

## Section 48.2: Output

 
| php || . || ini || , or manually issue the || Content || \- || Type |
| --- | --- | --- | --- | --- | --- | --- |

![](Image01114.jpg)If your application transmits text to other systems, they will also need to be informed of the character encoding. In PHP, you can use the [default\_charset](http://www.php.net/manual/en/ini.core.php#ini.default-charset) option in

MIME header yourself. This is the preferred method when targeting modern browsers.

![](Image01115.jpg)

[HTML metadata](http://stackoverflow.com/q/4696499/4245525) .

![](Image01116.jpg)

## Section 48.3: Data Storage and Access

![](Image01117.jpg)This topic specifically talks about UTF-8 and considerations for using it with a database. If you want more information about using databases in PHP then checkout this topic.

Storing Data in a MySQL Database:

![](Image01118.jpg)Specify the utf8mb4 character set on all tables and text columns in your database. This makes MySQL physically store and retrieve values encoded natively in UTF-8.

 
| utf8mb4\_ |
| --- |

![](Image01119.jpg)MySQL will implicitly use utf8mb4 encoding if a \* collation is specified (without any explicit character set).

Older versions of MySQL (< 5.5.3) do not support utf8mb4 so you'll be forced to use utf8 , which only supports a subset of Unicode characters.

Accessing Data in a MySQL Database:

![](Image01120.jpg)In your application code (e.g. PHP), in whatever DB access method you use, you'll need to set the connection charset to utf8mb4 . This way, MySQL does no conversion from its native UTF-8 when it hands data off to your application and vice versa.

![](Image01121.jpg)Some drivers provide their own mechanism for configuring the connection character set, which both updates its own internal state and informs MySQL of the encoding to be used on the connection. This is usually the preferred approach.

For Example (The same consideration regarding utf8mb4 / utf8 applies as above):

If you're using the [PDO](http://www.php.net/manual/en/book.pdo.php) abstraction layer with PHP ≥ 5.3.6, you can specify charset in the [DSN](http://www.php.net/manual/en/ref.pdo-mysql.connection.php) :

 
| [set\_charset](http://www.php.net/manual/en/mysqli.set-charset.php) |
| --- |

$handle \= new PDO ( 'mysql:charset=utf8mb4' ); If you're using [mysqli](http://www.php.net/manual/en/book.mysqli.php) , you can call [(](http://www.php.net/manual/en/mysqli.set-charset.php) [)](http://www.php.net/manual/en/mysqli.set-charset.php) :

$conn \= mysqli\_connect ( 'localhost' , 'my\_user' , 'my\_password' , 'my\_db' );

![](Image01122.jpg) $conn \-> set\_charset ( 'utf8mb4' );         // object oriented style mysqli\_set\_charset ( $conn , 'utf8mb4' ); // procedural style

If you're stuck with plain [mysql](http://www.php.net/manual/en/book.mysql.php) but happen to be running PHP ≥ 5.2.3, you can call [mysql\_set\_charset](http://www.php.net/manual/en/function.mysql-set-charset.php) .

$conn \= mysql\_connect ( 'localhost' , 'my\_user' , 'my\_password' );

$conn \-> set\_charset ( 'utf8mb4' );        // object oriented style mysql\_set\_charset ( $conn , 'utf8mb4' ); // procedural style

 
| [SET NAMES](http://dev.mysql.com/doc/en/charset-connection.html) ['utf8mb4'](http://dev.mysql.com/doc/en/charset-connection.html) |
| --- |

If the database driver does not provide its own mechanism for setting the connection character set, you may have to issue a query to tell MySQL how your application expects data on the connection to be encoded: .

# Chapter 49: Unicode Support in PHP

## Section 49.1: Converting Unicode characters to “\\uxxxx” format using PHP

You can use the following code for going back and forward.

![](Image01123.jpg)

How to use:

![](Image01124.jpg)

Output:

![](Image01125.jpg)

## Section 49.2: Converting Unicode characters to their numeric value and/or HTML entities using PHP

You can use the following code for going back and forward.

![](Image01126.jpg)

![](Image01127.jpg)

How to use :

![](Image01128.jpg)

Output :

![](Image01129.jpg)

![](Image01130.jpg)

## Section 49.3: Intl extention for Unicode support

Native string functions are mapped to single byte functions, they do not work well with Unicode. The extentions iconv and mbstring offer some support for Unicode, while the Intl-extention offers full support. Intl is a wrapper for the facto de standard ICU library, see [http://site.icu-project.org](http://site.icu-project.org/) for detailed information that is not available on [http://php.net/manual/en/book.intl.php](http://php.net/manual/en/book.intl.php) . If you can not install the extention, have a look at [an alternative](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) [implementation of Intl from the Symfony framework](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) .

ICU offers full Internationalization of which Unicode is only a smaller part. You can do transcoding easily:

![](Image01131.jpg) \\UConverter :: transcode ( $sString , 'UTF-8' , 'UTF-8' );   // strip bad bytes against attacks

But, do not dismiss iconv just yet, consider:

![](Image01132.jpg)

# Chapter 50: URLs

## Section 50.1: Parsing a URL

 
| [parse\_url](http://php.net/parse_url) |
| --- |

To separate a URL into its individual components, use [(](http://php.net/parse_url) [)](http://php.net/parse_url) :

![](Image01133.jpg)

After executing the above, the contents of $parts would be:

![](Image01134.jpg)

You can also selectively return just one component of the url. To return just the querystring:

![](Image01135.jpg)

Any of the following constants are accepted: PHP\_URL\_SCHEME , PHP\_URL\_HOST , PHP\_URL\_PORT , PHP\_URL\_USER , PHP\_URL\_PASS , PHP\_URL\_PATH , PHP\_URL\_QUERY and PHP\_URL\_FRAGMENT .

 
| [parse\_str](http://php.net/parse_str) |
| --- |

To further parse a query string into key value pairs use [(](http://php.net/parse_str) [)](http://php.net/parse_str) :

![](Image01136.jpg)

After execution of the above, the $params array would be populated with the following:

![](Image01137.jpg)

## Section 50.2: Build an URL-encoded query string from an array

 
| [http\_build\_query](http://php.net/manual/function.http-build-query.php) |
| --- |

The [(](http://php.net/manual/function.http-build-query.php) [)](http://php.net/manual/function.http-build-query.php) will create a query string from an array or object. These strings can be appended to a URL to create a GET request, or used in a POST request with, for example, cURL.

![](Image01138.jpg)

$queryString will have the following value:

![](Image01139.jpg)

![](Image01140.jpg)

![](Image01141.jpg)

which is the URL-encoded version of

![](Image01142.jpg)

## Section 50.3: Redirecting to another URL

 
| header |
| --- |

You can use the () function to instruct the browser to redirect to a different URL:

![](Image01143.jpg)

You can also redirect to a relative URL (this is not part of the official HTTP specification, but it does work in all browsers):

![](Image01144.jpg)

If headers have been sent, you can alternatively send a meta refresh HTML tag.

WARNING: The meta refresh tag relies on HTML being properly processed by the client, and some will not do this. In general, it only works in web browsers. Also, consider that if headers have been sent, you may have a bug and this should trigger an exception.

You may also print a link for users to click, for clients that ignore the meta refresh tag:

![](Image01145.jpg)

  $saveUrl \= htmlspecialchars ( $url ); // protects from browser seeing url as HTML

  // tells browser to redirect page to $saveUrl after 0 seconds

  print '<meta http-equiv="refresh" content="0; url=' . $saveUrl . '">' ;

![](Image01146.jpg)   // shows link for user   print '<p>Please continue to <a href="' . $saveUrl . '">' . $saveUrl . '</a></p>' ;

} exit ;

  

# Chapter 51: How to break down an URL

As you code PHP you will most likely get your self in a position where you need to break down an URL into several pieces. There's obviously more than one way of doing it depending on your needs. This article will explain those ways for you so you can find what works best for you.

## Section 51.1: Using parse\_url()

![](Image01147.jpg)

If you need the path separated you can use explode

![](Image01148.jpg)

If you need the last part of the section you can use end() like this:

![](Image01149.jpg)

If the URL contains GET vars you can retrieve those as well

![](Image01150.jpg)

![](Image01151.jpg)

If you wish to break down the query vars you can use parse\_str() like this:

![](Image01152.jpg)

## Section 51.2: Using explode()

![](Image01153.jpg)explode(): Returns an array of strings, each of which is a substring of string formed by splitting it on boundaries formed by the string delimiter.

This function is pretty much straight forward.

![](Image01154.jpg)

You can retrieve the last part of the URL by doing this:

![](Image01155.jpg)

You can also navigate inside the array by using sizeof() in combination with a math operator like this:

![](Image01156.jpg)

## Section 51.3: Using basename()

![](Image01157.jpg)basename(): Given a string containing the path to a file or directory, this function will return the trailing name component.

This function will return only the last part of an URL

![](Image01158.jpg)

![](Image01159.jpg)

If your URL has more stuff to it and what you need is the dir name containing the file you can use it with dirname() like this:

![](Image01160.jpg)

  

# Chapter 52: Object Serialization

## Section 52.1: Serialize / Unserialize

 
| serialize |
| --- |

() returns a string containing a byte-stream representation of any value that can be stored in PHP.

 
| unserialize |
| --- |

() can use this string to recreate the original variable values.

To serialize an object

![](Image01161.jpg)

To Unserialize an object

![](Image01162.jpg)

Example

![](Image01163.jpg)

## Section 52.2: The Serializable interface

Introduction

 
| \_\_sleep || () and || \_\_wakeup |
| --- | --- | --- |

 
| \_\_destruct |
| --- |

 
| unserialize |
| --- |

 
| \_\_construct |
| --- |

![](Image01164.jpg)Classes that implement this interface no longer support () . The method serialize is called whenever an instance needs to be serialized. This does not invoke () or has any other side effect unless programmed inside the method. When the data is unserialized the class is known and the appropriate () method is called as a constructor instead of calling

() . If you need to execute the standard constructor you may do so in the method.

Basic usage

![](Image01165.jpg)

![](Image01166.jpg)

  

# Chapter 53: Serialization

Parameter Details

The value to be serialized. [serialize()](http://php.net/manual/en/function.serialize.php) handles all types, except the [resource](http://php.net/manual/en/language.types.resource.php) \-type. You can even serialize() arrays that contain references to itself. Circular references inside the array/object you are serializing will also be stored. Any other reference will be lost. When serializing objects, PHP will attempt to call the member function [\_\_sleep()](http://php.net/manual/en/language.oop5.magic.php#object.sleep) prior to serialization. This is to allow the object to do any value last minute clean-up, etc. prior to being serialized. Likewise, when the object is restored using [unserialize()](http://php.net/manual/en/function.unserialize.php) the [\_\_wakeup()](http://php.net/manual/en/language.oop5.magic.php#object.wakeup) member function is called. Object's private members have the class name prepended to the member name; protected members have a '\*' prepended to the member name. These prepended values have null bytes on either side.

## Section 53.1: Serialization of dierent types

Generates a storable representation of a value.

This is useful for storing or passing PHP values around without losing their type and structure.

To make the serialized string into a PHP value again, use unserialize() . ![](Image01167.jpg)echo serialize ( $double );

Serializing a float

![](Image01168.jpg)

![](Image01169.jpg)

![](Image01170.jpg)

![](Image01171.jpg)

You can also serialize Objects.

When serializing objects, PHP will attempt to call the member function \_\_sleep() prior to serialization. This is to allow the object to do any last minute clean-up, etc. prior to being serialized. Likewise, when the object is restored using unserialize() the \_\_wakeup() member function is called.

![](Image01172.jpg)

Note that Closures cannot be serialized:

![](Image01173.jpg)

## Section 53.2: Security Issues with unserialize

Using unserialize function to unserialize data from user input can be dangerous.

A Warning from php.net

![](Image01174.jpg)Warning Do not pass untrusted user input to unserialize(). Unserialization can result in code being loaded and executed due to object instantiation and autoloading, and a malicious user may be able to exploit this. Use a safe, standard data interchange format such as JSON (via json\_decode() and json\_encode()) if you need to pass serialized data to the user.

Possible Attacks

![](Image01175.jpg)PHP Object Injection

PHP Object Injection

PHP Object Injection is an application level vulnerability that could allow an attacker to perform different kinds of malicious attacks, such as Code Injection, SQL Injection, Path Traversal and Application Denial of Service, depending on the context. The vulnerability occurs when user-supplied input is not properly sanitized before being passed to the unserialize() PHP function. Since PHP allows object serialization, attackers could pass ad-hoc serialized strings to a vulnerable unserialize() call, resulting in an arbitrary PHP object(s) injection into the application scope.

In order to successfully exploit a PHP Object Injection vulnerability two conditions must be met:

 
| unserialize |
| --- |

![](Image01176.jpg)The application must have a class which implements a PHP magic method (such as \_\_wakeup or \_\_destruct ) that can be used to carry out malicious attacks, or to start a "POP chain".

All of the classes used during the attack must be declared when the vulnerable () is being called, otherwise object autoloading must be supported for such classes.

Example 1 - Path Traversal Attack

The example below shows a PHP class with an exploitable \_\_destruct method:

![](Image01177.jpg)

In this example an attacker might be able to delete an arbitrary file via a Path Traversal attack, for e.g. requesting the following URL:

![](Image01178.jpg) http : //testsite.com/vuln.php?data=O:8:"Example1":1:{s:10:"cache\_file";s:15:"../../index.php";}

Example 2 - Code Injection attack

The example below shows a PHP class with an exploitable \_\_wakeup method:

![](Image01179.jpg)

In this example an attacker might be able to perform a Code Injection attack by sending an HTTP request like this:

![](Image01180.jpg)

Where the cookie parameter "data" has been generated by the following script:

![](Image01181.jpg)

# Chapter 54: Closure

## Section 54.1: Basic usage of a closure

A closure is the PHP equivalent of an anonymous function, eg. a function that does not have a name. Even if that is technically not correct, the behavior of a closure remains the same as a function's, with a few extra features.

A closure is nothing but an object of the Closure class which is created by declaring a function without a name. For example:

![](Image01182.jpg)

Keep in mind that $myClosure is an instance of Closure so that you are aware of what you can truly do with it (cf.

[http://fr2.php.net/manual/en/class.closure.php](http://fr2.php.net/manual/en/class.closure.php) )

The classic case you would need a Closure is when you have to give a callable to a function, for instance [usort](http://fr2.php.net/manual/en/function.usort.php) .

Here is an example where an array is sorted by the number of siblings of each person:

![](Image01183.jpg)

## Section 54.2: Using external variables

It is possible, inside a closure, to use an external variable with the special keyword use . For instance:

![](Image01184.jpg)

![](Image01185.jpg)

You can go further by creating "dynamic" closures. It is possible to create a function that returns a specific calculator, depending on the quantity you want to add. For example:

![](Image01186.jpg)

## Section 54.3: Basic closure binding

As seen previously, a closure is nothing but an instance of the Closure class, and different methods can be invoked on them. One of them is bindTo , which, given a closure, will return a new one that is bound to a given object. For example:

![](Image01187.jpg)

## Section 54.4: Closure binding and scope

Let's consider this example:

![](Image01188.jpg)

![](Image01189.jpg)

Try to change the property visibility to either protected or private . You get a fatal error indicating that you do not have access to this property. Indeed, even if the closure has been bound to the object, the scope in which the closure is invoked is not the one needed to have that access. That is what the second argument of bindTo is for.

The only way for a property to be accessed if it's private is that it is accessed from a scope that allows it, ie. the class's scope. In the just previous code example, the scope has not been specified, which means that the closure has been invoked in the same scope as the one used where the closure has been created. Let's change that:

![](Image01190.jpg)

As just said, if this second parameter is not used, the closure is invoked in the same context as the one used where the closure has been created. For example, a closure created inside a method's class which is invoked in an object context will have the same scope as the method's:

![](Image01191.jpg)

![](Image01192.jpg)

## Section 54.5: Binding a closure for one call

Since PHP7 , it is possible to bind a closure just for one call, thanks to the [call](http://fr2.php.net/manual/fr/closure.call.php) method. For instance:

![](Image01193.jpg)

As opposed to the bindTo method, there is no scope to worry about. The scope used for this call is the same as the one used when accessing or invoking a property of $myInstance .

## Section 54.6: Use closures to implement observer pattern

In general, an observer is a class with a specific method being called when an action on the observed object occurs. In certain situations, closures can be enough to implement the observer design pattern.

Here is a detailed example of such an implementation. Let's first declare a class whose purpose is to notify observers when its property is changed.

![](Image01194.jpg)

![](Image01195.jpg)

Then, let's declare the class that will represent the different observers.

![](Image01196.jpg)

Let's finally test this:

![](Image01197.jpg)

![](Image01198.jpg)

Note that this example works because the observers share the same nature (they are both "named observers.")

  

# Chapter 55: Reading Request Data

## Section 55.1: Reading raw POST data

 
| application || / x \- || www || \- || form |
| --- | --- | --- | --- | --- |

Usually data sent in a POST request is structured key/value pairs with a MIME type of \-

urlencoded . However many applications such as web services require raw data, often in XML or JSON format, to be sent instead. This data can be read using one of two methods.

 
| php || : || //input |
| --- | --- | --- |

is a stream that provides access to the raw request body.

![](Image01199.jpg)

Version < 5.6

 
| php || . || ini |
| --- | --- | --- |

$HTTP\_RAW\_POST\_DATA is a global variable that contains the raw POST data. It is only available if the always\_populate\_raw\_post\_data directive in  is enabled.

![](Image01200.jpg)

This variable has been deprecated since PHP version 5.6, and was removed in PHP 7.0.

 
| multipart || / || form || \- || data |
| --- | --- | --- | --- | --- |

Note that neither of these methods are available when the content type is set to , which is used for file uploads.

## Section 55.2: Reading POST data

Data from a POST request is stored in the [superglobal](http://php.net/manual/en/language.variables.superglobals.php) $\_POST in the form of an associative array.

 
| isset || () or || empty |
| --- | --- | --- |

Note that accessing a non-existent array item generates a notice, so existence should always be checked with the () functions, or the null coalesce operator.

Example:

![](Image01201.jpg)

Version ≥ 7.0

![](Image01202.jpg)

## Section 55.3: Reading GET data

Data from a GET request is stored in the [superglobal](http://php.net/manual/en/language.variables.superglobals.php) $\_GET in the form of an associative array.

 
| isset || () or || empty |
| --- | --- | --- |

Note that accessing a non-existent array item generates a notice, so existence should always be checked with the () functions, or the null coalesce operator.

 
| topics || . || php?author || \= || alice || & || topic || \= || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

Example: (for URL / )

![](Image01203.jpg)

Version ≥ 7.0

![](Image01204.jpg)

## Section 55.4: Handling file upload errors

 
| $\_FILES || \[ || "FILE\_NAME" || \]\[ || 'error' |
| --- | --- | --- | --- | --- |

The \] (where "FILE\_NAME" is the value of the name attribute of the file input, present in your form) might contain one of the following values:

1.    UPLOAD\_ERR\_OK \- There is no error, the file uploaded with success.

 
| php || . || ini |
| --- | --- | --- |

2.    UPLOAD\_ERR\_INI\_SIZE \- The uploaded file exceeds the upload\_max\_filesize directive in .

3.    UPLOAD\_ERR\_PARTIAL \- The uploaded file exceeds the MAX\_FILE\_SIZE directive that was specified in the HTML form.

4.    UPLOAD\_ERR\_NO\_FILE \- No file was uploaded.

5.    UPLOAD\_ERR\_NO\_TMP\_DIR \- Missing a temporary folder. (From PHP 5.0.3).

6.    UPLOAD\_ERR\_CANT\_WRITE \- Failed to write file to disk. (From PHP 5.1.0).

7.    UPLOAD\_ERR\_EXTENSION \- A PHP extension stopped the file upload. (From PHP 5.2.0).

An basic way to check for the errors, is as follows:

![](Image01205.jpg)

## Section 55.5: Passing arrays by POST

Usually, an HTML form element submitted to PHP results in a single value. For example:

![](Image01206.jpg)

![](Image01207.jpg)

This results in the following output:

![](Image01208.jpg)

However, there may be cases where you want to pass an array of values. This can be done by adding a PHP-like suffix to the name of the HTML elements:

![](Image01209.jpg)

This results in the following output:

![](Image01210.jpg)

You can also specify the array indices, as either numbers or strings:

![](Image01211.jpg)

Which returns this output:

![](Image01212.jpg)

This technique can be used to avoid post-processing loops over the $\_POST array, making your code leaner and more concise.

## Section 55.6: Uploading files with HTTP PUT

[PHP provides support](http://php.net/manual/en/features.file-upload.put-method.php) for the HTTP PUT method used by some clients to store files on a server. PUT requests are much simpler than a file upload using POST requests and they look something like this:

![](Image01213.jpg)

Into your PHP code you would then do something like this:

![](Image01214.jpg)

Also [here](http://stackoverflow.com/questions/12005790/how-to-receive-a-file-via-http-put-with-php) you can read interesting SO question/answers about receiving file via HTTP PUT.

# Chapter 56: Type juggling and Non-Strict Comparison Issues

## Section 56.1: What is Type Juggling?

PHP is a loosely typed language. This means that, by default, it doesn't require operands in an expression to be of the same (or compatible) types. For example, you can append a number to a string and expect it to work.

![](Image01215.jpg)

The output will be:

![](Image01216.jpg)              string(24) "This is example number 1"

PHP accomplishes this by automatically casting incompatible variable types into types that allow the requested operation to take place. In the case above, it will cast the integer literal 1 into a string, meaning that it can be concatenated onto the preceding string literal. This is referred to as type juggling. This is a very powerful feature of PHP, but it is also a feature that can lead you to a lot of hair-pulling if you are not aware of it, and can even lead to security problems.

Consider the following:

![](Image01217.jpg)

The intent appears to be that the programmer is checking that a variable has a value of 1. But what happens if $variable has a value of "1 and a half" instead? The answer might surprise you.

![](Image01218.jpg)

The result is:

![](Image01219.jpg)bool(true)

Why has this happened? It's because PHP realised that the string "1 and a half" isn't an integer, but it needs to be in order to compare it to integer 1. Instead of failing, PHP initiates type juggling and, attempts to convert the variable into an integer. It does this by taking all the characters at the start of the string that can be cast to integer and casting them. It stops as soon as it encounters a character that can't be treated as a number. Therefore "1 and a half" gets cast to integer 1.

Granted, this is a very contrived example, but it serves to demonstrate the issue. The next few examples will cover some cases where I've run into errors caused by type juggling that happened in real software.

## Section 56.2: Reading from a file

When reading from a file, we want to be able to know when we've reached the end of that file. Knowing that

 
| fgets |
| --- |

() returns false at the end of the file, we might use this as the condition for a loop. However, if the data

returned from the last read happens to be something that evaluates as boolean false , it can cause our file read loop to terminate prematurely.

![](Image01220.jpg)

If the file being read contains a blank line, the while loop will be terminated at that point, because the empty string evaluates as boolean false .

Instead, we can check for the boolean false value explicitly, using strict equality operators:

![](Image01221.jpg)

Note this is a contrived example; in real life we would use the following loop:

![](Image01222.jpg)

Or replace the whole thing with:

![](Image01223.jpg)

## Section 56.3: Switch surprises

Switch statements use non-strict comparison to determine matches. This can lead to some [nasty surprises](http://stackoverflow.com/questions/4098104/odd-behaviour-in-a-switch-statement) . For example, consider the following statement:

![](Image01224.jpg)

This is a very simple statement, and works as expected when $name is a string, but can cause problems otherwise.

For example, if $name is integer 0 , then type-juggling will happen during the comparison. However, it's the literal value in the case statement that gets juggled, not the condition in the switch statement. The string "input 1" is converted to integer 0 which matches the input value of integer 0 . The upshot of this is if you provide a value of integer 0 , the first case always executes.

There are a few solutions to this problem:

Explicit casting

The value can be typecast to a string before comparison:

![](Image01225.jpg)

Or a function known to return a string can also be used:

![](Image01226.jpg)

Both of these methods ensure the value is of the same type as the value in the case statements.

Avoid switch

Using an if statement will provide us with control over how the comparison is done, allowing us to use strict comparison operators:

![](Image01227.jpg)

## Section 56.4: Strict typing

Since PHP 7.0, some of the harmful effects of type juggling can be mitigated with [strict typing](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict) . By including this declare statement as the first line of the file, PHP will enforce parameter type declarations and return type declarations by throwing a TypeError exception.

![](Image01228.jpg)

For example, this code, using parameter type definitions, will throw a catchable exception of type TypeError when run:

![](Image01229.jpg)

Likewise, this code uses a return type declaration; it will also throw an exception if it tries to return anything other than an integer:

![](Image01230.jpg)

  

# Chapter 57: Sockets

## Section 57.1: TCP client socket

Creating a socket that uses the TCP (Transmission Control Protocol)

![](Image01231.jpg) $socket \= socket\_create ( AF\_INET , SOCK\_STREAM , SOL\_TCP );

![](Image01232.jpg) Make sure the socket is successfully created. The onSocketFailure function comes from Handling socket errors example in this topic. if (! is\_resource ( $socket )) onSocketFailure ( "Failed to create socket" ); Connect the socket to a specified address

The second line fails gracefully if connection failed.

socket\_connect ( $socket , "chat.stackoverflow.com" , 6667)

![](Image01233.jpg)         or onSocketFailure ( "Failed to connect to chat.stackoverflow.com:6667" , $socket );

Sending data to the server

The socket\_write function sends bytes through a socket. In PHP, a byte array is represented by a string, which is normally encoding-insensitive.

![](Image01234.jpg)

Receiving data from the server

The following snippet receives some data from the server using the socket\_read function.

Passing PHP\_NORMAL\_READ as the third parameter reads until a \\r / \\n byte, and this byte is included in the return value.

Passing PHP\_BINARY\_READ , on the contrary, reads the required amount of data from the stream.

If socket\_set\_nonblock was called in prior, and PHP\_BINARY\_READ is used, socket\_read will return false immediately. Otherwise, the method blocks until enough data (to reach the length in the second parameter, or to reach a line ending) are received, or the socket is closed.

This example reads data from a supposedly IRC server.

![](Image01235.jpg)

Closing the socket

Closing the socket frees the socket and its associated resources.

![](Image01236.jpg)

## Section 57.2: TCP server socket

Socket creation

Create a socket that uses the TCP. It is the same as creating a client socket.

![](Image01237.jpg)

Socket binding

Bind connections from a given network (parameter 2) for a specific port (parameter 3) to the socket.

The second parameter is usually "0.0.0.0" , which accepts connection from all networks. It can also

![](Image01238.jpg) One common cause of errors from socket\_bind is that [the address specified is already bound to another process](https://www.google.com.hk/search?q=site%3Astackexchange.com%20OR%20site%3Astackoverflow.com%20kill%20processes%20bound%20to%20address) . Other processes are usually killed (usually manually to prevent accidentally killing critical processes) so that the sockets would be freed. socket\_bind ( $socket , "0.0.0.0" , 6667) or onSocketFailure ( "Failed to bind to 0.0.0.0:6667" );

Set a socket to listening

Make the socket listen to incoming connections using socket\_listen . The second parameter is the maximum number of connections to allow queuing before they are accepted. ![](Image01239.jpg)socket\_listen ( $socket , 5); Handling connection

A TCP server is actually a server that handles child connections. socket\_accept creates a new child connection.

![](Image01240.jpg)

Data transferring for a connection from socket\_accept is the same as that for a TCP client socket.

 
| socket\_close || ( || $conn |
| --- | --- | --- |

When this connection should be closed, call ); directly. This will not affect the original TCP server socket.

Closing the server

 
| socket\_close || ( || $socket |
| --- | --- | --- |

On the other hand, ); should be called when the server is no longer used. This will free the TCP address as well, allowing other processes to bind to the address.

## Section 57.3: UDP server socket

A UDP (user datagram protocol) server, unlike TCP, is not stream-based. It is packet-based, i.e. a client sends data in units called "packets" to the server, and the client identifies clients by their address. There is no builtin function that relates different packets sent from the same client (unlike TCP, where data from the same client are handled by a specific resource created by socket\_accept ). It can be thought as a new TCP connection is accepted and closed every time a UDP packet arrives.

Creating a UDP server socket

![](Image01241.jpg)

Binding a socket to an address

The parameters are same as that for a TCP server.

![](Image01242.jpg)$socket );

Sending a packet

This line sends $data in a UDP packet to $address : $port .

![](Image01243.jpg)

Receiving a packet

The following snippet attempts to manage UDP packets in a client-indexed manner.

![](Image01244.jpg)

Closing the server

socket\_close can be used on the UDP server socket resource. This will free the UDP address, allowing other processes to bind to this address.

## Section 57.4: Handling socket errors

socket\_last\_error can be used to get the error ID of the last error from the sockets extension. socket\_strerror can be used to convert the ID to human-readable strings.

![](Image01245.jpg)

# Chapter 58: PDO

The [PDO](http://php.net/manual/en/book.pdo.php) (PHP Data Objects) extension allows developers to connect to numerous different types of databases and execute queries against them in a uniform, object oriented manner.

## Section 58.1: Preventing SQL injection with Parameterized Queries

SQL injection is a kind of attack that allows a malicious user to modify the SQL query, adding unwanted commands to it. For example, the following code is vulnerable :

![](Image01246.jpg)

This allows any user of this script to modify our database basically at will. For example consider the following query string:

![](Image01247.jpg)

This makes our example query look like this

![](Image01248.jpg) SELECT name , email , user\_level FROM users WHERE userID \= 0 ; TRUNCATE TABLE users;

While this is an extreme example (most SQL injection attacks do not aim to delete data, nor do most PHP query execution functions support multi-query), this is an example of how a SQL injection attack can be made possible by the careless assembly of the query. Unfortunately, attacks like this are very common, and are highly effective due to coders who fail to take proper precautions to protect their data.

To prevent SQL injection from occurring, prepared statements are the recommended solution. Instead of concatenating user data directly to the query, a placeholder is used instead. The data is then sent separately, which means there is no chance of the SQL engine confusing user data for a set of instructions.

![](Image01249.jpg)While the topic here is PDO, please note that the PHP MySQLi extension also supports prepared statements

PDO supports two kinds of placeholders (placeholders cannot be used for column or table names, only values):

 
| user |
| --- |

1.    Named placeholders. A colon( : ), followed by a distinct name (eg. : )

// using named placeholders

$sql \= 'SELECT name, email, user\_level FROM users WHERE userID = :user' ;

$prep \= $conn \-> prepare ( $sql );

![](Image01250.jpg) $prep \-> execute (\[ 'user' \=> $\_GET \[ 'user' \]\]); // associative array $result \= $prep \-> fetchAll ();

2.    Traditional SQL positional placeholders, represented as ? :

// using question-mark placeholders

![](Image01251.jpg) $sql \= 'SELECT name, user\_level FROM users WHERE userID = ? AND user\_level = ?' ;

$prep \= $conn \-> prepare ( $sql );

$prep \-> execute (\[ $\_GET \[ 'user' \], $\_GET \[ 'user\_level' \]\]); // indexed array

![](Image01252.jpg)

If ever you need to dynamically change table or column names, know that this is at your own security risks and a bad practice. Though, it can be done by string concatenation. One way to improve security of such queries is to set a table of allowed values and compare the value you want to concatenate to this table.

Be aware that it is important to set connection charset through DSN only, otherwise your application could be prone to an [obscure vulnerability](https://stackoverflow.com/questions/134099/are-pdo-prepared-statements-sufficient-to-prevent-sql-injection/12202218#12202218) if some odd encoding is used. For PDO versions prior to 5.3.6 setting charset

 
| PDO :: ATTR\_EMULATE\_PREPARES |
| --- |

through DSN is not available and thus the only option is to set  attribute to false on the connection right after i t’ s created.

![](Image01253.jpg)

This causes PDO to use the underlying DBM S’ s native prepared statements instead of just emulating it.

However, be aware that PDO will [silently fallback](https://github.com/php/php-src/blob/master/ext/pdo_mysql/mysql_driver.c#L210) to emulating statements that MySQL cannot prepare natively: those that it can are [listed in the manual](http://dev.mysql.com/doc/en/sql-syntax-prepared-statements.html) ( [source](https://stackoverflow.com/questions/134099/are-pdo-prepared-statements-sufficient-to-prevent-sql-injection/12202218#12202218) ).

## Section 58.2: Basic PDO Connection and Retrieval

Since PHP 5.0, [PDO](http://php.net/manual/en/intro.pdo.php) has been available as a database access layer. It is database agnostic, and so the following connection example code should work for any [of its supported databases](http://php.net/manual/en/pdo.drivers.php) simply by changing the DSN.

![](Image01254.jpg)

The [prepare](http://php.net/manual/en/pdo.prepare.php) function creates a PDOStatement object from the query string. The execution of the query and retrieval of the results are performed on this returned object. In case of a failure, the function either returns false or throws an exception (depending upon how the PDO connection was configured).

## Section 58.3: Database Transactions with PDO

Database transactions ensure that a set of data changes will only be made permanent if every statement is successful. Any query or code failure during a transaction can be caught and you then have the option to roll back the attempted changes.

PDO provides simple methods for beginning, committing, and rollbacking back transactions.

![](Image01255.jpg)

During a transaction any data changes made are only visible to the active connection. SELECT statements will return the altered changes even if they are not yet committed to the database.

Note : See database vendor documentation for details about transaction support. Some systems do not support transactions at all. Some support nested transactions while others do not.

Practical Example Using Transactions with PDO

In the following section is demonstrated a practical real world example where the use of transactions ensures the consistency of database.

Imagine the following scenario, let's say you are building a shopping cart for an e-commerce website and you decided to keep the orders in two database tables. One named orders with the fields order\_id , name , address , telephone and created\_at . And a second one named orders\_products with the fields order\_id , product\_id and quantity . The first table contains the metadata of the order while the second one the actual products that have been ordered.

Inserting a new order to the database

To insert a new order into the database you need to do two things. First you need to INSERT a new record inside the orders table that will contain the metadata of the order ( name , address , etc). And then you need to INSERT one record into the orders\_products table, for each one of the products that are included in the order.

You could do this by doing something similar to the following:

![](Image01256.jpg)

This will work great for inserting a new order into the database, until something unexpected happens and for some reason the second INSERT query fails. If that happens you will end up with a new order inside the orders table, which will have no products associated to it. Fortunately, the fix is very simple, all you have to do is to make the queries in the form of a single database transaction.

Inserting a new order into the database with a transaction

To start a transaction using PDO all you have to do is to call the beginTransaction method before you execute any queries to your database. Then you make any changes you want to your data by executing INSERT and / or UPDATE queries. And finally you call the commit method of the PDO object to make the changes permanent. Until you call the commit method every change you have done to your data up to this point is not yet permanent, and can be easily reverted by simply calling the rollback method of the PDO object.

On the following example is demonstrated the use of transactions for inserting a new order into the database, while ensuring the same time the consistency of the data. If one of the two queries fails all the changes will be reverted.

![](Image01257.jpg)

## Section 58.4: PDO: connecting to MySQL/MariaDB server

There are two ways to connect to a MySQL/MariaDB server, depending on your infrastructure.

Standard (TCP/IP) connection

$dsn \= 'mysql:dbname=demo;host=server;port=3306;charset=utf8' ;

$connection \= new \\PDO ( $dsn , $username , $password );

// throw exceptions, when SQL error is caused

![](Image01258.jpg) $connection \-> setAttribute ( \\PDO :: ATTR\_ERRMODE , \\PDO :: ERRMODE\_EXCEPTION );

// prevent emulation of prepared statements

$connection \-> setAttribute ( \\PDO :: ATTR\_EMULATE\_PREPARES , false );

Since PDO was designed to be compatible with older MySQL server versions (which did not have support for prepared statements), you have to explicitly disable the emulation. Otherwise, you will lose the added injection prevention benefits, that are usually granted by using prepared statements.

Another design compromise, that you have to keep in mind, is the default error handling behavior. If not otherwise configured, PDO will not show any indications of SQL errors.

It is strongly recommended setting it to "exception mode", because that gains you additional functionality, when writing persistence abstractions (for example: having an exception, when violating UNIQUE constraint).

Socket connection

$dsn \= 'mysql:unix\_socket=/tmp/mysql.sock;dbname=demo;charset=utf8' ;

$connection \= new \\PDO ( $dsn , $username , $password );

// throw exceptions, when SQL error is caused

![](Image01259.jpg) $connection \-> setAttribute ( \\PDO :: ATTR\_ERRMODE , \\PDO :: ERRMODE\_EXCEPTION );

// prevent emulation of prepared statements

$connection \-> setAttribute ( \\PDO :: ATTR\_EMULATE\_PREPARES , false );

On unix-like systems, if host name is 'localhost' , then the connection to the server is made through a domain socket.

## Section 58.5: PDO: Get number of aected rows by a query

 
| rowCount |
| --- |

We start off with $db , an instance of the PDO class. After executing a query we often want to determine the number of rows that have been affected by it. The () method of the PDOStatement will work nicely:

$query = $db->query("DELETE FROM table WHERE name = 'John'"); $count = $query->rowCount(); echo "Deleted $count rows named John";

NOTE: This method should only be used to determine the number of rows affected by INSERT, DELETE, and UPDATE statements. Although this method may work for SELECT statements as well, it is not consistent across all databases.

## Section 58.6: PDO::lastInsertId()

You may often find the need to get the auto incremented ID value for a row that you have just inserted into your database table. You can achieve this with the lastInsertId() method.

![](Image01260.jpg)

![](Image01261.jpg) $query \= "INSERT INTO foo\_user(pseudo, email) VALUES ('anonymous', 'anonymous@example.com')" ; $query\_success \= $pdo \-> query ( $query );

// 3. Retrieving the last inserted id

$id \= $pdo \-> lastInsertId (); // return value is an integer

In postgresql and oracle, there is the RETURNING Keyword, which returns the specified columns of the currently inserted / modified rows. Here example for inserting one entry:

![](Image01262.jpg)

  

# Chapter 59: PHP MySQLi

The [mysql](http://php.net/manual/en/book.mysqli.php) [i](http://php.net/manual/en/book.mysqli.php) [interface](http://php.net/manual/en/book.mysqli.php) is an improvement (it means "MySQL Improvement extension") of the mysql interface, which was deprecated in version 5.5 and is removed in version 7.0. The mysqli extension, or as it is sometimes known, the MySQL improved extension, was developed to take advantage of new features found in MySQL systems versions

4.1.3 and newer. The mysqli extension is included with PHP versions 5 and later.

## Section 59.1: Close connection

When we are finished querying the database, it is recommended to close the connection to free up resources.

Object oriented style

![](Image01263.jpg)

Procedural style

![](Image01264.jpg)

Note : The connection to the server will be closed as soon as the execution of the script ends, unless it's closed earlier by explicitly calling the close connection function.

Use Case: If our script has a fair amount of processing to perform after fetching the result and has retrieved the full result set, we definitely should close the connection. If we were not to, there's a chance the MySQL server will reach its connection limit when the web server is under heavy use.

## Section 59.2: MySQLi connect

Object oriented style

Connect to Server

![](Image01265.jpg)

 
| $conn \-> select\_db || ( || "my\_db" |
| --- | --- | --- |

Set the default database: );

Connect to Database

![](Image01266.jpg)

Procedural style

Connect to Server

![](Image01267.jpg)

 
| mysqli\_select\_db || ( || $conn || , ||   "my\_db" |
| --- | --- | --- | --- | --- |

Set the default database: );

Connect to Database

![](Image01268.jpg) $conn \= mysqli\_connect ( "localhost" , "my\_user" , "my\_password" , "my\_db" );

Verify Database Connection

Object oriented style

![](Image01269.jpg)

Procedural style

![](Image01270.jpg)

## Section 59.3: Loop through MySQLi results

PHP makes it easy to get data from your results and loop over it using a while statement. When it fails to get the next row, it returns false , and your loop ends. These examples work with

![](Image01271.jpg)[mysqli\_fetch\_assoc](http://php.net/manual/en/mysqli-result.fetch-assoc.php) \- Associative array with column names as keys [mysqli\_fetch\_object](http://php.net/manual/en/mysqli-result.fetch-object.php) \- stdClass object with column names as variables [mysqli\_fetch\_array](http://php.net/manual/en/mysqli-result.fetch-array.php) \- Associative AND Numeric array (can use arguments to get one or the other) [mysqli\_fetch\_row](http://php.net/manual/en/mysqli-result.fetch-row.php) \- Numeric array

Object oriented style

![](Image01272.jpg)

Procedural style

![](Image01273.jpg)

To get exact information from results, we can use:

![](Image01274.jpg)

## Section 59.4: Prepared statements in MySQLi

Please read Preventing SQL injection with Parametrized Queries for a complete discussion of why prepared statements help you secure your SQL statements from SQL Injection attacks

The $conn variable here is a MySQLi object. See MySQLi connect example for more details.

For both examples, we assume that $sql is

![](Image01275.jpg)

The ? represents the values we will provide later. Please note that we do not need quotes for the placeholders, regardless of the type. We can also only provide placeholders in the data portions of the query, meaning SET , VALUES and WHERE . You cannot use placeholders in the SELECT or FROM portions.

Object oriented style

![](Image01276.jpg)

Procedural style

![](Image01277.jpg)

 
| $stmt \-> bind\_param |
| --- |

The first parameter of  or the second parameter of mysqli\_stmt\_bind\_param is determined by the data type of the corresponding parameter in the SQL query:

Parameter Data type of the bound parameter

i integer d double s string b blob

 
| column\_2 || \= || ? || ) is string and the second parameter ( || column\_3 || \> || ? |
| --- | --- | --- | --- | --- | --- | --- |

Your list of parameters needs to be in the order provided in your query. In this example si means the first parameter () is integer.

For retrieving data, see How to get data from a prepared statement

## Section 59.5: Escaping Strings

Escaping strings is an older ( and less secure ) method of securing data for insertion into a query. It works by using [MySQL's function mysql\_real\_escape\_string()](http://dev.mysql.com/doc/refman/5.7/en/mysql-real-escape-string.html) to process and sanitize the data (in other words, PHP is not doing the escaping). The MySQLi API provides direct access to this function

![](Image01278.jpg)

At this point, you have a string that MySQL considers to be safe for use in a direct query

![](Image01279.jpg)

So why is this not as secure as prepared statements? There are ways to trick MySQL to produce a string it considers safe. Consider the following example

![](Image01280.jpg)

 
| OR |
| --- |

11=1 does not represent data that MySQL will escape, yet this still represents SQL injection. There are [other](http://stackoverflow.com/questions/5741187/sql-injection-that-gets-around-mysql-real-escape-string) [examples](http://stackoverflow.com/questions/5741187/sql-injection-that-gets-around-mysql-real-escape-string) as well that represent places where it returns unsafe data. The problem is that MySQL's escaping function is designed to make data comply with SQL syntax . It's NOT designed to make sure that MySQL can't confuse user data for SQL instructions .

## Section 59.6: Debugging SQL in MySQLi

So your query has failed (see MySQLi connect for how we made $conn )

![](Image01281.jpg) $result \= $conn \-> query ( 'SELECT \* FROM non\_existent\_table' ); // This query will fail

How do we find out what happened? $result is false so that's no help. Thankfully the connect $conn can tell us what MySQL told us about the failure

![](Image01282.jpg)

or procedural

![](Image01283.jpg)

You should get an error similar to

![](Image01284.jpg)              Table 'my\_db.non\_existent\_table' doesn't exist

## Section 59.7: MySQLi query

The query function takes a valid SQL string and executes it directly against the database connection $conn Object oriented style

![](Image01285.jpg)

![](Image01286.jpg)

A common problem here is that people will simply execute the query and expect it to work (i.e. return a [mysqli\_stmt object](https://secure.php.net/manual/en/class.mysqli-stmt.php) ). Since this function takes only a string, you're building the query first yourself. If there are any mistakes in the SQL at all, the MySQL compiler will fail, at which point this function will return false .

![](Image01287.jpg) $result \= $conn \-> query ( 'SELECT \* FROM non\_existent\_table' ); // This query will fail

$row \= $result \-> fetch\_assoc ();

The above code will generate a E\_FATAL error because $result is false , and not an object.

![](Image01288.jpg)              PHP Fatal error: Call to a member function fetch\_assoc() on a non-object

The procedural error is similar, but not fatal, because we're just violating the expectations of the function.

![](Image01289.jpg)

You will get the following message from PHP

![](Image01290.jpg)              mysqli\_fetch\_array() expects parameter 1 to be mysqli\_result, boolean given

You can avoid this by doing a test first

![](Image01291.jpg)

## Section 59.8: How to get data from a prepared statement

Prepared statements

See Prepared statements in MySQLi for how to prepare and execute a query.

Binding of results

Object-oriented style

![](Image01292.jpg)

Procedural style

![](Image01293.jpg)

The problem with using bind\_result is that it requires the statement to specify the columns that will be used. This

 
| SELECT forename FROM users |
| --- |

means that for the above to work the query must have looked like this . To include

more columns simply add them as parameters to the bind\_result function (and ensure that you add them to the SQL query).

In both cases, we're assigning the forename column to the $forename variable. These functions take as many arguments as columns you want to assign. The assignment is only done once, since the function binds by reference.

We can then loop as follows:

Object-oriented style

![](Image01294.jpg)

Procedural style

![](Image01295.jpg)

The drawback to this is that you have to assign a lot of variables at once. This makes keeping track of large queries difficult. If you have [MySQL Native Driver (](http://php.net/manual/en/book.mysqlnd.php) [mysqln](http://php.net/manual/en/book.mysqlnd.php) [d](http://php.net/manual/en/book.mysqlnd.php) [)](http://php.net/manual/en/book.mysqlnd.php) installed, all you need to do is use [get\_result](http://php.net/manual/en/mysqli-stmt.get-result.php) . Object-oriented style

![](Image01296.jpg)

Procedural style

![](Image01297.jpg)

This is much easier to work with because now we're getting a [mysqli\_result](http://php.net/manual/en/class.mysqli-result.php) object. This is the same object that mysqli\_query returns. This means you can use a regular result loop to get your data.

What if I cannot install mysqlnd ?

If that is the case then @Sophivorus has you covered with [this amazing answer](http://stackoverflow.com/a/30551477/3578036) .

This function can perform the task of get\_result without it being installed on the server. It simply loops through the results and builds an associative array

![](Image01298.jpg)

 
| mysqli\_fetch\_assoc |
| --- |

We can then use the function to get results like this, just as if we were using ()

![](Image01299.jpg)

It will have the same output as if you were using the mysqlnd driver, except it does not have to be installed. This is very useful if you are unable to install said driver on your system. Just implement this solution.

## Section 59.9: MySQLi Insert ID

Retrieve the last ID generated by an INSERT query on a table with an AUTO\_INCREMENT column.

Object-oriented Style

![](Image01300.jpg)

![](Image01301.jpg)

Insert id when updating rows

 
| INSERT ... ON |
| --- |

 
| DUPLICATE KEY UPDATE |
| --- |

Normally an UPDATE statement does not return an insert id, since an AUTO\_INCREMENT id is only returned when a new row has been saved (or inserted). One way of making updates to the new id is to use  syntax for updating.

Setup for examples to follow:

![](Image01302.jpg)

 
| LAST\_INSERT\_ID |
| --- |

The case of IODKU performing an "update" and () retrieving the relevant id :

![](Image01303.jpg)

 
| LAST\_INSERT\_ID |
| --- |

The case where IODKU performs an "insert" and () retrieves the new id :

![](Image01304.jpg)

Resulting table contents:

![](Image01305.jpg)

  

# Chapter 60: SQLite3

## Section 60.1: SQLite3 Quickstart Tutorial

This is a complete example of all the commonly used SQLite related APIs. The aim is to get you up and running really fast. You can also get a [runnable PHP file](https://gist.github.com/bladeSk/6294d3266370868601a7d2e50285dbf5) of of this tutorial.

Creating/opening a database

 
| sqlite |
| --- |

Let's create a new database first. Create it only if the file doesn't exist and open it for reading/writing. The extension of the file is up to you, but . is pretty common and self-explanatory.

![](Image01306.jpg) $db \= new SQLite3 ( 'analytics.sqlite' , SQLITE3\_OPEN\_CREATE | SQLITE3\_OPEN\_READWRITE ); Creating a table

![](Image01307.jpg)

Inserting sample data.

It's advisable to wrap related queries in a transaction (with keywords BEGIN and COMMIT ), even if you don't care about atomicity. If you don't do this, SQLite automatically wraps every single query in a transaction, which slows down everything immensely. If you're new to SQLite, you may be surprised why the [INSERTs are so slow](http://stackoverflow.com/a/3852082/388994) [ ](http://stackoverflow.com/a/3852082/388994) .

![](Image01308.jpg)

Insert potentially unsafe data with a prepared statement. You can do this with named parameters :

![](Image01309.jpg) $statement \= $db \-> prepare ( 'INSERT INTO "visits" ("user\_id", "url", "time")

    VALUES (:uid, :url, :time)' );

$statement \-> bindValue ( ':uid' , 1337);

$statement \-> bindValue ( ':url' , '/test' );

$statement \-> bindValue ( ':time' , date ( 'Y-m-d H:i:s' ));

$statement \-> execute (); you can reuse the statement with different values

Fetching data

Let's fetch today's visits of user #42. We'll use a prepared statement again, but with numbered parameters this time, which are more concise:

![](Image01310.jpg)

![](Image01311.jpg)

Free the memory - this in not done automatically, while your script is running

![](Image01312.jpg)

Shorthands

Here's a useful shorthand for fetching a single row as an associative array. The second parameter means we want all the selected columns.

Watch out, this shorthand doesn't support parameter binding, but you can escape the strings instead. Always put the values in SINGLE quotes! Double quotes are used for table and column names (similar to backticks in MySQL).

![](Image01313.jpg)

Another useful shorthand for retrieving just one value. ![](Image01314.jpg)echo " \\n " ;

Cleaning up

Finally, close the database. This is done automatically when the script finishes, though.

![](Image01315.jpg)

## Section 60.2: Querying a database

![](Image01316.jpg)

See also http://stackoverflow.com/documentation/sql/topics

## Section 60.3: Retrieving only one result

In addition to using LIMIT SQL statements you can also use the SQLite3 function querySingle to retrieve a single row, or the first column.

<?php

$database \= new SQLite3 ( 'mysqlitedb.db' );

//Without the optional second parameter set to true, this query would return just

//the first column of the first row of results and be of the same type as columnName

$database \-> querySingle ( 'SELECT column1Name FROM table WHERE column2Name=1' );

//With the optional entire\_row parameter, this query would return an array of the //entire first row of query results.

![](Image01317.jpg) $database \-> querySingle ( 'SELECT column1Name, column2Name FROM user WHERE column3Name=1' , true ); ?>

  

# Chapter 61: Using MongoDB

## Section 61.1: Connect to MongoDB

Create a MongoDB connection, that later you can query:

![](Image01318.jpg) $manager \= new \\MongoDB\\Driver\\Manager ( 'mongodb://localhost:27017' );

In the next example, you will learn how to query the connection object.

This extension close the connection automatically, it's not necessary to close manually.

## Section 61.2: Get multiple documents - find()

Example for searching multiple users with the name "Mike":

![](Image01319.jpg)

## Section 61.3: Get one document - findOne()

Example for searching just one user with a specific id, you should do:

![](Image01320.jpg)

## Section 61.4: Insert document

Example for adding a document:

![](Image01321.jpg)

## Section 61.5: Update a document

Example for updating all documents where name is equal to "John":

![](Image01322.jpg)

## Section 61.6: Delete a document

Example for deleting all documents where name is equal to "Peter":

![](Image01323.jpg)

  

# Chapter 62: mongo-php

## Section 62.1: Everything in between MongoDB and Php

Requirements

![](Image01324.jpg)MongoDB server running on port usually 27017. (type mongod on command prompt to run mongodb server)

Php installed as either cgi or fpm with MongoDB extension installed(MongoDB extension is not bundled with default php)

 
| php composer || . || phar require |
| --- | --- | --- |

![](Image01325.jpg)Composer library(mongodb/mongodb).(In the project root run

"mongodb/mongodb=^1.0.0" to install the MongoDB library)

If everything is ok you are ready to move on.

![](Image01326.jpg)              Check For Php installation

 
| php |
| --- |

if not sure check Php installation by running \- v on command prompt will return something like this

 
| PHP 7 || . 0 . || 6 || ( || cli |
| --- | --- | --- | --- | --- |

 
| built || : || Apr 28 2016 14 || : || 12 || : || 14 |
| --- | --- | --- | --- | --- | --- | --- |

 
| ZTS || ) || Copyright || ( c ) ||   1997 || \- || 2016 The PHP Group Zend |
| --- | --- | --- | --- | --- | --- | --- |

![](Image01327.jpg) ![](Image01328.jpg) ) () (

 
| Engine v3 || . 0 . 0 , || Copyright || ( c ) ||   1998 || \- || 2016 Zend Technologies |
| --- | --- | --- | --- | --- | --- | --- |

![](Image01329.jpg)              Check For MongoDB installation

 
| mongo \-- version || will return || MongoDB shell version || : || 3 |
| --- | --- | --- | --- | --- |

Check MongoDB installation by running . 2 . 6

![](Image01330.jpg)              Check For Composer installation

 
| php composer || . || phar \-- version || will return || Composer version 1.2 || \- || dev |
| --- | --- | --- | --- | --- | --- | --- |

Check for Composer installation by running

 
| 3d09c17b489cd29a0c0b3b11e731987e7097797d || ) ||   2016 || \- || 08 || \- || 30 16 || : || 12 || : || 39 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

( \`

Connecting to MongoDB from php

![](Image01331.jpg)

![](Image01332.jpg)

 
| mongodb || / || mongodb || ) included as || vendor || / || autoload || . || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

The above code will connect using MongoDB composer library( to

connect to the MongoDB server running on port : 27017 . If everything is ok it will connect and list an array, if exception occurs connecting to MongoDB server the message will be printed.

CREATE(Inserting) into MongoDB

![](Image01333.jpg)

 
| $result \-> getInsertedId |
| --- |

In the example we are using the $mongo instance previously used in the Connecting to MongoDB from php part. MongoDB uses JSON type data format, so in php we will use array to insert data into MongoDB, this conversion from array to Json and vice versa will be done by mongo library. Every document in MongoDB has a unique id named as \_id,during insertion we can get this by using () ;

READ(Find) in MongoDB

![](Image01334.jpg)

Drop in MongoDB

![](Image01335.jpg)

There are many methods that can be performed on $collection see [Official documentation](http://mongodb.github.io/mongo-php-library/api/index.html) from MongoDB

  

# Chapter 63: Using Redis with PHP

## Section 63.1: Connecting to a Redis instance

Assuming a default server running on localhost with the default port, the command to connect to that Redis server would be:

![](Image01336.jpg)

## Section 63.2: Installing PHP Redis on Ubuntu

To install PHP on Ubuntu, first install the Redis server:

![](Image01337.jpg)

then install the PHP module:

![](Image01338.jpg)

And restart the Apache server:

![](Image01339.jpg)

## Section 63.3: Executing Redis commands in PHP

The Redis PHP module gives access to the same commands as the Redis CLI client so it is quite straightforward to use.

The syntax is as follow:

![](Image01340.jpg)

# Chapter 64: Sending Email

Parameter Details

 
| string $to |
| --- |

The recipient email address

 
| string $subject |
| --- |

The subject line

 
| string $message |
| --- |

The body of the email

 
| string $additional\_headers |
| --- |

Optional: headers to add to the email

 
| string $additional\_parameters |
| --- |

Optional: arguments to pass to the configured mail send application in the command line

## Section 64.1: Sending Email - The basics, more details, and a full example

A typical email has three main components:

1.    A recipient (represented as an email address)

2.    A subject

3.    A message body

 
| mail || () . || mail |
| --- | --- | --- |

Sending mail in PHP can be as simple as calling the built-in function () takes up to five parameters but the first three are all that is required to send an email (although the four parameters is commonly used as will be demonstrated below). The first three parameters are:

1.    The recipient's email address (string)

2.    The email's subject (string)

3.    The body of the email (string) (e.g. the content of the email)

![](Image01341.jpg) A minimal example would resemble the following code: mail ( 'recipient@example.com' , 'Email Subject' , 'This is the email message body' );

 
| mail |
| --- |

The simple example above works well in limited circumstances such as hardcoding an email alert for an internal system. However, it is common to place the data passed as the parameters for () in variables to make the code cleaner and easier to manage (for example, dynamically building an email from a form submission).

 
| mail |
| --- |

Additionally, () accepts a fourth parameter which allows you to have additional mail headers sent with your email. These headers can allow you to set:

 
| Reply || \- || To |
| --- | --- | --- |

the From name and email address the user will see the  email address the user's response will be sent to

 
| Mailer |
| --- |

additional non-standards headers like X \- which can tell the recipient this email was sent via PHP

$to       \= 'recipient@example.com' ;              // Could also be $to      = $\_POST\['recipient'\]; 

![](Image01342.jpg) $subject \= 'Email Subject' ;                      // Could also be $subject = $\_POST\['subject'\];  $message \= 'This is the email message body' ;     // Could also be $message = $\_POST\['message'\];  $headers \= implode ( " \\r\\n " , \[

    'From: John Conde <webmaster@example.com>' ,

    'Reply-To: webmaster@example.com' ,

    'X-Mailer: PHP/' . PHP\_VERSION

\]);

The optional fifth parameter can be used to pass additional flags as command line options to the program configured to be used when sending mail, as defined by the sendmail\_path configuration setting. For example, this can be used to set the envelope sender address when using sendmail/postfix with the \-f sendmail option.

![](Image01343.jpg)

 
| mail || () can be pretty reliable, it is by no means guaranteed that an email will be sent when || mail |
| --- | --- | --- |

Although using () is called. To see if there is a potential error when sending your email, you should capture the return value from

 
| mail |
| --- |

() . TRUE will be returned if the mail was successfully accepted for delivery. Otherwise, you will receive FALSE .

![](Image01344.jpg)

 
| mail |
| --- |

NOTE : Although () may return TRUE , it does not mean the email was sent or that the email will be received by the recipient. It only indicates the mail was successfully handed over to your system's mail system successfully.

If you wish to send an HTML email, there isn't a lot more work you need to do. You need to:

 
| MIME || \- || Version |
| --- | --- | --- |

1.    Add the  header

 
| Content || \- || Type |
| --- | --- | --- |

2.    Add the  header

3.    Make sure your email content is HTML

![](Image01345.jpg)

![](Image01346.jpg)

![](Image01347.jpg)

See Also

Official documentation

 
| [mail](http://php.net/manual/en/function.mail.php) |
| --- |

 
| [mail](http://php.net/manual/en/mail.configuration.php) |
| --- |

![](Image01348.jpg)[(](http://php.net/manual/en/function.mail.php) [)](http://php.net/manual/en/function.mail.php)

[PHP](http://php.net/manual/en/mail.configuration.php) [()](http://php.net/manual/en/mail.configuration.php) [configuration](http://php.net/manual/en/mail.configuration.php)

Related Stack Overflow Questions

![](Image01349.jpg)[PHP mail form doesn't complete sending e-mail](http://stackoverflow.com/q/24644436/250259)

[How do you make sure email you send programmatically is not automatically marked as spam?](http://stackoverflow.com/q/371/250259)

[How to use SMTP to send email](http://stackoverflow.com/questions/15965376/how-to-configure-xampp-to-send-mail-from-localhost/18185233#18185233)

[Setting envelope from address](http://stackoverflow.com/a/5666682/2417031)

Alternative Mailers

![](Image01350.jpg)[PHPMailer](https://github.com/Synchro/PHPMailer)

[SwiftMailer](http://swiftmailer.org/)

[PEAR::Mail](https://pear.php.net/package/Mail)

Email Servers

![](Image01351.jpg)[Mercury Mail (Windows)](http://www.pmail.com/overviews/ovw_mercury.htm)

Related Topics

![](Image01352.jpg)[Post/Redirect/Get](https://en.wikipedia.org/wiki/Post/Redirect/Get)

## Section 64.2: Sending HTML Email Using mail()

![](Image01353.jpg)

![](Image01354.jpg)

This is not much different then sending a plain text email. Thet key differences being the content body is structured like an HTML document and there are two additional headers that must be included so the email client knows to trender the email as HTML. They are:

![](Image01355.jpg)MIME-Version: 1.0

Content-Type: text/html; charset=UTF-8

## Section 64.3: Sending Email With An Attachment Using mail()

![](Image01356.jpg)

![](Image01357.jpg)

Content-Transfer-Encodings

The available encodings are 7bit , 8bit , binary , quoted-printable , base64 , ietf-token , and x-token . Of these encodings, when a header has a multipart Content-Type, the Content-Transfer-Encoding must not be any other value other than 7bit , 8bit , or binary as stated in RFC 2045, section 6.4.

Our example chooses the 7bit encoding, which represents US-ASCII characters, for the multipart header because, as noted in RFC 2045 section 6, some protocols support only this encoding. Data within the boundaries can then be encoded on a part-by-part basis (RFC 2046, section 5.1). This example does exactly this. The first part, which contains the text/plain message, is defined to be 8bit since it may be necessary to support additional characters. In this case, the Latin1 (iso-8859-1) character set is being used. The second part is the attachment and so it is defined as a base64-encoded application/octet-stream. Since base64 transforms arbitrary data into the 7bit range, it can be sent over restricted transports (RFC 2045, section 6.2).

## Section 64.4: Sending Plain Text Email Using PHPMailer

Basic Text Email

![](Image01358.jpg)

![](Image01359.jpg)

Adding addtional recipients, CC recipients, BCC recipients

![](Image01360.jpg)

## Section 64.5: Sending HTML Email Using PHPMailer

![](Image01361.jpg)

![](Image01362.jpg)

## Section 64.6: Sending Email With An Attachment Using PHPMailer

![](Image01363.jpg)

## Section 64.7: Sending Plain Text Email Using Sendgrid

Basic Text Email

![](Image01364.jpg)

Adding addtional recipients, CC recipients, BCC recipients

![](Image01365.jpg)

## Section 64.8: Sending Email With An Attachment Using Sendgrid

![](Image01366.jpg)

# Chapter 65: Using SQLSRV

## Section 65.1: Retrieving Error Messages

When a query goes wrong, it is important to fetch the error message(s) returned by the driver to identify the cause of the problem. The syntax is:

![](Image01367.jpg)

This returns an array with:

Key Description

SQLSTATE The state that the SQL Server / OBDC Driver is in code The SQL Server error code message              The description of the error

It is common to use the above function like so:

![](Image01368.jpg)

## Section 65.2: Fetching Query Results

There are 3 main ways to fetch results from a query: sqlsrv\_fetch\_array()

![](Image01369.jpg)

 
| sqlsrv\_fetch\_array |
| --- |

() has an optional second parameter to fetch back different types of array:

SQLSRV\_FETCH\_ASSOC , SQLSRV\_FETCH\_NUMERIC and SQLSRV\_FETCH\_BOTH (default) can be used; each returns the associative, numeric, or associative and numeric arrays, respectively.

sqlsrv\_fetch\_object()

 
| sqlsrv\_fetch\_object |
| --- |

() retrieves the next row as an object.

![](Image01370.jpg)

sqlsrv\_fetch()

 
| sqlsrv\_fetch () |
| --- |

makes the next row available for reading.

![](Image01371.jpg)

## Section 65.3: Creating a Connection

![](Image01372.jpg)

SQLSRV also has a PDO Driver. To connect using PDO:

![](Image01373.jpg) $conn \= new PDO ( "sqlsrv:Server=localhost,1234;Database=db001" , $dbUser , $dbPassword );

## Section 65.4: Making a Simple Query

![](Image01374.jpg)

Note: the use of square brackets \[\] is to escape the word table as it is a [reserved word](https://msdn.microsoft.com/en-us/library/ms189822.aspx) . These work in the same way as backticks \` do in MySQL .

## Section 65.5: Invoking a Stored Procedure

To call a stored procedure on the server:

![](Image01375.jpg)

![](Image01376.jpg)

## Section 65.6: Making a Parameterised Query

![](Image01377.jpg)

 
| sqlsrv\_prepare () || and || sqlsrv\_execute () |
| --- | --- | --- |

If you plan on using the same query statement more than once, with different parameters, the same can be achieved with the  functions, as shown below:

![](Image01378.jpg)

# Chapter 66: Command Line Interface (CLI)

## Section 66.1: Handling Program Options

 
| getopt () |
| --- |

Program options can be handled with the  function. It operates with a similar syntax to the POSIX getopt command, with additional support for GNU-style long options.

![](Image01379.jpg)

This script can be tested like so:

![](Image01380.jpg)

![](Image01381.jpg)

 
| v |
| --- |

Note the last method will not work because \-5 is not valid.

![](Image01382.jpg)Note: As of PHP 5.3.0, getopt is OS independent, working also on Windows.

## Section 66.2: Argument Handling

Arguments are passed to the program in a manner similar to most C-style languages. $argc is an integer containing the number of arguments including the program name, and $argv is an array containing arguments to the program. The first element of $argv is the name of the program.

![](Image01383.jpg)

 
| php example || . || php foo bar |
| --- | --- | --- |

Calling the above application with  (where example.php contains the above code) will result in the following output:

![](Image01384.jpg)You called the program example.php with 2 arguments

Argument 1 is foo

Argument 2 is bar

Note that $argc and $argv are global variables, not superglobal variables. They must be imported into the local scope using the global keyword if they are needed in a function.

This example shows the how arguments are grouped when escapes such as "" or \\ are used.

Example script

![](Image01385.jpg)

Command line

![](Image01386.jpg)

![](Image01387.jpg)

![](Image01388.jpg)

![](Image01389.jpg)

## Section 66.3: Input and Output Handling

When run from the CLI, the constants STDIN , STDOUT , and STDERR are predefined. These constants are file handles, and can be considered equivalent to the results of running the following commands:

![](Image01390.jpg)

The constants can be used anywhere a standard file handle would be:

![](Image01391.jpg)

 
| php || : || //stdin || , || php || : || //stdout || , and || php || : || //stderr |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

The builtin stream addresses referenced earlier () can be used in place of filenames in most contexts:

![](Image01392.jpg)

![](Image01393.jpg)

As an alternative, you can also use [readline()](http://php.net/manual/en/function.readline.php) for input, and you can also use echo or print or any other string printing functions for output.

![](Image01394.jpg)

## Section 66.4: Return Codes

The exit construct can be used to pass a return code to the executing environment.

![](Image01395.jpg)

 
| exit |
| --- |

By default an exit code of 0 will be returned if none is provided, i.e. exit is the same as (0) . As exit is not a function, parentheses are not required if no return code is being passed.

Return codes must be in the range of 0 to 254 (255 is reserved by PHP and should not be used). By convention, exiting with a return code of 0 tells the calling program that the PHP script ran successfully. Use a non-zero return code to tell the calling program that a specific error condition occurred.

## Section 66.5: Restrict script execution to command line

 
| [php\_sapi\_nam](http://php.net/php_sapi_name) [e](http://php.net/php_sapi_name) |
| --- |

The function [(](http://php.net/php_sapi_name) [)](http://php.net/php_sapi_name) and the constant PHP\_SAPI both return the type of interface ( S erver API ) that is being used by PHP. They can be used to restrict the execution of a script to the command line, by checking whether the output of the function is equal to cli .

![](Image01396.jpg)

 
| [drupal\_is\_cl](https://api.drupal.org/api/drupal/includes!bootstrap.inc/function/drupal_is_cli/7.x) [i](https://api.drupal.org/api/drupal/includes!bootstrap.inc/function/drupal_is_cli/7.x) |
| --- |

The [()](https://api.drupal.org/api/drupal/includes!bootstrap.inc/function/drupal_is_cli/7.x) function is an example of a function that detects whether a script has been executed from the command line:

![](Image01397.jpg)

## Section 66.6: Behavioural dierences on the command line

When running from the CLI, PHP exhibits some different behaviours than when run from a web server. These differences should be kept in mind, especially in the case where the same script might be run from both environments.

 
| require || ( || "./stuff.inc" |
| --- | --- | --- |

![](Image01398.jpg)No directory change When running a script from a web server, the current working directory is always that of the script itself. The code ); assumes the file is in the same directory as the script. On the command line, the current working directory is the directory you're in when you call the script. Scripts that are going to be called from the command line should always use absolute paths. (Note the magic constants \_\_DIR\_\_ and \_\_FILE\_\_ continue to work as expected, and return the location of the script.)

 
| php || . || ini |
| --- | --- | --- |

![](Image01399.jpg)No output buffering The directives output\_buffering and implicit\_flush default to false and

true , respectively. Buffering is still available, but must be explicitly enabled, otherwise output will always be displayed in real time.

 
| php || . || ini |
| --- | --- | --- |

 
| php || . || ini |
| --- | --- | --- |

 
| php || . || ini || can be loaded . When you are using php from cli it can use different || php || . || ini |
| --- | --- | --- | --- | --- | --- | --- |

![](Image01400.jpg)No time limit The  directive max\_execution\_time is set to zero, so scripts will not time out by default.

No HTML errors In the event you have enabled the  directive html\_errors , it will be ignored on the command line.

 
| php \-- ini |
| --- |

Different than web server do. You can know what file is using by running .

## Section 66.7: Running your script

On either Linux/UNIX or Windows, a script can be passed as an argument to the PHP executable, with that script's options and arguments following:

![](Image01401.jpg)

 
| example || . || php |
| --- | --- | --- |

This passes foo and bar as arguments to .

On Linux/UNIX, the preferred method of running scripts is to use a [shebang](https://en.wikipedia.org/wiki/Shebang_\(Unix\)) (e.g. #!/usr/bin/env php ) as the first line of a file, and set the executable bit on the file. Assuming the script is in your path, you can then call it directly:

![](Image01402.jpg)

 
| usr || / || bin || / || env php |
| --- | --- | --- | --- | --- |

 
| usr || / || bin || / || php || or / || usr || / || local || / || bin || / || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

 
| usr || / || bin || / || env |
| --- | --- | --- | --- | --- |

Using / makes the PHP executable to be found using the PATH. Following how PHP is installed, it might not be located at the same place (such as / ), unlike env which is commonly available from / .

On Windows, you could have the same result by adding the PHP's directory and your script to the PATH and editing

 
| php || to be detected using the PATH. Another possibility is to add a file named || example || . || bat |
| --- | --- | --- | --- | --- |

PATHEXT to allow . or

 
| example || . || cmd |
| --- | --- | --- |

in the same directory as your PHP script and write this line into it:

![](Image01403.jpg)

Or, if you added PHP's directory into the PATH, for convenient use:

![](Image01404.jpg)

## Section 66.8: Edge Cases of getopt()

This example shows the behaviour of getopt when the user input is uncommon:

![](Image01405.jpg)

Shell command line

![](Image01406.jpg)

From this example, it can be seen that:

![](Image01407.jpg)Individual options (no colon) always carry a boolean value of false if enabled.

If an option is repeated, the respective value in the output of getopt will become an array.

Required argument options (one colon) accept one space or no space (like optional argument options) as separator

After one argument that cannot be mapped into any options, the options behind will not be mapped either.

## Section 66.9: Running built-in web server

As from version 5.4, PHP comes with built-in server. It can be used to run application without need to install other http server like nginx or apache. Built-in server is designed only in controller environment for development and testing purposes.

It can be run with command php -S :

 
| index || . || php |
| --- | --- | --- |

To test it create  file containing

![](Image01408.jpg)

 
| php || \- || S localhost || : || 8080 |
| --- | --- | --- | --- | --- |

and run command

 
| http || : || //localhost:8080 |
| --- | --- | --- |

Now yout should be able to see content in browser. To check this, navigate to

Every access should result in log entry written to terminal

![](Image01409.jpg)

  

# Chapter 67: Localization

## Section 67.1: Localizing strings with gettext()

 
| php || . || ini |
| --- | --- | --- |

GNU gettext is an extension within PHP that must be included at the : extension=php\_gettext.dll #Windows extension=gettext.so #Linux

The gettext functions implement an NLS (Native Language Support) API which can be used to internationalize your PHP applications.

 
| gettext |
| --- |

Translating strings can be done in PHP by setting the locale, setting up your translation tables and calling () on any string you want to translate.

![](Image01410.jpg)

myPHPApp.po

![](Image01411.jpg)

gettext() loads a given post-complied .po file, a .mo. which maps your to-be translated strings as above.

After this small bit of setup code, translations will now be looked for in the following file:

 
| ./ locale || / || fr\_FR || / || LC\_MESSAGES || / || myPHPApp || . || mo |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

![](Image01412.jpg).

 
| gettext || ( || 'some string' || ) , if 'some string' has been translated in the . || mo |
| --- | --- | --- | --- | --- |

Whenever you call  file, the translation will be returned. Otherwise, 'some string' will be returned untranslated.

![](Image01413.jpg)

# Chapter 68: Headers Manipulation

## Section 68.1: Basic Setting of a Header

Here is a basic setting of the Header to change to a new page when a button is clicked.

![](Image01414.jpg)

?>

# Chapter 69: Coding Conventions

## Section 69.1: PHP Tags

 
| <?php ?> || tags or short-echo tags || <?= ?> || . Other variations (in particular, short tags || <? ?> |
| --- | --- | --- | --- | --- |

You should always use ) should not be used as they are commonly disabled by system administrators.

When a file is not expected to produce output (the entire file is PHP code) the closing ?> syntax should be omitted to avoid unintentional output, which can cause problems when a client parses the document, in particular some browsers fail to recognise the <!DOCTYPE tag and activate [Quirks Mode](https://en.wikipedia.org/wiki/Quirks_mode) .

Example of a simple PHP script:

![](Image01415.jpg)

Example class definition file:

![](Image01416.jpg)

Example of PHP embedded in HTML:

![](Image01417.jpg)

# Chapter 70: Asynchronous programming

## Section 70.1: Advantages of Generators

PHP 5.5 introduces Generators and the yield keyword, which allows us to write asynchronous code that looks more like synchronous code.

 
| Generator :: send () |
| --- |

The yield expression is responsible for giving control back to the calling code and providing a point of resumption at that place. One can send a value along the yield instruction. The return value of this expression is either null or the value which was passed to .

![](Image01418.jpg)

This mechanism can be used by a coroutine implementation to wait for Awaitables yielded by the Generator (by registering itself as a callback for resolution) and continue execution of the Generator as soon as the Awaitable is resolved.

## Section 70.2: Using Icicle event loop

[Icicle](https://github.com/icicleio/icicle) uses Awaitables and Generators to create Coroutines.

![](Image01419.jpg)

![](Image01420.jpg)

## Section 70.3: Spawning non-blocking processes with proc\_open()

PHP has no support for running code concurrently unless you install extensions such as pthread . This can be

 
| [proc\_ope](http://php.net/manual/en/function.proc-open.php) [n](http://php.net/manual/en/function.proc-open.php) || [(](http://php.net/manual/en/function.proc-open.php) [)](http://php.net/manual/en/function.proc-open.php) and || [stream\_set\_blockin](http://php.net/manual/en/function.stream-set-blocking.php) [g](http://php.net/manual/en/function.stream-set-blocking.php) |
| --- | --- | --- |

sometimes bypassed by using [(](http://php.net/manual/en/function.stream-set-blocking.php) [)](http://php.net/manual/en/function.stream-set-blocking.php) and reading their output asynchronously.

 
| [stream\_set\_blocking](http://php.net/manual/en/function.stream-set-blocking.php) |
| --- |

If we split code into smaller chunks we can run it as multiple suprocesses. Then using [(](http://php.net/manual/en/function.stream-set-blocking.php) [)](http://php.net/manual/en/function.stream-set-blocking.php) function we can make each subprocess also non-blocking. This means we can spawn multiple subprocesses and then check for their output in a loop (similarly to an even loop) and wait until all of them finish.

As an example we can have a small subprocess that just runs a loop and in each iteration sleeps randomly for 100 1000ms (note, the delay is always the same for one subprocess).

![](Image01421.jpg)

Then the main process will spawn subprocesses and read their output. We can split it into smaller blocks:

![](Image01422.jpg)

![](Image01423.jpg)

The output then contains mixture from all three subprocesses as they we're read by [fread()](http://php.net/manual/en/function.fread.php) (note, that in this case proc1 ended much earlier than the other two):

![](Image01424.jpg)

## Section 70.4: Reading serial port with Event and DIO

[DIO](http://php.net/manual/en/book.dio.php) streams are currently not recognized by the [Event](http://php.net/manual/en/book.event.php) extension. There is no clean way to obtain the file descriptor encapsulated into the DIO resource. But there is a workaround:

 
| fopen |
| --- |

 
| [stream\_set\_blockin](http://php.net/manual/en/function.stream-set-blocking.php) [g](http://php.net/manual/en/function.stream-set-blocking.php) |
| --- |

 
| [EventUtil](http://php.net/manual/en/function.stream-set-blocking.php) [::](http://php.net/manual/en/function.stream-set-blocking.php) [getSocketFd](http://php.net/manual/en/function.stream-set-blocking.php) |
| --- |

 
| dio\_fdopen |
| --- |

![](Image01425.jpg)open stream for the port with () ;

make the stream non-blocking with [(](http://php.net/manual/en/function.stream-set-blocking.php) [)](http://php.net/manual/en/function.stream-set-blocking.php) ; obtain numeric file descriptor from the stream with [(](http://php.net/manual/en/function.stream-set-blocking.php) [)](http://php.net/manual/en/function.stream-set-blocking.php) ;

pass the numeric file descriptor to () (currently undocumented) and get the DIO resource; add an Event with a callback for listening to the read events on the file descriptor; in the callback drain the available data and process it according to the logic of your application.

dio.php

![](Image01426.jpg)

![](Image01427.jpg)

Testing

Run the following command in terminal A:

$ socat -d -d pty,raw,echo=0 pty,raw,echo=0

2016/12/01 18:04:06 socat\[16750\] N PTY is /dev/pts/5

2016/12/01 18:04:06 socat\[16750\] N PTY is /dev/pts/8

![](Image01428.jpg) 2016/12/01 18:04:06 socat\[16750\] N starting data transfer loop with FDs \[5,5\] and \[7,7\]

 
| dev || / || pts || /5 and / || dev || / || pts |
| --- | --- | --- | --- | --- | --- | --- |

The output may be different. Use the PTYs from the first couple of rows ( //8 , in particular).

In terminal B run the above-mentioned script. You may need root privileges:

![](Image01429.jpg)

In terminal C send a string to the first PTY:

![](Image01430.jpg)

Output:

![](Image01431.jpg)

## Section 70.5: HTTP Client Based on Event Extension

This is a sample HTTP client class based on [Event](https://pecl.php.net/package/event) extension.

The class allows to schedule a number of HTTP requests, then run them asynchronously.

http-client.php

![](Image01432.jpg)

 

 
| \*                       Dispatches all pending requests (events)   \*\*                       @return void   \*/   public function run () {    $this \-> base \-> dispatch ();  }  public function \_\_destruct () {    // Destroy connection objects explicitly, don't wait for GC.    // Otherwise, EventBase may be free'd earlier.    $this \-> connections \= null ;  }  /\*\*\*                       @brief Adds a pending HTTP request   \*\*                       @param string $address Hostname, or IP\*                       @param int $port Port number\*                       @param array $headers Extra HTTP headers\*                       @param int $cmd A EventHttpRequest::CMD\_\* constant\*                       @param string $resource HTTP request resource, e.g. '/page?a=b&c=d'   \*\*                       @return EventHttpRequest|false   \*/   public function addRequest ( $address , $port , array $headers ,     $cmd \= EventHttpRequest :: CMD\_GET , $resource \= '/' )  {    $conn \= new EventHttpConnection ( $this \-> base , null , $address , $port );    $conn \-> setTimeout (5);    $req \= new EventHttpRequest (\[ $this , '\_requestHandler' \], $this \-> base );    foreach ( $headers as $k \=> $v ) {      $req \-> addHeader ( $k , $v , EventHttpRequest :: OUTPUT\_HEADER );     }    $req \-> addHeader ( 'Host' , $address , EventHttpRequest :: OUTPUT\_HEADER );     $req \-> addHeader ( 'Connection' , 'close' , EventHttpRequest :: OUTPUT\_HEADER );     if ( $conn \-> makeRequest ( $req , $cmd , $resource )) {      $this \-> connections \[\]= $conn ;       return $req ;     }    return false ;   }  /\*\*\*                       @brief Handles an HTTP request   \*\*                       @param EventHttpRequest $req\*                       @param mixed $unused   \*\*                       @return void   \*/   public function \_requestHandler ( $req , $unused ) {     if ( is\_null ( $req )) {       echo "Timed out \\n " ;     } else {      $response\_code \= $req \-> getResponseCode ();       if ( $response\_code \== 0) { |
| --- |

![](Image01433.jpg)

test.php

This is a sample script on the server side.

![](Image01434.jpg)

Usage

![](Image01435.jpg)

Sample Output

![](Image01436.jpg)

![](Image01437.jpg)

(Trimmed.)

Note, the code is designed for long-term processing in the [CLI SAPI](http://php.net/manual/en/features.commandline.introduction.php) .

## Section 70.6: HTTP Client Based on Ev Extension

This is a sample HTTP client based on [Ev](https://pecl.php.net/package/ev) extension.

Ev extension implements a simple yet powerful general purpose event loop. It doesn't provide network-specific watchers, but its [I/O watcher](http://docs.php.net/manual/en/class.evio.php) can be used for asynchronous processing of [sockets](http://docs.php.net/manual/en/book.sockets.php) . The following code shows how HTTP requests can be scheduled for parallel processing.

http-client.php

![](Image01438.jpg)

 

 
|     $this \-> http\_client \= $client ;    $this \-> host         \= $host ;    $this \-> resource     \= $resource ;    $this \-> method       \= $method ;    // Get the port for the WWW service    $this \-> service\_port \= getservbyname ( 'www' , 'tcp' );    // Get the IP address for the target host    $this \-> address \= gethostbyname ( $this \-> host );    // Create a TCP/IP socket    $this \-> socket \= socket\_create ( AF\_INET , SOCK\_STREAM , SOL\_TCP );     if (! $this \-> socket ) {       throw new RuntimeException ( "socket\_create() failed: reason: " .        socket\_strerror ( socket\_last\_error ()));     }    // Set O\_NONBLOCK flag     socket\_set\_nonblock ( $this \-> socket );    $this \-> conn\_watcher \= $this \-> http\_client \-> getLoop ()      \-> timer (0, 0., \[ $this , 'connect' \]);  }  public function \_\_destruct () {    $this \-> close ();  }  private function freeWatcher (& $w ) {     if ( $w ) {       $w \-> stop ();      $w \= null ;    }  }  /\*\*\*                       Deallocates all resources of the request   \*/   private function close () {     if ( $this \-> socket ) {      socket\_close ( $this \-> socket );      $this \-> socket \= null ;    }    $this \-> freeWatcher ( $this \-> timeout\_watcher );    $this \-> freeWatcher ( $this \-> read\_watcher );    $this \-> freeWatcher ( $this \-> write\_watcher );     $this \-> freeWatcher ( $this \-> conn\_watcher );  }  /\*\*\*                       Initializes a connection on socket\*                       @return bool   \*/   public function connect () {    $loop \= $this \-> http\_client \-> getLoop ();    $this \-> timeout\_watcher \= $loop \-> timer ( $this \-> timeout , 0., \[ $this , '\_onTimeout' \]);     $this \-> write\_watcher \= $loop \-> io ( $this \-> socket , Ev :: WRITE , \[ $this , '\_onWritable' \]);     return socket\_connect ( $this \-> socket , $this \-> address , $this \-> service\_port ); |
| --- |

 

 
|   }  /\*\*\*                       Callback for timeout (EvTimer) watcher   \*/   public function \_onTimeout ( EvTimer $w ) {    $w \-> stop ();    $this \-> close ();  }  /\*\*\*                       Callback which is called when the socket becomes writable   \*/   public function \_onWritable ( EvIo $w ) {    $this \-> timeout\_watcher \-> stop ();    $w \-> stop ();    $in \= implode ( " \\r\\n " , \[      " {$this->method} {$this->resource} HTTP/1.1" ,      "Host: {$this->host} " ,      'Connection: Close' ,     \]) . " \\r\\n\\r\\n " ;    if (! socket\_write ( $this \-> socket , $in , strlen ( $in ))) {       trigger\_error ( "Failed writing $in to socket" , E\_USER\_ERROR );       return ;     }    $loop \= $this \-> http\_client \-> getLoop ();    $this \-> read\_watcher \= $loop \-> io ( $this \-> socket ,      Ev :: READ , \[ $this , '\_onReadable' \]);    // Continue running the loop    $loop \-> run ();  }  /\*\*   \* Callback which is called when the socket becomes readable    \*/   public function \_onReadable ( EvIo $w ) {    // recv() 20 bytes in non-blocking mode    $ret \= socket\_recv ( $this \-> socket , $out , 20, MSG\_DONTWAIT );    if ( $ret ) {      // Still have data to read. Append the read chunk to the buffer.      $this \-> buffer .= $out ;    } elseif ( $ret \=== 0) {       // All is read       printf ( " \\n <<<< \\n %s \\n \>>>>" , rtrim ( $this \-> buffer ));       fflush ( STDOUT );       $w \-> stop ();       $this \-> close ();       return ;     }    // Caught EINPROGRESS, EAGAIN, or EWOULDBLOCK     if ( in\_array ( socket\_last\_error (), static :: $e\_nonblocking )) {       return ;     }    $w \-> stop ();    $this \-> close (); |
| --- |

![](Image01439.jpg)

Testing

 
| http || : || //my-host.local/test.php |
| --- | --- | --- |

Suppose  script is printing the dump of $\_GET :

![](Image01440.jpg)

 
| php http || \- || client || . || php |
| --- | --- | --- | --- | --- |

Then the output of  command will be similar to the following:

![](Image01441.jpg)

![](Image01442.jpg)

(trimmed)

Note, in PHP 5 the sockets extension may log warnings for EINPROGRESS , EAGAIN , and EWOULDBLOCK errno values. It is possible to turn off the logs with

![](Image01443.jpg)

## Section 70.7: Using Amp event loop

[Amp](https://github.com/amphp/amp/tree/v1.x) harnesses Promises \[another name for Awaitables\] and Generators for coroutine creation.

![](Image01444.jpg)

        // convert to coroutine with Amp\\resolve()

![](Image01445.jpg)         $promise \= Amp\\resolve ( queryStackOverflow ( Dns\\Record :: NS ));         list ( $ns , $type , $ttl ) \= // we need only one NS result, not all             current ( yield Amp\\timeout ( $promise , 2000 /\* milliseconds \*/ ));         echo "The result of the fastest server to reply to our query was $ns " ;

    } catch ( Amp\\TimeoutException $e ) {         echo "We've heard no answer for 2 seconds! Bye!" ;

    } catch ( Dns\\NoRecordException $e ) {         echo "No NS records there? Stupid DNS nameserver!" ;     }

});

  

# Chapter 71: How to Detect Client IP Address

## Section 71.1: Proper use of HTTP\_X\_FORWARDED\_FOR

In the light of the latest [httpoxy](https://httpoxy.org/) vulnerabilities, there is another variable, that is widely misused.

HTTP\_X\_FORWARDED\_FOR is often used to detect the client IP address, but without any additional checks, this can lead to security issues, especially when this IP is later used for authentication or in SQL queries without sanitization.

Most of the code samples available ignore the fact that HTTP\_X\_FORWARDED\_FOR can actually be considered as information provided by the client itself and therefore is not a reliable source to detect clients IP address. Some of the samples do add a warning about the possible misuse, but still lack any additional check in the code itself.

So here is an example of function written in PHP, how to detect a client IP address, if you know that client may be behind a proxy and you know this proxy can be trusted. If you don't known any trusted proxies, you can just use

![](Image01446.jpg)

![](Image01447.jpg)

  

# Chapter 72: Create PDF files in PHP

## Section 72.1: Getting Started with PDFlib

This code requires that you use the [PDFlib library](http://php.net/manual/en/ref.pdf.php) for it to function properly.

![](Image01448.jpg)

# Chapter 73: YAML in PHP

## Section 73.1: Installing YAML extension

YAML does not come with a standard PHP installation, instead it needs to be installed as a PECL extension. On linux/unix it can be installed with a simple

![](Image01449.jpg)

 
| libyaml || \- || dev |
| --- | --- | --- |

Note that  package must be installed on the system, as the PECL package is simply a wrapper around libYAML calls.

Installation on Windows machines is different - you can either download a pre-compiled DLL or build from sources.

## Section 73.2: Using YAML to store application configuration

[YAML](http://www.yaml.org/) provides a way to store structured data. The data can be a simple set of name-value pairs or a complex hierarchical data with values even being arrays.

Consider the following YAML file:

![](Image01450.jpg)

 
| config || . || yaml |
| --- | --- | --- |

Let's say, it's saved as . Then to read this file in PHP the following code can be used:

![](Image01451.jpg)

print\_r will produce the following output:

![](Image01452.jpg)

Now config parameters can be used by simply using array elements:

![](Image01453.jpg)

  

# Chapter 74: Image Processing with GD

## Section 74.1: Image output

 
| [image](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) |
| --- |

An image can be created using [\*](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) [functions](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) , where \* is the file format.

They have this syntax in common:

![](Image01454.jpg)

Saving to a file

If you want to save the image to a file, you can pass the filename, or an opened file stream, as $to . If you pass a stream, you don't need to close it, because GD will automatically close it.

For example, to save a PNG file:

![](Image01455.jpg)

When using fopen , make sure to use the b flag rather than the t flag, because the file is a binary output.

 
| fopen || ( || "php://temp" || , ||   $f || ) or || fopen || ( || "php://memory" || , ||   $f |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Do not try to pass ) to it. Since the stream is closed by the function after the call, you will be unable to use it further, such as to retrieve its contents.

Output as an HTTP response

If you want to directly return this image as the response of the image (e.g. to create dynamic badges), you don't need to pass anything (or pass null ) as the second argument. However, in the HTTP response, you need to specify your content type:

![](Image01456.jpg)

 
| image || / || png || , || image || / || gif |
| --- | --- | --- | --- | --- | --- | --- |

$mimeType is the MIME type of the format you are returning. Examples include  and

 
| image || / || jpeg |
| --- | --- | --- |

.

Writing into a variable

There are two ways to write into a variable.

Using OB (Output Buffering)

![](Image01457.jpg)

Using stream wrappers

You may have many reasons that you don't want to use output buffering. For example, you may already have OB on. Therefore, an alternative is needed.

Using the stream\_wrapper\_register function, a new stream wrapper can be registered. Hence, you can pass a stream to the image output function, and retrieve it later.

![](Image01458.jpg)

In this example, the GlobalStream class writes any input into the reference variable (i.e. indirectly write to the global variable of the given name). The global variable can later be retrieved directly.

There are some special things to note:

![](Image01459.jpg)A fully implemented stream wrapper class should look like [this](http://php.net/manual/en/stream.streamwrapper.example-1.php) , but according to tests with the \_\_call magic method, only stream\_open , stream\_write and stream\_close are called from internal functions.

No flags are required in the fopen call, but you should at least pass an empty string. This is because the fopen function expects such parameter, and even if you don't use it in your stream\_open implementation, a dummy one is still required.

![](Image01460.jpg)According to tests, stream\_write is called multiple times. Remember to use .= (concatenation assignment), not \= (direct variable assignment).

Example usage

 
| <img |
| --- |

![](Image01461.jpg) In the \> HTML tag, an image can be directly provided rather than using an external link: echo '<img src="data:image/png;base64,' . base64\_encode ( $binary ) . '">' ;

## Section 74.2: Creating an image

To create a blank image, use the imagecreatetruecolor function:

![](Image01462.jpg)

$img is now a resource variable for an image resource with $width x $height pixels. Note that width counts from left to right, and height counts from top to bottom.

Image resources can also be created from [image creation functions](http://php.net/manual/en/ref.image.php) , such as:

![](Image01463.jpg)imagecreatefrompng imagecreatefromjpeg

 
| imagecreatefrom |
| --- |

![](Image01464.jpg)other \* functions.

 
| imagedestroy |
| --- |

Image resources may be freed later when there are no more references to them. However, to free the memory immediately (this may be important if you are processing many large images), using () on an image when it is no longer used might be a good practice. ![](Image01465.jpg)imagedestroy ( $image );

Converting an image

Images created by image conversion does not modify the image until you output it. Therefore, an image converter can be as simple as three lines of code:

![](Image01466.jpg)

## Section 74.3: Image Cropping and Resizing

If you have an image and want to create a new image, with new dimensions, you can use imagecopyresampled function: first create a new image with desired dimensions:

![](Image01467.jpg)

 
| createimagefrom |
| --- |

and store the original image into a variable. To do so, you may use one of the \* functions where \* stands for:

![](Image01468.jpg)jpeg

gif

png

string

For example:

![](Image01469.jpg)

Now, copy all (or part of) original image (src\_img) into the new image (dst\_img) by imagecopyresampled :

![](Image01470.jpg)

 
| src\_ || \* and || dst\_ |
| --- | --- | --- |

To set \* dimensions, use the below image:

![](Image01471.jpg)

Now, if you want to copy entire of source (initial) image, into entire of destination area (no cropping):

$src\_x \= $src\_y \= $dst\_x \= $dst\_y \= 0;

$dst\_width \= $width ; // width of new image

$dst\_height \= $height ; //height of new image

$src\_width \= imagesx ( $src\_img ); //width of initial image

![](Image01472.jpg) $src\_height \= imagesy ( $src\_img ); //height of initial image

  

# Chapter 75: Imagick

## Section 75.1: First Steps

Installation

Using apt on Debian based systems

![](Image01473.jpg)

Using Homebrew on OSX/macOs

![](Image01474.jpg)

To see the dependencies installed using the brew method, visit [brewformulas.org/Imagemagick](http://brewformulas.org/Imagemagick) .

Using binary releases

Instructions on [imagemagick website](https://www.imagemagick.org/script/binary-releases.php#macosx) .

Usage

![](Image01475.jpg)

## Section 75.2: Convert Image into base64 String

This example is how to turn an image into a Base64 string (i.e. a string you can use directly in a src attribute of an img tag). This example specifically uses the [Imagick](http://php.net/manual/en/intro.imagick.php) library (there are others available, such as [GD](http://php.net/manual/en/intro.image.php) as well).

![](Image01476.jpg)

![](Image01477.jpg)

  

# Chapter 76: SOAP Server

## Section 76.1: Basic SOAP Server

![](Image01478.jpg)

  

# Chapter 77: Machine learning

## Section 77.1: Classification using PHP-ML

Classification in Machine Learning is the problem that identifies to which set of categories does a new observation belong. Classification falls under the category of Supervised Machine Learning .

![](Image01479.jpg)Any algorithm that implements classification is known as classifier

The classifiers supported in PHP-ML are

![](Image01480.jpg)SVC (Support Vector Classification) k-Nearest Neighbors

Naive Bayes

The train and predict method are same for all classifiers. The only difference would be in the underlying algorithm used.

SVC (Support Vector Classification)

Before we can start with predicting a new observation, we need to train our classifier. Consider the following code

![](Image01481.jpg)

The code is pretty straight forward. $cost used above is a measure of how much we want to avoid misclassifying each training example. For a smaller value of $cost you might get misclassified examples. By default it is set to 1.0

Now that we have the classifier trained we can start making some actual predictions. Consider the following codes that we have for predictions

![](Image01482.jpg)

The classifier in the case above can take unclassified samples and predicts there labels. predict method can take a single sample as well as an array of samples.

k-Nearest Neighbors

The classfier for this algorithm takes in two parameters and can be initialized like

$classifier \= new KNearestNeighbors ( $neighbor\_num \=4);

![](Image01483.jpg) $classifier \= new KNearestNeighbors ( $neighbor\_num \=3, new Minkowski ( $lambda \=4));

$neighbor\_num is the number of nearest neighbours to scan in [knn](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) algorithm while the second parameter is distance metric which by default in first case would be Euclidean . More on Minkowski can be found [here](https://en.wikipedia.org/wiki/Minkowski_distance) . Following is a short example on how to use this classifier

![](Image01484.jpg)

NaiveBayes Classifier

 
| Bayes ' theorem |
| --- |

NaiveBayes Classifier is based on  and does not need any parameters in constructor.

The following code demonstrates a simple prediction implementation

![](Image01485.jpg)

Practical case

Till now we only used arrays of integer in all our case but that is not the case in real life. Therefore let me try to describe a practical situation on how to use classifiers.

 
| mm || , || 10 mm |
| --- | --- | --- |

 
| 10 mm || , || 20 mm |
| --- | --- | --- |

![](Image01486.jpg) ![](Image01487.jpg)Suppose you have an application that stores characteristics of flowers in nature. For the sake of simplicity we can consider the color and length of petals. So there two characteristics would be used to train our data. color is the simpler one where you can assign an int value to each of them and for length, you can have a range like (0)=1 , ()=2 . With the initial data train your classifier. Now one

of your user needs identify the kind of flower that grows in his backyard. What he does is select the color of the flower and adds the length of the petals. You classifier running can detect the type of flower ("Labels in example above")

## Section 77.2: Regression

 
| PHP || \- || ML |
| --- | --- | --- |

In classification using  we assigned labels to new observation. Regression is almost the same with difference being that the output value is not a class label but a continuous value. It is widely used for predictions and forecasting. PHP-ML supports the following regression algorithms

![](Image01488.jpg)Support Vector Regression

LeastSquares Linear Regression

Regression has the same train and predict methods as used in classification.

Support Vector Regression

This is the regression version for SVM(Support Vector Machine).The first step like in classification is to train our model.

![](Image01489.jpg)

In regression $targets are not class labels as opposed to classification. This is one of the differentiating factor for the two. After training our model with the data we can start with the actual predictions

![](Image01490.jpg)

Note that the predictions return a value outside the target.

LeastSquares Linear Regression

This algorithm uses least squares method to approximate solution. The following demonstrates a simple code of training and predicting

![](Image01491.jpg)

PHP-ML also provides with the option of Multiple Linear Regression . A sample code for the same can be as follows

$samples \= \[\[73676, 1996\], \[77006, 1998\], \[10565, 2000\], \[146088, 1995\], \[15000, 2001\], \[65940,

![](Image01492.jpg) 2000\], \[9300, 2000\], \[93739, 1996\], \[153260, 1994\], \[17764, 2002\], \[57000, 1998\], \[15000, 2000\]\];

$targets \= \[2000, 2750, 15500, 960, 4400, 8800, 7100, 2550, 1025, 5900, 4600, 4400\];

$regression \= new LeastSquares ();

$regression \-> train ( $samples , $targets );

$regression \-> predict (\[60000, 1996\]) // return 4094.82

Multiple Linear Regression is particularly useful when multiple factors or traits identify the outcome.

Practical case

Now let us take an application of regression in real life scenario.

![](Image01493.jpg)Suppose you run a very popular website, but the traffic keeps on changing. You want a solution that would predict the number of servers you need to deploy at any given instance of time. Lets assume for the sake that your hosting provider gives you an api to spawn out servers and each server takes 15 minutes to boot. Based on previous data of traffic, and regression you can predict the traffic that would hit your application at any instance of time. Using that knowledge you can start a server 15 minutes before the surge thereby preventing your application from going offline.

## Section 77.3: Clustering

Clustering is about grouping similar objects together. It is widely used for pattern recognition. Clustering comes under unsupervised machine learning , therefore there is no training needed. PHP-ML has support for the following clustering algorithms

![](Image01494.jpg)k-Means dbscan k-Means

k-Means separates the data into n groups of equal variance. This means that we need to pass in a number n which would be the number of clusters we need in our solution. The following code will help bring more clarity

![](Image01495.jpg)

Note that the output contains 3 arrays because because that was the value of n in KMeans constructor. There can also be an optional second parameter in the constructor which would be the initialization method . For example consider

![](Image01496.jpg)

INIT\_RANDOM places a completely random centroid while trying to determine the clusters. But just to avoid the centroid being too far away from the data, it is bound by the space boundaries of data.

The default constructor initialization method is [kmeans++](https://en.wikipedia.org/wiki/K-means%2B%2B) which selects centroid in a smart way to speed up the process.

DBSCAN

As opposed to KMeans , DBSCAN is a density based clustering algorithm which means that we would not be passing n which would determine the number of clusters we want in our result. On the other hand this requires two parameters to work

1.    $minSamples : The minimum number of objects that should be present in a cluster

2.    $epsilon : Which is the maximum distance between two samples for them to be considered as in the same cluster.

A quick sample for the same is as follows

![](Image01497.jpg)

The code is pretty much self explanatory. One major difference is that there is no way of knowing the number of elements in output array as opposed to KMeans.

Practical Case

Let us now have a look on using clustering in real life scenario

![](Image01498.jpg)Clustering is widely used in pattern recognition and data mining . Consider that you have a content publishing application. Now in order to retain your users they should look at content that they love. Let us assume for the sake of simplicity that if they are on a specific webpage for more that a minute and they scoll to bottom then they love that content. Now each of your content will be having a unique identifier with it and so will the user. Make cluster based on that and you will get to know which segment of users have a similar content taste. This in turn could be used in recommendation system where you can assume that if some users of same cluster love the article then so will others and that can be shown as recommendations on your application.

  

# Chapter 78: Cache

## Section 78.1: Caching using memcache

 
| key || \- || value |
| --- | --- | --- |

Memcache is a distributed object caching system and uses  for storing small data. Before you start calling Memcache code into PHP, you need to make sure that it is installed. That can be done using class\_exists method in php. Once it is validated that the module is installed, you start with connecting to memcache server instance.

![](Image01499.jpg)

This will validate that Memcache php-drivers are installed and connect to memcache server instance running on localhost.

![](Image01500.jpg)Memcache runs as a daemon and is called memcached

In the example above we only connected to a single instance, but you can also connect to multiple servers using

![](Image01501.jpg)

Note that in this case unlike connect , there won't be any active connection until you try to store or fetch a value.

In caching there are three important operations that needs to be implemented

1.    Store data : Add new data to memcached server

2.    Get data : Fetch data from memcached server

3.    Delete data : Delete already existing data from memcached server

Store data

$cache or memcached class object has a set method that takes in a key,value and time to save the value for (ttl).

![](Image01502.jpg)

Here $ttl or time to live is time in seconds that you want memcache to store the pair on server.

Get data

$cache or memcached class object has a get method that takes in a key and returns the corresponding value.

![](Image01503.jpg)

Delete data

Sometimes you might have the need to delete some cache value. $cache or memcache instance has a delete method that can be used for the same.

![](Image01504.jpg)

Small scenario for caching

Let us assume a simple blog. It will be having multiple posts on landing page that get fetched from database with each page load. In order to reduce the sql queries we can use memcached to cache the posts. Here is a very small implementation

![](Image01505.jpg)

## Section 78.2: Cache Using APC Cache

The Alternative PHP Cache (APC) is a free and open opcode cache for PHP. Its goal is to provide a free, open, and robust framework for caching and optimizing PHP intermediate code. [installation](http://php.net/manual/en/apc.installation.php)

![](Image01506.jpg)

Add Cache:

![](Image01507.jpg)

Delete Cache:

![](Image01508.jpg)

Set Cache Example:

![](Image01509.jpg)

![](Image01510.jpg)

[Performance](http://stackoverflow.com/questions/1794342/memcache-vs-apc-for-a-single-server-site-data-caching) :

APC is nearly [5 times](https://www.percona.com/blog/2006/09/27/apc-or-memcached/) faster than Memcached.

  

# Chapter 79: Autoloading Primer

## Section 79.1: Autoloading as part of a framework solution

![](Image01511.jpg)

Thanks to our generic autoloader, we have access to any class that follows our autoloader naming convention. In this example, our convention is simple: the desired class must have a file in the same directory named for the class and ending in ".php". Notice that the class name exactly matches the file name.

Without autoloading, we would have to manually require base classes. If we built an entire zoo of animals, we'd have thousands of require statements that could more easily be replaced with a single autoloader.

In the final analysis, PHP autoloading is a mechanism to help you write less mechanical code so you can focus on solving business problems. All you have to do is define a strategy that maps class name to file name . You can roll your own autoloading strategy, as done here. Or, you can use any of the standard ones the PHP community has adopted: [PSR-0](http://www.php-fig.org/psr/psr-0/) or [PSR-4](http://www.php-fig.org/psr/psr-4/) . Or, you can use [composer](http://www.getcomposer.org/) to generically define and manage these dependencies.

## Section 79.2: Inline class definition, no loading required

![](Image01512.jpg)

![](Image01513.jpg)

 
| new Animal |
| --- |

PHP knows what Animal is before executing , because PHP reads source files top-to-bottom. But what if we wanted to create new Animals in many places, not just in the source file where it's defined? To do that, we need to load the class definition.

## Section 79.3: Manual class loading with require

![](Image01514.jpg)

Here we have three files. One file ("Animal.php") defines the class. This file has no side effects besides defining the class and neatly keeps all the knowledge about an "Animal" in one place. It's easily version controlled. It's easily reused.

 
| new Animal |
| --- |

Two files consume the "Animal.php" file by manually require \-ing the file. Again, PHP reads source files top-tobottom, so the require goes and finds the "Animal.php" file and makes the Animal class definition available before calling .

 
| new Animal |
| --- |

Now imagine we had dozens or hundreds of cases where we wanted to perform . That would require (pun-intended) many, many require statements that are very tedious to code.

## Section 79.4: Autoloading replaces manual class definition loading

![](Image01515.jpg)

![](Image01516.jpg)

 
| require "Animal.php" |
| --- |

Compare this to the other examples. Notice how  was replaced with require

"autoload.php" . We're still including an external file at run-time, but rather than including a specific class definition we're including logic that can include any class. It's a level of indirection that eases our development. Instead of writing one require for every class we need, we write one require for all classes. We can replace N require with 1 require .

The magic happens with [spl\_autoload\_register](http://php.net/manual/en/function.spl-autoload-register.php) . This PHP function takes a closure and adds the closure to a queue of closures. When PHP encounters a class for which it has no definition, PHP hands the class name to each closure in the queue. If the class exists after calling a closure, PHP returns to its previous business. If the class fails to exist after trying the entire queue, PHP crashes with "Class 'Whatever' not found."

## Section 79.5: Autoloading with Composer

 
| vendor || / || autoload || . || php |
| --- | --- | --- | --- | --- |

Composer generates a  file.

You might simply include this file and you will get autoloading for free.

 
| require \_\_DIR\_\_ || . ||   '/vendor/autoload.php' |
| --- | --- | --- |

;

This makes working with third-party dependencies very easy.

 
| composer || . || json |
| --- | --- | --- |

You can also add your own code to the Autoloader by adding an autoload section to your .

![](Image01517.jpg)

In this section you define the autoload mappings. In this example its a [PSR-4](http://www.php-fig.org/psr/psr-4/) mapping of a namespace to a

 
| src || directory resides in your projects root folder, on the same level as the / || vendor |
| --- | --- | --- |

 
| src || / || Foo || . || php |
| --- | --- | --- | --- | --- |

directory: the / directory is. An example filename would be  containing an YourApplicationNamespace\\Foo class.

 
| [dump](https://getcomposer.org/doc/03-cli.md#dump-autoload) || [\-](https://getcomposer.org/doc/03-cli.md#dump-autoload) || [autoload](https://getcomposer.org/doc/03-cli.md#dump-autoload) |
| --- | --- | --- |

 
| vendor || / || autoload || . || php |
| --- | --- | --- | --- | --- |

Important: After adding new entries to the autoload section, you have to re-run the command  to re-generate and update the  file with the new information.

 
| PSR || \-4 autoloading, Composer also supports || PSR |
| --- | --- | --- |

In addition to \-0 , classmap and files autoloading. See the [autoload reference](https://getcomposer.org/doc/04-schema.md#autoload) for more information.

 
| vendor || / || autoload || . || php |
| --- | --- | --- | --- | --- |

When you including the / file it will return an instance of the Composer Autoloader. You might store the return value of the include call in a variable and add more namespaces. This can be useful for autoloading classes in a test suite, for example.

![](Image01518.jpg)

# Chapter 80: SPL data structures

## Section 80.1: SplFixedArray

Difference from PHP Array

PHP's default Array type is actually implemented as ordered hash maps, which allow us to create arrays that consist of key/value pairs where values can be of any type and keys can be either numbers or strings. This is not traditionally how arrays are created, however.

![](Image01519.jpg)

So as you can see from this illustration a normal PHP array can be viewed more like an an ordered set of key/value pairs, where each key can map to any value. Notice in this array we have keys that are both numbers and strings, as well as values of different types and the key has no bearing on the order of the elements.

![](Image01520.jpg)

![](Image01521.jpg)

So the above code would give us exactly what we'd expect.

9 => foo 1 => 4.2 bar =>

Regular PHP arrays are also dynamically sized for us. They grow and shrink as we push and pop values to and from the array, automatically.

However, in a traditional array the size is fixed and consists entirely of the same type of value. Also, rather than keys each value is access by its index, which can be deduced by its offset in the array.

![](Image01522.jpg)

 
| type size || \* || n |
| --- | --- | --- |

Since we would know the size of a given type and the fixed size of the array an offset is then the

 
| $arr |
| --- |

 
| $arr |
| --- |

were n represents the value's position in the array. So in the example above \[0\] gives us 1 , the first element in the array and \[1\] gives us 2 , and so on.

SplFixedArray, however, doesn't restrict the type of values. It only restricts the keys to number types. It's also of a fixed size.

This makes SplFixedArrays more efficient than normal PHP arrays in one particular way. They are more compact so they require less memory.

Instantiating the array

 
| count || ( || $arr |
| --- | --- | --- |

 
| foreach || ( || $arr as $k \=> $v |
| --- | --- | --- |

SplFixedArray is implemented as an object, but it can be accessed with the same familiar syntax that you access a normal PHP array since they implement the ArrayAccess interface. They also implement Countable and Iterator interfaces so they behave the same way you'd be used to arrays behaving in PHP (i.e. things like ) and ) work the same way for SplFixedArray as they do normal arrays in PHP.

The SplFixedArray constructor takes one argument, which is the size of the array.

![](Image01523.jpg)

![](Image01524.jpg)

This gives you what you would expect.

0 => foo 1 => bar 2 => baz 3 => This also works as expected.

![](Image01525.jpg)

Gives us...

int(4)

Notice in SplFixedArray, unlike a normal PHP Array, the key does depict the order of the element in our array, because it is a true index and not just a map .

Resizing the array

 
| unset || ( || $arr || \[1\]) will result in || $arr || \[1\] ||   \=== null || , || count || ( || $arr |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Just keep in mind that because the array is of a fixed size, count will always return the same value. So while ) still remains 4 .

So to resize the array you will need to call on the setSize method.

![](Image01526.jpg)

Now we get... int(3) 0 => foo 1 => 2 => baz Import to SplFixedArray & Export from SplFixedArray

You can also import/export a normal PHP Array into and out of an SplFixedArray with the fromArray and toArray methods.

![](Image01527.jpg)

1 2 3 4 5

Going the other way.

![](Image01528.jpg)

![](Image01529.jpg)

1 2 3 4 5

  

# Chapter 81: IMAP

## Section 81.1: Connecting to a mailbox

To do anything with an IMAP account you need to connect to it first. To do this you need to specify some required parameters:

The server name or IP address of the mail server

![](Image01530.jpg) The port you wish to connect on

IMAP is 143 or 993 (secure)

POP is 110 or 995 (secure)

SMTP is 25 or 465 (secure)

NNTP is 119 or 563 (secure)

Connection flags (see below)

 
| Flag || Description || Options imap, || Default |
| --- | --- | --- | --- |

 
| service || \= || service |
| --- | --- | --- |

/ Which service to use pop3, imap

nntp, smtp

 
| user || \= || user |
| --- | --- | --- |

/ remote user name for login on the server

 
| authuser || \= || user |
| --- | --- | --- |

remote authentication user; if specified this is the user name whose

/

password is used (e.g. administrator)

/ anonymous remote access as anonymous user

/ debug record protocol telemetry in application's debug log disabled

/ secure do not transmit a plaintext password over the network

/ norsh do not use rsh or ssh to establish a preauthenticated IMAP session

/ ssl use the Secure Socket Layer to encrypt the session

 
| validate || \- || cert |
| --- | --- | --- |

/ certificates from TLS/SSL server enabled

 
| novalidate || \- || cert |
| --- | --- | --- |

do not validate certificates from TLS/SSL server, needed if server uses self-

/ disabled

signed certificates. USE WITH CAUTION force use of start-TLS to encrypt the session, and reject connection to

/ tls servers that do not support it do not do start-TLS to encrypt the session, even with servers that support

/ notls it

request read-only mailbox open (IMAP only; ignored on NNTP, and an

/ readonly error with SMTP and POP3)

Your connection string will look something like this:

![](Image01531.jpg)

Please note that if any of the characters in your connection string is non-ASCII it must be encoded with [utf7\_encode($string)](https://php.net/manual/en/function.imap-utf7-encode.php) .

To connect to the mailbox, we use the [imap\_open](https://secure.php.net/manual/en/function.imap-open.php) command which returns a resource value pointing to a stream:

![](Image01532.jpg)

## Section 81.2: Install IMAP extension

To use the [IMAP functions](http://www.php.net/imap) in PHP you'll need to install the IMAP extension:

Debian/Ubuntu with PHP5

![](Image01533.jpg)

Debian/Ubuntu with PHP7

![](Image01534.jpg)

YUM based distro

![](Image01535.jpg)

Mac OS X with php5.6

![](Image01536.jpg)

## Section 81.3: List all folders in the mailbox

Once you've connected to your mailbox, you'll want to take a look inside. The first useful command is [imap\_list](https://secure.php.net/manual/en/function.imap-list.php) . The first parameter is the resource you acquired from imap\_open , the second is your mailbox string and the third is a fuzzy search string ( \* is used to match any pattern).

![](Image01537.jpg)

The output should look similar to this

![](Image01538.jpg)

You can use the third parameter to filter these results like this:

![](Image01539.jpg) $folders \= imap\_list ( $mailbox , "{imap.example.com:993/imap/tls/secure}" , "\*.Sent" );

 
| Sent |
| --- |

And now the result only contains entries with . in the name:

![](Image01540.jpg)

Note : Using \* as a fuzzy search will return all matches recursively. If you use % it will return only matches in the current folder specified.

## Section 81.4: Finding messages in the mailbox

You can return a list of all the messages in a mailbox using [imap\_headers](https://secure.php.net/manual/en/function.imap-headers.php) .

![](Image01541.jpg)

The result is an array of strings with the following pattern:

![](Image01542.jpg) \[ FLAG \] \[ MESSAGE \- ID \])\[ DD \- MM \- YYY \] \[ FROM ADDRESS \] \[ SUBJECT TRUNCATED TO 25 CHAR \] (\[ SIZE \] chars ) Here's a sample of what each line could look like:

A     1)19- Aug \-2016 someone @ example . com Message Subject (1728 chars )

D     2)19- Aug \-2016 someone @ example . com RE : Message Subject (22840 chars )

U     3)19- Aug \-2016 someone @ example . com RE : RE : Message Subject (1876 chars )

![](Image01543.jpg) N     4)19- Aug \-2016 someone @ example . com RE : RE : RE : Message Subje (1741 chars )

Symbol Flag Meaning

A Answered Message has been replied to

 
| D || Deleted || Message is deleted (but not removed) |
| --- | --- | --- |
| F || Flagged || Message is flagged/stared for attention |
| N || New || Message is new and has not been seen |
| R || Recent || Message is new and has been seen |
| U || Unread || Message has not been read |
| X || Draft || Message is a draft |

Note that this call could take a fair amount of time to run and may return a very large list.

 
| [imap\_num\_ms](https://secure.php.net/manual/en/function.imap-num-msg.php) [g](https://secure.php.net/manual/en/function.imap-num-msg.php) || [(](https://secure.php.net/manual/en/function.imap-num-msg.php) || [$mailbox](https://secure.php.net/manual/en/function.imap-num-msg.php) |
| --- | --- | --- |

An alternative is to load individual messages as you need them. Your emails are each assigned an ID from 1 (the oldest) to the value of [)](https://secure.php.net/manual/en/function.imap-num-msg.php) .

There are a number of functions to access an email directly, but the simplest way is to use [imap\_header](https://secure.php.net/manual/en/function.imap-header.php) which returns structured header information:

![](Image01544.jpg)

![](Image01545.jpg)

# Chapter 82: HTTP Authentication

In this topic we gonna make a HTTP-Header authenticate script.

## Section 82.1: Simple authenticate

PLEASE NOTE: ONLY PUT THIS CODE IN THE HEADER OF THE PAGE, OTHERWISE IT WILL NOT WORK!

![](Image01546.jpg)

  

# Chapter 83: WebSockets

Usage of socket extension implements a low-level interface to the socket communication functions based on the popular BSD sockets, providing the possibility to act as a socket server as well as a client.

## Section 83.1: Simple TCP/IP server

Minimal example based on PHP manual example found here: [http://php.net/manual/en/sockets.examples.php](http://php.net/manual/en/sockets.examples.php)

 
| telnet 127 || . 0 . 0 . || 1 5000 |
| --- | --- | --- |

Create a websocket script that listens to Port 5000 Use putty, terminal to run  (localhost).

This script replies with the message you sent (as a ping-back)

![](Image01547.jpg)

![](Image01548.jpg)

  

# Chapter 84: BC Math (Binary Calculator)

bcadd Add two arbitrary precision numbers. left\_operand The left operand, as a string. right\_operand The right operand, as a string. scale              A optional parameter to set the number of digits after the decimal place in the result. bccomp              Compare two arbitrary precision numbers. left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

A optional parameter to set the number of digits after the decimal place which will be used in the

scale

comparison.

bcdiv Divide two arbitrary precision numbers. left\_operand The left operand, as a string. right\_operand The right operand, as a string.

 
| scale || A optional parameter to set the number of digits after the decimal place in the result. |
| --- | --- |
| bcmod || Get modulus of an arbitrary precision number. |
| left\_operand || The left operand, as a string. |
| modulus || The modulus, as a string. |
| bcmul || Multiply two arbitrary precision numbers. |
| left\_operand || The left operand, as a string. |

right\_operand The right operand, as a string. scale A optional parameter to set the number of digits after the decimal place in the result. bcpow              Raise an arbitrary precision number to another. left\_operand The left operand, as a string. right\_operand The right operand, as a string. scale              A optional parameter to set the number of digits after the decimal place in the result. bcpowmod              Raise an arbitrary precision number to another, reduced by a specified modulus. left\_operand The left operand, as a string. right\_operand The right operand, as a string.

 
| modulus || The modulus, as a string. |
| --- | --- |
| scale || A optional parameter to set the number of digits after the decimal place in the result. |
| bcscale || Set default scale parameter for all bc math functions. |
| scale || The scale factor. |
| bcsqrt || Get the square root of an arbitrary precision number. |
| operand || The operand, as a string. |
| scale || A optional parameter to set the number of digits after the decimal place in the result. |
| bcsub || Subtract one arbitrary precision number from another. |

left\_operand The left operand, as a string. right\_operand The right operand, as a string. scale A optional parameter to set the number of digits after the decimal place in the result.

The Binary Calculator can be used to calculate with numbers of any size and precision up to 2147483647-1 decimals, in string format. The Binary Calculator is more precise than the float calculation of PHP.

## Section 84.1: Using bcmath to read/write a binary long on 32bit system

On 32-bit systems, integers greater than 0x7FFFFFFF cannot be stored primitively, while integers between

0x0000000080000000 and 0x7FFFFFFFFFFFFFFF can be stored primitively on 64-bit systems but not 32-bit systems ( signed long long ). However, since 64-bit systems and many other languages support storing signed long long integers, it is sometimes necessary to store this range of integers in exact value. There are several ways to do so, such as creating an array with two numbers, or converting the integer into its decimal human-readable form. This has several advantages, such as the convenience in presenting to the user, and the ability to manipulate it with bcmath directly.

The [pack](https://php.net/pack) / [unpack](https://php.net/unpack) methods can be used to convert between binary bytes and decimal form of the numbers (both of type string , but one is binary and one is ASCII), but they will always try to cast the ASCII string into a 32-bit int on 32-bit systems. The following snippet provides an alternative:

/\*\* Use pack("J") or pack("p") for 64-bit systems \*/ function writeLong ( string $ascii ) : string {     if ( bccomp ( $ascii , "0" ) \=== \-1) { // if $ascii < 0

        // 18446744073709551616 is equal to (1 << 64)

        // remember to add the quotes, or the number will be parsed as a float literal

        $ascii \= bcadd ( $ascii , "18446744073709551616" );

    }

![](Image01549.jpg)     // "n" is big-endian 16-bit unsigned short. Use "v" for small-endian.     return pack ( "n" , bcmod ( bcdiv ( $ascii , "281474976710656" ), "65536" )) .         pack ( "n" , bcmod ( bcdiv ( $ascii , "4294967296" ), "65536" )) .         pack ( "n" , bcdiv ( $ascii , "65536" ), "65536" )) .

        pack ( "n" , bcmod ( $ascii , "65536" )); }

function readLong ( string $binary ) : string {     $result \= "0" ;

    $result \= bcadd ( $result , unpack ( "n" , substr ( $binary , 0, 2)));

    $result \= bcmul ( $result , "65536" );

    $result \= bcadd ( $result , unpack ( "n" , substr ( $binary , 2, 2)));

    $result \= bcmul ( $result , "65536" );

    $result \= bcadd ( $result , unpack ( "n" , substr ( $binary , 4, 2)));

    $result \= bcmul ( $result , "65536" );

    $result \= bcadd ( $result , unpack ( "n" , substr ( $binary , 6, 2)));

    // if $binary is a signed long long

    // 9223372036854775808 is equal to (1 << 63) (note that this expression actually does not work even on 64-bit systems)     if ( bccomp ( $result , "9223372036854775808" ) !== \-1) { // if $result >= 9223372036854775807

        $result \= bcsub ( $result , "18446744073709551616" ); // $result -= (1 << 64)

    }     return $result ; }

## Section 84.2: Comparison between BCMath and float arithmetic operations

bcadd vs float+float

![](Image01550.jpg) var\_dump ( '10' + '-9.99' );            // float(0.0099999999999998) var\_dump (10 + \- 9.99 );                // float(0.0099999999999998) var\_dump ( 10.00 + \- 9.99 );             // float(0.0099999999999998) var\_dump ( bcadd ( '10' , '-9.99' , 20)); // string(22) "0.01000000000000000000" bcsub vs float-float

![](Image01551.jpg) var\_dump ( '10' \- '9.99' );            // float(0.0099999999999998) var\_dump (10 \- 9.99 );                // float(0.0099999999999998) var\_dump ( 10.00 \- 9.99 );             // float(0.0099999999999998) var\_dump ( bcsub ( '10' , '9.99' , 20)); // string(22) "0.01000000000000000000"

bcmul vs int\*int

![](Image01552.jpg) var\_dump ( '5.00' \* '2.00' );             // float(10) var\_dump ( 5.00 \* 2.00 );                 // float(10) var\_dump ( bcmul ( '5.0' , '2' , 20));       // string(4) "10.0" var\_dump ( bcmul ( '5.000' , '2.00' , 20)); // string(8) "10.00000" var\_dump ( bcmul ( '5' , '2' , 20));         // string(2) "10"

bcmul vs float\*float

![](Image01553.jpg) var\_dump ( '1.6767676767' \* '1.6767676767' );            // float(2.8115498416259) var\_dump ( 1.6767676767 \* 1.6767676767 );                // float(2.8115498416259) var\_dump ( bcmul ( '1.6767676767' , '1.6767676767' , 20)); // string(22) "2.81154984162591572289"

bcdiv vs float/float

![](Image01554.jpg) var\_dump ( '10' / '3.01' );            // float(3.3222591362126) var\_dump (10 / 3.01 );                // float(3.3222591362126) var\_dump ( 10.00 / 3.01 );             // float(3.3222591362126) var\_dump ( bcdiv ( '10' , '3.01' , 20)); // string(22) "3.32225913621262458471"

  

# Chapter 85: Docker deployment

[Docker](http://www.docker.com/) is a very popular container solution being used widely for deploying code in production environments. It makes it easier to Manage and Scale web-applications and microservices.

## Section 85.1: Get docker image for php

In order to deploy the application on docker, first we need to get the image from registry.

![](Image01555.jpg)

 
| php || : || 7.0 || \- || apache |
| --- | --- | --- | --- | --- |

This will get you the latest version of image from official php repository . Generally speaking, PHP is usually used to deploy web-applications so we need an http server to go with the image.  image comes preinstalled with apache to make deployment hastle free.

## Section 85.2: Writing dockerfile

Dockerfile is used to configure the custom image that we will be building with the web-application codes. Create a new file Dockerfile in the root folder of project and then put the following contents in the same

![](Image01556.jpg)

The first line is pretty straight forward and is used to describe which image should be used to build out new image. The same could be changed to any other specific version of PHP from the registry.

 
| php || . || ini |
| --- | --- | --- |

Second line is simply to upload  file to our image. You can always change that file to some other custom file location.

 
| var || / || www || / || html |
| --- | --- | --- | --- | --- |

The third line would copy the codes in current directory to / which is our webroot. Remember

 
| var || / || www || / || html |
| --- | --- | --- | --- | --- |

/ inside the image.

The last line would simply open up port 80 inside the docker container.

Ignoring files

 
| env |
| --- |

In some instances there might be some files that you don't want on server like environment configuration etc. Let us assume that we have our environment in . . Now in order to ignore this file, we can simply add it to . dockerignore in the root folder of our codebase.

## Section 85.3: Building image

Building image is not something specific to php , but in order to build the image that we described above, we can simply use

![](Image01557.jpg)

Once the image is built, you can verify the same using

![](Image01558.jpg)

Which would list out all the images installed in your system.

## Section 85.4: Starting application container

Once we have an image ready, we can start and serve the same. In order to create a container from the image, use

![](Image01559.jpg)

 
| p 80 || : || 80 |
| --- | --- | --- |

In the command above \- would forward port 80 of your server to port 80 of the container. The flag \-d tells that the container should run as background job. The final specifies which image should be used to build the container.

Checking container

In order to check running containers, simply use

![](Image01560.jpg)

This will list out all the containers running on docker daemon.

Application logs

Logs are very important to debug the application. In order to check on them use

![](Image01561.jpg)

  

# Chapter 86: APCu

APCu is a shared memory key-value store for PHP. The memory is shared between PHP-FPM processes of the same pool. Stored data persists between requests.

## Section 86.1: Iterating over Entries

The [APCUIterator](http://php.net/manual/en/class.apcuiterator.php) allows to iterate over entries in the cache:

![](Image01562.jpg)

The iterator can be initialized with an optional regular expression to select only entries with matching keys:

![](Image01563.jpg)

Information about a single cache entry can be obtained via:

![](Image01564.jpg)

## Section 86.2: Simple storage and retrieval

[apcu\_store](http://php.net/manual/de/function.apcu-store.php) can be used to store, [apcu\_fetch](http://php.net/manual/de/function.apcu-fetch.php) to retrieve values:

![](Image01565.jpg)

## Section 86.3: Store information

[apcu\_cache\_info](http://php.net/manual/en/function.apcu-cache-info.php) provides information about the store and its entries:

![](Image01566.jpg)

# Chapter 87: PHP Built in server

Column Column

\-S Tell the php that we want a webserver

<hostname>:<port> The host name and the por to be used

\-t Public directory

<filename> The routing script

Learn how to use the built in server to develop and test your application without the need of other tools like xamp, wamp, etc.

## Section 87.1: Running the built in server

 
| php || \- || S localhost || : || 80 |
| --- | --- | --- | --- | --- |

![](Image01567.jpg)PHP 7.1.7 Development Server started at Fri Jul 14 15:11:05 2017

Listening on http://localhost:80 Document root is C:\\projetos\\repgeral Press Ctrl-C to quit.

This is the simplest way to start a PHP server that responds to request made to localhost at the port 80.

The -S tells that we are starting a webserver.

The localhost:80 indicates the host that we are answering and the port. You can use other combinations like:

![](Image01568.jpg)mymachine:80 - will listen on the address mymachine and port 80;

127.0.0.1:8080 - will listen on the address 127.0.0.1 and port 8080;

## Section 87.2: built in server with specific directory and router script

 
| php || \- || S localhost || : || 80 || \- || t project || / || public router || . || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

![](Image01569.jpg)PHP 7.1.7 Development Server started at Fri Jul 14 15:22:25 2017

Listening on http://localhost:80 Document root is /home/project/public Press Ctrl-C to quit.

# Chapter 88: PSR

The [PSR](http://www.php-fig.org/psr/) (PHP Standards Recommendation) is a series of recommendations put together by the [FIG](http://www.php-fig.org/) (Framework Interop Group).

"The idea behind the group is for project representatives to talk about the commonalities between our projects and find ways we can work together" - [FIG FAQ](http://www.php-fig.org/faqs/)

PSRs can be in the following states: Accepted, Review, Draft or Deprecated.

## Section 88.1: PSR-4: Autoloader

[PSR-4](http://www.php-fig.org/psr/psr-4/) is an accepted recommendation that outlines the standard for autoloading classes via filenames. This recommendation is recommended as the alternative to the earlier (and now deprecated) [PSR-0](http://www.php-fig.org/psr/psr-0/) .

The fully qualified class name should match the following requirement:

![](Image01570.jpg)

 
| path\_to\_source || \]/ || Alphabet || / || Google || / || AdWord || / || KeywordPlanner || . || php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Thus the final class name would be Alphabet\\Google\\AdWord\\KeywordPlanner . The fully qualified class name should also translate into a meaningful file path therefore Alphabet\\Google\\AdWord\\KeywordPlanner would be located in \[

Starting with PHP 5.3.0, a [custom autoloader function](http://php.net/manual/en/function.spl-autoload-register.php) can be defined to load files based on the path and filename pattern that you define.

![](Image01571.jpg) \# Edit your php to include something like: spl\_autoload\_register ( function ( $class ) { include 'classes/' . $class . '.class.php' ;});

Replacing the location ('classes/') and filename extension ('.class.php') with values that apply to your structure.

Composer package manager [supports PSR-4](https://getcomposer.org/doc/01-basic-usage.md#autoloading) which means, if you follow the standard, you can load your classes in your project automatically using Composer's vendor autoloader.

![](Image01572.jpg)

Regenerate the autoloader file

![](Image01573.jpg)

Now in your code you can do the following:

![](Image01574.jpg)

![](Image01575.jpg) require \_\_DIR\_\_ . '/vendor/autoload.php' ; $KeywordPlanner \= new Alphabet\\Google\\AdWord\\KeywordPlanner ();

## Section 88.2: PSR-1: Basic Coding Standard

[PSR-1](http://www.php-fig.org/psr/psr-1/) is an accepted recommendation and outlines a basic standard recommendation for how code should be written.

![](Image01576.jpg)It outlines naming convetions for classes, methods and constants.

It makes adopting PSR-0 or PSR-4 recommendations a requirement.

It indicates which PHP tags to use: <?php and <?= but not <? .

It specifies what file encoding to use (UTF8).

It also states that files should either declare new symbols (classes, functions, constants, etc.) and cause no other side effects, or execute logic with side effects and not define symbols, but do both.

  

# Chapter 89: PHPDoc

## Section 89.1: Describing a variable

 
| @ var |
| --- |

The  keyword can be used to describe the type and usage of:

![](Image01577.jpg)

The type can be one of the built-in PHP types, or a user-defined class, including namespaces.

The name of the variable should be included, but can be omitted if the docblock applies to only one item.

## Section 89.2: Adding metadata to functions

Function level annotations help IDEs identify return values or potentially dangerous code

![](Image01578.jpg)

![](Image01579.jpg)

## Section 89.3: Describing parameters

![](Image01580.jpg)

![](Image01581.jpg)

## Section 89.4: Collections

[PSR-5](https://github.com/php-fig/fig-standards/blob/211063eed7f4d9b4514b728d7b1810d9b3379dd1/proposed/phpdoc.md#collections) proposes a form of Generics-style notation for collections.

Generics Syntax

![](Image01582.jpg)

Values in a Collection MAY even be another array and even another Collection.

![](Image01583.jpg)

Examples

![](Image01584.jpg)

![](Image01585.jpg)

## Section 89.5: Adding metadata to files

File level metadata applies to all the code within the file and should be placed at the top of the file:

![](Image01586.jpg)

## Section 89.6: Inheriting metadata from parent structures

 
| @ inheritDoc |
| --- |

If a class extends another class and would use the same metadata, providing it  is a simple way for use the same documentation. If multiple classes inherit from a base, only the base would need to be changed for the children to be affected.

![](Image01587.jpg)

![](Image01588.jpg)

  

# Chapter 90: Design Patterns

This topic provides examples of well known design patterns implemented in PHP.

## Section 90.1: Method Chaining in PHP

Method Chaining is a technique explained in [Martin Fowler's book](http://rads.stackoverflow.com/amzn/click/0321712943) [Domain Specific Languages](http://rads.stackoverflow.com/amzn/click/0321712943) . Method Chaining is summarized as

![](Image01589.jpg)[              Makes modifier methods return the host object, so that multiple modifiers can be invoked in a single expression](http://martinfowler.com/dslCatalog/methodChaining.html) .

Consider this non-chaining/regular piece of code (ported to PHP from the aforementioned book)

![](Image01590.jpg)

Method Chaining would allow you to write the above statements in a more compact way:

![](Image01591.jpg)

 
| return $this |
| --- |

All you need to do for this to work is to  in the methods you want to chain from:

![](Image01592.jpg)

When to use it

The primary use cases for utilizing Method Chaining is when building internal Domain Specific Languages. Method Chaining is a building block in [Expression Builders](http://martinfowler.com/bliki/ExpressionBuilder.html) and [Fluent Interfaces](http://martinfowler.com/bliki/FluentInterface.html) . [It is not synonymous with those, though](http://stackoverflow.com/a/17940086/208809) . Method Chaining merely enables those. Quoting Fowler:

![](Image01593.jpg)

![](Image01594.jpg)I've also noticed a common misconception - many people seem to equate fluent interfaces with Method Chaining. Certainly chaining is a common technique to use with fluent interfaces, but true fluency is much more than that.

With that said, using Method Chaining just for the sake of avoiding writing the host object is considered a [code](http://martinfowler.com/bliki/CodeSmell.html) [smell](http://martinfowler.com/bliki/CodeSmell.html) by many. It makes for unobvious APIs, especially when mixing with non-chaining APIs.

Additional Notes

Command Query Separation

[Command Query Separation is a design principle brought forth by Bertrand Meyer](http://martinfowler.com/bliki/CommandQuerySeparation.html) . It states that methods mutating state ( commands ) should not return anything, whereas methods returning something ( queries ) should not mutate state. This makes it easier to reason about the system. Method Chaining violates this principle because we are mutating state and returning something.

Getters

When making use of classes which implement method chaining, pay particular attention when calling getter methods (that is, methods which return something other than $this ). Since getters must return a value other than $this , chaining an additional method onto a getter makes the call operate on the gotten value, not on the original object. While there are some use cases for chained getters, they may make code less readable.

Law of Demeter and impact on testing

Method Chaining as presented above does not violate [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter) . Nor does it impact testing. That is because we are returning the host instance and not some collaborator. It's a common misconception stemming from people confusing mere Method Chaining with Fluent Interfaces and Expression Builders . It is only when Method Chaining returns other objects than the host object that you violate Law of Demeter and end up with Mock fests in your tests.

# Chapter 91: Compile PHP Extensions

## Section 91.1: Compiling on Linux

To compile a PHP extension in a typical Linux environment, there are a few pre-requisites:

![](Image01595.jpg)Basic Unix skills (being able to operate "make" and a C compiler)

An ANSI C compiler

The source code for the PHP extension you want to compile

Generally there are two ways to compile a PHP extension. You can statically compile the extension into the PHP binary, or compile it as a shared module loaded by your PHP binary at startup. Shared modules are more likely since they allow you to add or remove extensions without rebuilding the entire PHP binary. This example focuses on the shared option.

 
| apt || \- || get install |
| --- | --- | --- |

 
| php5 || \- || dev || or || php7 || \- || dev |
| --- | --- | --- | --- | --- | --- | --- |

If you installed PHP via your package manager (, yum install , etc..) you will need to install the dev package for PHP, which will include the necessary PHP header files and phpize script for the build environment to work. The package might be named something like , but be sure to use your package manager to search for the appropriate name using your distro's repositories. They can differ.

 
| usr || / || include |
| --- | --- | --- |

If you built PHP from source the header files most likely already exist on your system ( usually in / or

 
| usr || / || local || / || include |
| --- | --- | --- | --- | --- |

/ ).

Steps to compile

After you check to make sure you have all the prerequisites, necessary to compile, in place you can head over to [pecl.php.net](http://pecl.php.net/) , select an extension you wish to compile, and download the tar ball.

 
| tar xfvz yaml || \- 2 . 0 . || 0RC8 || . || tgz |
| --- | --- | --- | --- | --- |

1.    Unpack the tar ball (e.g. )

2.    Enter the directory where the archive was unpacked and run phpize

 
| configure || script if all went well, run that || ./ configure |
| --- | --- | --- |

3.    You should now see a newly created .

4.    Now you will need to run make , which will compile the extension

5.    Finally, make install will copy the compiled extension binary to your extension directory

 
| usr || / || lib || / , for example it might be something like / || usr || / || lib || / || php5 || / || 20131226 || / || yaml || . || so |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

 
| \-- with || \- || prefix |
| --- | --- | --- |

The make install step will typically provide the installation path for you where the extension was copied. This is usually in / . But this depends on your configuration of PHP (i.e. ) and specific API version. The API number is included in the path to keep extensions built for different API versions in separate locations.

Loading the Extension in PHP

 
| extension || \= || yaml || . || so || then restart PHP. Change || yaml || . || so |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

To load the extension in PHP, find your loaded php.ini file for the appropriate SAPI, and add the line  to the name of the actual extension you installed, of course.

For a Zend extension you do need to provide the full path to the shared object file. However, for normal PHP extensions this path derived from the [extension\_dir](http://php.net/ini.core#ini.extension-dir) directive in your loaded configuration, or from the $PATH environment during initial setup.

# Chapter 92: Common Errors

## Section 92.1: Call fetch\_assoc on boolean

If you get an error like this:

![](Image01596.jpg) Fatal error : Call to a member function fetch\_assoc () on boolean in C : \\xampp\\htdocs\\stack\\index . php on line 7

![](Image01597.jpg) Other variations include something along the lines of: mysql\_fetch\_assoc () expects parameter 1 to be resource , boolean given ...

These errors mean that there is something wrong with either your query (this is a PHP/MySQL error), or your referencing. The above error was produced by the following code:

![](Image01598.jpg)

In order to "fix" this error, it is recommended to make mysql throw exceptions instead:

![](Image01599.jpg)

This will then throw an exception with this much more helpful message instead:

![](Image01600.jpg) You have an error in your SQL syntax ; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'SELCT \* FROM db' at line 1

Another example that would produce a similar error, is where you simply just gave the wrong information to the mysql\_fetch\_assoc function or similar:

![](Image01601.jpg)

## Section 92.2: Unexpected $end

![](Image01602.jpg) Parse error : syntax error , unexpected end of file in C : \\xampp\\htdocs\\stack\\index . php on line 4

 
| unexpected $end |
| --- |

If you get an error like this (or sometimes , depending on PHP version), you will need to make sure that you've matched up all inverted commas, all parentheses, all curly braces, all brackets, etc.

The following code produced the above error:

![](Image01603.jpg)

Notice the missing curly brace. Also do note that the line number shown for this error is irrelevant - it always shows the last line of your document.

  

# Chapter 93: Compilation of Errors and Warnings

## Section 93.1: Parse error: syntax error, unexpected T\_PAAMAYIM\_NEKUDOTAYIM

Appearance:

"Paamayim Nekudotayim" means "double colon" in Hebrew; thus this error refers to the inappropriate use of the double colon operator ( :: ). The error is typically caused by an attempt to call a static method that is, in fact, not static.

Possible Solution:

![](Image01604.jpg)

If the above code causes this error, you most likely need to simply change the way you call the method:

![](Image01605.jpg)

 
| doMethod () |
| --- |

The latter example assumes that $classname is an instance of a class, and the  is not a static method of that class.

## Section 93.2: Notice: Undefined index

Appearance:

Trying to access an array by a key that does not exist in the array

Possible Solution:

Check the availability before accessing it. Use:

 
| [isset](http://php.net/manual/en/function.isset.php) [(](http://php.net/manual/en/function.isset.php) [)](http://php.net/manual/en/function.isset.php) |
| --- |

 
| [array\_key\_exists](http://php.net/manual/en/function.array-key-exists.php) [(](http://php.net/manual/en/function.array-key-exists.php) [)](http://php.net/manual/en/function.array-key-exists.php) |
| --- |

1\. 2.

## Section 93.3: Warning: Cannot modify header information headers already sent

Appearance:

Happens when your script tries to send a HTTP header to the client but there already was output before, which resulted in headers to be already sent to the client.

Possible Causes:

1.    Print, echo: Output from print and echo statements will terminate the opportunity to send HTTP headers. The application flow must be restructured to avoid that.

 
| header () |
| --- |

2.    Raw HTML areas: Unparsed HTML sections in a .php file are direct output as well. Script conditions that will trigger a  call must be noted before any raw blocks.

![](Image01606.jpg)

3.    Whitespace before <?php for "script.php line 1" warnings: If the warning refers to output in line 1, then it's mostly leading whitespace, text or HTML before the opening <?php token.

![](Image01607.jpg)

Reference from SO [answer](http://stackoverflow.com/a/8028987/5447994) by [Mario](http://stackoverflow.com/users/345031/mario)

  

# Chapter 94: Exception Handling and Error Reporting

## Section 94.1: Setting error reporting and where to display them

If it's not already done in php.ini, error reporting can be set dynamically and should be set to allow most errors to be shown:

Syntax

![](Image01608.jpg)

Examples

![](Image01609.jpg)

errors will be logged by default by php, normally in a error.log file at the same level than the running script. in development environment, one can also show them on screen:

![](Image01610.jpg)

in production however, one should

![](Image01611.jpg)

and show a friendly problem message through the use of an Exception or Error handler.

## Section 94.2: Logging fatal errors

In PHP, a fatal error is a kind of error that cannot be caught, that is, after experiencing a fatal error a program does not resume. However, to log this error or somehow handle the crash you can use register\_shutdown\_function to register shutdown handler.

![](Image01612.jpg)

![](Image01613.jpg)

Reference:

![](Image01614.jpg)[http://php.net/manual/en/function.register-shutdown-function.php](http://php.net/manual/en/function.register-shutdown-function.php) [http://php.net/manual/en/function.error-get-last.php](http://php.net/manual/en/function.error-get-last.php) [http://php.net/manual/en/errorfunc.constants.php](http://php.net/manual/en/errorfunc.constants.php)

# Chapter 95: Debugging

## Section 95.1: Dumping variables

The [var\_dump](http://php.net/manual/en/function.var-dump.php) function allows you to dump the contents of a variable (type and value) for debugging.

Example:

![](Image01615.jpg)

Output:

![](Image01616.jpg)

## Section 95.2: Displaying errors

 
| php . ini |
| --- |

If you want PHP to display runtime errors on the page, you have to enable [display\_errors](http://php.net/manual/en/errorfunc.configuration.php#ini.display-errors) , either in the  or using the [ini\_set](http://php.net/manual/en/function.ini-set.php) function.

 
| [E\_](http://php.net/manual/en/errorfunc.constants.php) [\*](http://php.net/manual/en/errorfunc.constants.php) |
| --- |

You can choose which errors to display, with the error\_reporting (or in the ini) function, which accepts [constants](http://php.net/manual/en/errorfunc.constants.php) , combined using [bitwise operators](http://php.net/manual/en/language.operators.bitwise.php) .

PHP can display errors in text or HTML format, depending on the [html\_errors](http://php.net/manual/en/errorfunc.configuration.php#ini.html-errors) setting.

Example:

![](Image01617.jpg)

![](Image01618.jpg)

Plain text output: (HTML format differs between implementations)

![](Image01619.jpg)

The common way to handle error\_reporting is to enable it fully with E\_ALL constant during the development, and to disable publicly displaying it with display\_errors on production stage to hide the internals of your scripts.

## Section 95.3: phpinfo()

Warning

It is imperative that phpinfo is only used in a development environment. Never release code containing phpinfo into a production environment

Introduction

Having said that, it can be a useful tool in understanding the PHP environment (OS, configuration, versions, paths, modules) in which you are working, especially when chasing a bug. It is a simple built in function:

![](Image01620.jpg)

It has one parameter $what that allows the output to be customized. The default is INFO\_ALL , causing it to display all information and is commonly used during development to see the current state of PHP.

 
| [INFO\_](http://php.net/manual/en/function.phpinfo.php#refsect1-function.phpinfo-parameters) |
| --- |

You can pass the parameter [\*](http://php.net/manual/en/function.phpinfo.php#refsect1-function.phpinfo-parameters) [constants](http://php.net/manual/en/function.phpinfo.php#refsect1-function.phpinfo-parameters) , combined with bitwise operators to see a customized list.

You can run it in the browser for a nicely formatted detailed look. It also works in PHP CLI, where you can pipe it into less for easier view.

Example

![](Image01621.jpg)

This will display a list of PHP directives ( [ini\_get](http://php.net/manual/en/function.ini-get.php) ), environment ( [$\_ENV](http://php.net/manual/en/reserved.variables.environment.php) ) and [predefined](http://php.net/manual/en/language.variables.predefined.php) variables.

## Section 95.4: Xdebug

[Xdebug](https://xdebug.org/) is a PHP extension which provides debugging and profiling capabilities. It uses the DBGp debugging protocol.

There are some nice features in this tool:

![](Image01622.jpg)stack traces on errors

 
| var\_dump |
| --- |

![](Image01623.jpg)maximum nesting level protection and time tracking helpful replacement of standard () function for displaying variables allows to log all function calls, including parameters and return values to a file in different formats code coverage analysis profiling information

remote debugging (provides interface for debugger clients that interact with running PHP scripts)

 
| ++ |
| --- |

As you can see this extension is perfectly suited for development environment. Especially remote debugging feature can help you to debug your php code without numerous var\_dump's and use normal debugging process as in C or Java languages.

Usually installing of this extension is very simple:

![](Image01624.jpg)

And activate it into your php.ini:

![](Image01625.jpg)

In more complicated cases see this [instructions](https://xdebug.org/docs/install)

When you use this tool you should remember that:

[XDebug is not suitable for production environments](http://stackoverflow.com/a/3522356/2253302)

## Section 95.5: Error Reporting (use them both)

![](Image01626.jpg)

## Section 95.6: phpversion()

Introduction

When working with various libraries and their associated requirements, it is often necessary to know the version of current PHP parser or one of it's packages.

 
| phpversion || ( || 'extension' |
| --- | --- | --- |

This function accepts a single optional parameter in the form of extension name: ) . If the

extension in question is installed, the function will return a string containing version value. However, if the extension not installed FALSE will be returned. If the extension name is not provided, the function will return the version of PHP parser itself.

Example

![](Image01627.jpg)

# Chapter 96: Unit Testing

## Section 96.1: Testing class rules

Let's say, we have a simple LoginForm class with rules() method (used in login page as framework template):

![](Image01628.jpg)

In order to perform tests on this class, we use Unit tests (checking source code to see if it fits our expectations):

![](Image01629.jpg)

How exactly Unit tests can help with (excluding general examples) in here? For example, it fits very well when we get unexpected results. For example, let's take this rule from earlier:

![](Image01630.jpg)

Instead, if we missed one important thing and wrote this:

![](Image01631.jpg)

With dozens of different rules (assuming we are using not just email and password), it's difficult to detect mistakes. This unit test:

// Initialize to valid and test this

$this \-> loginForm \-> email \= "valid@email.com" ;

$this \-> loginForm \-> password \= "password" ;

$this \-> loginForm \-> rememberMe \= true ;

![](Image01632.jpg) $this \-> assertTrue ( $this \-> loginForm \-> validate ( $rules ), "Should be valid as nothing is invalid" );

Will pass our first example but not second . Why? Because in 2nd example we wrote a pattern with a typo (missed + sign), meaning it only accepts one letter/number.

 
| phpunit || \[ || path\_to\_file |
| --- | --- | --- |

Unit tests can be run in console with command: \] . If everything is OK, we should be able to see that all tests are in OK state, else we will see either Error (syntax errors) or Fail (at least one line in that method did not pass).

 
| \-- coverage |
| --- |

With additional parameters like  we can also see visually how many lines in backend code were tested and which passed/failed. This applies to any framework that has installed [PHPUnit](https://phpunit.de/) .

Example how PHPUnit test looks like in console (general look, not according to this example):

  

![](Image01633.jpg)

## Section 96.2: PHPUnit Data Providers

Test methods often need data to be tested with. To test some methods completely you need to provide different data sets for every possible test condition. Of course, you can do it manually using loops, like this:

![](Image01634.jpg)

And someone can find it convenient. But there are some drawbacks of this approach. First, you'll have to perform additional actions to extract data if your test function accepts several parameters. Second, on failure it would be difficult to distinguish the failing data set without additional messages and debugging. Third, PHPUnit provides automatic way to deal with test data sets using [data providers](https://phpunit.de/manual/current/en/writing-tests-for-phpunit.html#writing-tests-for-phpunit.data-providers) .

Data provider is a function, that should return data for your particular test case.

![](Image01635.jpg)A data provider method must be public and either return an array of arrays or an object that implements the Iterator interface and yields an array for each iteration step. For each array that is part of the collection the test method will be called with the contents of the array as its arguments.

 
| dataProvider |
| --- |

To use a data provider with your test, use @ annotation with the name of data provider function specified:

![](Image01636.jpg)

![](Image01637.jpg)

Each data set can be named for convenience. It will be easier to detect failing data:

![](Image01638.jpg)

Iterators

![](Image01639.jpg)

![](Image01640.jpg)

As you can see, simple iterator also works.

 
| $parameter |
| --- |

 
| current |
| --- |

![](Image01641.jpg)Note that even for a single parameter, data provider must return an array \[ \] Because if we change our () method (which actually return data on every iteration) to this:

![](Image01642.jpg)

Or change actual data:

![](Image01643.jpg)

![](Image01644.jpg)

Generators

It is not explicitly noted and shown in manual, but you can also use a generator as data provider. Note that Generator class actually implements Iterator interface.

So here's an example of using DirectoryIterator combined with generator :

![](Image01645.jpg)

## Section 96.3: Test exceptions

Let's say you want to test method which throws an exception

![](Image01646.jpg)

![](Image01647.jpg)

You can do that by enclosing the method call into a try/catch block and making assertions on execption object's properties, but more conveniently you can use exception assertion methods. As of [PHPUnit 5.2](https://github.com/sebastianbergmann/phpunit/wiki/Release-Announcement-for-PHPUnit-5.2.0) you have expectX() methods available for asserting exception type, message & code

![](Image01648.jpg)

If you are using earlier version of PHPUnit, method setExpectedException can be used in stead of expectX() methods, but keep in mind that it's deprecated and will be removed in version 6.

![](Image01649.jpg)

# Chapter 97: Performance

## Section 97.1: Profiling with Xdebug

An extension to PHP called Xdebug is available to assist in [profiling PHP applications](https://xdebug.org/docs/profiler) , as well as runtime debugging. When running the profiler, the output is written to a file in a binary format called "cachegrind". Applications are available on each platform to analyze these files.

To enable profiling, install the extension and adjust php.ini settings. In our example we will run the profile optionally based on a request parameter. This allows us to keep settings static and turn on the profiler only as needed.

// Set to 1 to turn it on for every request xdebug . profiler\_enable \= 0

// Let's use a GET/POST parameter to turn on the profiler xdebug . profiler\_enable\_trigger \= 1

// The GET/POST value we will pass; empty for any value xdebug . profiler\_enable\_trigger\_value \= ""

![](Image01650.jpg) // Output cachegrind files to /tmp so our system cleans them up later xdebug . profiler\_output\_dir \= "/tmp"

xdebug . profiler\_output\_name \= "cachegrind.out.%p"

Next use a web client to make a request to your application's URL you wish to profile, e.g.

![](Image01651.jpg)

As the page processes it will write to a file with a name similar to

![](Image01652.jpg)

Note that it will write one file for each PHP request / process that is executed. So, for example, if you wish to analyze a form post, one profile will be written for the GET request to display the HTML form. The XDEBUG\_PROFILE parameter will need to be passed into the subsequent POST request to analyze the second request which processes the form. Therefore when profiling it is sometimes easier to run curl to POST a form directly.

Once written the profile cache can be read by an application such as KCachegrind.

![](Image01653.jpg)

This will display information including:

![](Image01654.jpg)Functions executed

Call time, both itself and inclusive of subsequent function calls

Number of times each function is called

Call graphs

Links to source code

Obviously performance tuning is very specific to each application's use cases. In general it's good to look for:

![](Image01655.jpg)Repeated calls to the same function you wouldn't expect to see. For functions that process and query data these could be prime opportunities for your application to cache.

Slow-running functions. Where is the application spending most of its time? the best payoff in performance tuning is focusing on those parts of the application which consume the most time.

Note : Xdebug, and in particular its profiling features, are very resource intensive and slow down PHP execution. It is recommended to not run these in a production server environment.

## Section 97.2: Memory Usage

 
| php || . || ini |
| --- | --- | --- |

PHP's runtime memory limit is set through the INI directive memory\_limit . This setting prevents any single execution of PHP from using up too much memory, exhausting it for other scripts and system software. The memory limit defaults to 128M and can be changed in the  file or at runtime. It can be set to have no limit, but this is generally considered bad practice.

 
| memory\_get\_usage |
| --- |

The exact memory usage used during runtime can be determined by calling () . It returns the number of bytes of memory allocated to the currently running script. As of PHP 5.2, it has one optional boolean parameter to get the total allocated system memory, as opposed to the memory that's actively being used by PHP.

![](Image01656.jpg)

 
| memory\_get\_peak\_usage |
| --- |

Now memory\_get\_usage gives you memory usage at the moment it is run. Between calls to this function you may allocate and deallocate other things in memory. To get the maximum amount of memory used up to a certain point, call () .

![](Image01657.jpg)

Notice the value will only go up or stay constant.

## Section 97.3: Profiling with XHProf

[XHProf](https://github.com/phacility/xhprof) is a PHP profiler originally written by Facebook, to provide a more lightweight alternative to XDebug.

After installing the xhprof PHP module, profiling can be enabled / disabled from PHP code:

![](Image01658.jpg)

 
| doSlowOperation |
| --- |

The returned array will contain data about the number of calls, CPU time and memory usage of each function that has been accessed inside () .

 
| xhprof\_sample\_enable || () / || xhprof\_sample\_disable |
| --- | --- | --- |

() can be used as a more lightweight option that will only log

profiling information for a fraction of requests (and in a different format).

XHProf has some (mostly undocumented) helper functions to display the data ( [see example](https://github.com/phacility/xhprof/blob/master/examples/sample.php) ), or you can use other tools to visualize it (the platform.sh blog [has an example](https://platform.sh/2015/07/29/flamegraphs/) ).

  

# Chapter 98: Multiprocessing

## Section 98.1: Multiprocessing using built-in fork functions

You can use built-in functions to run PHP processes as forks. This is the most simple way to achieve parallel work if you don't need your threads to talk to each other.

This allows you to put time intensive tasks (like uploading a file to another server or sending an email) to another thread so your script loads faster and can use multiple cores but be aware that this is not real multithreading and your main thread won't know what the children are up to.

Note that under Windows this will make another command prompt pop up for each fork you start.

master.php

![](Image01659.jpg)

worker.php

![](Image01660.jpg)

## Section 98.2: Creating child process using fork

PHP has built in function pcntl\_fork for creating child process. pcntl\_fork is same as fork in unix. It does not take in any parameters and returns integer which can be used to differentiate between parent and child process.

Consider the following code for explanation

![](Image01661.jpg)

As you can see \-1 is an error in fork and the child was not created. On creation of child, we have two processes running with separate PID .

 
| pcntl\_wait || ( || $status |
| --- | --- | --- |

Another consideration here is a zombie process or defunct process when parent process finishes before child process. To prevent a zombie children process simply add ) at the end of parent process. ![](Image01662.jpg)              pnctl\_wait suspends execution of parent process until the child process has exited.

It is also worth noting that zombie process can't be killed using SIGKILL signal.

## Section 98.3: Inter-Process Communication

Interprocess communication allows programmers to communicate between different processes. For example let us consider we need to write an PHP application that can run bash commands and print the output. We will be using proc\_open , which will execute the command and return a resource that we can communicate with. The following code shows a basic implementation that runs pwd in bash from php

![](Image01663.jpg)

proc\_open runs bash command with $descriptor as descriptor specifications. After that we use is\_resource to validate the process. Once done we can start interacting with the child process using $pipes which is generated according to descriptor specifications.

After that we can simply use fwrite to write to stdin of child process. In this case pwd followed by carriage return.

Finally stream\_get\_contents is used to read stdout of child process.

![](Image01664.jpg)Always remember to close the child process by using proc\_close() which will terminate the child and return the exit status code.

# Chapter 99: Multi Threading Extension

## Section 99.1: Getting Started

 
| pthreads \- ext |
| --- |

To start with multi-threading, you would need the  for php, which can be installed by

![](Image01665.jpg)

 
| php . ini |
| --- |

and adding the entry to .

A simple example:

![](Image01666.jpg)

## Section 99.2: Using Pools and Workers

![](Image01667.jpg)Pooling provides a higher level abstraction of the Worker functionality, including the management of references in the way required by pthreads. From: [http://php.net/manual/en/class.pool.php](http://php.net/manual/en/class.pool.php)

Pools and workers provide an higher level of control and ease of creating multi-threaded

![](Image01668.jpg)

![](Image01669.jpg)

# Chapter 100: Secure Remeber Me

I have been searching on this topic for sometime till i found this post [https://stackoverflow.com/a/17266448/4535386](https://stackoverflow.com/a/17266448/4535386) from ircmaxell, I think it deserves more exposure.

## Section 100.1: “Keep Me Logged In” - the best approach

store the cookie with three parts.

![](Image01670.jpg)

Then, to validate:

![](Image01671.jpg)

# Chapter 101: Security

As the majority of websites run off PHP, application security is an important topic for PHP developers to protect their website, data, and clients. This topic covers best security practices in PHP as well as common vulnerabilities and weaknesses with example fixes in PHP.

## Section 101.1: PHP Version Leakage

By default, PHP will tell the world what version of PHP you are using, e.g.

![](Image01672.jpg)

To fix this you can either change php.ini:

![](Image01673.jpg)

Or change the header:

![](Image01674.jpg)

Or if you'd prefer a htaccess method:

![](Image01675.jpg)

 
| [header\_remove](http://php.net/header_remove) |
| --- |

If either of the above methods do not work, there is also the [(](http://php.net/header_remove) [)](http://php.net/header_remove) function that provides you the ability to remove the header:

![](Image01676.jpg)

If attackers know that you are using PHP and the version of PHP that you are using, it's easier for them to exploit your server.

## Section 101.2: Cross-Site Scripting (XSS)

Problem

Cross-site scripting is the unintended execution of remote code by a web client. Any web application might expose itself to XSS if it takes input from a user and outputs it directly on a web page. If input includes HTML or JavaScript, remote code can be executed when this content is rendered by the web client.

For example, if a 3rd party side contains a JavaScript file:

![](Image01677.jpg)

And a PHP application directly outputs a string passed into it:

![](Image01678.jpg)

 
| <script src || \= || "http://example.com/runme.js" || \> || </script |
| --- | --- | --- | --- | --- |

If an unchecked GET parameter contains \> then the output of the PHP script will be:

![](Image01679.jpg)

The 3rd party JavaScript will run and the user will see "I'm running" on the web page.

Solution

As a general rule, never trust input coming from a client. Every GET, POST, and cookie value could be anything at all, and should therefore be validated. When outputting any of these values, escape them so they will not be evaluated in an unexpected way.

Keep in mind that even in the simplest applications data can be moved around and it will be hard to keep track of all sources. Therefore it is a best practice to always escape output.

PHP provides a few ways to escape output depending on the context.

Filter Functions

[PHPs Filter Functions](http://php.net/manual/en/ref.filter.php) allow the input data to the php script to be [sanitized](http://php.net/manual/en/filter.filters.sanitize.php) or [validated](http://php.net/manual/en/filter.filters.validate.php) in [many ways](http://php.net/manual/en/filter.filters.php) . They are useful when saving or outputting client input. HTML Encoding

htmlspecialchars will convert any "HTML special characters" into their HTML encodings, meaning they will then not be processed as standard HTML. To fix our previous example using this method:

![](Image01680.jpg)

Would output:

![](Image01681.jpg) <div> &lt; script src= &quot; http://example.com/runme.js &quot;&gt;&lt; /script &gt; </div>

 
| <div |
| --- |

Everything inside the \> tag will not be interpreted as a JavaScript tag by the browser, but instead as a simple text node. The user will safely see:

![](Image01682.jpg)

URL Encoding

When outputting a dynamically generated URL, PHP provides the urlencode function to safely output valid URLs. So, for example, if a user is able to input data that becomes part of another GET parameter:

![](Image01683.jpg)

Any malicious input will be converted to an encoded URL parameter.

Using specialised external libraries or OWASP AntiSamy lists

Sometimes you will want to send HTML or other kind of code inputs. You will need to maintain a list of authorised words (white list) and un-authorized (blacklist).

You can download standard lists available at the [OWASP AntiSamy website](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) . Each list is fit for a specific kind of interaction (ebay api, tinyMCE, etc...). And it is open source.

There are libraries existing to filter HTML and prevent XSS attacks for the general case and performing at least as well as AntiSamy lists with very easy use. For example you have [HTML Purifier](http://htmlpurifier.org/)

## Section 101.3: Cross-Site Request Forgery

Problem

 
| delete || . || php?accnt || \= || 12 |
| --- | --- | --- | --- | --- |

Cross-Site Request Forgery or CSRF can force an end user to unknowingly generate malicious requests to a web server. This attack vector can be exploited in both POST and GET requests. Let's say for example the url endpoint / deletes account as passed from accnt parameter of a GET request. Now if an authenticated

user will encounter the following script in any other application

![](Image01684.jpg) < img src \= "http://domain.com/delete.php?accnt=12" width \= "0" height \= "0" border \= "0" \> the account would be deleted.

Solution

A common solution to this problem is the use of CSRF tokens . CSRF tokens are embedded into requests so that a web application can trust that a request came from an expected source as part of the application's normal workflow. First the user performs some action, such as viewing a form, that triggers the creation of a unique token.

A sample form implementing this might look like

![](Image01685.jpg)

The token can then be validated by the server against the user session after form submission to eliminate malicious requests.

Sample code

Here is sample code for a basic implementation:

![](Image01686.jpg)

![](Image01687.jpg)

There are many libraries and frameworks already available which have their own implementation of CSRF validation. Though this is the simple implementation of CSRF, You need to write some code to regenerate your CSRF token dynamically to prevent from CSRF token stealing and fixation.

## Section 101.4: Command Line Injection

Problem

In a similar way that SQL injection allows an attacker to execute arbitrary queries on a database, command-line injection allows someone to run untrusted system commands on a web server. With an improperly secured server this would give an attacker complete control over a system.

Let's say, for example, a script allows a user to list directory contents on a web server.

![](Image01688.jpg)

(In a real-world application one would use PHP's built-in functions or objects to get path contents. This example is for a simple security demonstration.)

 
| tmp || . But as any input is allowed, path could be ; || rm || \- || fr |
| --- | --- | --- | --- | --- |

One would hope to get a path parameter similar to // .

The web server would then execute the command

![](Image01689.jpg)

and attempt to delete all files from the root of the server.

Solution

 
| escapeshellarg || () or || escapeshellcmd |
| --- | --- | --- |

All command arguments must be escaped using () . This makes the arguments non-executable. For each parameter, the input value should also be validated .

In the simplest case, we can secure our example with

![](Image01690.jpg)

![](Image01691.jpg)

Following the previous example with the attempt to remove files, the executed command becomes

![](Image01692.jpg)

And the string is simply passed as a parameter to ls , rather than terminating the ls command and running rm .

It should be noted that the example above is now secure from command injection, but not from directory traversal. To fix this, it should be checked that the normalized path starts with the desired sub-directory.

PHP offers a variety of functions to execute system commands, including exec , passthru , proc\_open , shell\_exec , and system . All must have their inputs carefully validated and escaped.

## Section 101.5: Stripping Tags

[strip\_tags](http://php.net/manual/en/function.strip-tags.php) is a very powerful function if you know how to use it. As a method to prevent cross-site scripting attacks there are better methods, such as character encoding, but stripping tags is useful in some cases. Basic Example

![](Image01693.jpg)

Raw Output

![](Image01694.jpg)

Allowing Tags

 
| <b |
| --- |

Say you wanted to allow a certain tag but no other tags, then you'd specify that in the second parameter of the function. This parameter is optional. In my case I only want the \> tag to be passed through.

![](Image01695.jpg)

Raw Output

![](Image01696.jpg)

Notice(s)

HTML comments and PHP tags are also stripped. This is hardcoded and can not be changed with allowable\_tags.

 
| <br || \> and || <br/> |
| --- | --- | --- |

In PHP 5.3.4 and later, self-closing XHTML tags are ignored and only non-self-closing tags should be used in allowable\_tags. For example, to allow both , you should use:

![](Image01697.jpg)

## Section 101.6: File Inclusion

Remote File Inclusion

Remote File Inclusion (also known as RFI) is a type of vulnerability that allows an attacker to include a remote file.

This example injects a remotely hosted file containing a malicious code:

![](Image01698.jpg)

Local File Inclusion

Local File Inclusion (also known as LFI) is the process of including files on a server through the web browser.

![](Image01699.jpg)

Solution to RFI & LFI:

It is recommended to only allow including files you approved, and limit to those only.

![](Image01700.jpg)

## Section 101.7: Error Reporting

By default PHP will output errors , warnings and notice messages directly on the page if something unexpected in a script occurs. This is useful for resolving specific issues with a script but at the same time it outputs information you don't want your users to know.

Therefore it's good practice to avoid displaying those messages which will reveal information about your server, like your directory tree for example, in production environments. In a development or testing environment these messages may still be useful to display for debugging purposes.

A quick solution

You can turn them off so the messages don't show at all, however this makes debugging your script harder.

![](Image01701.jpg)

Or change them directly in the php.ini . ![](Image01702.jpg)display\_errors \= 0 Handling errors

A better option would be to store those error messages to a place they are more useful, like a database:

![](Image01703.jpg)

This method will log the messages to the database and if that fails to a file instead of echoing it directly into the page. This way you can track what users are experiencing on your website and notify you immediately if something go's wrong.

## Section 101.8: Uploading files

If you want users to upload files to your server you need to do a couple of security checks before you actually move the uploaded file to your web directory.

The uploaded data:

This array contains user submitted data and is not information about the file itself. While usually this data is generated by the browser one can easily make a post request to the same form using software.

![](Image01704.jpg)

Exploiting the file name

Normally the operating system does not allow specific characters in a file name, but by spoofing the request you can add them allowing for unexpected things to happen. For example, lets name the file:

 
| ../ script || . || php || % || 00 || . || png |
| --- | --- | --- | --- | --- | --- | --- |

Take good look at that filename and you should notice a couple of things.

1.    The first to notice is the ../ , fully illegal in a file name and at the same time perfectly fine if you are moving a file from 1 directory to another, which we're gonna do right?

 
| 00 |
| --- |

 
| png |
| --- |

2.    Now you might think you were verifying the file extensions properly in your script but this exploit relies on the url decoding, translating % to a null character, basically saying to the operating system, this string ends here, stripping off . off the filename.

 
| script || . || php |
| --- | --- | --- |

 
| htaccess |
| --- |

So now I've uploaded  to another directory, by-passing simple validations to file extensions. It also bypasses . files disallowing scripts to be executed from within your upload directory.

Getting the file name and extension safely

 
| [pathinfo](http://php.net/manual/en/function.pathinfo.php) |
| --- |

You can use [(](http://php.net/manual/en/function.pathinfo.php) [)](http://php.net/manual/en/function.pathinfo.php) to extrapolate the name and extension in a safe manner but first we need to replace unwanted characters in the file name:

![](Image01705.jpg)

While now we have a filename and extension that can be used for storing, I still prefer storing that information in a

 
| md5 || ( || uniqid || (). || microtime |
| --- | --- | --- | --- | --- |

database and give that file a generated name of for example, ())

![](Image01706.jpg) +----+--------+-----------+------------+------+----------------------------------+----------------

\-----+

| id | title  | extension | mime       | size | filename                         | time

|

+----+--------+-----------+------------+------+----------------------------------+----------------

\-----+

| 1  | myfile | txt       | text/plain | 1020 | 5bcdaeddbfbd2810fa1b6f3118804d66 | 2017-03-11

00:38:54 |

+----+--------+-----------+------------+------+----------------------------------+----------------

\-----+

This would resolve the issue of duplicate file names and unforseen exploits in the file name. It would also cause the attacker to guess where that file has been stored as he or she cannot specifically target it for execution.

Mime-type validation

 
| image || . || png |
| --- | --- | --- |

Checking a file extension to determine what file it is is not enough as a file may named  but may very well contain a php script. By checking the mime-type of the uploaded file against a file extension you can verify if the file contains what its name is referring to.

You can even go 1 step further for validating images, and that is actually opening them:

![](Image01707.jpg)

You can fetch the mime-type using a build-in [function](http://php.net/manual/en/function.mime-content-type.php) or a [class](http://php.net/manual/en/book.fileinfo.php) .

White listing your uploads

Most importantly, you should whitelist file extensions and mime types depending on each form.

![](Image01708.jpg)

# Chapter 102: Cryptography

## Section 102.1: Symmetric Encryption and Decryption of large Files with OpenSSL

PHP lacks a build-in function to encrypt and decrypt large files. openssl\_encrypt can be used to encrypt strings, but loading a huge file into memory is a bad idea.

So we have to write a userland function doing that. This example uses the symmetric [AES-128-CBC](http://stackoverflow.com/a/33124706/1119601) algorithm to encrypt smaller chunks of a large file and writes them into another file.

Encrypt Files

![](Image01709.jpg)

Decrypt Files

To decrypt files that have been encrypted with the above function you can use this function.

![](Image01710.jpg)

How to use

If you need a small snippet to see how this works or to test the above functions, look at the following code.

![](Image01711.jpg)

This will create three files:

1.    testfile.txt with the plain text

2.    testfile.txt.enc with the encrypted file

3.    testfile.txt.dec with the decrypted file. This should have the same content as testfile.txt

## Section 102.2: Symmetric Cipher

This example illustrates the AES 256 symmetric cipher in CBC mode. An initialization vector is needed, so we generate one using an openssl function. The variable $strong is used to determine whether the IV generated was cryptographically strong.

Encryption

$method \= "aes-256-cbc" ; // cipher method

$iv\_length \= openssl\_cipher\_iv\_length ( $method ); // obtain required IV length

$strong \= false ; // set to false for next line

$iv \= openssl\_random\_pseudo\_bytes ( $iv\_length , $strong ); // generate initialization vector

/\* NOTE: The IV needs to be retrieved later, so store it in a database. However, do not reuse the same IV to encrypt the data again. \*/

![](Image01712.jpg) if (! $strong ) { // throw exception if the IV is not cryptographically strong     throw new Exception ( "IV not cryptographically strong!" ); }

$data \= "This is a message to be secured." ; // Our secret message

$pass \= "Stack0verfl0w" ; // Our password

/\* NOTE: Password should be submitted through POST over an HTTPS session.

Here, it's being stored in a variable for demonstration purposes. \*/

$enc\_data \= openssl\_encrypt ( $data , $method , $password , true , $iv ); // Encrypt

Decryption

/\* Retrieve the IV from the database and the password from a POST request \*/

![](Image01713.jpg) $dec\_data \= openssl\_decrypt ( $enc\_data , $method , $pass , true , $iv ); // Decrypt

Base64 Encode & Decode

 
| base64\_encode || () and || base64\_decode |
| --- | --- | --- |

If the encrypted data needs to be sent or stored in printable text, then the () functions should be used respectively.

![](Image01714.jpg)

# Chapter 103: Password Hashing Functions

As more secure web services avoid storing passwords in plain text format, languages such as PHP provide various (undecryptable) hash functions to support the more secure industry standard. This topic provides documentation for proper hashing with PHP.

## Section 103.1: Creating a password hash

 
| [password\_hash](http://php.net/manual/en/function.password-hash.php) |
| --- |

Create password hashes using [(](http://php.net/manual/en/function.password-hash.php) [)](http://php.net/manual/en/function.password-hash.php) to use the current industry best-practice standard hash or key derivation. At time of writing, the standard is [bcrypt](https://en.wikipedia.org/wiki/Bcrypt) , which means, that PASSWORD\_DEFAULT contains the same value

![](Image01715.jpg)

The third parameter is not mandatory .

The 'cost' value should be chosen based on your production server's hardware. Increasing it will make the password more costly to generate. The costlier it is to generate the longer it will take anyone trying to crack it to generate it also. The cost should ideally be as high as possible, but in practice it should be set so it does not slow down everything too much. Somewhere between 0.1 and 0.4 seconds would be okay. Use the default value if you are in doubt.

Version < 5.5

 
| password\_ |
| --- |

On PHP lower than 5.5.0 the \* functions are not available. You should use [the compatibility pack](https://github.com/ircmaxell/password_compat) to substitute those functions. Notice the compatibility pack requires PHP 5.3.7 or higher or a version that has the $2y fix backported into it (such as RedHat provides).

 
| [crypt](http://php.net/manual/en/function.crypt.php) || [(](http://php.net/manual/en/function.crypt.php) [)](http://php.net/manual/en/function.crypt.php) As || password\_hash |
| --- | --- | --- |

 
| crypt |
| --- |

If you are not able to use those, you can implement password hashing with () is implemented as a wrapper around the () function, you need not lose any functionality.

// this is a simple implementation of a bcrypt hash otherwise compatible

// with \`password\_hash()\`

// not guaranteed to maintain the same cryptographic strength of the full \`password\_hash()\`

// implementation

// if \`CRYPT\_BLOWFISH\` is 1, that means bcrypt (which uses blowfish) is available // on your system

if ( CRYPT\_BLOWFISH \== 1) {

    $salt \= mcrypt\_create\_iv (16, MCRYPT\_DEV\_URANDOM );

    $salt \= base64\_encode ( $salt );

    // crypt uses a modified base64 variant

    $source \= 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/' ;

    $dest \= './ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789' ;

    $salt \= strtr ( rtrim ( $salt , '=' ), $source , $dest );

    $salt \= substr ( $salt , 0, 22);

![](Image01716.jpg)     // \`crypt()\` determines which hashing algorithm to use by the form of the salt string     // that is passed in

    $hashedPassword \= crypt ( $plaintextPassword , '$2y$10$' . $salt . '$' );

}

Salt for password hash

Despite of reliability of crypt algorithm there is still vulnerability against [rainbow tables](https://en.wikipedia.org/wiki/Rainbow_table) . That's the reason, why it's recommended to use salt .

A salt is something that is appended to the password before hashing to make source string unique. Given two identical passwords, the resulting hashes will be also unique, because their salts are unique.

A random salt is one of the most important pieces of your password security. This means that even with a lookup table of known password hashes an attacker ca n’ t match up your use r’ s password hash with the database password hashes since a random salt has been used. You should use always random and cryptographically secure salts. [Read more](http://www.springer.com/us/book/9781484221198)

 
| [password\_hash](http://php.net/manual/en/function.password-hash.php) |
| --- |

With [(](http://php.net/manual/en/function.password-hash.php) [)](http://php.net/manual/en/function.password-hash.php) bcrypt algorithm, plain text salt is stored along with the resulting hash, which means that the hash can be transferred across different systems and platforms and still be matched against the original password.

Version < 7.0

Even when this is discouraged, you can use the salt option to define your own random salt.

![](Image01717.jpg)

Important . If you omit this option, a random salt will be generated by password\_hash() for each password hashed. This is the intended mode of operation.

Version ≥ 7.0

The salt option has been [deprecated](http://php.net/manual/ru/function.password-hash.php) as of PHP 7.0.0. It is now preferred to simply use the salt that is generated by default.

## Section 103.2: Determine if an existing password hash can be upgraded to a stronger algorithm

If you are using the PASSWORD\_DEFAULT method to let the system choose the best algorithm to hash your passwords with, as the default increases in strength you may wish to rehash old passwords as users log in

![](Image01718.jpg)

If the password\_\* functions are not available on your system (and you cannot use the compatibility pack linked in the remarks below), you can determine the algorithm and used to create the original hash in a method similar to the following:

![](Image01719.jpg)

## Section 103.3: Verifying a password against a hash

 
| password\_verify |
| --- |

() is the built-in function provided (as of PHP 5.5) to verify the validity of a password against a

known hash.

![](Image01720.jpg)

All supported hashing algorithms store information identifying which hash was used in the hash itself, so there is no need to indicate which algorithm you are using to encode the plaintext password with.

 
| crypt |
| --- |

If the password\_\* functions are not available on your system (and you cannot use the compatibility pack linked in the remarks below) you can implement password verification with the () function. Please note that specific precautions must be taken to avoid [timing attacks](https://en.wikipedia.org/wiki/Timing_attack) .

![](Image01721.jpg)

# Chapter 104: Contributing to the PHP Manual

The PHP Manual provides both a functional reference and a language reference along with explanations of PHP's major features. The PHP Manual, unlike most languages' documentation, encourages PHP developers to add their own examples and notes to each page of the documentation. This topic explains contribution to the PHP manual, along with tips, tricks, and guidelines for best practice.

## Section 104.1: Improve the ocial documentation

PHP has great official documentation already at [http://php.net/manual/](http://php.net/manual/) . The PHP Manual documents pretty much all language features, the core libraries and most available extensions. There are plenty of examples to learn from.

The PHP Manual is available in multiple languages and formats.

Best of all, the documentation is free for anyone to edit .

The PHP Documentation Team provides an online editor for the PHP Manual at [https://edit.php.net](https://edit.php.net/) . It supports multiple Single-Sign-On services, including logging in with your Stack Overflow account. You can find an introduction to the editor at [https://wiki.php.net/doc/editor](https://wiki.php.net/doc/editor) .

Changes to the PHP Manual need to be approved by people from the PHP Documentation Team having Doc Karma . Doc Karma is somewhat like reputation, but harder to get. This peer review process makes sure only factually correct information gets into the PHP Manual.

The PHP Manual is written in DocBook, which is an easy to learn markup language for authoring books. It might look a little bit complicated at first sight, but there are templates to get you started. You certainly don't need to be a DocBook expert to contribute.

## Section 104.2: Tips for contributing to the manual

The following is a list of tips for those who are looking to contribute to the PHP manual:

![](Image01722.jpg)Follow the manual's style guidelines . Ensure that the [manual's style guidelines](http://doc.php.net/tutorial/style.php) are always being followed for consistency's sake.

Perform spelling and grammar checks . Ensure proper spelling and grammar is being used - otherwise the information presented may be more difficult to assimilate, and the content will look less professional. Be terse in explanations . Avoid rambling to clearly and concisely present the information to developers who are looking to quickly reference it.

Separate code from its output . This gives cleaner and less convoluted code examples for developers to digest.

Check the page section order . Ensure that all sections of the manual page being edited are in the correct order. Uniformity in the manual makes it easier to quickly read and lookup information.

Remove PHP 4-related content . Specific mentions to PHP 4 are no longer relevant given how old it is now.

Mentions of it should be removed from the manual to prevent convoluting it with unnecessary information. Properly version files . When creating new files in the documentation, ensure that the revision ID of the file is set to nothing, like so: <!-- $Revision$ --> .

Merge useful comments into the manual . Some comments contribute useful information that the manual could benefit from having. These should be merged into the main page's content.

Don't break the documentation build . Always ensure that the PHP manual builds properly before committing the changes.

# Chapter 105: Contributing to the PHP Core

## Section 105.1: Setting up a basic development environment

PHP's source code is hosted on [GitHub](https://github.com/php/php-src) . To build from source you will first need to check out a working copy of the code.

![](Image01723.jpg)

If you want to add a feature, it's best to create your own branch.

![](Image01724.jpg)

Finally, configure and build PHP

![](Image01725.jpg)

If configuration fails due to missing dependencies, you will need to use your operating system's package management system to install them (e.g. yum , apt , etc.) or download and compile them from source.

  

# Appendix A: Installing a PHP environment on Windows

## Section A.1: Download, Install and use WAMP

WampServer is a Windows web development environment. It allows you to create web applications with Apache2, PHP and a MySQL database. Alongside, PhpMyAdmin allows you to manage easily your databases.

WampServer is available for free (under GPML license) in two distinct versions : 32 and 64 bits. Wampserver 2.5 is not compatible with Windows XP, neither with SP3, nor Windows Server 2003. Older WampServer versions are available on [SourceForge](https://sourceforge.net/projects/wampserver/files/) .

WampServer versions:

![](Image01726.jpg)[WampServer (64 BITS) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x64_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)

[WampServer (32 BITS) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x86_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)

Providing currently:

![](Image01727.jpg)Apache: 2.4.18

MySQL: 5.7.11

PHP: 5.6.19 & 7.0.4

Installation is simple, just execute the installer, choose the location and finish it.

Once that is done, you may start WampServer. Then it starts in the system tray (taskbar), initially red in color and then turns green once the server is up.

You may goto a browser and type localhost or 127.0.0.1 to get the index page of WAMP. You may work on PHP

 
| PATH\_TO\_WAMP \>/ www /< php\_or\_html\_file |
| --- |

locally from now by storing the files in <> and check the result on

 
| http || : || //localhost/<php\_or\_html\_file\_name> |
| --- | --- | --- |

## Section A.2: Install PHP and use it with IIS

First of all you need to have IIS ( Internet Information Services ) installed and running on your machine; IIS isn't available by default, you have to add the characteristic from Control Panel -> Programs -> Windows Characteristics.

1.        Download the PHP version you like from [http://windows.php.net/download/](http://windows.php.net/download/) and make sure you download the Non-Thread Safe (NTS) versions of PHP.

 
| \\PHP\\ |
| --- |

2.        Extract the files into C : .

3.        Open the Internet Information Services Administrator IIS .

4.        Select the root item in the left panel.

5.        Double click on Handler Mappings .

6.        On the right side panel click on Add Module Mapping .

7.        Setup the values like this:

![](Image01728.jpg)

 
| vcredist\_x64 || . || exe || or || vcredist\_x86 || . || exe |
| --- | --- | --- | --- | --- | --- | --- |

8.        Install  (Visual C++ 2012 Redistributable) from [https://www.microsoft.com/en-US/download/details.aspx?id=30679](https://www.microsoft.com/en-US/download/details.aspx?id=30679)

 
| \\PHP\\php || . || ini || , especially set the || extension\_dir || \= || "C:\\PHP\\ext" |
| --- | --- | --- | --- | --- | --- | --- |

9.        Setup your C : .

10.    Reset IIS: In a DOS command console type IISRESET .

Optionally you can install the [PHP Manager for IIS](https://phpmanager.codeplex.com/) which is of great help to setup the ini file and track the log of errors (doesn't work on Windows 10).

 
| index || . || php |
| --- | --- | --- |

Remember to set  as one of the default documents for IIS.

If you followed the installation guide now you are ready to test PHP.

 
| \\inetpub\\wwwroot\\ |
| --- |

Just like Linux, IIS has a directory structure on the server, the root of this tree is C : , here is the point of entry for all your public files and PHP scripts.

Now use your favorite editor, or just Windows Notepad, and type the following:

![](Image01729.jpg)

 
| \\inetpub\\wwwroot\\index || . || php |
| --- | --- | --- |

Save the file under C : using the UTF-8 format (without BOM).

Then open your brand new website using your browser on this address: [http://localhost/index.php](http://localhost/index.php)

## Section A.3: Download and Install XAMPP

What is XAMPP?

XAMPP is the most popular PHP development environment. XAMPP is a completely free, open-source and easy to install Apache distribution containing MariaDB, PHP, and Perl.

Where should I download it from?

Download appropriate stable XAMPP version from [their download page](http://www.apachefriends.org/download.html) . Choose the download based on the type of OS (32 or 64bit and OS version) and the PHP version it has to support.

Current latest being [XAMPP for Windows 7.0.8 / PHP 7.0.8](http://www.apachefriends.org/xampp-files/7.0.8/xampp-win32-7.0.8-0-VC14-installer.exe) .

Or you can follow this:

XAMPP for Windows exists in three different flavors:

 
| exe format |
| --- |

 
| zip format |
| --- |

 
| 7zip format |
| --- |

![](Image01730.jpg)[Installer](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14-installer.exe/download) (Probably . the easiest way to install XAMPP)

[ZIP](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.zip/download) (For purists: XAMPP as ordinary ZIP . archive)

[7zip:](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.7z/download) (For purists with low bandwidth: XAMPP as 7zip . archive)

How to install and where should I place my PHP/html files?

Install with the provided installer

 
| exe |
| --- |

1\. Execute the XAMPP server installer by double clicking the downloaded . .

Install from the ZIP

1.    Unzip the zip archives into the folder of your choice.

 
| \\xampp |
| --- |

2.    XAMPP is extracting to the subdirectory C : below the selected target directory.

 
| setup\_xampp || . || bat |
| --- | --- | --- |

3.    Now start the file , to adjust the XAMPP configuration to your system.

 
| setup\_xampp || . || bat |
| --- | --- | --- |

![](Image01731.jpg)Note: If you choose a root directory C : \\ as target, you must not start               .

Post-Install

Use the "XAMPP Control Panel" for additional tasks, like starting/stopping Apache, MySQL, FileZilla and Mercury or installing these as services.

File handling

The installation is a straight forward process and once the installation is complete you may add html/php files to be

 
| XAMPP || \- || root || / || htdocs || / . Then start the server and open || http || : || //localhost/file.php |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

hosted on the server in  on a browser to view the page.

 
| :/ xampp || / || htdocs |
| --- | --- | --- |

![](Image01732.jpg)Note: Default XAMPP root in Windows is C /

Type in one of the following URLs in your favourite web browser:

![](Image01733.jpg)

Now you should see the XAMPP start page.

  

![](Image01734.jpg)

# Appendix B: Installing on Linux/Unix Environments

## Section B.1: Command Line Install Using APT for PHP 7

 
| sudo add-apt-repository ppa:ondrej / php |
| --- |

![](Image01735.jpg)This will only install PHP. If you wish to serve a PHP file to the web you will also need to install a webserver such as [Apache](http://www.apache.org/) , [Nginx](https://www.nginx.com/) , or use [PHP's built in web-server](http://php.net/manual/en/features.commandline.webserver.php) ( php version 5.4+ ).

If you are in a Ubuntu version below 16.04 and want to use PHP 7 anyway, you can add [Ondrej's PPA](https://launchpad.net/%7Eondrej/+archive/ubuntu/php/) [repository](https://launchpad.net/%7Eondrej/+archive/ubuntu/php/) by doing:

Make sure that all of your [repositories](https://en.wikipedia.org/wiki/Software_repository) are up to date:

![](Image01736.jpg)

After updating your system's repositories, install PHP:

![](Image01737.jpg)

Let's test the installation by checking the PHP version:

![](Image01738.jpg)

This should output something like this.

Note: Your output will be slightly different.

PHP 7.0.8-0ubuntu0.16.04.1 (cli) ( NTS )

Copyright (c) 1997-2016 The PHP Group

![](Image01739.jpg) Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies with Zend OPcache v7.0.8-0ubuntu0.16.04.1, Copyright (c) 1999-2016, by Zend Technologies with Xdebug v2.4.0, Copyright (c) 2002-2016, by Derick Rethans

You now have the capability to run PHP from the command line.

## Section B.2: Installing in Enterprise Linux distributions (CentOS, Scientific Linux, etc)

Use the yum command to manage packages in Enterprise Linux-based operating systems:

![](Image01740.jpg)

This installs a minimal install of PHP including some common features. If you need additional modules, you will need to install them separately. Once again, you can use yum to search for these packages:

![](Image01741.jpg)

Example output:

![](Image01742.jpg) php-bcmath.x86\_64 : A module for PHP applications for using the bcmath library php-cli.x86\_64 : Command-line interface for PHP php-common.x86\_64 : Common files for PHP php-dba.x86\_64 : A database abstraction layer module for PHP applications php-devel.x86\_64 : Files needed for building PHP extensions php-embedded.x86\_64 : PHP library for embedding in applications php-enchant.x86\_64 : Human Language and Character Encoding Support php-gd.x86\_64 : A module for PHP applications for using the gd graphics library php-imap.x86\_64 : A module for PHP applications that use IMAP

To install the gd library:

![](Image01743.jpg)

Enterprise Linux distributions have always been conservative with updates, and typically do not update beyond the point release they shipped with. A number of third party repositories provide current versions of PHP:

![](Image01744.jpg)[IUS](https://ius.io/)

[Remi Colette](http://www.remirepo.net/)

[Webtatic](https://webtatic.com/)

  

#