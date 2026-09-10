![](images/title_page.jpg)

![Advanced PHP Strings](images/title_page.jpg)

## Advanced PHP Strings

### Text analysis, generation, and parsing via. Laravel

 

#### Johnathon Koster

 

這本書的網址是 [http://leanpub.com/eyeofthedragon\_writing](http://leanpub.com/eyeofthedragon_writing)

此版本發布於 2022-10-14

![publisher's logo](images/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](https://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](https://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2022 Johnathon Koster 

Carla and Eric, for whom “actions speak louder than words,” applies more than most.

## 書籍目錄

1.  [Introduction](#chap00.xhtml#leanpub-auto-introduction) 
    1.  [PHP Version](#chap00.xhtml#leanpub-auto-php-version)
    2.  [Laravel Version](#chap00.xhtml#leanpub-auto-laravel-version)
    3.  [Symbols Used In This Book](#chap00.xhtml#leanpub-auto-symbols-used-in-this-book)
2.  [1\. What are Strings](#chap01.xhtml#leanpub-auto-what-are-strings) 
    1.  [1.1 A Brief History of Character Encodings](#chap01.xhtml#leanpub-auto-a-brief-history-of-character-encodings)
    2.  [1.2 Unicode and UTF-8](#chap01.xhtml#leanpub-auto-unicode-and-utf-8)
    3.  [1.3 Implementing Upper and Lowercase Functions](#chap01.xhtml#leanpub-auto-implementing-upper-and-lowercase-functions)
    4.  [1.4 Iterating Multibyte Strings](#chap01.xhtml#leanpub-auto-iterating-multibyte-strings)
    5.  [1.5 Accessing Individual Characters in a UTF-8 String](#chap01.xhtml#leanpub-auto-accessing-individual-characters-in-a-utf-8-string)
    6.  [1.6 Managing Character Encodings](#chap01.xhtml#leanpub-auto-managing-character-encodings)
    7.  [1.7 Types of PHP Strings](#chap01.xhtml#leanpub-auto-types-of-php-strings)
    8.  [1.8 Backticks and Template Strings](#chap01.xhtml#leanpub-auto-backticks-and-template-strings)
    9.  [1.9 The Laravel String Helpers](#chap01.xhtml#leanpub-auto-the-laravel-string-helpers)
3.  [2\. Fluent Strings](#chap02.xhtml#leanpub-auto-fluent-strings) 
    1.  [2.1 Converting Fluent String Objects to Strings](#chap02.xhtml#leanpub-auto-converting-fluent-string-objects-to-strings)
    2.  [2.2 Conditional String Logic](#chap02.xhtml#leanpub-auto-conditional-string-logic)
4.  [3\. The Formatting Helper Methods](#chap03.xhtml#leanpub-auto-the-formatting-helper-methods) 
    1.  [3.1 Formatting Strings with camelCasing](#chap03.xhtml#leanpub-auto-formatting-strings-with-camelcasing)
    2.  [3.2 Formatting Headlines](#chap03.xhtml#leanpub-auto-formatting-headlines)
    3.  [3.3 Formatting Strings with “kebab-casing”](#chap03.xhtml#leanpub-auto-formatting-strings-with-kebab-casing)
    4.  [3.4 Lowercasing the First Character of a String](#chap03.xhtml#leanpub-auto-lowercasing-the-first-character-of-a-string)
    5.  [3.5 Creating Lowercase Variants of Strings](#chap03.xhtml#leanpub-auto-creating-lowercase-variants-of-strings)
    6.  [3.6 Reversing the Characters of a String](#chap03.xhtml#leanpub-auto-reversing-the-characters-of-a-string)
    7.  [3.7 Creating a URL from a Title](#chap03.xhtml#leanpub-auto-creating-a-url-from-a-title)
    8.  [3.8 Formatting Strings with snake\_casing](#chap03.xhtml#leanpub-auto-formatting-strings-with-snakecasing)
    9.  [3.9 Removing Extra Whitespace from a String](#chap03.xhtml#leanpub-auto-removing-extra-whitespace-from-a-string)
    10.  [3.10 Formatting Strings with StudlyCasing](#chap03.xhtml#leanpub-auto-formatting-strings-with-studlycasing)
    11.  [3.11 Formatting Strings with Title Casing](#chap03.xhtml#leanpub-auto-formatting-strings-with-title-casing)
    12.  [3.12 Uppercasing the First Character of a String](#chap03.xhtml#leanpub-auto-uppercasing-the-first-character-of-a-string)
    13.  [3.13 Generating Upper Cased Variants of Strings](#chap03.xhtml#leanpub-auto-generating-upper-cased-variants-of-strings)
    14.  [3.14 Counting the Number of Words in a String](#chap03.xhtml#leanpub-auto-counting-the-number-of-words-in-a-string)
5.  [4\. The Logical Helper Methods](#chap04.xhtml#leanpub-auto-the-logical-helper-methods) 
    1.  [4.1 Checking If a String Contains Another String](#chap04.xhtml#leanpub-auto-checking-if-a-string-contains-another-string)
    2.  [4.2 Checking If a String Contains Multiple Substrings](#chap04.xhtml#leanpub-auto-checking-if-a-string-contains-multiple-substrings)
    3.  [4.3 Checking If a String Ends with Another String](#chap04.xhtml#leanpub-auto-checking-if-a-string-ends-with-another-string)
    4.  [4.4 Checking If a String Starts with Another String](#chap04.xhtml#leanpub-auto-checking-if-a-string-starts-with-another-string)
    5.  [4.5 Checking If a String Contains Only ASCII Characters](#chap04.xhtml#leanpub-auto-checking-if-a-string-contains-only-ascii-characters)
6.  [5\. The Construction Helper Methods](#chap05.xhtml#leanpub-auto-the-construction-helper-methods) 
    1.  [5.1 Transliterating Characters to ASCII](#chap05.xhtml#leanpub-auto-transliterating-characters-to-ascii) 
        1.  [Language Codes](#chap05.xhtml#leanpub-auto-language-codes)
    2.  [5.2 Generating Excerpts of Text](#chap05.xhtml#leanpub-auto-generating-excerpts-of-text)
    3.  [5.3 Ensuring a String Always Ends with a Given String](#chap05.xhtml#leanpub-auto-ensuring-a-string-always-ends-with-a-given-string)
    4.  [5.4 Calculating String Length](#chap05.xhtml#leanpub-auto-calculating-string-length)
    5.  [5.5 Truncating Strings](#chap05.xhtml#leanpub-auto-truncating-strings)
    6.  [5.6 Obscuring Parts of a String](#chap05.xhtml#leanpub-auto-obscuring-parts-of-a-string) 
        1.  [You Probably Shouldn’t Store Credit Card Numbers](#chap05.xhtml#leanpub-auto-you-probably-shouldnt-store-credit-card-numbers)
    7.  [5.7 Generating Pseudo-Random Strings](#chap05.xhtml#leanpub-auto-generating-pseudo-random-strings)
    8.  [5.8 Removing Substrings or Characters from Strings](#chap05.xhtml#leanpub-auto-removing-substrings-or-characters-from-strings)
    9.  [5.9 Repeating Strings and Characters](#chap05.xhtml#leanpub-auto-repeating-strings-and-characters)
    10.  [5.10 Replacing Substrings](#chap05.xhtml#leanpub-auto-replacing-substrings)
    11.  [5.11 Sequentially Replacing Substrings in a String](#chap05.xhtml#leanpub-auto-sequentially-replacing-substrings-in-a-string)
    12.  [5.12 Replacing the First Occurrence of a Substring or Character](#chap05.xhtml#leanpub-auto-replacing-the-first-occurrence-of-a-substring-or-character)
    13.  [5.13 Replacing the Last Occurrence of a Substring or Character](#chap05.xhtml#leanpub-auto-replacing-the-last-occurrence-of-a-substring-or-character)
    14.  [5.14 Ensuring Strings Always Begin with a Specific Prefix](#chap05.xhtml#leanpub-auto-ensuring-strings-always-begin-with-a-specific-prefix)
    15.  [5.15 Replacing a Key/Value Pair of Strings within a String](#chap05.xhtml#leanpub-auto-replacing-a-keyvalue-pair-of-strings-within-a-string)
    16.  [5.16 Splitting Strings on Uppercase Characters](#chap05.xhtml#leanpub-auto-splitting-strings-on-uppercase-characters)
7.  [6\. The Extraction Helper Methods](#chap06.xhtml#leanpub-auto-the-extraction-helper-methods) 
    1.  [6.1 Returning Part of a String after Another String or Character](#chap06.xhtml#leanpub-auto-returning-part-of-a-string-after-another-string-or-character)
    2.  [6.2 Returning a Substring after the Last Occurrence of a String or Character](#chap06.xhtml#leanpub-auto-returning-a-substring-after-the-last-occurrence-of-a-string-or-character)
    3.  [6.3 Returning Part of a String before Another String or Character](#chap06.xhtml#leanpub-auto-returning-part-of-a-string-before-another-string-or-character)
    4.  [6.4 Retrieving All Content before the Last Occurrence of a Substring or Character](#chap06.xhtml#leanpub-auto-retrieving-all-content-before-the-last-occurrence-of-a-substring-or-character)
    5.  [6.5 Retrieving Content between Two Search Strings](#chap06.xhtml#leanpub-auto-retrieving-content-between-two-search-strings)
    6.  [6.6 Retrieving the Smallest Amount of Content between Two Search Strings](#chap06.xhtml#leanpub-auto-retrieving-the-smallest-amount-of-content-between-two-search-strings)
    7.  [6.7 Limiting the Number of Words in a String](#chap06.xhtml#leanpub-auto-limiting-the-number-of-words-in-a-string)
    8.  [6.8 Getting Portions of a String](#chap06.xhtml#leanpub-auto-getting-portions-of-a-string)
    9.  [6.9 Counting Occurrences of a Search String](#chap06.xhtml#leanpub-auto-counting-occurrences-of-a-search-string)
    10.  [6.10 Replacing Strings within a Portion of an Existing String](#chap06.xhtml#leanpub-auto-replacing-strings-within-a-portion-of-an-existing-string)
8.  [7\. Padding Strings](#chap07.xhtml#leanpub-auto-padding-strings) 
    1.  [7.1 Padding the Beginning of Strings](#chap07.xhtml#leanpub-auto-padding-the-beginning-of-strings)
    2.  [7.2 Padding the End of Strings](#chap07.xhtml#leanpub-auto-padding-the-end-of-strings)
    3.  [7.3 Padding Both Sides of a String](#chap07.xhtml#leanpub-auto-padding-both-sides-of-a-string)
9.  [8\. String Translations; Singular and Plural Word Forms](#chap08.xhtml#leanpub-auto-string-translations-singular-and-plural-word-forms) 
    1.  [8.1 Working with Variable Replacements](#chap08.xhtml#leanpub-auto-working-with-variable-replacements)
    2.  [8.2 Managing Ranges of Items](#chap08.xhtml#leanpub-auto-managing-ranges-of-items)
    3.  [8.3 Singular and Plural Word Forms](#chap08.xhtml#leanpub-auto-singular-and-plural-word-forms)
10.  [9\. Extending Strings with Macros and Mixins](#chap09.xhtml#leanpub-auto-extending-strings-with-macros-and-mixins)
11.  [10\. Lines and Words](#chap10.xhtml#leanpub-auto-lines-and-words) 
     1.  [10.1 Positions, Lines, and Columns](#chap10.xhtml#leanpub-auto-positions-lines-and-columns)
     2.  [10.2 Splitting Strings into Words](#chap10.xhtml#leanpub-auto-splitting-strings-into-words)
     3.  [10.3 Counting Word Occurrences](#chap10.xhtml#leanpub-auto-counting-word-occurrences)
     4.  [10.4 Finding Frequent and Repeated Words](#chap10.xhtml#leanpub-auto-finding-frequent-and-repeated-words)
     5.  [10.5 Stop Words](#chap10.xhtml#leanpub-auto-stop-words)
     6.  [10.6 Constructing Initialisms and Acronyms](#chap10.xhtml#leanpub-auto-constructing-initialisms-and-acronyms)
     7.  [10.7 Calculating Estimated Reading Time](#chap10.xhtml#leanpub-auto-calculating-estimated-reading-time)
12.  [11\. More Lines and Words](#chap11.xhtml#leanpub-auto-more-lines-and-words) 
     1.  [11.1 Locating Words at Arbitrary Positions](#chap11.xhtml#leanpub-auto-locating-words-at-arbitrary-positions)
     2.  [11.2 Locating Neighboring Words and Characters](#chap11.xhtml#leanpub-auto-locating-neighboring-words-and-characters)
     3.  [11.3 Retrieving Adjacent Lines](#chap11.xhtml#leanpub-auto-retrieving-adjacent-lines)
     4.  [11.4 Managing Text Indentation](#chap11.xhtml#leanpub-auto-managing-text-indentation)
     5.  [11.5 Implementing an IndentationManager Class](#chap11.xhtml#leanpub-auto-implementing-an-indentationmanager-class)
13.  [12\. Applied Techniques: Writing a Gherkin Parser](#chap12.xhtml#leanpub-auto-applied-techniques-writing-a-gherkin-parser) 
     1.  [12.1 Modeling Gherkin](#chap12.xhtml#leanpub-auto-modeling-gherkin)
     2.  [12.2 A Gherkin Lexer](#chap12.xhtml#leanpub-auto-a-gherkin-lexer)
     3.  [12.3 Implementing Our Gherkin Parser](#chap12.xhtml#leanpub-auto-implementing-our-gherkin-parser) 
         1.  [Parsing Gherkin Comments](#chap12.xhtml#leanpub-auto-parsing-gherkin-comments)
         2.  [Parsing Names](#chap12.xhtml#leanpub-auto-parsing-names)
         3.  [Parsing Step Text](#chap12.xhtml#leanpub-auto-parsing-step-text)
         4.  [Parsing Free-Form Gherkin Descriptions](#chap12.xhtml#leanpub-auto-parsing-free-form-gherkin-descriptions)
         5.  [Parsing Scenario Tags](#chap12.xhtml#leanpub-auto-parsing-scenario-tags)
         6.  [Parsing Step Parameters](#chap12.xhtml#leanpub-auto-parsing-step-parameters)
         7.  [Parsing Doc Strings](#chap12.xhtml#leanpub-auto-parsing-doc-strings)
         8.  [Parsing Gherkin Data Tables](#chap12.xhtml#leanpub-auto-parsing-gherkin-data-tables)
         9.  [Parsing Scenario Examples](#chap12.xhtml#leanpub-auto-parsing-scenario-examples)
         10.  [Parsing Steps](#chap12.xhtml#leanpub-auto-parsing-steps)
         11.  [Parsing a Single Scenario and Background](#chap12.xhtml#leanpub-auto-parsing-a-single-scenario-and-background)
         12.  [Parsing Scenario Outlines and Templates](#chap12.xhtml#leanpub-auto-parsing-scenario-outlines-and-templates)
         13.  [Parsing Multiple Scenarios](#chap12.xhtml#leanpub-auto-parsing-multiple-scenarios)
         14.  [Parsing a Single Rule and Multiple Rules](#chap12.xhtml#leanpub-auto-parsing-a-single-rule-and-multiple-rules)
         15.  [Parsing Features](#chap12.xhtml#leanpub-auto-parsing-features)
     4.  [12.4 Adding Localization Support to the Gherkin Parser](#chap12.xhtml#leanpub-auto-adding-localization-support-to-the-gherkin-parser)
     5.  [12.5 Other Applications of Indentation-Based Parsers](#chap12.xhtml#leanpub-auto-other-applications-of-indentation-based-parsers)
14.  [13\. Markov Chains and Text Generation](#chap13.xhtml#leanpub-auto-markov-chains-and-text-generation) 
     1.  [13.1 Writing a Markov Text Generator](#chap13.xhtml#leanpub-auto-writing-a-markov-text-generator)
     2.  [13.2 Weighted Randomized Selection](#chap13.xhtml#leanpub-auto-weighted-randomized-selection)
     3.  [13.3 Improving Our Text Generator](#chap13.xhtml#leanpub-auto-improving-our-text-generator)
15.  [14\. Fixed Width Data Parsing](#chap14.xhtml#leanpub-auto-fixed-width-data-parsing) 
     1.  [14.1 Managing Data Conversions](#chap14.xhtml#leanpub-auto-managing-data-conversions)
     2.  [14.2 Updating an Individual Record’s Values](#chap14.xhtml#leanpub-auto-updating-an-individual-records-values)
     3.  [14.3 Techniques for Managing Text Truncation](#chap14.xhtml#leanpub-auto-techniques-for-managing-text-truncation)
16.  [15\. Splitting Strings](#chap15.xhtml#leanpub-auto-splitting-strings) 
     1.  [15.1 Basic String Splitting](#chap15.xhtml#leanpub-auto-basic-string-splitting)
     2.  [15.2 Splitting Strings Using Regular Expressions](#chap15.xhtml#leanpub-auto-splitting-strings-using-regular-expressions)
     3.  [15.3 Extracting YAML Frontmatter from Documents](#chap15.xhtml#leanpub-auto-extracting-yaml-frontmatter-from-documents)
     4.  [15.4 Parsing Single-File Components](#chap15.xhtml#leanpub-auto-parsing-single-file-components)
     5.  [15.5 Splitting Input Containing Substrings with the Delimiter](#chap15.xhtml#leanpub-auto-splitting-input-containing-substrings-with-the-delimiter)
     6.  [15.6 Implementing a String Cursor System](#chap15.xhtml#leanpub-auto-implementing-a-string-cursor-system)
     7.  [15.7 Implementing the StringsCursor](#chap15.xhtml#leanpub-auto-implementing-the-stringscursor)
     8.  [15.8 Implementing the ClosureStringCursor](#chap15.xhtml#leanpub-auto-implementing-the-closurestringcursor)
     9.  [15.9 A Simple PHP Tokenizer](#chap15.xhtml#leanpub-auto-a-simple-php-tokenizer)
     10.  [15.10 Working with SQL-Style Strings](#chap15.xhtml#leanpub-auto-working-with-sql-style-strings)
     11.  [15.11 Splitting Strings Containing Paired Brackets](#chap15.xhtml#leanpub-auto-splitting-strings-containing-paired-brackets)
17.  [16\. Applied Techniques: A Blade Directive Validator](#chap16.xhtml#leanpub-auto-applied-techniques-a-blade-directive-validator) 
     1.  [16.1 Scaffolding our Parser Implementation](#chap16.xhtml#leanpub-auto-scaffolding-our-parser-implementation)
     2.  [16.2 Parsing Blade Directives](#chap16.xhtml#leanpub-auto-parsing-blade-directives)
     3.  [16.3 Parsing Directive Parameters](#chap16.xhtml#leanpub-auto-parsing-directive-parameters)
     4.  [16.4 Validating Blade Directives](#chap16.xhtml#leanpub-auto-validating-blade-directives)
     5.  [16.5 Ensuring Consistent Directive Casing](#chap16.xhtml#leanpub-auto-ensuring-consistent-directive-casing)
     6.  [16.6 Enforcing Spacing after Directive Names](#chap16.xhtml#leanpub-auto-enforcing-spacing-after-directive-names)
18.  [17\. Working with HTML](#chap17.xhtml#leanpub-auto-working-with-html) 
     1.  [17.1 Reversing Double Encoded HTML Entities](#chap17.xhtml#leanpub-auto-reversing-double-encoded-html-entities)
     2.  [17.2 Working with Embedded Languages](#chap17.xhtml#leanpub-auto-working-with-embedded-languages)
     3.  [17.3 Parsing Fragmented HTML Documents](#chap17.xhtml#leanpub-auto-parsing-fragmented-html-documents)
     4.  [17.4 Parsing HTML Attributes and Parameters](#chap17.xhtml#leanpub-auto-parsing-html-attributes-and-parameters)
     5.  [17.5 Analyzing Fragmented HTML Documents](#chap17.xhtml#leanpub-auto-analyzing-fragmented-html-documents)
19.  [18\. Regular Expressions](#chap18.xhtml#leanpub-auto-regular-expressions) 
     1.  [18.1 Regular Expression Syntax Primer](#chap18.xhtml#leanpub-auto-regular-expression-syntax-primer) 
         1.  [Meta-Characters](#chap18.xhtml#leanpub-auto-meta-characters)
         2.  [Anchors](#chap18.xhtml#leanpub-auto-anchors)
         3.  [Escape Sequences](#chap18.xhtml#leanpub-auto-escape-sequences)
         4.  [Character Classes](#chap18.xhtml#leanpub-auto-character-classes)
         5.  [Sub-Patterns, Capture Groups, and Non-Capturing Groups](#chap18.xhtml#leanpub-auto-sub-patterns-capture-groups-and-non-capturing-groups)
         6.  [Repeating Characters and Patterns](#chap18.xhtml#leanpub-auto-repeating-characters-and-patterns)
         7.  [Ensuring Matches Do Not Start or End with a Specific Pattern](#chap18.xhtml#leanpub-auto-ensuring-matches-do-not-start-or-end-with-a-specific-pattern)
20.  [Appendix A: UTF-8 String Iterator Implementation](#chap19.xhtml#leanpub-auto-appendix-a-utf-8-string-iterator-implementation)
21.  [Appendix B: CharacterPositionLocator Implementation](#chap20.xhtml#leanpub-auto-appendix-b-characterpositionlocator-implementation)
22.  [Appendix C: IndentationManager Implementation](#chap21.xhtml#leanpub-auto-appendix-c-indentationmanager-implementation)
23.  [Appendix D: Gherkin Parser Implementation](#chap22.xhtml#leanpub-auto-appendix-d-gherkin-parser-implementation)
24.  [Appendix E: Markov Chain Implementation](#chap23.xhtml#leanpub-auto-appendix-e-markov-chain-implementation)
25.  [Appendix F: Single-File Component Parser Implementation](#chap24.xhtml#leanpub-auto-appendix-f-single-file-component-parser-implementation)
26.  [Appendix G: String Cursor Implementation](#chap25.xhtml#leanpub-auto-appendix-g-string-cursor-implementation)
27.  [Appendix H: String Cursors](#chap26.xhtml#leanpub-auto-appendix-h-string-cursors)
28.  [Appendix I: Blade Directive Validator Implementation](#chap27.xhtml#leanpub-auto-appendix-i-blade-directive-validator-implementation)
29.  [Appendix J: HTML Fragments Parser and Analyzer Implementation](#chap28.xhtml#leanpub-auto-appendix-j-html-fragments-parser-and-analyzer-implementation)
30.  [備註](#chap29.xhtml#leanpub-endnotes)

## Guide

1.  [Begin Reading](#chap00.xhtml)

## Introduction

We will cover many topics throughout this book, from working with Unicode character sets and the Laravel helper methods to parsing and splitting complex strings. This book has been arranged such that each topic builds off the concepts that appear before it within the book, but there is no particular recommended order for reading this book.

You are encouraged to find a topic that interests you and jump to that section. When doing so, you may find that the discussion references previous items discussed in the book. When this happens, you may continue reading through your selected section. If the examples become challenging, you may wish to return to earlier parts of the book that help build foundational knowledge for your chosen area.

The topics listed below do not include everything each chapter provides and are intended to help give a general idea of what each chapter contains beyond its title. Exploration of this book’s content is encouraged!

**Chapter 1: What are Strings**: This chapter covers Unicode, UTF-8, the different types of PHP strings, and techniques to iterate multi-byte PHP strings.

**Chapter 2: Fluent Strings**: This chapter introduces Laravel’s fluent string helper class, which is used extensively throughout the book.

**Chapter 3: The Formatting Helper Methods**: This chapter covers the Laravel string helper methods that are typically used to help format or transform an existing string in some way. Examples include title casing and converting titles to URL slugs.

**Chapter 4: The Logical Helper Methods**: The logical helper methods assist in making decisions around our strings. Topics include determining if an input string contains one or more other strings and checking if our text starts or ends with particular values.

**Chapter 5: The Construction Helper Methods**: The construction helper methods allow us to generate new strings from existing input or to construct pseudo-random strings. Topics include replacing substrings using various techniques and ensuring input always ends with a given character sequence.

**Chapter 6: The Extraction Helper Methods**: The extraction helper methods are a set of utility methods that allow us to retrieve parts of existing strings using various techniques. Examples include converting input into a list of words and retrieving the content between two search strings.

**Chapter 7: Padding Strings**: This chapter thoroughly discusses the concept of string padding. Topics include simple string padding, advanced methods for number formatting, and more.

**Chapter 8: String Translations; Singular and Plural Word Forms**: This chapter discusses the various features Laravel provides to help work with, manage, and manipulate translation strings.

**Chapter 9: Extending Laravel Strings with Macros and Mixins**: This chapter provides an overview of how to extend Laravel’s string helper class and the fluent string class. Extending the Laravel helpers is used frequently throughout this book.

**Chapter 10: Lines and Words**: This chapter focuses on extracting line and column information from the input text and various techniques to extract and analyze words.

**Chapter 11: More Lines and Words**: This chapter continues the discussion surrounding lines and words and offers techniques for retrieving adjacent words and characters from arbitrary positions. Additional topics include calculating an estimated reading time and generating initialisms from input text.

**Chapter 12: Applied Techniques: Writing a Gherkin Parser**: This in-depth chapter utilizes techniques discussed in previous chapters to build a Gherkin parser from start to finish.

**Chapter 13: Markov Chains and Text Generation**: This chapter explores generating randomized text using Markov Chains. The discussion includes creating our training methods and implementing a weighted selecting algorithm to help generate our text.

**Chapter 14: Fixed With Data Parsing**: This chapter discusses various techniques for parsing fixed-width data commonly found in exports from financial institutions.

**Chapter 15: Splitting Strings**: The discussions in this chapter surround advanced techniques and methods for splitting complicated input text using non-trivial rules and requirements. The discussion concludes with building a general-purpose, reusable cursor system to make extracting information from strings easier.

**Chapter 16: Applied Techniques: A Blade Directive Validator**: This chapter applies most of the techniques covered in the book to implement a simple Blade directive parser and validation system. Validation logic includes detecting when directives are missing required arguments, have inconsistent spacing, or when errant newlines may cause compiler errors.

**Chapter 17: Working with HTML**: This chapter explores techniques for reading and manipulating HTML documents using Symfony framework components. Methods are also examined for parsing and analyzing semantically invalid HTML documents, such as those that contain embedded templating languages.

**Chapter 18: Regular Expressions**: The discussion of this chapter focuses on the most common regular expression features encountered when working on various code bases. Topics include the Laravel pattern-matching methods, negative look-behinds, and a regular expression language primer.

### PHP Version

Throughout this book, we will explore many different concepts and ideas through many code examples. PHP 8 was used throughout the writing process, but the code examples can be adapted to any modern PHP version.

As a consequence of deciding to use PHP 8, there was no consideration made for the overloading of the standard string functions using PHP’s function overloading feature, as this was removed in PHP version 8.0.0^([1](#chap29.xhtml#fn-funcoverload)).

### Laravel Version

The most recent version of Laravel, version 9.26.1, was used when writing the examples we will find throughout the book. Because of the frequency of updates to the Laravel framework, there may be delays in seeing newly added helper methods covered throughout the various chapters.

Although we will assume the most recent version of Laravel for our code examples and exercises, the method signatures will outline any difference between Laravel 8 and Laravel 9 to help upgrade processes.

When we introduce new helper methods throughout the book, we will see an overview of the signature of the method. Where we would typically see a description of the method in typical PHP source code, we will see which versions of the Laravel framework support the helper method.

For example, the `lcfirst` helper method was introduced in Laravel 9 and will have the following method signature:

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 9
 5  *
 6  * @return string
 7  */
 8 public static function lcfirst(
 9     string $string
10 );
```

In contrast, the `lower` helper method appears in Laravel versions 8 and 9, with no differences in the method signature between the two versions:

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function lower(
 9     string $value
10 );
```

If a helper method is present in both Laravel 8 and 9 but has a different signature between the two versions, the method signature will list both so we can more easily see the differences. An example of this is the `wordCount` method signature:

```
 1 <?php
 2 
 3 // Version: Laravel 8
 4 public static function wordCount(
 5     string $string
 6 );
 7 
 8 // Version: Laravel 9
 9 public static function wordCount(
10          string $string,
11     string|null $characters = null
12 );
```

### Symbols Used In This Book

We will encounter a small number of icons throughout this book. These icons call out additional information and potential pitfalls or direct you to other time-saving resources.

Hic sunt dracones

```
                                            .⌐-─ ``,,▄▄▄╥╥╥╥▄▄▓Q%╔╥,
                                     .- ` ,▄▄███▀▀▒.⌐─╜*╝╩▀▀▀▀▓▓▓▓║╣║"─
                               ⌐     =π"^`   ,-.``                  "^~
                     '   <ç ╚"╚≤[
                    ,╓═Qƒ.U  `µ                       .⌐^"`
             '   Æ ╚╦Ω "╗c-"σ â╝`  ╓~===~..,  .
            ┌ ,  ,s▄▄▄▓▄╗╜`⌠  ,«`     ─~     . `
     ñ    ræ╓═⌐'▓▓▓▀▓▓▓▌─ ' ,ƒ╨:z         ╒,  -"
    ╫└▄0╔²`╚▄╣r╘`╦╝"╚ `  '╘"╝%^¬ - "ⁿ≡     ═2.     `          `
   ╟▀╜`,!-.`²`ƒ ⌐"╜,;.╓≤7ÖD- ═∞    :o  `c` ^  ╚W`. ""
╔Ö`╛m╕╝═╖~,^ .═,, ¡    `    ;▓▓╖    .Ç~ r"╔ ,w ╚╕ `" -
 )Ü ╢CrJÇ~C═^ Γ``      ∞─`  ,▓▓▓&  A▓▓%  \╕┘  \ ╙╦ ⁿ:`` ─
 'r⌐⌐ L `"                ,g▓▓█▓▓ÅJ▀▀▓Å²╜  ┌╘       >       `
               .⌐─ ╓"║.π▒²╚╫▓▓▓╙" └  ╙▒tÑLY'`    `\            `
     ., .⌐ `                ╚▌:    \,.╓└╟╥  ┌┌` ¡ \ ╨
                             ▐╩╜"      [║,[┌   '  ▓
                                       /`^╒ ,    ,⌡        \
                            ╓Θç;═~,   v/ `= ├  ` ╬" `       `
                                   `"7 w ,╓/   φ`Ü
                         ╒          //╒,  .    ╓╒'
                       , ^^═<═.   .)'╓  ──    g⌠╛
                     .'         -²² '    ⌠   [╛
                   .`          /ε µ╒ ,  `╒  h"
                  â. ,,       ` /      ╝ ,jF
                  `      ""─^╜╜ ╒ `     ┌▐`
                ╓           ƒ╝        ¡`²╟
                '            [ ( `       ┐t
               ]  ,,,,,,,,╓═t\<`        ¡ .]
               ╚[ ─          -,  ─         `
               ]             .
```

 begin mainmatter  

## 1\. What are Strings

For a book that aims to explore PHP strings through the lens of the Laravel string helper functions, it seems obvious to start with the most basic question first: what even *are* strings? The first answer that might come to people is that strings are simply a list of characters. While, on the surface, this seems to satisfy the question, we are only three sentences into this book and have already hit our first set of problems, which leads to even more questions.

The first such question might be: what is a character? When we look at the text on a screen or in printed media, we naturally assume that each visually distinct unit of a piece of writing is a character. For example, if you grew up speaking and writing English, it is second nature to look at the following text and be able to see that it contains sixteen distinct characters quickly:

Figure 1.1 

```
1 Hello wilderness
```

But what about the following?

Figure 1.2 

```
1 你好荒野
```

Suppose you are reading a digital copy of this book. In that case, it is possible to highlight each character in that text, and you would ascertain that the previous text contains four characters. Let us make doubly sure of this and use PHP’s `strlen` function to count the characters in this string:

Figure 1.3 

```
1 <?php
2 
3 // Returns 12
4 strlen('你好荒野');
```

The `strlen` function returns twelve. That’s interesting! Is it broken? Let’s use it to count the number of characters in our English text:

Figure 1.4 

```
1 <?php
2 
3 // Returns 16
4 strlen('Hello wilderness');
```

This time the function returns sixteen, which is the correct number of characters in our text. What’s going on here? To answer this question, we should take a step back and think about how we store and represent text in computer memory.

### 1.1 A Brief History of Character Encodings

Suppose we must develop a compact way of sending messages between two groups, one that reduces the total amount of data sent but does not lose any information. Let’s say we only need to concern ourselves with words, not numbers or special characters. We could analyze previous communication between the two parties, find the frequent words and phrases, and represent them as numbers or symbols. When we want to send a new message, we will replace those words and phrases with their corresponding number or symbol. When the recipient of the message goes to read the message, they would consult the table of numbers and symbols and reverse the process to get back the original message. We would have developed an encoding scheme: a way to represent and interpret data.

When we look at the history of text data and character encodings within computer systems, it does not take long for the name ASCII, an abbreviation of the American Standard Code for Information Interchange, to come up, which has its roots in telegraph codes developed at Bell.

In the early days of computing, it was widespread for each company or organization producing a computer system to go through the same exercise of creating a unique way of storing text: to make a unique character encoding system. These systems were rarely compatible, and many parties, with the support and direction of the then American Standards Association, undertook work throughout the mid to late 1990s to produce a standard way of encoding text.

Much of this work was not widely adopted until March 11, 1968, when U.S. President Lyndon B. Johnson mandated that ASCII become a U.S. federal standard. In addition to promoting ASCII to a federal standard, the President also made it a requirement that all computers and related equipment purchased by the U.S. government starting July 1, 1969, be ASCII-compatible. Fast forward from these early days of the development of the standard (although there were many revisions to it in the following years) to 1981, when IBM used it to encode text with their first personal computer.

We will skip a lot more history and nuance, but we have enough context to proceed. Let’s now work to understand what all of this has to do with the wrong results of the strlen function when attempting to count the number of characters in our piece of Traditional Chinese text. The first fact to know is that ASCII was initially devised as a 7-bit standard and provided an encoding for 128 characters. The nice thing about this is that each character is easily represented by a single byte within a computer. Or, put another way, each character is mapped to an integer between 0 and 255, the maximum value we can represent with a single byte.

If we were to convert our English string into a byte array using:

Figure 1.5 

```
1 <?php
2 
3 $bytes = unpack('C*', 'Hello wilderness');
```

We would get the following array of integers:

Figure 1.6 

```
 1 array:16 [
 2      1 => 72
 3      2 => 101
 4      3 => 108
 5      4 => 108
 6      5 => 111
 7      6 => 32
 8      7 => 119
 9      8 => 105
10      9 => 108
11     10 => 100
12     11 => 101
13     12 => 114
14     13 => 110
15     14 => 101
16     15 => 115
17     16 => 115
18 ]
```

If we were to look up the ASCII table for those values, we would find that those numbers code for each of the characters in our original string. Let’s now look at the results of the following:

Figure 1.7 

```
1 <?php
2 
3 $bytes = unpack('C*', '你好荒野');
```

Which produces:

Figure 1.8 

```
 1 array:12 [
 2      1 => 228
 3      2 => 189
 4      3 => 160
 5      4 => 229
 6      5 => 165
 7      6 => 189
 8      7 => 232
 9      8 => 141
10      9 => 146
11     10 => 233
12     11 => 135
13     12 => 142
14 ]
```

If you notice, our Traditional Chinese string is a byte array containing twelve distinct values, which leads us to the next piece: the `strlen` function is counting the *number of bytes*.

For English characters in ASCII, counting the number of bytes is equivalent to counting the number of characters in the string: all English characters can be represented by a single byte. So how does this work with the Traditional Chinese text? Let’s start by breaking down each character and checking what the byte array it produces is:

Figure 1.9 

```
 1 // unpack('C*', '你');
 2 array:3 [
 3     1 => 228
 4     2 => 189
 5     3 => 160
 6 ]
 7 
 8 // unpack('C*', '好');
 9 array:3 [
10     1 => 229
11     2 => 165
12     3 => 189
13 ]
14 
15 // unpack('C*', '荒');
16 array:3 [
17     1 => 232
18     2 => 141
19     3 => 146
20 ]
21 
22 // unpack('C*', '野');
23 array:3 [
24     1 => 233
25     2 => 135
26     3 => 142
27 ]
```

As you can see, each of those characters is composed of *multiple* bytes, which is where the name multibyte comes from in the context of PHP’s multibyte string functions. One of the multibyte string functions is the `mb_strlen` function, which is the multibyte version of the strlen function. Using this function on our Traditional Chinese text returns the value four, which matches what we visually see:

Figure 1.10 

```
1 <?php
2 
3 // Returns 4
4 mb_strlen('你好荒野');
```

### 1.2 Unicode and UTF-8

In the previous section, we looked at the underlying bytes leading to strange results when using the `strlen` function. We also discussed a bit of the history of character encodings in general, but one thing we did not answer was: what was the character encoding used when converting our strings to byte arrays? When we looked at those byte arrays, we could see the representation of those characters. Still, without knowing the character encoding, all of those values are meaningless since we would not know how to interpret them. The short answer we could give here is, “well, it’s Unicode,” but that only gets us so far.

Unicode, like ASCII, is a character set that provides a mapping of characters to an integer (Unicode refers to these associations as code points). However, unlike ASCII, Unicode does not dictate how those values are stored or transferred (remember, in ASCII, characters are mapped to and persisted as single bytes).

Let’s take a look at our Traditional Chinese text again, but with the Unicode code points:

Table 1.1 Unicode Code Points Example

 
| Character || Code Point || Name |
| --- | --- | --- |
| 你 || U+4F60 || CJK Unified Ideograph-4F60 |
| --- | --- | --- |
| 好 || U+597D || CJK Unified Ideograph-597D |
| 荒 || U+8352 || CJK Unified Ideograph-8352 |
| 野 || U+91CE || CJK Unified Ideograph-91CE |

We can identify our four characters within the Unicode character set by referring to their code point. The code point maps a number to a character or position within the Unicode character set, and Unicode code points begin with the “U+” prefix followed by a hexadecimal number. To help build our understanding of how code points relate to the Unicode character set, we can look at a feature introduced in PHP 7: Unicode code point escape syntax.

From the PHP manual, the Unicode code point escape syntax “takes a Unicode code point in hexadecimal form, and outputs that codepoint in UTF-8”. Earlier, we discussed how the code point is the “U+” prefix followed by a hexadecimal number. Starting with PHP 7, we can embed those same characters by referring to their Unicode code point in hexadecimal form, which we can get from the “Unicode Code Points Example” table:

Figure 1.11 

```
1 <?php
2 
3 // Outputs "你好荒野"
4 echo "\u{4F60}\u{597D}\u{8352}\u{91CE}";
```

Apart from language-specific escape sequence characters, PHP’s code point escape syntax reads almost identical to the Unicode code point itself. However, one essential phrase in the PHP manual’s explanation was “and outputs that codepoint in UTF-8.” What is UTF-8, and why does it keep appearing in this discussion about Unicode, characters, and text? If Unicode describes the character set, UTF-8 is one of three *Unicode transformation formats*.

We, as developers, will most commonly encounter UTF-8 within the context of web applications, websites, or other Internet-connected applications. With UTF-8, we can encode Unicode using one, two, three, or four *eight*\-bit bytes.

To explore this, let’s have fun with the “你” character. To get started, we will take the hex component of the code point and convert it to a decimal number using PHP’s `hexdec` function:

Figure 1.12 

```
1 <?php
2 
3 // Returns 20320
4 hexdec('4F60');
```

Converting the hexadecimal component to a decimal produces the result 20320. If we were to look up the HTML code for the 你 character, we would see that it is:

Figure 1.13 

```
1 &#20320;
```

Notice how the character’s HTML and decimal versions are almost the same? Pretty interesting! We will now take it a step further and work to take our decimal number and convert it to binary, and eventually arrive at the same array of integers we saw in the previous section.

We will start this process using PHP’s `decbin` function to convert our decimal number into binary. Doing this returns the binary value `100111101100000`:

Figure 1.14 

```
1 <?php
2 
3 // Returns "100111101100000":
4 decbin(20320);
```

To get this value encoded using UTF-8, we will have to look at the rules for encoding values.

The rules we will look at are adapted from RFC 3629, which provides ranges of numbers and their sequence of an eight-bit byte, or octet “templates.”

Octet is one of those words that can be intimidating at first: it just feels complicated and advanced. In reality, it often just refers to a group of eight things. In our case, it refers to a byte of precisely eight bits: eight ones or zeroes. Most modern developers will have only ever encountered bytes eight bits in length, but this has not always been the case historically. We need not look further back than the discussion about ASCII, which stored characters in seven-bit bytes.

With UTF-8, we will encode characters in an octet *sequence*: a series of either one, two, three, or four octets. To encode a character with UTF-8, we need to know its numeric value or Unicode code point. The size of this number in bytes is what we will use to determine which UTF-8 octet sequence to use. The following table lists the numeric ranges and the octet template to use:

Table 1.2 UTF-8 Octet Sequence Ranges

 
| Decimal Range || Hex Range || Octet Sequence |
| --- | --- | --- |
| 0 - 127 || 0000 0000 - 0000 007F || 0xxxxxxx |
| --- | --- | --- |
| 128 - 2,047 || 0000 0080 - 0000 07FF || 110xxxxx 10xxxxxx |
| 2,048 - 65,535 || 0000 0800 - 0000 FFFF || 1110xxxx 10xxxxxx 10xxxxxx |
| 65,536 - 1,114,111 || 0001 0000 - 0010 FFFF || 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx |

We will use the decimal values to compare in the table, but most implementations will use the hex values. Earlier, we found that the decimal value of the code point for the “你” character was 20320. Looking at our table, we can see that we will need to use the following octet sequence template:

Figure 1.15 

```
1 1110xxxx 10xxxxxx 10xxxxxx
```

We will also need our character’s binary data now that we have our template. Luckily, the value `100111101100000` we came up with earlier is just what we need for this next step. We now need to replace the x’s in the octet template with the binary data.

We do this by starting at the template’s right-hand side and replacing the last x with the last bit in the binary data. After this, we continue to move toward the left until we run out of data. Once complete, we should end up with the following result:

Figure 1.16 

```
1 1110x100 10111101 10100000
```

As you can see, we have one x left over in the result. Anytime we have left-over placeholders, we simply replace them with 0’s to arrive at (**Figure 1.18** visually represents where we replace the bits in our sequence template):

Figure 1.17 

```
1 11100100 10111101 10100000
```

![Figure 1.18 Encoding UTF-8 Values](images/diagram_binary_replacement-1662320348.png)

Figure 1.18 Encoding UTF-8 Values

If we were to look up the UTF-8 binary value for “你,” we would find that it matches the value we produced manually. At the beginning of this chapter, we looked at how we could use the `unpack` function to retrieve a character’s constituent values. As a refresher, here are that function’s results for “你”:

Figure 1.19 

```
1 // unpack('C*', '你');
2 array:3 [
3     1 => 228
4    2 => 189
5     3 => 160
6 ]
```

To bring things full circle, we can now use PHP’s `bindec` function to convert the binary values we arrived at manually to their decimal value:

Figure 1.20 

```
 1 <?php
 2 
 3 // Returns 228
 4 bindec('11100100');
 5 
 6 // Returns 189
 7 bindec('10111101');
 8 
 9 // Returns 160
10 bindec('10100000');
```

### 1.3 Implementing Upper and Lowercase Functions

As stated earlier, one of the benefits of UTF-8 is that it preserves the ASCII values^([2](#chap29.xhtml#fn-utf8ascii)) and their relative positions. We can explore working more closely with strings by reimplementing the upper and lowercase functions. We will only focus on the ASCII character range to keep things simple.

Table 1.3 ASCII Alpha Characters

 
| ASCII Code || Symbol || ASCII Code || Symbol |
| --- | --- | --- | --- |
| 65 || A || 97 || a |
| --- | --- | --- | --- |
| 66 || B || 98 || b |
| 67 || C || 99 || c |
| 68 || D || 100 || d |
| 69 || E || 101 || e |
| 70 || F || 102 || f |
| 71 || G || 103 || g |
| 72 || H || 104 || h |
| 73 || I || 105 || i |
| … || … || … || … |
| 87 || W || 119 || w |
| 88 || X || 120 || x |
| 89 || Y || 121 || y |
| 90 || Z || 122 || z |

From the table, we can notice an interesting pattern with the ASCII characters: all of the lowercase character’s decimal values are thirty-two greater than their uppercased variant. This ASCII code distribution means that if we want to convert all uppercase characters to lowercase, we need to add thirty-two to its value.

Figure 1.21 uppercaseString Implementation 

```
 1 <?php
 2 
 3 function uppercaseString($input) {
 4     $newString = '';
 5 
 6     for ($i = 0; $i < strlen($input); $i++) {
 7       $firstByte = ord($input[$i]);
 8 
 9       if ($firstByte >= 97 && $firstByte <= 122) {
10         $newString .= chr($firstByte - 32);
11       } else {
12         $newString .= chr($firstByte);
13       }
14     }
15 
16     return $newString;
17 }
```

Figure 1.22 lowercaseString Implementation 

```
 1 <?php
 2 
 3 function lowercaseString($input) {
 4     $newString = '';
 5 
 6     for ($i = 0; $i < strlen($input); $i++) {
 7       $firstByte = ord($input[$i]);
 8 
 9       if ($firstByte >= 65 && $firstByte <= 90) {
10         $newString .= chr($firstByte + 32);
11       } else {
12         $newString .= chr($firstByte);
13       }
14     }
15 
16     return $newString;
17 }
```

Our two functions can be used like so:

Figure 1.23 

```
1 <?php
2 
3 // Returns "HELLO, WORLD!"
4 uppercaseString('hello, world!');
5 
6 // Returns "hello, there!"
7 lowercaseString('HELLO, there!');
```

We saw two new PHP functions in the previous code samples: `ord` and `chr`.

The `ord` function will return the first byte of a string value as a value between 0 and 255. For our purposes here, this will effectively tell us the character’s position within the ASCII range. The `chr` function does the opposite: it will take a value between 0 and 255 and convert it to its ASCII character.

If we wanted a little bit of fun, we could combine these functions to swap the casing of each letter in the input string. Because ASCII characters are thirty-two bytes away from their counterparts, we can use the bitwise XOR operator to swap the positions of our letters:

Figure 1.24 swapCase Implementation 

```
 1 <?php
 2 
 3 function swapCase($input) {  
 4     $newString = '';
 5 
 6     for ($i = 0; $i < strlen($input); $i++) {
 7       $firstByte = ord($input[$i]);
 8 
 9       if ($firstByte >= 65 && $firstByte <= 90 ||
10           $firstByte >= 97 && $firstByte <= 122) {
11         $newString .= chr($firstByte ^ 32);
12       } else {
13         $newString .= chr($firstByte);
14       }
15     }
16 
17     return $newString;
18 }
```

Our `swapCase` function would return the following results given the sample input:

Figure 1.25 

```
1 <?php
2 
3 // Returns "hElLo, WoRlD!"
4 swapCase('HeLlO, wOrLd!');
5 
6 // Returns "hellO, wOrld!"
7 swapCase('HELLo, WoRLD!');
```

Our simple implementations also use a loop to iterate the characters of our string. With ASCII being one-byte-per-character, this is completely fine. However, as you may have guessed, this becomes a bit more challenging once we move into multi-byte characters.

### 1.4 Iterating Multibyte Strings

In the previous section, we implemented several string functions that worked by iterating a string’s characters. Treating each byte as a single character is fine when working with ASCII, but as soon as we need to work with multibyte characters, things become a little more complicated. As an example, if we attempted to iterate “這可以” using the following:

Figure 1.26 

```
1 <?php
2 
3 $string = '這可以';
4 
5 $output = '';
6 
7 for ($i = 0; $i < strlen($string); $i++) {
8     $output .= $i . ': '. $string[$i];
9 }
```

Our output string would appear corrupted:

Figure 1.27 

```
1 0: Ú1: Ç2: Ö3: Õ4: Å5: »6: õ7: ╗8: Ñ
```

We can attempt to fix this by replacing the `strlen` call with `mb_strlen`:

Figure 1.28 

```
1 <?php
2 
3 $string = '這可以';
4 
5 $output = '';
6 
7 for ($i = 0; $i < mb_strlen($string); $i++) {
8     $output .= $i . ': '. $string[$i];
9 }
```

However, this time we would receive the following output, which also does not look correct:

Figure 1.29 

```
1 0: é1: €2: ™
```

A quick fix for this would be to use the `mb_str_split` function to break our input string into an array of characters and iterate that:

Figure 1.30 

```
1 <?php
2 
3 $output = '';
4 
5 $chars = mb_str_split($string);
6 
7 for ($i = 0; $i < count($chars); $i++) {
8     $output .= $i . ': '. $chars[$i];
9 }
```

Which produces the result:

Figure 1.31 

```
1 0: 這1: 可2: 以
```

However, as the input size grows, this method can lead to substantial memory consumption. Depending on the use case, this may be fine. Other applications, such as those that parse arbitrary user input on every request, may not be able to get away with such high memory consumption, particularly if the parsing function is being invoked many times across multiple simultaneous requests.

Before diving directly into iterating multibyte strings, we will take a quick detour and see what it would look like if we were to implement the mb\_strlen function for UTF-8 strings ourselves.

In our discussion about Unicode and UTF-8, we saw a table listing the different ranges of values and their octet sequences used to encode UTF-8 strings. We have also encountered the `ord` function while implementing various functions, which returns the first byte of a string as a value between 0 and 255. These two pieces of information will become very useful when we implement our length function.

As the first step in implementing our length function, let’s take another look at the UTF-8 octet sequence table, but this time let’s figure out what the maximum value of the first byte could be:

Table 1.4 UTF-8 Octet Sequence First Byte Maximum Values

 
| Sequence || Max (Binary) || Max (Decimal) || Byte Length |
| --- | --- | --- | --- |
| 0xxxxxxx || 01111111 || 127 || 1 |
| --- | --- | --- | --- |
| 110xxxxx 10xxxxxx || 11011111 || 223 || 2 |
| 1110xxxx 10xxxxxx 10xxxxxx || 11101111 || 239 || 3 |
| 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx || 11110111 || 247 || 4 |

We know that we can use the `strlen` function to get the total number of *bytes* in a string and the `ord` function to return a numeric value of a byte. Using this, we can iterate a string’s bytes and determine its UTF-8 sequence. For example, using the ord function on “A” would return 16, meaning it would use the first sequence, and we can expect one byte. Calling ord with “這” would yield 233, which falls within the range of the third sequence. Because of this, we can expect three bytes.

With all of this information in mind, we can implement our length function like so:

Figure 1.32 

```
 1 <?php
 2 
 3 function utf8_strlen($input) {
 4   $charCount = 0;
 5   
 6   for ($i = 0; $i < strlen($input); $i++) {
 7       $charCount += 1;
 8       $byte = ord($input[$i]);
 9 
10       if ($byte <= 127) {
11           continue;
12       } else if ($byte <= 223) {
13           $i += 1;
14       } else if ($byte <= 239) {
15           $i += 2;
16       } else {
17           $i += 3;
18       }
19     }
20 
21     return $charCount;
22 }
```

We can compare the output of our function to the results of the `mb_strlen` function:

Figure 1.33 

```
1 <?php
2 
3 // Returns 16
4 utf8_strlen('這可以abcd!!這可以abcd');
5 
6 // Returns 16
7 mb_strlen('這可以abcd!!這可以abcd');
```

Our implementation checks the byte value against our known ranges and uses that information to skip ahead in the string. You will notice that each time we skip a number of bytes in the string, we always skip one less than what we see in the table. We do this because the for loop will add one to our counter variable after each iteration.

Throughout the rest of this chapter, we will work to implement the following class that we can use to iterate UTF-8 strings:

Figure 1.34 

```
1 <?php
2 
3 $iterator = new Utf8StringIterator('這可以-this is fine!');
4 
5 foreach ($iterator as $char) {
6     echo $char."\n";
7 }
```

After our implementation is complete, the above will produce the following output:

Figure 1.35 

```
 1 這
 2 可
 3 以
 4 -
 5 t
 6 h
 7 i
 8 s
 9 
10 i
11 s
12 
13 f
14 i
15 n
16 e
17 !
```

We will use all the techniques we’ve discussed so far, with the significant difference being the implementation details of various PHP interfaces. We will start with the following empty class and work to fill in all of the methods:

Figure 1.36 

```
 1 <?php
 2 
 3 use Iterator;
 4 
 5 class Utf8StringIterator implements Iterator
 6 {
 7     protected $string = '';
 8 
 9     public function __construct(string $string)
10     {
11         $this->string = $string;
12     }
13 
14     public function current()
15     {
16     }
17 
18     public function next()
19     {
20     }
21 
22     public function key()
23     {
24     }
25 
26     public function valid()
27     {
28     }
29 
30     public function rewind()
31     {
32     }
33 
34     public function __toString()
35     {
36         return $this->string;
37     }
38 }
```

Our class accepts a string as part of its constructor and stores it internally. All of the class’s empty methods come from PHP’s `Iterator` interface, which allows us to create class implementations that we can use in foreach loops. We have also included the `__toString` magic method so that users of our class can easily convert instances of our class to strings. We will start with the more straightforward methods first.

Within our implementation, we will need to keep track of the current position within the string. Remember that we want to accommodate multibyte strings, so an index of one may correspond to the fourth byte of our string. We will store this internally as `$position`.

Figure 1.37 

```
 1 <?php
 2 
 3 use Iterator;
 4 
 5 class Utf8StringIterator implements Iterator
 6 {
 7     protected $string = '';
 8     protected $position = 0;
 9 
10     public function __construct(string $string)
11     {
12         $this->string = $string;
13     }
14 
15     public function current()
16     {
17     }
18 
19     public function next()
20     {
21     }
22 
23     public function key()
24     {
25         return $this->position;
26     }
27 
28     public function valid()
29     {
30         return isset($this->string[$this->position]);
31     }
32 
33     public function rewind()
34     {
35         $this->position = 0;
36     }
37 
38     public function __toString()
39     {
40         return $this->string;
41     }
42 }
```

PHP uses the `key` method to know the array key for the current element within the loop. For our purposes, that will be the position within the original string the character appears. We will also use the internal position to help implement the valid method.

PHP uses the `valid` method to determine if the current position within the loop is valid after each iteration (through calling next) or when the iteration is reset (through a call to rewind). We will consider a position valid if a byte exists in the original string at that location.

We will now implement the central part of the string iterator: the `current` and `next` methods.

Figure 1.38 

```
 1 <?php
 2 
 3 use Iterator;
 4 
 5 class Utf8StringIterator implements Iterator
 6 {
 7     protected $string = '';
 8     protected $position = 0;
 9     protected $lastSize = 1;
10 
11     public function __construct(string $string)
12     {
13         $this->string = $string;
14     }
15 
16     public function current()
17     {
18         $firstByte = ord($this->string[$this->position]);
19 
20         $this->lastSize = match(true) {
21             $firstByte <= 127 => 1,
22             $firstByte <= 223 => 2,
23             $firstByte <= 239 => 3,
24             default => 4
25         };
26 
27         return substr(
28             $this->string,
29             $this->position,
30             $this->lastSize
31         );
32     }
33 
34     public function next()
35     {
36         $this->position += $this->lastSize;
37     }
38 
39     public function key()
40     {
41         return $this->position;
42     }
43 
44     public function valid()
45     {
46         return isset($this->string[$this->position]);
47     }
48 
49     public function rewind()
50     {
51         $this->position = 0;
52     }
53 
54     public function __toString()
55     {
56         return $this->string;
57     }
58 }
```

The `current` method implementation looks very similar to the character counting function we did in the previous section. We are checking the size of the first byte at any given position and using it to determine the number of bytes the character is composed of at that location. We are storing the character’s size internally as `$lastSize`, which we can use in our next implementation: to return the position of the *next* character within the string.

The `return` value of the current method returns a *substring* of our original string. This substring starts at the iterator’s current position and will continue up the current character’s number of bytes. You may wonder why we are using the `substr` method instead of `mb_substr`.

We are using `substr` instead of `mb_substr` since we manage the number of bytes-per-character ourselves and do not need to rely on the capability of the built-in function, as it would lead to further issues.

At this point, we can use our class to loop through all the characters of a UTF-8 string. Our next improvement will be to make our string iterator work with PHP’s `count` function. To do this, we need to implement the `Countable` interface.

The `Countable` interface defines a single count method, which should return the size of the object we want to count. For our use case, this will be the length of the string. We do not need to do anything super complicated for this implementation and can use the `mb_strlen` function with the UTF-8 encoding parameter to pre-calculate our length and return that:

Figure 1.39 

```
 1 <?php
 2 
 3 use Countable;
 4 use Iterator;
 5 
 6 class Utf8StringIterator implements
 7     Countable,
 8     Iterator
 9 {
10     protected $string = '';
11     protected $position = 0;
12     protected $lastSize = 1;
13     protected $length = 0;
14 
15     public function __construct(string $string)
16     {
17         $this->string = $string;
18         $this->length = mb_strlen($string, 'UTF-8');
19     }
20 
21     public function count()
22     {
23         $this->length;
24     }
25 
26     // ...
27 }
```

With this change, we can do the following to get the number of characters in our string:

Figure 1.40 

```
1 <?php
2 
3 $iterator = new Utf8StringIterator('這可以-this is fine!');
4 
5 // Returns 17
6 $length = count($iterator);
```

### 1.5 Accessing Individual Characters in a UTF-8 String

We now have a fully functional class that can iterate UTF-8 strings and return the correct number of characters when using PHP’s count function. Currently, if we attempt to do the following, we will receive errors:

Figure 1.41 

```
1 <?php
2 
3 $iterator = new Utf8StringIterator('這可以-this is fine!');
4 
5 $iterator[0];
6 $iterator[1];
7 $iterator[2] = 'A';
```

It would be nice to be able to access, set, or remove characters at arbitrary positions using PHP’s array access syntax. We can accomplish this by implementing another PHP interface: the `ArrayAccess` interface.

To implement this interface, we can make the following additions. A lot is going on with these additions, but we will cover all of the crucial parts throughout the remainder of this section:

Figure 1.42 

```
  1 <?php
  2 
  3 namespace App;
  4 
  5 use ArrayAccess;
  6 use Countable;
  7 use Iterator;
  8 
  9 class Utf8StringIterator implements
 10     ArrayAccess,
 11     Countable,
 12     Iterator
 13 {
 14     protected $string = '';
 15     protected $position = 0;
 16     protected $lastSize = 1;
 17     protected $length = 0;
 18     protected $stringIndex = null;
 19 
 20     public function __construct(string $string)
 21     {
 22         $this->string = $string;
 23         $this->length = mb_strlen($string, 'UTF-8');
 24     }
 25 
 26     // ...
 27 
 28     public function lastCharSize()
 29     {
 30         return $this->lastSize;
 31     }
 32 
 33     private function buildStringIndex()
 34     {
 35         if ($this->stringIndex !== null) {
 36             return;
 37         }
 38 
 39         $this->stringIndex = [];
 40         $string = new Utf8StringIterator($this->string);
 41 
 42         $charIndex = 0;
 43 
 44         foreach ($string as $char) {
 45             $this->stringIndex[$charIndex] = $string->lastCharSize();
 46             $charIndex += 1;
 47         }
 48 
 49         unset($string);
 50     }
 51 
 52     public function offsetExists(mixed $offset)
 53     {
 54         $this->buildStringIndex();
 55 
 56         return array_key_exists(
 57             $offset,
 58             $this->stringIndex
 59         );
 60     }
 61 
 62     public function offsetGet(mixed $offset)
 63     {
 64         $this->buildStringIndex();
 65 
 66         return substr(
 67             $this->string,
 68             $this->getPosition($offset),
 69             $this->stringIndex[$offset]
 70         );
 71     }
 72 
 73     protected function getPosition($offset)
 74     {
 75         $position = 0;
 76 
 77         for ($i = 0; $i < $offset; $i++) {
 78             $position += $this->stringIndex[$i];
 79         }
 80 
 81         return $position;
 82     }
 83 
 84 	public function getPositionFromCharIndex($charIndex)
 85     {
 86         $this->buildStringIndex();
 87 
 88         return $this->getPosition($charIndex);
 89     }
 90 
 91     public function offsetSet(mixed $offset, mixed $value)
 92     {
 93         $this->buildStringIndex();
 94 
 95         $this->string = substr_replace(
 96             $this->string,
 97             $value,
 98             $this->getPosition($offset),
 99             $this->stringIndex[$offset]
100         );
101         $this->stringIndex = null;
102 
103         $this->buildStringIndex();
104         $this->updateStringMetaData();
105     }
106 
107     public function offsetUnset(mixed $offset)
108     {
109         $this->buildStringIndex();
110 
111         $this->string = substr_replace(
112             $this->string,
113             '',
114             $this->getPosition($offset),
115             $this->stringIndex[$offset]
116         );
117         unset($this->stringIndex[$offset]);
118 
119         $this->updateStringMetaData();
120     }
121 
122     protected function updateStringMetaData()
123     {
124         $this->stringIndex = array_values($this->stringIndex);
125         $this->length = mb_strlen($this->string);
126     }
127 }
```

The first exciting part of this implementation is the string index concept. The string index will store an internal map of each character and how many bytes it needs. We construct this map by iterating all of the characters of the string, using a new instance of our iterator. You will notice that we also created a new helper method: `lastCharSize`. The `lastCharSize` method will return the total number of bytes for the last character the iterator returned, which we can then use to populate our index. Another new method used quite often with this implementation is the `getPosition` method.

The `getPosition` will take a zero-indexed character position and return the location it appears at in the original string. We do this by counting the number of bytes before the desired offset within the index. We also added a public `getPositionFromCharIndex` method that does the same thing, but will check the state of the string index first.

When we write code like the following, PHP internally makes a call to the `offsetGet` method with the desired offset:

Figure 1.43 

```
1 <?php
2 
3 $iterator = new Utf8StringIterator('這可以-this is fine!');
4 
5 $firstChar  = $iterator[0];
6 $secondChar = $iterator[1];
7 $thirdChar  = $iterator[2];
```

The first thing we do in any of our `ArrayAccess` methods is to make a call to our `buildStringIndex` method, which will create our index if it does not already exist. To return a single character based on its index, we call `substr` against our internal string with the location of the provided offset and the length of the character at that location.

Similarly, when we do the following, PHP will make a call to our `offsetSet` method:

Figure 1.44 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator('這可以-this is fine!');
 4 
 5 $iterator[0] = 'A';
 6 $iterator[1] = 'B';
 7 $iterator[2] = 'C';
 8 
 9 // Returns "ABC-this is fine!"
10 $value = (string) $iterator;
```

When we change characters within our string, we call the `substr_replace` method to replace all of the original characters at that location. Afterward, we must reset our string index and rebuild some metadata.

When we rebuild our string’s metadata, we call the `array_values` function on our internal string index, which we start the numbering over at zero and update our internally stored length. Our implementation of the `offsetUnset` method is almost the same, but instead of accepting a value from the user, we replace the original characters with an empty string.

One side effect of our `offsetSet` implementation is that we can now do the following to replace substrings at specific locations:

Figure 1.45 

```
1 <?php
2 
3 $iterator = new Utf8StringIterator('這可以-this is fine!');
4 
5 $iterator[1] = '-hello world-';
6 
7 // Returns "這-hello world-以-this is fine!"
8 $value = (string) $iterator;
```

### 1.6 Managing Character Encodings

楮⁃桡灴敲‱Ⱐ睥⁨慤ⁱ畩瑥⁡⁬敮杴桹⁤楳捵獳楯渠慢潵琠䅓䍉䤠慮搠啔䘭㠮⁔桥獥⁡牥硡浰汥猠潦⁣桡牡捴敲湣潤楮杳Ⱐ扵琠瑨敲攠慲攠浡湹⁭潲攮⁗桡琠桡灰敮敤⁡琠瑨攠扥杩湮楮朠潦⁴桩猠灡牡杲慰栠楳⁡渠數慭灬攠潦⁭潪楢慫攠ⴠ瑨攠牥獵氍ਠ潦⁰牯捥獳楮 - what went wrong there? What should have appeared there was that so far in Chapter 1, we have had quite a lengthy discussion about ASCII and UTF-8. These are examples of character encodings, but there are many more. What happened at the beginning of this paragraph is an example of mojibake - the result of processing text in a different character encoding than the one used to write it. The specific example here was UTF-8 encoded content interpreted as a sequence of bytes encoded using UTF-16 BE. While this particular example was purposely done and is benign, having this happen on accident can have consequences for application data flow, user experience, and breaking layouts, amongst other things. In extreme cases, this process may unintentionally change the meaning of a message entirely when read by the right reader, such as taking an ordinary conversation about character encodings and producing a disjointed equine conversation.

While we know it is essential to be mindful of different character encodings, one of a PHP application’s most often overlooked aspects is failing to configure the default charset used. We can modify PHP’s default character encoding by changing the `default_charset` value within the php.ini file. Unless you have specific reasons to change the default setting, I would recommend ensuring it is set to “UTF-8”:

Figure 1.46 

```
1 ; ...
2 
3 ; PHP's default character set is set to UTF-8.
4 ; http://php.net/default-charset
5 default_charset = "UTF-8"
6 
7 ; ...
```

Now that we have addressed the character encoding that PHP will use by default if your application interacts with a database, we should ensure that it uses a character encoding that *matches* your applications. Suppose you have encountered an issue where data retrieved from your database and processed by your application looks mangled or broken but works fine in isolation within either system. In that case, both are likely configured to use a different character set or encoding.

Laravel’s default database configuration will have most likely configured your database connections to use UTF-8. Still, you can double-check this by looking for the following configuration options within your `config/database.php` file:

Table 1.5 Database Character Sets

 
| Database System || Configuration Option || UTF-8 Value |
| --- | --- | --- |
| MySQL || charset || utf8mb4 |
| --- | --- | --- |
| MySQL || collation || utf8mb4\_unicode\_ci |
| PostgreSQL || charset || utf8 |
| SQL Server || charset || utf8 |

**Table 1.6** provides a list of resources for looking up the supported character sets and encodings for PHP, MySQL, PostgreSQL, and SQL Server:

Table 1.6 Software Character Encodings Reference

 
| Software || Encoding Reference Link |
| --- | --- |
| PHP || https://www.php.net/manual/en/mbstring.encodings.php |
| --- | --- |
| PostgreSQL || https://www.postgresql.org/docs/9.3/multibyte.html |
| MySQL || https://dev.mysql.com/doc/refman/8.0/en/charset-charsets.html |
| SQL Server 16 || https://docs.microsoft.com/en-us/sql/relational-databases/collations/collation-and-unicode-support?view=sql-server-ver16 |

Working with consistent character sets and encodings when interacting with internal systems is a great start, but most applications will occasionally interact with third-party data. Whether from external APIs, user-supplied file uploads, or related, we need to be aware of different encodings sneaking their way into our applications. Luckily, we have various ways to analyze, detect, and convert the character encodings of external data.

We can use PHP’s `mb_detect_encoding` function to try and determine the character encoding of the provided data. This function will attempt to detect the character encoding of the value but may return `false` if it fails. We can use this function like so to attempt to convert our input data into an encoding our application supports:

Figure 1.47 

```
1 <?php
2 
3 $encoding = mb_detect_encoding(
4     $value,
5     ['UTF-8', 'ASCII', 'ISO-8859-1'],
6     true
7 );
```

You may notice that we are supplying a list of different character encodings as the second argument and the boolean value `true` as the third argument.

The second argument, which contains a list of character encodings, specifies the list of encodings that the `mb_detect_encoding` function will attempt to detect in order. This can be useful when an input value contains characters that fall entirely within the ASCII range. Without specifying any order, the `mb_detect_encoding` function may return “ASCII,” which is technically correct, but with UTF-8, the lower range corresponds to the ASCII range, so it may be beneficial to have it report as UTF-8. By specifying our character encodings in this order, we can help to eliminate that difference. The character encoding order may be specified by configuring the `mbstring.detect_order` PHP configuration value. Whichever method you choose to use to control the encoding order, you should list the encodings in the most specific order relevant to your application and list those that your system can manage.

The third parameter corresponds to the `$strict` parameter for the `mb_detect_encoding` function. This value is set to `false`, by default, which will cause the `mb_detect_encoding` to return the encoding that most closely matches the input value even if it does not strictly adhere to the encoding standard, which may lead to unexpected results. A typical example is when accepting input encoded in UTF-8 or ISO-8859-1, where some strings encoded in ISO-8859-1 can be detected as UTF-8 and lead to hard-to-diagnose issues, a Heisenbug of sorts.

We can avoid many potential issues by specifying our desired detection order and using `mb_detect_encoding` in strict mode. Putting all of this together, we can create a simple helper function that will attempt to normalize the data our application receives:

Figure 1.48 

```
 1 <?php
 2 
 3 use InvalidArgumentException;
 4 
 5 function convertToUtf8($value) {
 6     if ($value === null) { return $value; }
 7 
 8     $encoding = mb_detect_encoding(
 9         $value,
10         ['UTF-8', 'ASCII', 'ISO-8859-1'],
11         true
12     );
13 
14     if ($encoding === false) {
15         // Handle encoding issues in
16         // whatever way makes sense
17         // for your application.
18         throw new InvalidArgumentException(
19             'Input could not be converted to UTF-8'
20         );
21     }
22 
23     if ($encoding === 'UTF-8') {
24         return $value;
25     }
26 
27     $result = mb_convert_encoding(
28         $value,
29         'UTF-8',
30         $encoding
31     );
32 
33     if ($result === false) {
34         // Handle encoding issues in
35         // whatever way makes sense
36         // for your application.
37         throw new InvalidArgumentException(
38             'Input could not be converted to UTF-8'
39         );
40     }
41 
42     return $result;
43 }
```

Our current function implementation works well for string input across the encodings we are interested in but will fail when presented with data that contains a byte order mark (BOM) character. A BOM character at the beginning of a piece of text tells us quite a bit about the text we are about to analyze. For instance, it can tell us the following things:

1.  It indicates to us that the text is highly likely to be Unicode
2.  The specific Unicode encoding used, and
3.  The byte order, or endianness, of the text when using 16-bit and 32-bit character encodings

If you have ever worked with the `json_encode` function and noticed a weird triangle symbol with a question mark inside it when displaying the results, the input to the function likely contained a BOM character. The presence of these characters is also particularly problematic when passing a UTF-8 string into a process that handles ASCII text since BOM sequences are composed of non-ASCII bytes.

If you recall, the `mb_detect_encoding` function does not handle character encodings such as UTF-16 BE/LE well. We can detect those character encodings by looking for their BOM character sequence. **Table 1.7** displays the hex sequence of bytes and their corresponding Unicode encoding^([3](#chap29.xhtml#fn-bomsource)):

Table 1.7 Unicode BOM Sequences

 
| Encoding || Sequence |
| --- | --- |
| UTF-8 || EF BB BF |
| --- | --- |
| UTF-32 BE || 00 00 FE |
| UTF-32 LE || FF FE 00 |
| UTF-16 BE || FE FF |
| UTF-16 LE || FF FE |

Using this, we can construct a function to determine a string’s encoding based on those bytes’ presence at the beginning of the data:

Figure 1.49 Detect Various UTF-8 Encodings 

```
 1 <?php
 2 
 3 function detectEncodingFromBom($value) {
 4     if (str_starts_with($value, "\xEF\xBB\xBF")) {
 5         return ['UTF-8', substr($value, 3)];
 6     } else if (str_starts_with($value, "\x00\x00\xFE")) {
 7         return ['UTF-32BE', substr($value, 3)];
 8     } else if (str_starts_with($value, "\xFF\xFE\x00")) {
 9         return ['UTF-32LE', substr($value, 3)];
10     } else if (str_starts_with($value, "\xFE\xFF")) {
11         return ['UTF-16BE', substr($value, 2)];
12     } else if (str_starts_with($value, "\xFF\xFE")) {
13         return ['UTF-16LE', substr($value, 2)];
14     }
15 
16     return null;
17 }
```

An interesting choice with this function’s implementation is that it will return `null` if it cannot detect a Unicode BOM character sequence. If it can detect a BOM sequence, it will return an array containing the character encoding and a copy of the input value with the BOM sequence removed. We can now refactor our `convertToUtf8` function to make use of this new function:

Figure 1.50 Convert Strings to UTF-8 

```
 1 <?php
 2 
 3 function convertToUtf8($value) {
 4     if ($value === null) { return $value; }
 5 
 6     $unicodeEncoding = detectEncodingFromBom($value);
 7 
 8     $encoding = false;
 9 
10     if ($unicodeEncoding != null) {
11         // Return our UTF-8 string without the BOM.
12         if ($unicodeEncoding[0] == 'UTF-8') {
13             return $unicodeEncoding[1];
14         }
15 
16         $encoding = $unicodeEncoding[0];
17         $value = $unicodeEncoding[1];
18     } else {
19         $encoding = mb_detect_encoding(
20             $value,
21             ['UTF-8', 'ASCII', 'ISO-8859-1'],
22             true
23         );
24     }
25 
26     if ($encoding === false) {
27         // Handle encoding issues in
28         // whatever way makes sense
29         // for your application.
30         throw new InvalidArgumentException(
31             'Input could not be converted to UTF-8'
32         );
33     }
34 
35     if ($encoding === 'UTF-8') {
36         return $value;
37     }
38 
39     $result = mb_convert_encoding(
40         $value,
41         'UTF-8',
42         $encoding
43     );
44 
45     if ($result === false) {
46         // Handle encoding issues in
47         // whatever way makes sense
48         // for your application.
49         throw new InvalidArgumentException(
50             'Input could not be converted to UTF-8'
51         );
52     }
53 
54     return $result;
55 }
```

After these changes, our `convertToUtf8` function is now capable of converting a large variety of Unicode strings to UTF-8, as well as being capable of being extended to detect a variety of other character encodings.

### 1.7 Types of PHP Strings

We have covered a lot of ground so far but have not taken much time to look at how we can create strings in PHP. PHP provides four different ways to define strings:

*   Single quoted strings
*   Double quoted strings
*   Nowdoc strings
*   Heredoc strings

One of the most common string syntaxes we find is the single quote syntax. Using this syntax, we wrap the contents of our string with single quotes:

Figure 1.51 

```
1 <?php
2 
3 // Outputs A single quote string.
4 echo 'A single quote string.';
```

The benefit of the single quote syntax is that all escape escapes sequences (beyond escaping a single quote or backslash) will be output as literal string content:

Figure 1.52 

```
1 <?php
2 
3 // Outputs \tA single quote string ' \ " \n
4 echo '\tA single quote string \' \\ " \n';
```

The double quote syntax is similar but provides many escape sequences we can use to output special characters and allows the embedding of variables within our string. We’ve already seen one such escape sequence: the Unicode code point escape sequence. The following table lists the different PHP string escape sequences:

Table 1.8 String Escape Sequences

 
| Sequence || Description || Example String |
| --- | --- | --- |
| \\n || Line feed ||   |
| --- | --- | --- |
| \\r || Carriage return ||   |
| \\t || Horizontal tab ||   |
| \\v || Vertical tab ||   |
| \\e || Escape ||   |
| \\f || Form feed ||   |
| \\\\ || Backslash || ”\\\\mnt\\\\c” |
| $ || Dollar sign || ”\\$app” |
| " || Double quote || ”\\“Whoever is happy…\\”” |
| \[0-7\]{1,3} || Octal sequence || “\\064\\062” |
| \\x\[0-9A-Fa-f\]{1,2} || Hexadecimal sequence || “\\x2E\\x35\\x37\\x37\\x32\\x31” |
| \\u{\[0-9A-Fa-f\]+} || Unicode code point (UTF-8 output) || “Hi, Jesse! \\u{1f440}” |

When working with double-quoted strings, we can embed variables within them, access array elements, and call methods on objects. The following examples demonstrate these techniques for building up strings from dynamic input:

Figure 1.53 

```
 1 <?php
 2 
 3 // Simple variable expansion.
 4 $name = 'Jean';
 5 
 6 // Outputs "Hello, Jean!"
 7 echo "Hello, {$name}!";
 8 
 9 // Accessing array elements.
10 $colors = [
11     'White',
12     'Grey',
13     'Blue'
14 ];
15 
16 // Outputs "The color is: Grey"
17 echo "The color is: {$colors[1]}";
18 
19 // Calling methods on objects.
20 $name = str('clippy');
21 
22 // Outputs "Product of the year: Clippy"
23 echo "Product of the year: {$name->title()}";
```

The more obscure string syntaxes are the nowdoc and heredoc syntaxes. These syntaxes help construct large, multiline strings, and we specify them similarly. The first type we will look at is the heredoc syntax.

When we define a string using either syntax, we always start by using the `<<<` PHP operator, followed by some identifier. Identifiers follow the same rules as PHP variable names, so they must begin with a letter or underscore. To finish our string, we repeat the identifier on another line, with the contents of our string appearing between the start and closing identifier of our heredoc string:

Figure 1.54 

```
 1 <?php
 2 
 3 $name = 'Alice';
 4 
 5 echo <<<STRING
 6   Hello, $name,
 7 
 8   "We do not need to escape quotes"
 9 
10   Line one
11   Line two
12 
13   End
14 STRING;
```

Which produces:

Figure 1.55 

```
1   Hello, Alice,
2 
3   "We do not need to escape quotes"
4 
5   Line one
6   Line two
7 
8   End
```

You will have noticed that when this syntax is, we do not need to escape our double quotes, and the whitespace at the beginning of our strings was preserved in the output. We can move the indentation of the closing identifier to influence the whitespace that is removed from the output string.

Figure 1.56 

```
 1 <?php
 2 
 3 $name = 'Alice';
 4 
 5 echo <<<STRING
 6   Hello, $name,
 7 
 8   "We do not need to escape quotes"
 9 
10   Line one
11   Line two
12 
13   End
14   STRING;
```

Moving the closing `STRING` identifier will now the following output:

Figure 1.57 

```
1 Hello, Alice,
2 
3 "We do not need to escape quotes"
4 
5 Line one
6 Line two
7 
8 End
```

It is important to note that indenting the final closing identifier further than any content of the string will produce a PHP parsing error:

Figure 1.58 

```
 1 <?php
 2 
 3 $name = 'Alice';
 4 
 5 echo <<<STRING
 6   Hello, $name,
 7 
 8   "We do not need to escape quotes"
 9 
10   Line one
11   Line two
12 
13   End
14     STRING;
```

Produces the following parse error:

Figure 1.59 

```
1 PHP Parse error: Invalid body indentation level (expecting an indentati\
2 on level of at least 4) on line 6
```

Nowdoc strings follow the same basic rules as heredoc strings, but when we specify the identifier of a nowdoc string, we surround it in single quotes. Additionally, variables are not interpreted inside nowdoc strings:

Figure 1.60 

```
 1 <?php
 2 
 3 
 4 $name = 'Alice';
 5 
 6 echo <<<'STRING'
 7   Hello, $name,
 8 
 9   "We do not need to escape quotes"
10 
11   Line one
12   Line two
13 
14   End
15 STRING;
```

Which produces the following output:

Figure 1.61 

```
1   Hello, $name,
2 
3   "We do not need to escape quotes"
4 
5   Line one
6   Line two
7 
8   End
```

### 1.8 Backticks and Template Strings

PHP developers commonly move back and forth between front-end languages, such as JavaScript, and our backend languages. When working in languages like JavaScript, it is common to construct template strings using the backtick (“\`”) character:

Figure 1.62 

```
1 `Hello, ${name}.`
```

It is imperative to note that to accomplish the same thing in PHP, we should use the heredoc syntax or double-quoted strings:

Figure 1.63 

```
1 <?php
2 
3 $string = <<<STRING
4 Hello, {$name}.
5 STRING;
6 
7 $string = "Hello, {$name}.";
```

The backtick character in PHP is a language-level operator that will execute the contents of the string as a shell command. Because of this, the following are identical:

Figure 1.64 

```
1 <?php
2 
3 `Hello, {$name}.`;
4 
5 shell_exec("Hello, {$name}.");
```

Never use backtick strings when attempting to construct template strings, as the results could be disastrous.

### 1.9 The Laravel String Helpers

What an adventure we’ve been on throughout this chapter! Throughout the rest of this book, we will be looking at the Laravel string helper methods and working through practical examples using them. From time to time, we will refer back to the concepts and techniques discussed in this chapter. Still, it is a relief knowing that the intricate details of managing multibyte strings are abstracted away for us when using the Laravel string helper methods.

The Laravel framework provides an extensive collection of string helper methods to assist application development. Recent versions of PHP provide much more overlap in the built-in string functions and those provided by the Laravel framework. The Laravel-provided helper methods are still beneficial, however, in that they help to normalize the order of parameters and go out of their way to be multi-byte safe when it is safe.

Throughout the following few chapters, we will look at the most interesting of these helper methods, which we can split into several broad categories:

*   **Formatting**: These helper methods help to transform input strings by adjusting their casing, composition, etc.
*   **Logical**: These helper methods provide some utility or functionality that makes their use in conditional or logical statements beneficial
*   **Construction**: These helper methods provide features that help you to construct new strings from other strings
*   **Extraction**: These helper methods help to retrieve portions of existing strings for further manipulation

While we can group most helper methods into one of those four categories, others do not fit nicely into any specific category or are best discussed in their dedicated section or chapter.

## 2\. Fluent Strings

Throughout this book, we will see references to Stringable objects or fluent strings. Fluent strings are an object-oriented wrapper around the Laravel string helper methods, which provides a convenient and natural API for working with those methods, with a few additional features.

When we see the phrase fluent, especially within the context of Laravel and the packages within its ecosystem, it often refers to an object that allows you to continuously chain method calls on the same object instance or a new instance of the same type. Everyday use cases for this are query builders, request builders, etc.

To compare and contrast the fluent string API versus the standard, method-call-based approach, we can look at the following **Figure 2.1**:

Figure 2.1 Class Based vs. Fluent String Helpers 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $string = 'This is an input string.';
 6 
 7 // Using the string helpers directly.
 8 $value = Str::lower($string);
 9 $value = Str::limit($value, 10);
10 
11 // Using fluent strings.
12 $value = (string) str($string)->lower()->limit(10);
```

We can see from **Figure 2.1** that with fluent strings, we do not need to refer to the `Str` class continuously and can continue to call methods based on the results of the previous method call. In this example, we also see the `str` function (all lowercase), which we can use to create a new instance of the fluent string object anywhere.

We can also use the `of` method on the `Str` class to create these fluent string objects:

Figure 2.2 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $string = 'This is an input string.';
6 
7 $value = (string) Str::of($string)->lower()->limit(10);
```

One notable aspect of fluent strings is their ability to proxy dynamic property access onto method calls. That is quite the sentence, but what it means is that we can call methods on our fluent strings without having to specify the parenthesis that is typical of method calls:

Figure 2.3 

```
1 <?php
2 
3 // Returns "this_is_an_input_string"
4 (string) str('This is an input string.')
5     ->lower->snake;
```

We should note, however, that if we need to supply arguments to our method calls, we will still need to use the complete method syntax. If methods exist that define parameters, the default values of those parameters are used when we use the property proxying method.

Developers from other languages, such as C# or Java, may notice that Laravel’s fluent string objects share many similarities with the concept of a “string builder.” While the API for interacting with the objects may be similar, it is essential to note that internally these systems behave very differently, mainly due to how PHP internally manages and processes strings.

When targeting other runtimes, such as the Common Language Runtime (CLR) or Java Virtual Machine (JVM), there are genuine performance benefits to using the platform’s string builders. PHP’s internal string management is highly optimized, and there is no tangible benefit in trying to introduce similar concepts for the vast majority of use cases.

### 2.1 Converting Fluent String Objects to Strings

There are several ways to convert a fluent string instance to an actual string, and the first approach is not worrying about it and allowing PHP to coerce our object into a string by itself. As an example, the following will take pass a fluent string instance to the `mb_strlen` function:

Figure 2.4 

```
1 <?php
2 
3 // Returns 24
4 mb_strlen(str('This is an input string.'));
```

Fluent strings implement PHP’s `__toString` magic method, which allows objects to tell PHP how it should convert them to strings. PHP also uses this method when we explicitly cast our fluent string instances to a string:

Figure 2.5 

```
1 <?php
2 
3 $value = (string)str('This is an input string.');
```

We can also call the `toString` and `value` methods on our fluent string instances to retrieve the string value:

Figure 2.6 

```
1 <?php
2 
3 $value = str('This is an input string.')->toString();
4 
5 $value = str('This is an input string.')->value;
```

### 2.2 Conditional String Logic

Fluent strings provide many different methods for applying conditional logic inline. These methods can help reduce the total amount of code we write, but care should be taken not to do it, and make things much more difficult to understand for the developers who come after us. To start this discussion, imagine we have a function that accepts a universally unique identifier (UUID) argument. If the argument is not a valid UUID, the function would then generate a new one. If the provided UUID is valid, we will use the supplied one instead:

Figure 2.7 

```
1 <?php
2 
3 function makeBlogPost($id = null) {
4     if (str($id)->isUuid() == false) {
5         $id = Str::uuid();
6     }
7 
8     // Other code that relies on $id.
9 }
```

We can pass in any of the following values, and our function will internally generate a new UUID:

Figure 2.8 

```
1 <?php
2 
3 makeBlogPost();
4 makeBlogPost('a');
5 makeBlogPost('abc');
```

However, if we pass in a valid UUID, it will not generate a new identifier:

Figure 2.9 

```
1 <?php
2 
3 makeBlogPost('174c479a-ee02-40e5-9bf3-eecb8445144b');
```

We can rewrite our implementation using the `whenIsUuid` conditional method:

Figure 2.10 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 function makeBlogPost($id = null) {
6     $id = str($id)->whenIsUuid(fn() => $id, fn() => Str::uuid());
7 
8     // Other code that relies on $id.
9 }
```

Our new implementation makes use of the `whenIsUuid` method and supplies two callback functions as its arguments. The `whenIsUuid` method will execute the first callback function, and its return value will be used if the input string matches the format expected of a UUID. If the input string is not a valid UUID, the second callback function is invoked, and the return value is used; in our case, we generate a new UUID.

We were able to condense our conditional statement to one line, but as the size and complexity of the conditions grow, it could easily hurt the readability of our code.

**Table 2.1** lists the available conditional fluent methods:

Table 2.1 Conditional Fluent Methods

 
| Method || Description |
| --- | --- |
| whenContains($needles, $callback, $default = null) || Tests if the string contains any of the provided substrings |
| --- | --- |
| whenContainsAll(array $needles, $callback, $default = null) || Tests if the string contains all of the provided substrings. |
| whenEmpty($callback, $default = null) || Tests if the string is empty (strict comparison). |
| whenNotEmpty($callback, $default = null) || Tests if the string is not empty (strict comparison). |
| whenEndsWith($needles, $callback, $default = null) || Tests if the string ends with another substring. |
| whenExactly($value, $callback, $default = null) || Tests if the string is exactly equal (strict comparison) to another string. |
| whenIs($pattern, $callback, $default = null) || Tests if the string is matched by the provided regular expression. |
| whenIsAscii($callback, $default = null) || Tests if the string contains only ASCII characters. |
| whenIsUuid($callback, $default = null) || Tests if the string is a valid UUID. |
| whenStartsWith($needles, $callback, $default = null) || Tests if the string begins with another substring. |
| whenTest($pattern, $callback, $default = null) || Tests if the string is matched by the provided regular expression, and executes a callback. |
| when($value, callable $callback = null, callable $default = null) || Performs a user-defined test against the string. |
| unless($value, callable $callback = null, callable $default = null) || Performs a user-defined test against the string, and executes a callback if the test fails. |

## 3\. The Formatting Helper Methods

The formatting helper methods provide utilities to allow us to transform one string into another quickly. Everyday use cases for these helper methods are generating URLs from titles and modifying the case of strings, amongst others.

**Table 3.1** provides example input and output for each of the formatting helper methods we will cover throughout the remainder of this chapter:

Table 3.1 Formatting Helpers

 
| Method || Input || Output |
| --- | --- | --- |
| camel || Battle not with monsters || battleNotWithMonsters |
| --- | --- | --- |
| headline || Battle not with monsters || Battle Not With Monsters |
| kebab || Battle not with monsters || battle-not-with-monsters |
| lcfirst || UPPER || uPPER |
| lower || UPPER || upper |
| reverse || eternally || yllanrete |
| slug || Battle not with monsters || battle-not-with-monsters |
| snake || Battle not with monsters || battle\_not\_with\_monsters |
| squish || “Balance between “ ||   |
| studly || Battle not with monsters || BattleNotWithMonsters |
| title || Battle not with monsters || Battle Not With Monsters |
| ucfirst || lower || Lower |
| upper || lower || LOWER |
| wordCount || Battle not with monsters || 4 |

### 3.1 Formatting Strings with camelCasing

Figure 3.1 camel Method Signature 

```
 1 <?php 
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function camel(
 9     string $value
10 );
```

Camel casing is similar to `studly` casing such that each word starts with a capitalized letter, with the difference being the first character is lowercased. Like the `studly` method, the `camel` method will not affect the casing of the rest of the word.

The following examples demonstrate the various usage of the `camel` helper method:

Figure 3.2 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "myWords"
 6 Str::camel('my words');
 7 Str::camel('my-words');
 8 Str::camel('my_words');
 9 Str::camel(' my-words_');
10 
11 // Returns "mYWORDS"
12 (string) str('MY WORDS')->camel();
13 
14 // Returns "myWords"
15 (string) str('my words')->camel();
```

### 3.2 Formatting Headlines

Figure 3.3 headline Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function headline(
 9     string $value
10 );
```

The `headline` helper method will apply title casing to each word of the input string (the “value”). Consecutive spaces will collapse when producing the final output.

The following characters are considered word boundaries and will be converted to spaces when formatting the input: `-`, `_`, and ` ` (space). The `headline` helper method preserves newline characters when formatting.

The following example uses collections and the `map` method to apply headline formatting to all input strings. All input strings will return the value “Working With Dynamic Variables”:

Figure 3.4 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $input = [
 6     'Working With Dynamic Variables',
 7     'working with dynamic variables',
 8     'Working with dynamic variables',
 9     'working with Dynamic Variables',
10     'WORKING WITH    DYNAMIC VARIABLES',
11 ];
12 
13 collect($input)->map(function ($value) {
14     return Str::headline($value);
15 })->all();
```

The `headline` helper method preserves non-word boundary punctuation when formatting the input string:

Figure 3.5 

```
1 <?php
2 
3 // Returns: "Working With Dynamic Variables!"
4 (string) str('working-with_dynamic variables!')
5     ->headline();
```

### 3.3 Formatting Strings with “kebab-casing”

Figure 3.6 kebab Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function kebab(
 9     string $value
10 );
```

The `kebab` helper method replaces all uppercase letters within the string with the lower-cased variant prefixed with the `-` character. The method will not prefix the first character if it is already capitalized; instead, it will be replaced by its lower-cased version. The `kebab` method trims all extraneous whitespace from the string.

Figure 3.7 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "my-words"
 6 Str::kebab('myWords');
 7 
 8 // Returns "m-y-w-o-r-d-s"
 9 Str::kebab('MYWORDS');
10 
11 
12 // Returns "this_is_-pretty-cool"
13 (string) str('this_is_PrettyCool')
14     ->kebab();
```

The `kebab` helper method produces the same output as the `snake` helper method when using the `-` character as the delimiter. Both of the following examples would return the result `hello-world`:

Figure 3.8 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::kebab('helloWord');
6 Str::snake('helloWorld', '-');
```

### 3.4 Lowercasing the First Character of a String

Figure 3.9 lcfirst Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 9
 5  *
 6  * @return string
 7  */
 8 public static function lcfirst(
 9     string $string
10 );
```

The `lcfirst` helper method is the logical opposite of the `ucfirst` helper method. The `lcfirst` helper method will return a copy of the string its first character lowercased. This method is multi-byte safe and uses the UTF-8 character encoding internally.

All of the following examples would return the value “behind the scenes”:

Figure 3.10 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::lcfirst('Behind the scenes');
6 Str::lcfirst('behind the scenes');
7 
8 (string) str('Behind the scenes')
9     ->lcfirst();
```

### 3.5 Creating Lowercase Variants of Strings

Figure 3.11 lower Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function lower(
 9     string $value
10 );
```

The `lower` helper method takes a given value and returns a lower cased variant. The `lower` method will use the UTF-8 character encoding when converting the value to its lowercased equivalent.

All of the following examples will return the value `hello, world`:

Figure 3.12 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::lower('HELLO, THERE');
6 
7 (string) str('HELLO, TheRE')
8     ->lower();
```

### 3.6 Reversing the Characters of a String

Figure 3.13 reverse Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function reverse(
 9     string $value
10 );
```

The `reverse` helper method generates a new string with all the character orders reversed.

The following example showcases how to use the reverse helper method on simple input:

Figure 3.14 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "!gnirts a ma I"
6 Str::reverse('I am a string!');
```

If you need to work with the reversed characters, it is much more efficient to split the input string manually, reverse that array, and then work with the resulting array directly. Calling `split` in this way will limit the number of times that `mb_str_split` is invoked, which can become expensive on substantial input text:

Figure 3.15 

```
1 <?php
2 
3 // The following returns a
4 // collection of characters.
5 str('I am a string!')
6     ->split(1)
7     ->reverse();
```

A palindrome is any word or phrase that reads the same backward or forward. We can make use of the `reverse` helper method to write a surprisingly efficient helper method to check if a word is a palindrome:

Figure 3.16 

```
 1 <?php
 2 
 3 $words = [
 4     'wow',
 5     'tuesday',
 6     'noon',
 7     'racecar',
 8 ];
 9 
10 Str::macro('isPalindrome', function ($word) {
11     return $word == static::reverse($word);
12 });
13 
14 collect($words)->map(function ($word) {
15     return $word.': '. (Str::isPalindrome($word) ? 'Yes' : 'No');
16 })->all();
```

The above example would result in the following:

Figure 3.17 

```
1 [
2     "wow: Yes",
3     "tuesday: No",
4     "noon: Yes",
5     "racecar: Yes",
6 ]
```

### 3.7 Creating a URL from a Title

Figure 3.18 slug Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function slug(
 9          string $title,
10          string $separator = '-',
11     string|null $language = 'en'
12 );
```

We can use the `slug` helper method to format the provided value into a URL-friendly version. This helper method is valuable when constructing URLs from dynamic input, such as a blog title.

Internally, the slug helper method will perform several steps to help produce the final string:

1.  Transliterates a string UTF-8 to its ASCII equivalent; you may provide an optional language to help influence this step.
2.  Converts spaces, dashes, and underscores to the desired URL separator.
3.  Replaces all instances of the “@” character with the word “at.”
4.  Removes all extra characters that are not the desired separator, letters, and numbers.

The following example uses a collection of titles to observe the behavior of the slug helper method:

Figure 3.19 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $titles = [
 6     'Generating Dynamic CSS',
 7     'Working with Dynamic Variables',
 8     'Conditional Parameters',
 9     'some/path/value--- _with_characters',
10     'Panic@the   disco'
11 ];
12 
13 collect($titles)->map(function ($title) {
14     return Str::slug($title);
15 })->all();
```

The previous example would produce output similar to the following:

Figure 3.20 

```
1 [
2     "generating-dynamic-css",
3     "working-with-dynamic-variables",
4     "conditional-parameters",
5     "somepathvalue-with-characters",
6     "panic-at-the-disco",
7 ]
```

Fluent strings can also make use of the `slug` helper method:

Figure 3.21 

```
1 <?php
2 
3 // Returns "an-existing-title"
4 (string) str('An-Existing_Title!')
5     ->slug('-');
```

### 3.8 Formatting Strings with snake\_casing

Figure 3.22 snake Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function snake(
 9     string $value,
10     string $delimiter = '_'
11 );
```

The `snake` helper method replaces all uppercase characters within the string with their lowercased variant, prefixed with the specified delimiter string (`_` by default). The delimiter will not be prepended to the output string if the first character of the input string is capitalized.

The `snake` helper method trims all extraneous whitespace when preparing the output string.

The following examples demonstrate how to use the `snake` helper method:

Figure 3.23 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "my_words"
 6 Str::snake('MyWords');
 7 
 8 // Customizing the delimiter.
 9 // Returns "my-words"
10 Str::snake('MyWords', '-');
11 
12 // Returns "m_y_w_o_r_d_s"
13 Str::snake('MYWORDS');
```

The fluent string API also provides a `snake` helper method:

Figure 3.24 

```
1 <?php
2 
3 // Returns "my_words"
4 (string) str('MyWords')
5     ->snake();
6 
7 // Returns "my-words"
8 (string) str('MyWords')
9     ->snake('-');
```

### 3.9 Removing Extra Whitespace from a String

Figure 3.25 squish Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 9
 5  *
 6  * @return string
 7  */
 8 public static function squish(
 9     string $value
10 );
```

The `squish` helper method is one of my favorite helper methods. Using it, we can collapse consecutive whitespace characters into a single space character. This helper method will convert newlines into spaces.

I took the following sample content from [https://stillat.com/blog/2021/02/15/implementing-a-customer-dsl-parser-in-php.](https://stillat.com/blog/2021/02/15/implementing-a-customer-dsl-parser-in-php.) Using the `squish` helper method, we can remove all of the extra spaces and newline characters and replace them with a single space:

Figure 3.26 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $content = <<<CONTENT
 6     By convention, we will say that when a single quote is proceeded
 7 	by a backslash (\) character within a string, only the single
 8 	quote will become part of the string's value.  
 9 
10     When a backslash is used as a way to indicate special output
11 	within a string, we will refer to it as the escape character. 
12 
13 
14     When a valid character follows the escape character, such as
15 	a single quote, we will refer to both the backslash and
16 	that next character as an escape sequence.   
17 
18     
19 CONTENT;
20 
21 Str::squish($content);
```

The `squish` method would return the following result in the previous example (newlines inserted for formatting):

Figure 3.27 

```
1 By convention, we will say that when a single quote is proceeded
2 by a backslash (\) character within a string, only the single
3 quote will become part of the string's value. When a backslash
4 is used as a way to indicate special output within a string, we
5 will refer to it as the escape character. When a valid character
6 follows the escape character, such as a single quote, we will refer
7 to both the backslash and that next character as an escape sequence.
```

You may notice that the `squish` helper method trimmed the extraneous whitespace at the start and end of the result string.

The `squish` helper method is also available for fluent strings:

Figure 3.28 

```
1 <?php
2 
3 str($content)
4     ->squish()
5     ->toString();
```

### 3.10 Formatting Strings with StudlyCasing

Figure 3.29 studly Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function studly(
 9     string $value
10 );
```

Studly caps are a way of formatting text with capital letters according to some pattern. The `studly` helper method removes the following word separators and capitalizes the first letter of each word it finds (while not affecting the case of any other characters):

*   Any number of spaces
*   The underscore (`_`)
*   The hyphen (`-`)

All of the following examples would return the result `MyWords`:

Figure 3.30 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::studly('my words');
 6 Str::studly('my   words');
 7 Str::studly('   my-words');
 8 
 9 (string) str(' my-words_')
10     ->studly();
```

Because the `studly` method does not affect the case of any letters after the first letter, we can arrive at an output that some users might not expect:

Figure 3.31 

```
1 <?php
2 
3 // Returns: "MyWORDS"
4 (string) str('my-WORDS')->studly();
5 
6 // Returns: "MYWORDS"
7 (string) str('MY_WORDS')->studly();
```

### 3.11 Formatting Strings with Title Casing

Figure 3.32 title Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function title(
 9     string $value
10 );
```

The `title` helper method will reformat the string to look like a traditional print title. This method may affect the case of every input string character.

All of the following examples will return the result `This Is A Title`:

Figure 3.33 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::title('THIS IS A TITLE');
 6 
 7 Str::title('this is a title');
 8 
 9 (string) str('ThIs iS a TiTlE')
10     ->title();
```

### 3.12 Uppercasing the First Character of a String

Figure 3.34 ucfirst Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function ucfirst(
 9     string $string
10 );
```

The `ucfirst` helper method is used to uppercase the first character of a string, and it defines only one parameter (the `$string`) which will have its first character uppercased. This helper method differs from PHP’s `ucfirst` function because the Laravel helper method handles multi-byte strings by reimplementing the `ucfirst` function using PHP’s multi-byte string API. Internally this method uses the UTF-8 character encoding.

All of the following examples will return the result `Conditional parameters`:

Figure 3.35 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::ucfirst('conditional parameters');
6 Str::ucfirst('Conditional parameters');
7 
8 (string) str('conditional parameters')
9     ->ucfirst();
```

### 3.13 Generating Upper Cased Variants of Strings

Figure 3.36 upper Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function upper(
 9     string $value
10 );
```

The `upper` helper method is the opposite of the lower method; the upper method returns the upper-cased variant. This method is helpful when performing invariant string comparisons or modifying content to display to an end-user, as well as when you just need to ensure a string is upper-cased.

Both of the following code examples would return the value `ALL UPPER CASED`:

Figure 3.37 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::upper('all upper cased');
6 
7 (string) str('all upper cased')
8     ->upper();
```

### 3.14 Counting the Number of Words in a String

Figure 3.38 wordCount Method Signature 

```
 1 <?php
 2 
 3 // Version: Laravel 8
 4 public static function wordCount(
 5     string $string
 6 );
 7 
 8 // Version: Laravel 9
 9 public static function wordCount(
10          string $string,
11     string|null $characters = null
12 );
```

The `wordCount` helper method is used to count the number of words in the provided string. Internally, this helper method calls PHP’s built-in `str_word_count` function.

Laravel 9 added the ability to specify a list of `$characters` used to help determine a word.

The `wordCount` helper method is simple to call and accepts the string to count the number of words as its first argument.

Figure 3.39 

```
1 <?php
2 
3 use Illuminate\Support\str;
4 
5 // Returns 2
6 Str::wordCount('Hello, wilderness');
```

The word “there” is misspelled in the following example as “th3r3”. We can leverage the characters parameter introduced in Laravel 9 to have this counted as a word:

Figure 3.40 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns 3
6 Str::wordCount('Hello, th3r3');
7 
8 // Returns 2
9 Str::wordCount('Hello, th3r3', '3');
```

The `Stringable` object also exposes a `wordCount` helper method, but unlike the `Str` version, it does not accept a characters argument:

Figure 3.41 

```
1 <?php
2 
3 // Returns 2
4 str('Hello, there')->wordCount();
```

## 4\. The Logical Helper Methods

The logical helper methods are a collection of utility methods that can help us make decisions based on the composition of our existing strings.

**Table 4.1** providers an overview of the logical helper methods we will discuss through this chapter:

Table 4.1 Logical Helper Methods

 
| Method || Description |
| --- | --- |
| contains || Tests if a string contains one or more provided substrings. |
| --- | --- |
| containsAll || Tests if a string contains all of the provided substrings. |
| endsWith || Tests if a string ends with a provided substring. |
| startsWith || Tests if a string starts with the provided substring. |
| isAscii || Tests if a string contains only ASCII characters. |

### 4.1 Checking If a String Contains Another String

Figure 4.1 contains Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 8
 5  * @return bool
 6  */
 7 public static function contains(
 8              string $haystack,
 9     string|string[] $needles
10 );
11 
12 // Version: Laravel 9
13 
14 /**
15  * @return bool
16  */
17 public static function contains(
18              string $haystack,
19     string|string[] $needles,
20                bool $ignoreCase = false
21 );
```

The `contains` helper method is used to check if a string (the `$haystack`) contains one or more substrings (the `$needles`). The method returns true if the haystack includes any of the provided needles. Otherwise, it returns false.

The case of the haystack and needles are essential, and similar strings with different casings will not be a match. Starting with Laravel 9, the `contains` search can be made case-insensitive.

The following examples demonstrate the primary usage of the `contains` helper method:

Figure 4.2 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $searchStrings = [
 6     'hello', 'wilderness', 'WORLD'
 7 ];
 8 
 9 // Returns "true"
10 Str::contains('Hello, wilderness', $searchStrings);
11 
12 // Returns "false"
13 Str::contains('HELLO, WILDERNESS', $searchStrings);
14 
15 // Disables the case-sensitive search.
16 // Returns "true"
17 Str::contains(
18     'HELLO, WORLD',
19     $searchStrings,
20     true
21 );
```

The `contains` method is also available on fluent strings, but it does not offer a way to disable the case-sensitive search:

Figure 4.3 

```
1 <?php
2 
3 // Returns "true"
4 str('HELLO, WORLD')->contains($searchStrings);
```

### 4.2 Checking If a String Contains Multiple Substrings

Figure 4.4 containsAll Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 8
 5  *
 6  * @return bool
 7  */
 8 public static function containsAll(
 9       string $haystack,
10     string[] $needles
11 );
12 
13 /**
14  * Version: Laravel 9
15  *
16  * @return bool
17  */
18 public static function containsAll(
19       string $haystack,
20     string[] $needles,
21         bool $ignoreCase = false
22 );
```

The `containsAll` helper method is used to check if a string (the `$haystack`) contains all of the provided substrings (the “needles”). The method returns true if, and only if, all of the substrings are present in the search string.

The case of the haystack and needles are essential, and similar strings with different casings will not be a match. Starting with Laravel 9, the contains search can be made case-insensitive.

The following examples demonstrate using the `containsAll` method to check if a string contains all search strings:

Figure 4.5 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $fruits = [
 6     'apple',
 7     'banana',
 8     'cherry',
 9 ];
10 
11 // Returns "false"
12 Str::containsAll(
13     'The fruits are: apple, and cherry.',
14     $fruits
15 );
16 
17 // Returns "true"
18 Str::containsAll(
19     'The fruits are: apple, banana, and cherry.',
20     $fruits
21 );
22 
23 // Disables the case-sensitive search.
24 // Returns "true"
25 Str::containsAll(
26     'The fruits are: APPLE, BANANA, and CHERRY.',
27     $fruits,
28     true
29 );
```

We can also use the `containsAll` method on fluent string instances, but it’s implementation does not provide a way to disable the case-sensitive search:

Figure 4.6 

```
1 <?php
2 
3 // Returns "true"
4 str('The fruits are: apple, banana, and cherry.')
5     ->containsAll($fruits);
```

### 4.3 Checking If a String Ends with Another String

Figure 4.7 endsWIth Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return bool
 7  */
 8 public static function endsWith(
 9              string $haystack,
10     string|string[] $needles
11 );
```

The `endsWith` helper method checks if a given string (the `$haystack`) ends with any of the supplied strings (the `$needles`). The haystack is any value that is convertible to a string.

A single needle can be supplied as a string to check if the haystack ends with that single needle. To check if a string ends with any number of needles, the needles are provided as an array of strings.

The following examples demonstrate the essential use of the `endsWith` helper method:

Figure 4.8 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $punctuation = [
 6     '.', '!', '?'
 7 ];
 8 
 9 // Returns "true"
10 Str::endsWith(
11     'A simple sentence.',
12     '.'
13 );
14 
15 // Returns "true"
16 Str::endsWith(
17     'A simple sentence.',
18     $punctuation
19 );
```

We may also use the `endsWith` method on fluent string instances:

Figure 4.9 

```
1 <?php
2 
3 // Returns "false"
4 str('Case matters')->endsWith('S');
5 
6 // Returns "true"
7 str('Another example string!')
8     ->endsWith($punctuation);
```

### 4.4 Checking If a String Starts with Another String

Figure 4.10 startsWith Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return bool
 7  */
 8 public static function startsWith(
 9              string $haystack,
10     string|string[] $needles
11 );
```

The `startsWith` helper method checks if a given string (the `$haystack`) starts with any of the supplied strings (the `$needles`). The haystack is any value that is convertible to a string. This helper method is the logical opposite of the `endsWith` helper method.

A single needle can be supplied as a string to check if the haystack starts with that single needle. To check if a string starts with any number of needles, the needles are provided as an array of strings.

Figure 4.11 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 
 6 $schemes = [
 7     'http://',
 8     'https://'
 9 ];
10 
11 // Returns "true"
12 Str::startsWith('https://stillat.com/', $schemes);
13 
14 // Case matters.
15 // Returns "false"
16 str('Just a simple sentence')
17     ->startsWith('j');
```

### 4.5 Checking If a String Contains Only ASCII Characters

Figure 4.12 isAscii Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return bool
 7  */
 8 public static function isAscii(
 9     string $value
10 );
```

You can use the `isAscii` helper method to check whether the provided string contains only ASCII characters. The results of this method can be useful to conditionally transliterate non-ASCII characters to their ASCII equivalents.

Some use-cases for the `isAscii` helper method may include:

*   Validating input into legacy software systems or hardware systems that only support ASCII encoding
*   Conditionally modifying runtime behavior if the input is not ASCII

The following examples demonstrate how you can use the `isAscii` method:

Figure 4.13 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "true"
6 Str::isAscii('Hello');
7 
8 // Returns "false"
9 str('你好')->isAscii();
```

This method can be combined with the transliterate helper method to achieve interesting results. As a refresher, you can use the transliterate method to convert non-ASCII characters to their closest ASCII equivalent:

Figure 4.14 

```
1 <?php
2 
3 // Returns "Ni Hao"
4 Str::transliterate('你好');
```

We can combine these two methods to create a function that generates URL slugs differently depending on if the input is ASCII:

Figure 4.15 

```
 1 <?php
 2 
 3 function makeSlug($title)
 4 {
 5     if (! Str::isAscii($title)) {
 6       $title = Str::transliterate($title);
 7     }
 8 
 9     return Str::slug($title);
10 }
11 
12 // Returns "hello-world"
13 makeSlug('Hello World');
14 
15 // Returns "ni-hao"
16 makeSlug('你好');
```

Fluent strings also provide a `whenIsAscii` helper method. This helper method accepts two callback functions: the first is invoked when the value of the fluent string is an ASCII string, and the second callback will be invoked when the input string is non-ASCII. We could rewrite our slug generating function using this helper method:

Figure 4.16 

```
1 <?php
2 
3 function makeSlug($title)
4 {
5     return str($title)->whenIsAscii(
6       fn($title) => $title->slug(),
7       fn($title) => str(Str::transliterate($title))->slug()
8     )->toString();
9 }
```

## 5\. The Construction Helper Methods

The construction helper methods help to produce new strings from existing strings in some way. For example, we can use the construction helper methods to replace substrings, split strings by specific characters or casing, or even limit strings to particular lengths.

**Table 5.1** provides an overview of the various construction methods we will encounter throughout this chapter:

Table 5.1 Construction Helper Methods

 
| Method || Description |
| --- | --- |
| ascii || Converts UTF-8 characters to their closest ASCII equivalent. |
| --- | --- |
| excerpt || Generates an excerpt of the provided text. |
| finish || Ensures a string ends with a given substring. |
| start || Ensures a string begins with a given substring. |
| length || Returns the length of the provided string. |
| limit || Truncates a string if it exceeds the provided character limit. |
| mask || Obscures parts of an existing string. |
| random || Generates pseudo-random strings of a given length. |
| remove || Removes parts of an existing string. |
| repeat || Repeats a given string a given number of times. |
| replace || Replace one, or many, substrings in an existing string. |
| replaceArray || Sequentially replaces substrings in an existing string, with a frequent use case replacing query parameters in a parameterized SQL statement. |
| replaceFirst || Replaces the first occurrence of a substring within the provided string. |
| replaceLast || Replaces the last occurrence of a string within the provided string. |
| swap || Replaces substrings in the provided string using a key/value pair as the source of the replacements. |
| ucsplit || Splits a string on capital letters into an array of strings. |

### 5.1 Transliterating Characters to ASCII

Figure 5.1 ascii Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function ascii(
 9     string $value,
10     string $language = 'en'
11 );
```

The `ascii` helper method is used to transliterate [UTF-8](https://en.wikipedia.org/wiki/UTF-8) characters to their closest [ASCII](https://en.wikipedia.org/wiki/ASCII) equivalent.

This method is useful when communicating with other software platforms that require ASCII, or when complying with protocols (such as HTTP) about how headers, or some values, need to be formatted or encoded.

#### Language Codes

The `ascii` method can accept the following language codes for the language parameter (`$language`):

| Language || Parameter Value |
| --- | --- |
| Amharic || `am` |
| --- | --- |
| Arabic || `ar` |
| Armenian || `hy` |
| Azerbaijani || `az` |
| Belarusian || `bg` |
| Bengali || `bn` |
| Bulgarian || `bg` |
| Chinese || `zh` |
| Croatian || `hr` |
| Czech || `cs` |
| Danish || `da` |
| Dutch || `nl` |
| English || `en` |
| Esperanto || `eo` |
| Estonian || `et` |
| Extra Latin Characters || `latin` |
| Extra Microsoft Word Characters || `msword` |
| Extra Whitespace Characters || ` ` (single space) |
| Finnish || `fi` |
| French Austrian || `fr_at` |
| French || `fr` |
| French Switzerland || `fr_ch` |
| Georgian || `ka` |
| German Austrian || `de_at` |
| German || `de` |
| German Switzerland || `de_ch` |
| Greeklish || `el__greeklish` |
| Greek || `el` |
| Hindi || `hi` |
| Hungarian || `hu` |
| Italian || `it` |
| Japanese || `ja` |
| Kazakh || `kk` |
| Kirghitz || `ky` |
| Korean || `ko` |
| Latvian || `lv` |
| Lithuanian || `lt` |
| Macedonian || `mk` |
| Mongolian || `mn` |
| Myanmar || `my` |
| Norwegian || `no` |
| Oriya || `or` |
| Pashto || `ps` |
| Persian || `fa` |
| Polish || `pl` |
| Portuguese || `pt` |
| Romanian || `ro` |
| Russian GOST 2000 B || `ru__gost2000_b` |
| Russian || `ru` |
| Russian Passport 2013 || `ru__passport2013` |
| Serbian Cyrillic || `sr__cyr` |
| Serbian || `sr` |
| Serbian Latin || `sr__lat` |
| Slovak || `sk` |
| Swedish || `sv` |
| Thai || `th` |
| Turkish || `tr` |
| Turkmen || `tk` |
| Ukranian || `uk` |
| Uzbek || `uz` |
| Vietnamese || `vi` |

The following example uses the `ascii` helper method to transliterate some characters to their closest English ASCII counterpart:

Figure 5.2 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "ASz"
6 Str::ascii('ÀŠž');
```

The `ascii` method is also available on fluent strings:

Figure 5.3 

```
1 <?php
2 
3 // Returns "ASz"
4 (string) str('ÀŠž')
5     ->ascii();
```

### 5.2 Generating Excerpts of Text

Figure 5.4 excerpt Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 9
 5  *
 6  * @return string|null
 7  */
 8 public static function excerpt(
 9     string $text,
10     string $phrase = '',
11      array $options = []
12 );
```

The `excerpt` helper method is used to generate an excerpt from a piece of text based on the *first* occurrence provided phrase. This method is handy for displaying the results of a user search.

The excerpt method would return a string if it could generate an excerpt from the provided text and search phrase. Otherwise, it returns `null`.

A key/value pair of options can change the behavior of the excerpt method. The excerpt method supports the following options:

Table 5.2 Excerpt Method Options

 
| Option || Description || Default Value |
| --- | --- | --- |
| radius || The number of characters around the provided phrase that should be included in the generated excerpt. || 100 |
| --- | --- | --- |
| omission || This option controls the text that will be added to the start or end of the generated excerpt if there are more characters on either side than the provided radius. || `...` |

The examples will use the following text^([4](#chap29.xhtml#fn-textsource)):

Figure 5.5 

```
1 <?php
2 
3 $text = <<<'EOT'
4 Before we start writing custom PHP code and developing our Antlers
5 templates, lets take a moment to think about what we are going to
6 build. We want to build a system that allows visitors to submit
7 their reactions to a piece of content. At a high level we will
8 have to develop the following pieces in order to make this work
9 EOT;
```

The following example generates an excerpt around the phrase “Antlers”. Since the default radius is 100, the resulting string will end with the omission string (`...` by default):

Figure 5.6 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::excerpt($text, 'Antlers');
```

Would result in:

Figure 5.7 

```
1 Before we start writing custom PHP code and developing our Antlers
2 templates, lets take a moment to think about what we are going to
3 build. We want to build a system...
```

A shorter excerpt can be generated by specifying a different value for the `radius` option:

Figure 5.8 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::excerpt(
 6     $text,
 7     'Antlers', [
 8       'radius' => 20
 9     ]
10 );
```

The previous code example would result in:

Figure 5.9 

```
1 ...and developing our Antlers templates, lets tak...
```

Using the `omission` option can be used to change the `...` that appears on both sides of the previous output:

Figure 5.10 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::excerpt(
 6     $text,
 7     'Antlers', [
 8       'radius' => 20,
 9       'omission' => '[...]'
10     ]
11 );
```

resulting in:

Figure 5.11 

```
1 [...]and developing our Antlers templates, lets tak[...]
```

### 5.3 Ensuring a String Always Ends with a Given String

Figure 5.12 finish Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function finish(
 9     string $value,
10     string $cap
11 );
```

The `finish` helper method will ensure that the provided string (the `$value`) always ends with exactly one occurrence of another string (the `$cap`). This helper method is advantageous when constructing URIs or file paths. The cap can be any string of characters and does not have to be only a single character.

The following are simple examples of how to use the `finish` method:

Figure 5.13 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "/home/path/"
 6 Str::finish('/home/path', '/');
 7 
 8 // Returns "/home/path/"
 9 Str::finish('/home/path/', '/');
10 
11 // Returns: "Sentences should end with a period, or full stop."
12 Str::finish(
13     'Sentences should end with a period, or full stop.',
14     '.'
15 );
```

The `finish` method can be combined with the `slug` helper method to generate HTML file names from blog post titles:

Figure 5.14 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "creating_dynamic_css_class_names.html"
6 Str::finish(
7     Str::slug('Creating Dynamic CSS Class Names', '_'),
8     '.html'
9 );
```

We may also use the `finish` method on fluent strings:

Figure 5.15 

```
1 <?php
2 
3 (string) str('Creating Dynamic CSS Class Names')
4     ->slug('_')
5     ->finish('.html');
```

### 5.4 Calculating String Length

Figure 5.16 length Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return int
 7  */
 8 public static function length(
 9          string $value,
10     string|null $encoding = null
11 );
```

You can use the `length` helper method to calculate the length of a given string. It uses PHP’s default encoding by default, but you may change the encoding used by supplying a second argument.

PHP will generate an `E_WARNING` error if the provided encoding is unknown.

All of the following examples would return the value `10`:

Figure 5.17 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::length('My string!');
6 Str::length('My string!', 'UTF-8');
7 str('My string!')
8     ->length();
```

### 5.5 Truncating Strings

Figure 5.18 truncate Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function limit(
 9     string $value,
10        int $limit = 100,
11     string $end = '...'
12 );
```

You can use the `limit` helper method to truncate the provided value if it exceeds some limit. The limit is 100 characters by default, but you can change this by supplying a value for the `$limit` parameter.

If the string exceeds the configured limit, an *end* string (`...` by default) is appended to the final string. If the original string does not exceed the limit, the original string will be returned.

The following examples will utilize content from [https://stillat.com/blog/2021/12/12/creating-a-content-reaction-system-with-statamic-3-and-antlers:](https://stillat.com/blog/2021/12/12/creating-a-content-reaction-system-with-statamic-3-and-antlers:)

Figure 5.19 

```
1 <?php
2 
3 $text = <<<TEXT
4 Taking a look at the current state of our Antlers partial, we can see
5 a lot of duplicate code starting to emerge. This problem will only
6 get worse over time since we will be referencing those field names
7 in a few places: once to create the buttons to submit a reaction,
8 and again to indicate what kinds of reactions have already been left.
9 TEXT;
```

With the method’s default values, the following code example:

Figure 5.20 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::limit($text);
```

Would produce this result:

Figure 5.21 

```
1 Taking a look at the current state of our Antlers partial, we can see
2 a lot of duplicate code starti...
```

We can control the output of the limit method by modifying the defaults of the limit and end parameters:

Figure 5.22 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "Taking a l..."
 6 Str::limit($text, 10);
 7 
 8 // The following examples both return:
 9 // "Taking a l... [Read More]"
10 Str::limit($text, 10, '... [Read More]');
11 
12 str($text)
13     ->limit(10, '... [Read More]')
14     ->toString();
```

### 5.6 Obscuring Parts of a String

Figure 5.23 mask Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function mask(
 9       string $string,
10       string $character,
11          int $index,
12     int|null $length = null,
13       string $encoding = 'UTF-8'
14 );
```

The `mask` helper method is a simple but handy string manipulation method. We can use this method to hide or obscure parts of an existing string. One of the most common applications of this helper method is to only store and display the last four digits of a credit card number:

Figure 5.24 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "************4242"
 6 Str::mask(
 7     '4242424242424242',
 8     '*', 
 9     0, -4
10 );
```

In the previous example, we are using several parameters. We indicate that the masking should start at the first character by supplying the value `0` for the index parameter. The `-4` for the length will cause our masking to continue until the last four characters in our input string, leaving the rest unmasked.

As another example of how we can use these parameters together, let us mask everything but the first character and the last four characters of the same sample credit card number:

Figure 5.25 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "4***********4242"
 6 Str::mask(
 7     4242424242424242,
 8     '*',
 9     1, -4
10 );
```

Alternatively, we can use a positive length to achieve the same result:

Figure 5.26 

```
1 <?php
2 
3 // Returns "4***********4242"
4 str('4242424242424242')
5     ->mask('*', 1, 11)
6     ->toString();
```

#### You Probably Shouldn’t Store Credit Card Numbers

So far, we’ve used sample credit card numbers to experiment with the mask helper method. I chose credit card numbers because they are easy to visualize the behavior of the mask helper method. Still, I should note that you should not be storing credit card numbers or similar information, if possible. For this type of information, it is much safer for you and your users to keep as little information as possible, such as the last four digits of the credit card number, and use other helper methods to produce the intended visual representation:

Figure 5.27 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "************4242"
6 Str::padLeft(4242, 16, '*');
```

With that out of the way, what are some use cases where the mask helper method is beneficial?

The first use case that comes to mind is when your application does store sensitive data, such as third-party API keys. In these situations, displaying a masked API key is often desirable to help users manage their linked credentials. Even under these conditions, I recommend storing the real API key in a location not retrievable in the application’s main execution path and keeping a masked version of the API key for display purposes.

### 5.7 Generating Pseudo-Random Strings

Figure 5.28 random Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function random(
 9     int $length = 16
10 );
```

You can use the `random` helper method to generate a random string of an arbitrary length (by default, the method will return a string 16 containing characters). Unless the application uses a custom random string generator, the helper method will use PHP’s built-in `random_bytes` function to generate a series of cryptographically secure pseudo-random bytes.

By default, the `random` helper method will never contain the following characters in its output: `/`, `+`, and `=`.

The following two examples will both generate random strings 16 characters long:

Figure 5.29 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Generates 16-character random strings.
6 Str::random(16);
7 Str::random();
```

You can modify the length of the random string by supplying a custom length value:

Figure 5.30 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Generate a 32-character random string.
6 Str::random(32);
```

### 5.8 Removing Substrings or Characters from Strings

Figure 5.31 remove Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function remove(
 9     string|array<string> $search,
10                   string $subject,
11                     bool $caseSensitive = true
12 );
```

The `remove` helper method is simple yet powerful, and you can use it to remove one or many values from any given string. The removal is case-sensitive by default, but you can change this behavior by supplying a false value for the third argument.

You can remove a single string from the subject by supplying a single string argument for the first parameter or multiple strings by providing an array of strings.

A few example use cases of the remove helper method include:

*   Removing path traversal strings from input
*   A naïve word filter
*   Removing special characters

The following example will remove any of the specified special characters from the input string:

Figure 5.32 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $specialCharacters = [
 6     '!', '@', '#', '$', '%', '^',
 7     '&', '*', '(', ')', '-', '?'
 8 ];
 9 
10 // Returns "Hello"
11 Str::remove(
12     $specialCharacters,
13     'Hello!?!',
14 );
```

Fluent strings also provide a `remove` method:

Figure 5.33 

```
 1 <?php
 2 
 3 // Performs a case-sensitive removal.
 4 // Returns "Hello, world!"
 5 (string) str('Hello, world!')
 6     ->remove(', WORLD');
 7 
 8 // Performs a case-insensitive removal.
 9 // Returns "Hello!"
10 (string) str('Hello, world!')
11     ->remove(', WORLD', false);
```

### 5.9 Repeating Strings and Characters

Figure 5.34 repeat Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function repeat(
 9     string $string,
10        int $times
11 );
```

You can use the `repeat` helper method to repeat an input string a specified number of times. As an example, the following code samples would return the value “**********”:

Figure 5.35 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::repeat('*', 10);
6 
7 (string) str('*')
8     ->repeat(10);
```

The following is a more complicated example and uses the `repeat` helper to pretty-print a directory listing recursively:

Figure 5.36 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function printDirectory($directory, $depth = 1)
 6 {
 7     $ouptut = '';
 8     $ignoreFiles = ['.', '..'];
 9 
10     if ($depth == 1) {
11         $ouptut = '/' . basename($directory);
12     } else {
13         $ouptut = Str::repeat(' ', $depth) . '/' . basename($directory);
14     }
15 
16     $ouptut .= collect(scandir($directory))
17         ->filter(function ($file) use ($ignoreFiles) {
18             return !in_array($file, $ignoreFiles);
19         })->join(function ($item) use ($directory, $depth) {
20             $fullPath = $directory . '/' . $item;
21 
22             if (is_dir($fullPath)) {
23                 return "\n" . printDirectory($fullPath, $depth + 1);
24             } else {
25                 return "\n" . Str::repeat(' ', $depth) . ' - ' . $item;
26             }
27         });
28 
29     return $ouptut;
30 }
```

The `printDirectory` function retrieves all the files and folders from a directory and uses the repeat helper method to add whitespace before the file or directory name. When we call the function recursively, we increment the depth each time, which indents nested listings in the final output.

As an example, if we were to call this function on the resource path in a fresh Laravel installation:

Figure 5.37 

```
1 <?php
2 
3 echo printDirectory(resource_path());
```

The output would be:

Figure 5.38 

```
1 /resources
2   /css
3    - app.css
4   /js
5    - app.js
6    - bootstrap.js
7   /views
8    - welcome.blade.php
```

And for the public directory:

Figure 5.39 

```
1 /public
2   - .htaccess
3   - favicon.ico
4   - index.php
5   - robots.txt
```

### 5.10 Replacing Substrings

Figure 5.40 replace Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function replace(
 9     string|string[] $search,
10     string|string[] $replace,
11     string|string[] $subject
12 );
```

The `replace` helper method can find and replace strings within an existing string. You can also use this method to replace multiple strings within a single value or even replace multiple strings across many values.

The `replace` helper is useful for, but not limited to:

*   Normalizing file path delimiters
*   Replacing line breaks with HTML elements in a text
*   Dynamically modifying PHP namespace strings

The following example demonstrates using the `replace` helper to do a simple replacement in a single string:

Figure 5.41 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "working_with_dynamic_variables"
 6 Str::replace(
 7     '-',
 8     '_',
 9     'working-with-dynamic-variables'
10 );
```

Fluent strings also provide the `replace` method. The following example would produce the same result as the previous code example:

Figure 5.42 

```
1 <?php
2 
3 // Returns "working_with_dynamic_variables"
4 str('working-with-dynamic-variables')
5     ->replace('-', '_')
6     ->toString();
```

We can search for multiple input strings and replace all occurrences with a single value. The following example uses this technique to normalize directory separators in a path. The exact output this sample will return will depend on the system running the code sample; on my system, it returns the result `\some\path\`:

Figure 5.43 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::replace(
6     ['\\', '/'],
7     DIRECTORY_SEPARATOR,
8     '/some/path/'
9 );
```

We can also supply arrays for both the search and replace parameters. The values of the arrays will be paired together and used to perform the replacements. Doing this can help clean up repeated calls to the replace method. For example, consider the following repeated calls to the `replace` method:

Figure 5.44 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = <<<TEXT
 6 Hello, there,
 7 
 8 Please email support@example.org
 9 
10 Thanks!
11 TEXT;
12 
13 $result = Str::replace(
14     '@',
15     '[at]',
16     $text
17 );
18 
19 $result = Str::replace(
20     "\n",
21     '<br />',
22     $result
23 );
```

We could refactor those calls to a single call like so:

Figure 5.45 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::replace(
6     [ '@',    "\n" ],
7     [ '[at]', '<br />', ],
8     $text
9 );
```

And finally, we can also supply an array of strings as the value to perform replacements on:

Figure 5.46 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $addresses = [
 6     'address1@example.org',
 7     'address2@example.org',
 8     'address3@example.org',
 9 ];
10 
11 Str::replace(
12     '@', '[at]',
13     $addresses
14 );
```

Which would return an array with the following values:

Figure 5.47 

```
1 [
2     "address1[at]example.org",
3     "address2[at]example.org",
4     "address3[at]example.org",
5 ]
```

### 5.11 Sequentially Replacing Substrings in a String

Figure 5.48 replaceArray Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function replaceArray(
 9                        string $search,
10     array<int|string, string> $replace,
11                        string $subject
12 );
```

Applications can use the `replaceArray` helper method to sequentially replace placeholders in a string from an array of values. This helper method is most commonly used to construct SQL queries but can be used for any number of things, including creating URLs or as a simple way to accept user template strings.

The first argument supplied to the `replaceArray` helper method will be the value the method should replace in the target string (the “subject”). The second argument will be an array containing all of the values that are used to replace the placeholder value in the string. The first occurrence of the search string is replaced by the first element of the replace array, the second element of the array will replace the second occurrence of the search string, and so on. If there are more items in the replace array than occurrences of the search string, the helper method will not replace the remaining search strings within the subject.

The following example demonstrates the behavior of the `replaceArray` helper method:

Figure 5.49 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "1 2 3"
 6 Str::replaceArray(
 7     '?',
 8     [1, 2, 3],
 9     '? ? ?'
10 );
```

You can also use the `replaceArray` method on fluent string instances:

Figure 5.50 

```
1 <?php
2 
3 // Returns "1 2 3"
4 str('? ? ?')
5     ->replaceArray(
6       '?', [1, 2, 3]
7     )
8     ->toString();
```

If there are more occurrences of the search string than replacement values, the `replaceArray` helper method will not replace the remaining search strings:

Figure 5.51 

```
1 <?php
2 
3 // Returns "1 2 ?"
4 str('? ? ?')
5     ->replaceArray(
6       '?', [1, 2]
7     )
8     ->toString();
```

Similarly, if there are *no* replacement values, no occurrences of the search string are replaced:

Figure 5.52 

```
1 <?php
2 
3 // Returns "? ? ?"
4 str('? ? ?')
5     ->replaceArray(
6       '?', []
7     )
8     ->toString();
```

### 5.12 Replacing the First Occurrence of a Substring or Character

Figure 5.53 replaceFirst Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function replaceFirst(
 9     string $search,
10     string $replace,
11     string $subject
12 );
```

You can use the `replaceFirst` helper method to replace the first occurrence of a string with a value with some other value. This method is helpful in several situations, including, but not limited to:

*   Replacing content in simple templates,
*   Modifying URL schemes on the fly,
*   Modifying file-system paths

The following example uses the `replaceFirst` helper to convert the URL “[https://stillat.com/](https://stillat.com/)” into a scheme-less URL:

Figure 5.54 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "//stillat.com/"
6 Str::replaceFirst(
7     'https:', '',
8     'https://stillat.com/'
9 );
```

The previous example can also be written using fluent strings like so:

Figure 5.55 

```
1 <?php
2 
3 str('https://stillat.com/')
4     ->replaceFirst('https:', '')
5     ->toString();
```

The following simple example utilizes the `replaceFirst` method to convert the path from a storage path to a public path. Notice the `replaceFirst` helper method replaced only the first instance of the “storage/” search string:

Figure 5.56 

```
1 <?php
2 
3 // Returns "public/users/storage/profile/"
4 str('storage/users/storage/profile/')
5     ->replaceFirst('storage/', 'public/')
6     ->toString();
```

### 5.13 Replacing the Last Occurrence of a Substring or Character

Figure 5.57 replaceLast Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function replaceLast(
 9     string $search,
10     string $replace,
11     string $subject
12 );
```

The `replaceLast` helper method is the opposite of `replaceFirst`. You can use it to find the last occurrence of some search string and replace it with another value. You can use this method for many useful things, including but not limited to:

*   Replacing file extensions dynamically
*   Modifying the format of currencies
*   Making error messages more friendly
*   Modifying PHP namespace strings

The following example utilizes `replaceLast` to replace file extensions within a single path:

Figure 5.58 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "some/video/path.png"
 6 Str::replaceLast(
 7     '.mp4',
 8     '.png',
 9     'some/video/path.mp4'
10 );
```

Fluent string instances also provide a `replaceLast` method. The following example would produce the same output:

Figure 5.59 

```
1 <?php
2 
3 // Returns "some/video/path.png"
4 str('some/video/path.mp4')
5     ->replaceLast('.mp4', '.png')
6     ->toString();
```

If we wanted to do the same thing for an array of URLs, we could use a collection to help change all of the values:

Figure 5.60 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $videos = [
 6     'courses/course/episode_1.mp4',
 7     'courses/course/episode_2.mp4',
 8     'courses/course/episode_3.mp4',
 9 ];
10 
11 collect($videos)->map(function ($url) {
12     return Str::replaceLast(
13       '.mp4',
14       '.png',
15       $url
16     );
17 })->all();
```

Which would return an array with the following values:

Figure 5.61 

```
1 [
2     "courses/course/episode_1.png",
3     "courses/course/episode_2.png",
4     "courses/course/episode_3.png",
5 ]
```

### 5.14 Ensuring Strings Always Begin with a Specific Prefix

Figure 5.62 start Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function start(
 9     string $value,
10     string $prefix
11 );
```

The `start` helper method is the opposite of the finish helper method. It ensures that the provided value always begins with some prefix. This method can be helpful when generating absolute URLs from relative paths, ensuring hierarchical blog post slugs always start with their parent slug, constructing dynamic PHP class names with namespaces, etc.

The following simple example will use a collection of class names and ensures that all of the provided class names begin with the `Illuminate\Support` namespace:

Figure 5.63 

```
 1 <?php
 2 
 3 $classes = [
 4     'Illuminate\Support\Str',
 5     'Arr',
 6     'Carbon',
 7 ];
 8 
 9 collect($classes)->map(function ($class) {
10     return Str::start($class, 'Illuminate\Support\\');
11 })->all();
```

The previous code sample would produce the following result:

Figure 5.64 

```
1 [
2     "Illuminate\Support\Str",
3     "Illuminate\Support\Arr",
4     "Illuminate\Support\Carbon",
5 ]
```

The following example will create a simple PHP class named `BlogPost`. This blog post class will contain the title, URL, and an optional parent blog post. This class also defines a `getUrl` method that will generate a URL for the blog post instance. The `getUrl` method will do an interesting thing if the blog post has a parent.

When a blog post does not have a parent, we will ensure that all generated URLs begin with the “/” character. However, when there is a parent blog post, we call the `getUrl` method on the parent post and use that value as the prefix for our current blog post.

Figure 5.65 

```
 1 <?php
 2 
 3 class BlogPost
 4 {
 5     public function __construct(
 6       public string $title,
 7       public string $url,
 8       public ?BlogPost $parent = null
 9     ) { }
10 
11     public function getUrl()
12     {
13       return Str::start(
14           $this->url,
15           Str::finish($this->parent?->getUrl() ?? '/', '/'),
16         );
17     }
18 }
```

Now that we have our `BlogPost` class, let’s create a few instances and how the `getUrl` method behaves:

Figure 5.66 

```
 1 <?php
 2 
 3 // Create some example blog posts.
 4 $postOne = new BlogPost(
 5     'The First', 'the-first'
 6 );
 7 
 8 $postTwo = new BlogPost(
 9     'The Second', 'the-second'
10 );
11 
12 $postThree = new BlogPost(
13     'The Third', 'the-third', $postOne
14 );
15 
16 $postFour = new BlogPost(
17     'The Fourth', 'the-fourth', $postThree
18 );
19 
20 // Use a collection to get the URLs of all blog posts.
21 collect([
22     $postOne,
23     $postTwo,
24     $postThree,
25     $postFour
26 ])->map(function (BlogPost $post) {
27     return $post->getUrl();
28 })->all();
```

The above code example would produce the following output:

Figure 5.67 

```
1 [
2     "/the-first",
3     "/the-second",
4     "/the-first/the-third",
5     "/the-first/the-third/the-fourth",
6 ]
```

As you can see from the last two examples in the output, you can use the `start` helper method to help produce recursive/hierarchical URLs relatively quickly.

### 5.15 Replacing a Key/Value Pair of Strings within a String

Figure 5.68 swap Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function swap(
 9      array $map,
10     string $subject
11 );
```

The `swap` helper method is another way to replace values in an existing string. The `swap` method accepts a key/value pair of string replacements as its first argument and the string to replace values as its second. The behavior of the `swap` method is quite different from other string replacement methods you may have encountered.

To highlight the behavior differences, we will create a simple canned email template function. We will first implement this function using the replace helper method. We will use the following email template across all the following examples:

Figure 5.69 

```
 1 <?php
 2 
 3 $emailTemplate = <<<TEMPLATE
 4 Hello [name],
 5 
 6 Thank you for reaching out! We are working to process your request;
 7 in the meantime, you may find the following resources helpful:
 8 [resources]
 9 
10 Sincerely,
11 [sender]
12 TEMPLATE;
```

Our email template function will accept the template, the recipient’s name, a link to additional resources, as well as the name of the sender. Our first version of this function may look like the following:

Figure 5.70 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function renderEmailTemplate($template, $name, $resources, $sender) {
 6     return Str::replace(
 7         [ '[name]', '[resources]', '[sender]', ],
 8         [ $name, $resources, $sender, ],
 9         $template
10     );
11 }
```

We can test the output of our function with the following:

Figure 5.71 

```
1 <?php
2 
3 renderEmailTemplate(
4     $emailTemplate,
5     'Alice',
6     'https://stillat.com/blog',
7     'Core Team'
8 );
```

And we would get the following return value:

Figure 5.72 

```
1 Hello Alice,
2 
3 Thank you for reaching out! We are working to process your request;
4 in the meantime, you may find the following resources helpful:
5 https://stillat.com/blog
6 
7 Sincerely,
8 Core Team
```

The issue with this approach is that if our input contains our template’s placeholders, traditional string replacement methods will replace them as the replace helper method works through the list of replacements. The following example calls the `renderEmailTemplate` function but uses one of the template placeholders in the name:

Figure 5.73 

```
1 <?php
2 
3 renderEmailTemplate(
4     $emailTemplate,
5     '[resources] Director',
6     'https://stillat.com/blog',
7     'Core Team'
8 );
```

Which produces the following result:

Figure 5.74 

```
1 Hello https://stillat.com/blog Director,
2 
3 Thank you for reaching out! We are working to process your request;
4 in the meantime, you may find the following resources helpful:
5 https://stillat.com/blog
6 
7 Sincerely,
8 Core Team
```

While this may seem benign, this type of behavior can lead to hard-to-diagnose bugs or behavior or could even be used to retrieve sensitive information depending on the implementation of the templating system.

To get around this behavior, we can re-implement our email templating function using the `swap` helper method. The `swap` helper method will replace our template placeholders like before, but importantly - it will *not* replace values in the inserted text.

Figure 5.75 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function renderEmailTemplate($template, $name, $resources, $sender) {
 6     return Str::swap(
 7         [
 8             '[name]' => $name,
 9             '[resources]' => $resources,
10             '[sender]' => $sender,
11         ],
12         $template
13     );
14 }
```

Using our refactored function, we can again invoke it with the problematic input. But using the `swap` helper method instead, we now get the output we would expect:

Figure 5.76 

```
1 Hello [resources] Director,
2 
3 Thank you for reaching out! We are working to process your request;
4 in the meantime, you may find the following resources helpful:
5 https://stillat.com/blog
6 
7 Sincerely,
8 Core Team
```

The `swap` method is also available on fluent string instances; we could rewrite the previous example as:

Figure 5.77 

```
1 <?php
2 
3 function renderEmailTemplate($template, $name, $resources, $sender) {
4     return str($template)->swap([
5         '[name]' => $name,
6         '[resources]' => $resources,
7         '[sender]' => $sender,
8     ])->toString();
9 }
```

When the `swap` helper method is processing its string replacements, it processes the replacement map based on the length of the key, starting with the longest. Because of this, the following method calls are equivalent:

Figure 5.78 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::swap([
 6         '[name]' => $name,
 7         '[sender]' => $sender,
 8         '[resources]' => $resources,
 9     ],
10     $template
11 );
12 
13 Str::swap([
14         '[resources]' => $resources,
15         '[sender]' => $sender,
16         '[name]' => $name,
17     ],
18     $template
19 );
```

### 5.16 Splitting Strings on Uppercase Characters

Figure 5.79 ucsplit Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return array
 7  */
 8 public static function ucsplit(
 9     string $string
10 );
```

The `ucsplit` helper method will break the input string into an array of strings by uppercase characters. This method can be handy to undo or retrieve the parts of a string that has been previously `camelCased`.

All text that appears between uppercased characters will be part of the first match.

The following example demonstrates the behavior of `ucsplit` when there is text in between uppercased characters:

Figure 5.80 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::ucsplit('He stood there, looking out over The Island.');
```

Which returns:

Figure 5.81 

```
1 [
2     "He stood there, looking out over ",
3     "The ",
4     "Island.",
5 ]
```

The following example makes use of the fluent `ucsplit` method to break apart a PHP function name. An essential difference between the fluent helper and the `Str` helper is the fluent helper will return a Collection instance, while the `Str` helper returns an array:

Figure 5.82 

```
1 <?php
2 
3 str('matchAll')
4     ->ucsplit()
5     ->all(); // Retrieve all items from the collection.
```

## 6\. The Extraction Helper Methods

Throughout this chapter, we will discuss the helper methods that are commonly used to help construct new strings from existing strings.

**Table 6.1** provides an overview of the various extraction methods we will encounter throughout this chapter:

Table 6.1 Extraction Helper Methods

 
| Method || Description |
| --- | --- |
| after || Returns a substring that appears after the provided search string. |
| --- | --- |
| afterLast || Returns a substring that appears after the last occurrence of the provided search string. |
| before || Returns the substring that appears before the first occurrence of a provided search string. |
| beforeLast || Returns the substring that appears before the last occurrence of a provided search string. |
| between || Returns the substring that appears between two search strings. |
| betweenFirst || Returns the smallest substring that appears between two search strings. |
| words || Limits the number of words that appear within the provided string. |
| substr || Extracts a substring from the provided string. |
| substrCount || Counts the number of times a substring appears within the provided search string. |
| substrReplace || Replaces or inserts substrings at a particular location within the provided string. |

### 6.1 Returning Part of a String after Another String or Character

Figure 6.1 after Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function after(
 9     string $subject,
10     string $search
11 );
```

The `after` method can be used to return part of a string after the *first* occurrence of another string, the `$search` string.

This method can be used to help parser URL query strings, or to quickly find substrings based on a certain character or substring.

The `after` method can be used to retrieve a section of a string that appears after a specific character like so:

Figure 6.2 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "ref=newsletter"
6 Str::after('https://stillat.com?ref=newsletter', '?');
```

We may also use the `after` method on fluent string instances:

Figure 6.3 

```
1 <?php
2 
3 // Returns 'ref=newsletter'
4 (string) str('https://stillat.com?ref=newsletter')
5     ->after('?');
```

### 6.2 Returning a Substring after the Last Occurrence of a String or Character

Figure 6.4 afterLast Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function afterLast(
 9     string $subject,
10     string $search
11 );
```

The `afterLast` helper method is similar to the `after` helper in that it can be used to retrieve a portion of a string after some character or substring, the `$search` string. The difference with the `afterLast` helper method is that it will return the section of a string that appears after the *last* occurrence of the provided search string.

The `afterLast` helper method can be used to retrieve the last part of a file path by specifying `/` as the search string:

Figure 6.5 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 
6 // Returns "name'
7 Str::afterLast('var/path/directory/name', '/');
```

We can also use the `afterLast` method on fluent string instances:

Figure 6.6 

```
1 <?php
2 
3 // Returns "name"
4 (string) str('var/path/directory/name')
5     ->afterLast('/');
6 
7 // Returns "Third"
8 (string) str('First, Second, Third')
9     ->afterLast(',')->trim();
```

### 6.3 Returning Part of a String before Another String or Character

Figure 6.7 before Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function before(
 9     string $subject,
10     string $search
11 );
```

The `before` helper method can be used to return the part of a string that appears before the first occurrence of a search string, or single character.

This method can be used to help parse URL query strings, or to quickly find substrings that appear before a certain character. This method is the logical opposite of the `after` helper method.

The following example uses the `before` method to return the contents of the string that appear before the first occurrence of the `?` character:

Figure 6.8 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "https://stillat.com"
6 Str::before('https://stillat.com?ref=newsletter', '?');
```

We can also call the `before` method on fluent string instances:

Figure 6.9 

```
1 <?php
2 
3 // Returns "https://stillat.com"
4 (string) str('https://stillat.com?ref=newsletter')
5     ->before('?');
6 
7 // Returns "Stop"
8 (string) str('Stop. Hammer time.')
9     ->before('.');
```

### 6.4 Retrieving All Content before the Last Occurrence of a Substring or Character

Figure 6.10 beforeLast Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function beforeLast(
 9     string $subject,
10     string $search
11 );
```

The `beforeLast` helper method will return everything in a string that appears before the *last* occurrence of a given search string. Contrast this behavior with the before helper function, which will return everything before the search string’s *first* occurrence.

The following example makes use of the `beforeLast` helper method to return everything in the provided path that appears before the final directory separator character:

Figure 6.11 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "/some/path"
6 Str::beforeLast('/some/path/', '/');
```

As an example of the fluent strings helper method, the following example will return the namespace of the PHP class:

Figure 6.12 

```
1 <?php
2 
3 // Returns "Illuminate\Support"
4 (string) str('Illuminate\Support\Str')->beforeLast('\\');
```

### 6.5 Retrieving Content between Two Search Strings

Figure 6.13 between Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function between(
 9     string $subject,
10     string $from,
11     string $to
12 );
```

The `between` helper method is interesting because it allows you to retrieve sections of a string that appear *between* two other search strings (the “from” and “to” search strings).

The following example uses the between `method` to return the part of a directory that appears between a known root directory and the final directory separator character:

Figure 6.14 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "some/nested/directory"
6 Str::between('/root/path/some/nested/directory/',
7 	'/root/path/', '/');
```

To demonstrate the fluent string version of this helper method and to show that it is helpful in a wide range of situations (not just dull file-system paths), the following will return what a prince turned into after a princess kissed it:

Figure 6.15 

```
1 <?php
2 
3 // Returns "prince"
4 (string) str("The princess kissed the frog
5               and it turned into a prince.")
6     ->between('turned into a', '.');
```

### 6.6 Retrieving the Smallest Amount of Content between Two Search Strings

Figure 6.16 betweenFirst Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Version: Laravel 9
 5  *
 6  * @return string
 7  */
 8 public static function betweenFirst(
 9     string $subject,
10     string $from,
11     string $to
12 );
```

The `betweenFirst` helper method will return the smallest amount of text between two search strings (the `$from` and `$to` arguments).

The following example uses the `betweenFirst` method to retrieve the name of the first directory in a given path that appears *after* a known root directory:

Figure 6.17 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "some"
6 Str::betweenFirst(
7     '/root/path/some/nested/directory/',
8     '/root/path/', '/'
9 );
```

In contrast, the following example will return the first directory in the provided path:

Figure 6.18 

```
1 <?php
2 
3 // Returns "root"
4 (string) str('/root/path/some/nested/directory/')
5     ->betweenFirst('/', '/');
```

### 6.7 Limiting the Number of Words in a String

Figure 6.19 words Method Signature 

```
 1 <?php
 2 
 3 /*
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function words(
 9     string $value,
10        int $words = 100,
11     string $end = '...'
12 );
```

The `words` helper method is similar to the `limit` helper method, but instead of limiting the number of characters returned, it can be used to limit the number of *words* returned.

The following examples demonstrate the usage of the `words` helper method:

Figure 6.20 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "Hello everyone..."
 6 Str::words('Hello everyone out there!', 2);
 7 
 8 // Returns "Hello everyone [Read More]"
 9 Str::words('Hello everyone out there!', 
10       2, ' [Read More]');
```

We may also use the `words` helper method on fluent strings:

Figure 6.21 

```
1 <?php
2 
3 // Returns "Hello everyone..."
4 (string) str('Hello everyone out there!')
5     ->words(2);
```

### 6.8 Getting Portions of a String

Figure 6.22 substr Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function substr(
 9       string $string,
10          int $start,
11     int|null $length = null
12 );
```

You can use the `substr` helper method to retrieve portions of an existing string. This helper defines a start argument and an optional length argument.

If the start value is positive, the method will return text starting at that location in the original string. If a length has not been provided or is longer than the remaining text, the `substr` method will return all text after the start position.

When the start value is negative, that number of characters will be returned starting at the *end* of the input string.

The following examples demonstrate the basic usage of the `substr` helper method:

Figure 6.23 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $testString = '0123456789';
 6 
 7 // Returns "56789"
 8 Str::substr($testString, 5);
 9 
10 // Returns "6789"
11 Str::substr($testString, 6);
12 
13 // Returns
14 Str::substr($testString, 6, 2);
```

The `substr` method can also be called on fluent strings. In the following example, the `substr` method is used to retrieve the last two characters of the string:

Figure 6.24 

```
1 <?php
2 
3 // Returns "89"
4 (string) str('0123456789')
5     ->substr(-2);
```

And in this example, it is used to retrieve the second to last character:

Figure 6.25 

```
1 <?php
2 
3 // Returns "8"
4 (string) str('0123456789')
5     ->substr(-2, 1);
```

An everyday use case for retrieving substrings of another value is to simplify the display of complex/pseudo-random information within user interfaces. One example of this is something that most developers may be familiar with, and that is the shortening of git commit hashes. The following example retrieves the first part of a git commit hash to display to an end user, similar to how the GitHub user interface displays shortened commit hashes:

Figure 6.26 

```
1 <?php
2 
3 // Returns "3b649c0"
4 str('3b649c0e4aad6127f647cc0f3c1a037399b06461')
5     ->substr(0, 7)
6     ->toString();
```

### 6.9 Counting Occurrences of a Search String

Figure 6.27 substrCount Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return int
 7  */
 8 public static function substrCount(
 9       string $haystack,
10       string $needle,
11          int $offset = 0,
12     int|null $length = null
13 );
```

You can use the `substrCount` helper method to count the number of times a particular string appears in a value. Applications can use this method to perform any of the following tasks (but are not limited to these):

*   Determine if an IP address is a v4 or v6 address.
*   Validate user input.
*   Check if a domain has at least a certain number of parts.
*   Determine if a file contains specific content or PHP tags.

The following example checks if the provided string is an IP v4 or v6 address by detecting the presence of the “:” character:

Figure 6.28 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function isIpv6($address) {
 6     return Str::substrCount($address, ':') > 0;
 7 }
 8 
 9 
10 // Returns "true"
11 isIpv6('0:0:0:0:0:0:0:1');
12 
13 // Returns "false"
14 isIpv6('127.0.0.1');
```

The `substrCount` helper method defines several parameters you can use to modify its behavior. The following example uses the offset parameter, which specifies at what point in the string to start counting substrings. This example counts the number of “\” characters that appear after a known root PHP namespace to determine the number of nested namespaces:

Figure 6.29 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "2"
 6 Str::substrCount(
 7     'Illuminate\Database\Console\Migrations',
 8     '\\',
 9     Str::length('Illuminate\Database')
10 );
```

We could also rewrite the previous example using fluent strings:

Figure 6.30 

```
1 <?php
2 
3 str('Illuminate\Database\Console\Migrations')
4     ->substrCount(
5       '\\', str('Illuminate\Database')->length());
```

We can also specify a negative start offset that causes the search to start at the end of the string. The following example also makes use of the length parameter to ensure that the method will only look at a single character:

Figure 6.31 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "1"
 6 Str::substrCount(
 7     'some/path.png',
 8     '.', // The character to count.
 9     -4,  // Start counting 4 characters from the end.
10      1   // Only search one character.
11 );
```

### 6.10 Replacing Strings within a Portion of an Existing String

Figure 6.32 substrReplace Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string|array
 7  */
 8 public static function substrReplace(
 9       string|array $string,
10       string|array $replace,
11          array|int $offset = 0,
12     array|int|null $length = null
13 );
```

The `substrReplace` helper method is an interesting one. At a high level, we can use it to replace portions of an existing string. That can be a confusing explanation, so we can think of it as being capable of doing the following (and more):

*   Inserting text into a current string at a specific location
*   Replacing text in an existing string at a specific location
*   Skipping parts of a string while performing string replacements

In the following example, we will use the `substrReplace` helper method to replace the last character of our string by supplying the value `-1` as our argument for the offset parameter. When our offset is negative, it will cause the `substrReplace` method to perform its replacement starting at the end of the string:

Figure 6.33 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "Hello, world."
 6 Str::substrReplace(
 7     'Hello, world!',
 8     '.',
 9     -1
10 );
```

The following examples use both the offset and length parameters to control the behavior of the `substrReplace` method.

Figure 6.34 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "Hello_world!"
6 Str::substrReplace(
7     'Hello, world!',
8     '_', 5, 2
9 );
```

In the previous example, the `substrReplace` method performs the following actions for us:

*   Find the substring starting at character five (zero-based indexing) that is two characters long; this locates the “, “ character sequence.
*   Replace the “, “ character sequence with “\_” and return the modified string

Fluent strings also provide a `substrReplace` method. We can rewrite the previous example using fluent strings like so:

Figure 6.35 

```
1 <?php
2 
3 // Returns "Hello_world!"
4 str('Hello, world!')
5     ->substrReplace('_', 5, 2)
6     ->toString();
```

One thing that developers seem to become masters at throughout their careers is over-engineering automation solutions for highly trivial tasks. In the spirit of keeping this tradition alive, let’s assume that, for some reason, we have a lot of BASIC programs that look similar to the following:

Figure 6.36 

```
1 <?php
2 
3 $basicProgram = <<<PROGRAM
4 05 LET NUMBERONE = 10
5 10 LET NUMBERTWO = 20
6 15 LET RESULT = NUMBERONE + NUMBERTWO
7 20 PRINT RESULT
8 PROGRAM;
```

Now, we need a simple task to over-engineer an automated solution. Let’s say that we are required to perform the following actions across all of our BASIC programs:

*   Replace all instances of the number “10” with the number “30.”
*   Replace all occurrences of the number “20” with the number “50”.
*   Do not replace these numbers in line number labels.

Why these particular requirements? Sometimes it is much easier not to question things. To perform these actions, we could reach for our typical string replacement methods, but the line numbers at the beginning of each line in our BASIC programs will pose a problem since we do not want to replace any numbers inside those.

To help overcome these challenges, we can perform several tasks to perform our replacement operation:

1.  Normalize our programs’ line endings to account for different line ending styles
2.  Split our program string into an array representing the individual lines of the program
3.  Iterate each line of the program and perform our replacement on the text of the line that would appear after the line number (we will assume that the line numbers will always be the first three characters)
4.  Recombine the lines of the program into a single string

We can make use of several Laravel helper methods and PHP functions to create our implementation:

Figure 6.37 

```
 1 <?php
 2 
 3 // Normalize our input program's line endings.
 4 $normalized = preg_replace("/\r\n|\r|\n/", "\n", $basicProgram);
 5 
 6 // Convert our program into an array of individual lines.
 7 $lines = explode("\n", $normalized);
 8 
 9 collect($lines)->map(function ($line) {
10     return str($line)
11       // Use the substrReplace method to
12       // replace all content after the
13       // third character in the line.
14       ->substrReplace(
15           // Get all content after the third characters
16           // and replace the numbers within the line.
17           str($line)->substr(3)
18 	  		->replace(['10', '20'], ['30', '50']),
19           // Perform the replacement after the line number.
20           3
21         );
22 })->join("\n");
```

Which produces the following result:

Figure 6.38 

```
1 05 LET NUMBERONE = 30
2 10 LET NUMBERTWO = 50
3 15 LET RESULT = NUMBERONE + NUMBERTWO
4 20 PRINT RESULT
```

## 7\. Padding Strings

Padding strings is a common technique and is often used to help format the display or alignment of information visually. An everyday use case for string padding is adding trailing or leading zeroes to numbers, but that is not all that we can do with string padding.

Laravel provides several string padding helper method:

*   **padLeft**: Adds padding characters to the beginning, or left side, of a string
*   **padRight**: Adds padding characters to the end, or left side, of a string
*   **padBoth**: Attempts to add an equal number of padding characters to both sides of a string, up to the provided length limit

### 7.1 Padding the Beginning of Strings

Figure 7.1 padLeft Method Signature 

```
 1 <?php 
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function padLeft(
 9     string $value,
10        int $length,
11     string $pad = ' '
12 );
```

We can use the `padLeft` helper method to pad the start of a string to a certain number of characters, with a given padding character. The following example demonstrates a simple use of the `padLeft` helper, and is often used to add leading zeroes to invoice numbers (or similar):

Figure 7.2 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "00001"
6 Str::padLeft(1, 5, '0');
```

One thing to note is that the padding helper methods will not truncate, or limit, the length of a string if it exceeds the specified number of characters:

Figure 7.3 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "123456"
6 Str::padLeft(123456, 5, '0');
```

We can use the conditional features of fluent strings to elegantly limit the length of a string or add padding to it, depending on the length:

Figure 7.4 

```
1 <?php
2 
3 function printInvoiceNumber($number) {
4     return str($number)->when(
5         fn($s) => $s->length() > 5,
6         fn($s) => $s->substr(-4)->prepend('x'),
7         fn($s) => $s->padLeft(5, '0')
8     )->toString();
9 }
```

In the previous function implementation, we are using the when method on the fluent instance. We are supplying three callback functions to this method:

*   The first callback function contains our conditional logic, and should return a boolean value.
*   The second callback function contains the logic that should be executed if our conditional logic returns true. In this cause, if the length is more than five characters, we return the last four characters of the string and add “x” to the beginning of the new string.
*   The third callback function is invoked when the conditional callback returns false. For our example, will pad the input string to five characters with leading zeroes.

We can call our new function with different input and observe its behavior:

Figure 7.5 

```
1 <?php
2 
3 // Returns "x5467"
4 printInvoiceNumber(12345467);
5 
6 // Returns "00003"
7 printInvoiceNumber(3);
```

### 7.2 Padding the End of Strings

Figure 7.6 padRight Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function padRight(
 9     string $value,
10        int $length,
11     string $pad = ' '
12 );
```

We can use the `padRight` helper method to add padding characters to the end of a string, up to a specific length. This method is beneficial in ensuring a value takes up a fixed amount of space. For example, the following example will ensure that the input strings always take up at least fifteen characters:

Figure 7.7 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "Desk           "
 6 Str::padRight('Desk', 15);
 7 
 8 // Returns "Lamp           "
 9 Str::padRight('Lamp', 15);
10 
11 // Returns "Office Printer "
12 Str::padRight('Office Printer', 15);
```

One use case that many new developers may attempt to use the `padRight` method is to add trailing zeroes to numbers, as well as attempt to pad the left side of the number with leading zeroes. Attempting to use the `padRight` method to add trailing zeroes can often lead to complicated logic to account for numbers that do not have any values after the decimal point, ensuring the string ends up with the correct number of digits, etc.

As an example, let us say we wanted to write a function that would format the number “3.9” to “003.90” such that:

*   We round the resulting to two decimal places, and add trailing zeroes if necessary
*   There are always at least five digits, with leading zeroes to pad the start of the string

We could implement this function using the padLeft and `padRight` helper methods, but as you can see, the complexity of this implementation is not insignificant:

Figure 7.8 

```
 1 <?php
 2 
 3 function padNumber($float, $length) {
 4     // The default suffix to use.
 5     $suffix = '00';
 6 
 7     if (Str::contains($float, '.')) {
 8         // Gets all the digits after the decimal
 9         // point, and creates a new number.
10         $end = '0.'.Str::afterLast($float, '.');
11         // Round the new number to two decimal places.
12         $end = round($end, 2);
13         // Get all of the digits after the decimal place.
14         $end = Str::afterLast($end, '.');
15         // Pad our digits with trailing zeroes.
16         $suffix = Str::padRight($end, 2, '0');
17     }
18 
19       // Retrieves all numbers before the decimal point
20       // and append our new suffix that contains the
21       // trailing zeroes after we rounded the number.
22       $number = Str::beforeLast($float, '.').'.'.$suffix;
23 
24       return Str::padLeft(
25         $number,
26         $length + 1, '0'
27       );
28 }
```

Calling our function like so does produce the intended result, however:

Figure 7.9 

```
1 <?php
2 
3 // Returns "003.90"
4 padNumber(3.9, 5);
```

So now we may ask: how can we refactor this to be less complex? The great thing about the Laravel framework and its helper methods is that we are still working with PHP at the end of the day,. We can use PHP’s `number_format` function to dramatically simplify our function’s implementation.

The following code example reimplements our function to produce the same output with dramatically fewer moving pieces. We are supplying an empty string as the fourth argument to the `number_format` function to disable the thousands separator effectively.

Figure 7.10 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function padNumber($float, $length) {
 6     return Str::padLeft(
 7         number_format($float, 2, '.', ''),
 8         // We are adding one to account
 9 	    // for the decimal separator.
10         $length + 1, '0'
11     );
12 }
13 
14 // Returns "003.90"
15 padNumber(3.9, 5);
```

### 7.3 Padding Both Sides of a String

Figure 7.11 padBoth Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function padBoth(
 9     string $value,
10        int $length,
11     string $pad = ' '
12 );
```

In this section, we will look at the `padBoth` helper method, which adds a padding character to both ends of a string up to a certain length. The following examples demonstrate the basic usage of the `padBoth` helper method:

Figure 7.12 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "     Hello     "
6 Str::padBoth('Hello', 15);
7 
8 // Returns "*****World*****"
9 Str::padBoth('World', 15, '*');
```

We can use the `padBoth` helper method to produce some exciting results. For our first example, we will create a function that we can use to help print headers like the following:

Figure 7.13 

```
1 ################################
2 #######  A Fancy Title  ########
3 ################################
```

Looking at our sample output, the behavior of our function will be relatively simple:

*   Add lines with our delimiter character to the start and end of our header.
*   Center our header title on the second line, surrounded by our delimiter character.

We will implement our function using Laravel’s fluent string class. You may have noticed that we are using standard string concatenation to add two spaces to the start and end of our trimmed title. We could have done this using the prepend and append helper methods or the `padBoth` helper method. However, simply concatenating in this scenario is a lot easier to understand while glancing through the sample code:

Figure 7.14 

```
 1 <?php
 2 
 3 
 4 function printHeader($title) {
 5     $divider = str('#')->repeat(32);
 6 
 7     return str($divider)->newLine()
 8         ->append(
 9           str('  ' . str($title)->trim() . '  ')->padBoth(32, '#')
10         )->newLine()->append($divider)
11         ->toString();
12 }
```

We can now call our function to generate blocked centered headers:

Figure 7.15 

```
1 <?phpf
2 
3 printHeader('Hello, world!');
```

Which returns the following result:

Figure 7.16 

```
1 ################################
2 #######  Hello, world!  ########
3 ################################
```

## 8\. String Translations; Singular and Plural Word Forms

In this chapter, we will look at the various methods and functions provided by Laravel that assist in string translation. We will not focus on where these string translation files are stored or how the framework loads them but on how to use them, their nuances, and the syntaxes supported by these methods.

The translation helper functions differ from those we’ve seen so far in that they are not present on the `Illuminate\Support\Str` class but are globally defined and ultimately call methods on an `Illuminate\Translation\Translator` instance. **Table 8.1** lists the available global translation helper functions:

Table 8.1 Translation Helper Functions

 
| Function || Description |
| --- | --- |
| trans || Translates the provided string. |
| --- | --- |
| \_\_ (double underscore) || Translates the provided string. Alias of trans. |
| trans\_choice || Translates the provided string, based on a count. |

We can use the `trans` and `__` helper functions to translate simple messages with an optional array of variable replacements or within a specific locale. Both of these functions share the same function signature in **Figure 8.1**.

Figure 8.1 trans and \_\_ Function Signature 

```
 1 <?php
 2 
 3 use Illuminate\Translation\Translator;
 4 
 5 /**
 6  * Versions: Laravel 8, 9
 7  *
 8  * @return Translator|string|array|null
 9  */
10 function trans(
11   string|null $key = null,
12         array $replace = [],
13   string|null $locale = null
14 );
```

If we do not pass any arguments or pass a null value for the key, the `trans` and `__` functions will return an instance of `Illuminate\Translation\Translator`. The `trans_choice` helper function is similar but accepts a count of items that it will use to help select the translation string to use:

Figure 8.2 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 function trans_choice(
 9              string|null $key = null,
10     \Countable|int|array $number,
11                    array $replace = [],
12              string|null $locale = null
13 );
```

The rest of this chapter will assume we have the following translation file:

Figure 8.3 /lang/en/plural.php 

```
 1 <?php
 2 
 3 return [
 4 
 5     'welcome' => 'Hello, :name',
 6     'welcome_upper' => 'Hello, :NAME',
 7     'welcome_ucfirst' => 'Hello, :Name',
 8 
 9     'ranges' =>
10          '{0}No items
11          |[1,3]Between one and three
12          |[4,6]Between four and six
13          |[7,*]Seven and beyond!',
14 
15 ];
```

### 8.1 Working with Variable Replacements

In **Figure 8.3**, we defined the following translation keys, each of which can accept a variable “name”:

*   welcome
*   welcome\_upper
*   welcome\_ucfirst

If we were to call the trans method on our welcome key without supplying any replacement variables, we would get the entire translation message as the return value:

Figure 8.4 

```
1 <?php
2 
3 // Returns "Hello, :name"
4 trans('plural.welcome');
5 
6 // Returns "Hello, :name"
7 trans('plural.welcome', []);
```

However, we can supply an array of replacement values that Laravel will use when producing the final string:

Figure 8.5 

```
1 <?php
2 
3 // Returns "Hello, world"
4 trans('plural.welcome', [
5     'name' => 'world'
6 ]);
```

The `welcome_upper`* *and `welcome_ucfirst `translation keys are particularly interesting. We used “:NAME” and “:Name” in the translation message instead of the typical lowercase variable placeholder.

When we do this, Laravel will apply the same casing to our variable when it makes the replacement:

Figure 8.6 

```
 1 <?php
 2 
 3 // Returns "Hello, woRlD"
 4 trans('plural.welcome', [
 5     'name' => 'woRlD'
 6 ]);
 7 
 8 // Returns "Hello, WORLD"
 9 trans('plural.welcome_upper', [
10     'name' => 'woRlD'
11 ]);
12 
13 // Returns "Hello, WoRlD"
14 trans('plural.welcome_ucfirst', [
15     'name' => 'woRlD'
16 ]);
```

### 8.2 Managing Ranges of Items

Working with a collection of items is the more exciting part of Laravel’s translation system. We can define translation messages that will dynamically change depending on the number of items in a collection. We do this by separating each section of our translation message with the pipe character (“|”).

For example, in **Figure 8.3** we defined the “ranges” translation key, which contains the following individual translation messages:

Figure 8.7 

```
1 {0}No items
2 [1,3]Between one and three
3 [4,6]Between four and six
4 [7,*]Seven and beyond!
```

The first translation message begins with the sequence `{0}`, which indicates that the following message should be used when our collection contains no items (it has a count of zero):

Figure 8.8 

```
 1 <?php
 2 
 3 // Returns "No items"
 4 trans_choice('plural.ranges', collect());
 5 
 6 // Returns "No items"
 7 trans_choice('plural.ranges', []);
 8 
 9 // Returns "No items"
10 trans_choice('plural.ranges', 0);
```

The subsequent translation messages use a similar sequence of numbers in square brackets. These sequences allow us to define *ranges* of item counts that the translator will use to select the right message.

The following example will use PHP’s `range` function to generate an array of data with the desired amount of items:

Figure 8.9 

```
 1 <?php
 2 
 3 // Returns "Between one and three"
 4 trans_choice('plural.ranges', range(1, 3));
 5 
 6 // Returns "Between four and six"
 7 trans_choice('plural.ranges', range(1, 6));
 8 
 9 // Returns "Seven and beyond!"
10 trans_choice('plural.ranges', range(1, 42));
```

We used the sequence `[7,*]` for the last translation message, which indicates to the Laravel translator that the message should be applied starting at seven items, up to *any* number of items. If we want to use a specific translation message for a particular set of numbers, we could do that by supplying a comma-separated list of values between curly brackets:

Figure 8.10 

```
1 {0}Matches zero items.
2 |{1,2,3} Matches one, two or three items.
```

Similarly, we can also match *negative* ranges. As an example, the pattern in **Figure 8.11** provides several ranges that match: specific sets of integers, a range that includes positive infinity, as well as a range that contains negative infinity:

Figure 8.11 

```
1 {0}Matches zero items.
2 |{1,2,3} Matches one, two or three items.
3 |{4} Matches exactly four items.
4 |[5-10] Matches between five and ten items.
5 |[11,*] Matches eleven or more items.
6 |[*,-1] Matches all negative counts.
```

### 8.3 Singular and Plural Word Forms

In addition to the string translation helper methods and supporting features, Laravel provides simple ways to convert words to their singular or plural forms^([5](#chap29.xhtml#fn-doctrine)). By default, this feature works for English words, but we can enable it for Norwegian Bokmål, French, Portuguese, Spanish, and Turkish^([6](#chap29.xhtml#fn-pluralizerdocs)).

The three methods we use to interact with the pluralization features are `plural`, `pluralStudly`, and `singular`. We will start our discussion with the `singular` helper method.

Figure 8.12 singular Method Signature 

```
1 <?php
2 
3 /**
4  * Versions: Laravel 8, 9
5  *
6  * @return string
7  */
8 public static function singular(string $value);
```

**Figure 8.13** demonstrates the usage of the `singular` helper method. An interesting thing to note is that Doctrine’s word inflection implementation can handle edge cases, such as the English word “moose.”

Figure 8.13 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "moose"
6 Str::singular('moose');
7 
8 // Returns "mouse"
9 (string) str('mice')->singular;
```

We can also use the `singular` method to convert a studly-cased word into its singular form. The following code example will break the word “theMice” into “the” and “Mice,” convert “Mice” to its singular form, and then combine them into the final result:

Figure 8.14 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "theMouse"
6 Str::singular('theMice');
```

The `plural` and `pluralStudly` methods are similar to the singular method but accept a count of items we can use to influence the final word form. We can also supply a count of one to effectively return the singular word form, removing the need to have an explicit check for this case.

Figure 8.15 plural and pluralStudly Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function plural(
 9                   string $value,
10     int|array|\Countable $count = 2
11 );
12 
13 /**
14  * Versions: Laravel 8, 9
15  *
16  * @return string
17  */
18 public static function pluralStudly(
19                   string $value,
20     int|array|\Countable $count = 2
21 );
```

**Figure 8.16** provides examples of how we can utilize the `plural` method:

Figure 8.16 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "mice"
 6 Str::plural('mouse', 0);
 7 
 8 // Returns "mouse"
 9 Str::plural('mouse', collect(1));
10 
11 // Returns "mouse"
12 Str::plural('mouse', 1);
13 
14 // Returns "mice"
15 (string) str('mouse')->plural;
```

Like when we converted a studly-cased word into its singular form, we can use the `pluralStudly` method to convert a singular studly-cased word to its plural form:

Figure 8.17 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // Returns "theMices"
 6 Str::pluralStudly('theMice', 0);
 7 
 8 // Returns "theMice"
 9 Str::pluralStudly('theMice', 1);
10 
11 // Returns "theMices"
12 (string) str('theMice')->pluralStudly(0);
13 
14 // Returns "theMiceMices"
15 Str::pluralStudly('theMiceMice', 3);
```

In **Figure 8.17** we can see some interesting behavior when pluralizing the word “Mice,” which is already in its plural form. The inflection system returns “Mice,” which most would not be considered correct. If the application is sensitive, it may be beneficial to review the output of the inflector periodically; however, for use with internal naming, as long as the results are consistent, it should not prove to be an issue.

## 9\. Extending Strings with Macros and Mixins

Laravel provides two primary ways to add additional capabilities to the `Str` helper class and fluent strings: mixins and macros. Macros allow us to add new helper methods, and mixins will enable us to inject the methods of a different class into either the `Str` helper class or fluent strings. We will be making great use of them throughout the rest of this book as we work to expand our knowledge of string management. Developers from languages such as C# can equate these features to the extension methods those languages provide.

For example, **Figure 9.1** defines a C# extension method that would make the `SplitLines` method available on strings:

Figure 9.1 

```
 1 namespace ExtensionExample
 2 {
 3     public static class StringExtension
 4     {
 5         public static int SplitLines(this String str)
 6         {
 7             // Implementation of SplitLines in C#
 8             // return word count here.
 9         }
10     }
11 }
```

We can accomplish a similar thing using the macros feature. As an example, the following example would add a new `lineSplit` method to the Laravel `Str` class to split an input string on newline characters:

Figure 9.2 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::macro('lineSplit', function ($value) {
6     return explode("\n", $value);
7 });
```

We can now use our new method like so:

Figure 9.3 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $result = Str::lineSplit(<<<EOT
6   “ Simplicity is an acquired taste. ”
7   — Katharine Gerould
8 EOT);
```

Which would produce the following output:

Figure 9.4 

```
1 [
2   "  “ Simplicity is an acquired taste. ”",
3   "  — Katharine Gerould",
4 ]
```

Similarly, we can add new methods to fluent strings in a similar manner, with the difference being that when we add macros to fluent strings, we are within the context of a fluent object instance and can retrieve the string value through the “value” member:

Figure 9.5 

```
1 <?php
2 
3 use Illuminate\Support\Stringable;
4 
5 Stringable::macro('lineSplit', function () {
6     return $this->explode("\n");
7 });
```

We can now also call the `lineSplit` method on fluent string instances:

Figure 9.6 

```
1 <?php
2 
3 str(<<<EOT
4   “ Simplicity is an acquired taste. ”
5   — Katharine Gerould
6 EOT)->lineSplit;
```

When we extend fluent strings, our callback function will be within the context of a fluent object instance, which allows us to call other methods on the fluent instance. Additionally, we returned a call to the fluent string’s explode method, which returns a Collection instance instead of an array to remain consistent with the return types of other fluent string methods.

If we have a lot of helper methods we would like to extend Laravel with we can use mixins to help keep our code base clean and organized. When we use mixins, we create a class containing public methods that return functions:

Figure 9.7 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class StringHelperMethods {
 6     public function splitLine() {
 7         return function ($value) {
 8             return explode("\n", $value);
 9         };
10     }
11 }
12 
13 Str::mixin(new StringHelperMethods());
14 
15 // Using or mixin method:
16 Str::splitLine($stringInput);
```

The public method’s name will become the method name of the method injected into the Laravel `Str` class; in **Figure 9.7** the method name is `splitLine`. Our mixin method returns a function that will be invoked by the Str class when we call the `splitLine` method. We can also add mixins to fluent string classes:

Figure 9.8 

```
 1 <?php
 2 
 3 use Illuminate\Support\Stringable;
 4 
 5 class StringHelperMethods {
 6     public function splitLine() {
 7         return function () {
 8           return $this->explode("\n");
 9         };
10     }
11 }
12 
13 Stringable::mixin(new StringHelperMethods());
14 
15 str($stringInput)->splitLine;
```

In both **Figure 9.7** and **Figure 9.8** we pass in instances of our mixin class. If we attempted to pass only the class name, such as `StringHelperMethods::class`, we would receive a “TypeError: ReflectionMethod::invoke()” error.

## 10\. Lines and Words

Throughout this chapter, we will explore the concepts of lines and words. Both terms are ubiquitous: we see them everywhere but probably do not give them much thought. We will start with lines.

Back in Chapter 9 we put together a quick example macro that would break a corpus into an array of individual lines:

Figure 10.1 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::macro('lineSplit', function ($value) {
6     return explode("\n", $value);
7 });
```

When we did this in that chapter, we did note that this implementation had some issues. Namely, it does not handle the line ending types we often encounter. Our current line splitting implementation only accounts for the “\\n” (line feed) character, which will work well with text input or documents from UNIX or modern macOS systems. However, there are others.

For example, older macOS systems would use the “\\r” (carriage return), and Windows systems use the “\\r\\n” sequence (carriage return followed by a line feed). These characters are interesting in their own right. Most developers will have interacted with completely digital systems and may not know that each of these characters has historical use and significance.

Back in Chapter 1 we discussed ASCII, Unicode, and character encodings. One of the interesting things about character sets is that they are often subdivided into at least two groups: control characters and printable characters. The various newline characters fall into the former group of control characters. Control characters cause a physical system to do something: they *control it*. Let’s take a moment and think about a typewriter.

When we type characters on a typewriter, a hammer is flung through the air, hits an ink strip, and stamps the symbol on our page. Each time this happens, the carriage, the apparatus that advances the page as we type and moves it up and down, moves to the left slightly. If we do this enough, the carriage will eventually get as far to the left as it can and will not be able to advance any further; a satisfying bell ring often accompanies this. To start a new line, we hit the return key, which causes the wheel holding the paper to rotate slightly. The carriage returns to its original position, allowing us to start typing at the start of the new line.

Pressing the return key initiates two actions: the paper feeds through the roller, and the carriage *returns* to its starting position.

Now that we have a bit of context surrounding the different line ends we commonly see, we can ask ourselves another question: are there other characters we need to be aware of? There are, in fact, many different control characters that have historically been used that cause a new line to be inserted or indicate some vertical separation. **Table 10.1** provides a list of the possible newline character sequences we should be aware of:

Table 10.1 Possible Newline Characters

 
| Character Sequence || RegEx Pattern || Unicode Code Point |
| --- | --- | --- |
| Line Feed (LF) || /\\n/ || U+000A |
| --- | --- | --- |
| Carriage Return (CR) || /\\r/ || U+000D |
| CR+LF || /\\r\\n/ ||   |
| LF+CR || /\\n\\r/ ||   |
| Form Feed (FF) || /\\x{000C}/ || U+000C |
| Next Line (NEL) || /\\x{0085}/ || U+0085 |
| Line Separator (LS) || /\\x{2028}/ || U+2028 |
| Paragraph Separator (PS) || /\\x{2029}/ || U+2029 |
| Vertical Tab (VT) || /\\x{000B}/ || U+000B |

Each of the different characters in **Table 10.1** has its use. For example, the vertical tab character instructs a printer or display to advance a single line while preserving the horizontal spacing. For our purposes, however, we will only focus on the line feed and carriage return characters.

Using the regular expression patterns from **Table 10.1**, we can construct a pattern that we can use with PHP’s `preg_split` function. Our regular expression will accept either the carriage return followed by the line feed sequence *or* the line feed character *or* the carriage return character:

Figure 10.2 regex Pattern to Match Line Endings 

```
1 /(\r\n|\n|\r)/
```

We can now update the macro we created in the previous chapter:

Figure 10.3 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::macro('lineSplit', function ($value) {
6     return preg_split("/(\r\n|\n|\r)/u", $value);
7 });
```

After this change, our `lineSplit` method will now be able to handle the most common of the new line characters. We also have the opportunity to create another helper method: one to *normalize* the line endings that appear within a piece of text:

Figure 10.4 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::macro('normalizeEol', function ($value, $to = PHP_EOL) {
6     return preg_replace("/(\r\n|\n|\r)/u", $to, $value);
7 });
```

We can use our new `normalizeEol` method like so to convert line endings:

Figure 10.5 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $string = "line one\nline two\r\nline three\rline four";
6 
7 // Returns "line one\nline two\nline three\nline four"
8 Str::normalizeEol($string, "\n");
```

An interesting aspect of the `normalizeEol` signature is the default value of the `$to` parameter: `PHP_EOL`. The `PHP_EOL` constant will return the line ending style for the platform that PHP is running on; for example, it will be set to “\r\n” on a Windows system.

We can also update our `lineSplit` fluent string macro and add a `normalizeEol` method as well:

Figure 10.6 

```
 1 <?php
 2 
 3 use Illuminate\Support\Stringable;
 4 
 5 Stringable::macro('normalizeEol', function ($to = PHP_EOL) {
 6     return new static(
 7         preg_replace("/(\r\n|\n|\r)/u", $to, $this->value)
 8     );
 9 });
10 
11 Stringable::macro('lineSplit', function () {
12     return collect(preg_split("/(\r\n|\n|\r)/u", $this->value));
13 });
```

Using our new fluent `lineSplit` method like so:

Figure 10.7 

```
1 <?php
2 
3 str("line one\nline two\r\nline three\rline four")
4     ->lineSplit;
```

Would return a new Collection containing the following elements:

Figure 10.8 

```
1 [
2     "line one",
3     "line two",
4     "line three",
5     "line four",
6 ]
```

### 10.1 Positions, Lines, and Columns

Over the years, I have worked on many text-related projects that have involved working with lines, positions, and columns. For example, when we look at a cursor’s position with a text editor, we often see it displayed in lines and columns (e.g., Ln 7, Col 62). From our discussions in Chapter 1, we know that strings are represented in memory as a contiguous array of bytes. The question then becomes: how do we apply two-dimensional concepts on top of a unidimensional array of bytes?

Unpacking the following string value:

Figure 10.9 

```
1 <?php
2 
3 $text = "one\ntwo\nthree four\nfive";
4 
5 unpack('C*', $text);
```

Returns the following list of bytes in decimal form:

Figure 10.10 

```
 1 array:23 [
 2      1 => 111
 3      2 => 110
 4      3 => 101
 5      4 => 10
 6      5 => 116
 7      6 => 119
 8      7 => 111
 9      8 => 10
10      9 => 116
11     10 => 104
12     11 => 114
13     12 => 101
14     13 => 101
15     14 => 32
16     15 => 102
17     16 => 111
18     17 => 117
19     18 => 114
20     19 => 10
21     20 => 102
22     21 => 105
23     22 => 118
24     23 => 101
25 ]
```

Looking at the results in **Figure 10.10**, we can glean a few clues as to what we can do to convert arbitrary string positions into their line and column numbers. For instance, we know that the decimal value 10 corresponds to the newline character. To get the current line number from a position within the string, we can count the number of times this character has appeared before the current position. The following code example demonstrates a simple way we could convert any string position into a line number:

Figure 10.11 

```
 1 <?php
 2 
 3 $text = "one\ntwo\nthree four\nfive";
 4 
 5 function getLineNumber($value, $position) {
 6     return mb_substr_count(
 7         mb_substr($value, 0, $position),
 8         "\n"
 9     ) + 1;
10 }
11 
12 // Get line number of the first "o".
13 // Returns 1
14 getLineNumber($text, 0);
15 
16 // Get the line number of the first "t".
17 // Returns 2
18 getLineNumber($text, 4);
```

This initial implementation works by using the desired position and extracting a substring from the original string. We then count the number of newline characters that appear in the resulting string. The line count will be zero-based, so we add one to get a human-friendly line number. This technique works well on smaller strings but can become quite memory intensive, creating the substrings on huge strings. We will explore ways to address this later.

We can employ a similar strategy to determine the column number for any position in the string. The basic technique will be to get the position of the newline character that immediately precedes the desired position. Once we have both positions, the column number will be the difference between the two positions.

Figure 10.12 

```
 1 <?php
 2 
 3 $text = "one\ntwo\nthree four\nfive";
 4 
 5 function getColumnNumber($value, $position) {
 6     $lastNlPosition = mb_strrpos(
 7         mb_substr($value, 0, $position),
 8         "\n"
 9     );
10 
11 
12     if ($lastNlPosition === false) {
13         return $position + 1;
14     }
15 
16     return $position - $lastNlPosition;
17 }
18 
19 // Returns 1
20 getColumnNumber($text, 0);
21 
22 // Returns 3
23 getColumnNumber($text, 2);
24 
25 // Returns 1
26 getColumnNumber($text, 8);
27 
28 // Returns 8
29 getColumnNumber($text, 15);
```

Using the string iterator developed in Chapter 1, we can construct a loop to help better visualize the output of these two functions. The following code example:

Figure 10.13 

```
 1 <?php
 2 
 3 $text = "one\ntwo\nthree four\nfive";
 4 
 5 $string = new Utf8StringIterator($text);
 6 
 7 for ($i = 0; $i < count($string); $i++) {
 8     if ($string[$i] == "\n") { echo "\n"; continue; }
 9 
10     $line = getLineNumber($text, $i);
11     $col = getColumnNumber($text, $i);
12 
13     echo "Char: {$string[$i]} Ln: {$line} Col: {$col}\n";
14 }
```

Produces the following output:

Figure 10.14 

```
 1 Char: o Ln: 1 Col: 1
 2 Char: n Ln: 1 Col: 2
 3 Char: e Ln: 1 Col: 3
 4 
 5 Char: t Ln: 2 Col: 1
 6 Char: w Ln: 2 Col: 2
 7 Char: o Ln: 2 Col: 3
 8 
 9 Char: t Ln: 3 Col: 1
10 Char: h Ln: 3 Col: 2
11 Char: r Ln: 3 Col: 3
12 Char: e Ln: 3 Col: 4
13 Char: e Ln: 3 Col: 5
14 Char:   Ln: 3 Col: 6
15 Char: f Ln: 3 Col: 7
16 Char: o Ln: 3 Col: 8
17 Char: u Ln: 3 Col: 9
18 Char: r Ln: 3 Col: 10
19 
20 Char: f Ln: 4 Col: 1
21 Char: i Ln: 4 Col: 2
22 Char: v Ln: 4 Col: 3
23 Char: e Ln: 4 Col: 4
```

For one-off uses, we can package our two functions into a set of string helper methods:

Figure 10.15 Line and Column Number Helper Method Implementations 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('lineNumber', function ($value, $position) {
 7     return mb_substr_count(
 8             str($value)->substr(0, $position), "\n"
 9         ) + 1;
10 });
11 
12 Stringable::macro('lineNumber', function ($position) {
13     return Str::lineNumber($this->value, $position);
14 });
15 
16 Str::macro('columnNumber', function ($value, $position) {
17     $lastNlPosition = mb_strrpos(
18         str($value)->substr(0, $position), "\n"
19     );
20 
21 
22     if ($lastNlPosition === false) {
23         return $position + 1;
24     }
25 
26     return $position - $lastNlPosition;
27 });
28 
29 Stringable::macro('columnNumber', function ($position) {
30     return Str::columnNumber($this->value, $position);
31 });
```

We have alluded that these helper methods might not be an optimal solution if we need to retrieve lines and columns frequently; this is mainly due to the large number of substrings we would be creating if we did so. To improve our existing implementations, we can create an index of all line endings within the text, similar to how we indexed character offsets when implementing our UTF-8 string iterator in Chapter 1.

Our implementation will use the single “\\n” newline character. If the input text uses a different line ending style, we can use the normalizeEol helper method we have already developed. Using PHP’s `preg_match_all` function with the `PREG_OFFSET_CAPTURE` flag:

Figure 10.16 

```
1 <?php
2 
3 
4 $text = "one\ntwo\nthree four\nfive";
5 
6 preg_match_all("/\n/u", $text, $matches, PREG_OFFSET_CAPTURE);
```

Would produce the following array of matches, with the positions of the newline characters within the text for us:

Figure 10.17 

```
 1 array:1 [
 2     0 => array:3 [
 3       0 => array:2 [
 4         0 => "\n"
 5         1 => 3
 6       ]
 7       1 => array:2 [
 8         0 => "\n"
 9         1 => 7
10       ]
11       2 => array:2 [
12         0 => "\n"
13         1 => 18
14       ]
15     ]
16 ]
```

Our next task will be to convert the array of matches into a more straightforward array containing just the offsets of the newline characters. We can do this using Laravel Collections:

Figure 10.18 

```
1 <?php
2 
3 // ...
4 
5 $index = collect($matches[0])->map(function ($match) {
6     return $match[1];
7 })->all();
```

Which produces the following array:

Figure 10.19 

```
1 array:3 [
2     0 => 3
3     1 => 7
4     2 => 18
5 ]
```

Now, to get the line number from our index for any given position, we can iterate the index and compare the desired position to the positions within the index. Suppose the current position within the index is greater than the desired position. In that case, we know that the line number offset we are interested in was the previous offset within the index and can return the current value of the counter variable after adding one (to make our line numbers one-based):

Figure 10.20 

```
 1 <?php
 2 
 3 function getLineNumber($position, $index) {
 4     for ($i = 0; $i < count($index); $i++) {
 5         $offset = $index[$i];
 6 
 7         if ($i == 0 && $position < $offset) {
 8             return 1;
 9         }
10 
11         if ($offset > $position) {
12             return $i + 1;
13         }
14     }
15 
16     return $i + 1;
17 }
```

We will do something similar with our new `getColumnNumber` implementation. Compared with the line number function, the difference with this implementation is that we need to keep track of the value of the offsets. The loop’s counting variable was enough to get the information we needed when counting line numbers. However, for columns, we need to know the position of the line ending within the string so we can compute our difference:

Figure 10.21 

```
 1 <?php
 2 
 3 function getColumnNumber($position, $index) {    
 4     $lastOffset = null;
 5 
 6     for ($i = 0; $i < count($index); $i++) {
 7         $offset = $index[$i];
 8 
 9         if ($i == 0 && $position < $offset) {
10             return $position + 1;
11         }
12 
13         if ($offset > $position) {
14             return $position - $lastOffset;
15         }
16 
17         $lastOffset = $offset;
18     }
19 
20     return $position - $lastOffset;
21 }
```

Our two functions are pretty helpful, but it would become tedious if we manually initialize the index and pass it around whenever we wanted to use it. To get around this, we can create a new utility class to help out. Because naming things is incredibly difficult, we will call it `CharacterPositionLocator`:

Figure 10.22 

```
 1 <?php
 2 
 3 class CharacterPositionLocator
 4 {
 5     protected $string = '';
 6     protected $newLineIndex = [];
 7 
 8     public function __construct(string $string)
 9     {
10         $this->string = $string;
11         $this->buildNewLineIndex();
12     }
13 
14     protected function buildNewLineIndex()
15     {
16         preg_match_all(
17           "/\n/u",
18           $this->string,
19           $matches,
20           PREG_OFFSET_CAPTURE
21         );
22 
23         $this->newLineIndex = collect($matches[0])
24           ->map(function ($match) {
25             return $match[1];
26         })->all();
27     }
28 
29     public function getLineNumber($position)
30     {
31         for ($i = 0; $i < count($this->newLineIndex); $i++) {
32             $offset = $this->newLineIndex[$i];
33 
34             if ($i == 0 && $position < $offset) {
35                 return 1;
36             }
37 
38             if ($offset > $position) {
39                 return $i + 1;
40             }
41         }
42 
43         return $i + 1;
44     }
45 
46     public function getColumnNumber($position)
47     {
48         $lastOffset = null;
49 
50         for ($i = 0; $i < count($this->newLineIndex); $i++) {
51             $offset = $this->newLineIndex[$i];
52 
53             if ($i == 0 && $position < $offset) {
54                 return $position + 1;
55             }
56 
57             if ($offset > $position) {
58                 return $position - $lastOffset;
59             }
60 
61             $lastOffset = $offset;
62         }
63 
64         return $position - $lastOffset;
65     }
66 }
```

We now have a utility class capable of retrieving line and column numbers from arbitrary positions, but we have another opportunity for refactoring. We will likely want the column number when we want to retrieve a line number, and we can retrieve both pieces of information by slightly modifying the details of our `getColumnNumber` method. While doing these refactors, we can take the time to protect against supplying a negative position or one that exceeds the length of the string:

Figure 10.23 

```
 1 <?php
 2 
 3 class Position
 4 {
 5     public $position = null;
 6     public $column = null;
 7     public $line = null;
 8 }
 9 
10 class CharacterPositionLocator
11 {
12     protected $string = '';
13     protected $length = 0;
14     protected $newLineIndex = [];
15 
16     public function __construct(string $string)
17     {
18         $this->string = $string;
19         $this->length = mb_strlen($string, 'UTF-8');
20         $this->buildNewLineIndex();
21     }
22 
23     protected function buildNewLineIndex()
24     {
25         preg_match_all(
26           "/\n/u",
27           $this->string,
28           $matches,
29           PREG_OFFSET_CAPTURE
30         );
31 
32         $this->newLineIndex = collect($matches[0])
33           ->map(function ($match) {
34             return $match[1];
35         })->all();
36     }
37 
38     public function getLineNumber($position)
39     {
40         return $this->getCharPosition($position)?->line;
41     }
42 
43     public function getColumnNumber($position)
44     {
45         return $this->getCharPosition($position)?->column;
46     }
47 
48     public function getCharPosition($position)
49     {
50         if ($position > $this->length || $position < 0) {
51             return null;
52         }
53 
54         $lastOffset = null;
55         $column = null;
56         $line = null;
57 
58         for ($i = 0; $i < count($this->newLineIndex); $i++) {
59             $offset = $this->newLineIndex[$i];
60 
61             if ($i == 0 && $position < $offset) {
62                 $line = 1;
63                 $column = $position + 1;
64                 break;
65             }
66 
67             if ($offset > $position) {
68                 $line = $i + 1;
69                 $column = $position - $lastOffset;
70                 break;
71             }
72 
73             $lastOffset = $offset;
74         }
75 
76         if ($column === null) {
77             $line = $i + 1;
78             $column = $position - $lastOffset;
79         }
80 
81         $charPosition = new Position();
82         $charPosition->position = $position;
83         $charPosition->column = $column;
84         $charPosition->line = $line;
85 
86         return $charPosition;
87     }
88 }
```

As part of our refactors, we defined a new `Position` class that will hold our desired line number and column number; it also stores our original position. To not break compatibility with our existing `getLineNumber` and `getColumnNumber` methods, and reduce the amount of duplicate code, we now internally make a call to our new method and return the appropriate member. We can reproduce the output of **Figure 10.14** using our new class like so:

Figure 10.24 

```
 1 <?php
 2 
 3 $text = "one\ntwo\nthree four\nfive";
 4 
 5 $string = new Utf8StringIterator($text);
 6 $locator = new CharacterPositionLocator($text);
 7 
 8 for ($i = 0; $i < count($string); $i++) {
 9     if ($string[$i] == "\n") { echo "\n"; continue; }
10 
11     $pos = $locator->getCharPosition($i);
12 
13     echo "Char: {$string[$i]} Ln: {$pos->line} Col: {$pos->column}\n";
14 }
```

The next obvious question we may ask is can we do this reversed? Can we supply a line number and column and return the position within the string that corresponds to that location? So far, our implementation has assumed that the newline character present in the text will always be the “\\n” sequence, but it could be any of the newline styles we are interested in supporting. Perhaps we may even see input text like the following, maybe as a result of poorly appended documents through some automated process:

Figure 10.25 

```
1 <?php
2 
3 $text = "one\r\ntwo\nthree\r\nfour\nfive";
```

We can support this by changing our indexing regex to account for multiple newline styles. One side effect of many newline styles is that we will also need to store how many characters are part of the newline sequence. If we do not, we would not be able to easily account for position parameters that are inside a newline sequence. Additionally, suppose we will account for the possibility of many types of newline sequences in a piece of text. In that case, we can also add a way to check if any given position belongs to a newline sequence. We will implement these changes before tackling retrieving positions from the known line and column numbers:

Figure 10.26 

```
  1 <?php
  2 
  3 class Position
  4 {
  5     public $position = null;
  6     public $column = null;
  7     public $line = null;
  8 }
  9 
 10 class CharacterPositionLocator
 11 {
 12     protected $string = '';
 13     protected $length = 0;
 14     protected $newLineIndex = [];
 15 
 16     public function __construct(string $string)
 17     {
 18         $this->string = $string;
 19         $this->length = mb_strlen($string, 'UTF-8')
 20         $this->buildNewLineIndex();
 21     }
 22 
 23     protected function buildNewLineIndex()
 24     {
 25         preg_match_all(
 26           "/\n/u",
 27           "/\r\n|\n|\r/u"
 28           $this->string,
 29           $matches,
 30           PREG_OFFSET_CAPTURE
 31         );
 32 
 33         $this->newLineIndex = collect($matches[0])
 34           ->map(function ($match) {
 35             return $match[1];
 36             // Return an array containing the start
 37             // and end position of the sequence.
 38             return [$match[1], $match[1] + strlen($match[0]) - 1];
 39         })->all();
 40     }
 41 
 42     public function getLineNumber($position)
 43     {
 44         return $this->getCharPosition($position)?->line;
 45     }
 46 
 47     public function getColumnNumber($position)
 48     {
 49         return $this->getCharPosition($position)?->column;
 50     }
 51 
 52     public function isNewLine($position): bool
 53     {
 54         if ($position > $this->length || $position < 0) {
 55             return false;
 56         }
 57 
 58         for ($i = 0; $i < count($this->newLineIndex); $i++) {
 59             $nlStart = $this->newLineIndex[$i][0];
 60             $nlEnd = $this->newLineIndex[$i][1];
 61 
 62             if ($position >= $nlStart && $position <= $nlEnd) {
 63                 return true;
 64             }
 65         }
 66 
 67         return false;
 68     }
 69 
 70     public function getCharPosition($position)
 71     {
 72         if ($position > $this->length || $position < 0) {
 73             return null;
 74         }
 75 
 76         $lastOffset = null;
 77         $column = null;
 78         $line = null;
 79 
 80         for ($i = 0; $i < count($this->newLineIndex); $i++) {
 81             $offset = $this->newLineIndex[$i];
 82             $offset = $this->newLineIndex[$i][1];
 83 
 84             if ($i == 0 && $position < $offset) {
 85                 $line = 1;
 86                 $column = $position + 1;
 87                 break;
 88             }
 89 
 90             if ($offset > $position) {
 91                 $line = $i + 1;
 92                 $column = $position - $lastOffset;
 93                 break;
 94             }
 95 
 96             $lastOffset = $offset;
 97         }
 98 
 99         if ($column === null) {
100             $line = $i + 1;
101             $column = $position - $lastOffset;
102         }
103 
104         $charPosition = new Position();
105         $charPosition->position = $position;
106         $charPosition->column = $column;
107         $charPosition->line = $line;
108 
109         return $charPosition;
110     }
111 }
```

We can utilize familiar techniques to implement our method to retrieve a character position for a line and column number. We will iterate each element of our newline character index and check whether or not the line matches the desired line. If it does, we will add the column number to the end position of the previous newline:

Figure 10.27 

```
 1 <?php
 2 
 3 class CharacterPositionLocator
 4 {
 5     // ...
 6 
 7     public function getCharPositionFromLineColumn($line, $column)
 8     {
 9         $position = null;
10         for ($i = 0; $i < count($this->newLineIndex); $i++) {
11             if ($i + 1 != $line) {
12                 continue;
13             }
14 
15             if ($i == 0) {
16                 return $column - 1;
17             }
18 
19             $index = $this->newLineIndex[$i - 1];
20 
21             $position = $index[1] + $column;
22         }
23 
24         if ($position === null) {
25             $lastIndex =
26               $this->newLineIndex[count($this->newLineIndex) - 1];
27 
28             $position = $lastIndex[1] + $column;
29         }
30 
31         return $position;
32     }
33   
34     // ...
35 }
```

We can now use our new method to retrieve the position of the character that appears in line 5, column 3:

Figure 10.28 

```
1 <?php
2 
3 $text = "one\r\ntwo\nthree\r\nfour\nfive";
4 
5 $locator = new CharacterPositionLocator($text);
6 
7 // Returns 23
8 $locator->getCharPositionFromLineColumn(5, 3);
```

Now, this implementation works fine if the line and column numbers provided match a character within the boundaries of the line but can produce interesting results if we attempt to retrieve a character that does not. We will address this next.

The scenarios we will want to cover include

*   handling negative line and column numbers,
*   resolving positions that exceed the string’s length, and
*   column numbers that exceed the total number of characters for the requested line.

Figure 10.29 

```
 1 <?php
 2 
 3 class CharacterPositionLocator
 4 {
 5     // ...
 6 
 7     public function getCharPositionFromLineColumn($line, $column)
 8     {
 9         if ($line < 1 || $column < 1) {
10             return null;
11         }
12 
13         $position = null;
14         for ($i = 0; $i < count($this->newLineIndex); $i++) {
15             if ($i + 1 != $line) {
16                 continue;
17             }
18 
19             if ($i == 0) {
20                 return $column - 1;
21                 $position = $column - 1;
22                 break;
23             }
24 
25             $index = $this->newLineIndex[$i - 1];
26 
27             $position = $index[1] + $column;
28 
29             // Ensure the position is inside the current line.
30             $nextLineStart = $this->newLineIndex[$i];
31 
32             if ($position >= $nextLineStart[0]) {
33                 return null;
34             }
35 
36             break;
37         }
38 
39         if ($position === null) {
40             $lastIndex =
41               $this->newLineIndex[count($this->newLineIndex) - 1];
42 
43             $position = $lastIndex[1] + $column;
44         }
45 
46         if ($position >= $this->length || $position < 0) {
47             return null;
48         }
49 
50         return $position;
51     }
52   
53     // ...
54 }
```

We can update our sample code from **Figure 10.13** to include our refactored `getCharPositionFromLineColumn` method and print the results along with our previous output:

Figure 10.30 

```
 1 <?php
 2 
 3 $text = "one\r\ntwo\nthree\r\nfour\nfive";
 4 
 5 $string = new Utf8StringIterator($text);
 6 $locator = new CharacterPositionLocator($text);
 7 
 8 for ($i = 0; $i < count($string); $i++) {
 9     if ($locator->isNewLine($i)) { continue; }
10 
11     $pos     = $locator->getCharPosition($i);
12     $charPos = $locator->getCharPositionFromLineColumn(
13         $pos->line,
14         $pos->column
15     );
16 
17     $printI       = str($i)->padLeft(2);
18     $printCharPos = str($charPos)->padLeft(2);
19     
20     echo "Pos: {$printI} - {$printCharPos} ",
21          "Char: {$string[$i]} Ln: {$pos->line} Col: {$pos->column}\n";
22 }
```

This results in:

Figure 10.31 

```
 1 Pos:  0 -  0 Char: o Ln: 1 Col: 1
 2 Pos:  1 -  1 Char: n Ln: 1 Col: 2
 3 Pos:  2 -  2 Char: e Ln: 1 Col: 3
 4 Pos:  5 -  5 Char: t Ln: 2 Col: 1
 5 Pos:  6 -  6 Char: w Ln: 2 Col: 2
 6 Pos:  7 -  7 Char: o Ln: 2 Col: 3
 7 Pos:  9 -  9 Char: t Ln: 3 Col: 1
 8 Pos: 10 - 10 Char: h Ln: 3 Col: 2
 9 Pos: 11 - 11 Char: r Ln: 3 Col: 3
10 Pos: 12 - 12 Char: e Ln: 3 Col: 4
11 Pos: 13 - 13 Char: e Ln: 3 Col: 5
12 Pos: 16 - 16 Char: f Ln: 4 Col: 1
13 Pos: 17 - 17 Char: o Ln: 4 Col: 2
14 Pos: 18 - 18 Char: u Ln: 4 Col: 3
15 Pos: 19 - 19 Char: r Ln: 4 Col: 4
16 Pos: 21 - 21 Char: f Ln: 5 Col: 1
17 Pos: 22 - 22 Char: i Ln: 5 Col: 2
18 Pos: 23 - 23 Char: v Ln: 5 Col: 3
19 Pos: 24 - 24 Char: e Ln: 5 Col: 4
```

### 10.2 Splitting Strings into Words

We can now split arbitrary strings into an array of lines, bringing us to our next logical step: breaking strings into lists of words. A word’s concept and exact definition can easily lead us astray and into a separate discussion. With this in mind, we will say a space, or other arbitrary characters we define (we will cover this later), separates a word. The first method we will create will be an adaptation of Laravel’s `words` method. This approach will produce a list of strings that matches what the `words` helper method is operating on internally.

To do this, we can use the following regular expression, which will match any number of whitespace characters and split our string into an array of words:

Figure 10.32 

```
1 /\s+/u
```

The regular expression in **Figure 10.32** will match any number of whitespace characters. We can now use this with `preg_split` to break our string into an array of words:

Figure 10.33 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordSplit', function ($value) {
 7     return preg_split("/\s+/u", $value);
 8 });
 9 
10 Stringable::macro('wordSplit', function () {
11     return collect(preg_split("/\s+/u", $this->value));
12 });
```

Calling our new `wordSplit` method on the `Str` class like so:

Figure 10.34 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::wordSplit("A simple string made up of words.");
```

Would return the following result:

Figure 10.35 

```
1 [
2     "A",
3     "simple",
4     "string",
5     "made",
6     "up",
7     "of",
8     "words.",
9 ]
```

Using our fluent macro would return a Collection instance with the same list of words. You may have noticed that the final element of the results in **Figure 10.35** contains a trailing full-stop (“.”).

We can address this by modifying our macro implementations to the following:

Figure 10.36 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordSplit', function ($value) {
 7     return preg_split("/\W+/u", $value, -1, PREG_SPLIT_NO_EMPTY);
 8 });
 9 
10 Stringable::macro('wordSplit', function () {
11     return collect(
12         preg_split("/\W+/u", $this->value, -1, PREG_SPLIT_NO_EMPTY
13       )
14     );
15 });
```

The regular expression in **Figure 10.36** is slightly different, and it matches word boundaries, which include additional characters, not just whitespace. We are supplying -1 as the third argument to instruct the `preg_split` function not to limit the number of elements it returns. We are passing the `PREG_SPLIT_NO_EMPTY` flag to have the function remove empty strings for us automatically.

Calling our modified methods on the following input:

Figure 10.37 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $string = "A simple string (word (word))
6    made up of words; hello--there.";
7 
8 Str::wordSplit($string);
```

Produces the following result:

Figure 10.38 

```
 1 [
 2     "A",
 3     "simple",
 4     "string",
 5     "word",
 6     "word",
 7     "made",
 8     "up",
 9     "of",
10     "words",
11     "hello",
12     "there",
13 ]
```

### 10.3 Counting Word Occurrences

While Laravel already provides a `wordCount` helper method, we could also use our `wordSplit` method in combination with PHP’s `count` function:

Figure 10.39 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $string = 'The quick brown fox jumps over the lazy dog.';
 6 
 7 // Returns 9
 8 count(Str::wordSplit($string));
 9   
10 // Returns 9
11 Str::wordCount($string);
```

While using our custom method this way is not particularly advantageous, we can use it to accomplish some more nuanced tasks. One such thing might be to count the number of unique words in a string:

Figure 10.40 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns 9
6 count(array_unique(
7     Str::wordSplit($string)
8 ));
```

The example in **Figure 10.40** doesn’t seem to be working quite right, as it returns the same number of words as before. The culprit is the different casing between “The” and “the” within the sentence. We can solve this by transforming all of the words in our sentence first and then counting the result:

Figure 10.41 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns 8
6 count(array_unique(
7     array_map('mb_strtolower', Str::wordSplit($string))
8 ));
```

Our code now returns the value 8, the number of distinct words in our sentence. The previous example works because of the call to PHP’s `array_map` function. This function will apply a callback method to each element of an array; in our case, we will transform all of our strings to their lowercase variant. We can package these as new helper methods to be reused:

Figure 10.42 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('uniqueWordCount', function ($value) {
 7     return count(array_unique(
 8         array_map('mb_strtolower', Str::wordSplit($value))
 9     ));
10 });
11 
12 Stringable::macro('uniqueWordCount', function () {
13     return count(array_unique(
14         array_map('mb_strtolower', $this->wordSplit()->toArray())
15     ));
16 });
```

What if we wanted to count the number of occurrences of each word? One way we could accomplish this is by using Laravel’s Collection class.

Let’s think through what it is we are doing. We are effectively grouping each lowercase word variant and counting the number of items that appear within that group. We can express this quite nicely using Collections:

Figure 10.43 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $string = 'The quick brown fox jumps over the lazy dog.';
 6 
 7 collect(array_map('mb_strtolower', Str::wordSplit($string)))
 8     ->groupBy(fn($x) => $x)
 9     ->map(fn($g) => count($g))
10     ->all();
```

Our code in **Figure 10.43** would produce the following result:

Figure 10.44 

```
 1 array:8 [
 2     "the"   => 2
 3     "quick" => 1
 4     "brown" => 1
 5     "fox"   => 1
 6     "jumps" => 1
 7     "over"  => 1
 8     "lazy"  => 1
 9     "dog"   => 1
10 ]
```

At this point, we have created quite a few new helper methods to split our string into words, count the unique number of words, and count the number of times each word appears. However, we have two concepts of word splitting going on throughout these methods: retrieving *all* words and retrieving only the *unique* ones. Most of the code between these two techniques is shared, but we have no way to get a list of only the unique words. We can address the latter issue and do some code cleanup by adding a `$unique` parameter to our existing `wordSplit` helper methods:

Figure 10.45 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordSplit', function ($value, $unique = false) {
 7     if ($unique) {
 8         return array_unique(
 9 		    array_map('mb_strtolower', Str::wordSplit($value))
10 		);
11     }
12 
13     return preg_split("/\W+/u", $value, -1, PREG_SPLIT_NO_EMPTY);
14 });
15 
16 Stringable::macro('wordSplit', function ($unique = false) {
17     return collect(Str::wordSplit($this->value, $unique));
18 });
19 
20 Str::macro('uniqueWordCount', function ($value) {
21     return count(Str::wordSplit($value, true));
22 });
23 
24 Stringable::macro('uniqueWordCount', function () {
25     return Str::uniqueWordCount($this->value);
26 });
```

With these refactors out of the way, we can now define our new `wordFrequency` helper method to return the number of occurrences of each word in our text:

Figure 10.46 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordFrequency', function ($value) {
 7     return collect(array_map('mb_strtolower', Str::wordSplit($value)))
 8         ->groupBy(fn($x) => $x)
 9         ->map(fn($g) => count($g))
10         ->all();
11 });
12 
13 Stringable::macro('wordFrequency', function () {
14    return collect(Str::wordFrequency($this->value));
15 });
```

### 10.4 Finding Frequent and Repeated Words

In the previous section, we developed several word-related helper methods, among them being the `wordFrequency` method which returns the number of times a word appears in a piece of text. We can use this existing helper method to implement two new methods.

The first will find the top n most commonly used words in the text, and the other will find the words that repeatedly appear within the text. Both of these methods will be relatively straightforward to implement.

The first method we will implement will be the `commonWords` method, which will return an array of words up to some limit (the `$count` parameter). We do not care about the number of times the words appear in the text necessarily, just that the most commonly used ones appear first:

Figure 10.47 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('commonWords', function ($value, $count = 10) {
 7     return collect(Str::wordFrequency($value))
 8         ->sortDesc()
 9         ->take($count)
10         ->keys()
11         ->all();
12 });
13 
14 Stringable::macro('commonWords', function ($count = 10) {
15     return collect(Str::commonWords($this->value, $count));
16 });
```

Using our method on the following input:

Figure 10.48 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $string = 'the the the of of hello world';
6 
7 Str::commonWords($string, 2);
```

Would produce the following list of words:

Figure 10.49 

```
1 array:3 [
2     0 => "the"
3     1 => "of"
4     2 => "hello"
5 ]
```

The `repeatedWords` method will be similar, but for this implementation, we want to ensure the words returned in our array appear at least once in the input:

Figure 10.50 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('repeatedWords', function ($value, $count = 10) {
 7     return collect(Str::wordFrequency($value))
 8         ->filter(fn($x) => $x > 1)
 9         ->sortDesc()
10         ->take($count)
11         ->keys()
12         ->all();
13 });
14 
15 Stringable::macro('repeatedWords', function ($count = 10) {
16     return collect(Str::repeatedWords($this->value, $count));
17 });
```

Calling `repeatedWords` like so:

Figure 10.51 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::repeatedWords($string, 3)
```

Returns:

Figure 10.52 

```
1 array:2 [
2     0 => "the"
3     1 => "of"
4 ]
```

### 10.5 Stop Words

So far, we have developed several helper methods for extracting words, counting their frequency, etc. A common issue arising when we perform text analysis or mining is the frequency of common words within natural languages. Consider the following sample text:

> The group of otherwise ordinary but eccentric teenagers ran towards the barn under destress, with nothing but a crumpled newspaper for covering, before the storm hit fully.

While we can get through this text relatively quickly, this English sentence contains many words or phrases that help “glue” the individual words together and help set the pacing. Using our `commonWords` helper method on this text produces the following list:

Figure 10.53 

```
 1 array:24 [
 2      0 => "the"
 3      1 => "but"
 4      2 => "group"
 5      3 => "of"
 6      4 => "otherwise"
 7      5 => "ordinary"
 8      6 => "eccentric"
 9      7 => "teenagers"
10      8 => "ran"
11      9 => "towards"
12     10 => "barn"
13     11 => "under"
14     12 => "destress"
15     13 => "with"
16     14 => "nothing"
17     15 => "a"
18     16 => "crumpled"
19     17 => "newspaper"
20     18 => "for"
21     19 => "covering"
22     20 => "before"
23     21 => "storm"
24     22 => "hit"
25     23 => "fully"
26 ]
```

In the list of words produced, prepositions, coordinating conjunctions, and determiners dominate the top ten most commonly used words. We can help alleviate this problem through the use of stop words.

Stop words are a list of words we should remove from a piece of text before further processing. In our case, we will use a simple list of stop words. Still, the list of stop “words” can be anything that helps to make sense of the text we want to analyze: individual words, phrases, or combinations of them. There are many sources of stop word lists, but for our purposes, we will use the following list of words to help clean up our text:

Figure 10.54 

```
1 the
2 of
3 but
4 under
5 with
6 a
7 for
8 before
```

Our next step is to remove all of the words in our text that are also present in the stop word list. Suppose we wanted to describe our problem more formally. In that case, we could say that we have a set of words A and another B, and we want to produce a new set C containing all of the words in A that are not present in B.

We can accomplish this easily using Laravel’s Collection features and the diff method. The diff method will allow us to filter a collection of items and return those that do not appear in whatever list we supply. The code in **Figure 10.55**:

Figure 10.55 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 
 6 $text = <<<EOT
 7 The group of otherwise ordinary but eccentric teenagers
 8 ran towards the barn under destress, with nothing but a
 9 crumpled newspaper for covering, before the storm hit
10 fully.
11 EOT;
12 
13 $words = str($text)->wordSplit(true)->diff([
14     'the',
15     'of',
16     'but',
17     'under',
18     'with',
19     'a',
20     'for',
21     'before'
22 ]);
```

Would produce the following list of words:

Figure 10.56 

```
 1 group
 2 otherwise
 3 ordinary
 4 eccentric
 5 teenagers
 6 ran
 7 towards
 8 barn
 9 destress
10 nothing
11 crumpled
12 newspaper
13 covering
14 storm
15 hit
16 fully
```

Fantastic! We now have a method of removing words that add noise to our text analysis. Still, it would be even better if we could supply a list of stop words to our existing helper methods. Doing so would allow us to take advantage of things like word frequency, common occurrences, etc. while removing our stop words. **Figure 10.57** provides updated versions of our word-related helper methods with support for stop words:

Figure 10.57 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordSplit', function ($value,
 7                                   $unique = false,
 8                                   $stopWords = []) {
 9     if ($unique) {
10         return array_unique(array_map(
11             'mb_strtolower',
12             Str::wordSplit($value, false, $stopWords)
13         ));
14     }
15 
16     return collect(preg_split(
17         "/\W+/u", $value, -1,
18         PREG_SPLIT_NO_EMPTY
19     ))->diff($stopWords)->all();
20 });
21 
22 Stringable::macro('wordSplit', function ($unique = false,
23                                          $stopWords = []) {
24     return collect(Str::wordSplit($this->value, $unique, $stopWords));
25 });
26 
27 Str::macro('uniqueWordCount', function ($value,
28                                         $stopWords = []) {
29     return count(Str::wordSplit($value, true, $stopWords));
30 });
31 
32 Stringable::macro('uniqueWordCount', function () {
33     return count(Str::wordSplit($this->value, true));
34 });
35 
36 Str::macro('wordFrequency', function ($value,
37                                       $stopWords = []) {
38     return collect(array_map('mb_strtolower', Str::wordSplit($value)))
39         ->diff($stopWords)
40         ->groupBy(fn($x) => $x)
41         ->map(fn($g) => count($g))
42         ->all();
43 });
44 
45 Stringable::macro('wordFrequency', function ($stopWords = []) {
46    return collect(Str::wordFrequency($this->value));
47 });
48 
49 Str::macro('commonWords', function ($value,
50                                     $count = 10,
51                                     $stopWords = []) {
52     return collect(Str::wordFrequency($value))
53         ->diff($stopWords)
54         ->sortDesc()
55         ->take($count)
56         ->keys()
57         ->all();
58 });
59 
60 Stringable::macro('commonWords', function ($count = 10) {
61     return collect(Str::commonWords($this->value, $count));
62 });
63 
64 Str::macro('repeatedWords', function ($value,
65                                       $count = 10,
66                                       $stopWords = []) {
67     return collect(Str::wordFrequency($value))
68         ->diff($stopWords)
69         ->filter(fn($x) => $x > 1)
70         ->sortDesc()
71         ->take($count)
72         ->keys()
73         ->all();
74 });
75 
76 Stringable::macro('repeatedWords', function ($count = 10) {
77     return collect(Str::repeatedWords($this->value, $count));
78 });
```

We can now use our existing `wordFrequency` helper method to retrieve all words that were are interested in, with their number of occurrences:

Figure 10.58 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::wordFrequency($text, [
 6     'the',
 7     'of',
 8     'but',
 9     'under',
10     'with',
11     'a',
12     'for',
13     'before'
14 ]);
```

### 10.6 Constructing Initialisms and Acronyms

An interesting thing we can do with the word helper methods is to create a new one to help construct initialisms or acronyms from a string of words. For example, we may want to shorten the name “Jane Doe” to “JD” or even “J.D.” We already have a way to retrieve a list of words from a string using `wordSplit`. Our basic process will be to iterate each of the words of our string and extract the first character from each word and then concatenate them.

Leveraging our existing helper method and Laravel’s Collections, this simple implementation could look like the example in **Figure 10.59**:

Figure 10.59 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "JD"
6 collect(Str::wordSplit('Jane Doe'))
7     ->map(fn($w) => mb_substr($w, 0, 1))
8     ->join('');
```

The implementation in **Figure 10.59** works for our simple text input, but what if we wanted only to include words that have their first letter upper-cased? To do this, we can grab the first character of each word and check to see if it is already capitalized and if so, we will use it. We will start implementing these additional features in an `initials` macro method:

Figure 10.60 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 Str::macro('isCapitalized', function ($value) {
 6    if (str($value)->isEmpty()) {
 7          return false;
 8    }
 9 
10     $firstChar = str($value)->substr(0, 1);
11 
12    return $firstChar == mb_strtoupper($firstChar);
13 });
14 
15 Str::macro('initials', function ($value, $ucOnly = true) {
16     return str($value)->wordSplit->reject(function ($word)
17                                                use ($ucOnly) {
18         if ($ucOnly && !Str::isCapitalized($word)) {
19             return true;
20         }
21 
22         return false;
23     })->map(function ($word) {
24         return mb_strtoupper(mb_substr($word, 0, 1));
25     })->join('');
26 });
```

We have a lot going on with this updated implementation. To start, we added a new helper method `isCapitalized` that tests if the provided value has its first character uppercased. We use this inside a newly added “reject” callback on our collection of words.

When the reject callback returns true, it will not include that word in the final list. We are taking advantage of this to exclude any words that do not have their first letter capitalized. Finally, we modified the final `map` callback to uppercase all the characters in the final initialism.

Calling our new helper method from **Figure 10.60** would produce the following results:

Figure 10.61 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "JD"
6 Str::initials('Jane m Doe');
7 
8 // Returns "JMD"
9 Str::initials('Jane m Doe', false);
```

### 10.7 Calculating Estimated Reading Time

An interesting thing we can do with our word helper methods is to calculate an estimated reading time for a piece of text. From an implementation standpoint, it is relatively straightforward: we need to know the number of words within the text and have a value for the average number of words people read in some time frame.

An analysis of 190 studies estimates that the average reading time was between 238 and 260 words per minute, depending on the genre^([7](#chap29.xhtml#fn-citation_wpm)). This estimate was arrived at by looking at the reading time of adults silently reading English text. For our use case, we will use the lower value of 238 words per minute for non-fiction in our calculations.

Our first pass at implementing this feature may look something like **Figure 10.62**:

Figure 10.62 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 Str::macro('readingTime', function ($value, $wpm = 238) {
6     return ceil(Str::wordCount($value) / $wpm);
7 });
```

Our implementation uses the `wordCount` helper method to retrieve the number of words in the provided value and divides it by the desired words per minute. We also use PHP’s `ceil` function on the result to round up the nearest whole minute. These calculations are estimates at best, and it is not entirely practical to break things down into minutes and seconds in most cases.

We can use our new `readingTime` helper method like so to get the approximate reading time of a string containing 1,000 words:

Figure 10.63 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns 5.0
6 Str::readingTime(
7     Str::repeat('word ', 1000)
8 );
```

Our method returns an approximate value of five minutes. The next question might be, what about if we had an extremely long piece of text? For example, using our default words per minute value, a text containing 65,535 words would return an estimated reading time of 275 minutes. Most people are comfortable with smaller units of time and may find it challenging to understand precisely how long 275 minutes is quickly. A better user experience might be to break these larger time frames into smaller units, such as hours and minutes.

We could work to implement this ourselves, but one of Laravel’s dependencies is the Carbon date/time library. Luckily for us, a `CarbonInterval` class exists that allows us to take a time interval expressed in seconds and convert it into a more understandable format.

The following refactors to our implementation to return a new `CarbonInterval` instance, which provides many helpful methods (note that we are multiplying our previous results by sixty to convert the number of minutes into seconds):

Figure 10.64 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 use Carbon\CarbonInterval;
 6 
 7 Str::macro('readingTime', function ($value, $wpm = 238) {
 8     return CarbonInterval::seconds(
 9         ceil(Str::wordCount($value) / $wpm) * 60
10     )->cascade();
11 });
12 
13 Stringable::macro('readingTime', function ($wpm = 238) {
14     return Str::readingTime($this->value, $wpm);
15 });
```

The `cascade` method call on the `CarbonInterval` class is what will break our seconds into smaller units. Using our updated helper method in **Figure 10.64**, we can now chain the `forHumans` method call to output nicely formatted results:

Figure 10.65 

```
1 <?php
2 
3 // Returns "4 hours 36 minutes"
4 str('word ')
5     ->repeat(65535)
6     ->readingTime->forHumans();
```

We’ve covered a lot of ground in this chapter, and there is still much more to do with lines and words. You may ask: “Where do we go from here?”. We go to chapter eleven.

## 11\. More Lines and Words

We are going to continue our discussion surrounding lines and words. So much of our work and lives revolve around information presented using these two constructs it makes sense for us to linger on them for a little longer. In Chapter 10, we created several helper methods that enable us to perform various word and line-related tasks, such as:

*   Resolving the line and column numbers of arbitrary positions,
*   Counting word occurrences,
*   Splitting strings into words

We will dive right in and work on a collection of new word-related helper methods aimed at helping retrieve information about words located at arbitrary positions within a string.

### 11.1 Locating Words at Arbitrary Positions

Consider the simple phrase “Hello, world.” Let us say that we need to get the word located at position 9, which corresponds to the letter “r” within the word “world.” This position was chosen because it presents an exciting challenge right from the start: we have multiple choices for word boundaries on the right and a word boundary and end of the string to the right.

When approaching problems like this, it is tempting to split the string into an array of words and then count the number of characters of each word you encounter until you get within range of the desired position. While this approach can work, it often ignores things such as whitespace or punctuation characters. The technique I like to use when tackling these sorts of problems is to start at the requested position within the string and iterate backward until I hit a word boundary and do the same going forwards. The basic implementation of this technique can be found in **Figure 11.1**:

Figure 11.1 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function getWordAtPosition($value, $position) {
 6     if ($position < 0) { return null; }
 7 
 8     $string = new Utf8StringIterator($value);
 9 
10     if ($position > count($string)) { return null; }
11 
12     $leadingChars = '';
13     $trailingChars = '';
14 
15     for ($i = $position; $i >= 0; $i--) {
16         $char = $string[$i];
17 
18         if (ctype_space($char) || ctype_punct($char)) {
19             break;
20         }
21 
22         $leadingChars .= $char;
23     }
24 
25     if ($position + 1 < count($string)) {
26         for ($i = $position + 1; $i < count($string); $i++) {
27             $char = $string[$i];
28 
29             if (ctype_space($char) || ctype_punct($char)) {
30                 break;
31             }
32 
33             $trailingChars .= $char;
34         }
35     }
36 
37     return Str::reverse($leadingChars).$trailingChars;
38 }
```

We see two new PHP functions being used within the `getWordAtPosition` function implementation: `ctype_space` and `ctype_punct`. These handy functions check if the provided string is composed entirely of whitespace or punctuation characters.

The first loop we create starts at the requested position and scans backward through the string until it encounters a whitespace or punctuation character, at which point it exits the loop. Because we are looping back through the text, the characters we retrieve will be reversed relative to the direction they appear in the input string. We take care of this at the end of the function when returning the output by reversing all leading characters.

The second loop is incredibly similar to the first, except that we start at a position one greater than the requested position since the requested position will already be part of the leading character string. Again, we continue to iterate all of the characters of the string until we encounter whitespace or punctuation characters. The final step of our function is to reverse the leading characters and concatenate them with the trailing characters, returning the combined result.

We can now use our function to get words at arbitrary positions within our string like so:

Figure 11.2 

```
 1 <?php
 2 
 3 $text = 'Hello, world';
 4 
 5 // Returns "world"
 6 getWordAtPosition($text, 9);
 7 
 8 // Returns "world"
 9 getWordAtPosition($text, 10);
10 
11 // Returns "Hello"
12 getWordAtPosition($text, 2);
```

Our current implementation behaves as expected when we supply a position within a word but returns unexpected results when we provide a position corresponding to whitespace characters or punctuation. As an example, if we call our function with a position value of 6, which corresponds to the space between “Hello,” and “world,” it will currently return “world.” We can resolve this by checking the character at the desired position before iterating our string like so:

Figure 11.3 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function getWordAtPosition($value, $position) {
 6     if ($position < 0) { return null; }
 7 
 8     $string = new Utf8StringIterator($value);
 9 
10     if ($position > count($string)) { return null; }
11 
12     $posChar = $string[$position];
13 
14     if (ctype_space($posChar) || ctype_punct($posChar)) {
15         return null;
16     }
17 
18     $leadingChars = '';
19     $trailingChars = '';
20 
21     for ($i = $position; $i >= 0; $i--) {
22         $char = $string[$i];
23 
24         if (ctype_space($char) || ctype_punct($char)) {
25             break;
26         }
27 
28         $leadingChars .= $char;
29     }
30 
31     if ($position + 1 < count($string)) {
32         for ($i = $position + 1; $i < count($string); $i++) {
33             $char = $string[$i];
34 
35             if (ctype_space($char) || ctype_punct($char)) {
36                 break;
37             }
38 
39             $trailingChars .= $char;
40         }
41     }
42 
43     return Str::reverse($leadingChars).$trailingChars;
44 }
```

Calling our refactored function with a position of 6 will now return `null`, which is consistent with the behavior of requesting a word that is not within the string’s boundary.

The finish line is in sight, but we have one last thing to address before moving on. If we attempt to retrieve a hyphenated word with our current implementation, it will currently return whatever part of the word happens to be located at the requested position. We can solve this by adding a third, optional parameter that accepts an array of characters that we should *not* break on.

Figure 11.4 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 function getWordAtPosition(
 6     $value,
 7     $position,
 8     $chars = ['-']
 9     ) {
10 
11     if ($position < 0) { return null; }
12 
13     $string = new Utf8StringIterator($value);
14 
15     if ($position > count($string)) { return null; }
16 
17     $posChar = $string[$position];
18 
19     if (ctype_space($posChar) || ctype_punct($posChar)) {
20         return null;
21     }
22     if (! in_array($posChar, $chars) &&
23         (ctype_space($posChar) || ctype_punct($posChar))) {
24         return null;
25     }
26 
27     $leadingChars = '';
28     $trailingChars = '';
29 
30     for ($i = $position; $i >= 0; $i--) {
31         $char = $string[$i];
32 
33         if (in_array($char, $chars)) {
34             $leadingChars .= $char;
35             continue;
36         }
37 
38         if (ctype_space($char) || ctype_punct($char)) {
39             break;
40         }
41 
42         $leadingChars .= $char;
43     }
44 
45     if ($position + 1 < count($string)) {
46         for ($i = $position + 1; $i < count($string); $i++) {
47             $char = $string[$i];
48 
49             if (in_array($char, $chars)) {
50                 $trailingChars .= $char;
51                 continue;
52             }
53 
54             if (ctype_space($char) || ctype_punct($char)) {
55                 break;
56             }
57 
58             $trailingChars .= $char;
59         }
60     }
61 
62     return Str::reverse($leadingChars).$trailingChars;
63 }
```

Our refactors from **Figure 11.4** now enable us to retrieve the hyphenated word “hello-world” in the following example:

Figure 11.5 

```
 1 <?php
 2 
 3 // Returns "hello-world"
 4 getWordAtPosition("hello-world", 5);
 5 
 6 // Returns "hello-world"
 7 getWordAtPosition("hello-world", 5, ['-']);
 8 
 9 // Returns null
10 getWordAtPosition("hello-world", 5, []);
```

Our final step will be to package this function into a set of Laravel string helper methods:

Figure 11.6 wordAt Helper Method Implementations 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('wordAt', function ($value, $position, $chars = ['-']) {
 7     if ($position < 0) { return null; }
 8 
 9     $string = new Utf8StringIterator($value);
10 
11     if ($position > count($string)) { return null; }
12 
13     $posChar = $string[$position];
14 
15     if (! in_array($posChar, $chars) &&
16         (ctype_space($posChar) || ctype_punct($posChar))) {
17         return null;
18     }
19 
20     $leadingChars = '';
21     $trailingChars = '';
22 
23     for ($i = $position; $i >= 0; $i--) {
24         $char = $string[$i];
25 
26         if (in_array($char, $chars)) {
27             $leadingChars .= $char;
28             continue;
29         }
30 
31         if (ctype_space($char) || ctype_punct($char)) {
32             break;
33         }
34 
35         $leadingChars .= $char;
36     }
37 
38     if ($position + 1 < count($string)) {
39         for ($i = $position + 1; $i < count($string); $i++) {
40             $char = $string[$i];
41 
42             if (in_array($char, $chars)) {
43                 $trailingChars .= $char;
44                 continue;
45             }
46 
47             if (ctype_space($char) || ctype_punct($char)) {
48                 break;
49             }
50 
51             $trailingChars .= $char;
52         }
53     }
54 
55     return Str::reverse($leadingChars).$trailingChars;
56 });
57 
58 Stringable::macro('wordAt', function ($position, $chars = ['-']) {
59     return new static (
60         Str::wordAt($this->value, $position, $chars)
61     );
62 });
```

### 11.2 Locating Neighboring Words and Characters

The next task we will look at together is retrieving neighboring words from arbitrary positions. For example, given the sentence “The quick brown fox jumped over the lazy dog,” if we supplied position 6, we might want to be able to retrieve the word “The” on the left and the word “brown” on the right. There are a few ways we could approach implementing this. The first idea may be to update our previous `wordAt` implementation and skip collecting the characters to return until we’ve reached a word boundary.

The approach of waiting until we’ve seen a word boundary works but involves keeping track of additional states, which can quickly get messy. A more elegant solution may be to retrieve the position of the neighboring non-word boundary character and then use that position in a call to our existing `wordAt` helper method.

To begin, we will start by retrieving the position of the next non-word boundary character to the left of our target position. This implementation will feel familiar, as it is a stripped-down version of our `wordAt` helper method but only focuses on scanning backward through our input string. **Figure 11.7** provides an implementation of retrieving the end position of the word before our desired position:

Figure 11.7 

```
 1 <?php
 2 
 3 function getNextWordPositionLeft(
 4     $value,
 5     $position,
 6     $chars = ['-']
 7 ) {
 8     if ($position < 0) { return null; }
 9 
10     $string = new Utf8StringIterator($value);
11 
12     if ($position > count($string)) { return null; }
13 
14     $exitedInitialWord = false;
15 
16     for ($i = $position; $i >= 0; $i--) {
17         $char = $string[$i];
18 
19         if (in_array($char, $chars)) {
20             if ($exitedInitialWord) {
21                 return $string->getPositionFromCharIndex($i);
22             }
23 
24             continue;
25         }
26 
27         if (ctype_space($char) || ctype_punct($char)) {
28             $exitedInitialWord = true;
29             continue;
30         }
31 
32         if ($exitedInitialWord) {
33             return $string->getPositionFromCharIndex($i);
34         }
35     }
36 
37     return null;
38 }
```

Calling this function on our sample returns the value 2, which corresponds to the letter “e” in the word “The”:

Figure 11.8 

```
1 <?php
2 
3 $text = 'The quick brown fox jumped over the lazy dog';
4 
5 // Returns 2
6 getNextWordPositionLeft($text, 6);
```

This currently does not return the actual word, but we can use the results of this function in another call to `wordAt` to return the entire word:

Figure 11.9 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = 'The quick brown fox jumped over the lazy dog';
 6 
 7 // Returns "The"
 8 Str::wordAt(
 9     $text,
10     getNextWordPositionLeft($text, 6)
11 );
```

Implementing the function to retrieve the word position to the right is also relatively straightforward:

Figure 11.10 

```
 1 <?php
 2 
 3 function getNextWordPositionRight(
 4     $value,
 5     $position,
 6     $chars = ['-']
 7 ) {
 8     if ($position < 0) { return null; }
 9 
10     $string = new Utf8StringIterator($value);
11 
12     if ($position > count($string)) { return null; }
13 
14     $exitedInitialWord = false;
15 
16     for ($i = $position; $i < count($string); $i++) {
17         $char = $string[$i];
18 
19         if (in_array($char, $chars)) {
20             if ($exitedInitialWord) {
21                 return $string->getPositionFromCharIndex($i);
22             }
23 
24             continue;
25         }
26 
27         if (ctype_space($char) || ctype_punct($char)) {
28             $exitedInitialWord = true;
29             continue;
30         }
31 
32         if ($exitedInitialWord) {
33             return $string->getPositionFromCharIndex($i);
34         }
35     }
36 
37     return null;
38 }
```

Using all of our new functions together, we can retrieve the words “The,” “quick,” and “brown” by supplying only position 6 to our various functions:

Figure 11.11 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = 'The quick brown fox jumped over the lazy dog';
 6 
 7 // Returns "The"
 8 Str::wordAt(
 9     $text,
10     getNextWordPositionLeft($text, 6)
11 );
12 
13 // Returns "quick"
14 Str::wordAt($text, 6);
15 
16 // Returns "brown"
17 Str::wordAt(
18     $text,
19     getNextWordPositionRight($text, 6)
20 );
```

We can package all of these functions into a set of new helper methods to make them more approachable:

Figure 11.12 Retrieving Left and Right Words 

```
  1 <?php
  2 
  3 use Illuminate\Support\Str;
  4 use Illuminate\Support\Stringable;
  5 
  6 Str::macro('nextWordPositionLeft', function (
  7     $value,
  8     $position,
  9     $chars = ['-']) {
 10     if ($position < 0) { return null; }
 11 
 12     $string = new Utf8StringIterator($value);
 13 
 14     if ($position > count($string)) { return null; }
 15 
 16     $exitedInitialWord = false;
 17 
 18     for ($i = $position; $i >= 0; $i--) {
 19         $char = $string[$i];
 20 
 21         if (in_array($char, $chars)) {
 22             if ($exitedInitialWord) {
 23                 return $string->getPositionFromCharIndex($i);
 24             }
 25 
 26             continue;
 27         }
 28 
 29         if (ctype_space($char) || ctype_punct($char)) {
 30             $exitedInitialWord = true;
 31             continue;
 32         }
 33 
 34         if ($exitedInitialWord) {
 35             return $string->getPositionFromCharIndex($i);
 36         }
 37     }
 38 
 39     return null;
 40 });
 41 
 42 Stringable::macro('nextWordPositionLeft', function (
 43     $position,
 44     $chars = ['-']) {
 45     return Str::nextWordPositionLeft($this->value, $position, $chars);
 46 });
 47 
 48 Str::macro('nextWordPositionRight', function (
 49     $value,
 50     $position,
 51     $chars = ['-']) {
 52     if ($position < 0) { return null; }
 53 
 54     $string = new Utf8StringIterator($value);
 55 
 56     if ($position > count($string)) { return null; }
 57 
 58     $exitedInitialWord = false;
 59 
 60     for ($i = $position; $i < count($string); $i++) {
 61         $char = $string[$i];
 62 
 63         if (in_array($char, $chars)) {
 64             if ($exitedInitialWord) {
 65                 return $string->getPositionFromCharIndex($i);
 66             }
 67 
 68             continue;
 69         }
 70 
 71         if (ctype_space($char) || ctype_punct($char)) {
 72             $exitedInitialWord = true;
 73             continue;
 74         }
 75 
 76         if ($exitedInitialWord) {
 77             return $string->getPositionFromCharIndex($i);
 78         }
 79     }
 80 
 81     return null;
 82 });
 83 
 84 Stringable::macro('nextWordPositionRight', function (
 85     $position,
 86     $chars = ['-']) {
 87     return Str::nextWordPositionRight($this->value, $position, $chars);
 88 });
 89 
 90 Str::macro('wordLeftAt', function (
 91     $value,
 92     $position,
 93     $chars = ['-']) {
 94    return Str::wordAt(
 95          $value,
 96          Str::nextWordPositionLeft($value, $position, $chars),
 97          $chars
 98     );
 99 });
100 
101 Stringable::macro('wordLeftAt', function ($position, $chars = ['-']) {
102     return new static (
103         Str::wordLeftAt($this->value, $position, $chars)
104     );
105 });
106 
107 Str::macro('wordRightAt', function (
108     $value,
109     $position,
110     $chars = ['-']) {
111    return Str::wordAt(
112          $value,
113          Str::nextWordPositionRight($value, $position, $chars),
114          $chars
115     );
116 });
117 
118 Stringable::macro('wordRightAt', function ($position, $chars = ['-']) {
119     return new static (
120         Str::wordRightAt($this->value, $position, $chars)
121     );
122 });
```

Our new set of helper methods is much less intimidating to look at:

Figure 11.13 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = 'The quick brown fox jumped over the lazy dog';
 6 
 7 // Returns "The"
 8 Str::wordLeftAt($text, 6);
 9 
10 // Returns "quick"
11 Str::wordAt($text, 6);
12 
13 // Returns "brown"
14 Str::wordRightAt($text, 6);
```

### 11.3 Retrieving Adjacent Lines

In this section, we are going to do some experimenting with lines instead of words. Specifically, we are going to work on implementing a new helper method that will accept a value, a target line number, and a radius, a number of additional lines surrounding our target line to return. Our new method will behave similarly to the `excerpt` helper method but work on lines instead.

Let us take a look at the following piece of text:

Figure 11.14 

```
 1 Line one
 2 Line two
 3 Line three
 4 Line four
 5 Line five
 6 Line six
 7 Line seven
 8 Line eight
 9 Line nine
10 Line ten
```

Suppose we want to extract line five and two additional lines on either side and return them as an array. The basic implementation of this, while accounting for the radius lines exceeding the number of total lines, may look similar to the following:

Figure 11.15 lineExcerpt Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('lineExcerpt', function ($value, $lineNumber, $radius = 2) {
 7     if ($lineNumber < 0) { return []; }
 8 
 9     $lines = Str::lineSplit($value);
10     $lineCount = count($lines);
11 
12     if ($lineNumber > $lineCount) { return []; }
13 
14     // Subtract one to convert our one-based
15     // line number into a zero-based index.
16     $lineNumber -= 1;
17 
18     $minLine = $lineNumber - $radius;
19     $maxLine = $lineNumber + $radius;
20 
21     // Ensure or min and max lines stay within bounds.
22     if ($minLine < 0) { $minLine = 0; }
23     if ($maxLine >= $lineCount) { $maxLine = $lineCount - 1; }
24 
25     $returnLines = [];
26 
27     for ($i = $minLine; $i <= $maxLine; $i++) {
28         $returnLines[$i + 1] = $lines[$i];
29     }
30 
31     return $returnLines;
32 });
33 
34 Stringable::macro('lineExcerpt', function ($lineNumber, $radius = 2) {
35     return collect(
36         Str::lineExcerpt($this->value, $lineNumber, $radius)
37     );
38 });
```

Calling our method on our sample text like so:

Figure 11.16 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = <<<LINES
 6 Line one
 7 Line two
 8 Line three
 9 Line four
10 Line five
11 Line six
12 Line seven
13 Line eight
14 Line nine
15 Line ten
16 LINES;
17 
18 Str::lineExcerpt($text, 5, 2);
```

Produces the following array:

Figure 11.17 

```
1 array:5 [
2     3 => "Line three"
3     4 => "Line four"
4     5 => "Line five"
5     6 => "Line six"
6     7 => "Line seven"
7 ]
```

You may notice that we are not returning a string from this method. This implementation has opted to return an array instead of a concatenated string so that it can return the line numbers as the keys of the array. We can either use PHP’s `implode` function or Laravel’s collection features to convert our array into a single string:

Figure 11.18 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 implode("\n", Str::lineExcerpt($text, 5, 2));
6 
7 str($text)->lineExcerpt(5)->join("\n");
```

Because our method returns an array (or a Collection instance in the case of the fluent string macro), we can now do some rather interesting things with this method. While working on a number of developer tools throughout the years, one common technique I like to use to provide feedback to users of command-line systems is to present error messages in a format similar to the following:

Figure 11.19 

```
1 foreach is missing a variable to loop
2 
3    07|line seven
4    08|
5  =>09|@foreach
6    10|    more lines
7    11|
```

The message in **Figure 11.19** was generated from the sample text in **Figure 11.20**. We will not concern ourselves with *how* we detected an error but focus instead on how to print our lines using that style.

Figure 11.20 

```
 1 line one
 2 line two
 3 line three
 4 line four
 5 line five
 6 line six
 7 line seven
 8 
 9 @foreach
10     more lines
11 
12 @endforeach
```

Our basic algorithm will break out our input value into an array of lines and their contents using our existing `lineExcerpt` helper method. Each line will be printed using a prefix with either three spaces or a space followed by a sequence of characters that look like an arrow. This is followed by the line number, a pipe, and then the contents of the line. The helper method implementation may look like the one provided in **Figure 11.21**:

Figure 11.21 prettyPrintError Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('prettyPrintError', function (
 7     $value,
 8     $targetLine,
 9     $message,
10     $radius = 2) {
11 
12     $lines = Str::lineExcerpt($value, $targetLine, $radius);
13     // Get the size of the largest line number from our text
14     $maxLineLen = str(max(array_keys($lines)))->length;
15 
16     // Add some newlines to our message.
17     $message .= "\n\n";
18 
19     return $message . collect($lines)
20             ->map(function ($line, $lineNo)
21                        use ($targetLine, $maxLineLen) {
22             $prefix = '   ';
23 
24             if ($targetLine == $lineNo) {
25                 $prefix = ' =>';
26             }
27 
28             return $prefix .
29                    str($lineNo)->padLeft($maxLineLen, '0') .
30                    '|' . $line;
31         })->join("\n");
32 });
```

The first part of the implementation is concerned with determining the max line length, which we later use to pad all line numbers with leading zeroes, and adding some extra new lines to our error message. After that, we use Laravel’s collection features to map our array of lines to their prefixed version and then join them using the newline character.

Calling our new helper method like so would produce the output seen in **Figure 11.19**:

Figure 11.22 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $code = <<<BLADE
 6 line one
 7 line two
 8 line three
 9 line four
10 line five
11 line six
12 line seven
13 
14 @foreach
15     more lines
16 
17 @endforeach
18 BLADE;
19 
20 
21 Str::prettyPrintError(
22     $code,
23     9,
24     'foreach is missing a variable to loop'
25 );
```

### 11.4 Managing Text Indentation

Working with both spaces and tabs is not uncommon when accepting text input from users. For internal processing, I find it easier to work exclusively with spaces instead of tabs. The helper method in **Figure 11.23** can be used to convert tab characters into spaces using a predefined tab size:

Figure 11.23 convertTabs Method Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('convertTabs', function ($value, $tabSize = 4) {
 7     return str($value)->replace("\t", str(' ')
 8         ->repeat($tabSize))->toString();
 9 });
10 
11 Stringable::macro('convertTabs', function ($tabSize = 4) {
12     return new static (
13         Str::convertTabs($this->value, $tabSize)
14     );
15 });
```

We can now use our helper method to convert tab characters to spaces like so:

Figure 11.24 

```
1 <?php
2 
3 // Returns "    Hello"
4 str('	Hello')->convertTabs(4);
```

If you are not used to replacing escape sequences within strings, you may wonder if this would accidentally replace a literal backslash followed by the character “t.” We can do a quick experiment to prove to ourselves that this is not the case. Recall from Chapter 1 that single-quoted strings do not support escape sequences. We can test if our blind replacement will accidentally remove literal character sequences:

Figure 11.25 

```
1 <?php
2 
3 // Returns "\tNot a tab"
4 (string) str('\tNot a tab')
5   ->replace("\t", '  ');
```

We can use this helper method to implement another handy helper method, one that will return the indentation level of a given string using a known tab size:

Figure 11.26 indentCount Method Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('indentCount', function ($value, $tabSize = 4) {
 7     if ($tabSize <= 0) { return 0; }
 8 
 9     $withoutTabChar = Str::convertTabs($value, $tabSize);
10     $trimmedLen = str($withoutTabChar)->ltrim->length;
11     $origLen = str($value)->length;
12     $wsDifference = $origLen - $trimmedLen;
13 
14     return floor($wsDifference / $tabSize);
15 });
16 
17 Stringable::macro('indentCount', function ($tabSize = 4) {
18     return Str::getIndentCount($this->value, $tabSize);
19 });
```

This implementation first ensures that the input value contains only tab characters, using the provided tab size. Next, we get the string length before and after trimming any leading whitespace. We then divide the difference between the original and trimmed lengths by the tab size. This process may yield floats if the difference cannot be divided evenly. To account for this, we use PHP’s `floor` function to effectively round the result down to the nearest whole number.

The following example demonstrates how we may use our new `indentCount` helper method:

Figure 11.27 

```
 1 <?php
 2 
 3 // Returns 1
 4 str('    Hello')->indentCount(4);
 5 
 6 // Returns 1
 7 str('      Hello')->indentCount(4);
 8 
 9 // Returns 2
10 str('    Hello')->indentCount(2);
11 
12 // Returns 3
13 str('      Hello')->indentCount(2);
```

We can continue building on our existing methods to create another indentation-related helper method. This new method will iterate all of the lines within a piece of text, calculate the indentation for each line, and return the results.

Figure 11.28 indentation Method Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 class TextIndentation
 7 {
 8     public function __construct(
 9         public string $line,
10         public int $lineNumber,
11         public int $leadingWhitespace,
12         public int $indentCount,
13     ) {}
14 }
15 
16 Str::macro('indentation', function ($value, $tabSize = 4) {
17     return str($value)->lineSplit->map(function ($line, $i)
18                                             use ($tabSize) {
19         $trimmedLen = str($line)->ltrim->length;
20         $originalLen = str($line)->length;
21         $leadingWhitespace = $originalLen - $trimmedLen;
22         $indentCount = Str::indentCount($line, $tabSize);
23 
24         return new TextIndentation(
25             $line,
26             $i + 1,
27             $leadingWhitespace,
28             $indentCount
29         );
30     })->all();
31 });
32 
33 Stringable::macro('indentation', function ($tabSize = 4) {
34     return collect(
35         Str::indentation($this->value, $tabSize)
36     );
37 });
```

There looks to be a lot going on with the indentation implementation, but if we break it down, it is iterating each line of our input string and returning the total amount of leading whitespace. The amount of leading whitespace is again the difference between the untrimmed and trimmed lines. Along with this information, we also return the line content, the one-based line number (the current index incremented by one), and an indentation count calculated using our previous helper method. This information is encapsulated in a new `TextIndentation` class to help keep things organized. We will make further use of this class soon.

Given the sample string in **Figure 11.29**:

Figure 11.29 

```
1 L01
2       L02
3         L03
4         L04
```

Calling our new helper method like so:

Figure 11.30 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = <<<TEXT
 6 L01
 7       L02
 8         L03
 9         L04
10 TEXT;
11 
12 Str::indentation($text);
```

Returns the following result:

Figure 11.31 

```
 1 array:4 [
 2   0 => TextIndentation {
 3     line: "L01"
 4     lineNumber: 1
 5     leadingWhitespace: 0
 6     indentCount: 0
 7   }
 8   1 => TextIndentation {
 9     line: "      L02"
10     lineNumber: 2
11     leadingWhitespace: 6
12     indentCount: 1
13   }
14   2 => TextIndentation {
15     line: "        L03"
16     lineNumber: 3
17     leadingWhitespace: 8
18     indentCount: 2
19   }
20   3 => TextIndentation {
21     line: "        L04"
22     lineNumber: 4
23     leadingWhitespace: 8
24     indentCount: 2
25   }
26 ]
```

As you can see, our helper method extracts quite a bit of information about the provided text. We will use this information to create an `IndentationManager` class in the next section, which can be used to group lines based on their relative indentation.

### 11.5 Implementing an IndentationManager Class

We will continue to build on the numerous indentation helper methods in this section to create a new `IndentationManager` class. This class will be capable of grouping lines together based on their relative indentation. To help clarify what we are going to build, let us reuse the following text:

Figure 11.32 

```
1 L01
2     L02
3         L03
4         L04
5     L05
```

With the class we are about to build together, we would be able to retrieve the following direct ancestors of line one because they are indented a level further than line one:

*   L02
*   L05

Additionally, we would be able to retrieve all lines two through five under line one since their indentation levels are all nested below it.

Before we start on our implementation, we will need to add a few new properties to our existing `TextIndentation` class. These new properties will be used to store what lines are direct ancestors of any given line as well as all of the lines below any given line:

Figure 11.33 

```
 1 <?php
 2 
 3 class TextIndentation
 4 {
 5     public function __construct(
 6         public string $line,
 7         public int $lineNumber,
 8         public int $leadingWhitespace,
 9         public int $indentCount,
10     ) {}
11 
12     /**
13      * @var TextIndentation[]
14      */
15     public $nestedLines = [];
16 
17     /**
18      * @var TextIndentation[]
19      */
20     public $allNestedLines = [];
21 }
```

The following shell will be used to implement our `IndentationManager`, and we will implement each empty method and discuss the changes as we go along:

Figure 11.34 IndentationManager Class Overview 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class IndentationManager
 6 {
 7     /**
 8      * @var TextIndentation[]
 9      */
10     protected $lines;
11 
12     /**
13      * @var int
14      */
15     protected $numberOfLines;
16 
17     public function __construct(string $value, $tabSize = 4)
18     {
19         $this->lines = Str::indentation($value, $tabSize);
20         $this->numberOfLines = count($this->lines);
21         $this->groupIndentation();
22     }
23 
24     public function getLines()
25     {
26         return $this->lines;
27     }
28 
29     private function groupIndentation()
30     {
31     }
32 
33     protected function nestLines($start)
34     {
35     }
36 }
```

Our constructor is doing several things right from the start. The first thing it does is use our existing indentation helper method to calculate all of the relative indentation and leading whitespace for all lines of the input text. After this, we store the number of lines in an internal variable, which we will make frequent use of later. Finally, we call an internal `groupIndentation` method, which has not yet been implemented.

Let us take a look at the implementation of the `groupIndentation` method:

Figure 11.35 Implementing the groupIndentation Method 

```
 1 <?php
 2 
 3 class IndentationManager
 4 {
 5 
 6     // ...
 7 
 8     private function groupIndentation()
 9     {
10         if ($this->numberOfLines == 0) {
11             return;
12         }
13 
14         for ($i = 0; $i < $this->numberOfLines; $i++) {
15             if (str($this->lines[$i]->line)->trim->length == 0) {
16                 continue;
17             }
18 
19             $this->nestLines($i);
20         }
21     }
22 
23     // ...
24 
25 }
```

The first thing we do is check if the number of lines is zero; if so, we return from our method early as there will be nothing to process. If we do have lines to process, our next step is to iterate each and call another internal method `nestLines` on each line. We only call this internal method if the trimmed length of our line is non-zero, as these just add extra noise to our analysis step and can overcomplicate things.

Our next step is to implement the `nestLines` method, which will perform the actual nesting of our lines from the input text, and is by far the most involved method so far:

Figure 11.36 Implementing the nestLines Method 

```
 1 <?php
 2 
 3 class IndentationManager
 4 {
 5 
 6     // ...
 7 
 8     protected function nestLines($start)
 9     {
10         $line = $this->lines[$start];
11 
12         if ($start + 1 >= $this->numberOfLines) {
13             return;
14         }
15 
16         $nestedLines = [];
17 
18         for ($i = $start + 1; $i < $this->numberOfLines; $i++) {
19             $current = $this->lines[$i];
20 
21             if ($current->indentCount <= $line->indentCount &&
22                 str($current->line)->trim->length > 0) {
23                 break;
24             }
25 
26             $nestedLines[] = $current;
27         }
28 
29         if (count($nestedLines) == 0) {
30             return;
31         }
32 
33         $firstIndent = $nestedLines[0]->indentCount;
34 
35         // Find the first non-zero indentation, if any.
36         if ($firstIndent == 0) {
37             for ($i = 1; $i < count($nestedLines); $i++) {
38                 if ($nestedLines[$i]->indentCount > 0) {
39                     $firstIndent = $nestedLines[$i]->indentCount;
40                     break;
41                 }
42             }
43         }
44 
45         $line->allNestedLines = $nestedLines;
46 
47         $line->nestedLines = collect($nestedLines)
48             ->filter(function ($line) use ($firstIndent) {
49             return $line->indentCount == $firstIndent;
50         })->values()->all();
51     }
52 
53     // ...
54 }
```

Our `nestLines` method accepts the index of the line to nest as its only argument; the first thing we do is check if there are any more lines after the current line. If not, we return early from the method.

Between lines 18 and 27, we begin iterating all of the lines that appear after the current line. We are gathering all of the lines that come after the current line with an indentation depth *greater* than the current line. This is accomplished by breaking out of our loop the first time we encounter a line with an indentation level that is the same or less than our current line.

Lines 29-31 check to see if we have found any lines that should be nested. If we have not found any, we return from our method early.

Between lines 33 and 43, we are looking for the first *smallest* indentation level from the previously collected lines. We are checking to see if the first indentation level we resolved was zero and replacing it with a non-zero value.

We use the relative indentation level retrieved in the last step on lines 47-50 to populate our internal `nestedLines` property with only those immediately nested lines under our target line. This is in contrast to line 45, where we populate the `allNestedLines` internal property with all of the discovered lines, regardless of their relative depth.

That was quite a lot, but we made it through. We can now use our class like so:

Figure 11.37 

```
 1 <?php
 2 
 3 $text = <<<TEXT
 4 L01
 5     L02
 6         L03
 7         L04
 8     L05
 9 TEXT;
10 
11 
12 $indentation = new IndentationManager($text);
13 
14 $lines = $indentation->getLines();
15 $firstLine = $lines[0];
```

Which would produce a result similar to the following output (most nested properties have been removed for formatting):

Figure 11.38 IndentationManager Example Output 

```
 1 TextIndentation {
 2   line: "L01",
 3   lineNumber: 1,
 4   leadingWhitespace: 0,
 5   indentCount: 0,
 6   nestedLines: [
 7     TextIndentation {
 8       line: "    L02",
 9       lineNumber: 2,
10       leadingWhitespace: 4,
11       indentCount: 1,
12       nestedLines: [
13         TextIndentation {
14           line: "        L03",
15           lineNumber: 3,
16           leadingWhitespace: 8,
17           indentCount: 2,
18         },
19         TextIndentation {
20           line: "        L04",
21           lineNumber: 4,
22           leadingWhitespace: 8,
23           indentCount: 2,
24         },
25       ],
26       allNestedLines: [ /* L03, L04 */ ],
27     },
28     TextIndentation {
29       line: "    L05",
30       lineNumber: 5,
31       leadingWhitespace: 4,
32       indentCount: 1,
33     },
34   ],
35   allNestedLines: [ /* L02, L03, L04, L05 */ ],
36 }
```

## 12\. Applied Techniques: Writing a Gherkin Parser

While working on example concepts for a simple language parser, I encountered the article “Behavioural Driven Development in Laravel” on Laravel News^([8](#chap29.xhtml#fn-sourcelnews)). Throughout the article, there are mentions of a testing language called Gherkin.

Gherkin is an indentation-based language that allows developers to write software tests in a way that reads like a natural language, such as English or French. We will not be looking to explain how to use Gherkin to run tests but rather explore the structure of the language and write a parser in PHP that will handle it.

While we do not want to get into deep discussions on how tests written in Gherkin are eventually used, we need to look at quite a few language examples to get a sense of what we are dealing with before we start writing our parser. Let us take a look at the following code example from the Gherkin Reference^([9](#chap29.xhtml#fn-citegherkin)):

Figure 12.1 Gherkin Feature 

```
 1 Feature: Guess the word
 2 
 3   # The first example has two steps
 4   Scenario: Maker starts a game
 5     When the Maker starts a game
 6     Then the Maker waits for a Breaker to join
 7 
 8   # The second example has three steps
 9   Scenario: Breaker joins a game
10     Given the Maker has started a game with the word "silky"
11     When the Breaker joins the Maker's game
12     Then the Breaker must guess a word with 5 characters
```

We can already see a few notable things in **Figure 12.1** before we get into our parser implementation. The first thing to note is that a Gherkin file always begins with a Feature block^([10](#chap29.xhtml#fn-gherkstart)) and may contain multiple children, and we also have two other block types called Scenarios.

Gherkin uses a scenario to express a testable behavior within the feature test. Every Gherkin scenario belongs to a feature, and a scenario may have many steps.

Gherkin’s parent-child relationships are indicated by the indentation of the file. In **Figure 12.1**, we have the following program structure:

1.  Feature 
    1.  Scenario 
        1.  Step
        2.  Step
    2.  Scenario 
        1.  Step
        2.  Step
        3.  Step

The empty lines on lines two and seven can largely be ignored for our purposes. Lines three and eight contain an interesting construct we need to consider: the Gherkin comment.

Gherkin comments can appear on any line, with any number of leading whitespace, but will always start with the `#` character. These few facts will make it relatively painless for us to parse these later.

We can update our mental program structure to:

1.  Feature 
    1.  Comment
    2.  Scenario 
        1.  Step
        2.  Step
    3.  Comment
    4.  Scenario 
        1.  Step
        2.  Step
        3.  Step

The next question is whether these structures are identified exclusively by their indentation, or does Gherkin provide a different way to distinguish a scenario from a step? Continuing to peruse the documentation, we find that every non-blank line must begin with a Gherkin keyword. They call out that the exception to this rule is free-form descriptions, but we will get into that later.

The list of keywords that we need to be aware of is as follows:

Table 12.1 Gherkin Keywords

 
| Keyword || Description |
| --- | --- |
| Feature: || Provides a high-level description of a testable software feature. |
| --- | --- |
| Rule: || Provides an organizational abstraction around a single business rule to be tested. |
| Background: || Provides a way to define steps that apply to all scenarios within a Feature test suite. |
| Scenario: || Alias of Example. |
| Scenario Outline: || Used to define a Scenario/Example that can be repeated with dynamic values defined in an attached Data Table. |
| Scenario Template: || Alias of Scenario Outline. |
| Example: || An example application of a business rule. Defines some series of steps that can be used to test a behavior. |
| Examples: || A container for a Data Table that appears below a Scenario Outline. |
| Scenarios: || Alias of Examples. |
| Given || Identifies the initial state of a software system before a test is executed. |
| When || Represents a description of an action or event taken place within the software system. |
| Then || Represents a description of an expected outcome after actions are taken within a software system. |
| But || Alias of Then |
| And || Alias of And |
| \* || Repeats the last Step Keyword |

In addition to the keywords, we also need to be mindful of the following additional language constructs:

Table 12.2 Gherkin Language Constructs

 
| Construct || Description |
| --- | --- |
| Free Form Description || Optional descriptions that can appear below a Feature, Example, Scenario, Background, Scenario Outline, or Rule block. |
| --- | --- |
| Comment || A non-blank line that will not be parsed as any other Gherkin block type. |
| Doc Strings || Used to pass large pieces of text to step definition. Can be multiline, and can be defined in two different ways. |
| Data Tables || Provides a syntax to define tables of data, similar to Markdown. |
| Parameters || Parameters can be embedded in step definitions to dynamically replace data from rows defined in a Data Table. |
| Tags || Provides a way to group related Gherkin scenarios. |

The number of keywords and constructs may feel a bit overwhelming initially, especially under the guise of implementing a simple parser. However, we will cover each individually and discuss the various parsing strategies of each construct when appropriate. For now, let us continue analyzing more specific aspects of the language. The results of this analysis step will become important implementation details later.

Consider the following lines in **Figure 12.2**:

Figure 12.2 

```
1 Feature: Guess the word
2 Scenario: Maker starts a game
3 When the Breaker joins the Maker's game
```

The leading whitespace has been removed to make analyzing our text a bit simpler, but we are interested in where keywords appear and where non-keyword text appears within the lines. Our lines follow the following basic pattern:

Figure 12.3 

```
1 <KEYWORD><OTHER_TEXT>
```

For blocks such as features and scenarios (and the other similar blocks we will cover later), we can break the line up into:

*   Keyword
*   Feature/Scenario/etc. Name

For blocks that are not necessarily *structural*, like steps, we can generalize the same idea to the following:

*   Keyword
*   Text

Thinking through the main structural blocks, such as features and scenarios, and referring back to the structures described in **Figure 12.1**, we can also note that most things in Gherkin are lists of other things.

A Feature is a list of scenarios or examples. Each scenario or example is composed of a list of steps. Each scenario or example may have an associated data table, which itself contains a list of rows, and each row contains a list of cells.

Lists on lists, on lists.

### 12.1 Modeling Gherkin

Whenever I start a significant parsing or static analyzer project, I like to begin by thinking through the data model that I would like to work with at the end of the project. I find this helps to produce *valuable* objects at the end and allows me to think through the end result without getting distracted by all of the finer details and issues that always appear when implementing the parser itself. When too much of the parser’s implementation leaks through to the final data models, it generally produces a final result that feels rather difficult and unfriendly to work with.

If you take this approach on your projects, you will likely discover weaknesses and issues with your data model as you implement your parser. You may find that the way objects are related could be improved, or how you represent specific data could also change. You should not feel discouraged when this happens. As I write this section, I have the benefit of already having gone through the exercise of creating the data model, implementing the parser, and discovering these types of issues in my own implementation beforehand. You will find problems as you work through these projects; do not feel discouraged.

If we think back to our very brief introduction to the Gherkin language, we know that, for the most part, all lines will begin with a keyword and that comments can appear anywhere within a document. Additionally, we understand that each structure appears at a specific location within the document. For example, it is easier for humans to think about this in terms of lines and columns. From a software perspective, it is much easier to work with the starting offset in which the structure appears within the document. Recall that in Chapter 10, we implemented the `CharacterPositionLocator` class that can convert relative positions to their line and column numbers. This will become useful in our parser implementation.

With this information in mind, we can say that almost everything we parse could contain the following information:

*   Where the structure starts within the document,
*   Any comments that appear around the structure,
*   The keyword that identifies the type of feature

We can represent this information in PHP utilizing the following two classes. One thing to note is how our `Comment` class also extends our `Block` class, allowing it to inherit all of the properties of our generic block:

Figure 12.4 Gherkin Block and Comment Model 

```
 1 <?php
 2 
 3 class Block
 4 {
 5     /**
 6      * The start offset of the block.
 7      *
 8      * @var int
 9      */
10     public int $start;
11 
12     /**
13      * A list of all comments below the block.
14      *
15      * @var Comment[]
16      */
17     public array $comments = [];
18 
19     /**
20      * The normalized Gherkin keyword of the block..
21      *
22      * @var string
23      */
24     public string $keyword = '';
25 }
26 
27 /**
28  * Represents a Gherkin Comment.
29  *
30  * @see https://cucumber.io/docs/gherkin/reference
31  */
32 class Comment extends Block
33 {
34     /**
35      * The comment's text.
36      *
37      * @var string
38      */
39     public string $text;
40 }
```

We will continue our data modeling process and purposely go out of what may be considered a typical order. For example, we will not proceed by modeling our features or scenarios immediately, as they depend on other language structures we have not modeled yet. The list of structures that can be considered independently are:

*   Scenario Tags
*   Step Parameters
*   Doc Strings
*   Data Tables and their related models

Once we have those out of the way, we can begin composing larger structures by combing those. Additionally, utilizing this approach will allow us to briefly discuss each of these Gherkin features we did not cover in our quick introduction at the beginning of this chapter. First, let us get the most challenging construct out of the way: the data table. One thing I hope you take away from approaching the most complex construct first is that even though it appears challenging initially, we can break even the most complicated problem into elementary building blocks.

To begin, we need to see a Gherkin data table. In **Figure 12.5**, we can see that a Gherkin data table looks a lot like a Markdown table:

Figure 12.5 Example of a Gherkin Data Table 

```
1 Feature: Feature Name
2 
3   Scenario: Scenario Name
4     Given the following users exist:
5       | name   | email              |
6       | User1  | user1@example.org  |
7       | User2  | user2@example.org  |
8       | User3  | user3@example.org  |
```

Each data table row begins and ends with a vertical pipe character, which we can use to our advantage later when implementing the parser. For now, all we are concerned with this object’s actual structure. We can break a data table into the following components:

*   **Data Table**: An object containing rows of data 
    *   **Row**: An object containing cells 
        *   **Cell**: An entity containing an individual value within the table

We can represent the data table using the set of classes in **Figure 12.6**:

Figure 12.6 Gherkin Data Table Model 

```
 1 <?php
 2 
 3 class DataBlock
 4 {
 5     /**
 6      * The start offset of the block.
 7      *
 8      * @var int
 9      */
10     public int $start;
11 
12     /**
13      * The end offset of the block.
14      *
15      * @var int
16      */
17     public int $end;
18 }
19 
20 /**
21  * Represents a Gherkin DataTable
22  *
23  * Used to supplying a list of values a step definition.
24  *
25  * @see https://cucumber.io/docs/gherkin/reference/#data-tables
26  */
27 class DataTable extends DataBlock
28 {
29     /**
30      * @var TableRow[]
31      */
32     public array $rows = [];
33 }
34 
35 /**
36  * Represents a single row in a DataTable.
37  */
38 class TableRow extends Block
39 {
40     /**
41      * @var TableCell[]
42      */
43     public array $cells = [];
44 }
45 
46 /**
47  * Holds a single cell value in a TableRow.
48  */
49 class TableCell extends Block
50 {
51     public function __construct(public string $value)
52     { }
53 }
```

You will notice that we also defined a new base class: `DataBlock`. We will use this base class for data tables and doc strings since those structures can span multiple lines. We are not using those for other constructs, such as features or scenarios, since most sub-components can be located on a single line within the document.

Let us now look at two examples of doc strings and create the model for them next. In Gherkin, we can declare a doc string by having three consecutive double-quotes, or three consecutive backticks on their own lines, surrounding the contents of the doc string:

Figure 12.7 

```
 1 Feature: Feature Name
 2 
 3   Scenario: Doc String Example One
 4     Given a blog post named "Random" with Markdown body
 5       """
 6       Some Title, Eh?
 7       ===============
 8       Here is the first paragraph of my blog post. Lorem ipsum dolor
 9       consectetur adipiscing elit.
10       """
11 
12   Scenario: Doc String Example Twoc
13     Given a blog post named "Random" with Markdown body
14       '''
15       Some Title, Eh?
16       ===============
17       Here is the first paragraph of my blog post. Lorem ipsum dolor
18       consectetur adipiscing elit.
19       '''
```

Like our data table, a doc string starts at some location and can span multiple lines. There are two pieces of information that could be useful to whoever is working with the models our parser returns:

*   **Content**: The actual content of the doc string
*   **Delimiter**: Whether the doc string was created using double-quotes or backticks

We can model this like so:

Figure 12.8 Gherkin DocString Model 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin DocString
 5  *
 6  * Can start with """ or ```
 7  *
 8  * @see https://cucumber.io/docs/gherkin/reference/#doc-strings
 9  */
10 class DocString extends DataBlock
11 {
12     public string $content = '';
13     public string $delimiter = '';
14 }
```

The next structure to create a model for will be the tags that can be associated with scenarios. **Figure 12.9** showcases how tags may appear within a Gherkin document:

Figure 12.9 Gherkin Tag Example 

```
1 Feature: Feature Name
2 
3   @tagOne @tagTwo @tagThree
4   Scenario: Doc String Example One
5     Given a blog post named "Random" with Markdown body
```

We only really need to keep track of the content of the tag, which we can do using the following PHP class:

Figure 12.10 Modeling Gherkin Tags 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin Scenario Tag
 5  *
 6  * Scenario tags are defined as @tag @tag2, etc.
 7  */
 8 class Tag extends Block
 9 {
10     /**
11      * The name of the tag.
12      *
13      * @var string
14      */
15     public string $name;
16 }
```

Gherkin step parameters will be modeled similarly to the tags, but they appear within the document as part of the step’s text:

Figure 12.11 Gherkin Step Parameter Example 

```
1 Feature: Feature Name
2 
3   Scenario Outline: eating
4     Given there are <start> cucumbers
5     When I eat <eat> cucumbers
6     Then I should have <left> cucumbers
```

Our step parameter model will be similar to our tag model:

Figure 12.12 Modeling Gherkin Step Parameters 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin Step Parameter.
 5  *
 6  * Step parameters a defined as <param> <param2>, etc.
 7  *
 8  * @see https://cucumber.io/docs/gherkin/reference/#step-parameters
 9  */
10 class Parameter extends Block
11 {
12     /**
13      * The name of the parameter.
14      *
15      * @var string
16      */
17     public string $name;
18 }
```

The next Gherkin construct to add to our model will be the individual steps. From what we’ve seen so far, we know that a step can contain the following information:

*   **Text**: The actual text of the step
*   **Data Table**: A list of additional data for the step
*   **Doc String**: A multi-line string that is added to the end of the step’s parameter list
*   **Parameters**: A list of parameters that can be defined within the step’s text using angle brackets

Luckily for us, we have already modeled all of the extra information that can appear within a step and can now create our first model object that is composed of other entities:

Figure 12.13 Modeling Gherkin Steps 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin Scenario Step
 5  *
 6  * @see https://cucumber.io/docs/gherkin/reference/#steps
 7  */
 8 class Step extends Block
 9 {
10     /**
11      * The step's instructions, or text.
12      *
13      * @var string
14      */
15     public string $text;
16 
17     /**
18      * The list of data blocks for the step.
19      *
20      * May include a DocString or DataTable.
21      *
22      * @var DataBlock[]
23      */
24     public array $data = [];
25 
26     /**
27      * A list of parameters for the step.
28      *
29      * @var Parameter[]
30      */
31     public array $parameters = [];
32 }
```

Notice how our `$data` array is type-hinted to directly use the generic `DataBlock` class instead of the `DataTable` or `DocString` classes. This provides a place to store both data types; anyone consuming our model can check the class type to make decisions.

The next Gherkin construct to create a data model for will be the Examples block. These blocks appear within a scenario outline and contain a data table that can be used to supply data to a given test scenario:

Figure 12.14 Gherkin Examples Block 

```
1 Scenario Outline: eating
2   Given there are <start> cucumbers
3   When I eat <eat> cucumbers
4   Then I should have <left> cucumbers
5 
6   Examples:
7     | start | eat | left |
8     |    12 |   5 |    7 |
9     |    20 |   5 |   15 |
```

Modeling this in PHP is straightforward, as we just need a way to store a `DataTable` instance. We are making this nullable to account for incomplete documents:

Figure 12.15 Modeling Gherkin Examples 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Scenario Outline's Examples.
 5  */
 6 class Examples extends Block
 7 {
 8     /**
 9      * The Example's DataTable.
10      *
11      * @var DataTable|null
12      */
13     public ?DataTable $table;
14 }
```

As you can see, our new PHP classes are beginning to comprise more and more other PHP classes. **Figure 12.16** shows an example of a Gherkin scenario, with many steps:

Figure 12.16 Gherkin Scenario Example 

```
1 Feature: Feature Name
2 
3   Scenario: All done
4     Given I am out shopping
5     And I have eggs
6     And I have milk
7     And I have butter
8     When I check my list
9     Then I don't need anything
```

We can model a Gherkin scenario by creating a new PHP class that contains a field for its text, as well as all of the various objects it can include:

Figure 12.17 Modeling Gherkin Scenarios 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin Scenario
 5  *
 6  * @see https://cucumber.io/docs/gherkin/reference/#example
 7  */
 8 class Scenario extends Block
 9 {
10     /**
11      * The free-form description of the scenario.
12      *
13      * @var string
14      */
15     public string $description;
16 
17     /**
18      * The name of the scenario.
19      *
20      * @var string
21      */
22     public string $name;
23 
24     /**
25      * The list of steps for the scenario.
26      *
27      * @var Step[]
28      */
29     public array $steps = [];
30 
31     /**
32      * Any DataTable examples for the scenario.
33      *
34      * @var Examples[]
35      */
36     public array $examples = [];
37 
38     /**
39      * The tags for the scenario.
40      *
41      * @var Tag[]
42      */
43     public array $tags = [];
44 }
```

Gherkin contains several other constructs that are very similar to Scenarios structurally. These structures include:

*   **Background**: Used to represent a set of common steps across all scenarios in a feature.
*   **Scenario Outline**: Used to run the same Gherkin test scenario multiple times with different values.
*   **Rule**: Groups several scenarios together within a feature. Conceptually similar to tags, but represents a business rule rather than a way to organize scenarios.

**Figure 12.18** contains an example of a Gherkin background block:

Figure 12.18 

```
1 Feature: Multiple site support
2   Only blog owners can post to a blog, except administrators,
3   who can post to all blogs.
4 
5   Background:
6     Given a global administrator named "Greg"
7     And a blog named "Greg's anti-tax rants"
8     And a customer named "Dr. Bill"
9     And a blog named "Expensive Therapy" owned by "Dr. Bill"
```

**Figure 12.19** shows an example of a Gherkin scenario outline block:

Figure 12.19 

```
 1 Feature: Feature Name
 2 
 3   Scenario Outline: eating
 4     Given there are <start> cucumbers
 5     When I eat <eat> cucumbers
 6     Then I should have <left> cucumbers
 7 
 8     Examples:
 9         | start | eat | left |
10         |    12 |   5 |    7 |
11         |    20 |   5 |   15 |
```

Because both of these block types contain largely the same information as a scenario, we can simply extend our Scenario class like so:

Figure 12.20 Modeling Gherkin Scenario Outline and Background 

```
 1 <?php
 2 
 3 /**
 4  * Represents a Gherkin Scenario Outline
 5  *
 6  * @see https://cucumber.io/docs/gherkin/reference/#scenario-outline
 7  */
 8 class ScenarioOutline extends Scenario
 9 {
10 
11 }
12 
13 /**
14  * Represents a Gherkin Background
15  *
16  * @see https://cucumber.io/docs/gherkin/reference/#background
17  */
18 class Background extends Scenario
19 {
20 
21 }
```

We can produce a high-level visualization of our data model to help our understanding of how all the pieces are fitting together:

![](images/gherkin_relationships.png)

What we have done through creating representations of all of the Gherkin structures we want to parse and their relationships is to produce an abstract syntax tree definition. Our input Gherkin program, through our parser, will be converted into a tree of objects representing our feature test suite. I did not open this section with the phrase “abstract syntax tree” because sometimes, approaching things with difficult-sounding names can preemptively make things more difficult cognitively than they need to be.

With our data model in place, we can begin working on our Gherkin parser implementation.

### 12.2 A Gherkin Lexer

A lexer is an interesting topic when parsing text, as it can often be confused with the parser itself. If we look at the Gherkin example in **Figure 12.21**, we can see that there are a lot of individual characters and words, and it may be difficult to even figure out where we should start parsing this:

Figure 12.21 An Example Gherkin Program 

```
 1 Feature: Overdue tasks
 2   Let users know when tasks are overdue, even when using other
 3   features of the app
 4 
 5   Rule: Users are notified about overdue tasks on first use of the day
 6     Background:
 7       Given I have overdue tasks
 8 
 9     Example: First use of the day
10       Given I last used the app yesterday
11       When I use the app
12       Then I am notified about overdue tasks
```

Operating directly on individual characters or entire words can be complicated from a parser’s perspective. It would be much more helpful if we could work on a higher-level structure instead. This is where a lexer comes in.

Because Gherkin is an indentation-based language, we could be much more productive implementing our parse if we could operate on entire lines. Additionally, if we already knew the relative indentation and the relationship between the lines, that would accelerate the development of our parser even further. This is in contrast to other languages, where combining the lexing and parsing phases into a single step may make sense.

If you recall, at the end of Chapter 11, we created an `IndentationManager` class capable of breaking apart a piece of text into a list of `TextIndentation` objects with the relative indentation information stored. We can actually use this as the lexer for our Gherkin parser!

To help illustrate this, consider **Figure 12.22**, where we pass a simple Gherkin program to our `IndentationManager` instance:

Figure 12.22 

```
 1 <?php
 2 
 3 $text = <<<GHERKIN
 4 Feature: Feature Name
 5 
 6   Scenario Outline: eating
 7     Given there are <start> cucumbers
 8 GHERKIN;
 9 
10 
11 $indentation = new IndentationManager($text, 2);
12 $lines = $indentation->getLines();
```

If we were to inspect the results, we would find something similar to the following:

Figure 12.23 

```
 1 array:4 [
 2   0 => TextIndentation {
 3     line: "Feature: Feature Name"
 4     lineNumber: 1
 5     leadingWhitespace: 0
 6     indentCount: 0
 7     nestedLines: array:1 [
 8       0 => TextIndentation {
 9         line: "  Scenario Outline: eating"
10         lineNumber: 3
11         leadingWhitespace: 2
12         indentCount: 1
13         nestedLines: array:1 [
14           0 => TextIndentation {
15             line: "    Given there are <start> cucumbers"
16             lineNumber: 4
17             leadingWhitespace: 4
18             indentCount: 2
19             nestedLines: []
20             allNestedLines: []
21           }
22         ]
23         allNestedLines: array:1 [
24           // Line 3
25         ]
26       }
27     ]
28     allNestedLines: array:3 [
29       // Line 1
30       // Line 2
31       // Line 3
32     ]
33   }
34 ]
```

Looking through the results of using our `IndentationManager`, we already have most of the structure of our Gherkin program resolved for us since it is indentation-based. Each line within the document is represented by a `TextIndentation` instance. Each of these line instances already has all of its descendants already associated with it for us, which lets us simply check for specific keywords and other structural indicators when implementing our parser.

### 12.3 Implementing Our Gherkin Parser

Our existing `IndentationManager` class will help us quite a bit to implement our Gherkin parser, but there is still a lot for us to do. Don’t worry; like with the data modeling, we will work through each section one at a time and discuss what we are doing along the way. We should first address the hidden complexity of Gherkin’s keywords.

At the beginning of this chapter, we briefly mentioned that Gherkin can be localized in several different languages. Gherkin has been translated into over seventy languages, including English and Norwegian. We can find the following example from their documentation:

Figure 12.24 Localized Gherkin Example 

```
 1 Funksjonalitet: Gjett et ord
 2 
 3   Eksempel: Ordmaker starter et spill
 4     Når Ordmaker starter et spill
 5     Så må Ordmaker vente på at Gjetter blir med
 6 
 7   Eksempel: Gjetter blir med
 8     Gitt at Ordmaker har startet et spill med ordet "bløtt"
 9     Når Gjetter blir med på Ordmakers spill
10     Så må Gjetter gjette et ord på 5 bokstaver
```

This presents a particularly interesting challenge to us working to implement a parser: we cannot rely on the keywords directly when looking for different Gherkin features. Instead, we will have to rely on an internal mapping of localized keywords to a known set of keywords our parser can use. Sometimes it can be challenging to determine where we should start implementing a parser, but this seems like an excellent place to start.

Let us examine **Figure 12.25** where we begin our parser implementation:

Figure 12.25 Defining our Gherkin Keywords 

```
 1 <?php
 2 
 3 class GherkinParser
 4 {
 5 
 6     /**
 7      * @var CharacterPositionLocator
 8      */
 9     protected CharacterPositionLocator $locator;
10 
11     /**
12      * The list of keywords that can be used to start a new block.
13      *
14      * @var string[]
15      */
16     protected array $gherkinKeywords = [
17         'feature' => 'Feature:',
18         'rule' => 'Rule:',
19         'background' => 'Background:',
20         'scenario' => 'Scenario:',
21         'scenario_outline' => 'Scenario Outline:',
22         'scenario_template' => 'Scenario Template:',
23         'example' => 'Example:',
24         'examples' => 'Examples:',
25         'scenarios' => 'Scenarios:',
26     ];
27 
28     /**
29      * The list of keywords that can be used to start a new step.
30      *
31      * @var string[]
32      */
33     protected array $stepKeywords = [
34         'given' => 'Given ',
35         'when' => 'When ',
36         'then' => 'Then ',
37         'and' => 'And ',
38         'but' => 'But ',
39         '*' => '* ',
40     ];
41 }
```

Between lines 16 and 26, we are creating a mapping between a set of internal keywords and the different types of structural elements we have discussed previously. Similarly, between lines 33 and 40, we are mapping a set of internal keywords to the various keywords that would indicate the start of a Gherkin step.

Our next step will be to write the initial version of a `parse` method. Developers using our parser can call `parse` to convert their Gherkin program into the data models we defined previously. For now, our `parse` method is only concerned with performing house-cleaning tasks and setting up additional internal variables for us to use.

Figure 12.26 Scaffolding the Parse Method 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses the provided Gherkin text.
12      *
13      * @param string $value The string to parse.
14      * @param int $tabSize The tab size.
15      * @return Feature|null
16      */
17     public function parse(string $value, int $tabSize = 2): ?Feature
18     {
19         $value = Str::normalizeEol($value);
20         $this->locator = new CharacterPositionLocator($value);
21 
22         $indentationManager = new IndentationManager($value, $tabSize);
23         $lines = $indentationManager->getLines();
24 
25         return null;
26     }
27 
28     // ...
29 }
```

On line 17, we are making a call to the `normalizeEol` helper method we created in a previous chapter. We are doing this so we can assume a consistent line ending style when working with our input text. After this, we create a new instance of the `CharacterPositionLocator` class we also created; we will use this in the first supporting method we implement together.

Lines 20-21 create a new `IndentationManager` instance and fetch the strings with their indentation information. This is where we will kick off the main parsing sequence later on, but we are not quite ready for that.

If you remember, from our discussion surrounding the Gherkin lexer, we talked about how we would use our indentation manager to provide information to our parser. Additionally, when we modeled our Gherkin structures, one of the pieces of data we wanted to store with all of the objects we created was their position within the document.

The parsing methods we will implement throughout this section will almost always receive an instance of `TextIndentation` from the indentation manager. We can use the information that is already provided by that and our local `CharacterPositionLocator` instance we created in **Figure 12.26** to implement a supporting `lineToPosition` method:

Figure 12.27 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Returns the position of the provided line.
12      *
13      * @param TextIndentation $line The line.
14      * @return int
15      */
16     protected function lineToPosition(TextIndentation $line): int
17     {
18         return $this->locator->getCharPositionFromLineColumn(
19             $line->lineNumber, $line->leadingWhitespace + 1
20         );
21     }
22 
23     // ...
24 }
```

We will frequently use this method throughout our parser’s implementation. As you can see, it simply asks our position locator to return the offset of provided text indentation line based on its line number. We are using the total amount of leading whitespace as the column number.

You may have noticed that we are added one to the leading whitespace value. We are doing this because if a line has *no* leading whitespace, its value will be zero, which is not a valid one-based column position for our locator class.

#### Parsing Gherkin Comments

To ease into implementing more nuanced parsing methods, let us start with one of the simpler constructs we can parse: the Gherkin comment. **Figure 12.28** provides an example of a Gherkin comment:

Figure 12.28 Gherkin Comment Example 

```
1 # I am a comment.
```

Remember that we are parsing the location manager’s results, not the text directly. The previous comment would result in the following text indentation object:

Figure 12.29 

```
 1 TextIndentation {
 2   line: "# I am a comment."
 3   lineNumber: 1
 4   leadingWhitespace: 0
 5   indentCount: 0
 6   nestedLines: array:1 [
 7     0 => TextIndentation {
 8       line: ""
 9       lineNumber: 2
10       leadingWhitespace: 0
11       indentCount: 0
12       nestedLines: []
13       allNestedLines: []
14     }
15   ]
16 }
```

The information we want to parse is contained within the line property, but it would be more useful if we didn’t have the leading `#` character in the `Comment` class we want to create. From our earlier discussions surrounding the Laravel string helper methods, we know we can do this by constructing a substring starting at the first character and then trimming the result:

Figure 12.30 Parsing Gherkin Comments 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses an individual Gherkin comment.
12      *
13      * @param TextIndentation $line The line to parse.
14      * @return Comment
15      */
16     protected function parseComment(TextIndentation $line): Comment
17     {
18         $comment = new Comment();
19         $comment->start = $this->lineToPosition($line);
20         $comment->text = (string) str($line->line)->substr(1)->trim;
21 
22         return $comment;
23     }
24 
25     // ...
26 }
```

Our method would parse our example line into the following `Comment` data object:

Figure 12.31 

```
1 Comment {
2   start: 1
3   comments: []
4   keyword: ""
5   text: "I am a comment."
6 }
```

The parser method is producing the expected result, but it currently is not super helpful since it already expects an indentation line instance. Let’s consider the following example containing multiple Gherkin comments:

Figure 12.32 Gherkin Multiple Comments Example 

```
1 # I am a comment.
2 # I am another comment.
3 # Yet another comment.
```

We know that our indentation manager will return an array of indentation line objects, and we can take advantage of this to detect our comments and then run them through our parsing method:

Figure 12.33 Parsing Multiple Gherkin Comments 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Retrieves all Gherkin comments from the provided lines.
12      *
13      * @param TextIndentation[] $lines The lines to parse.
14      * @return Comment[]
15      */
16     protected function parseComments(array $lines): array
17     {
18         $comments = [];
19 
20         foreach ($lines as $line) {
21             if (str($line->line)->trim->startsWith('#')) {
22                 $comments[] = $this->parseComment($line);
23             }
24         }
25 
26         return $comments;
27     }
28 
29     // ...
30 }
```

We are seeing some more tricky things, but things are still relatively simple. Our `parseComments` method is looping through all of the lines and checking to see if they start with the “#” character. If they do, we pass the line into the `parseComment` method we just developed.

Executing this method on our list of multiple comments would produce the following list of `Comment` data objects:

Figure 12.34 

```
 1 array:3 [
 2   0 => Comment {
 3     start: 0
 4     comments: []
 5     keyword: ""
 6     text: "I am a comment."
 7   }
 8   1 => Comment {
 9     start: 19
10     comments: []
11     keyword: ""
12     text: "I am another comment."
13   }
14   2 => Comment {
15     start: 44
16     comments: []
17     keyword: ""
18     text: "Yet another comment."
19   }
20 ]
```

We now have two methods that can be used to parse comments from a list of indentation lines. We are currently not concerned with where those lines come from and will get to that in future sections. However, we can congratulate ourselves since we have officially started our parser implementation!

#### Parsing Names

Many Gherkin structures, such as features and scenarios, contain a name. We will focus on features for this section, but the method we develop will apply to all Gherkin structures with names. Let us consider the following example line:

Figure 12.35 Gherkin Feature Example 

```
1 Feature: The feature name
```

The piece of text we want to extract from our line is “The feature name.” We can do this relatively simply if we remove the “Feature: “ part at the beginning. Our name parsing method could be implemented like so:

Figure 12.36 Parsing Gherkin Feature Names 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a name for various blocks, such as the Feature name.
12      *
13      * @param TextIndentation $line The line to parse.
14      * @param string $keyword The original keyword.
15      * @return string
16      */
17     protected function parseName(
18         TextIndentation $line,
19         string $keyword
20     ): string
21     {
22         return (string) str($line->line)
23             ->trim->substr(strlen($this->gherkinKeywords[$keyword]))
24             ->trim;
25     }
26 
27     // ...
28 }
```

Internally, our method will be called using our standardized keyword names, such as feature, scenario, or rule. We look up the localized version of the keyword and use its length to produce a substring, trimming all of the results along the way.

Our parsing method would return “The feature name” from our sample input in **Figure 12.35**, which is exactly what we need later on in our parser.

#### Parsing Step Text

Each Gherkin step begins with a step keyword, followed by some text:

Figure 12.37 Gherkin Step Example 

```
1 When the Maker starts a game
```

Our strategy for parsing this will be very similar to our process for parsing the names of features. We can do this using the following PHP method:

Figure 12.38 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Returns the instruction text for a Gherkin Step.
12      *
13      * @param TextIndentation $stepLine The line to parse.
14      * @param string $keyword The original keyword.
15      * @return string
16      */
17     protected function parseStepText(
18         TextIndentation $stepLine,
19         string $keyword): string
20     {
21         $content = (string) str($stepLine->line)->ltrim;
22 
23         $stepText = str($content)->after($keyword);
24 
25         return (string) str($stepText)->trim;
26     }
27 
28     // ...
29 }
```

Given any line, we also need a method that will be able to tell us which step keyword is being used on that line:

Figure 12.39 Parsing Gherkin Step Keywords 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Returns the keyword for a Gherkin Step.
12      *
13      * @param TextIndentation $stepLine The line to parse.
14      * @return array
15      * @throws Exception
16      */
17     protected function parseStepKeyword(
18         TextIndentation $stepLine
19     ): array
20     {
21         $content = (string) str($stepLine->line)->ltrim;
22 
23         foreach ($this->stepKeywords as $name => $keyword) {
24             if (str($content)->startsWith($keyword)) {
25                 return [$name, $keyword];
26             }
27         }
28 
29         throw new \Exception('Invalid step keyword');
30     }
31 
32     // ...
33 }
```

You will notice that our `parseStepKeyword` is returning both the internal and localized keyword versions. We will later supply this localized version to our `parseStepText` method.

#### Parsing Free-Form Gherkin Descriptions

Gherkin supports the concept of free-form descriptions, which can be added to features, scenarios, backgrounds, scenario outlines, and rules. These descriptions are indented below the Gherkin construct they belong to, just like anything else, and can contain any content as long as the lines do not start with any Gherkin keyword. **Figure 12.40** provides an example of a Gherkin description:

Figure 12.40 Gherkin Free-Form Description Example 

```
1 Feature: Guess the word
2 
3   The word guess game is a turn-based game for two players.
4   The Maker makes a word for the Breaker to guess. The game
5   is over when the Breaker guesses the Maker's word.
```

The basic process for parsing free-form descriptions will be to iterate our indentation lines and check if they begin with a Gherkin keyword. We will continue adding their content to our description if they do not start with a keyword. As soon as we encounter a Gherkin keyword, we need to stop parsing our description, as that line indicates the start of another feature.

Our PHP methods to do this may look like those provided in **Figure 12.41**:

Figure 12.41 Parsing Gherkin Descriptions 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Tests if the provided line begins with any Gherkin keyword.
12      *
13      * @param string $line The line to test.
14      * @return bool
15      */
16     protected function startsWithKeyword(string $line): bool
17     {
18         $content = str($line)->ltrim;
19 
20         return $content->startsWith($this->stepKeywords) ||
21                $content->startsWith($this->gherkinKeywords) ||
22                $content->startsWith('@');
23     }
24 
25     /**
26      * Parses a free-form Gherkin description.
27      *
28      * @param TextIndentation[] $lines The lines to parse.
29      * @return string
30      */
31     protected function parseDescription(array $lines): string
32     {
33         if (count($lines) == 0) { return ''; }
34         $description = [];
35 
36         for ($i = 0; $i < count($lines); $i++) {
37             $cur = $lines[$i];
38 
39             // We will stop looking for free-form
40             // description text when we encounter
41             // a line that starts with a keyword.
42             if (str($cur->line)->trim->length == 0  ||
43                 $this->startsWithKeyword($cur->line)) {
44                 break;
45             }
46 
47             if ($cur->indentCount > 0) {
48                 $description[] = (string) str($cur->line)->ltrim;
49                 continue;
50             }
51 
52             break;
53         }
54 
55         return (string) str(implode(' ', $description))
56             ->squish();
57     }
58 
59     // ...
60 }
```

The `startsWithKeyword` method in **Figure 12.41** checks if the provided text starts with any of our step or structural keywords or with the `@` character. We have included the `@` symbol in this list to be able detect scenario tags later.

Our `parseDescription` method iterates all of the provided lines. Between lines 42 and 44, we check if the line begins with any of Gherkin’s reserved keywords. If it does, we break out of our loop early. Lines 47-49 will add the contents of the current line to our `$description` array if the indent level is greater than zero; we are doing this as an easy way to filter out blank lines.

The final step of our method is to combine the individual lines of our description and remove all of the extraneous whitespace using Laravel’s `squish` method.

This technique would convert the following description lines:

Figure 12.42 

```
1   Line one.
2     Line two.
3        Line three.
```

To:

Figure 12.43 

```
1 Line one. Line two. Line three.
```

#### Parsing Scenario Tags

As we saw in this chapter’s beginning, Gherkin supports adding various tags to scenarios. **Figure 12.44** demonstrates how tags may be added to a scenario to organize them:

Figure 12.44 Gherkin Scenario Tag Example 

```
1 Feature: Feature Name
2 
3   @tagOne @tagTwo @tagThree
4   Scenario: Doc String Example One
5     Given a blog post named "Random" with Markdown body
```

Our strategy to get these lines into a list of `Tag` objects will be relatively straightforward. The basic process will be to split our input string into an array on the `@` symbol. Once we have the list of tags, we can then filter out empty strings and create our `Tag` instances:

Figure 12.45 Parsing Gherkin Scenario Tags 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses Scenario Tags.
12      *
13      * @param TextIndentation $tagLine The tag line.
14      * @return array
15      */
16     protected function parseTags(TextIndentation $tagLine): array
17     {
18         $tags = [];
19 
20         $tagLineContent = str($tagLine->line)->ltrim;
21 
22         // Splits the string into an array on the "@"
23         // character. The string "@tag1 @tag2" will
24         // become ["tag1", "tag2"].
25         $tagNames = $tagLineContent->split('/@/');
26 
27         foreach ($tagNames as $tagName) {
28             if (empty($tagName)) {
29                 continue;
30             }
31 
32             $tag = new Tag();
33             $tag->name = (string) str($tagName)->trim;
34             $tag->start = $this->lineToPosition($tagLine);
35 
36             $tags[] = $tag;
37         }
38 
39         return $tags;
40     }
41 
42     // ...
43 }
```

If we refer back to **Figure 12.44**, we will notice an exciting challenge to overcome. The line containing our tags will become before the line containing our scenario keyword. We could resolve this by keeping track of which lines we’ve already seen and “remembering” that we encountered a line that includes tags. For our implementation, this seems overly complex, and an alternative technique would be to look at the previous line when we encounter a scenario.

When we encounter a line that contains the scenario keyword, we will look back at the previous line to see if it begins with the `@` symbol. If so, we will parse the previous line using our `parseTags` method. The method to look backward is:

Figure 12.46 Scanning Backwards to Locate Scenario Tags 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Searches a list of lines in reverse for a
12      * line that begins with the tag keyword (@).
13      *
14      * This method will stop searching if the
15      * line immediately before the current
16      * line is not a tag line.
17      *
18      * @param TextIndentation[] $lines The lines to search.
19      * @param int $i The current line index.
20      * @return TextIndentation|null
21      */
22     protected function getTagsLine(
23         array $lines,
24         int $i): ?TextIndentation
25     {
26         $tagLine = null;
27 
28         if ($i > 0) {
29             $prev = $lines[$i - 1];
30             $prevContent = str($prev->line)->ltrim;
31 
32             if ($prevContent->startsWith('@')) {
33                 $tagLine =  $prev;
34             }
35         }
36 
37         return $tagLine;
38     }
39 
40     // ...
41 }
```

We have been developing several supporting methods to help implement our parser but have not yet quite gotten around to implementing the central part of the parser. We will get to that in due time, as we still have many Gherkin features to parse before we can parse our large structures, such as features and scenarios. An important thing to remember while we work through this chapter is that we are effectively approaching this process in reverse, as it helps aid the discussion process. For a more “real” look at how this was implemented while preparing this chapter, you could start at the last section and work backward.

#### Parsing Step Parameters

In this section, we will work to implement our method to parse step parameters. If you recall from the beginning of this chapter, step parameters are defined within the text of a step using angle brackets:

Figure 12.47 Example of Gherkin Step Parameters 

```
1 Feature: Feature Name
2 
3   Scenario Outline: eating
4     Given there are <start> cucumbers
5     When I eat <eat> cucumbers
6     Then I should have <left> cucumbers
```

Our process will be to extract these from our text by using a regular expression and PHP’s `preg_match_all` function. Once we have all of the matches from our regular expression, we will iterate them all and return an array of `Tag` instances:

Figure 12.48 Parsing Gherkin Step Parameters 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses step parameters from a step line.
12      *
13      * @param TextIndentation $stepLine The line to parse.
14      * @return array
15      */
16     protected function parseStepParameters(
17         TextIndentation $stepLine
18     ): array
19     {
20         // Matches all parameters in the step line.
21         // For example, if the step line is:
22         // Then I should have <left> cucumbers
23         // This will match "<left>".
24         preg_match_all(
25             '/<([^>]+)>/u',
26             $stepLine->line,
27             $matches,
28             PREG_OFFSET_CAPTURE)
29         ;
30 
31         // Iterate all of our matches and
32         // create new Parameter instances.
33         return collect($matches[1])
34             ->map(function ($match) use ($stepLine) {
35                 $parameter = new Parameter();
36 
37                 // Add the relative position of our parameter.
38                 $parameter->start =
39                     $this->lineToPosition($stepLine) + $match[1];
40 
41                 $parameter->name = $match[0];
42 
43                 return $parameter;
44             })->all();
45     }
46 
47     // ...
48 }
```

We use Laravel’s collection features to iterate our matches and construct our final tag’s array instead of a normal foreach loop.

#### Parsing Doc Strings

We will begin parsing some more complicated structures, starting with Gherkin’s doc strings. Let us familiarize ourselves again with the doc string syntax:

Figure 12.49 Gherkin Doc Strings 

```
 1 Feature: Feature Name
 2 
 3   Scenario: Doc String Example One
 4     Given a blog post named "Random" with Markdown body
 5       """
 6       Some Title, Eh?
 7       ===============
 8       Here is the first paragraph of my blog post. Lorem ipsum dolor
 9       consectetur adipiscing elit.
10       """
```

The strategy for parsing doc strings will be similar to our free-form descriptions. The basic method will be to scan each line and check to see if its starts with one of the two character sequences that indicate the start of a doc string:

*   Three double-quotes, or
*   Three backticks

We will also need to remember which one of the two sequences we saw, as we need to stop parsing our doc string when we see it again. Our implementation for parsing doc strings is as follows:

Figure 12.50 Parsing Gherkin Doc Strings 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Ghrekin DocString.
12      *
13      * @param TextIndentation $docStringLine The line to parse.
14      * @param TextIndentation[] $lines The lines to parse.
15      * @return DocString
16      */
17     protected function parseDocString(
18         TextIndentation $docStringLine,
19         array $lines
20     ): DocString
21     {
22         $docString = new DocString();
23 
24         $docString->start = $this->lineToPosition($docStringLine);
25         $content = (string) str($docStringLine->line)->ltrim;
26 
27         if (str($content)->startsWith('"""')) {
28             $docString->delimiter = '"""';
29         } else {
30             $docString->delimiter = '```';
31         }
32 
33         $contentLines = [];
34 
35         foreach ($lines as $line) {
36             if ($line->lineNumber <= $docStringLine->lineNumber) {
37                 continue;
38             }
39 
40             $trimmedLine = str($line->line)->ltrim;
41 
42             if ($trimmedLine->startsWith($docString->delimiter) &&
43                 $line->leadingWhitespace ==
44                     $docStringLine->leadingWhitespace) {
45 
46                 $docString->end = $this->lineToPosition($line);
47                 break;
48             }
49 
50             $contentLines[] = $line->line;
51         }
52 
53         // Remove the leading whitespace from each line.
54         $docString->content = collect($contentLines)
55             ->map(function ($line) use ($docStringLine) {
56 
57             return (string) str($line)->substr(
58                 $docStringLine->leadingWhitespace
59             );
60 
61         })->implode("\n");
62 
63         return $docString;
64     }
65 
66     // ...
67 }
```

We are “remembering” which delimiter we encountered earlier on between lines 27 and 31 and storing it within our new `DocString` instance we created on line 22.

Our doc string parsing method will eventually receive all the lines that are part of the document when the initial doc string sequence is discovered. Because of this, we need to check if the lines we are iterating come before the line that initiated the doc string parsing method. We do this on lines 36 through 38.

We have implemented a rather interesting check between lines 42 and 47. Let us consider the following example input to help explain what this check is guarding against:

Figure 12.51 

```
 1 Feature: Feature Name
 2 
 3   Scenario: Doc String Example One
 4     Given a blog post named "Random" with Markdown body
 5       """
 6       Some Title, Eh?
 7       ===============
 8       Here is the first paragraph of my blog post. Lorem ipsum dolor
 9       consectetur adipiscing elit.
10         """
11       """
```

On line 10 of **Figure 12.51**, we can see that the doc string delimiter appears but is more indented than the original delimiter discovered on line 5. Our checks between lines 42 and 47 accounts for this scenario.

One of the last things we do before returning our `DocString` instance is to remove the relative leading whitespace from all content lines and then join them with the newline character. This happens between lines 54 and 61. Removing the relative leading whitespace would have the effect of transforming the following set of lines:

Figure 12.52 

```
1       Line One
2       ============
3       Line Two
4          Line Three
5              Line Four
6 
7       Line Five
```

Into:

Figure 12.53 

```
1 Line One
2 ============
3 Line Two
4     Line Three
5         Line Four
6 
7 Line Five
```

Notice how the relative indentation was preserved on lines 4 and 5 in **Figure 12.53**.

#### Parsing Gherkin Data Tables

We will now work to parse Gherkin data tables, which will be the most substantial structure we’ve parsed and is, in some ways, the most difficult to parse out of all of the different Gherkin elements. A Gherkin data table looks similar to a Markdown table, and each line starts and ends with a vertical pipe character, with each column also separated by a pipe character:

Figure 12.54 Gherkin Data Table Example 

```
 1 Feature: Feature Name
 2 
 3   Scenario Outline: eating
 4     Given there are <start> cucumbers
 5     When I eat <eat> cucumbers
 6     Then I should have <left> cucumbers
 7 
 8     Examples:
 9         | start | eat | left |
10         |    12 |   5 |    7 |
11         |    20 |   5 |   15 |
```

Like with doc strings and free-form descriptions, we will want to gather all of the lines that should be part of our data table. For data tables, this will be all lines that begin with the “|” symbol. Once we have the individual lines for our data table, we will then need to parse each line into a list of `TableCell` objects, which can then be stored on a `TableRow` object.

If we take a look at a single row:

Figure 12.55 

```
1 |    12 |   5 |    7 |
```

We can see that there are three distinct values we need to extract:

*   12
*   5
*   7

The basic process will be to split our line on the vertical pipe character, but only if it is not preceded by a backslash character. This is because Gherkin allows for the following escape sequences when defining cell values:

Table 12.3 Gherkin Data Table Cell Escape Sequences

 
| Escape Sequence || Description |
| --- | --- |
| \\| || Escapes the vertical pipe character. |
| --- | --- |
| \\n || Produces a newline within the cell contents. |
| \\\\ || Escapes the backslash, producing a single backslash in the cell contents. |

Like step parameters, we can accomplish this with a relatively simple regular expression. The following implementation may seem like a lot, but each individual method is handling its own individual step:

Figure 12.56 Parsing Gherkin Data Tables 

```
  1 <?php
  2 
  3 use Illuminate\Support\Str;
  4 
  5 class GherkinParser
  6 {
  7 
  8     // ...
  9 
 10     /**
 11      * Parses a Gherkin DataTable.
 12      *
 13      * @param TextIndentation $tableLine The line to parse.
 14      * @param TextIndentation[] $lines All nested lines.
 15      * @return DataTable
 16      */
 17     protected function parseTable(
 18         TextIndentation $tableLine,
 19         array $lines
 20     ): DataTable
 21     {
 22         $table = new DataTable();
 23 
 24         $table->start = $this->lineToPosition($tableLine);
 25         $table->rows = $this->parseTableRows($lines);
 26 
 27         return $table;
 28     }
 29 
 30     /**
 31      * Parses the provided lines and returns a TableRow array.
 32      *
 33      * @param TextIndentation[] $lines The lines to parse.
 34      * @return TableRow[]
 35      */
 36     protected function parseTableRows(array $lines): array
 37     {
 38         $rows = [];
 39 
 40         for ($i = 0; $i < count($lines); $i++) {
 41             $cur = $lines[$i];
 42 
 43             $content = (string) str($cur->line)->ltrim;
 44 
 45             // If the current line begins with a vertical
 46             // pipe, we will parse it as a table row.
 47             if (str($content)->startsWith('|')) {
 48                 $rows[] = $this->parseTableRow($cur);
 49             }
 50         }
 51 
 52         return $rows;
 53     }
 54 
 55     /**
 56      * Parses a single line into a Gherkin DataRow.
 57      *
 58      * @param TextIndentation $tableRowLine The line to parse.
 59      * @return TableRow
 60      */
 61     protected function parseTableRow(
 62         TextIndentation $tableRowLine
 63     ): TableRow
 64     {
 65         $row = new TableRow();
 66 
 67         $row->start = $this->lineToPosition($tableRowLine);
 68         $row->cells = $this->parseTableCells($tableRowLine);
 69 
 70         return $row;
 71     }
 72 
 73     /**
 74      * Parses a single line into a Gherkin TableCell array.
 75      *
 76      * @param TextIndentation $tableRowLine The line to parse.
 77      * @return TableCell[]
 78      */
 79     protected function parseTableCells(
 80         TextIndentation $tableRowLine
 81     ): array
 82     {
 83         $cells = [];
 84 
 85         $content = (string) str($tableRowLine->line)->ltrim;
 86 
 87         // Splits our string into an array on the pipe character.
 88         // For example, if the line is: "| foo | bar |" this will
 89         // return ["", " foo ", " bar ", ""]. We also have a
 90         // negative lookbehind to ensure that we don't split
 91         // on escaped pipes. For example, if the line is:
 92         // "| foo \| bar |" this will return ["", " foo \| bar ", ""]
 93         $content = preg_split('/(?<!\\\)\|/u', $content);
 94 
 95         // Remove the spaces left over from the beginning and end.
 96         // We cannot remove all empty spaces,
 97         // since some cells can be empty.
 98         array_shift($content);
 99         array_pop($content);
100 
101         $content = collect($content)->map(function ($value) {
102             return (string) str($value)
103                 ->replace('\|', '|') // Replace escaped pipes
104                 ->replace('\n', "\n") // Replace escaped newlines
105                 ->replace('\\\\', '\\') // Replace escaped backslashes
106                 ->trim;
107         })->all();
108 
109         // Create a new TableCell for each cell value.
110         foreach ($content as $cell) {
111             $cells[] = new TableCell($cell);
112         }
113 
114         return $cells;
115     }
116 
117     // ...
118 }
```

Our `parseTable` method declared on line 17 will be called whenever we find a string that starts with the vertical pipe character. This method, in turn, calls our `parseTableRows` method, which is responsible for finding every line that begins with the vertical pipe character.

Remember that our parser will receive the results from the `IndentationManager`, which allows us to retrieve the lines directly below any given line. We are leveraging this fact to avoid accidentally scanning the entire document in all the methods that employ this strategy. Whenever we find a valid line, we call our `parseTableRows`, which creates our `TableRow` instance and then calls the `parseTableCells` method, where most of the work is performed.

On line 93, we use a regular expression to split the contents of the line into an array. This process results in the resulting array of values having empty strings as the first and last elements of the array, where the initial vertical pipe characters were. We remove these empty strings on lines 98 and 99. The remainder of our data tables parsing method is relatively straightforward: it will iterate all of the values and apply the rules of all the allowed escape sequences.

Once we have the final contents for all of our cells, we create new `TableCell` instances for them and return the results.

Because of the relative complexity of parsing Gherkin data tables, it may be beneficial to see the resulting output from the example input provided in **Figure 12.54**:

Figure 12.57 Classes Produced from Parsing Gherkin Data Tables 

```
 1 DataTable {
 2   start: 190
 3   rows: array:3 [
 4     0 => TableRow {
 5       start: 190
 6       comments: []
 7       keyword: ""
 8       cells: array:3 [
 9         0 => TableCell {
10           comments: []
11           keyword: ""
12           value: "start"
13         }
14         1 => TableCell {
15           comments: []
16           keyword: ""
17           value: "eat"
18         }
19         2 => TableCell {
20           comments: []
21           keyword: ""
22           value: "left"
23         }
24       ]
25     }
26     1 => TableRow {
27       start: 222
28       comments: []
29       keyword: ""
30       cells: array:3 [
31         0 => TableCell {
32           comments: []
33           keyword: ""
34           value: "12"
35         }
36         1 => TableCell {
37           comments: []
38           keyword: ""
39           value: "5"
40         }
41         2 => TableCell {
42           comments: []
43           keyword: ""
44           value: "7"
45         }
46       ]
47     }
48     2 => TableRow {
49       start: 254
50       comments: []
51       keyword: ""
52       cells: array:3 [
53         0 => TableCell {
54           comments: []
55           keyword: ""
56           value: "20"
57         }
58         1 => TableCell {
59           comments: []
60           keyword: ""
61           value: "5"
62         }
63         2 => TableCell {
64           comments: []
65           keyword: ""
66           value: "15"
67         }
68       ]
69     }
70   ]
71 }
```

#### Parsing Scenario Examples

We are almost ready to start parsing some of the larger Gherkin structures but have just a few smaller structures to take care of first. In this section, we are going to work on parsing the “Examples” or “Scenarios” block that appears under scenario outlines:

Figure 12.58 Example of Gherkin Examples/Scenarios 

```
1 Scenario Outline: eating
2   Given there are <start> cucumbers
3   When I eat <eat> cucumbers
4   Then I should have <left> cucumbers
5 
6   Examples:
7     | start | eat | left |
8     |    12 |   5 |    7 |
9     |    20 |   5 |   15 |
```

For now, let us assume that we are already inside a parser method that handles the scenario outline and already have access to the indentation lines 2-6 from **Figure 12.58**. From the same example figure, line 6 starts with the keyword “Examples:.” We will look for this keyword and its “Scenarios:” alias and then begin parsing all of the lines under it. In our specific example, these will be lines 7-9.

Figure 12.59 Detecting Examples and Scenarios Structures 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a list of Gherkin Examples block.
12      *
13      * @param TextIndentation[] $lines The lines to parse.
14      * @return array
15      */
16     protected function parseExamples(array $lines): array
17     {
18         $examples = [];
19 
20         for ($i = 0; $i < count($lines); $i++) {
21             $cur = $lines[$i];
22 
23             $content = (string) str($cur->line)->ltrim;
24 
25             // Test if the current line starts with the Examples
26             // or Scenarios keyword. For English, this checks
27             // for "Examples:" or "Scenarios:".
28             if (str($content)->startsWith(
29                 $this->gherkinKeywords['examples'],
30                 $this->gherkinKeywords['scenarios']
31             )) {
32                 $examples[] = $this->parseExample($cur);
33             }
34         }
35 
36         return $examples;
37     }
38 
39     // ...
40 }
```

In **Figure 12.59**, we added the `parseExamples` method, which will visit each line under the Scenario Outline (lines 2-6 from **Figure 12.58**). Between Lines 28 and 31, we are checking to see if the current line begins with either of the two keywords that would indicate the start of the scenario outline examples block, and if it does match, we call the `parseExample` method on the current line. We must continuously remind ourselves that these methods will work on instances of `TextIndentation` objects. As a consequence, on line 32, when we supply the current line to `parseExample`, it will receive the content of line 6 from **Figure 12.58**, but also lines 7-9 nested under it. Let us now take a look at the `parseExample` method:

Figure 12.60 Parsing Gherkin Examples Blocks 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Gherkin Example.
12      *
13      * @param TextIndentation $exampleLine The line to parse.
14      * @return Examples
15      */
16     protected function parseExample(
17         TextIndentation $exampleLine
18     ): Examples
19     {
20         $example = new Examples();
21 
22         $example->comments = $this->parseComments(
23             $exampleLine->nestedLines
24         );
25 
26         $example->keyword = 'examples';
27         $example->start = $this->lineToPosition($exampleLine);
28 
29         if (count($exampleLine->nestedLines) > 0) {
30             $tableLine = $exampleLine->nestedLines[0];
31 
32             // Ask the table parser to handle the contents.
33             $example->table = $this->parseTable(
34                 $tableLine,
35                 $exampleLine->nestedLines
36             );
37         }
38 
39         return $example;
40     }
41 
42     // ...
43 }
```

As we progress in writing our parser, we will see a similar trend starting to emerge: we are working less and less with splitting lines/words, as we can see in **Figure 12.60**. Between lines 29 and 37, we are performing a check to see if the incoming line has any nested lines below it. If so, we grab the first line assuming it will be a table for now, and then we call our existing `parseTable` method we developed earlier.

#### Parsing Steps

Steps are what provide the individual action items when defining a Gherkin test. **Figure 12.61** offers a quick overview of what these look like in context:

Figure 12.61 Gherkin Steps Example 

```
1 Scenario: eat 5 out of 12
2   Given there are 12 cucumbers
3   When I eat 5 cucumbers
4   Then I should have 7 cucumbers
```

Like with most things we’ve done so far, we will iterate each line we are interested in and check to see if they start with any step keywords. If so, we will parse that line into an individual `Step` data object.

You may remember that we have already developed several step-related parsing methods throughout this chapter. For example, we have already developed a method to parse a step’s text, keywords, and parameters. We will be making use of all of those now to bring together our first large Gherkin language construct:

Figure 12.62 Parsing Gherkin Steps 

```
  1 <?php
  2 
  3 use Illuminate\Support\Str;
  4 
  5 class GherkinParser
  6 {
  7 
  8     // ...
  9 
 10     /**
 11      * Parses a list of Gherkin Steps.
 12      *
 13      * @param TextIndentation[] $lines The lines to parse.
 14      * @return Step[]
 15      * @throws Exception
 16      */
 17     protected function parseSteps(array $lines): array
 18     {
 19         $steps = [];
 20 
 21         for ($i = 0; $i < count($lines); $i++) {
 22             $cur = $lines[$i];
 23 
 24             $content = (string) str($cur->line)->ltrim;
 25 
 26             // Test if the current line starts with a Step
 27             // keyword. For English, this checks can be any
 28             // of "Given", "When", "Then", "And", or "But".
 29             if (str($content)
 30                 ->ltrim->startsWith($this->stepKeywords)) {
 31                 $steps[] = $this->parseStep($cur);
 32             }
 33         }
 34 
 35         return $steps;
 36     }
 37 
 38     /**
 39      * Parses an individual Gherkin Step.
 40      *
 41      * @param TextIndentation $stepLine The line to parse.
 42      * @return Step
 43      * @throws Exception
 44      */
 45     protected function parseStep(TextIndentation $stepLine): Step
 46     {
 47         $step = new Step();
 48 
 49         $step->comments = $this->parseComments($stepLine->nestedLines);
 50 
 51         // Extract the keyword from the line.
 52         // This returns an array containing a
 53         // normalized keyword as the first
 54         // element, and the localized keyword
 55         // as the second element. For example,
 56         // ["given", "Given"].
 57         $sourceKeyword = $this->parseStepKeyword($stepLine);
 58 
 59         $step->keyword = $sourceKeyword[0];
 60 
 61         $step->text = $this->parseStepText(
 62             $stepLine, str($sourceKeyword[1])->rtrim
 63         );
 64 
 65         $step->start = $this->lineToPosition($stepLine);
 66         $step->data = $this->parseStepData($stepLine);
 67         $step->parameters = $this->parseStepParameters($stepLine);
 68 
 69         return $step;
 70     }
 71 
 72     /**
 73      * Parses the line and returns an array containing
 74      * instances of either DataTable or DocString.
 75      *
 76      * @param TextIndentation $stepLine The line to parse.
 77      * @return DataTable[]|DocString[]
 78      */
 79     protected function parseStepData(TextIndentation $stepLine): array
 80     {
 81         $data = [];
 82 
 83         for ($i = 0; $i < count($stepLine->nestedLines); $i++) {
 84             $cur = $stepLine->nestedLines[$i];
 85 
 86             $content = (string) str($cur->line)->ltrim;
 87 
 88             // Doc strings can begin with either a
 89             // """ or ```. We will check for both.
 90             if (str($content)->startsWith(['"""', '```'])) {
 91                 $data[] = $this->parseDocString(
 92                     $cur,
 93                     $stepLine->allNestedLines
 94                 );
 95             } elseif (str($content)->startsWith('|')) {
 96                 // If the current line starts with a vertical
 97                 // pipe, we will ask the table parser to
 98                 // handle the contents.
 99                 $data[] = $this->parseTable(
100                     $cur,
101                     $stepLine->nestedLines
102                 );
103             }
104         }
105 
106         return $data;
107     }
108 
109     // ...
110 
111 }
```

The pace is picking up now, and we will continue to make quick progress as we move through the remainder of the larger constructs. The first method called from **Figure 12.62** is the `parseSteps` method.

The `parseSteps` method iterates each of the lines provided to it, and between lines 29-32, we check to see if the current line begins with any of the step keywords. If it does, we make a call to our `parseStep` method on line 31 to do the actual parsing of the step.

The `parseStep` method is one of the first we’ve done that makes a lot of calls to many of the supporting parsing methods we have already developed. For example, it calls `parseStepKeyword` on line 57 to resolve the internal and localized keyword. Between lines 61 and 63, we use our `parseStepText` method to extract the text from the step line, and lines 66 and 67 resolve additional information, such as any attached data tables, doc strings, or parameters.

#### Parsing a Single Scenario and Background

We will now work to parse a single Gherkin scenario and the background structure. We will do this together because Gherkin’s backgrounds are similar to scenarios. If we look at **Figure 12.63**, we can see that structurally the two are identical:

Figure 12.63 Example of a Gherkin Background and Scenario 

```
 1 Feature: Multiple site support
 2   Only blog owners can post to a blog, except administrators,
 3   who can post to all blogs.
 4 
 5   Background:
 6     Given a global administrator named "Greg"
 7     And a blog named "Greg's anti-tax rants"
 8     And a customer named "Dr. Bill"
 9     And a blog named "Expensive Therapy" owned by "Dr. Bill"
10 
11   Scenario: Dr. Bill posts to his own blog
12     Given I am logged in as Dr. Bill
13     When I try to post to "Expensive Therapy"
```

However, remember that during our data modeling process, we created two different PHP classes to represent these structures. Because these features are so similar, we can actually leverage the scenario parser to implement our background parser.

Figure 12.64 Parsing a Single Gherkin Scenario 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Gherkin Scenario.
12      *
13      * @param TextIndentation $scenarioLine The line to parse.
14      * @param TextIndentation|null $tagLine The tag line.
15      * @return Scenario
16      * @throws Exception
17      */
18     protected function parseScenario(
19         TextIndentation $scenarioLine,
20         TextIndentation $tagLine = null): Scenario
21     {
22         $scenario = new Scenario();
23 
24         $scenario->comments = $this->parseComments(
25             $scenarioLine->nestedLines
26         );
27 
28         $scenario->description = $this->parseDescription(
29             $scenarioLine->allNestedLines
30         );
31 
32         $scenario->keyword = 'scenario';
33 
34         $scenario->name = (string) str($this->parseName(
35             $scenarioLine,
36             'scenario')
37         )->ltrim;
38 
39         $scenario->steps = $this->parseSteps(
40             $scenarioLine->nestedLines
41         );
42 
43         $scenario->start = $this->lineToPosition(
44             $scenarioLine
45         );
46 
47         $scenario->examples = $this->parseExamples(
48             $scenarioLine->nestedLines
49         );
50 
51         if ($tagLine) {
52             $scenario->tags = $this->parseTags($tagLine);
53         }
54 
55         return $scenario;
56     }
57 
58     // ...
59 
60 }
```

The interesting thing about our `parseScenario` method implementation in **Figure 12.64** is that it isn’t doing anything *new*. It is simply taking all of the lines provided to it, in this instance it would receive lines 11-13 from **Figure 12.63**, and calling existing methods to compose our final Scenario object. Let us now take a look at **Figure 12.65**, which parses Gherkin backgrounds:

Figure 12.65 Parsing Gherkin Backgrounds 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Gherkin Background.
12      *
13      * @param TextIndentation[] $lines Then lines to parse.
14      * @return Background|null
15      * @throws Exception
16      */
17     protected function parseBackground(array $lines): ?Background
18     {
19         for ($i = 0; $i < count($lines); $i++) {
20             $cur = $lines[$i];
21 
22             $content = (string) str($cur->line)->ltrim;
23 
24             // Test if the current line starts with the Background
25             // keyword. For English, this checks for "Background:".
26             if (str($content)->startsWith(
27                     $this->gherkinKeywords['background'])) {
28                 $scenario = $this->parseScenario($cur);
29 
30                 $background = new Background();
31                 $background->steps = $scenario->steps;
32                 $background->start = $scenario->start;
33                 $background->keyword = 'background';
34 
35                 return $background;
36             }
37         }
38 
39         return null;
40     }
41 
42     // ...
43 
44 }
```

Before diving into the implementation of the `parseBackground` method in **Figure 12.65**, it will be helpful to understand how it relates to the input in **Figure 12.63**. The `parseBackground` method will be called at the *feature* or the *rule* level to locate any background objects that may exist. In **Figure 12.63**, our `parseBackground` method would receive lines 2, 5, and 11 because of how our indentation manager groups our lines based on their relative indentation level. Our implementation will loop over all of these lines, and checks if the current line starts with the background keyword on lines 26 and 27.

Once our method has discovered a line that should be parsed as a Gherkin background, we make a call to our `parseScenario` method on line 28. We do this because of how similar the two constructs are to each other. Finally, between lines 30 and 33, we create a new instance of our final `Background` object and simply assign the results of the `parseScenario` method to this new object.

#### Parsing Scenario Outlines and Templates

We are almost at the finish line, and our next step is to work on parsing scenario outlines and templates. **Figure 12.66** offers a quick reminder of what we are working with:

Figure 12.66 Example of Gherkin Scenario Outlines and Templates 

```
1 Scenario Outline: eating
2   Given there are <start> cucumbers
3   When I eat <eat> cucumbers
4   Then I should have <left> cucumbers
5 
6   Examples:
7     | start | eat | left |
8     |    12 |   5 |    7 |
9     |    20 |   5 |   15 |
```

From **Figure 12.66**, we can see that a scenario outline is structurally very similar to our scenarios, but also has a data table attached to it using the “Examples:” keyword. Luckily for us, we already have all the supporting methods to help us parse **Figure 12.66** into a `ScenarioOutline` object:

Figure 12.67 Parsing Gherkin Scenario Templates 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Gherkin Scenario Outline.
12      *
13      * @param TextIndentation $scenarioLine The line to parse.
14      * @param TextIndentation|null $tagLine The tag line.
15      * @return ScenarioOutline
16      * @throws Exception
17      */
18     protected function parseScenarioOutline(
19         TextIndentation $scenarioLine,
20         TextIndentation $tagLine = null
21     ): ScenarioOutline
22     {
23         $scenario = new ScenarioOutline();
24 
25         $scenario->comments = $this->parseComments(
26             $scenarioLine->nestedLines
27         );
28 
29         $scenario->start = $this->lineToPosition($scenarioLine);
30 
31         $scenario->keyword = 'scenario_outline';
32 
33         $scenario->name = $this->parseName(
34             $scenarioLine,
35             'scenario_outline'
36         );
37 
38         $scenario->steps = $this->parseSteps(
39             $scenarioLine->nestedLines
40         );
41 
42         $scenario->examples = $this->parseExamples(
43             $scenarioLine->nestedLines
44         );
45 
46         if ($tagLine) {
47             $scenario->tags = $this->parseTags($tagLine);
48         }
49 
50         return $scenario;
51     }
52 
53     // ...
54 
55 }
```

There is not too much to say about our `parseScenarioOutline` method in **Figure 12.67** as it is very similar to the last few methods we have worked through. It accepts the indentation line object from the line that contains the correct keyword, and manages calls to other parser methods to build up the final result. One thing to note is that it accepts an optional `$tagLine` argument, which we will take a look at in the next section when we parse lists of scenarios.

#### Parsing Multiple Scenarios

In **Figure 12.68**, we can see that our figure contains multiple scenarios. Our scenarios to parse begin on lines 4 and 9. Our parser method will receive all of the lines that appear below line 1, so we will be able to utilize our existing strategy of looping over those lines and checking if they begin with our scenario keyword.

Figure 12.68 Example of Multiple Gherkin Scenarios 

```
 1 Feature: Guess the word
 2 
 3   # The first example has two steps
 4   Scenario: Maker starts a game
 5     When the Maker starts a game
 6     Then the Maker waits for a Breaker to join
 7 
 8   # The second example has three steps
 9   Scenario: Breaker joins a game
10     Given the Maker has started a game with the word "silky"
11     When the Breaker joins the Maker's game
12     Then the Breaker must guess a word with 5 characters
```

We will continue with our long-established strategy of checking if the line begins with the appropriate keywords, and then calling the proper internal parsing methods. We will also handle scenario templates and outlines within this same method:

Figure 12.69 Parsing Gherkin Scenarios 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a list of Gherkin Scenarios.
12      *
13      * @param TextIndentation[] $lines The lines to parse.
14      * @return array
15      * @throws Exception
16      */
17     protected function parseScenarios(array $lines): array
18     {
19         $scenarios = [];
20 
21         for ($i = 0; $i < count($lines); $i++) {
22             $cur = $lines[$i];
23 
24             $content = str($cur->line)->ltrim;
25 
26             // Test if the current line starts with the Scenario
27             // keyword. For English, this checks for "Scenario:".
28             // The Examples keyword will also be parsed as a
29             // scenario. For English, this checks for "Examples:".
30             if ($content->startsWith([
31                 $this->gherkinKeywords['scenario'],
32                 $this->gherkinKeywords['example']
33             ])) {
34                 $scenarios[] = $this->parseScenario(
35                     $cur, $this->getTagsLine($lines, $i)
36                 );
37 
38             } elseif ($content->startsWith(
39                     $this->gherkinKeywords['scenario_outline'],
40                     $this->gherkinKeywords['scenario_template']
41             )) {
42 
43                 // Parses Scenario Outline if the current line
44                 // begins with the scenario_outline or the
45                 // scenario_template keyword. For English,
46                 // this is "Scenario Outline:" or "Scenario Template:".
47                 $scenarios[] = $this->parseScenarioOutline(
48                     $cur, $this->getTagsLine($lines, $i)
49                 );
50             }
51         }
52 
53         return $scenarios;
54     }
55 
56     // ...
57 
58 }
```

#### Parsing a Single Rule and Multiple Rules

If we look at **Figure 12.70**, we can see a Gherkin rule is starting on line 3, and this rule has multiple examples that begin on lines 5 and 12.

Figure 12.70 Example of Gherkin Rules 

```
 1 Feature: Highlander
 2 
 3   Rule: There can be only One
 4 
 5     Example: Only One -- More than one alive
 6       Given there are 3 ninjas
 7       And there are more than one ninja alive
 8       When 2 ninjas meet, they will fight
 9       Then one ninja dies (but not me)
10       And there is one ninja less alive
11 
12     Example: Only One -- One alive
13       Given there is only 1 ninja alive
14       Then he (or she) will live forever ;-)
```

Our process for parsing these will be the same as all of the other nested block parsing we’ve done so far. **Figure 12.71** contains our `parseRule` method, which is responsible for parsing a single rule. If we refer back to **Figure 12.70**, the `parseRule` method would receive the indentation line objects for lines 5 and 12, individually.

Figure 12.71 Parsing a Single Gherkin Rule 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a Gherkin Rule.
12      *
13      * @param TextIndentation $ruleLine The line to parse.
14      * @return Rule
15      * @throws Exception
16      */
17     protected function parseRule(TextIndentation $ruleLine): Rule
18     {
19         $rule = new Rule();
20 
21         $rule->comments = $this->parseComments($ruleLine->nestedLines);
22         $rule->start = $this->lineToPosition($ruleLine);
23         $rule->keyword = 'rule';
24         $rule->name = $this->parseName($ruleLine, 'rule');
25 
26         $rule->description = $this->parseDescription(
27             $ruleLine->allNestedLines
28         );
29 
30         $rule->background = $this->parseBackground(
31             $ruleLine->nestedLines
32         );
33 
34         $rule->scenarios = $this->parseScenarios(
35             $ruleLine->nestedLines
36         );
37 
38         return $rule;
39     }
40 
41     // ...
42 
43 }
```

Similarly to how we parsed multiple scenarios within a feature, we can create a second parsing method that will receive the feature that starts on line 1 of **Figure 12.70**. This new method will iterate all of its direct children lines, and check for the rule keyword. If found, it will then make a call to our `parseRule` to handle the parsing of the individual rule:

Figure 12.72 Parsing Multiple Gherkin Rules 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a list of Gherkin Rules.
12      *
13      * @param TextIndentation[] $lines The lines to parse.
14      * @return array
15      * @throws Exception
16      */
17     protected function parseRules(array $lines): array
18     {
19         $rules = [];
20 
21         for ($i = 0; $i < count($lines); $i++) {
22             $cur = $lines[$i];
23 
24             $content = (string) str($cur->line)->ltrim;
25 
26             // Test if the current line starts with the Rule
27             // keyword. For English, this checks for "Rule:".
28             if (str($content)->startsWith(
29                 $this->gherkinKeywords['rule'])) {
30                 $rules[] = $this->parseRule($cur);
31             }
32         }
33 
34         return $rules;
35     }
36 
37     // ...
38 
39 }
```

#### Parsing Features

All of the work we have done thus far has been leading up to our final construct: the feature. With all of the parsing methods we have implemented so far, our strategy has always been to loop over the lines that ultimately come from the feature line. We will continue that with this section. As a quick reminder of what we need to do, lets take a quick look at **Figure 12.73**:

Figure 12.73 Gherkin Feature Example 

```
1 Feature: Guess the word
2 
3   # The first example has two steps
4   Scenario: Maker starts a game
5     When the Maker starts a game
6     Then the Maker waits for a Breaker to join
```

Each Gherkin file may have at most one feature, and they appear on a line with the least amount of indentation. We can use this fact to iterate each line and find the one line that contains our feature keyword. Once we have found this keyword, we can take that line and parse it using the `parseFeature` method in **Figure 12.74**:

Figure 12.74 Parsing a Gherkin Feature 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses a feature.
12      *
13      * @param TextIndentation $featureLine The line to parse.
14      * @param TextIndentation[] $lines The lines to parse.
15      * @return Feature
16      * @throws Exception
17      */
18     protected function parseFeature(
19         TextIndentation $featureLine,
20         array $lines): Feature
21     {
22         $feature = new Feature();
23 
24         $feature->comments = $this->parseComments($lines);
25         $feature->start = $this->lineToPosition($featureLine);
26         $feature->keyword = 'feature';
27 
28         $feature->name = $this->parseName(
29             $featureLine,
30             'feature'
31         );
32 
33         $feature->description = $this->parseDescription(
34             $featureLine->nestedLines
35         );
36 
37         $feature->background = $this->parseBackground($lines);
38         $feature->scenarios = $this->parseScenarios($lines);
39         $feature->rules = $this->parseRules($lines);
40 
41         return $feature;
42     }
43 
44     // ...
45 
46 }
```

Because a Gherkin feature contains all of the various constructs we have already written parsing methods for, the `parseFeature` method will primarily just manage calling those existing methods for us. As an example, between lines 37 and 39 in **Figure 12.74**, we can see that our `parseFeature` method calls out to our `parseBackground`, `parseScenarios`, and `parseRules` methods. These methods will in turn perform their parsing steps to fully parse our document.

While we have a method to parse a single feature, but we have not yet done anything to actually call it like we have with the others. Our call to the `parseFeature` method will actually take place in the `parse` method we defined all the way back at the beginning of this process. **Figure 12.75** contains the changes to our `parse` method:

Figure 12.75 Updating the parse Method 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses the provided Gherkin text.
12      *
13      * @param string $value The string to parse.
14      * @param int $tabSize The tab size.
15      * @return Feature|null
16      * @throws Exception
17      */
18     public function parse(string $value, int $tabSize = 2): ?Feature
19     {
20         $value = Str::normalizeEol($value);
21         $this->locator = new CharacterPositionLocator($value);
22 
23         $indentationManager = new IndentationManager($value, $tabSize);
24         $lines = $indentationManager->getLines();
25 
26         // Locate the start of the feature.
27         for ($i = 0; $i < count($lines); $i++) {
28             $cur = $lines[$i];
29 
30             $content = (string) str($cur->line)->ltrim;
31 
32             if (str($content)->startsWith(
33                     $this->gherkinKeywords['feature'])) {
34                 return $this->parseFeature($cur, $cur->nestedLines);
35             }
36         }
37 
38         return null;
39     }
40 
41     // ...
42 
43 }
```

With this change, our first pass at implementing a Gherkin parser is now complete. It has been quite the journey to get to this point, but we can now invoke our parser like so:

Figure 12.76 

```
 1 <?php
 2 
 3 $gherkin = <<<GHERKIN
 4 Feature: Feature name
 5 
 6   Scenario Outline: eating
 7     Given there are <start> cucumbers
 8     When I eat <eat> cucumbers
 9     Then I should have <left> cucumbers
10 
11     Examples:
12         | start | eat | left |
13         |    12 |   5 |    7 |
14 GHERKIN;
15 
16 $parser = new GherkinParser();
17 
18 $parser->parse($gherkin, 2);
```

To produce the following final result:

Figure 12.77 

```
  1 Feature {
  2   start: 0
  3   comments: []
  4   keyword: "feature"
  5   name: "Feature name"
  6   description: ""
  7   background: null
  8   scenarios: array:1 [
  9     0 => ScenarioOutline {
 10       start: 27
 11       comments: []
 12       keyword: "scenario_outline"
 13       name: "eating"
 14       steps: array:3 [
 15         0 => Step {
 16           start: 57
 17           comments: []
 18           keyword: "given"
 19           text: "there are <start> cucumbers"
 20           data: []
 21           parameters: array:1 [
 22             0 => Parameter {
 23               start: 78
 24               comments: []
 25               keyword: ""
 26               name: "start"
 27             }
 28           ]
 29         }
 30         1 => Step {
 31           start: 96
 32           comments: []
 33           keyword: "when"
 34           text: "I eat <eat> cucumbers"
 35           data: []
 36           parameters: array:1 [
 37             0 => Parameter {
 38               start: 112
 39               comments: []
 40               keyword: ""
 41               name: "eat"
 42             }
 43           ]
 44         }
 45         2 => Step {
 46           start: 128
 47           comments: []
 48           keyword: "then"
 49           text: "I should have <left> cucumbers"
 50           data: []
 51           parameters: array:1 [
 52             0 => Parameter {
 53               start: 152
 54               comments: []
 55               keyword: ""
 56               name: "left"
 57             }
 58           ]
 59         }
 60       ]
 61       examples: array:1 [
 62         0 => Examples {
 63           start: 171
 64           comments: []
 65           keyword: "examples"
 66           table: DataTable {
 67             start: 190
 68             rows: array:2 [
 69               0 => TableRow {
 70                 start: 190
 71                 comments: []
 72                 keyword: ""
 73                 cells: array:3 [
 74                   0 => TableCell {
 75                     comments: []
 76                     keyword: ""
 77                     value: "start"
 78                   }
 79                   1 => TableCell {
 80                     comments: []
 81                     keyword: ""
 82                     value: "eat"
 83                   }
 84                   2 => TableCell {
 85                     comments: []
 86                     keyword: ""
 87                     value: "left"
 88                   }
 89                 ]
 90               }
 91               1 => TableRow {
 92                 start: 222
 93                 comments: []
 94                 keyword: ""
 95                 cells: array:3 [
 96                   0 => TableCell {
 97                     comments: []
 98                     keyword: ""
 99                     value: "12"
100                   }
101                   1 => TableCell {
102                     comments: []
103                     keyword: ""
104                     value: "5"
105                   }
106                   2 => TableCell {
107                     comments: []
108                     keyword: ""
109                     value: "7"
110                   }
111                 ]
112               }
113             ]
114           }
115         }
116       ]
117       tags: []
118     }
119   ]
120   rules: []
121 }
```

### 12.4 Adding Localization Support to the Gherkin Parser

One of the more interesting aspects of the Gherkin language is the fact that the language itself supports localization, which our parser currently will not handle that well. Consider **Figure 12.78**, which is a sample feature test written in Norwegian:

Figure 12.78 Localized Gherkin Example 

```
 1 Funksjonalitet: Gjett et ord
 2 
 3   Eksempel: Ordmaker starter et spill
 4     Når Ordmaker starter et spill
 5     Så må Ordmaker vente på at Gjetter blir med
 6 
 7   Eksempel: Gjetter blir med
 8     Gitt at Ordmaker har startet et spill med ordet "bløtt"
 9     Når Gjetter blir med på Ordmakers spill
10     Så må Gjetter gjette et ord på 5 bokstaver
```

If we attempt to parse this currently, our parser will simply return `null`. Our task within this section will be to update our existing parser implementation to handle different language localizations. At the moment, our parser contains a hard-coded list of internal keyword mappings, which we can see in **Figure 12.79**.

Figure 12.79 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     /**
 9      * @var CharacterPositionLocator
10      */
11     protected CharacterPositionLocator $locator;
12 
13     /**
14      * The list of keywords that can be used to start a new block.
15      *
16      * @var string[]
17      */
18     protected array $gherkinKeywords = [
19         'feature' => 'Feature:',
20         // ...
21     ];
22 
23     /**
24      * The list of keywords that can be used to start a new step.
25      *
26      * @var string[]
27      */
28     protected array $stepKeywords = [
29         'given' => 'Given ',
30         // ...
31     ];
32 
33     // ...
34 
35 }
```

We can update this to use an internal locale mapping instead and then provide a `setLocale` method:

Figure 12.80 Supporting Multiple Locales 

```
  1 <?php
  2 
  3 use Illuminate\Support\Str;
  4 
  5 class GherkinParser
  6 {
  7 
  8     /**
  9      * @var CharacterPositionLocator
 10      */
 11     protected CharacterPositionLocator $locator;
 12 
 13     /**
 14      * The list of keywords that can be used to start a new block.
 15      *
 16      * @var string[]
 17      */
 18     protected array $gherkinKeywords = [
 19         'feature' => 'Feature:',
 20         'rule' => 'Rule:',
 21         'background' => 'Background:',
 22         'scenario' => 'Scenario:',
 23         'scenario_outline' => 'Scenario Outline:',
 24         'scenario_template' => 'Scenario Template:',
 25         'example' => 'Example:',
 26         'examples' => 'Examples:',
 27         'scenarios' => 'Scenarios:',
 28     ];
 29 
 30     /**
 31      * The list of keywords that can be used to start a new step.
 32      *
 33      * @var string[]
 34      */
 35     protected array $stepKeywords = [
 36         'given' => 'Given ',
 37         'when' => 'When ',
 38         'then' => 'Then ',
 39         'and' => 'And ',
 40         'but' => 'But ',
 41         '*' => '* ',
 42     ];
 43 
 44     protected array $locales = [
 45         'en' => [
 46             'keywords' => [
 47                 'feature' => 'Feature:',
 48                 'rule' => 'Rule:',
 49                 'background' => 'Background:',
 50                 'scenario' => 'Scenario:',
 51                 'scenario_outline' => 'Scenario Outline:',
 52                 'scenario_template' => 'Scenario Template:',
 53                 'example' => 'Example:',
 54                 'examples' => 'Examples:',
 55                 'scenarios' => 'Scenarios:',
 56             ],
 57             'stepKeywords' => [
 58                 'given' => 'Given ',
 59                 'when' => 'When ',
 60                 'then' => 'Then ',
 61                 'and' => 'And ',
 62                 'but' => 'But ',
 63             ],
 64         ],
 65         'no' => [
 66             'keywords' => [
 67                 'feature' => 'Funksjonalitet:',
 68                 'rule' => 'Regel:',
 69                 'background' => 'Bakgrunn:',
 70                 'scenario' => 'Scenario:',
 71                 'scenario_outline' => 'Abstrakt Scenario:',
 72                 'scenario_template' => 'Scenariomal:',
 73                 'example' => 'Eksempel:',
 74                 'examples' => 'Eksempler:',
 75                 'scenarios' => 'Scenarier:',
 76             ],
 77             'stepKeywords' => [
 78                 'given' => 'Gitt ',
 79                 'when' => 'Når ',
 80                 'then' => 'Så ',
 81                 'and' => 'Og ',
 82             ],
 83         ],
 84     ];
 85 
 86     /**
 87      * Sets the parser locale.
 88      * 
 89      * @param string $locale The locale.
 90      * @return void
 91      */
 92     public function setLocale(string $locale = 'en')
 93     {
 94         $this->gherkinKeywords = $this->locales[$locale]['keywords'];
 95         $this->stepKeywords = $this->locales[$locale]['stepKeywords'];
 96         $this->stepKeywords['*'] = '* ';
 97     }
 98 
 99     // ...
100 
101 }
```

Users of our parser would now have to remember to call the `setLocale` method before parsing. We can address this by adding a `$locale` parameter to our `parse` method and internally calling the `setLocale` method:

Figure 12.81 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     /**
11      * Parses the provided Gherkin text.
12      *
13      * @param string $value The string to parse.
14      * @param int $tabSize The tab size.
15      * @param string $locale The locale.
16      * @return Feature|null
17      * @throws Exception
18      */
19     public function parse(
20         string $value,
21         int $tabSize = 2,
22         string $locale = 'en'
23     ): ?Feature
24     {
25         $this->setLocale($locale);
26 
27         // ...
28     }
29 
30     // ...
31 
32 }
```

With our refactors out of the way, we can now change our parser’s locale to parse the Norwegian Gherkin sample from **Figure 12.78**:

Figure 12.82 

```
1 <?php
2 
3 $parser = new GherkinParser();
4 $parser->parse($text, 2, 'no');
```

Yielding the following results:

Figure 12.83 

```
 1 Feature {
 2   start: 0
 3   comments: []
 4   keyword: "feature"
 5   name: "Gjett et ord"
 6   description: ""
 7   background: null
 8   scenarios: array:2 [
 9     0 => Scenario {
10       start: 34
11       comments: []
12       keyword: "scenario"
13       description: ""
14       name: "Ordmaker starter et spill"
15       steps: array:2 [
16         0 => Step {
17           start: 75
18           comments: []
19           keyword: "when"
20           text: "Ordmaker starter et spill"
21           data: []
22           parameters: []
23         }
24         // ...
25       ]
26       examples: []
27       // ...
28   ]
29 }
```

It should also be noted that Gherkin also supports specifying the language within the test file itself by specifying a language header. Language headers appear on the first line and are implemented as a special comment:

Figure 12.84 Gherkin Language Header 

```
1 # language: no
2 Funksjonalitet: Gjett et ord
3 
4   Eksempel: Ordmaker starter et spill
5     Når Ordmaker starter et spill
6     Så må Ordmaker vente på at Gjetter blir med
```

We can support this in our parser as well by checking for this special header on the first line within our `parse` method:

Figure 12.85 Adding Support for Gherkin Language Headers 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 class GherkinParser
 6 {
 7 
 8     // ...
 9 
10     public function parse(string $value,
11         int $tabSize = 2,
12         string $locale = 'en'
13     ): ?Feature
14     {
15         $this->setLocale($locale);
16 
17         $value = Str::normalizeEol($value);
18         $this->locator = new CharacterPositionLocator($value);
19 
20         $indentationManager = new IndentationManager($value, $tabSize);
21         $lines = $indentationManager->getLines();
22 
23         // Locate the start of the feature.
24         for ($i = 0; $i < count($lines); $i++) {
25             $cur = $lines[$i];
26 
27             $content = (string) str($cur->line)->ltrim;
28 
29             if ($i == 0 && $cur->indentCount == 0 &&
30                 str($content)->startsWith('# language')
31             ) {
32                 $this->setLocale(str($content)->after(':')->trim);
33                 continue;
34             }
35 
36             if (str($content)->startsWith(
37                 $this->gherkinKeywords['feature'])) {
38                 return $this->parseFeature($cur, $cur->nestedLines);
39             }
40         }
41 
42         return null;
43     }
44 
45     // ...
46 
47 }
```

### 12.5 Other Applications of Indentation-Based Parsers

We have been incredibly focused on Gherkin throughout this chapter, as it is a relatively simple language for constructing a parser. This process was made even more accessible through our `IndentationManager` class. In this short section, I would like to take a brief moment to quickly explore other languages where such techniques might be beneficial.

When thinking of what language would be interesting to briefly explore, I could think of no better language than Python. Let us take a quick look at the Python code in **Figure 12.86**:

Figure 12.86 Example Python Program 

```
1 def hello():
2   name = str(input("Enter your name: "))
3   if name:
4     print ("Hello " + str(name))
5   else:
6     print("Hello World") 
7   return 
8   
9 hello()
```

A function is defined on line 1, and the body spans lines 2-7. The critical thing to note is that the function’s body is indented relative to the line it was defined on. We will now use our `IndentationManager` on this example Python code to see what we get back:

Figure 12.87 

```
 1 <?php
 2 
 3 $text = <<<PYTHON
 4 def hello():
 5   name = str(input("Enter your name: "))
 6   if name:
 7     print ("Hello " + str(name))
 8   else:
 9     print("Hello World") 
10   return 
11   
12 hello()
13 
14 PYTHON;
15 
16 $indentation = new IndentationManager($text, 2);
17 $lines = $indentation->getLines();
```

The results of the first few lines are:

Figure 12.88 

```
 1 array:10 [
 2   0 => TextIndentation {
 3     line: "def hello():"
 4     lineNumber: 1
 5     nestedLines: array:5 [
 6       0 => TextIndentation {
 7         line: "  name = str(input("Enter your name: "))"
 8         lineNumber: 2
 9       }
10       1 => TextIndentation {
11         line: "  if name:"
12         lineNumber: 3
13         nestedLines: array:1 [
14           0 => TextIndentation {
15             line: "    print ("Hello " + str(name))"
16             lineNumber: 4
17           }
18         ]
19       }
20       2 => TextIndentation {
21         line: "  else:"
22         lineNumber: 5
23         nestedLines: array:1 [
24           0 => TextIndentation {
25             line: "    print("Hello World") "
26             lineNumber: 6
27           }
28         ]
29   // ...
30 ]
```

While we are not going to explore creating a Python parser in this book, it is helpful to see how a simple concept such as the `IndentationManager` can be applied to many use cases.

## 13\. Markov Chains and Text Generation

When it comes to automated text generation, one of the more approachable techniques is Markov chains. A Markov chain is a mathematical concept that helps us model random systems where the sequence of events within the system is probabilistic. Specifically, the interesting aspect of Markov chains is that for any given event within the system, the probability of the next event within a series of events only depends on the state of the current event.

That is a lot to take in all at once. In a previous chapter, we worked through some helper methods to split a piece of input text into a list of words and retrieve the frequency or number of times a term appears within a piece of text. Let us look at the text in **Figure 13.1**:

Figure 13.1 Example Text 

```
1 The eldest cat, the youngest cat, and their group of cat friends went
2 down the alley to fetch the runaway ball.
```

If we count the number of words (not uniquely) within the text, we can see there are 21 words; additionally, if we use our previously developed `wordFrequency` helper method to get our word frequency ordered by how often they appear:

Figure 13.2 

```
1 <?php
2 
3 $text = <<<TEXT
4 The eldest cat, the youngest cat, and their group of cat friends went
5 down the alley to fetch the runaway ball.
6 TEXT;
7 
8 str($text)->wordFrequency
9     ->sortByDesc(fn($x) => $x);
```

We would arrive at the results in **Table 13.1**:

Table 13.1 Example Word Frequency

 
| Word || Occurrences || Perecentage |
| --- | --- | --- |
| the || 4 || 19.05% |
| --- | --- | --- |
| cat || 3 || 14.29% |
| eldest || 1 || 4.76% |
| youngest || 1 || 4.76% |
| and || 1 || 4.76% |
| their || 1 || 4.76% |
| group || 1 || 4.76% |
| of || 1 || 4.76% |
| friends || 1 || 4.76% |
| went || 1 || 4.76% |
| down || 1 || 4.76% |
| alley || 1 || 4.76% |
| to || 1 || 4.76% |
| fetch || 1 || 4.76% |
| runaway || 1 || 4.76% |
| ball || 1 || 4.76% |

The results in **Table 13.1** are not too surprising: the word “the” appears the most often, followed by cat, and then things quickly taper off, where all the remaining words appear once within the original text. This alone is a curious piece of information, but let us look at the frequency of words that occur after the word “the”:

Table 13.2 Frequency of Words Following the

 
| Word || Occurrences || Percentage |
| --- | --- | --- |
| alley || 1 || 25% |
| --- | --- | --- |
| eldest || 1 || 25% |
| runaway || 1 || 25% |
| youngest || 1 || 25% |

When we restrict the words we are interested into only those following a specific word instance, we can see that their percentages change pretty dramatically. Four words uniquely appear after the word “the,” and if we were asked what the probability of that word occurring after any given instance of the word “the,” it is 25%. We can repeat this process for the word “cat”:

Table 13.3 Frequency of Words Following cat

 
| Word || Occurrences || Percentage |
| --- | --- | --- |
| the || 1 || 33.33% |
| --- | --- | --- |
| and || 1 || 33.33% |
| friends || 1 || 33.33% |

Again, the percentages of each individual have changed quite dramatically, even though relative word occurrences remain the same. These two examples are particularly interesting since some words following “the” will also be followed by “cat.” This relationship can be visualized in **Figure 13.3**:

![Figure 13.3 Word Transition Probabilities](images/TextCHains.png)

Figure 13.3 Word Transition Probabilities

Let us imagine that in **Figure 13.3**, we start with the word “cat.” From this starting position, we have a 33% chance of moving to “friends,” “and,” or “the.” Let us now suppose that we transitioned to the word “the.”

Now that we are on the word “the,” we have a 25% chance of moving to “alley,” “eldest,” “youngest,” or “runaway.” Importantly, we do not necessarily care how we got to our current word since we are only concerned with where we can move next and the chances of each transition. Using only the word transitions presented in **Figure 13.3**, we can see that “alley” and “runway” would terminate our process: they do not connect to anything else on our reduced transition graph.

However, if we were to choose either “eldest” or “youngest,” we can transition back to “cat” one-hundred percent of the time, which starts the process over for our graph. Using this process of selecting a word, choosing a word based on its probability, and continuously repeating the process until we reach a termination point could produce the following example text from our transition graph:

Figure 13.4 

```
1 cat the eldest cat the youngest cat and
```

We have just described the process of implementing a Markov chain: we have broken our input text into a list of words. We select a new word based on the probabilities of subsequent words determined by analyzing the original text. When we have our new word, we repeat the process until we reach a word that leads nowhere. Our simple example isn’t too exciting, primarily because of the small amount of text used. This idea of selecting a new word using probabilities becomes much more interesting as the size of the analyzed text increases. This process seems like something we could encapsulate within a PHP class.

### 13.1 Writing a Markov Text Generator

To begin the process of writing a Markov text generator, let us first think through the first few steps we will need to accomplish:

1.  Break our input text into a list of words;
2.  For each word, find all words immediately following and count their frequency

This process will feel very similar to our previous work when implementing the word split and frequency helper methods. However, we will take a slightly different implementation approach when building the Markov text generator. This is because we can slightly modify *how* we represent our data to make it easier to work with for the current use case.

We will start our Markov text generator in **Figure 13.5**:

Figure 13.5 Beginning the Markov Text Generator 

```
 1 <?php
 2 
 3 class MarkovGenerator
 4 {
 5     protected $dictionary = [];
 6 
 7     public function loadText($text)
 8     {
 9         $words = str($text)->lower->wordSplit->all();
10 
11         for ($i = 0; $i < count($words); $i++) {
12             $word = $words[$i];
13             $nextWord = $words[$i + 1] ?? null;
14 
15             if (! isset($this->dictionary[$word][$nextWord])) {
16                 $this->dictionary[$word][$nextWord] = 1;
17             } else {
18                 $this->dictionary[$word][$nextWord]++;
19             }
20         }
21     }
22 }
```

On line 9, we split the lowercase version of our input text into a list of words. We are taking the lowercase version since it will help to remove the differences between words like “The” and “the.” Lines 11-20 are where things begin to get interesting.

Lines 12 and 13 are responsible for retrieving the current word within the list of extracted words and the word that appears immediately after it in the list. If no word appears after the present word, we default to `null`. Lines 15-19 use the two words retrieved and store them within the class’s internal dictionary; if it is the first time we’ve seen a particular word sequence, we set its count to 1. Every time we encounter the same word sequence, we increment its count on line 18.

We can now move on to implementing the central part of our algorithm in **Figure 13.6**:

Figure 13.6 Generating Text 

```
 1 <?php
 2 
 3 class MarkovGenerator
 4 {
 5     // ...
 6 
 7     public function generateText($seed = null, $length = 100)
 8     {
 9         if ($seed == null) {
10             $seed = array_rand($this->dictionary);
11         }
12 
13         // Set the output to the initial seed word.
14         $output = $seed;
15 
16         for ($i = 0; $i < $length; $i++) {
17             // Stop generating if the word does
18             // not exist inside our dictionary.
19             if (! array_key_exists($seed, $this->dictionary)) {
20                 break;
21             }
22 
23             $nextWord = array_rand($this->dictionary[$seed]);
24 
25             if ($nextWord == null) {
26                 break;
27             }
28 
29             $output .= ' ' . $nextWord;
30 
31             // Reset the seed to continue our generation.
32             $seed = $nextWord;
33         }
34 
35         return $output;
36     }
37 
38     // ...
39 }
```

Our new method accepts two arguments: an optional `$seed` and an `$optional` length. The seed word is what will begin the word selection process we discussed earlier. Our length will be used to limit the number of iterations in the unlikely event our text generation process enters into an infinite loop. If no seed word has been provided, we will retrieve a random word that is known to be in our dictionary between lines 9-11.

To handle the case of terminating the sequence, we check to see if the provided word exists within our dictionary on lines 19-21. If the word does not exist within our dictionary, we break out of our loop early. Similarly, on lines 25-27, we will also break out of the loop early if the next word we retrieved is `null`. Our word selection process happens on line 23, but at the moment, it simply returns the next word in the sequence completely at random.

The remainder of this chapter will work with the text found within Laravel’s documentation on the Artisan command-line utility^([11](#chap29.xhtml#fn-artisandocs)). In **Table 13.4** we can see the frequency of words that appear after the word “console” within the Laravel documentation:

Table 13.4 Frequency of Words Following console

 
| Word || Occurrences || Percentage |
| --- | --- | --- |
| command || 14 || 35% |
| --- | --- | --- |
| commands || 11 || 27.5% |
| kernel || 4 || 10% |
| events || 3 || 7.5% |
| php || 2 || 5% |
| introduction || 1 || 2.5% |
| based || 1 || 2.5% |
| this || 1 || 2.5% |
| you || 1 || 2.5% |
| as || 1 || 2.5% |
| helpers || 1 || 2.5% |

Calling our text generator using the following a few times:

Figure 13.7 

```
1 <?php
2 
3 $generator = new MarkovGenerator();
4 
5 // Contents of the Laravel Artisan documentation.
6 $laravelDocs = '...';
7 
8 $generator->generateText('console', 5);
```

May produce output similar to the following:

Figure 13.8 

```
1 console helpers progressbar html a registering
2 console as the load method lets
3 console php configuration file commands calling
```

Our production is definitely randomized, but it feels a bit “off”; i.e., it is a little too random. We can see this behavior in **Figure 13.9**, which is the results of generating thirty random words 10,000 times:

![Figure 13.9 Random Word Selection](images/ex_randomized.png)

Figure 13.9 Random Word Selection

On the left of the **Figure 13.9**, we start at generation 1 and move towards generation 10,000 on the right. Each line represents how many times that word has been selected at each generation; the exact labels of each word are unimportant as we can see that every word is chosen relatively equally. This behavior is not what we want if we want to preserve the probability of subsequent words.

### 13.2 Weighted Randomized Selection

We can improve the behavior of our text generator by updating the process we use to select our next word. Currently, our algorithm is simply choosing a word entirely at random. This is in contrast to the behavior we want: randomly selecting a word but preserving the relative probability of word sequences. The changes to achieve this can be found in **Figure 13.10**:

Figure 13.10 Weighted Word Selection 

```
 1 <?php
 2 
 3 class MarkovGenerator
 4 {
 5     protected $dictionary = [];
 6     protected $totals = [];
 7 
 8     public function loadText($text)
 9     {
10         // ...
11 
12         foreach ($this->dictionary as $sequence => $values) {
13             $this->totals[$sequence] = array_sum($values);
14         }
15     }
16 
17     protected function getWord($seed)
18     {
19         $rand = rand(1, $this->totals[$seed]);
20 
21         foreach ($this->dictionary[$seed] as $word => $count) {
22             $rand -= $count;
23 
24             if ($rand <= 0) {
25                 return $word;
26             }
27         }
28 
29         return null;
30     }
31 
32     public function generateText($seed = null, $length = 100)
33     {
34         if ($seed == null) {
35             $seed = array_rand($this->dictionary);
36         }
37 
38         // Set the output to the initial seed word.
39         $output = $seed;
40 
41         for ($i = 0; $i < $length; $i++) {
42             // Stop generating if the word does
43             // not exist inside our dictionary.
44             if (! array_key_exists($seed, $this->dictionary)) {
45                 break;
46             }
47 
48             $nextWord = array_rand($this->dictionary[$seed]);
49             $nextWord = $this->getWord($seed);
50 
51             if ($nextWord == null) {
52                 break;
53             }
54 
55             $output .= ' ' . $nextWord;
56 
57             // Reset the seed to continue our generation.
58             $seed = $nextWord;
59         }
60 
61         return $output;
62     }
63 }
```

We are creating a new internal array, `$totals`, on line 8. This will store the total number of words that follow any word in our dictionary. We populate this table on lines 12-14, and we will use these totals later to help select a word while preserving our relative weights.

On line 49, we refactor our `generateText` method and call a new `getWord` method instead of randomly selecting a word. We will now discuss our new `getWord` method.

Suppose that when we want to retrieve the next word following “console,” and the random number selected on line 19 is 16. We can look at **Table 13.5** to see how our `$rand` variable will change after each iteration:

Table 13.5 Weighted Word Selection Iterations

 
| Iteration || Word || Occurrences || rand Value |
| --- | --- | --- | --- |
| 1 || introudction || 1 || 15 |
| --- | --- | --- | --- |
| 2 || commands || 11 || 4 |
| 3 || command || 14 || \-10 |

After three iterations, our `getWord` method will return the word “command.” We can see from **Table 13.5** that the more often a word appears after our target word, the faster it will decrease our `$rand` variable, making it much more likely to be selected.

Let us now reanalyze the behavior of our generator like before and compare its behavior to the selected frequency in **Figure 13.9**. In **Figure 13.11** we can see that our new randomized selection process is now favoring more frequent words but still allowing for the less frequent words to be chosen:

![Figure 13.11 Weighted Word Selection](images/weighted_selection.png)

Figure 13.11 Weighted Word Selection

Looking at **Figure 13.12**, we can see that our weighted randomized selection process is retrieving words close to the same frequency as they appear within our source text.

![Figure 13.12 Comparing Generated Word Frequency to Source Word Frequency](images/word_distribution.png)

Figure 13.12 Comparing Generated Word Frequency to Source Word Frequency

### 13.3 Improving Our Text Generator

If we repeat our earlier experiment and generate some random text with our improved word selection, we may get results similar to the following:

Figure 13.13 

```
1 console command you need to select
2 console kernel class you may wish
3 console commands provide any changes to
```

Our generated text is starting to *feel* better, but we can still make improvements. One way we can do this is to use more than one word when constructing our dictionary. If we think about this idea, it makes sense.

Our text generation algorithm generates subsequent words based on how often they appeared in the original text. Presumably, this original text was written by a human, so they ultimately determined the frequency of those words. If we increase the number of words we reuse when predicting our text, more human influence will come through in the produced text. This, however, only works to a certain extent.

If we reuse too many words from the original text, the generated text will become less and less original and just appear as copy/pasted chunks from the original text.

We can update our existing implementation to support multi-word sequences like so:

Figure 13.14 Supporting Multiword Sequences in Our Text Generator 

```
 1 <?php
 2 
 3 class MarkovGenerator
 4 {
 5     protected $dictionary = [];
 6     protected $totals = [];
 7     protected $sequenceLength;
 8 
 9     public function __construct($sequenceLength = 1)
10     {
11         $this->sequenceLength = $sequenceLength;
12 
13         if ($this->sequenceLength <= 0) {
14             $this->sequenceLength = 1;
15         }
16     }
17 
18     public function loadText($text)
19     {
20         $words = str($text)->lower->wordSplit->all();
21 
22         for ($i = 0; $i < count($words); $i++) {
23             $word = $words[$i];
24             $nextWord = $words[$i + 1] ?? null;
25             $word = implode(
26                 ' ',
27                 array_slice($words, $i, $this->sequenceLength)
28             );
29 
30             $nextWord = $words[$i + $this->sequenceLength] ?? null;
31 
32             if (! isset($this->dictionary[$word][$nextWord])) {
33                 $this->dictionary[$word][$nextWord] = 1;
34             } else {
35                 $this->dictionary[$word][$nextWord]++;
36             }
37         }
38 
39         foreach ($this->dictionary as $sequence => $values) {
40             $this->totals[$sequence] = array_sum($values);
41         }
42     }
43 
44     // ...
45 
46     public function generateText($seed = null, $length = 100)
47     {
48         if ($seed == null) {
49             $seed = array_rand($this->dictionary);
50         }
51 
52         // Set the output to the initial seed word.
53         $output = $seed;
54 
55         // We need to break our seed into its
56         // own list of words so that we can
57         // retrieve the last word later
58         // to help build up our seeds.
59         $words = str($seed)->wordSplit->all();
60 
61         for ($i = 0; $i < $length; $i++) {
62             // Stop generating if the word does
63             // not exist inside our dictionary.
64             if (! array_key_exists($seed, $this->dictionary)) {
65                 break;
66             }
67 
68             $nextWord = $this->getWord($seed);
69 
70             if ($nextWord == null) {
71                 break;
72             }
73 
74             $output .= ' ' . $nextWord;
75 
76             // Remove the first word from our list of words.
77             $words = array_slice($words, 1);
78 
79             // Append the next word to the list.
80             $words[] = $nextWord;
81 
82             // Reset the seed to continue our generation.
83             $seed = $nextWord;
84             // Combine our words to create our next seed.
85             $seed = implode(' ', $words);
86         }
87 
88         return $output;
89     }
90 }
```

On lines 7-16 in **Figure 13.14**, we have created and are storing a new internal property: the sequence length. This value will be set via our class’s constructor since it does not make sense to load multiple pieces of text using a different sequence length.

On lines 25-30, we have refactored our logic to retrieve the current and next words when constructing our internal dictionary. Lines 25-28 are responsible for iterating each section of our input text and breaking it into chunks equal to the length of our sequence length. Line 30 retrieves the word that comes immediately after the sequence created in the previous step.

Some unobvious changes were made to our `generateText` method, particularly those surrounding generating the next seed word to continue our text generation process. On line 59, we break our initial seed word into an array using our `wordSplit` helper method.

When we generate our next seed word, we want to reuse all but the first word from our existing phrase. We accomplish this on line 77 by calling PHP’s `array_slice` function to remove the first element of the words array. If we have a sequence length of one, this will effectively clear our word list. Next, we add our newly retrieved word to the list of seed components on line 80. Finally, on line 85, we combine all the words to create a new seed word.

We can visualize this process in action by analyzing the results of multiple generations in **Table 13.6**, assuming an initial seed phrase “as user”:

Table 13.6 Constructing New Seed Words

 
| Generation || Seed Word |
| --- | --- |
| 0 (Initial) || as user |
| --- | --- |
| 1 || user this |
| 2 || this table |
| 3 || table name |
| 4 || name email |

As we can see from **Table 13.6**, each new seed word will use the end of the last seed to begin the following sequence. We can use our refactored text generator like so:

Figure 13.15 

```
1 <?php
2 
3 $markov = new MarkovGenerator(2);
4 $markov->loadText('...Laravel Artisan Documentation Text');
5 
6 for ($i = 0; $i < 3; $i++) {
7     echo $generator->generateText('for input', 5), "\n";
8 }
```

To produce new output using two-word sequences as the seed words:

Figure 13.16 

```
1 for input prompting for input in addition
2 for input in addition to displaying output
3 for input writing output to the prompt
```

## 14\. Fixed Width Data Parsing

This chapter will explore techniques and methods for working with data formatted using fixed-width data schemes. Fixed-width data formats are one of those development items that do not come up that often when working on typical web applications, but when they do, they can completely take some developers off guard. This is not because working with these formats is inherently tricky; and it is just that it is quite different from typical day-to-day tasks.

It will be challenging to discuss this topic in terms of absolutes or provide a meaningful generalized solution for reading and writing fixed-width data. The way data is encoded when stored in a fixed-width format highly depends on the application used to do the storage and the schema or data definition used, amongst other things. However, we can look at a few techniques together to understand how to work with this type of data.

Let us consider **Table 14.1**, which contains some sample invoice data:

Table 14.1 Sample Invoices

 
| Invoice # || Total || Quantity || Product ID |
| --- | --- | --- | --- |
| 1 || 12.00 || 5 || 1 |
| --- | --- | --- | --- |
| 2 || 32.32 || 1 || 2 |
| 3 || 16 || 10 || 3 |
| 4 || 622 || 4 || 4 |
| 5 || 77 || 1 || 5 |

Our table contains a handful of sample invoice data. From left to right, we have the invoice number, the total amount of currency charged for the invoice, the amount of product purchased, and finally, a product identifier. We do not know much about this data, such as the actual data types. For our sample invoices, we will assume that all values, except for the total, are integers; our total is a decimal number.

Let us now assume that we have received the following text file:

Figure 14.1 Example of Fixed-Width Data 

```
1          1        12         5         1
2          2     32.32         1         2
3          3        16        10         3
4          4       622         4         4
5          5        77         1         5
```

When we compare **Figure 14.1** to **Table 14.1**, we can quickly see how the data is associated. Each table row is represented as a single line within our text file, and each “cell” is stored within ten characters. Our first task will be to generate our text file from the following PHP array:

Figure 14.2 Array of Invoice Data 

```
 1 <?php
 2 
 3 $invoices = [
 4     [
 5         'number'   => 1,
 6         'total'    => 12.0,
 7         'quantity' => 5,
 8         'pid'      => 1,
 9     ],
10     [
11         'number'   => 2,
12         'total'    => 32.32,
13         'quantity' => 1,
14         'pid'      => 2,
15     ],
16     [
17         'number'   => 3,
18         'total'    => 16.0,
19         'quantity' => 10,
20         'pid'      => 3,
21     ],
22     [
23         'number'   => 4,
24         'total'    => 622.0,
25         'quantity' => 4,
26         'pid'      => 4,
27     ],
28     [
29         'number'   => 5,
30         'total'    => 77.0,
31         'quantity' => 1,
32         'pid'      => 5,
33     ],
34 ];
```

Let us think about how we can convert our array into the format we saw in **Figure 14.1**. It is at this point that it is easy to overcomplicate things. We have already encountered the tools we need to perform our task through the Laravel helper methods:

Figure 14.3 Converting Our Invoices to a Text File 

```
1 <?php
2 
3 $textData = collect($invoices)->map(function ($invoice) {
4     return str('')
5         ->append(str($invoice['number'])->padLeft(10))
6         ->append(str($invoice['total'])->padLeft(10))
7         ->append(str($invoice['quantity'])->padLeft(10))
8         ->append(str($invoice['pid'])->padLeft(10));
9 })->join("\n");
```

On line 3, we are creating a Laravel collection instance using our invoices array to leverage all of its features. In particular, we are utilizing its `map` method, which can be used to transform each element of our invoice array. Inside our `map` method’s body, we convert each invoice to a string, and finally, on line 9, we join all elements of our array with a newline character.

Between lines 4 and 8, we convert each invoice into our textual format. In line 4, we initialize an empty fluent string object to chain method calls. Each subsequent line appends each column to our empty string after padding the value to ten characters, using the `padLeft` method.

Now that we have a simple way to convert our invoice array to a string, we can start to ask some interesting questions about it. The first such question might be, considering everything we know about our text, is there a way can count the number of records without converting it back to an array?

In **Figure 14.3**, when we converted our invoices to a string, we joined all of our records using the newline character. We can take advantage of this fact and count the number of newline characters that appear in our text to retrieve the number of records:

Figure 14.4 Counting the Number of Records 

```
1 <?php
2 
3 // Count the number of records in our string.
4 
5 // Returns 4
6 str($textData)->substrCount("\n");
```

You may have noticed that counting the number of newline characters returns one less than the total record count. This is because our document does not end with a trailing newline; we can accommodate this my adding one to our newline count to retrieve the final record count:

Figure 14.5 Accounting for No Trailing Newline Character 

```
1 <?php
2 
3 // Count the number of records in our string.
4 
5 // Returns 5
6 str($textData)->substrCount("\n") + 1;
```

The next question we may ask is, for each individual record, what is the size of each record? Considering that we have four columns and padded each column to use ten characters when storing the data, we can say that each record is precisely forty characters long.

For the sake of discussion, let us refactor our existing conversion method to join our records using an empty string character instead of a newline character:

Figure 14.6 

```
1 <?php
2 
3 $textData = collect($invoices)->map(function ($invoice) {
4     return str('')
5         ->append(str($invoice['number'])->padLeft(10))
6         ->append(str($invoice['total'])->padLeft(10))
7         ->append(str($invoice['quantity'])->padLeft(10))
8         ->append(str($invoice['pid'])->padLeft(10));
9 })->join('');
```

Which would produce text similar to the following. The newline characters have been added for formatting reasons but are not present in the string output:

Figure 14.7 Records Joined With an Empty String 

```
1 1        12         5         1         2     32.32         1         2
2 3        16        10         3         4       622         4         4
3 5        77         1         5
```

Now that we have our records joined by an empty string, we cannot use our technique of counting the newline characters to determine our record count. However, we know how many characters each record individually takes up, which is forty characters. Additionally, we can quickly determine the length of our output string. We can divide these two values to retrieve the total number of records in our text:

Figure 14.8 Getting Record Counts Without Newline Characters 

```
1 <?php
2 
3 // Count the number of records in our string.
4 
5 // Returns 5
6 str($textData)->length() / 40;
```

Our next task will be to convert our string back into an array of invoices. We will work with the text output in **Figure 14.7**, where each record is joined by an empty string.

If we were working with the version joined by newline characters, we could split our input string on newline characters to retrieve the text contents of each record. Since we do not have newline characters, our task will be a bit more challenging but not impossible.

Figure 14.9 Breaking a String Into an Array of Strings 

```
 1 <?php
 2 
 3 $data = str($textData);
 4 $dataLength = $data->length();
 5 
 6 $processedLength = 0;
 7 
 8 $records = [];
 9 
10 while ($processedLength < $dataLength) {
11     $records[] = (string) $data->substr($processedLength, 40);
12     $processedLength += 40;
13 }
```

In **Figure 14.9**, we are extracting the strings representing each record within our larger data string. On line 3, we convert our data string into a fluent string instance to give us access to many helper methods. On line 4, we retrieve the total length of our data string; in our example, this is still 200 characters.

On line 6, we are defining a variable, `$processedLength`, which we will use to keep track of the number of characters we’ve processed within our data string. We use this between lines 10 and 13.

On line 11, we are extracting substrings from our larger data string and adding each one to our records array. Let’s talk through how this particular strategy actually works.

We know that each record contains forty characters. On the first iteration, our processed length will have the value zero. When we call the substring method at this point, it will extract the first forty characters from the data string. We then increment our `$processedLength` variable on line 12.

On the second iteration, our substring will start on character forty and retrieve the following forty characters. This process will repeat until we’ve exhausted our string. After our code has been executed, our records array would contain the following data:

Figure 14.10 

```
1 array:5 [
2   0 => "         1        12         5         1"
3   1 => "         2     32.32         1         2"
4   2 => "         3        16        10         3"
5   3 => "         4       622         4         4"
6   4 => "         5        77         1         5"
7 ]
```

We are getting close to achieving our goal. However., we are now in the same situation as before, but this time for each record within our dataset. Luckily, we can use the same process of extracting substrings to convert our data into individual fields:

Figure 14.11 Extracting Column Values from String Records 

```
 1 <?php
 2 
 3 $data = str($textData);
 4 $dataLength = $data->length();
 5 
 6 $processedLength = 0;
 7 
 8 $records = [];
 9 
10 while ($processedLength < $dataLength) {
11     $record = $data->substr($processedLength, 40);
12 
13     // Convert our string into an invoice record.
14     $records[] = [
15         'number' => intval((string) $record->substr(0, 10)),
16         'total' => floatval((string) $record->substr(10, 10)),
17         'quantity' => intval((string) $record->substr(20, 10)),
18         'pid' => intval((string) $record->substr(30, 10)),
19     ];
20 
21     $processedLength += 40;
22 }
```

We are getting close to achieving our goal. However., we are now in the same situation as before, but this time for each record within our dataset. Luckily, we can use the same process of extracting substrings to convert our data into individual fields:

In **Figure 14.11**, our approach is similar but looks slightly different from what we did before. The main difference is that we do not need to keep track of the number of characters we’ve processed for each record since we know exactly where each value will appear when we are in the context of an individual record. Between lines 14 and 19, we extract different substrings and call either PHP’s `intval` or `floatval` functions to convert our strings into the appropriate data type. Once this process has been completed, our resulting records array will match the invoices array we started this chapter with.

Since we know that each of our records is exactly forty characters in length, it is trivial for us to retrieve individual records without processing the entire data string. To do this, we will just need to compute the starting offset of each individual record based on the record number we want to retrieve.

For example, if we wanted record number 1, we would start at offset 0; if we wished to retrieve record 2, we would start at offset 40, and so on. This is relatively simple to encapsulate into its own function and will, in fact, make our previous implementation simpler to reason with. The implementation in **Figure 14.12** will use zero-based indexes, as it helps to make our math simpler:

Figure 14.12 Function to Retrieve Individual Invoices 

```
 1 <?php
 2 
 3 function getInvoice($data, $recordNumber) {
 4     // Prevent attempting to read before the start of the data.
 5     if ($recordNumber < 0) { return null; }
 6 
 7     $strData = str($data);
 8 
 9     $startIndex = $recordNumber * 40;
10     
11     // Prevent reading past the end of the data.
12     if ($startIndex >= $strData->length()) { return null; }
13 
14     $record = $strData->substr($startIndex, 40);
15 
16     return [
17         'number' => intval((string) $record->substr(0, 10)),
18         'total' => floatval((string) $record->substr(10, 10)),
19         'quantity' => intval((string) $record->substr(20, 10)),
20         'pid' => intval((string) $record->substr(30, 10)),
21     ];
22 }
```

Our `getInvoice` function receives the entire data string as its first argument and the desired record number as its second. Our logic contained between lines 4 and 12 guards against accidentally reading data before or after the contents of our data string. If the requested record exceeds the boundary of our data, we return null. Apart from this, lines 14-21 remain relatively unchanged compared to our previous implementation.

We can use our new function like so to retrieve an individual invoice from our text data:

Figure 14.13 

```
1 <?php
2 
3 // Retrieve the last record from our invoices table.
4 getInvoice($textData, 4);
```

Which returns the following array of data:

Figure 14.14 

```
1 array:4 [
2   "number" => 5
3   "total" => 77.0
4   "quantity" => 1
5   "pid" => 5
6 ]
```

To retrieve all of our invoices like before, we can compute the total amount of expected records based on the data string length and the size of each record. Once we know the expected number of data records, we can simply use a for loop to retrieve all of the original invoices:

Figure 14.15 

```
 1 <?php
 2 
 3 // Calculate the total number of expected records.
 4 $totalRecords = str($textData)->length() / 40;
 5 
 6 $records = [];
 7 
 8 // Iterate each record and retrieve the invoice data.
 9 for ($i = 0 ; $i < $totalRecords; $i++) {
10     $records[] = getInvoice($textData, $i);
11 }
```

### 14.1 Managing Data Conversions

In the previous section, we worked to convert our string data back into our original records. In **Figure 14.11**, we used PHP’s `intval` and `floatval` functions to convert our strings into PHP data types. Converting our initial data into strings and then from strings back into floats and integers are examples of data conversion. It is relatively rare that data will be stored strictly as-is, without any conversion process.

Let us revisit the idea of converting our invoice data into a fixed-width string format. Still, instead of simply encoding everything as a string, let’s decide that all financial data, such as our total, will be stored with trailing zeroes, up to two digits of precision. We can accomplish this by making use of PHP’s `number_format` function:

Figure 14.16 Formatting Numbers when Converting Invoice Data 

```
 1 <?php
 2 
 3 $textData = collect($invoices)->map(function ($invoice) {
 4     $totalFormatted = number_format($invoice['total'], 2);
 5 
 6     return str('')
 7         ->append(str($invoice['number'])->padLeft(10))
 8         ->append(str($totalFormatted)->padLeft(10))
 9         ->append(str($invoice['quantity'])->padLeft(10))
10         ->append(str($invoice['pid'])->padLeft(10));
11 })->join('');
```

Now, when we convert our invoice array into a data string, we see results similar to the following:

Figure 14.17 

```
1 1     12.00         5         1         2     32.32         1         2
2 3     16.00        10         3         4    622.00         4         4
3 5     77.00         1         5
```

If we look closely at the data in output in **Figure 14.17**, we can see that we have an exciting opportunity. Because we have decided that all currency values will *always* be stored with up to two digits of precision, it has become redundant to store the actual decimal separator. If we were to remove it, our storage field would be able to contain an additional digit that was previously being used by the separator character. We can also do this by slightly modifying our existing implementation to let PHP know we do not want any separator characters. We achieve this by supplying an empty string for both the decimal and thousandths separator arguments:

Figure 14.18 Removing the Decimal Separtor 

```
 1 <?php
 2 
 3 $textData = collect($invoices)->map(function ($invoice) {
 4     $totalFormatted = number_format($invoice['total'], 2);
 5     $totalFormatted = number_format($invoice['total'], 2, '', '');
 6 
 7     return str('')
 8         ->append(str($invoice['number'])->padLeft(10))
 9         ->append(str($totalFormatted)->padLeft(10))
10         ->append(str($invoice['quantity'])->padLeft(10))
11         ->append(str($invoice['pid'])->padLeft(10));
12 })->join('');
```

Encoding our data using the modifications in **Figure 14.18**, our output would now be:

Figure 14.19 

```
1          1      1200         5         1         2      3232         1
2 2         3      1600        10         3         4     62200         4
3 4         5      7700         1         5
```

Our generated data string in **Figure 14.19** is still the same length as before, so our total record calculations will still be correct. However, our changes will present a new problem when attempting to retrieve the total currency amount of each invoice. Specifically, the challenge is that each total now looks similar to:

Figure 14.20 

```
1 3232
```

There are actually several different approaches to solving this problem. If we look carefully at our new numbers, we can see that all we have actually done by removing the decimal place is to multiply the original total by 100. We can make this assumption since we know that our invoice totals will always be stored with precisely 2 digits of precision. More specifically, we can state that what we are actually storing is the significand of a base ten number, with an exponent of -2:

![32.32 = \\underbrace{3232}\_{\\text{significand}} x {\\underbrace{10}\_{\\text{base}}}^{\\overbrace{-2}^{exponent}}](images/leanpub_equation_0.png)

We can update our existing `getInvoice` function to do this with relative ease:

Figure 14.21 

```
 1 <?php
 2 
 3 function getInvoice($data, $recordNumber) {
 4     // Prevent attempting to read before the start of the data.
 5     if ($recordNumber < 0) { return null; }
 6 
 7     $strData = str($data);
 8 
 9     $startIndex = $recordNumber * 40;
10     
11     // Prevent reading past the end of the data.
12     if ($startIndex >= $strData->length()) { return null; }
13 
14     $record = $strData->substr($startIndex, 40);
15 
16     return [
17         'number' => intval((string) $record->substr(0, 10)),
18         'total' => intval((string) $record->substr(10, 10)) / 100,
19         'quantity' => intval((string) $record->substr(20, 10)),
20         'pid' => intval((string) $record->substr(30, 10)),
21     ];
22 }
```

Now, our invoices will be retrieved with the correct invoice total.

Another approach to solving this problem would be reconstructing the original string by extracting its component parts and then recombining them. We can do this in our example by extracting two substrings: the first will be everything up to the last two characters, and the second substring will contain the last two characters.

Once we have our two component parts, we can concatenate them all by using a decimal separator in between them and then using PHP’s `floatval` function:

Figure 14.22 Parsing Invoice Totals Using Substrings and Concatenation 

```
 1 <?php
 2 
 3 function getInvoice($data, $recordNumber) {
 4     // Prevent attempting to read before the start of the data.
 5     if ($recordNumber < 0) { return null; }
 6 
 7     $strData = str($data);
 8 
 9     $startIndex = $recordNumber * 40;
10     
11     // Prevent reading past the end of the data.
12     if ($startIndex >= $strData->length()) { return null; }
13 
14     $record = $strData->substr($startIndex, 40);
15 
16     $total = $record->substr(10, 10);
17     
18     $integer  = $total->substr(0, 8);
19     $fraction = $total->substr(8);
20 
21     $parsedTotal = floatval($integer . '.' .$fraction);
22 
23     return [
24         'number' => intval((string) $record->substr(0, 10)),
25         'total' => $parsedTotal,
26         'quantity' => intval((string) $record->substr(20, 10)),
27         'pid' => intval((string) $record->substr(30, 10)),
28     ];
29 }
```

With regards to the string concatenation method, we can simplify this further by cleverly using the `substrReplace` method. We can specify a replacement length of zero to effectively insert new strings at arbitrary positions. For our use case, we can insert the decimal separator by specifying an offset of 8 and a length of 0:

Figure 14.23 

```
 1 <?php
 2 
 3 function getInvoice($data, $recordNumber) {
 4     // Prevent attempting to read before the start of the data.
 5     if ($recordNumber < 0) { return null; }
 6 
 7     $strData = str($data);
 8 
 9     $startIndex = $recordNumber * 40;
10     
11     // Prevent reading past the end of the data.
12     if ($startIndex >= $strData->length()) { return null; }
13 
14     $record = $strData->substr($startIndex, 40);
15 
16     return [
17         'number' => intval((string) $record->substr(0, 10)),
18         'total' => floatval(
19             (string) $record->substr(10, 10)->substrReplace('.', 8, 0)
20         ),
21         'quantity' => intval((string) $record->substr(20, 10)),
22         'pid' => intval((string) $record->substr(30, 10)),
23     ];
24 }
```

We have focused quite heavily on integers and decimal numbers throughout this section. Still, it is pervasive to see almost all data types being converted to and from their storage formats. In particular, this method is often used with dates; when working with fixed-width data formats, you should always seek documentation surrounding how that data has been formatted and which steps should be taken to retrieve it.

### 14.2 Updating an Individual Record’s Values

In the previous section, we used the `substrReplace` method to insert a decimal separator into a string of numbers. We can make further use of this method to actually update the value of an individual record. For example, assuming the following data string:

Figure 14.24 

```
1          1      1200         5         1         2      3232         1
2 2         3      1600        10         3         4     62200         4
3 4         5      7700         1         5
```

We could update the product identifier of the third record quite easily; the steps to do this are straightforward, as we only need to determine the starting offset of the product identifier for the given record we are interested in.

Like before, we can determine the initial starting offset by multiplying our target record number by 40. Once we have this, we need to calculate the relative offset of the column we want to update. For our sample invoice data, we have specified that each column of data will contain ten characters in the formatted output.

We will continue to use zero-based indexes when determining the offsets of a particular field and then multiply that by ten to arrive at the relative offset. We can add the relative offset to the record’s offset to know where to begin inserting our new data.

Figure 14.25 Updating Individual Fields within a Set of Records 

```
 1 <?php
 2 
 3 function updateData($data, $recordNumber, $fieldNumber, $newData) {
 4     // Calculate the starting offset of the record.
 5     $startIndex = $recordNumber * 40;
 6 
 7     // Calculate the relative offset of our target field.
 8     $fieldIndex = $fieldNumber * 10;
 9 
10     // Combine both offsets to get the starting index of our data.
11     $dataOffset = $startIndex + $fieldIndex;
12 
13     // Replace the existing data with our new data.
14     return (string) str($data)
15         ->substrReplace($newData, $dataOffset, 10);
16 }
```

We can now use our `updateData` function to update the product identifier of the third record:

Figure 14.26 

```
1 <?php
2 
3 $newData = updateData(
4     $textData, // The original data string.
5     2, // The zero-based index of our record.
6     3, // The zero-based index of our field.
7     str(3)->padLeft(10) // The new data to store.
8 );
```

Which produces the new data string:

Figure 14.27 

```
1          1      1200         5         1         2      3232         1
2 2         3      1600        10         3         4     62200         4
3 4         5      7700         1         5
```

Our method for calculating the offsets of arbitrary record fields was generalized because we know that each field within our dataset has a consistent width. If the widths of our fields were variable, our approach would be to take the sum of all field widths that appear before our target field.

### 14.3 Techniques for Managing Text Truncation

Text truncation is one of the more challenging aspects of working with fixed-width data formats. Since, by definition, our storage format is of a fixed length, any text we attempt to store that exceeds the size of any given field will not fit. Some systems will provide a warning when this is about to occur or even trigger a fatal error to prevent truncating data.

Let’s take a look at **Table 14.2**, which contains some example data we will work to store in a limited data format:

Table 14.2 Example Text Data

 
| Record Number || Text Value |
| --- | --- |
| 1 || Lorem ipsum dolor sit amet |
| --- | --- |
| 2 || Nam finibus nulla non bibendum bibendum |
| 3 || Ut sed ante euismod, vulputate justo sit amet |

which we will represent with the following PHP array:

Figure 14.28 

```
 1 <?php
 2 
 3 $data = [
 4     [
 5         'record_no' => 1,
 6         'text' => 'Lorem ipsum dolor sit amet',
 7     ],
 8     [
 9         'record_no' => 2,
10         'text' => 'Nam finibus nulla non bibendum bibendum',
11     ],
12     [
13         'record_no' => 3,
14         'text' => 'Ut sed ante euismod, vulputate justo sit amet',
15     ]
16 ];
```

Like we’ve done before, we are going to work to store our data array in a fixed-width data format. We will say that our record numbers will be stored using three characters, and our text data will be stored with up to ten characters:

Figure 14.29 Throwing Exceptions on Data Truncation 

```
 1 <?php
 2 
 3 $dataString = collect($data)->map(function ($record) {
 4     $textValue = str($record['text']);
 5 
 6     if ($textValue->length() > 10) {
 7         throw new Exception('Text value would be truncated.');
 8     }
 9 
10     return str('')
11         ->append(str($record['record_no'])->padLeft(3))
12         ->append($textValue->padRight(10));
13 })->join('');
```

Our code in **Figure 14.29** will currently throw an exception whenever we attempt to store data that exceeds ten characters. This check happens between lines 6 and 8. We can ask ourselves how we may be able to persist our data even if it exceeds the length of an individual record?

One method I have encountered quite often is to simply append additional data records that continue the data for each field that would have been truncated. Some implementations may add a different field, such as a sequence number, or as a way to identify an entirely different record type to help keep track of which additional records belong together. We will simply reuse our record number for each subsequent record we create to store text that would have been truncated.

An implementation of this may be found in **Figure 14.30**:

Figure 14.30 Preventing Truncated Data 

```
 1 <?php
 2 
 3 $dataString = collect($data)->map(function ($record) {
 4     $recordNumber = str($record['record_no'])->padLeft(3);
 5     $textValue = $record['text'];
 6     $textValues = mb_str_split($textValue, 10);
 7 
 8     return collect($textValues)->map(function ($textValue)
 9                                           use ($recordNumber) {
10         return $recordNumber->append(
11             str($textValue)->padRight(10)
12         );
13     });
14 })->map(function ($data) {
15     return $data->join('');
16 })->join('');
```

A lot is going on in **Figure 14.30**, but we will work to break it down together. On line 4, we are constructing the final version of our record number since it will not change for any of the additional records if our text exceeds 10 characters. On line 6, we are using PHP’s `mb_str_split` function to break up our input string into an array. The benefit of using the `mb_str_split` function is that passing the argument 10 will split our string into an array of substrings, with a maximum length of 10 characters per substring.

One key difference with our new implementation is that our first `map` method will return an array containing all of the storage records for each input record. As an example of this, the first record would produce the following array to store all of the text:

Figure 14.31 Example of Multiple Output Records per Input Record 

```
1 array:3 [
2   0 => "  1Lorem ipsu"
3   1 => "  1m dolor si"
4   2 => "  1t amet    "
5 ]
```

Each of our input records will produce an array similar to that in **Figure 14.31**. Because of this, we need to combine all of those records into a single string, which we do within the `map` method body on line 15. This will result in a collection instance containing an array of single lines, which we further combine on line 16 to produce the following final result:

Figure 14.32 Example Output of Producing Multiple Output Records per Input Record 

```
1   1Lorem ipsu  1m dolor si  1t amet      2Nam finibu  2s nulla no  2n b
2   ibendum  2 bibendum   3Ut sed ant  3e euismod,  3 vulputate  3 justo 
3   sit  3 amet
```

Reversing the process is a bit more complicated for our output in **Figure 14.32**, but it is definitely doable. Our approach will be to retrieve every record first, group them by their record number, and then combine all of the different text values to construct our original string:

Figure 14.33 Reconstructing Single Records from Multiple Storage Records 

```
 1 <?php
 2 
 3 $records = collect(mb_str_split($input, 13))
 4     ->map(function ($record) {
 5 
 6     $recordStr = str($record);
 7     $recordNumber = intval((string) $recordStr->substr(0, 3));
 8     $text = (string) $recordStr->substr(3);
 9 
10     return [
11         'record_no' => $recordNumber,
12         'text' => $text
13     ];
14 })->groupBy('record_no')->map(function ($group) {
15     // Remove the last entry.
16     $lastLine = $group->pop();
17 
18     // Retrieve our record number.
19     $recordNumber = $lastLine['record_no'];
20 
21     // Join all but the last text values.
22     $textValue = $group->map(function ($line) {
23         return $line['text'];
24     })->join('');
25 
26     // Trim the end of the last entry, and append it to our value.
27     $textValue .= str($lastLine['text'])->rtrim;
28 
29     return [
30         'record_no' => $recordNumber,
31         'text' => $textValue
32     ];
33 })->all();
```

We are using the `mb_str_split` function again on line 3. This time, however, we are using it split our larger data string into an array containing substrings of length 13. We could do this without breaking up the entire string, which would be beneficial on extensive input text, but knowing that we want to retrieve all of the records anyway, there is not much harm in it for now.

Between lines 6 and 13, we are retrieving the integer record number and the intermediate text value for each record represented by our data string. At this stage, our data will look similar to the following sample array:

Figure 14.34 

```
 1 array:12 [
 2   0 => array:2 [
 3     "record_no" => 1
 4     "text" => "Lorem ipsu"
 5   ]
 6   1 => array:2 [
 7     "record_no" => 1
 8     "text" => "m dolor si"
 9   ]
10   2 => array:2 [
11     "record_no" => 1
12     "text" => "t amet    "
13   ]
14   // ...
15 ]
```

We then group all of our intermediate records on line 14 by their record number, which we then work with inside another `map` method call.

On line 16, we are removing the last entry of the intermediate records. We are doing this because we want to trim the trailing whitespace from this record since each text value is padded out to 10 characters. We do not want to remove any trailing whitespace on any of the other records since that whitespace would have been part of the data that caused the original value to exceed the size of our field.

With the last entry removed, we combine all the other text values on lines 22 through 24; finally, on line 27, we append the trimmed value of the last line.

Once our implementation has been executed, we will receive back our original array of data:

Figure 14.35 

```
 1 array:3 [
 2   1 => array:2 [
 3     "record_no" => 1
 4     "text" => "Lorem ipsum dolor sit amet"
 5   ]
 6   2 => array:2 [
 7     "record_no" => 2
 8     "text" => "Nam finibus nulla non bibendum bibendum"
 9   ]
10   3 => array:2 [
11     "record_no" => 3
12     "text" => "Ut sed ante euismod, vulputate justo sit amet"
13   ]
14 ]
```

## 15\. Splitting Strings

Accepting input strings and converting them into an array of data following some set of rules is a prevalent task when developing almost any type of application. Laravel, and PHP, provide many different helper methods and functions that help to accomplish this, and some we have already seen, such as PHP’s `mb_str_split` function.

One of the most common tasks for doing this is to split a comma-separated string into an array of strings. In **Figure 15.1**, we can see a simple PHP program that separates some input text on the comma character:

Figure 15.1 

```
1 <?php
2 
3 function splitString($value) {
4     return str($value)->explode(',')
5         ->map(fn($x) => ltrim($x))
6         ->all();
7 }
8 
9 splitString('hello, world');
```

Which produces the following list of strings:

Figure 15.2 

```
1 array:2 [
2   0 => "hello"
3   1 => "world"
4 ]
```

This particular example is relatively trivial to reason with and implement, but what if our application’s requirements change and we need to break the following string:

Figure 15.3 

```
1 hello, "Hello, world", '"hello ", world!', world
```

Into this array?

Figure 15.4 

```
1 array:4 [
2   0 => "hello"
3   1 => "Hello, world"
4   2 => ""hello ", world!"
5   3 => "world"
6 ]
```

Minor changes to our requirements like this can dramatically increase the complexity of our problem, and it may not be obvious where we should even start solving it. We will discuss these issues in this chapter; we will begin with more straightforward techniques and slowly increase the difficulty of the problems as we progress.

### 15.1 Basic String Splitting

In the introduction of this chapter, we saw an example of one of the most basic ways we can split a string: using the `explode` helper method. There is not much else to add about this particular method compared to what we have discussed in previous sections. Still, we can explore some interesting use cases and address a common misconception.

We know that we can use the following to split by a single character:

Figure 15.5 

```
1 <?php
2 
3 // Returns ["one", "two", "three"]
4 str('one, two, three')->explode(',')
5     ->map(fn($x) => ltrim($x))
6     ->all();
```

But in discussions with people over the years, one point of confusion is how to split a string based on larger “chunks.” I believe this is caused by almost always encountering these methods used to separate a string on a single character, but the vital thing to note is that these methods can split a string on *any* substring. For example, we can split the following string on the “OR” keyword:

Figure 15.6 Example of Splitting a String on Substrings 

```
1 <?php
2 
3 str('this OR that OR some other thing or another thing')
4     ->explode('OR')
5     ->map(fn($x) => trim($x))
6     ->all();
```

Which would produce the following output:

Figure 15.7 Example Output of Splitting Strings on Substrings 

```
1 array:3 [
2   0 => "this"
3   1 => "that"
4   2 => "some other thing or another thing"
5 ]
```

If we closely compare the input in **Figure 15.6** to the output generated in **Figure 15.7**, we will notice that the `explode` helper method is case-sensitive. The final element of our output array is “some other thing or another thing,” which contains a lower-case version of our separator string.

The `explode` method accepts a second argument: a limit on the number of substrings it will produce. By default, this is configured to effectively not limit the number of substrings it will create, but we can change this. To demonstrate its usage, let us look at **Figure 15.8**, where we now limit the number of substrings produced:

Figure 15.8 Limiting the Number of Substrings Produced 

```
1 <?php
2 
3 dd(str('this OR that OR some other thing or another thing')
4     ->explode('OR', 2)
5     ->map(fn($x) => trim($x))
6     ->all())
```

This results in the array in **Figure 15.9**:

Figure 15.9 Example Output of Limiting the Number of Substrings Produced 

```
1 array:2 [
2   0 => "this"
3   1 => "that OR some other thing or another thing"
4 ]
```

Our output is undoubtedly interesting, but it may not always be clear how we can take advantage of this behavior. Let us consider the following PHPDoc comment, which documents the fluent `whenEndsWith` method (content after the parameter names was added for discussion purposes):

Figure 15.10 

```
1 /**
2  * Execute the given callback if the string ends with a given substring.
3  *
4  * @param  string|string[]  $needles The needles.
5  * @param  callable  $callback The callback.
6  * @param  callable|null  $default The default value, if any.
7  * @return static
8  */
```

Suppose we wanted to write an incredibly simple parser to help analyze our PHP comment. We will make a few assumptions at this time. The first assumption is that our comment’s first and last lines will never contain actual content and will serve as the start and end of our comment. Our second assumption will be that each line that contains content will always have exactly one space following the first asterisk character. Finally, our last assumption is that we will not have spaces following the param or return keywords in our type definitions. With our assumptions out of the way, we can begin implementing a naïve PHP comment parser.

Like when we implemented our Gherkin parser, we will start by creating data models to represent our parsed comments. Our parser will be incredibly simple, and we will only work to break our comments into a list of “tags” and all of the content that was not part of a tag. We will say that tags are defined on lines that begin with the “@” character. Our PHP classes to encapsulate this structure can be found in **Figure 15.11**:

Figure 15.11 Simple PHP Comment Data Models 

```
 1 <?php
 2 
 3 class PhpComment
 4 {
 5     /**
 6      * The comment's content.
 7      *
 8      * @var string
 9      */
10     public string $content = '';
11 
12     /**
13      * The comment's tags.
14      *
15      * @var TagLine[]
16      */
17     public array $tags = [];
18 }
19 
20 class TagLine
21 {
22     /**
23      * The tag's name.
24      *
25      * @var string
26      */
27     public string $tag = '';
28 
29     /**
30      * The tag's individual components.
31      *
32      * @var string[]
33      */
34     public array $parts = [];
35 }
```

**Figure 15.12** contains the implementation for our naïve PHP parser implementation. It is a naïve implementation since it is not set up to handle more complicated comments, such as those that contain spaces within a parameter’s type definition.

Figure 15.12 Naïve PHP Comment Parser Implementation 

```
 1 <?php
 2 
 3 class NaiveCommentParser
 4 {
 5 
 6     /**
 7      * Parses the provided text into a PhpComment object.
 8      *
 9      * @param string $comment The text to parse.
10      * @return PhpComment
11      */
12     public function parse(string $comment): PhpComment
13     {
14         $phpComment = new PhpComment();
15 
16         $lines = str($comment)->lineSplit->all();
17 
18         // Remove the first and last lines.
19         array_shift($lines);
20         array_pop($lines);
21 
22         $lines = collect($lines)->map(function ($line) {
23             // Remove the leading whitespace and asterisk.
24             return (string) str($line)->ltrim->substr(1)->ltrim;
25         })->reject(function ($line) {
26             // Removes empty lines.
27             return str($line)->trim->length == 0;
28         })->values()->all();
29 
30         $contentLines = [];
31         $keywordLines = [];
32 
33         for ($i = 0; $i < count($lines); $i++) {
34             $line = $lines[$i];
35 
36             if (Str::startsWith($line, '@')) {
37                 $keywordLines = array_slice($lines, $i);
38                 break;
39             }
40 
41             $contentLines[] = $line;
42         }
43 
44         $phpComment->content = implode("\n", $contentLines);
45 
46         $phpComment->tags = collect($keywordLines)
47                 ->map(function ($line) {
48 
49             $parts = str($line)->explode(' ', 6)->all();
50             $tagLine = new TagLine();
51 
52             $tagLine->tag = $parts[0];
53             $tagLine->parts = collect($parts)->skip(1)
54                 ->reject(function ($part) {
55 
56                 return str($part)->trim->length == 0;
57             })->all();
58 
59             return $tagLine;
60         })->all();
61 
62         return $phpComment;
63     }
64 }
```

We can now use our comment parser like so:

Figure 15.13 

```
 1 <?php
 2 
 3 $comment = <<<'COMMENT'
 4 /**
 5  * Execute the given callback if the string ends with a given substring.
 6  *
 7  * @param  string|string[]  $needles The needles.
 8  * @param  callable  $callback The callback.
 9  * @param  callable|null  $default The default value, if any.
10  * @return static
11  */
12 COMMENT;
13 
14 
15 $parser = new NaiveCommentParser();
16 $parsedComment = $parser->parse($comment);
```

To produce the following output:

Figure 15.14 

```
 1 PhpComment {
 2   content: "Execute the given callback if the string ends with a given \
 3 substring."
 4   tags: array:4 [
 5     0 => TagLine {
 6       tag: "@param"
 7       parts: array:3 [
 8         2 => "string|string[]"
 9         4 => "$needles"
10         5 => "The needles."
11       ]
12     }
13     1 => TagLine {
14       tag: "@param"
15       parts: array:3 [
16         2 => "callable"
17         4 => "$callback"
18         5 => "The callback."
19       ]
20     }
21     2 => TagLine {
22       tag: "@param"
23       parts: array:3 [
24         2 => "callable|null"
25         4 => "$default"
26         5 => "The default value, if any."
27       ]
28     }
29     3 => TagLine {
30       tag: "@return"
31       parts: array:1 [
32         1 => "static"
33       ]
34     }
35   ]
36 }
```

Let us break down what is going on in **Figure 15.12**. On line 16, we break our input string into an array of lines to make it easier to work with. Lines 19 and 20 remove the first and last lines, respectively. These correspond to our input string’s “/\*” and “/” lines.

Once have reduced the line array, we then work to remove the leading whitespace and asterisk that appears at the beginning of every line. This happens within the map method body between lines 22 and 25. At this stage, our lines array would contain the following items:

Figure 15.15 

```
1 array:6 [
2   0 => "Execute the given callback if the string ends with a given subs\
3 tring."
4   1 => ""
5   2 => "@param  string|string[]  $needles The needles."
6   3 => "@param  callable  $callback The callback."
7   4 => "@param  callable|null  $default The default value, if any."
8   5 => "@return static"
9 ]
```

You will see in **Figure 15.15** that we have an empty line as the second element in our array. For our purposes, these are just noise and can be removed. Removing these blank lines occurs between lines 25 and 27 of **Figure 15.12**.

At this point, things begin to get exciting with our implementation. The process we implement throughout the remainder of the method is to split all of our lines into one of two arrays: the content lines and the keyword lines.

This happens between lines 33 and 42. We iterate all of our lines and check if the string starts with the “@” character. If the line does not begin with this character, we add it to our content lines list. However, if the line does begin the “@” character, we stop iterating our strings entirely and then use PHP’s `array_slice` function to retrieve all of the lines starting at the point we encountered our first “@’ character.

At this point of our method’s execution, we will have the following two arrays created from our sample input:

Figure 15.16 $contentLines Array Elements 

```
1 array:1 [
2   0 => "Execute the given callback if the string ends with a given subs\
3 tring."
4 ]
```

Figure 15.17 $keywordLines Array Elements 

```
1 array:4 [
2   0 => "@param  string|string[]  $needles The needles."
3   1 => "@param  callable  $callback The callback."
4   2 => "@param  callable|null  $default The default value, if any."
5   3 => "@return static"
6 ]
```

Once we have our two new arrays containing our content tag lines, we combine all our content lines together on line 44. From here, we work to create all of our `TagLine` instances between lines 46 and 60.

Our general approach is to iterate all our tag lines and map them into their corresponding `TagLine` instance. On line 49, we are calling `explode` on our line but are limiting the results to 6. For our first line, our `$parts` array on line 49 would contain the following elements:

Figure 15.18 

```
1 array:6 [
2   0 => "@param"
3   1 => ""
4   2 => "string|string[]"
5   3 => ""
6   4 => "$needles"
7   5 => "The needles."
8 ]
```

We can see in **Figure 15.18** that the last element contains spaces due to us limiting the number of substrings the explode method would create. The remainder of our method sets the values of our `$tag` and `$parts` `TagLine` members and returns the results.

### 15.2 Splitting Strings Using Regular Expressions

Towards the end of Chapter 14, we encountered PHP’s `mb_str_split` function and were using it to break an input string into an array of substrings, with each substring containing up to a certain amount of characters. We can accomplish the same thing using the `split` method on fluent string instances when supplying an integer argument. The following example splits our input string into an array of 3 substrings, each containing 3 characters:

Figure 15.19 

```
1 <?php
2 
3 // Returns ["123", "456", "789"]
4 str('123456789')
5     ->split(3)
6     ->all();
```

While this is beneficial information, the more exciting aspect of the `split` method is how it differs from the `explode` method. The `split` method can be used to split our input strings using a regular expression.

Figure 15.20 Fluent split Method Signature 

```
 1 <?php
 2 
 3 use Illuminate\Support\Collection;
 4 
 5 /**
 6  * Versions: Laravel 8, 9
 7  *
 8  * @return Collection
 9  */
10 public function split(
11     string|int $pattern,
12            int $limit = -1,
13            int $flags = 0
14 );
```

In **Figure 15.20**, we can see that the `split` method accepts up to three arguments. If we do not supply an integer as the first argument, the method will internally call PHP’s `preg_split` function.

Throughout this book, we have encountered code similar to that in **Figure 15.21**:

Figure 15.21 Using Existing Helpers to Remove Blank Lines 

```
1 <?php
2 
3 str($text)->lineSplit->reject(function ($line) {
4     return str($line)->trim->length == 0;
5 })->values()->all();
```

The intent of this code is to break a piece of input text into an array of individual lines and then remove all of the blank lines. We can achieve the same thing rather quickly using the `split` method and the `PREG_SPLIT_NO_EMPTY` flag to eliminate the blank lines for us:

Figure 15.22 Using split To Remove Blank Lines 

```
1 <?php
2 
3 str($text)
4     ->split("/(\r\n|\n|\r)/", -1, PREG_SPLIT_NO_EMPTY)
5     ->all();
```

If we were to compare the output of **Figure 15.21** and **Figure 15.22**, we would find that both return the same array:

Figure 15.23 Removing Blank Lines Example Output 

```
1 array:4 [
2   0 => "line one"
3   1 => "line two"
4   2 => "line three"
5   3 => "line four"
6 ]
```

### 15.3 Extracting YAML Frontmatter from Documents

When working with text formats, such as Markdown, it is widespread to come across the concept of YAML frontmatter. These frontmatter documents are a section of the otherwise standard Markdown or similar file with a YAML document embedded at the top of the file. This usually looks like the example found in **Figure 15.24**:

Figure 15.24 

```
1 ---
2 title: An Unassuming Title
3 ---
4 
5 This is the content.
6 ---
7 This is more content.
```

From **Figure 15.24**, we can note that the YAML frontmatter is typically delimited from the rest of the document by having a line containing “—” surrounding the front matter. Splitting an input string into its YAML front matter and content is relatively trivial. However, it is also simple enough that we can use it to discuss some other exciting string-splitting techniques.

The first technique we will look at to break our string into its frontmatter and content is one of my favorites, and it is to use a regular expression:

Figure 15.25 

```
 1 <?php
 2 
 3 $content = <<<CONTENT
 4 ---
 5 title: An Unassuming Title
 6 ---
 7 
 8 This is the content.
 9 ---
10 This is more content.
11 CONTENT;
12 
13 str($content)->split(
14     "/^---(\r\n|\n\r)/m", 2, PREG_SPLIT_NO_EMPTY
15 )->all();
```

When executed, **Figure 15.25** would produce the following output array:

Figure 15.26 

```
 1 array:2 [
 2   0 => "title: An Unassuming Title\n"
 3   1 => """
 4     \n
 5     ---\n
 6     The content!\n
 7     \n
 8     this 
 9     """
10 ]
```

From here, we could do further processing to trim our substrings, if necessary. From here, we could do further processing to trim our substrings, if necessary. In **Figure 15.25**, we supply a limit of 2 when invoking the `split` method. We do this to ensure the content string does not also get split on the “—that appears on line 6. Additionally, our regular expression uses the “^” anchor, which tells the engine to begin matching at the beginning of lines; for this to work, we also must supply the multiline, or “m,” modifier.

Another approach using regular expressions would be to use PHP’s `preg_match_all` function with the `PREG_OFFSET_CAPTURE` flag:

Figure 15.27 

```
 1 <?php
 2 $content = <<<CONTENT
 3 ---
 4 title: An Unassuming Title
 5 ---
 6 
 7 This is the content.
 8 ---
 9 This is more content.
10 CONTENT;
11 
12 preg_match_all(
13     '/^---/m',
14     $content,
15     $matches,
16     PREG_OFFSET_CAPTURE
17 );
```

To receive an array of matches like **Figure 15.28**:

Figure 15.28 

```
 1 array:1 [
 2   0 => array:3 [
 3     0 => array:2 [
 4       0 => "---"
 5       1 => 0
 6     ]
 7     1 => array:2 [
 8       0 => "---"
 9       1 => 33
10     ]
11     2 => array:2 [
12       0 => "---"
13       1 => 62
14     ]
15   ]
16 ]
```

Our regular expression is more straightforward than the one we used earlier, but that is okay for what we will work through. What we are going to do is use the offsets from our matches to extract the substrings representing our frontmatter and content. An implementation of this can be found in **Figure 15.29**:

Figure 15.29 

```
 1 <?php
 2 
 3 $firstMatch  = $matches[0][0];
 4 $secondMatch = $matches[0][1];
 5 
 6 $startOfFrontMatter = $firstMatch[1] + 3;
 7 $endOfFrontMatter   = $secondMatch[1];
 8 $startOfContent     = $endOfFrontMatter + 3;
 9 
10 $frontMatterLength = $endOfFrontMatter - $startOfFrontMatter;
11 
12 $frontMatter = str($content)->substr(
13     $startOfFrontMatter, $frontMatterLength
14 )->trim->toString();
15 
16 $content = str($content)->substr($startOfContent)
17     ->ltrim->toString();
```

On lines 3 and 4, we retrieve the matches from **Figure 15.28** that correspond to the first and second instances of the “—” sequence. On line 6, we calculate the offset our frontmatter begins on. Our regular expression will capture the offset where the match *starts*, so we add 3 to move over the “—” sequence. We do a similar thing on line 7 to determine where the frontmatter ends, but we do not need to account for the length of the “—” sequence since our frontmatter ends where it begins.

On line 10, we calculate the length of frontmatter, which is the difference between its end and start offsets. We can then use the frontmatter’s beginning offset and length on lines 12 through 14 to retrieve the substring corresponding to our frontmatter.

Retrieving our content is more straightforward on lines 16 and 17 since we only need to retrieve the substring of everything that appears 3 offsets after the frontmatter ends.

### 15.4 Parsing Single-File Components

In this section, we will work through another example that utilizes regular expressions to help extract information from input strings. We will be working to construct a simple parser to split a single-file component document, similar to those used by front-end tools like Vue.js. **Figure 15.30** contains the sample document we will work with through this section:

Figure 15.30 Example Single-File Component Document 

```
 1 <style>
 2     .hero {
 3 
 4     }
 5 </style>
 6 
 7 <template>
 8     <div class="hero">
 9 
10     </div>
11 </template>
12 
13 <script>
14     var heroElements = document.getElementsByClassName('hero');
15 </script>
```

Our approach to splitting our document into its individual components will be to use a regular expression to locate the start of all HTML tags we are interested in; in our example, those are the style, template, and script tag pairs. Once we have the locations of these tags, we will extract substrings from the original document and return the results.

Before looking at the implementation, let us first take a look at the results of calling PHP’s `preg_match_all` function on our sample input like so:

Figure 15.31 

```
 1 <?php
 2 
 3 $code = <<<CODE
 4 
 5 <style>
 6     .hero {
 7 
 8     }
 9 </style>
10 CODE;
11 
12 preg_match_all(
13   '/^<[\/]?(style|template|script).*>/m',
14   $code,
15   $matches,
16   PREG_OFFSET_CAPTURE
17 );
```

After **Figure 15.31** has executed, we would receive the following output:

Figure 15.32 

```
 1 array:2 [
 2   0 => array:2 [
 3     0 => array:2 [
 4       0 => "<style>"
 5       1 => 2
 6     ]
 7     1 => array:2 [
 8       0 => "</style>"
 9       1 => 33
10     ]
11   ]
12   1 => array:2 [
13     0 => array:2 [
14       0 => "style"
15       1 => 3
16     ]
17     1 => array:2 [
18       0 => "style"
19       1 => 35
20     ]
21   ]
22 ]
```

Our `$matches` result contains two arrays, the first one includes the full text of our match, and the second array contains the positions and text of the matched individual tag. If you notice, the second array contains the tag names but lacks enough information to determine if the tag was a closing tag or not. Our first array does collect this information, but it also includes the angle brackets, which we will avoid stripping out. We will use both arrays in our final implementation to get the information we want and help generate error messages when we find something unexpected.

Currently, our two sub-arrays in **Figure 15.32** have a one-to-one correspondence. That is to say, the first element “<style>” of the first array corresponds to the first element “style” of the second array. We can use this to our advantage when iterating through the second array later; if we are on the first “style” within the second array, we expect to see its closing pair as the second element in the first array, and so on. We can be sure we have encountered an error condition whenever this is not the case. As an example of this, let us consider **Figure 15.33**:

Figure 15.33 

```
 1 <?php
 2 
 3 $code = <<<CODE
 4 
 5 <style>
 6     .hero {
 7 
 8     }
 9 <template>
10 CODE;
11 
12 preg_match_all(
13   '/^<[\/]?(style|template|script).*>/m',
14   $code,
15   $matches,
16   PREG_OFFSET_CAPTURE
17 );
```

Which produces the following output:

Figure 15.34 

```
 1 array:2 [
 2   0 => array:2 [
 3     0 => array:2 [
 4       0 => "<style>"
 5       1 => 2
 6     ]
 7     1 => array:2 [
 8       0 => "<template>"
 9       1 => 33
10     ]
11   ]
12   1 => array:2 [
13     0 => array:2 [
14       0 => "style"
15       1 => 3
16     ]
17     1 => array:2 [
18       0 => "template"
19       1 => 34
20     ]
21   ]
22 ]
```

When we look at **Figure 15.34**, we can see that if we are currently analyzing the first element of the second array, the second element of the first array now contains “<template>” instead of the “</style>” we would expect to see. These are the conditions we will look for to generate our error messages.

We will now work through our single-file component parser implementation. **Figure 15.35** contains the beginning of our implementation:

Figure 15.35 

```
 1 <?php
 2 
 3 class ParseResult
 4 {
 5     public $content = '';
 6     public $type = '';
 7     public $startOffset = 0;
 8     public $endOffset = 0;
 9 }
10 
11 class SingleFileComponentParser
12 {
13 
14     /**
15      * Parses the provided text into individual components.
16      *
17      * @param string $value The text to parse.
18      * @param array $parts The parts to parse.
19      * @return array
20      * @throws Exception
21      */
22     public function parse(
23         $value,
24         $parts = ['style', 'template', 'script'])
25     {
26         // We will use this later to retrieve line and
27         // column numbers if we encounter an error.
28         $positionLocator = new CharacterPositionLocator($value);
29 
30         // Construct a dynamic regex pattern that will
31         // match any of the provided parts.
32         $pattern = collect($parts)
33             ->map(fn($x) => preg_quote($x))->implode('|');
34 
35         preg_match_all(
36             '/^<[\/]?('.$pattern.').*>/m',
37             $value, $matches, PREG_OFFSET_CAPTURE
38         );
39 
40 	  	$tagNames = $matches[1];
41         $sourceTags = $matches[0];
42 
43         // ...
44 
45         return $results;
46     }
47 }
```

On lines 3-9, we define the class into which the individual sections of our single-file component document will be parsed. We will store the content between the opening and closing tags within the `$content` member, the opening tag type in `$type`, and the section’s start and end offsets.

On line 28, we create a new instance of `CharacterPositionLocator`, which we developed together in Chapter 10. We will use this later whenever we encounter an error to use the line and column numbers in our error messages.

Lines 32 and 33 help to construct a dynamic regular expression from the value of the `$parts` parameter. We then use these results on lines 35-38 as part of the full regular expression we have encountered a few times through this section.

Lines 40 and 41 store both arrays returned within our matches into variable names that will be more friendly to work with. The `$sourceTags` array will contain the matches with the included angle brackets, and the `$tagNames` array will contain only the name of the matched tag.

Figure 15.36 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class SingleFileComponentParser
 6 {
 7 
 8     public function parse(
 9         $value,
10         $parts = ['style', 'template', 'script'])
11     {
12 
13         // ...
14 
15         for ($i = 0; $i < count($tagNames); $i++) {
16             $tag = $tagNames[$i];
17 
18             $next = $i + 1;
19 
20             if (! isset($sourceTags[$next])) {
21                 $location = $positionLocator
22                     ->getCharPosition($sourceTags[$i][1]);
23 
24                 throw new Exception("Missing closing tag for".
25                   " '{$tag[0]}' at line {$location->line} " .
26                   "column {$location->column}");
27             }
28 
29             // ...
30         }
31 
32         return $results;
33     }
34 }
```

In **Figure 15.36**, we are starting to get into the actual parsing stage. We have now introduced a loop, which iterates all of the tag names we stored earlier. We retrieve the current tag name on line 16 and then calculate the index of the following tag on line 18. Between lines 20 and 27, we check to see if we even have the next match; if not, we throw an error.

To see this in action, if we invoked our parse with the following input:

Figure 15.37 

```
 1 <?php
 2 
 3 $code = <<<CODE
 4 
 5 <style>
 6     .hero {
 7 
 8     }
 9 CODE;
10 
11 $parser = new SingleFileComponentParser();
12 $parser->parse($code);
```

We would be presented with the following error message:

Figure 15.38 

```
1 Missing closing tag for 'style' at line 2 column 1
```

We will now move on to handling our second error condition in **Figure 15.39**: when we encounter an unexpected closing tag.

Figure 15.39 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class SingleFileComponentParser
 6 {
 7 
 8     public function parse(
 9         $value,
10         $parts = ['style', 'template', 'script'])
11     {
12 
13         // ...
14 
15         for ($i = 0; $i < count($tagNames); $i++) {
16 
17             // ...
18 
19             $nextTag = $sourceTags[$next];
20             $expected = '</'.$tag[0].'>';
21 
22             if ($nextTag[0] != $expected) {
23                 $location = $positionLocator
24                     ->getCharPosition($sourceTags[$i][1]);
25 
26                 throw new Exception("Invalid closing tag " .
27                   "{$nextTag[0]}' for '{$tag[0]}' at ".
28                   "line {$location->line} column {$location->column}");
29             }
30 
31             // ...
32         }
33 
34         return $results;
35     }
36 }
```

On line 19, we retrieve the contents of the following tag from our matches, including the angle brackets. We then construct what we would expect to see on line 20 using our current tag match. We throw a new error message if the next tag does not match our expected value. The following example:

Figure 15.40 

```
 1 <?php
 2 
 3 $code = <<<CODE
 4 
 5 <style>
 6     .hero {
 7 
 8     }
 9 </script>
10 CODE;
11 
12 $parser = new SingleFileComponentParser();
13 $parser->parse($code);
```

Throws this error message:

Figure 15.41 

```
1 Invalid closing tag </script>' for 'style' at line 2 column 1
```

We can now finish our simple single-file component parser:

Figure 15.42 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class SingleFileComponentParser
 6 {
 7 
 8     public function parse(
 9         $value,
10         $parts = ['style', 'template', 'script'])
11     {
12 
13         // ...
14 
15         for ($i = 0; $i < count($tagNames); $i++) {
16 
17             // ...
18 
19             $sourceTag = $sourceTags[$i][0];
20 
21             $start = $sourceTags[$i][1] + str($sourceTag)->length;
22             $end = $nextTag[1];
23 
24             $parseResult = new ParseResult();
25             $parseResult->type = $sourceTag;
26             $parseResult->startOffset = $start;
27             $parseResult->endOffset = $end;
28             $parseResult->content = str($value)
29                 ->substr($start, $end - $start)->toString();
30 
31             $results[] = $parseResult;
32 
33             $i += 1;
34         }
35 
36         return $results;
37     }
38 }
```

Lines 19-22 are concerned with calculating the start and end offsets of the current section we are parsing. Our regular expression match will return the offset at the *beginning* of the match, so we add the length of the original match with angle brackets to this value on line 21 to get the position immediately after the opening tag. The end of our current section will be the starting location of the following tag, which we set on line 22.

Lines 24-31 are trivial and work to create a new instance of `ParseResult` and set all of the values we want to store.

Line 33, however, is a bit curious. We are iterating all of the matches if we think through our approach. We increment our loops index by an additional 1 to skip over the closing tag we just analyzed to create our section.

Invoking our parser on the entire input:

Figure 15.43 

```
 1 <?php
 2 
 3 $code = <<<CODE
 4 <style>
 5     .hero {
 6 
 7     }
 8 </style>
 9 
10 <template>
11     <div class="hero">
12 
13     </div>
14 </template>
15 
16 <script>
17     var heroElements = document.getElementsByClassName('hero');
18 </script>
19 CODE;
20 
21 $parser = new SingleFileComponentParser();
22 $parser->parse($code);
```

Produces the following results, which contain all of the different sections broken out for us:

Figure 15.44 

```
 1 [
 2   ParseResult {
 3     content: """
 4       
 5           .hero {
 6       
 7           }
 8       """,
 9     type: "<style>",
10     startOffset: 7,
11     endOffset: 31,
12   },
13   ParseResult {
14     content: """
15       
16           <div class="hero">
17       
18           </div>
19       """,
20     type: "<template>",
21     startOffset: 53,
22     endOffset: 93,
23   },
24   ParseResult {
25     content: """
26       
27           var heroElements = document.getElementsByClassName('hero');
28       """,
29     type: "<script>",
30     startOffset: 116,
31     endOffset: 183,
32   },
33 ]
```

### 15.5 Splitting Input Containing Substrings with the Delimiter

Suppose we wanted to break the following string into an array on the “,” character:

Figure 15.45 

```
1 one, two, three
```

We can accomplish this easily using the `explode` helper method like so:

Figure 15.46 

```
1 <?php
2 
3 str('one, two, three')
4     ->explode(',')->all();
```

Resulting in the following array:

Figure 15.47 

```
1 array:3 [
2   0 => "one"
3   1 => " two"
4   2 => " three"
5 ]
```

Our results in **Figure 15.47** are what we would expect given our sample input, but let us say we want to split the following string:

Figure 15.48 

```
1 one, "two, three", four, five
```

Into this array:

Figure 15.49 

```
1 array:5 [
2   0 => "one"
3   1 => " two"
4   2 => " "three, four, five""
5   3 => " six"
6   4 => " seven"
7 ]
```

Using the `explode` method on this string produces the following results, which are not quite what we are after:

Figure 15.50 

```
1 array:5 [
2   0 => "one"
3   1 => " "two"
4   2 => " three""
5   3 => " four"
6   4 => " five"
7 ]
```

If we carefully analyze our string in **Figure 15.48**, it is clear why the `explode` method is not producing the expected results. We need to be able to account for strings within our data, which may also contain the character we want to use to break our string. The `explode` method does not know about this and will split our string on every instance of our delimiter.

We will solve this problem by manually iterating our string and splitting it ourselves. When we iterate our string, we can keep track of all the characters we have seen, and every time we encounter the “,” character or the end of the string, we can create a new substring and add it to an array. To account for our delimiter character appearing within string values, we just need a way to know that we are in a string and then ignore the delimiter.

When we first encounter a character that indicates the start of a string, such as the double or single quote characters, we can then say that we are “inside” of a string. When this is the case, we can simply ignore any character we would typically use to split our input. When we see the same character double or single quote again, we can say we are no longer inside the string. We can also account for escape characters by checking if the character before any double or single quote we encounter is the backslash character; if so, we will continue processing our inner string contents. An implementation of this can be found in **Figure 15.51**:

Figure 15.51 Splitting Input Containing Strings 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three, four, five", six, seven'
 5 );
 6 
 7 $isParsingString = false;
 8 $stringTerminator = '';
 9 
10 $results = [];
11 
12 $buffer = '';
13 
14 for ($i = 0; $i < count($iterator); $i++) {
15     $cur = $iterator[$i];
16     $prev = null;
17     $next = null;
18 
19     if ($i > 0) {
20         $prev = $iterator[$i - 1];
21     }
22 
23     if ($i + 1< count($iterator)) {
24         $next = $iterator[$i + 1];
25     }
26 
27     if (!$isParsingString && ($cur == '"' || $cur == "'")
28         && $prev != '\\') {
29         $stringTerminator = $cur;
30         $isParsingString = true;
31         $buffer .= $cur;
32         continue;
33     }
34 
35     if ($isParsingString && $cur == $stringTerminator
36         && $prev != '\\') {
37         $isParsingString = false;
38         $buffer .= $cur;
39         continue;
40     }
41 
42     if (($cur == ',' && !$isParsingString) || $next == null) {
43         if ($next == null) {
44             $buffer .= $cur;
45         }
46         $results[] = $buffer;
47         $buffer = '';
48         continue;
49     }
50 
51     $buffer .= $cur;
52 }
```

The first several lines of **Figure 15.51** are dedicated to keeping track of our final results and maintaining a state to indicate if we are currently inside of a string or not, as well as what type of string we are in. We store the string terminator (double or single quote) on line 8 so that if we are writing a double-quoted string, we do not have to escape all of the single quotes and vice-versa. We will also use this when checking to see if we have reached the end of our string.

Once inside our loop, we retrieve what the current, previous, and following characters are for the current position between lines 15 and 25. We initialize the previous and next characters to null each time, providing an easy value to check if we are at the start or end of the input text.

We will quickly jump to line 51, which adds the current character to our buffer string. This line will be reached when nothing interesting happens; i.e., we are not working with the start or end of a string, and we have not encountered our delimiter character. It is important to note that this buffer will continue growing until we encounter our delimiter or the end of the string.

We perform the actual splitting of string between lines 42 and 49. We check if the current character is “,” and we are not parsing a string or if the next character is `null`, which indicates the end of the input text. If the next character is `null`, we must add it to the current buffer on line 44 before continuing. If we did not add the current character at this time, our output would always be one character short of the expected result. Lines 46 and 47 will add the contents of our buffer to the `$results` array, reset the buffer contents, and then continue iterating through the remainder of the input text.

Our string detection logic occurs between lines 27 and 33. If our current character is a single or double quote, and the previous character is not a backslash (which would indicate an escaped string), and we are not already parsing a string, we know we have just encountered the start of a new string. We then set the type of string we will be parsing, indicate that we are parsing a string, and add the double or single quote to the buffer.

Whenever we are currently parsing a string, and we encounter the same string terminator that was used to *start* the string and is not preceded by a backslash character, we know we are leaving our string. Our logic for this can be found in lines 42-49.

### 15.6 Implementing a String Cursor System

While our implementation in **Figure 15.51** works and can be expanded to handle even more complicated scenarios, writing these types of implementations each time we want to manage nested strings quickly becomes incredibly tedious. We will work throughout the remainder of this section to develop a reusable way to encapsulate this logic.

The overarching concept behind what we will build is a “cursor.” Our cursors will move along our string and “see” the current character and the previous and next character. They can either accept the new character and continue processing or reject it whenever they want to stop processing more text.

Our cursors will work in conjunction with the `Utf8StringIterator`. When a cursor moves onto the next character, the main iterator will also advance by one position. This behavior allows us to use a cursor while iterating our string normally to essentially skip over parts of the string; once the cursor has completed, we can retrieve its results, and our loop continues where the cursor left off.

That is quite a lot to take in, so let us look at how our string splitting implementation could be done using our cursor idea:

Figure 15.52 Splitting a String Using Cursors 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three, four, five", six, seven'
 5 );
 6 $cursor = new ClosureStringCursor($iterator);
 7 $strings = [];
 8 
 9 $cursor->traverseUsing(function ($cur, $prev, $next) use (&$strings) {
10     if ($cur == '"') {
11         $strings[] = $this->bufferCursorResult(
12             new StringsCursor($this->iterator())
13         );
14 
15         return;
16     }
17 
18     if ($cur == ',') {
19         return $this->clearBuffer()->continue();
20     }
21 
22     if ($next == ',' || $next == null) {
23         $strings[] = $this->flushBuffer();
24     }
25 });
```

When our example code in **Figure 15.52** has been executed, our `$strings` array would contain the five elements we see in **Figure 15.49**. **Figure 15.52** actually has two cursors working together.

The first cursor is the `ClosureStringCursor`, which takes the place of a traditional loop. A `ClosureStringCursor` accepts any arbitrary function, which will get at every position along the string until it rejects the input. A cursor can decline the input by returning `false` at any time; if the function returns `void` or `true`, the cursor will continue internally iterating the string.

Internally, each cursor maintains a string buffer, so we do not have to manage those ourselves. Between lines 18-20, we check to see if the current character is a comma; if so, we clear the cursor’s internal buffer and continue processing the input text. Clearing the internal buffer will reset its contents to an empty string, which we will want to do whenever we encounter our delimiter character, so it doesn’t appear in the final output. We also chain the `continue` method, which simply returns `true`, so our cursor continues processing the string.

We also see a similar check happen on lines 22-24, which checks if the *next* character is a comma or `null`, which indicates the end of the string. Instead of clearing the buffer, we see a new method `flushBuffer`, whose output we add to our `$strings` array. When we flush our buffer, the cursor will clear the contents of its internal buffer and return them to us. This is incredibly handy, as it helps us to dramatically clean up our implementations.

However, you may notice that our new versions of these checks do not contain all of the logic to avoid processing commas when inside strings. This is where our cursor idea really starts to get exciting.

On line 10, we are checking if the current character is a double quote. If it is, we see a rather curious call to a method named `bufferCursorResult`. This method accepts *another* cursor that will begin processing our input text at the current position; in our example, it is the `StringsCursor`, which contains all of our logic to extract strings from our input text.

The `bufferCursorResult` method we will build later will let the second cursor perform its task, and then add its results to “outer” cursor’s buffer, and then return its results, allowing us to quickly move our primary cursor over any problematic areas, such as strings containing the character we want to split our string on.

To help visualize this behavior of a cursor advancing the position of other cursors, or the main `Utf8StringIterator`, let us consider the sample code in **Figure 15.54**:

Figure 15.53 Using a Cursor to Skip Sections of a String 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three, four, five", six, seven'
 5 );
 6 
 7 foreach ($iterator as $char) {
 8     if ($char == '"') {
 9         echo (new StringsCursor($iterator))->traverse()->value, "\n";
10         continue;
11     }
12 
13     echo $char, "\n";
14 }
```

Which produces the following output:

Figure 15.54 

```
 1 o
 2 n
 3 e
 4 ,
 5  
 6 t
 7 w
 8 o
 9 ,
10  
11 "three, four, five"
12 ,
13  
14 s
15 i
16 x
17 ,
18  
19 s
20 e
21 v
22 e
23 n
```

We can see an interesting behavior in the output of **Figure 15.54**. Our main loop iterates over each character of our input text and outputs it on a new line. However, if we look at line 11 in **Figure 15.54**, we can see that the entirety of our nested string appears on its own line, separate from everything else. This is because our `StringsCursor` was able to extract our nested string for us, and advance the main iterator so that it can continue processing the rest of the string, without worrying about the region of text processed by the cursor.

We have enough background information to begin working on our cursor implementation; it will be an abstract implementation, allowing us to build other cursor implementations on top of it. To start, we will define our eventual return type, abstract class, and the abstract method that cursor implementations must provide:

Figure 15.55 Beginning Our AbstractStringCursor Implementation 

```
 1 <?php
 2 
 3 class CursorResult
 4 {
 5     public $startPosition = 0;
 6     public $endPosition = 0;
 7     public $length = 0;
 8     public $value = '';
 9     public $content = '';
10 }
11 
12 abstract class AbstractStringCursor
13 {
14     /**
15      * The string being iterated over.
16      *
17      * @var Utf8StringIterator
18      */
19     protected $iterator;
20 
21     // ...
22 
23     public function __construct(Utf8StringIterator $iterator)
24     {
25         $this->iterator = $iterator;
26     }
27 
28     public function iterator()
29     {
30         return $this->iterator;
31     }
32 
33     // ...
34 
35     abstract public function accept(
36         $current,
37         $prev = null,
38         $next = null);
39 
40     // ...
41 }
```

Between lines 3 and 10, we are defining the data type our cursors will return. Our `CursorResult` will keep track of the start and ending positions, the length of the final result, as well as two string values: the value, and the content. Not all of this information is useful in every situation, but it is commonly needed so we will include it as part of our expected result. Let us quickly look at **Figure 15.56**:

Figure 15.56 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three, four, five", six, seven'
 5 );
 6 
 7 foreach ($iterator as $char) {
 8     if ($char == '"') {
 9         $result = new StringsCursor($iterator))->traverse();
10         continue;
11     }
12 }
```

When our code executes, the `$result` variable would contain the following object:

Figure 15.57 Example CursorResult Output 

```
1 CursorResult {
2   startPosition: 10
3   endPosition: 28
4   length: 19
5   value: ""three, four, five""
6   content: "three, four, five"
7 }
```

Our cursor keeps track of the start and end position, as well as the length of the final result. The exciting part is the the `content` value. It is the same as the other value, but with the first and last characters removed for us. It is highly likely that we will want to work with the inner content retrieved by the cursor, and having the cursor remove those characters for us is just a convenience.

In addition to defining the `CursorResult` data type, we have also started our `AbstractStringCursor` implementation. At the moment, it only defines a constructor which accepts a `Utf8StringIterator` instance and its related member and accessor methods, as well as our abstract accept method.

Our abstract method should look familiar: it’s signature contains the three values that we have been using so far to make decisions about our text input when iterating character-by-character. Our abstract cursor will call this method at each position of the string, and use its return value to decide whether or not it should continue. We will now begin work on our `traverse` method.

Figure 15.58 Starting our traverse Method Implementation 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5 
 6     // ...
 7 
 8     protected $initialCharacter;
 9 
10     protected $position = 0;
11 
12     protected $index = 0;
13 
14     public function traverse()
15     {
16         $result = new CursorResult();
17 
18         $lastSize = $this->iterator->lastCharSize();
19         $startPosition = $this->iterator->key();
20 
21         $this->position = $startPosition;
22 
23         $result->startPosition = $startPosition;
24 
25         $this->initialCharacter = $this->iterator->current();
26 
27         // ...
28 
29         return $result;
30     }
31 
32     // ...
33 }
```

The implementation of our `traverse` method begins in **Figure 15.58**. We have defined some additional internal properties that will be used to help maintain state as our cursor traverses a string. As a convenience, we keep track of the initial character, allowing us to easily compare subsequent characters to it without figuring this out in all cursor implementations that require this information.

The `$position` and `$index` values will contain similar information but serve different purposes. The `$position` will keep track of the current character position within the larger string, and the `$index` will keep track of the cursor’s relative position. For example, our output in **Figure 15.57** began at position 10 within the larger input. However, the `$index` would have been 0 at this point. This is because the `$index` counts the number of characters the cursor has seen.

Lines 16 and 29 create an instance of `CursorResult` and return it, respectively. Our first bit of interesting code starts to appear on lines 18 and 19.

We are storing the number of bytes that appeared in the iterator’s last character and its position within the input text. We will use these later when we implement a way to abandon a cursor’s processing. Since our cursors will advance the iterator each time they see a new character, we want to restore it to its original position if we need to exit a cursor early without performing any actual processing.

Now we need to iterate the characters of our input text and call the accept method at each position. This will involve us retrieving the current, next, and previous characters at each position, which is something we have seen a few times already:

Figure 15.59 Traversing Input Text Within a Cursor 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5 
 6     // ...
 7 
 8     protected $buffer = '';
 9 
10     public function traverse()
11     {
12         $result = new CursorResult();
13 
14         $lastSize = $this->iterator->lastCharSize();
15         $startPosition = $this->iterator->key();
16 
17         $this->position = $startPosition;
18 
19         $result->startPosition = $startPosition;
20 
21         $this->initialCharacter = $this->iterator->current();
22 
23         for ($this->position = $startPosition;
24              $this->position < count($this->iterator);
25              $this->position++) {
26             $current = $this->iterator[$this->position];
27             $next = null;
28             $prev = null;
29 
30             if ($this->position > 0) {
31                 $prev = $this->iterator[$this->position - 1];
32             }
33 
34             if ($this->position + 1 < count($this->iterator)) {
35                 $next = $this->iterator[$this->position + 1];
36             }
37 
38             $this->buffer .= $current;
39 
40             if ($this->accept($current, $prev, $next) === false) {
41                 $result->endPosition = $this->iterator->key();
42                 $result->value = $this->buffer;
43                 $result->length = str($this->buffer)->length();
44                 $result->content = str($this->buffer)->
45                 substr(1, -1)->toString();
46                 break;
47             }
48 
49             $this->iterator->next();
50 
51             $this->index += 1;
52         }
53 
54         return $result;
55     }
56 
57     // ...
58 }
```

In **Figure 15.59**, we start by creating our internal string buffer on line 8. Each time we advance our cursor, we will append the current character to this string. We see the main heart of our cursor implementation between lines 23 and 52. Lines 26-36 manage the `$current`, `$next`, and `$previous` character values and line 38 adds the current character to our internal string buffer.

On line 40, we call the `accept` method with the current character state and check if the result is strictly equal to `false`, which indicates the cursor should stop processing the input text. When this happens, we work to set the different values we expect to appear within our final `CursorResult` instance.

If the `accept` method has not returned `false`, we advance the iterator by calling its `next` method and increment our cursor’s internal index before continuing on to the next character.

We will now work to add some additional features to our `AbstractStringCursor` and some utility methods. The first feature will provide a way for a cursor to indicate that they have not processed anything and return the iterator to its original position. Before implementing this feature within our abstract cursor, we will need to add a new method to the `Utf8StringIterator` we developed all the way back in Chapter 1:

Figure 15.60 Adding the setIteratorPosition Method to the Utf8StringIterator 

```
 1 <?php
 2 
 3 class Utf8StringIterator implements
 4     ArrayAccess,
 5     Countable,
 6     Iterator
 7 {
 8     // ...
 9 
10     public function setIteratorPosition(
11         $position,
12         $lastSize)
13     {
14         $this->position = $position;
15         $this->lastSize = $lastSize;
16     }
17 
18     // ...
19 
20 }
```

Our new `setIteratorPosition` method is reasonably straightforward and provides a quick way to set the iterator’s internal position and last byte size. We can use this to move our iterator to any position we’d like without resorting to rewinding it and “catching it up” to our desired location. It is important to note that we must supply the last byte size and the position to account for multi-byte character sequences. We can now use this new method to implement our rest functionality within the abstract string cursor:

Figure 15.61 Implementing Cursor Abandonment 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5 
 6     // ...
 7 
 8     private $shouldReset = false;
 9 
10     public function didNotProcess()
11     {
12         $this->shouldReset = true;
13 
14         return false;
15     }
16 
17     public function traverse()
18     {
19         $result = new CursorResult();
20 
21         $lastSize = $this->iterator->lastCharSize();
22         $startPosition = $this->iterator->key();
23 
24         $this->shouldReset = false;
25 
26         $this->position = $startPosition;
27 
28         $result->startPosition = $startPosition;
29 
30         $this->initialCharacter = $this->iterator->current();
31 
32         for ($this->position = $startPosition;
33              $this->position < count($this->iterator);
34              $this->position++) {
35             $current = $this->iterator[$this->position];
36             $next = null;
37             $prev = null;
38 
39             if ($this->position > 0) {
40                 $prev = $this->iterator[$this->position - 1];
41             }
42 
43             if ($this->position + 1 < count($this->iterator)) {
44                 $next = $this->iterator[$this->position + 1];
45             }
46 
47             $this->buffer .= $current;
48 
49             if ($this->accept($current, $prev, $next) === false) {
50                 if ($this->shouldReset) {
51                     $this->iterator->setIteratorPosition(
52                         $startPosition,
53                         $lastSize
54                     );
55                 }
56 
57                 $result->endPosition = $this->iterator->key();
58                 $result->value = $this->buffer;
59                 $result->length = str($this->buffer)->length();
60                 $result->content = str($this->buffer)->
61                 substr(1, -1)->toString();
62                 break;
63             }
64 
65             $this->iterator->next();
66 
67             $this->index += 1;
68         }
69 
70         return $result;
71     }
72 
73     // ...
74 }
```

Our changes are surprisingly minimal for what this feature will allow us to do. If a cursor calls the `didNotProcess` method, we set an internal flag indicating that we should reset our iterator. This occurs between lines 50 and 55, using our new `setIteratorPosition` method.

The idea of abandoning our cursor’s processing may feel a bit obscure. To help our understanding of this feature, let us take a look at **Figure 15.62**, which makes use of this feature:

Figure 15.62 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three, four, five"'
 5 );
 6 
 7 $closeCursor = new ClosureStringCursor($iterator);
 8 
 9 foreach ($iterator as $char) {
10     echo "Iterator char: ", $char, "\n";
11     if ($char == '"') {
12         $closeCursor->traverseUsing(function ($current) {
13             echo "    Cursor char: ", $current, "\n";
14 
15             if ($current == 'r') {
16                 return $this->didNotProcess();
17             }
18         });
19     }
20 }
```

Our example will iterate through the characters of our string and print each on a new line. If our loop encounters a double quote, we then use a cursor to continue traversing our string.

Within our cursor, we print each character we encounter. However, if we encounter the “r” character, we return the results of the `didNotProcess` method. Doing this causes our cursor to stop processing and return the outer loop to its original position, producing the output in **Figure 15.63**:

Figure 15.63 

```
 1 Iterator char: o
 2 Iterator char: n
 3 Iterator char: e
 4 Iterator char: ,
 5 Iterator char:  
 6 Iterator char: t
 7 Iterator char: w
 8 Iterator char: o
 9 Iterator char: ,
10 Iterator char:  
11 Iterator char: "
12     Cursor char: "
13     Cursor char: t
14     Cursor char: h
15     Cursor char: r
16 Iterator char: t
17 Iterator char: h
18 Iterator char: r
19 Iterator char: e
20 Iterator char: e
21 // ...
```

We can see from **Figure 15.63** that our cursor encountered all characters, starting from the double quote to the lowercase “r.” However, because we invoked the `didNotProcess` method, our outer loop was returned to its position when the cursor was created and processed the same characters.

The next features we will implement will allow us to arbitrarily advance our cursor over a desired number of characters and skip an arbitrary number of characters. These two things sound similar, and they will be implemented similarly. The critical difference between the two features is that advancing our cursor will still append each character it moves over to our internal buffer, and skipping characters will *not* append characters to the buffer.

Figure 15.64 Implementing Character Skipping Methods 

```
  1 <?php
  2 
  3 abstract class AbstractStringCursor
  4 {
  5 
  6     // ...
  7 
  8     private $advanceCount = null;
  9 
 10     public function advance($count)
 11     {
 12         $this->advanceCount = $count;
 13 
 14         return $this;
 15     }
 16 
 17     public function skip($count)
 18     {
 19         $this->position += $count;
 20         $this->index += $count;
 21 
 22         for ($i = 0; $i < $count; $i++) {
 23             $this->iterator->next();
 24         }
 25 
 26         return $this;
 27     }
 28 
 29     public function traverse()
 30     {
 31         $result = new CursorResult();
 32 
 33         $lastSize = $this->iterator->lastCharSize();
 34         $startPosition = $this->iterator->key();
 35 
 36         $this->shouldReset = false;
 37         $this->advanceCount = null;
 38 
 39         $this->position = $startPosition;
 40 
 41         $result->startPosition = $startPosition;
 42 
 43         $this->initialCharacter = $this->iterator->current();
 44 
 45         for ($this->position = $startPosition;
 46              $this->position < count($this->iterator);
 47              $this->position++) {
 48             $current = $this->iterator[$this->position];
 49             $next = null;
 50             $prev = null;
 51 
 52             if ($this->position > 0) {
 53                 $prev = $this->iterator[$this->position - 1];
 54             }
 55 
 56             if ($this->position + 1 < count($this->iterator)) {
 57                 $next = $this->iterator[$this->position + 1];
 58             }
 59 
 60             $this->buffer .= $current;
 61 
 62             if ($this->accept($current, $prev, $next) === false) {
 63                 if ($this->shouldReset) {
 64                     $this->iterator->setIteratorPosition(
 65                         $startPosition,
 66                         $lastSize
 67                     );
 68                 }
 69 
 70                 $result->endPosition = $this->iterator->key();
 71                 $result->value = $this->buffer;
 72                 $result->length = str($this->buffer)->length();
 73                 $result->content = str($this->buffer)->
 74                 substr(1, -1)->toString();
 75                 break;
 76             }
 77 
 78             if ($this->advanceCount != null) {
 79                 for ($j = 0; $j < $this->advanceCount; $j++) {
 80                     $this->iterator->next();
 81                     $cur = $this->iterator->current();
 82                     $this->buffer .= $cur;
 83                 }
 84 
 85                 $this->position  += $this->advanceCount;
 86                 $this->index += $this->advanceCount;
 87                 $this->advanceCount = null;
 88 
 89                 continue;
 90             }
 91 
 92             $this->iterator->next();
 93 
 94             $this->index += 1;
 95         }
 96 
 97         return $result;
 98     }
 99 
100     // ...
101 }
```

The implementation for skipping characters without appending them to the buffer is the more straightforward of the two. We do this on lines 17-27 and simply advance the iterator by the specified number of characters to skip and return the cursor instance. Advancing is a bit more nuanced since we want this to happen *after* the current iteration is about to complete.

Our `advance` method will set an internal flag indicating the number of characters we should advance over. We check if this flag has been set on line 78; if so, we iterate the specified number of characters and add them to our buffer.

We will take the time to look at the behavior of these two new methods. **Figure 15.65** uses the skip method to skip over the subsequent 3 characters each time it encounters the “r” character:

Figure 15.65 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "threeaab"'
 5 );
 6 
 7 $closeCursor = new ClosureStringCursor($iterator);
 8 
 9 foreach ($iterator as $char) {
10     if ($char == '"') {
11         $result = $closeCursor->traverseUsing(function ($current) {
12             if ($current == '"' && $this->index > 0) { return false; }
13 
14             if ($current == 'r') {
15                 $this->skip(3);
16             }
17 
18             echo "Char: ", $current, " Index: ", $this->index, "\n";
19         });
20     }
21 }
```

Once complete, our `$result` would contain the value `"thrab"`. However, it is more interesting to look at which characters and indexes the cursor encounters once the `skip` method has been called:

Figure 15.66 

```
1 Char: " Index: 0
2 Char: t Index: 1
3 Char: h Index: 2
4 Char: r Index: 6
5 Char: a Index: 7
6 Char: b Index: 8
```

Let us now compare this to **Figure 15.67** which uses the `advance` method instead:

Figure 15.67 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "threeaab"'
 5 );
 6 
 7 $closeCursor = new ClosureStringCursor($iterator);
 8 
 9 foreach ($iterator as $char) {
10     if ($char == '"') {
11         $result = $closeCursor->traverseUsing(function ($current) {
12             if ($current == '"' && $this->index > 0) { return false; }
13 
14             if ($current == 'r') {
15                 $this->skip(3);
16                 $this->advance(3);
17             }
18 
19             echo "Char: ", $current, " Index: ", $this->index, "\n";
20         });
21     }
22 }
```

Our `$result` would now contain the value `"threeaab"` because the advance method will add characters it encounters to the internal buffer. If we compare **Figure 15.68** to **Figure 15.66**, we can see that the behavior of the characters and indexes the cursor encounters is the same:

Figure 15.68 

```
1 Char: " Index: 0
2 Char: t Index: 1
3 Char: h Index: 2
4 Char: r Index: 3
5 Char: a Index: 6
6 Char: b Index: 7
```

We will take a step back and implement some more straightforward utility methods. These helper methods will allow cursor implementations to manipulate the internal string buffer and provide methods that help manage return values more readably.

Figure 15.69 Implementing Additional Utility Methods 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5 
 6     // ...
 7 
 8     public function continue(): bool
 9     {
10         return true;
11     }
12 
13     public function break(): bool
14     {
15         return false;
16     }
17 
18     public function append($content)
19     {
20         $this->buffer .= $content;
21 
22         return $this;
23     }
24 
25     public function popBuffer()
26     {
27         $this->buffer = str($this->buffer)->substr(0, -1);
28 
29         return $this;
30     }
31 
32     public function clearBuffer()
33     {
34         $this->buffer = '';
35 
36         return $this;
37     }
38 
39     public function flushBuffer()
40     {
41         $contents = $this->buffer;
42         $this->buffer = '';
43 
44         return $contents;
45     }
46 
47     /**
48      * Indicates if the cursor completed its traversal.
49      *
50      * @return bool
51      */
52     public function didProcess(): bool
53     {
54         return ! $this->shouldReset;
55     }
56 
57     // ...
58 }
```

Most of our new methods interact with the internal string buffer somehow. For example, the `popBuffer` will remove the last character of the buffer for us. The `flushBuffer` and `clearBuffer` methods are similar, with the difference being the `flushBuffer` method will return the buffer contents while the `clearBuffer` variant will not.

The `continue` and `break` methods are arguably the simplest methods we added but allow us to dramatically improve the readability of cursor implementations. As an example, the following returns `false` when we want to stop processing the input text:

Figure 15.70 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three"'
 5 );
 6 
 7 $closeCursor = new ClosureStringCursor($iterator);
 8 
 9 foreach ($iterator as $char) {
10     if ($char == '"') {
11         $result = $closeCursor->traverseUsing(function ($current) {
12             if ($current == '"' && $this->index > 0) {
13                 return false;
14             }
15         });
16     }
17 }
```

However, if you came across this code and were not entirely familiar with what exactly is going on, this may seem a bit puzzling at first. We can refactor this to use our `break` method, which maps more closely to the iteration that is happening behind the scenes:

Figure 15.71 

```
 1 <?php
 2 
 3 $iterator = new Utf8StringIterator(
 4     'one, two, "three"'
 5 );
 6 
 7 $closeCursor = new ClosureStringCursor($iterator);
 8 
 9 foreach ($iterator as $char) {
10     if ($char == '"') {
11         $result = $closeCursor->traverseUsing(function ($current) {
12             if ($current == '"' && $this->index > 0) {
13                 return false;
14                 return $this->break();
15             }
16         });
17     }
18 }
```

We will now work on our last utility method, which I find the most useful. This utility method will allow us to *inject* the contents of another cursor into the current cursor’s buffer. This is a beneficial behavior; if you recall, each cursor isolates the current iteration from everything else. This behavior allows us to create highly reusable cursor implementations and nest them.

Figure 15.72 Implementing the bufferCursorResult Utility Method 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5 
 6     // ...
 7 
 8     public function bufferCursorResult(
 9         AbstractStringCursor $cursor)
10     {
11         $result = $cursor->traverse();
12         $this->popBuffer();
13         $this->append($result->value);
14 
15         $bufferContents = $this->flushBuffer();
16         $this->position += $result->length - 1;
17 
18         return $bufferContents;
19     }
20 
21     // ...
22 }
```

Our new `bufferCursorResult` method is mainly just a way for us to avoid performing all of the individual actions that would be required to append the contents of another cursor. The first thing we do on 11 is retrieve the results of the cursor we are interested in.

Then, on line 12, we remove the last character of our current buffer using the `popBuffer` method. Remember that cursors will always include the character they started on, which corresponds to the last character the “parent” cursor saw. After this, we append those results to our internal buffer.

A relatively obscure thing we do is clear our current cursor’s buffer and skip over the characters our second cursor processed for us. We do this by manually adjusting the cursor’s position, to avoid accidentally advancing the iterator too much when nesting cursors. This will help us later to combine strings in complicated ways without having to worry about accidentally duplicating them in the final output.

The last thing we will do is ensure that we reset all of our internal state variables. We want to do this in case the same cursor instance is used multiple times on a single input string:

Figure 15.73 Resetting the Cursor State 

```
 1 <?php
 2 
 3 abstract class AbstractStringCursor
 4 {
 5     // ...
 6 
 7     public function traverse(): CursorResult
 8     {
 9         $result = new CursorResult();
10 
11         $lastSize = $this->iterator->lastCharSize();
12         $startPosition = $this->iterator->key();
13 
14         $this->shouldReset = false;
15         $this->advanceCount = null;
16         $this->buffer = '';
17         $this->index = 0;
18 
19         // ...
20 
21         return $result;
22     }
23 }
```

If we did not reset our state to initial conditions every time we traverse our string, we might accidentally have an index value or buffer contents from a previous traversal.

### 15.7 Implementing the StringsCursor

We have discussed at length how to use our string cursor concept and implement the underlying features, but we have not yet looked at how to actually implement a cursor. If we think back to our initial string splitting implementation in **Figure 15.51**, most of our complexity surrounding parsing strings from our input text was related to keeping track of state and not applying certain logic when we were inside of a string.

Because our cursor system isolates character iteration within each cursor and hides it away from our main loop, we can leverage all of the features that our `AbstractStringCursor` provides and rewrite our string detection logic in a much simpler way:

Figure 15.74 StringsCursor Implementation 

```
 1 <?php
 2 
 3 class StringsCursor extends AbstractStringCursor
 4 {
 5     public function accept($current, $prev = null, $next = null)
 6     {
 7         if ($this->index > 0 &&
 8             $current == $this->initialCharacter && $prev != '\\') {
 9             return $this->break();
10         }
11     }
12 }
```

Remember that our `accept` method is only concerned with whether or not the cursor should continue processing the input text, so our implementation only needs to implement the logic to detect *leaving* our strings.

Our cursors will always begin processing at the character they were created, so we need to check if the current index is greater than 0 on line 7. If it is, we can check if the current character matches the quote style that was present when the cursor was created and ensure it is not preceded by the backslash character.

### 15.8 Implementing the ClosureStringCursor

In addition to the `StringsCursor`, we have also seen the `ClosureStringCursor` several times throughout the preceding sections. Our implementation for this will be straightforward, as we only need to store a user-provided callback and invoke it from our `accept` method:

Figure 15.75 ClosureStringCursor Implementation 

```
 1 <?php
 2 
 3 class ClosureStringCursor extends AbstractStringCursor
 4 {
 5     protected $callback;
 6 
 7     public function traverseUsing(Closure $callback)
 8     {
 9         $this->callback = $callback;
10 
11         return $this->traverse();
12     }
13 
14     public function accept($current, $prev = null, $next = null)
15     {
16         if ($this->callback == null) {
17             return $this->break();
18         }
19 
20         return $this->callback->call($this, $current, $prev, $next);
21     }
22 }
```

### 15.9 A Simple PHP Tokenizer

Let us consider the example code in **Figure 15.76**. Our example uses PHP’s `token_get_all` function to return the results of PHP’s tokenizer on the input string. We then use Laravel’s collection features to provide a friendlier name for each of the returned tokens:

Figure 15.76 Tokenizing PHP Code 

```
 1 <?php
 2 
 3 $code = <<<'PHP'
 4 <?php
 5 $value = 5 + (532_323) - $total;
 6 PHP;
 7 
 8 
 9 collect(token_get_all($code))->map(function ($token) {
10     if (!is_string($token) && count($token) > 1) {
11         $token['name'] = token_name($token[0]);
12     }
13 
14     return $token;
15 })->all();
```

Our example would produce the following output:

Figure 15.77 PHP Lexer Example Output 

```
 1 [
 2   [
 3     0 => 394,
 4     1 => "<?php\n",
 5     2 => 1,
 6     "name" => "T_OPEN_TAG",
 7   ],
 8   [
 9     0 => 317,
10     1 => "$value",
11     2 => 2,
12     "name" => "T_VARIABLE",
13   ],
14   [
15     0 => 397,
16     1 => " ",
17     2 => 2,
18     "name" => "T_WHITESPACE",
19   ],
20   "=",
21   [
22     0 => 397,
23     1 => " ",
24     2 => 2,
25     "name" => "T_WHITESPACE",
26   ],
27   [
28     0 => 311,
29     1 => "5",
30     2 => 2,
31     "name" => "T_LNUMBER",
32   ],
33   [
34     0 => 397,
35     1 => " ",
36     2 => 2,
37     "name" => "T_WHITESPACE",
38   ],
39   "+",
40   [
41     0 => 397,
42     1 => " ",
43     2 => 2,
44     "name" => "T_WHITESPACE",
45   ],
46   "(",
47   [
48     0 => 311,
49     1 => "532_323",
50     2 => 2,
51     "name" => "T_LNUMBER",
52   ],
53   ")",
54   [
55     0 => 397,
56     1 => " ",
57     2 => 2,
58     "name" => "T_WHITESPACE",
59   ],
60   "-",
61   [
62     0 => 397,
63     1 => " ",
64     2 => 2,
65     "name" => "T_WHITESPACE",
66   ],
67   [
68     0 => 317,
69     1 => "$total",
70     2 => 2,
71     "name" => "T_VARIABLE",
72   ],
73   ";",
74 ]
```

Each element in our resulting array corresponds to some of our input text. For instance, the second element corresponds to the `$value` variable on line 2. The first value in all of our nested arrays contains the token identifier, the second value holds the contents of the match, and the third value includes the line number the token is located on. We can also see that values such as the “+” and “=” are simply added to our output array without additional information.

We will work on implementing something that would return the same array using our cursor concept. It is important to note that we will not be working on writing a complete PHP lexer and will only be implementing enough to match the output in **Figure 15.77**. The first cursor implementation we will undertake is the `VariableCursor`, which we will use to iterate over PHP variables:

Figure 15.78 VariableCursor Implementation 

```
 1 <?php
 2 
 3 class VariableCursor extends AbstractStringCursor
 4 {
 5 
 6     protected function isValidChar($char)
 7     {
 8         return ctype_alnum($char) || $char == '_';
 9     }
10 
11     public function accept($current, $prev = null, $next = null)
12     {
13         if (! $this->isValidChar($next)) {
14             return $this->break();
15         }
16 
17         return $this->continue();
18     }
19 }
```

Because our cursors will always *start* on a valid character, we can easily detect the end of a PHP variable by checking if the *next* character available to our cursor is valid. Our implementation allows alphanumeric characters, as well as the underscore character.

Our next cursor will be the `NumberCursor`, which will traverse PHP numeric values:

Figure 15.79 NumberCursor Implementation 

```
 1 <?php
 2 
 3 class NumberCursor extends  AbstractStringCursor
 4 {
 5     protected function isValidChar($char)
 6     {
 7         if ($char == '.' || $char == '_') {
 8             return true;
 9         }
10         if (! ctype_digit($char) || ctype_punct($char)) {
11             return false;
12         }
13 
14         return true;
15     }
16 
17     public function accept($current, $prev = null, $next = null)
18     {
19         return $this->isValidChar($next);
20     }
21 }
```

The last cursor we will implement before moving on to iterating our input text will be the `OpenTagCursor`:

Figure 15.80 OpenTagCursor Implementation 

```
 1 <?php
 2 
 3 class OpenTagCursor extends AbstractStringCursor
 4 {
 5     public function accept($current, $prev = null, $next = null)
 6     {
 7         if (str($this->buffer)->startsWith('<?php')) {
 8             if (! ctype_space($next)) {
 9                 return $this->break();
10             }
11         }
12 
13         return $this->continue();
14     }
15 }
```

If we take a moment to look at **Figure 15.80**, we have some exciting things going on. On line 7, we check if our current buffer starts with the text “<?php.” Because each cursor has its internal buffer, we can check against it to see if we’ve moved over the opening PHP tag. If we have moved over the opening tag, and the next character is not whitespace, we return false on line 9. We do this to get the same output as PHP’s `token_get_all` function for the opening tag.

Using these simple cursor implementations, we can relatively painlessly write a loop that will produce the same output as **Figure 15.77**:

Figure 15.81 Simple PHP Lexer 

```
 1 <?php
 2 
 3 $code = <<<'PHP'
 4 <?php
 5 $value = 5 + (532_323) - $total;
 6 PHP;
 7 
 8 $string         = new Utf8StringIterator($code);
 9 $locator        = new CharacterPositionLocator($code);
10 $variableCursor = new VariableCursor($string);
11 $numberCursor   = new NumberCursor($string);
12 
13 $tokens = [];
14 $symbols = ['=', '+', '-', '(', ')', ';'];
15 
16 function makeTokenArray($locator, $result, $tokenType) {
17     return [
18         $tokenType,
19         $result->value,
20         $locator->getLineNumber($result->startPosition),
21         token_name($tokenType)
22     ];
23 }
24 
25 foreach ($string as $char) {
26     if ($char == '<' && str($string)->substr($string->key(), 5)) {
27         $result = (new OpenTagCursor($string))->traverse();
28 
29         $tokens[] = makeTokenArray(
30             $locator,
31             $result,
32             T_OPEN_TAG
33         );
34         continue;
35     }
36 
37     if (in_array($char, $symbols)) {
38         $tokens[] = $char;
39         continue;
40     }
41 
42     if (ctype_space($char)) {
43         $tokens[] = [
44             T_WHITESPACE,
45             $char,
46             $locator->getLineNumber($string->key()),
47             token_name(T_WHITESPACE)
48         ];
49 
50         continue;
51     }
52 
53     if (ctype_digit($char)) {
54         $result = $numberCursor->traverse();
55 
56         $tokens[] = makeTokenArray(
57             $locator,
58             $result,
59             T_LNUMBER
60         );
61 
62         continue;
63     }
64 
65     if ($char == '$') {
66         $result = $variableCursor->traverse();
67 
68         $tokens[] = makeTokenArray(
69             $locator,
70             $result,
71             T_VARIABLE
72         );
73         continue;
74     }
75 }
```

Most of our implementation should feel familiar, as we are using the same pattern of checking if our current character looks like something we would be interested in. If so, we call the appropriate cursor and add its results to our `$tokens` array.

Our `makeTokenArray` helper function exists so that we can more easily create arrays that match our output in **Figure 15.77**, but it is not strictly necessary for our implementation.

**Figure 15.81** new technique is what is happening on line 26. When the current character is “<,” we retrieve a substring from our input at the iterator’s current location. Our substring contains five characters, which would cover the entire PHP opening tag if it exists. This is how our implementation can tell the difference between a “<” being part of the opening tag instead of the less-than operator. There are other ways to accomplish this, but this approach is suitable for our simple implementation.

If we were to run our code and compare the results of our simple lexer implementation, we would find that it does indeed match the results in **Figure 15.77**. Given enough time and patience, we could continue with this approach to eventually write an entire PHP lexer.

### 15.10 Working with SQL-Style Strings

Consider the sample SQL query in **Figure 15.82**. Suppose we want to extract all of the strings inside it. These values can be a bit trickier to retrieve from a piece of text, mainly because they use two occurrences of the string delimiter character as the escape sequence.

Figure 15.82 Example SQL Query 

```
1 SELECT * FROM companies WHERE name = 'Jim''s Tackle Shop'
2 OR name = 'Bob''s Burger'
```

We can also solve this problem using our cursor concept and will involve using some of our utility methods. The basic process will be similar to handling PHP-style double or single quote strings, except that we need to check if the *next* character is a single quote instead of the previous character. This implementation can be found in **Figure 15.83**:

Figure 15.83 SqlStringsCursor Implementation 

```
 1 <?php
 2 
 3 class SqlStringsCursor extends AbstractStringCursor
 4 {
 5     public function accept($current, $prev = null, $next = null)
 6     {
 7         if ($this->index > 0 && $current == "'") {
 8             if ($next == "'") {
 9                 return $this->advance(1)->continue();
10             }
11 
12             return $this->skip(1)->break();
13         }
14 
15         return $this->continue();
16     }
17 }
```

Between lines 8 and 10, we check if the next character in the input text is the single quote string, which indicates that we are starting an SQL-style string escape sequence. We then call our `advance` method and continue processing the input text. Remember that the `advance` method will move the desired number of characters and add the character to the cursor’s internal buffer.

When we leave the cursor on line 12, we skip the current character, so it does not get duplicated and exit the cursor.

We can use our new cursor like so:

Figure 15.84 

```
 1 <?php
 2 
 3 $sql = <<<'SQL'
 4 SELECT * FROM companies WHERE name = 'Jim''s Tackle Shop'
 5 OR name = 'Bob''s Burger'a
 6 SQL;
 7 
 8 $string = new Utf8StringIterator($sql);
 9 $sqlStringCursor = new SqlStringsCursor($string);
10 
11 $strings = [];
12 
13 foreach ($string as $char) {
14     if ($char == "'") {
15         $result = $sqlStringCursor->traverse();
16 
17         $strings[] = $result->value;
18         continue;
19     }
20 }
```

After **Figure 15.84** has been executed, our `$strings` array would contain the following values:

Figure 15.85 

```
1 array:2 [
2   0 => "'Jim''s Tackle Shop'"
3   1 => "'Bob''s Burger'"
4 ]
```

While our results are already fairly impressive, we can take this a step further to explore some additional use cases. So far, we have always extracted the cursor results or collected them in a list to inspect further. However, we can also use cursors to effectively replace values in our input text and simply ignore their results:

Figure 15.86 

```
 1 <?php
 2 
 3 $sql = <<<'SQL'
 4 SELECT * FROM companies WHERE name = 'Jim''s Tackle Shop'
 5 OR name = 'Bob''s Burger'
 6 SQL;
 7 
 8 $string = new Utf8StringIterator($sql);
 9 $sqlStringCursor = new SqlStringsCursor($string);
10 
11 
12 $newString = '';
13 
14 foreach ($string as $char) {
15     if ($char == "'") {
16         $result = $sqlStringCursor->traverse();
17     
18         $newString .= '?';
19         continue;
20     }
21 
22     $newString .= $char;
23 }
```

Our results would now be, with all the SQL strings replaced by the “?” character:

Figure 15.87 

```
1 SELECT * FROM companies WHERE name = ?
2 OR name = ?
```

### 15.11 Splitting Strings Containing Paired Brackets

Suppose we have the input text provided in **Figure 15.88**:

Figure 15.88 

```
1 ($one, $two, ($string .")" )), $three, hello,
2 "(this", "that )", $end($one, ($two))
```

And would like to split it into the array of strings in **Figure 15.89**:

Figure 15.89 

```
 1 array:6 [
 2   0 => "($one, $two, ($string .")" ))"
 3   1 => " $three"
 4   2 => " hello"
 5   3 => """
 6     
 7     "(this"
 8     """
 9   4 => " "that )""
10   5 => " $end($one, ($two))"
11 ]
```

However, if the entire input text is surrounded in parenthesis like in **Figure 15.90**:

Figure 15.90 

```
1 (($one, $two, ($string .")" )), $three, hello,
2 "(this", "that )", $end($one, ($two)))
```

We want to produce an array containing only a single value, which would be the input string:

Figure 15.91 

```
1 array:1 [
2   0 => """
3     (($one, $two, ($string .")" )), $three, hello,
4     "(this", "that )", $end($one, ($two)))
5     """
6 ]
```

At first, this may seem like an incredibly complex problem to solve. However, if we analyze our expected output carefully, we can see that we are *not* splitting a substring if it is contained within a balanced set of parentheses. Additionally, we ignore any parenthesis that appears within a single or double-quoted string. Instead of trying to engineer an overly-complicated pattern-matching solution, we can reduce our problem to a simple counting problem.

Suppose we were to keep a running count that increments every time we see opening parentheses and decrement it when we encounter a valid closing parenthesis. In that case, we can use that more straightforward counter to complete our task because the counter will equal zero when we have assembled a valid parentheses pair, regardless of how many nested pairs appear.

Let us take a look at how we could implement this using our cursor concept in **Figure 15.92**:

Figure 15.92 Implementing the PairedBracketCursor 

```
 1 <?php
 2 
 3 class PairedBracketCursor extends AbstractStringCursor
 4 {
 5     private $closingBracket = '';
 6     private $openingBracket = '';
 7     private $pairCount = 0;
 8 
 9     public function __construct(
10         $iterator,
11         $openingBracket,
12         $closingBracket
13     )
14     {
15         parent::__construct($iterator);
16         $this->openingBracket = $openingBracket;
17         $this->closingBracket = $closingBracket;
18     }
19 
20     public function accept($current, $prev = null, $next = null)
21     {
22         if ($current == '"' || $current == "'") {
23             $this->buffer = $this->bufferCursorResult(
24                 new StringsCursor($this->iterator)
25             );
26 
27             return $this->continue();
28         }
29 
30         if ($this->index == 0 || $current == $this->openingBracket) {
31             $this->pairCount += 1;
32 
33             return $this->continue();
34         }
35 
36         if ($current == $this->closingBracket) {
37             $this->pairCount -= 1;
38 
39             if ($this->pairCount == 0) {
40                 return $this->break();
41             }
42         }
43 
44         return $this->continue();
45     }
46 }
```

We have modified our cursor’s constructor to accept the opening and closing bracket characters. We do this to know what to compare against when updating our counter later in the implementation. On lines 22-28, we see our existing `StringsCursor` being used to advance over any problematic strings. This helps to keep any parenthesis that appears within these substrings from contributing to our counter’s value.

Between lines 30 and 34, we have our logic that will increment our counter. Because our cursor always starts on the iterator’s current character, we need to check if the current index is zero and if the current character matches our opening bracket.

Between lines 26 and 42, we decrement the value of our counter. If the `$pairCount` value has reached zero, we know we have reached the end of a balanced pair.

To help get a sense of how this new cursor works, we can take a look at **Figure 15.93**, which uses it to extract the outermost pairs of parenthesis:

Figure 15.93 

```
 1 <?php
 2 
 3 $input = <<<'INPUT'
 4 ($one, $two, ($string . ")" )), "(this)", (that)
 5 INPUT;
 6 
 7 $string = new Utf8StringIterator($input);
 8 $cursor = new ClosureStringCursor($string);
 9 
10 $pairs = [];
11 
12 $cursor->traverseUsing(function ($cur, $prev, $next) use (&$pairs) {
13     if ($cur == '(') {
14         $this->flushBuffer();
15         $result = $this->bufferCursorResult(
16             new PairedBracketCursor(
17                 $this->iterator(), '(', ')'
18             )
19         );
20 
21         $pairs[] = $result;
22     }
23 });
```

Our example produces the following output:

Figure 15.94 

```
1 array:3 [
2   0 => "($one, $two, ($string . ")" ))"
3   1 => "(this)"
4   2 => "(that)"
5 ]
```

The one thing to note, which we can see on line 17 of **Figure 15.93**, is that we need to supply the opening and closing bracket styles when we create our cursor. This allows us to re-use our new cursor for angle brackets, square brackets, or any other combination of characters (as long as they are not the same character).

So far in this chapter, we have worked with our cursors inline and have not created anything more substantial with them. To implement our string splitter that is aware of paired brackets, in addition to substrings, we will encapsulate this logic into its own class, which will make it easier to work with in the future:

Figure 15.95 CommaStringSplitter Implementation 

```
 1 <?php
 2 
 3 class CommaStringSplitter extends AbstractStringCursor
 4 {
 5     protected $current = '';
 6     protected $prev = null;
 7     protected $next = null;
 8     protected $strings = [];
 9 
10     protected function nextIsNull()
11     {
12         return $this->next == null ||
13             $this->iterator->key() == $this->iterator->count() - 1;
14     }
15 
16     public function continue()
17     {
18         if ($this->nextIsNull()) {
19             $this->strings[] = $this->flushBuffer();
20             return false;
21         }
22 
23         return true;
24     }
25 
26     public function accept($current, $prev = null, $next = null)
27     {
28         $this->current = $current;
29         $this->prev = $prev;
30         $this->next = $next;
31 
32         if ($current == '(') {
33             return $this->append($this->bufferCursorResult(
34                 new PairedBracketCursor(
35                     $this->iterator, '(', ')'
36                 )
37             ))->continue();
38         }
39 
40         if ($current == '"' || $current == "'") {
41             return $this->append($this->bufferCursorResult(
42                 new StringsCursor($this->iterator)
43             ))->continue();
44         }
45 
46         if ($current == ',') {
47             $this->strings[] = $this->popBuffer()->flushBuffer();
48         }
49 
50         return $this->continue();
51     }
52 
53     public function getStrings()
54     {
55         return $this->strings;
56     }
57 }
```

Our implementation in **Figure 15.95** is similar to what we have seen before, but a few notable and exciting things are happening. The first thing we have done differently in this example is overriding the continue method on lines 16-24.

Overriding the `continue` method allows us to move our logic that decides whether or not to split the string into a central location. This prevents us from including it at the end of each nested cursor, quickly becoming difficult to reason with. We also see a call to a new `nextIsNull` method within this method.

Because our nested cursors advance the main `Utf8StringIterator`, we may be at the end of the string after a nested cursor has finished traversing the string. We can account for this situation by checking if the iterator’s current key is one less than the length of the input string, which we do on line 13.

We can now use our new `CommaStringSplitter` implementation like so:

Figure 15.96 

```
 1 <?php
 2 
 3 $input = <<<'INPUT'
 4 ($one, $two, ($string .")" )), $three, $four,
 5 "(five", "six )", seven($one, ($two)), eight,
 6 nine($ten, $eleven)
 7 INPUT;
 8 
 9 $string = new Utf8StringIterator($input);
10 $stringSplitter = new CommaStringSplitter($string);
11 
12 $stringSplitter->traverse();
13 
14 $strings = $stringSplitter->getStrings();
```

To produce the following output:

Figure 15.97 

```
 1 array:8 [
 2   0 => "($one, $two, ($string .")" ))"
 3   1 => " $three"
 4   2 => " $four"
 5   3 => """
 6     \r\n
 7     "(five"
 8     """
 9   4 => " "six )""
10   5 => " seven($one, ($two))"
11   6 => " eight"
12   7 => """
13     \r\n
14     nine($ten, $eleven)
15     """
16 ]
```

## 16\. Applied Techniques: A Blade Directive Validator

Throughout this chapter, we will apply many of the concepts and techniques we have discussed so far in this book to develop a Laravel Blade validation system. Our validator will only be concerned with directives and their parameters, and these limitations will allow us to take a few shortcuts and dramatically simplify our validator implementation. Instead of diving head first into our validator, let us take some time to explore some of the situations we are going to want to detect with our validator.

The main set of issues we will be detecting are related to directive arguments. The first will be directives missing required argument groups and argument groups being present on those that should not have argument groups. An example of this is in **Figure 16.1**, where the `@foreach` directive is missing all of its argument group, and the `@endforeach` directive has one where it is not necessary:

Figure 16.1 

```
1 @foreach
2 
3 @endforeach ($users as $user)
```

The next type of issue we will detect is when an argument group starts on the line following the directive name, which will cause invalid PHP code when the template is compiled:

Figure 16.2 

```
1 @if
2     (5 > 3)
3 
4 
5 @endif
```

Thirdly, we will also provide ways to enforce the casing of directive names, as well as the spacing between a directive’s name and its argument group:

Figure 16.3 

```
1 @FOREACH     ($users as $user)
2 
3 
4 @ENDFOREACH
```

Admittedly, the last group of items to validate does not necessarily produce compiler errors, but it will provide us an opportunity to have some fun with our validator.

We now need to start thinking about what we will parse. While our end goal is to validate Blade directives, there are several potential issues that we need to think through before we start writing our parser. For example, **Figure 16.4** provides an example Blade template that contains raw PHP blocks, Blade comments, some verbatim blocks, as well as some PHP code all mixed together:

Figure 16.4 Example of Blade Complexity 

```
 1 @foreach
 2 
 3 @endforeach
 4 
 5     {{-- @foreach --}}
 6 
 7 <?php echo 'some php @code'; ?>
 8 
 9 @php
10 $total = $quantity * $unitCost;
11 @endphp
12 
13 @verbatim
14 
15     @foreach
16 
17     @endforeach
18 
19     {{-- @foreach --}}
20 
21     <?php echo 'some php @code'; ?>
22 
23 @endverbatim
24 
25 @CAN
26 
27 @endCan
```

These structures will add tremendous complexity to any Blade parser that wants to parse Blade templates and understand how each structure relates to every other one. If we were to write a Blade code formatter, we would need to manage these complexities. Luckily, we have decided to only parse and validate directives, so we can simply remove Blade comments, verbatim, and raw PHP blocks.

If we look through the Blade compiler’s source code, we will find that it internally processes verbatim blocks, PHP blocks, and comments in that order. For verbatim and PHP blocks, it will replace them with an internal identifier, and comments are simply replaced with an empty string. We can experiment to see what it would take to remove all of these structures from our template.

Figure 16.5 Removing Blade Structures from Input Text 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 
 5 @foreach
 6 
 7 @endforeach
 8 
 9     {{-- @foreach --}}
10 
11 <?php echo 'some php @code'; ?>
12 
13 @php
14 $total = $quantity * $unitCost;
15 @endphp
16 
17 @verbatim
18 
19     @foreach
20 
21     @endforeach
22 
23     {{-- @foreach --}}
24 
25     <?php echo 'some php @code'; ?>
26 
27 @endverbatim
28 
29 @CAN
30 
31 @endCan
32 BLADE;
33 
34 // Remove the contents of any Verbatim blocks.
35 $blade = preg_replace_callback(
36     '/(?<!@)@verbatim(.*?)@endverbatim/s',
37     function ($matches) {
38         return '';
39     }, $blade
40 );
41 
42 // Remove the contents of any PHP blocks.
43 $blade = preg_replace_callback(
44     '/(?<!@)@php(.*?)@endphp/s',
45     function ($matches) {
46         return '';
47     }, $blade
48 );
49 
50 // Remove the contents of any Blade comments.
51 $blade = preg_replace_callback(
52     '/{{--(.*?)--}}/s',
53     function ($matches) {
54         return '';
55     }, $blade
56 );
```

In **Figure 16.5**, we can see three regular expressions being used to replace our problematic regions. On lines 35-40, we remove the verbatim blocks, the PHP blocks on lines 43-48, and finally, on lines 51-56, we remove the Blade comments. Once all of these replacements have been made, we will be left with the following Blade template:

Figure 16.6 

```
 1 @foreach
 2 
 3 @endforeach
 4 
 5     
 6 
 7 <?php echo 'some php @code'; ?>
 8 
 9 @CAN
10 
11 @endCan
```

While this has simplified our template considerably, we have introduced a new problem. If we compare the template in **Figure 16.6** to that in **Figure 16.4**, we can see that we have moved the `@CAN` directive from line 26 to line 9 within the Blade template. Later, when we want to alert the user of potential issues, the relative line numbers will no longer be correct. A relatively simple solution to our new problem would be to not replace our problematic Blade regions with an empty string but rather with a string of the same length that contains only spaces and newlines. We can see an example of this in **Figure 16.7**:

Figure 16.7 

```
 1 <?php
 2 
 3 // ...
 4 
 5 function fillSpaces($value)
 6 {
 7     $string = new Utf8StringIterator($value);
 8     $newString = '';
 9 
10     foreach ($string as $char) {
11         if ($char == "\n") {
12             $newString .= $char;
13             continue;
14         }
15 
16         $newString .= ' ';
17     }
18 
19     return $newString;
20 }
21 
22 // Remove the contents of any Verbatim blocks.
23 $blade = preg_replace_callback(
24     '/(?<!@)@verbatim(.*?)@endverbatim/s',
25     function ($matches) {
26         return fillSpaces($matches[0]);
27     }, $blade
28 );
29 
30 // Remove the contents of any PHP blocks.
31 $blade = preg_replace_callback(
32     '/(?<!@)@php(.*?)@endphp/s',
33     function ($matches) {
34         return fillSpaces($matches[0]);
35     }, $blade
36 );
37 
38 // Remove the contents of any Blade comments.
39 $blade = preg_replace_callback(
40     '/{{--(.*?)--}}/s',
41     function ($matches) {
42         return fillSpaces($matches[0]);
43     }, $blade
44 );
```

Between lines 5 and 20 of **Figure 16.7**, we see a new function `fillSpaces`. This function uses the `Utf8StringIterator` we developed in Chapter 1 to iterate each of the characters of the input value. If the current character is a newline character, we add it to our output string; if it is not, we add a space instead. Our `preg_replace_callback` function calls have also been updated to use this new function instead of returning an empty string when performing the replacements. With our refactored code, our final Blade template would now be:

Figure 16.8 

```
 1 @foreach
 2 
 3 @endforeach
 4 
 5                       
 6 
 7 <?php echo 'some php @code'; ?>
 8 
 9      
10                                 
11        
12 
13           
14  
15              
16  
17                 
18  
19                        
20  
21                                     
22  
23             
24 
25 @CAN
26 
27 @endCan
```

Our template in **Figure 16.8** is much easier to work with and preserves the offsets and line numbers from the original template. We now have enough experimentation done to begin our validator implementation.

### 16.1 Scaffolding our Parser Implementation

We will begin our Blade validator by scaffolding our parser. To start, we will define our Blade data models and recreate our technique to replace complicated structures with spaces and newlines.

Figure 16.9 Beginning the Blade Parser Implementation 

```
  1 <?php
  2 
  3 use Illuminate\Support\Str;
  4 
  5 abstract class BladeStructure
  6 {
  7     public $startPosition = 0;
  8     public $endPosition = 0;
  9     public $length = 0;
 10 
 11     public $line = 0;
 12     public $column = 0;
 13 
 14     public function getEndOffset()
 15     {
 16         return $this->endPosition;
 17     }
 18 }
 19 
 20 class ParsedDirective extends BladeStructure
 21 {
 22     public $args = null;
 23     public $directiveName = '';
 24 
 25     public function getEndOffset()
 26     {
 27         if ($this->args != null && $this->args->endPosition > 0) {
 28             return $this->args->endPosition;
 29         }
 30 
 31         return $this->endPosition;
 32     }
 33 }
 34 
 35 class ParsedArguments extends BladeStructure
 36 {
 37     public $value = '';
 38     public $content = '';
 39 }
 40 
 41 class BladeDirectiveValidator
 42 {
 43     protected $structures = [];
 44 
 45     protected function fillSpaces($value)
 46     {
 47         $string = new Utf8StringIterator($value);
 48         $newString = '';
 49 
 50         foreach ($string as $char) {
 51             if ($char == "\n") {
 52                 $newString .= $char;
 53                 continue;
 54             }
 55 
 56             $newString .= ' ';
 57         }
 58 
 59         return $newString;
 60     }
 61 
 62     protected function prepareInput($value)
 63     {
 64         $value = Str::normalizeEol($value, "\n");
 65 
 66         // Remove the contents of any verbatim blocks.
 67         $value = preg_replace_callback(
 68             '/(?<!@)@verbatim(.*?)@endverbatim/s',
 69             function ($matches) {
 70                 return $this->fillSpaces($matches[0]);
 71             }, $value
 72         );
 73 
 74         // Remove the contents of any PHP blocks.
 75         $value = preg_replace_callback(
 76             '/(?<!@)@php(.*?)@endphp/s',
 77             function ($matches) {
 78                 return $this->fillSpaces($matches[0]);
 79             }, $value
 80         );
 81 
 82         // Remove the contents of any Blade comments.
 83         return preg_replace_callback(
 84             '/{{--(.*?)--}}/s',
 85             function ($matches) {
 86                 return $this->fillSpaces($matches[0]);
 87             }, $value
 88         );
 89     }
 90 
 91     /**
 92      * Parses the provided Blade template.
 93      *
 94      * @param $value
 95      * @return array
 96      */
 97     public function parse($value)
 98     {
 99         $value = $this->prepareInput($value);
100 
101         return $this->structures;
102     }
103 }
```

Between lines 5 and 39, we define our classes that will represent the directives and argument groups we parse from the input text. Both the directive and arguments extend an abstract `BladeStructure` class, which contains information such as the start and end position and the line number. We will not be working with column numbers for reasons we will get to later in this chapter. We have also moved our `fillSpaces` function to a class method on lines 45-60, which we are now using within the `prepareInput` method.

The `prepareInput` method will accept an input template string and ensure all newline characters are consistent, as well as remove the Blade features we are not interested in working with. This method is eventually called by the `parse` method, which is currently mostly empty.

Our next challenge to work through before really getting into our validator’s parser is how to work with PHP embedded within our template. If we look at **Figure 16.10**, we can see an HTML paragraph tag that has PHP embedded within its contents:

Figure 16.10 

```
1 <p>
2     Hello,
3     <?php ?>
4     there!
5 </p>
```

Our goal is to remove that `<?php ?>` that appears in the middle of our paragraph. We could do this manually, but getting it right every time is not trivial.

In the previous chapter, we experimented briefly with PHP’s `token_get_all` function, which will return the results of PHP’s lexer on the input string. Let us take a moment to invoke this function on our sample input in **Figure 16.11**:

Figure 16.11 

```
1 <?php
2 
3 $value = <<<'VALUE'
4 <p>
5     Hello,
6     <?php ?>
7     there!
8 </p>
9 VALUE;
```

And review its output in **Figure 16.12**:

Figure 16.12 

```
 1 array:4 [
 2   0 => array:3 [
 3     0 => 318
 4     1 => """
 5       <p>\n
 6           Hello,\n
 7           
 8       """
 9     2 => 1
10   ]
11   1 => array:3 [
12     0 => 394
13     1 => "<?php "
14     2 => 3
15   ]
16   2 => array:3 [
17     0 => 396
18     1 => "?>\n"
19     2 => 3
20   ]
21   3 => array:3 [
22     0 => 318
23     1 => """
24           there!\n
25       </p>
26       """
27     2 => 4
28   ]
29 ]
```

Looking at **Figure 16.12**, we can see the `token_get_all` function returned four elements for our input text. The second and third correspond to the opening and closing PHP tags, but the first and last elements correspond to our non-PHP code.

Recalling from the previous chapter, we know that for each array element returned by PHP’s lexer, the first element identifies the *type* of item detected by the lexer, and the third element tells us the line number on which it appeared. In our instance, we are interested in all elements with a token type of 318, which corresponds to the `T_INLINE_HTML` token type. By using the results of the `token_get_all` function, we can filter out the inline HTML tokens and effectively skip over all of the embedded PHP code, which could get complicated to work with. However, this presents a small problem we need to be aware of.

Looking at our inline HTML tokens from **Figure 16.12**, we can see that each element contains the content we want to parse for directives. Still, each element’s content alone only provides a partial overview of the document. Because of this, we now have the same problem as before: our line numbers would be wrong. We could attempt to combine all of the inline HTML elements and fill in the gaps, similar to what we did before. However, we can take a different approach this time.

Because PHP’s lexer provides an accurate line number for each element it returns, we can use that value to offset any line numbers we retrieve later. For example, if we are on line 1 of the third element, we can take that token’s line number, subtract one, and add back our relative line number to get the final result of 4, which is the correct line number from the original document. You may notice that the lexer’s results do not include column numbers.

We could traverse the content’s of all token types returned and calculate the column position for each token if we wanted to. However, since most Blade directives will appear on their own line, using only line numbers is acceptable for our use case.

### 16.2 Parsing Blade Directives

Our next task will be to set things up to extract information about any Blade directives that appear within our input text. In the previous chapter, we explored the idea of using a regular expression to help us build an index of where we should start looking for parseable items within a document. We will do the same for the Blade directives, as this will help us to avoid escaped Blade directives, as well as things that *look* like directives that should be ignored, such as CSS media queries.

To do this, we will need a list of the core directive names and a way to provide a list of custom directives, which can be populated at runtime by retrieving them from the Blade compiler within the context of a running application. Once we have those items, we can construct a dynamic regular expression that is similar to the one in **Figure 16.13**:

Figure 16.13 

```
1 /(?<!@)@(?!@)(can|cannot|canany)/i
```

The regular expression in **Figure 16.13** begins with an obscure-looking pattern. Still, it matches the “@” character, as long it is not followed by *or* preceded by another instance of the “@” character. We must account for both cases to avoid accidentally matching the first “@” in an escaped Blade directive.

Figure 16.14 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7 
 8     protected $structures = [];
 9 
10     // ...
11 
12     protected $coreDirectives = [
13         'can', 'cannot', 'canany', 'elsecan', 'elsecannot',
14         'elsecanany', 'endcan', 'endcannot', 'endcanany',
15         'class', 'component', 'endComponent', 'slot', 'endSlot',
16         'props', 'endComponentClass', 'componentClass',
17         'componentFirst', 'endComponentFirst', 'push', 'endPush',
18         'aware', 'auth', 'elseAuth', 'endAuth', 'env', 'endEnv',
19         'production', 'endProduction', 'guest', 'elseGuest',
20         'endGuest', 'hasSection', 'if', 'unless', 'elseIf',
21         'else', 'endIf', 'endUnless', 'isset', 'endIsset',
22         'switch', 'case', 'default', 'endSwitch', 'once',
23         'endOnce', 'selected', 'checked', 'disabled', 'required',
24         'readonly', 'pushIf', 'endPushIf', 'error', 'enderror',
25         'csrf', 'dd', 'dump', 'method', 'vite', 'viteReactRefresh',
26         'each', 'include', 'includeIf', 'includeWhen',
27         'includeUnless', 'includeFirst', 'inject', 'js', 'json',
28         'extends', 'extendsFirst', 'section', 'parent', 'yield',
29         'show', 'append', 'overwrite', 'stop', 'endsection',
30         'foreelse', 'empty', 'endforelse', 'endempty', 'for',
31         'foreach', 'break', 'continue', 'endfor', 'endforeach',
32         'while', 'endwhile', 'php', 'unset', 'stack', 'push',
33         'pushOnce', 'endpush', 'endpushonce', 'prepend',
34         'prependOnce', 'endprepend', 'endprependOnce', 'lang',
35         'endlang', 'choice'
36     ];
37 
38     protected $customDirectives = [];
39 
40     public function setCustomDirectives(array $directives)
41     {
42         $this->customDirectives = $directives;
43     }
44 
45     public function getDirectiveNames()
46     {
47         return array_merge(
48             $this->coreDirectives,
49             $this->customDirectives
50         );
51     }
52 
53     public function parse($value)
54     {
55         $value = $this->prepareInput($value);
56 
57         $htmlRegions = collect(token_get_all($value))
58             ->filter(function ($token) {
59                 return is_array($token) && $token[0] == T_INLINE_HTML;
60             })->all();
61 
62         $pattern = collect($this->getDirectiveNames())
63             ->map(function ($name) {
64                 return preg_quote($name);
65             })->implode('|');
66 
67         foreach ($htmlRegions as $region) {
68             preg_match_all(
69                 '/(?<!@)@(?!@)('.$pattern.')/i',
70                 $region[1], $matches,
71                 PREG_OFFSET_CAPTURE
72             );
73 
74             $directiveIndex = $matches[0];
75         }
76     }
77 }
```

In **Figure 16.14**, we have added a significant amount of code, with the vast majority of it being related to defining the list of core Blade directives and setting custom directives. Our additions between lines 57 and 75 are more interesting, however.

Between lines 57 and 60, we use Laravel’s collections to retrieve all of the `T_INLINE_HTML` tokens from the results of calling PHP’s `token_get_all` function, allowing us to get everything in our document that is not PHP code.

On lines 62-65 we create our dynamic regular expression using the core and custom Blade directives list. From here, we start to iterate each HTML region between lines 67 and 75.

The first thing we do within our loop is to use our regular expression to get all matches within the current region with their offsets. At this point in our implementation, if we were to invoke our parser like so:

Figure 16.15 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 @@foreach ($users as $user)
 5 
 6 @@endforeach
 7 
 8 @foreach ($users as $user)
 9 
10 
11 @endforeach
12 BLADE;
13 
14 $validator = new BladeDirectiveValidator();
15 $validator->parse($blade);
```

Our `$directiveIndex` variable would contain the following array of matches:

Figure 16.16 

```
 1 array:2 [
 2   0 => array:2 [
 3     0 => "@for"
 4     1 => 43
 5   ]
 6   1 => array:2 [
 7     0 => "@endfor"
 8     1 => 72
 9   ]
10 ]
```

We can see that our regular expression has skipped the first two directives since they were escaped by using two “@” characters. From here, we will visit each directive’s offset captured by our regular expression and use techniques we’ve seen before to tackle our directives.

Figure 16.17 Parsing Blade Directives 

```
  1 <?php
  2 
  3 // ...
  4 
  5 class BladeDirectiveCursor extends AbstractStringCursor
  6 {
  7     public function accept(string $current,
  8                            ?string $prev = null,
  9                            ?string $next = null): ?bool
 10     {
 11         if ($next == null || ctype_space($next)) {
 12             return $this->break();
 13         }
 14 
 15         if (ctype_punct($next) && $next != '_' && $next != '-') {
 16             return $this->break();
 17         }
 18 
 19         return $this->continue();
 20     }
 21 }
 22 
 23 class BladeDirectiveValidator
 24 {
 25     // ...
 26     protected $directiveCursor;
 27     protected $hasAdvancedIterator = false;
 28     protected $locator;
 29     protected $structures = [];
 30     protected $lineOffset = 0;
 31 
 32     private function advance($targetOffset)
 33     {
 34         $targetOffset -= 1;
 35         if ($targetOffset <= 0) { $targetOffset = 0; }
 36 
 37         $byteSize = $this->string->index()[$targetOffset];
 38 
 39         if (!$this->hasAdvancedIterator &&
 40             $this->string->key() != $targetOffset) {
 41             $this->hasAdvancedIterator = true;
 42             $this->string->setIteratorPosition(
 43                 $targetOffset,
 44                 $byteSize
 45             );
 46         } else {
 47             $this->hasAdvancedIterator = true;
 48         }
 49     }
 50 
 51     protected function fillStructureDetails(CursorResult $result,
 52                                             BladeStructure $structure)
 53     {
 54         $structure->startPosition = $result->startPosition;
 55         $structure->endPosition = $result->endPosition;
 56         $structure->length = $result->length;
 57 
 58         $location = $this->locator->getCharPosition(
 59             $result->startPosition
 60         );
 61 
 62         if ($location) {
 63             $structure->line = $location->line + $this->lineOffset;
 64         }
 65 
 66         return $structure;
 67     }
 68 
 69     protected function parseDirective($offset)
 70     {
 71         $directive = null;
 72 
 73         $this->hasAdvancedIterator = false;
 74 
 75         foreach ($this->string as $char) {
 76             if (!$this->hasAdvancedIterator) {
 77                 $this->advance($offset);
 78                 continue;
 79             }
 80 
 81             $result = $this->directiveCursor->traverse();
 82 
 83             $directive = new ParsedDirective();
 84             $this->fillStructureDetails($result, $directive);
 85             if (str($result->value)->startsWith('@')) {
 86                 $directive->directiveName = str($result->value)
 87                                                 ->substr(1)
 88                                                 ->toString();
 89             } else {
 90                 $directive->directiveName = $result->value;
 91             }
 92             break;
 93         }
 94 
 95         return $directive;
 96     }
 97 
 98     public function parse($value)
 99     {
100         $value = $this->prepareInput($value);
101 
102         $htmlRegions = collect(token_get_all($value))
103             ->filter(function ($token) {
104                 return is_array($token) && $token[0] == T_INLINE_HTML;
105             })->all();
106 
107         $this->structures = [];
108 
109         $pattern = collect($this->getDirectiveNames())
110             ->map(function ($name) {
111                 return preg_quote($name);
112             })->implode('|');
113 
114         foreach ($htmlRegions as $region) {
115             $this->lineOffset = $region[2] - 1;
116             $this->string = new Utf8StringIterator($region[1]);
117             $this->locator = new CharacterPositionLocator($region[1]);
118             $this->directiveCursor = new BladeDirectiveCursor(
119                 $this->string
120             );
121 
122             preg_match_all(
123                 '/(?<!@)@(?!@)('.$pattern.')/i',
124                 $region[1], $matches,
125                 PREG_OFFSET_CAPTURE
126             );
127 
128             $directiveIndex = $matches[0];
129 
130             for ($i = 0; $i < count($directiveIndex); $i++) {
131                 $directive = $this->parseDirective(
132                     $directiveIndex[$i][1]
133                 );
134 
135                 if ($directive != null) {
136                     $this->structures[] = $directive;
137                 }
138             }
139         }
140     }
141 }
```

We’ve added a lot in **Figure 16.17**, but the additions broadly apply similar techniques and concepts we’ve seen in previous sections and chapters. Within our parse method, we initialize a handful of instance variables between lines 108 and 113. Because it is possible we may be iterating multiple HTML regions, we must create new instances of our `Utf8StringIterator`, line and column number locator, and related objects for each HTML region.

Between lines 130 and 138, we iterate each directive match within the current HTML region and call a new `parseDirective` method with the match’s offset. Let us spend some time discussing what is happening within the `parseDirective` method, which includes an exciting technique we have not seen yet.

Our new `parseDirective` method is defined between lines 69 and 96 and will receive the offset of the directive to parse. Our directive parser utilizes the instance’s `Utf8StringIterator` class to iterate the characters of our input text; this is beneficial since they work well with our cursor implementations, which help to simplify our parsing tasks. However, we have an interesting situation since each time we begin looping over an iterable object, its `rewind` method is called, which resets the position of the loop back to the first position.

This behavior is typically desired, but since we are using our regular expression to retrieve the offset of each directive, we need to be able to start our foreach loop at arbitrary positions within the string. We accomplish this by using our `$hasAdvancedIterator` flag to check if we’ve moved our iterator to the correct location. If we haven’t, we call our internal `advance` method with the desired offset and then continue on to the next iteration of our loop, which will now be located at the correct position.

Looking at our `advance` method defined between lines 32 and 49, we find several interesting things. First, we calculate the target offset on line 34, which will be one less than the regular expressions offset. This is because the regular expression will return the location of the “@” character. We want the offset that immediately precedes that location so that when we start looping our string, we begin on the “@” character (recall that after we advance our iterator, we use the `continue` keyword to move over it). On line 35, check if the new target offset is less than zero. If it is, we reset our target offset back to zero to accommodate the case where our document begins with a Blade directive. Once we have our target offset, we retrieve the number of bytes at that location within the string. If the iterator’s current location does not match our target offset, we manually set it between lines 42 and 45. Now that we have a way to jump around our string within the context of a `Utf8StringIterator` loop, we can bring in the cursor concept we worked through in Chapter 15.

The first new cursor we introduce is the `BladeDirectiveCursor`, defined between lines 5 and 21, which will work to find the end of the current Blade directive. We call this cursor’s `traverse` method on line 81, which will collect the details of our directive and advance our string’s iterator over the directive’s name.

Once we’ve done this, we create a new instance of our `ParsedDirective` class on line 83. We use our `fillStructureDetails` method on line 84 to populate information such as the directive’s start and end offset and its line number. It has been implemented this way so we can reuse this logic later when parsing directive parameters. The final thing we do within our `parseDirective` method before returning the directive is to set the directive name using the `substr` helper method.

When we determine the directive names between lines 85 and 91, we check to see if our current value starts with the “@” character. If it doesn’t, this indicates that the document started with a Blade directive. We do not use the `substr` helper method when this is the case.

If we were to invoke our validator’s parse method like so:

Figure 16.18 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 @@foreach ($users as $user)
 5 
 6 @@endforeach
 7 
 8 @foreach ($users as $user)
 9 
10 
11 @endforeach
12 BLADE;
13 
14 $validator = new BladeDirectiveValidator();
15 $validator->parse($blade);
```

We would receive the following list of structures:

Figure 16.19 

```
 1 array:2 [
 2   0 => ParsedDirective {
 3     startPosition: 43
 4     endPosition: 50
 5     length: 8
 6     line: 5
 7     args: null
 8     directiveName: "foreach"
 9   }
10   1 => ParsedDirective {
11     startPosition: 72
12     endPosition: 82
13     length: 11
14     line: 8
15     args: null
16     directiveName: "endforeach"
17   }
18 ]
```

We are starting to get somewhere and just need to take care of directive parameters next.

### 16.3 Parsing Directive Parameters

Parsing Blade directive parameters will be very similar to how we are parsing the directives themselves. The main difference is we need a simple way to look to the next non-whitespace character and jump to its location. We can also implement this using a cursor; it will simply break when it encounters a non-whitespace character. Once we have located the first instance of a non-whitespace character, we can check if it is the “(“ character. If it is, we can make use of our existing `PairedBracketCursor` cursor to scan to the end of the directive’s argument group:

Figure 16.20 Parsing Directive Parameters 

```
  1 <?php
  2 
  3 // ...
  4 
  5 class NonWhitespaceCursor extends AbstractStringCursor
  6 {
  7     public function accept(string $current,
  8                            ?string $prev = null,
  9                            ?string $next = null): ?bool
 10     {
 11         if (! ctype_space($current)) {
 12             return $this->break();
 13         }
 14 
 15         return $this->continue();
 16     }
 17 }
 18 
 19 class BladeDirectiveValidator
 20 {
 21     // ...
 22     protected $nonWhitespaceCursor;
 23     protected $pairedBracketCursor;
 24 
 25     protected function parseArgs($offset)
 26     {
 27         $args = null;
 28         $this->hasAdvancedIterator = false;
 29 
 30         foreach ($this->string as $char) {
 31             if (! $this->hasAdvancedIterator) {
 32                 $this->advance($offset);
 33                 continue;
 34             }
 35 
 36             // Get the argument string.
 37             $result = $this->pairedBracketCursor->traverse();
 38             $args = new ParsedArguments();
 39             $this->fillStructureDetails($result, $args);
 40             $args->content = $result->content;
 41             $args->value = $result->value;
 42 
 43             break;
 44         }
 45 
 46         return $args;
 47     }
 48 
 49     protected function parseDirective($offset)
 50     {
 51         $directive = null;
 52 
 53         $this->hasAdvancedIterator = false;
 54 
 55         foreach ($this->string as $char) {
 56             if (!$this->hasAdvancedIterator) {
 57                 $this->advance($offset);
 58                 continue;
 59             }
 60 
 61             $result = $this->directiveCursor->traverse();
 62 
 63             $directive = new ParsedDirective();
 64             $this->fillStructureDetails($result, $directive);
 65             if (str($result->value)->startsWith('@')) {
 66                 $directive->directiveName = str($result->value)
 67                                                 ->substr(1)
 68                                                 ->toString();
 69             } else {
 70                 $directive->directiveName = $result->value;
 71             }
 72 
 73             if ($directive->endPosition + 1 < count($this->string)) {
 74                 $this->string->setIteratorPosition(
 75                     $directive->endPosition + 1,
 76                     $this->string->index()[$directive->endPosition + 1]
 77                 );
 78 
 79                 $nextNonWhitespace = $this->nonWhitespaceCursor
 80                     ->traverse();
 81 
 82                 if (str($nextNonWhitespace->value)->endsWith('(')) {
 83                     $directive->args = $this->parseArgs(
 84                         $nextNonWhitespace->endPosition
 85                     );
 86                 }
 87             }
 88 
 89             break;
 90         }
 91 
 92         return $directive;
 93     }
 94 
 95     public function parse($value)
 96     {
 97         // ...
 98 
 99         foreach ($htmlRegions as $region) {
100             $this->lineOffset = $region[2] - 1;
101             $this->string = new Utf8StringIterator($region[1]);
102             $this->locator = new CharacterPositionLocator($region[1]);
103             $this->directiveCursor = new BladeDirectiveCursor(
104                 $this->string
105             );
106 
107             $this->pairedBracketCursor = new PairedBracketCursor(
108                 $this->string,
109                 '(', ')'
110             );
111 
112             $this->nonWhitespaceCursor = new NonWhitespaceCursor(
113                 $this->string
114             );
115 
116         }
117 
118         return $this->structures;
119     }
120 }
```

The additions in **Figure 16.20** will feel similar to those added to parse the directives themselves. Our new `NonWhitespaceCursor` is defined on lines 5-17, which breaks whenever it encounters a non-whitespace character. We initialize this new cursor and our `PairedBracketCursor` between lines 107 and 114. Our most substantial changes occur within the `parseDirective` method, between lines 68 and 82.

Between lines 74 and 77, we adjust our string iterator’s position over the end of the directive name. This will help to ensure that our non-whitespace cursor does not break early on the directive’s name itself.

Once we have moved our iterator over the directive name, we call the traverse method on our `NonWhitespaceCursor`. When the `NonWhitespaceCursor` has completed its traversal, and its value ends with the “(“ character, we then call the `parseArgs`, using the offset of the “(“ character from the `NonWhitespaceCursor`.

Our `parseArgs` method is very similar to our `parseDirective` method and simply scans to the end of a parameter group. Invoking our validator’s `parse` method on our sample input like so:

Figure 16.21 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 @foreach ($invoices as $invoice)
 5 
 6     <?php echo $invoice->number; ?>
 7 
 8 @endforeach
 9 BLADE;
10 
11 $validator = new BladeDirectiveValidator();
12 $validator->parse($blade);
```

Now produces the following output:

Figure 16.22 

```
 1 array:2 [
 2   0 => ParsedDirective {
 3     startPosition: 1
 4     endPosition: 7
 5     length: 7
 6     line: 1
 7     args: ParsedArguments {
 8       startPosition: 9
 9       endPosition: 31
10       length: 23
11       line: 1
12       value: "($invoices as $invoice)"
13       content: "$invoices as $invoice"
14     }
15     directiveName: "foreach"
16   }
17   1 => ParsedDirective {
18     startPosition: 1
19     endPosition: 11
20     length: 11
21     line: 5
22     args: null
23     directiveName: "endforeach"
24   }
25 ]
```

Our example in **Figure 16.22** now contains the contents of our directive’s arguments, and we can begin writing our validation logic.

### 16.4 Validating Blade Directives

In this final section, we will work to implement a Blade directive validation system. Our validation system will allow developers to specify arbitrary callback functions that will be used to determine if a directive is valid or not. We will also use this system internally to support the default validators. Our validation functions will indicate an issue if they return a string, and returning nothing will mean that the directive passed that particular validation rule.

To begin, we will add our `$validators` array and our `addValidator` method:

Figure 16.23 Beginning the Validator Implementation 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7     // ...
 8     protected $validators = [];
 9     
10     // ...
11 
12     public function addValidator($directive, $validator)
13     {
14         $directive = str($directive)->lower->toString();
15 
16         if (! array_key_exists($directive, $this->validators)) {
17             $this->validators[$directive] = [];
18         }
19 
20         $this->validators[$directive][] = $validator;
21     }
22 }
```

Now that we have a way to add validators, we can add our `validate` method, which will parse our template and invoke our validators on all directives within the provided template:

Figure 16.24 Adding our Validate Method 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7     // ...
 8 
 9     public function validate($value)
10     {
11         $structures = $this->parse($value);
12 
13         foreach ($structures as $structure) {
14             if (! $structure instanceof ParsedDirective) {
15                 continue;
16             }
17 
18             $directive = str($structure->directiveName)
19                 ->lower->toString();
20 
21             if (! array_key_exists($directive, $this->validators)) {
22                 continue;
23             }
24 
25             foreach ($this->validators[$directive] as $validator) {
26                 $result = $validator($structure);
27 
28                 if (is_string($result)) {
29                     throw new Exception(
30                         $result . ' on line ' .
31                         $structure->line
32                     );
33                 }
34             }
35         }
36     }
37 }
```

The first thing we do within our `validate` method is to parse the input text on line 11. From there, we iterate all the directives discovered during the parsing process. If validators exist for the current directive name, we invoke the validator supplying the directive as the first and only argument.

Lines 27 and 33 are where our validator implementation gets interesting. If a validator returns a string as its result, we will use that as an indicator that the directive has failed the validation and use the returned message to help construct an exception message.

Let us now create a sample validator to validate that “if” statements contain an expression:

Figure 16.25 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 
 5 @if ()
 6 
 7 @endif
 8 BLADE;
 9 
10 $validator = new BladeDirectiveValidator();
11 $validator->addValidator('if', function ($directive) {
12     if ($directive->args == null || $directive->args->content == '') {
13         return 'if statement does not have condition';
14     }
15 });
16 
17 $validator->validate($blade);
```

When executed, our sample code in **Figure 16.25** would raise an exception with the following message:

Figure 16.26 

```
1 if statement does not have condition on line 2
```

We can generalize our example validator in **Figure 16.25** to make it easier to work with. Additionally, we can also support the opposite validation rule: ensuring a directive does *not* have an argument group:

Figure 16.27 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7     // ...
 8 
 9     public function shouldHaveArgs($directives)
10     {
11         if (! is_array($directives)) {
12             $directives = [$directives];
13         }
14 
15         foreach ($directives as $directive) {
16             $this->addValidator($directive, function ($structure)
17             use ($directive) {
18                 if ($structure->args == null ||
19                     $structure->args->content == '') {
20                     return '@' . $directive .
21                         ' is missing required argument group';
22                 }
23 
24                 return true;
25             });
26         }
27 
28         return $this;
29     }
30 
31     public function shouldNotHaveArgs($directives)
32     {
33         if (! is_array($directives)) {
34             $directives = [$directives];
35         }
36 
37         foreach ($directives as $directive) {
38             $this->addValidator($directive, function ($structure)
39             use ($directive) {
40                 if ($structure->args != null) {
41                     return 'Unexpected argument group for @' .
42                         $directive.' directive';
43                 }
44 
45                 return true;
46             });
47         }
48 
49         return $this;
50     }
51 }
```

We can use our new validation helpers like so to achieve the same result:

Figure 16.28 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 
 5 @if (true)
 6 
 7 @endif ()
 8 BLADE;
 9 
10 $validator = new BladeDirectiveValidator();
11 $validator->shouldHaveArgs('if')
12     ->shouldNotHaveArgs('endif');
```

Our example in **Figure 16.28** would now throw an exception with the following message:

Figure 16.29 

```
1 Unexpected argument group for @endif directive on line 4
```

### 16.5 Ensuring Consistent Directive Casing

A common desire when working on large software applications or with a team of sufficient size is to ensure consistent casing when writing code. We can expand our validation system to enforce consistent casing when working with Blade directives.

Figure 16.30 Validating Directive Name Casing 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7     // ...
 8 
 9     public function mustMatchCase($directives)
10     {
11         if (! is_array($directives)) {
12             $directives = [$directives];
13         }
14 
15         foreach ($directives as $directive) {
16             $this->addValidator($directive, function ($structure)
17             use ($directive) {
18                 if ($structure->directiveName != $directive) {
19                     return 'Directive @'.$structure->directiveName .
20                         ' does not match case of @' . $directive;
21                 }
22 
23                 return true;
24             });
25         }
26 
27         return $this;
28     }
29 
30     public function validateCoreDirectiveCasing()
31     {
32         $this->mustMatchCase($this->coreDirectives);
33 
34         return $this;
35     }
36 }
```

In **Figure 16.30**, we’ve added a new `mustMatchCase` validation method. If directive names within the source document do not match the case supplied to this method, a validation exception will be thrown. Additionally, we’ve added a `validateCoreDirectiveCasing` method which will add similar validation methods for all core Blade directives.

Using our new methods like so:

Figure 16.31 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 
 5 @if (true)
 6     @customDirective
 7 @endIf
 8 BLADE;
 9 
10 $validator = new BladeDirectiveValidator();
11 $validator->setCustomDirectives([
12     'customDirective'
13 ]);
14 
15 $validator->validateCoreDirectiveCasing()
16     ->mustMatchCase('customDIRECTIVE');
17 
18 $validator->validate($blade);
```

Would generate the following validation exception:

Figure 16.32 

```
1 Directive @customDirective does not match case
2 of @customDIRECTIVE on line 3
```

### 16.6 Enforcing Spacing after Directive Names

Similar to ensuring consistent casing of Blade directive names, it may also be desirable to ensure uniform spacing between a directive’s name and its argument group. As an example, **Figure 16.33** contains numerous directives with different spacing, as well as one example of a directive’s arguments appearing on a separate line:

Figure 16.33 

```
1 @if   (true)
2 
3     @if 
4             (5 < 3)
5     @endif
6 @endif
```

We can implement validation methods to account for both of the scenarios like so:

Figure 16.34 

```
 1 <?php
 2 
 3 // ...
 4 
 5 class BladeDirectiveValidator
 6 {
 7     // ...
 8     protected $argGroupSpacing = null;
 9 
10     public function validate($value)
11     {
12         $structures = $this->parse($value);
13 
14         foreach ($structures as $structure) {
15             if (! $structure instanceof ParsedDirective) {
16                 continue;
17             }
18 
19             $directive = str($structure->directiveName)
20                 ->lower->toString();
21 
22             if ($structure->args != null) {
23                 $this->validateArgumentOnSameLine($structure);
24 
25                 if ($this->argGroupSpacing != null) {
26                     $spacing = $structure->args->startPosition -
27                         $structure->endPosition - 1;
28 
29                     if ($spacing !=  $this->argGroupSpacing) {
30                         throw new Exception(
31                             'Improper spacing between @' .
32                             $structure->directiveName .
33                             ' and its arguments. Expected ' .
34                             $this->argGroupSpacing.' spaces, got ' .
35                             $spacing . ' on line ' . $structure->line
36                         );
37                     }
38                 }
39             }
40 
41             // ...
42         }
43     }
44 
45     protected function validateArgumentOnSameLine(
46         ParsedDirective $structure
47     )
48     {
49         if ($structure->line != $structure->args->line) {
50             throw new Exception(
51                 'Start of argument group for @' .
52                 $structure->directiveName .
53                 ' directive must be on the same line on line ' .
54                 $structure->line
55             );
56         }
57     }
58 
59     public function requireArgGroupSpacing($spacing)
60     {
61         $this->argGroupSpacing = $spacing;
62 
63         return $this;
64     }
65 }
```

Our changes in **Figure 16.34** add several new methods and a new private class property: `$argGroupSpacing`. The `requireArgGroupSpacing` method will set our new property, indicating that our validator should check the spacing between a directive’s name and its argument group.

The argument group validation methods have been added to our existing validate method, and these changes appear between lines 22 and 39. On line 22, we check if the current directive has any arguments before attempting to validate them. If our internal `$argGroupSpacing` value is not `null`, we calculate the number of spaces that appear from the end of the directive name and the start of its arguments on line 26. We throw a new exception if this value does not equal our desired amount.

Figure 16.35 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 @if   (true)
 5 
 6     @if 
 7             (5 < 3)
 8     @endif
 9 @endif
10 BLADE;
11 
12 $validator = new BladeDirectiveValidator();
13 $validator->requireArgGroupSpacing(1);
```

The code example in **Figure 16.35** would throw an exception with the following message:

Figure 16.36 

```
1 Improper spacing between @if and its arguments. Expected 1 spaces, got \
2 3 on line 1
```

Correcting the spacing issue and rerunning our example:

Figure 16.37 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 @if (true)
 5 
 6     @if 
 7             (5 < 3)
 8     @endif
 9 @endif
10 BLADE;
11 
12 $validator = new BladeDirectiveValidator();
13 $validator->requireArgGroupSpacing(1);
```

Would now produce the following validation exception, alerting us of an argument group appearing on a different line than its directive:

Figure 16.38 

```
1 Start of argument group for @if directive must be
2 on the same line on line 3
```

## 17\. Working with HTML

Broadly speaking, the questions I have received over the years relating to working with HTML have fallen into three categories: generating new HTML, manipulating existing HTML, and analyzing HTML-like documents with other languages embedded in them. The first category is one we are all generally familiar with, as the output of most PHP applications is an HTML string, whether produced entirely in PHP or through some other purpose-built templating engine, such as Blade. However, things get particularly interesting and nuanced in the last two categories.

An example of manipulating existing HTML may be adding CSS classes to specific elements. The desire here is usually to express the targeted HTML elements using CSS’s selector syntax, which we will cover later in this chapter. Another example would be to reverse the double-encoding of HTML entities in the generated output, which can commonly occur accidentally with many layers of HTML output generated by content management systems.

The third category, analyzing HTML documents with other embedded languages, is the much more interesting of the three. The complexity within this category is that the embedded languages typically significantly make the overall document invalid HTML. Let us consider **Figure 17.1**, which is a snippet of Antlers, the templating language for Statamic, a Laravel-based content management system:

Figure 17.1 

```
1 <{{ as or 'a' }} class="list of CSS classes">
2     Element content.
3 </{{ as or 'a' }}>
```

The exact semantics of what is happening in **Figure 17.1** are unimportant, except that we have some embedded code that will dynamically generate an HTML element’s name. These scenarios are relatively straightforward for us to visually analyze but add significant complexity when attempting to analyze the structure of our HTML documents using existing third-party libraries, which may not handle arbitrary embedded languages gracefully. This is not necessarily a problem with these libraries, either, and their goal is to analyze HTML and not the infinite number of other ways HTML may be dynamically constructed. We will discuss techniques for managing these scenarios towards the end of this chapter.

Throughout this chapter, we will work through various examples to traverse, manipulate, and modify existing HTML documents. We will use a few packages released by Symfony: the `symfony/dom-crawler` and `symfony/css-selector` packages. Symfony’s DomCrawler package makes traversing HTML and XML documents more accessible, and the CssSelector allows us to use CSS selectors to retrieve nodes from structured documents.

To get started using the DOM Crawler package, we can create a new `Crawler` instance while supplying the HTML or XML document as the first argument:

Figure 17.2 Creating a new Crawler Instance 

```
 1 <?php
 2 
 3 use Symfony\Component\DomCrawler\Crawler;
 4 
 5 $html = <<<'HTML'
 6 <!DOCTYPE html>
 7 <html>
 8     <body>
 9         <div class="profiles">
10             <div class="profile">
11                 <h3 class="name">Alice</h3>
12                 <p class="location">US</p>
13             </div>
14             <div class="profile">
15                 <h3 class="name">Bob</h3>
16                 <p class="location">CA</p>
17             </div>
18             <div class="profile">
19                 <h3 class="name">Charlie</h3>
20                 <p class="location">UK</p>
21             </div>
22             <div class="profile">
23                 <h3 class="name">Daniel</h3>
24                 <p class="location">MX</p>
25             </div>
26         </div>
27     </body>
28 </html>
29 HTML;
30 
31 $crawler = new Crawler($html);
```

Now that we have a crawler instance, we can use its public API to interact with our document more straightforwardly, compared to working directly with the underlying `DOMDocument`, `DOMNodeList`, and `DOMNode` instances. For instance, we can use the `filter` method to target all elements containing the `location` class and then use the `each` method on the returned list of nodes.

The `each` method allows us to specify a callback function that will receive each element that matches our selector. The `each` method will use the returned value of our callback as its result, similar to Laravel’s collection `map` method. Our example in **Figure 17.3** will return the inner text of elements that contain the `location` class:

Figure 17.3 

```
1 <?php
2 
3 $locations = $crawler->filter('.location')
4     ->each(fn($l) => $l->innerText());
```

**Figure 17.3** would produce the following result:

Figure 17.4 

```
1 array:4 [
2   0 => "US"
3   1 => "CA"
4   2 => "UK"
5   3 => "MX"
6 ]
```

Our example in **Figure 17.3** is not overly specific on what elements it matches. For instance, if our input document contained the following text:

Figure 17.5 

```
 1 <!DOCTYPE html>
 2 <html>
 3     <body>
 4         <p class="location">A non-profile location.</p>
 5         <div class="profiles">
 6             <div class="profile">
 7                 <h3 class="name">Alice</h3>
 8                 <p class="location">US</p>
 9             </div>
10             <div class="profile">
11                 <h3 class="name">Bob</h3>
12                 <p class="location">CA</p>
13             </div>
14             <div class="profile">
15                 <h3 class="name">Charlie</h3>
16                 <p class="location">UK</p>
17             </div>
18             <div class="profile">
19                 <h3 class="name">Daniel</h3>
20                 <p class="location">MX</p>
21             </div>
22         </div>
23     </body>
24 </html>
```

Our locations array would now include the following results:

Figure 17.6 

```
1 array:5 [
2   0 => "A non-profile location."
3   1 => "US"
4   2 => "CA"
5   3 => "UK"
6   4 => "MX"
7 ]
```

This may be perfectly fine, depending on the use case. Still, if we only wanted to return the locations associated with a profile, we could adjust our selector to target our desired elements more specifically. We can do this because we are also using the CssSelector package:

Figure 17.7 

```
1 <?php
2 
3 $locations = $crawler->filter('.profile .location')
4     ->each(fn($l) => $l->innerText());
```

The `filter` method returns a Crawler instance, allowing us to retrieve more specific information from each matched element. As an example, **Figure 17.8** utilizes this to extract the name and location of each profile within the source document by calling the `innerText` method their respective elements:

Figure 17.8 

```
 1 <?php
 2 
 3 use Symfony\Component\DomCrawler\Crawler;
 4 
 5 $html = <<<'HTML'
 6 <!DOCTYPE html>
 7 <html>
 8     <body>
 9         <div class="profiles">
10             <div class="profile">
11                 <h3 class="name">Alice</h3>
12                 <p class="location">US</p>
13             </div>
14             <div class="profile">
15                 <h3 class="name">Bob</h3>
16                 <p class="location">CA</p>
17             </div>
18             <div class="profile">
19                 <h3 class="name">Charlie</h3>
20                 <p class="location">UK</p>
21             </div>
22             <div class="profile">
23                 <h3 class="name">Daniel</h3>
24                 <p class="location">MX</p>
25             </div>
26         </div>
27     </body>
28 </html>
29 HTML;
30 
31 $crawler = new Crawler($html);
32 
33 $profiles = $crawler->filter('.profile')
34     ->each(function (Crawler $profile) {
35         $name = $profile->filter('.name')->innerText();
36         $location = $profile->filter('.location')->innerText();
37 
38         return [
39             'name'     => $name,
40             'location' => $location
41         ];
42 });
```

After our code in **Figure 17.8** has executed, we would end up with the following array of profiles:

Figure 17.9 

```
 1 array:4 [
 2   0 => array:2 [
 3     "name" => "Alice"
 4     "location" => "US"
 5   ]
 6   1 => array:2 [
 7     "name" => "Bob"
 8     "location" => "CA"
 9   ]
10   2 => array:2 [
11     "name" => "Charlie"
12     "location" => "UK"
13   ]
14   3 => array:2 [
15     "name" => "Daniel"
16     "location" => "MX"
17   ]
18 ]
```

Symfony’s DomCrawler package can also modify the attributes of existing HTML. For example, we could use it to add Tailwind CSS classes to dynamic output, such as that from a content management system:

Figure 17.10 

```
 1 <?php
 2 
 3 use Symfony\Component\DomCrawler\Crawler;
 4 
 5 $html = <<<'HTML'
 6 <article>
 7     <h1>Title</h1>
 8 
 9     <p>Paragraph one.</p>
10     <p>Paragraph two.</p>
11 </article>
12 
13 <article>
14     <h1>Title Two</h1>
15 
16     <p>Paragraph one.</p>
17     <p>Paragraph two.</p>
18 </article>
19 HTML;
20 
21 $crawler = new Crawler($html);
22 $articles = $crawler->filter('article');
23 
24 foreach ($articles as $article) {
25     $article->setAttribute('class', 'prose lg:prose-xl');
26 }
27 
28 $output = $crawler->html();
```

In **Figure 17.10**, we instantiate a new Crawler instance using a partial HTML document as its input. We then use the filter method to retrieve all of the “article” elements. Once we have our list of articles, we use a foreach loop to iterate all of the `DOMElement` instances and call the `setAttribute` method to add a list of classes to our HTML elements. Finally, we utilize the `html` method to return the modified HTML output we see in **Figure 17.11**:

Figure 17.11 

```
 1 <body><article class="prose lg:prose-xl">
 2     <h1>Title</h1>
 3 
 4     <p>Paragraph one.</p>
 5     <p>Paragraph two.</p>
 6 </article>
 7 
 8 <article class="prose lg:prose-xl">
 9     <h1>Title Two</h1>
10 
11     <p>Paragraph one.</p>
12     <p>Paragraph two.</p>
13 </article></body>
```

Our output in **Figure 17.11** is close to our desired outcome but is wrapped in an extra tag pair. We can take care of these additional tags by using Laravel’s string helpers; more specifically, the `substr` method, to remove the beginning and end of our resulting string:

Figure 17.12 

```
1 <?php
2 
3 $output = str($crawler->html())
4             ->substr(6)
5             ->substr(0, -7)
6             ->toString();
```

With our changes in **Figure 17.12**, our output would now be as we expect:

Figure 17.13 

```
 1 <article class="prose lg:prose-xl">
 2     <h1>Title</h1>
 3 
 4     <p>Paragraph one.</p>
 5     <p>Paragraph two.</p>
 6 </article>
 7 
 8 <article class="prose lg:prose-xl">
 9     <h1>Title Two</h1>
10 
11     <p>Paragraph one.</p>
12     <p>Paragraph two.</p>
13 </article>
```

### 17.1 Reversing Double Encoded HTML Entities

The double encoding of HTML entities is a common issue we have to deal with. Often, it is caused by a front-end editor unknowingly encoding special characters. Then a second process performs an HTML encoding step before the information is displayed on our sites. An example of what the final result may look like can be found in **Figure 17.14**:

Figure 17.14 

```
1 <p>&amp;copy; Author Name</p>
```

In **Figure 17.14**, we have a double-encoded copyright symbol character. The first step of the process produced:

Figure 17.15 

```
1 <p>&copy; Author Name</p>
```

And when the second encoding process occurred, it encoded the “&” character of the previous operation to produce the output in **Figure 17.14**. If we look at our incorrectly encoded output, we can see that all of our undesired encodings will always start with the “&” character sequence. We can leverage this fact to construct a small helper method that can help to reverse our unintended double-encoding:

Figure 17.16 reverseHtmlEncoding Helper Method Implementation 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 use Illuminate\Support\Stringable;
 5 
 6 Str::macro('reverseHtmlEncoding', function ($value) {
 7     $reversed = (string) str($value)->replace('&amp;', '&');
 8 
 9     return preg_replace_callback('/&(?!&)[^#A-z]/', function ($matches)\
10  {
11         return '&amp;'.substr($matches[0], 1);
12     }, $reversed);
13 });
14 
15 Stringable::macro('reverseHtmlEncoding', function () {
16     return new static(Str::reverseHtmlEncoding($this->value));
17 });
```

We can use our new helper method to reverse double-encoded HTML entities like so:

Figure 17.17 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 // Returns "&copy; Author Name"
6 Str::reverseHtmlEncoding("&amp;copy; Author Name");
```

Our method works by first replacing all instances of “&” with a single instance of the “&” character. This solves our immediate issue of undoing double-encoded HTML entities but is overly aggressive and will undo the encoding where it shouldn’t. An example scenario where we should not undo the encoding can be found in **Figure 17.18**:

Figure 17.18 

```
1 &amp;copy; Author Name &amp;123
```

**Figure 17.18** shows the sequence “&123”. Undoing this encoding results in the value “&123”, which is not a valid HTML entity. To prevent this, we use our regular expression between lines 9 and 11 and PHP’s `preg_replace_callback` to revert the changes made by our string replacement on line 7.

### 17.2 Working with Embedded Languages

Throughout the remainder of this chapter, we will work to build an HTML fragment and position analyzer. Our parser will not be concerned with creating the association between HTML elements, nor will it work to extract the content or sections of the document between the elements. Instead, we will focus entirely on where HTML elements appear and what features they may have, such as parameters or attributes. The intended use-case for this parser will be to help make decisions from the results of other parsers.

As an example, let us look at the following Blade template, which dynamically constructs an HTML tag-pair from a variable:

Figure 17.19 

```
1 <{{ $element }} class="bg-white">
2 
3 </{{ $element }}>
```

It is relatively simple for us to read through **Figure 17.19** and understand the intention behind the dynamic code. However, this task is much more difficult for HTML parsers or analysis systems. For instance, if we were to ignore the invalid characters at that location within an HTML document, would the tag name become “{{“ or “{{ $element }}”? Questions like this make working HTML documents containing embedded languages particularly difficult, especially when we need to preserve our account for the embedded languages.

The system we will work through will allow us to reasonably quickly solve these problems and provide a foundation for new features. This system will be able to accept an input document containing HTML with any number of embedded languages and produce a list of parsed HTML nodes we can ask questions about to help with whatever our task is. Our HTML parser will be able to accept ranges within the document parser it should ignore.

When our specialized HTML parser encounters one of these regions, it will skip over them and continue with the source document. This is similar to our previous technique of filling a document with spaces and newlines, with the vital difference being we do not remove information from the input document. These ranges will come from other parsers, such as a dedicated Blade parser, and allow our HTML parser to only concern itself with determining what is most likely to produce HTML once the embedded languages have been evaluated.

I have used this technique numerous times over the years to help develop code formatting systems for languages embedded in HTML. Determining the context in which a piece of embedded code is being used is tremendously valuable in ensuring the final results are reasonably acceptable. For instance, the rules for indenting a Blade directive are significantly different depending on whether it appears within the content between two HTML tags or is used as an HTML attribute or parameter.

An important distinction to make between our system and standard HTML parsers is that our parser will work to try and make sense of incomplete document information. For example, our parse will be able to handle documents where HTML elements contain invalid characters within the tag name, as we have seen before. In addition to this, our parser will also work to make sense of documents similar to **Figure 17.20**:

Figure 17.20 

```
1 <{{ $element }} {{ "<nested>" . "</elements>" }}>
2 
3 </{{ $element }}>
```

In **Figure 17.20**, we have our dynamic tag names and strings embedded within the element’s content that could also be interpreted as HTML. Compared to standard HTML, our input document is quite disjointed compared to a valid document of similar structure, which is the justification for calling this system a “fragments” parser. The way we will work to handle these scenarios is to first use a different approach that will be able to extract information about our embedded languages, such as a Blade parser. Once we have these results, we can then convert them into a list of ranges that should be ignored by our HTML fragments parser.

Combined with its internal logic and the results of other dedicated parsers, our HTML fragments parser will return a list of potential HTML fragments. These fragments can be further analyzed to provide contextual information about any location within the source document. We can visualize the data flow of our system in **Figure 17.21**.

![Figure 17.21 Fragments Parser Data Flow](images/fragments_overview_smaller.png)

Figure 17.21 Fragments Parser Data Flow

We will begin implementing our fragments parser like we have many times before: by defining our data models. Additionally, we will create a base parser implementation that we will use to parse our HTML fragments and parameters later in this chapter. We can see these in **Figure 17.22**:

Figure 17.22 Beginning our HTML Fragments Parser 

```
 1 <?php
 2 
 3 enum AttributeType
 4 {
 5     case Attribute;
 6     case Parameter;
 7 }
 8 
 9 class Fragment
10 {
11     public $startPosition = 0;
12     public $endPosition = 0;
13     public $content = '';
14 
15     public function contains(int $position)
16     {
17         return $position >= $this->startPosition &&
18             $position <= $this->endPosition;
19     }
20 }
21 
22 class FragmentAttribute extends Fragment
23 {
24     public $name = '';
25     public $value = '';
26     public $type = AttributeType::Attribute;
27 }
28 
29 class HtmlFragment extends Fragment
30 {
31     public $isClosingTag = false;
32     public $isSelfClosing = false;
33     public $documentContent = '';
34     public $innerContent = null;
35     public $name = null;
36     public $tagName = '';
37 
38     /**
39      * @var FragmentAttribute[]
40      */
41     public $attributes = [];
42 }
43 
44 abstract class BaseFragmentParser
45 {
46     protected $string;
47     protected $buffer = '';
48     protected $position = 0;
49     protected $current = null;
50     protected $next = null;
51     protected $prev = null;
52 
53     protected function checkCurrentOffsets($offset)
54     {
55         $this->position = $offset;
56         $this->current = $this->string[$offset] ?? null;
57         $this->next = $this->string[$offset + 1] ?? null;
58         $this->prev = $this->string[$offset - 1] ?? null;
59     }
60 
61     protected function resetState()
62     {
63         $this->position = 0;
64         $this->buffer = '';
65         $this->next = null;
66         $this->prev = null;
67         $this->current = null;
68     }
69 
70     protected function isStartOfString()
71     {
72         return $this->current == '"' || $this->current == "'";
73     }
74 
75     protected function scanToEndOfString($start)
76     {
77         $stringStyle = $this->current;
78         $this->buffer .= $this->current;
79         $returnedOn = $start;
80 
81         for ($i = $start + 1; $i < count($this->string); $i++) {
82             $this->checkCurrentOffsets($i);
83 
84             $this->buffer .= $this->current;
85             if ($this->current == $stringStyle) {
86                 $returnedOn = $i;
87                 break;
88             }
89         }
90 
91         return $returnedOn;
92     }
93 }
```

In **Figure 17.22**, we have defined a base `Fragment` class, which contains a small amount of information, such as the original document’s content and start and end position. Additionally, on lines 15-19, we have defined a small helper method that can be used to determine if any arbitrary positions fall within the bounds of the fragment. We will extensively use this when implementing our fragments analyzer towards the end of this chapter.

Our `HtmlFragment` and `FragmentAttribute` classes extend our base fragment but add additional information for each use case. For instance, our `FragmentAttribute` defines a `$type` property that will indicate if any given nested fragment appears to be an HTML parameter or an attribute. Our `HtmlFragment`, however, contains much more information.

Our `HtmlFragment` is defined between lines 29 and 42. The `$isClosingTag` property will determine if the parsed fragment appears to be a closing tag, and the `$isSelfClosing` tag will indicate if the parsed fragment is a self-closing tag. The `$attributes` array on line 41 will contain instances of our `FragmentAttribute` class. The more interesting properties, however, are those related to the content and tag names.

The `$tagName` property will contain only the tag name that was parsed from the document; in most instances, this will be the document’s content that appears before the first space. The `$documentContent` will contain the parsed text that produced the HTML fragment; it will not contain the content that was ignored. Similarly, the `$innerContent` property will include all of the fragment’s content that appears after the tag name that was not skipped because of our ignore ranges.

Our `$name` property on line 35 will eventually become an instance of `Fragment`, allowing us to more easily detect if arbitrary positions fall within the name of an HTML element.

Our base fragment parser is defined between lines 44 and 93, and it sets up several utility methods we can use to manage our parser’s current state and detect and move over strings. These techniques are similar to those we developed in Chapter 16. Before diving too deeply into our implementations, we first explore what exactly it is our fragments parser will be using to determine fragment boundaries.

Looking at **Figure 17.23**, we can see a simple HTML document that Vue.js developers will be comfortable with. It contains a simple unordered list, some conditional logic, and a Vue loop:

Figure 17.23 

```
1 <ul v-if="items.length > 0 && items.length < 10">
2     <li v-for="item in items">
3         {{ item.text }}
4     </li>
5 </ul>
```

On line one, our unordered list contains a condition that contains some problematic characters. For instance, it includes the condition `items.length > 0`, which could be incorrectly interpreted as the ending of an HTML tag. Additionally, it has `items.length < 10`, which could also easily be interpreted as the start of a new HTML tag. We will consider these trivial cases because we can skip over all strings within our elements to avoid these characters.

A more complicated edge case can be found in **Figure 17.24**:

Figure 17.24 

```
1 <span>Is 5 < 3? No, but 3 < 5!</span>
```

In **Figure 17.24**, we have an HTML tag that contains less than and greater than characters within the tag’s content. It would be ideal if the input document contained the appropriate HTML entities for these two scenarios, but that is unfortunately not the case most of the time. These are more complicated to work around because we do not have a simple string that we can skip over. However, what we can do is every time we are parsing an HTML fragment and encounter a new instance of the greater than character, or the end of the input document, we can abandon parsing the current HTML fragment. In **Figure 17.24**, we can see this logic would abandon attempting to parse the `< 3` as an HTML element when it encounters the `< 5` further in the content. Similarly, it will abandon parsing the document’s `< 5` section when it meets the opening less than the character of the `</span>` element.

A similar edge case we will need to account for is script tags, which can contain problematic characters in numerous scenarios, such as in **Figure 17.25**:

Figure 17.25 

```
 1 <ul v-if="items.length > 0 && items.length < 10">
 2     <li v-for="item in items">
 3         {{ item.text }}
 4     </li>
 5 </ul>
 6 
 7 
 8 <script>
 9     if (total < accountBalance) {
10         // Process transaction.
11     }
12 </script>
```

Our strategy for handling JavaScript content will be to detect when we’ve entered a script tag and fast-forward through the document until we encounter the closing script tag. This is not a fool-proof method if our JavaScript contains a string literal containing the content “</script>,” but we will accept this limitation to simplify our parser’s implementation considerably.

We have discussed the concept of ignoring ranges of text within our parser. Let us take a moment to look at how this will work in practice before working on our fragments parser. In **Figure 17.26**, we have a simple Blade template that dynamically constructs HTML elements:

Figure 17.26 

```
1 <{{ $element }} class="bg-white">
2 
3 </{{ $element }}>
```

To demonstrate how flexible our concept can be, we will use a simple regular expression to find the regions we want to ignore. In **Figure 17.27**, we use a regular expression to find all areas of the document that match:

Figure 17.27 

```
1 <?php
2 
3 $blade = <<<'BLADE'
4 <{{ $element }} class="bg-white">
5 
6 </{{ $element }}>
7 BLADE;
8 
9 preg_match_all('/{{.*?}}/i', $blade, $echos, PREG_OFFSET_CAPTURE);
```

Which produces the following array of matches:

Figure 17.28 

```
 1 array:1 [
 2   0 => array:2 [
 3     0 => array:2 [
 4       0 => "{{ $element }}"
 5       1 => 1
 6     ]
 7     1 => array:2 [
 8       0 => "{{ $element }}"
 9       1 => 37
10     ]
11   ]
12 ]
```

When looking at **Figure 17.28**, we can see that our regular expression returns the start offset, as well as the content of the match. We can use these two pieces of information to construct an array containing the start and end offsets that our fragments parser should eventually ignore like so:

Figure 17.29 

```
1 <?php
2 
3 $ignore = [];
4 
5 foreach ($echos[0] as $match) {
6     $start = $match[1];
7     $end   = $start + str($match[0])->length() - 1;
8     $ignore[$start] = $end;
9 }
```

We calculate the end offset by adding the length of the content to the start offset and subtracting one. We subtract one here to account for the fact that our content contains the initial character captured by our start offset. After our code in **Figure 17.29** has executed, our `$ignore` array would include the following values:

Figure 17.30 

```
1 array:2 [
2   1 => 14
3   37 => 50
4 ]
```

### 17.3 Parsing Fragmented HTML Documents

We have enough background information to look at our `FragmentsDocumentParser` implementation:

Figure 17.31 FragmentsDocumentParser Implementation 

```
  1 <?php
  2 
  3 class FragmentsDocumentParser extends BaseFragmentParser
  4 {
  5     private $fragments = [];
  6 
  7     protected $ignoreRanges = [];
  8 
  9     private $isParsingScript = false;
 10 
 11     public function setIgnoreRanges($ignoreRanges)
 12     {
 13         $this->ignoreRanges = $ignoreRanges;
 14     }
 15 
 16     private function parseFragment($index)
 17     {
 18         $this->buffer = '';
 19         $brokeEarly = false;
 20 
 21         for ($i = $index; $i < count($this->string); $i++) {
 22             if (array_key_exists($i, $this->ignoreRanges)) {
 23                 $jumpIndex = $this->ignoreRanges[$i];
 24 
 25                 $this->buffer .= str(' ')->repeat($jumpIndex - $i + 1);
 26 
 27                 $i = $jumpIndex;
 28                 continue;
 29             }
 30             $this->checkCurrentOffsets($i);
 31 
 32             if (($i != $index && $this->current == '<') ||
 33                 ($this->current != '>' && $this->next == null)) {
 34                 $brokeEarly = true;
 35                 break;
 36             }
 37 
 38             if ($this->isStartOfString()) {
 39                 $i = $this->scanToEndOfString($i);
 40                 continue;
 41             }
 42 
 43             if ($this->current == '>') {
 44                 $this->buffer .= $this->current;
 45                 break;
 46             }
 47 
 48             $this->buffer .= $this->current;
 49         }
 50 
 51         if ($brokeEarly) {
 52             $this->buffer = '';
 53             return;
 54         }
 55 
 56         $fragment = new HtmlFragment();
 57         $fragment->startPosition = $index;
 58         $fragment->endPosition = $this->position;
 59         $fragment->content = $this->buffer;
 60         $fragment->isSelfClosing = str($this->buffer)->endsWith('/>');
 61         $fragment->isClosingTag = str($this->buffer)->startsWith('</');
 62 
 63         $documentContentStartOffset = 1;
 64         $documentContentEndOffset = -1;
 65 
 66         if ($fragment->isClosingTag) {
 67             $documentContentStartOffset = 2;
 68         }
 69 
 70         if ($fragment->isSelfClosing) {
 71             $documentContentEndOffset = -2;
 72         }
 73 
 74         $fragment->documentContent =
 75             str($this->buffer)->substr(
 76                 $documentContentStartOffset,
 77                 $documentContentEndOffset
 78             );
 79 
 80         // Retrieve all content before the first space.
 81         $tagName = str($fragment->documentContent)->before(' ');
 82         $fragment->tagName = (string) $tagName->trim();
 83 
 84         // Check if the tag name was an ignored region.
 85         // If so, we can grab that content substring.
 86         if (array_key_exists(
 87             $fragment->startPosition + $documentContentStartOffset
 88             , $this->ignoreRanges
 89         )) {
 90             $tagNameStart =
 91                 $fragment->startPosition + $documentContentStartOffset;
 92 
 93             $tagNameEnd = $this->ignoreRanges[$tagNameStart];
 94             $nameLength = $tagNameEnd - $tagNameStart + 1;
 95             $fragment->tagName = str($this->string)
 96                 ->substr($tagNameStart, $nameLength)->value();
 97         }
 98 
 99         // Create a Fragment representing the name.
100         if (str($fragment->tagName)->trim()->length > 0) {
101             $fragment->name = new Fragment();
102             $fragment->name->content = $fragment->tagName;
103             $fragment->name->startPosition =
104                 $fragment->startPosition + $documentContentStartOffset;
105 
106             $fragment->name->endPosition =
107                 $fragment->name->startPosition +
108                 str($fragment->tagName)->length() - 1;
109         }
110 
111         // Calculate the start of the inner content.
112         // This will be the first space after the tag name.
113         $innerContentStart = mb_strpos($fragment->documentContent,
114             ' ');
115 
116         if ($innerContentStart !== false) {
117             $innerContentFragment = new Fragment();
118             $innerContentFragment->content =
119                 str($fragment->documentContent)
120                     ->substr($innerContentStart)
121                     ->trim();
122 
123             // Calculate the start and end positions of the
124             // inner content relative to the document.
125             $innerContentFragment->startPosition = mb_strpos(
126                     $fragment->documentContent,
127                     $innerContentFragment->content
128                 ) + 1 + $fragment->startPosition;
129 
130             if ($fragment->isClosingTag) {
131                 $innerContentFragment->startPosition += 1;
132             }
133 
134             $innerContentFragment->endPosition =
135                 $innerContentFragment->startPosition +
136                 str($innerContentFragment->content)->length();
137 
138             $fragment->innerContent = $innerContentFragment;
139         }
140 
141         if (!$fragment->isClosingTag && !$fragment->isSelfClosing &&
142             str($fragment->tagName)->lower == 'script'
143         ) {
144             $this->isParsingScript = true;
145         }
146 
147         $this->fragments[] = $fragment;
148     }
149 
150     /**
151      * @return array
152      */
153     private function buildFragmentIndex()
154     {
155         preg_match_all('/</', $this->string,
156             $matches, PREG_OFFSET_CAPTURE);
157 
158         $fragmentStarts = [];
159 
160         foreach ($matches[0] as $match) {
161             $index = $match[1];
162             $isValid = true;
163 
164             foreach ($this->ignoreRanges as $rangeStart => $rangeEnd) {
165                 if ($index >= $rangeStart && $index <= $rangeEnd) {
166                     $isValid = false;
167                     break;
168                 }
169             }
170 
171             if ($isValid) {
172                 $fragmentStarts[] = $index;
173             }
174         }
175 
176         return $fragmentStarts;
177     }
178 
179     public function getFragments()
180     {
181         return $this->fragments;
182     }
183 
184     public function parse($value)
185     {
186         $this->isParsingScript = false;
187         $this->string = new Utf8StringIterator(
188             Str::normalizeEol($value, "\n")
189         );
190 
191         $fragmentStartIndexes = $this->buildFragmentIndex();
192         $fragmentCount = count($fragmentStartIndexes);
193 
194         for ($i = 0; $i < $fragmentCount; $i++) {
195             $this->parseFragment($fragmentStartIndexes[$i]);
196             $this->resetState();
197 
198             if ($this->isParsingScript) {
199                 for ($j = $i + 1; $j < $fragmentCount; $j++) {
200                     $start = $fragmentStartIndexes[$j];
201                     $check = str($this->string)
202                         ->substr($start, 8)
203                         ->lower();
204 
205                     if ($check == '</script') {
206                         $this->isParsingScript = false;
207                         $i = $j - 1;
208                         break;
209                     }
210                 }
211             }
212         }
213 
214         return $this->fragments;
215     }
216 }
```

**Figure 17.31** has many moving parts, but it is primarily the same techniques and methods we have seen in previous chapters. Because of this, we will discuss the more exciting aspects of our implementation. The first aspect we will examine is how our ignore ranges are managed internally. Our `setIgnoreRanges` method, defined between lines 11 and 14, sets our internal list of ranges to ignore. These ranges are utilized within the `buildFragmentIndex`, defined between lines 153 and 177. This method is responsible for using our regular expression to determine the start offset of all potential HTML tags within the source document. We iterate these offsets between lines 160 and 174 to build a new list of all the offsets we should start parsing within our input document. We compare all of the offsets from our regular expression to the list of ranges we should ignore between lines 164 and 169. If the start offset captured by our regular expression is contained within one of the ranges to ignore, we do not add it to our final list of fragment start locations.

The final list of fragment start locations is used within our parse method, which is defined between lines 184 and 215. The first few lines of our method work to manage some internal state and set our internal `Utf8StringIterator` instance. Our internal string iterator contains the normalized contents of our string iterator. Normalizing the newlines within our document is important, as it will dramatically simplify managing the relative offsets as we parse our input string.

We iterate the list of potential HTML fragment starting offsets between lines 194 and 212. Within this loop, we call our `parseFragment` method, which will add a new `HtmlFragment` instance to the internal list of fragments if it can successfully parse an HTML element.

Our `parseFragment` method will contain some logic to check if the HTML element it just produced is a `<script>` tag. If so, it will set the internal `isParsingScript` flag. If this flag has been set to true, our `parse` method will scan forward through the potential start locations and retrieve a substring at that location. If the substring returned matches “</script,” we will use this as the script tag’s ending location and set our loop’s current position to this location. This logic occurs between lines 198 and 211.

Our next point of interest is the `parseFragment` method, defined between lines 16 and 148. This method is one of the more notable examples we have encountered thus far in this book. Most of our method’s implementation, however, is only working to fill in the details of our parsed HTML element, such as whether or not it is a closing tag, self-closing, etc. The actual parsing takes place between lines 21 and 49.

We see the second place our list of ranges to ignore comes into use between lines 22 and 29. If the current position of our parser aligns with one of these ranges, we fill our internal buffer with spaces to match the length of the range we will skip over. We add these empty spaces to our buffer at this point to make parsing HTML attributes and parameters simpler at a later stage. An example of why we may want to do this can be found in **Figure 17.32**, where we have an embedded Antlers tag that contains parameters that could easily be confused for regular HTML parameters:

Figure 17.32 

```
1 <div {{ increment by="1" }}>
2     Content
3 </div>
```

Once we are sure we are not inside one of our ranges that should not be parsed, we can look to see if we have encountered an invalid character sequence. This happens between lines 32 and 36. Here, we check if we have encountered an instance of the less than character outside a string. The other scenario we check for is to see if we have reached the end of the input document. You will notice that on line 32, we also have a check to ensure that the counting variable of our loop does not match the index we supplied when we called our `parseFragment` method. Our `parseFragment` method will always begin at the location of the first less-than character, and we need to ensure we’ve moved over it to prevent exiting too our loop too early. When we encounter an invalid sequence, we set the `$brokeEarly` flag and use it to exit the `parseFragment` method early between lines 51 and 54.

Between lines 38 and 41, we check if our parser is at a location that would indicate the start of a string. If so, we call the `scanToEndOfString` method, which adds the contents of the string to our internal buffer and updates the loop’s current position. This will helpfully move our fragment parser over the contents of the string, which may contain characters that would confuse our parser implementation.

Between lines 43 and 46, we check if the current character the parser is on is the greater-than character. At this point, we know we are not in a range that should be skipped and are not within a string. At this point, we can add the greater-than character to our internal buffer and exit our loop, as we have found the end of our current HTML fragment.

The remainder of our `parseFragment` method simply analyzes the parsed content to set some properties on the new `HtmlFragment` instance. For instance, on line 60, we can check whether or not an HTML is self-closing or not by whether it ends with the “/>” character sequence. Similarly, we can determine if an HTML element is self-closing by checking if its content begins with the “</” character sequence. The more nuanced implementation details are related to how we determine the final name for our parsed HTML element.

On lines 81 and 82, we extract all of the tag’s content before the first space. For most tags, this technique works just fine. However, if our HTML tag name is being dynamically constructed, the first position within the tag’s content will align with one of the ranges we previously skipped. When this happens, we locate the original text skipped over from the source document and use it as the tag’s final name. To help illustrate this process of determining tag names, let us analyze the results of calling our fragment’s parser like so:

Figure 17.33 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 <{{ $dynamic }} />
 5 <div />
 6 BLADE;
 7 
 8 preg_match_all('/{{.*?}}/i', $blade, $echos, PREG_OFFSET_CAPTURE);
 9 
10 $ignore = [];
11 
12 foreach ($echos[0] as $match) {
13     $start = $match[1];
14     $end   = $start + str($match[0])->length() - 1;
15     $ignore[$start] = $end;
16 }
17 
18 $fragmentsParser = new FragmentsDocumentParser();
19 $fragmentsParser->setIgnoreRanges($ignore);
20 $fragments = $fragmentsParser->parse($blade);
```

**Figure 17.33** would produce the following list of `HtmlFragment` instances:

Figure 17.34 

```
 1 array:2 [
 2   0 => HtmlFragment {
 3     startPosition: 0
 4     endPosition: 17
 5     content: "<               />"
 6     isClosingTag: false
 7     isSelfClosing: true
 8     documentContent: "               "
 9     innerContent: Fragment {
10       startPosition: 1
11       endPosition: 1
12       content: ""
13     }
14     name: Fragment {
15       startPosition: 1
16       endPosition: 14
17       content: "{{ $dynamic }}"
18     }
19     tagName: "{{ $dynamic }}"
20     attributes: []
21   }
22   1 => HtmlFragment {
23     startPosition: 19
24     endPosition: 25
25     content: "<div />"
26     isClosingTag: false
27     isSelfClosing: true
28     documentContent: "div "
29     innerContent: Fragment {
30       startPosition: 20
31       endPosition: 20
32       content: ""
33     }
34     name: Fragment {
35       startPosition: 20
36       endPosition: 22
37       content: "div"
38     }
39     tagName: "div"
40     attributes: []
41   }
42 ]
```

In **Figure 17.34**, we can see that our fragments parser has returned two HTML elements. The second fragment in the list corresponds to the “div” tag from **Figure 17.33**. The first element in the list is more interesting, however. If we look at the `tagName` value for the first fragment returned, we can see that it has been set to `{{ $dynamic }}`, extracted from the original source document. This happened because the first position of that element’s content aligned with a range we skipped earlier in the parsing process. Having the names of dynamic HTML resolved for us helps simplify decision-making when using the results in other processes, such as static analyzers or code formatting solutions.

### 17.4 Parsing HTML Attributes and Parameters

Parsing the parameters and attributes of our fragments will be similar to extracting the HTML fragments themselves. Instead of checking for characters such as the greater-than and less-than characters, we will use the presence of whitespace to determine attribute and parameter boundaries. Because parameter values may contain valid whitespace, we will use the same technique to skip over strings when parsing parameters to advance our parser over those problematic areas. Our implementation of this can be found in **Figure 17.35**:

Figure 17.35 FragmentAttributeParser Implementation 

```
 1 <?php
 2 
 3 class FragmentAttributeParser extends BaseFragmentParser
 4 {
 5     public function parse($fragment)
 6     {
 7         $this->resetState();
 8         $this->string = new Utf8StringIterator(
 9             $fragment->innerContent->content
10         );
11 
12         $tempAttributes = [];
13         $attributes = [];
14 
15         for ($i = 0; $i < count($this->string); $i++) {
16             $this->checkCurrentOffsets($i);
17 
18             if (ctype_space($this->current)) {
19                 $this->buffer = '';
20                 continue;
21             }
22 
23             if ($this->isStartOfString()) {
24                 $i = $this->scanToEndOfString($i);
25                 $this->checkCurrentOffsets($i);
26             } else {
27                 $this->buffer .= $this->current;
28             }
29 
30             if ($this->next == null || ctype_space($this->next)) {
31                 $tempAttributes[] = [
32                     $this->buffer, $i
33                 ];
34 
35                 $this->buffer = '';
36                 continue;
37             }
38         }
39 
40         foreach ($tempAttributes as $tempAttribute) {
41             $attribute = new FragmentAttribute();
42 
43             $attribute->content = $tempAttribute[0];
44 
45             // Calculate the attribute's start and end
46             // positions relative to the original doc.
47             $attribute->endPosition = $tempAttribute[1] +
48                 $fragment->innerContent->startPosition;
49             $attribute->startPosition = $attribute->endPosition -
50                 str($attribute->content)->length() + 1;
51 
52             // Extract name/values, if present.
53             $parts = str($attribute->content)->explode('=', 2);
54 
55             if ($parts->count() == 2) {
56                 $attribute->type = AttributeType::Parameter;
57                 $attribute->name = $parts->first();
58                 $attribute->value = $parts->last();
59             } else {
60                 $attribute->name = $attribute->content;
61                 $attribute->type = AttributeType::Attribute;
62             }
63 
64             $attributes[] = $attribute;
65         }
66 
67         return $attributes;
68     }
69 }
```

Like our fragments parser, much of what is happening in **Figure 17.35** is similar to what we’ve seen before. The more table differences are that between lines 18 and 21 if the current character is whitespace, we clear the contents of our internal buffer and move to the next position within the string. This will ensure that our parsed attributes and parameters do not have extraneous whitespace on either side and provide a simple way to determine boundaries. Between lines 30 and 36 is where we create a list of temporary attributes.

Our list of temporary attributes contains the buffer’s content at that time and the position within with HTML fragment attribute or parameter *ended*. The remainder of our attribute parser iterates over these temporary attributes to produce the final list.

Between lines 40 and 65, we iterate the list of temporary attributes. The first thing we do is set the attribute’s content on line 43. From here, we need to calculate the end and starting position of the attribute relative to the original document.

Because our attribute parser creates a new `Utf8StringIterator` instance from the fragment’s inner content, all of our temporary attribute offsets will start over at zero and be relative to that inner-content string. This means we will have lost its relative position within the original document. To account for this, we can add the starting position the fragment’s inner content started at to our end position to arrive at the location the parsed attribute or parameter would appear within the larger source document. This happens between lines 47 and 48. To determine the starting position, we can take the length of the temporary attribute’s content and subtract it from the ending position; this will give us the position within the document immediately preceding our attribute or parameter. To account for our position being immediately before our target position, we can add one; this happens between lines 49 and 50.

To tell the difference between HTML parameters and attributes, we split our string using the explode helper method on line 53, using the “=” character as the delimiter. If the resulting `$parts` array contains two elements, we assume that the value we parsed is an HTML parameter instead of an attribute.

We can update our `FragmentsDocumentParser` to utilize our `FragmentAttributeParser` to parse the fragments and attributes of each HTML fragment:

Figure 17.36 

```
 1 <?php
 2 
 3 class FragmentsDocumentParser extends BaseFragmentParser
 4 {
 5     protected $attributeParser;
 6 
 7     public function __construct()
 8     {
 9         $this->attributeParser = new FragmentAttributeParser();
10     }
11 
12     private function parseAttributes($fragment)
13     {
14         if ($fragment->innerContent == null ||
15             str($fragment->innerContent->content)->length() == 0) {
16             return;
17         }
18 
19         $fragment->attributes = $this->attributeParser
20             ->parse($fragment);
21     }
22 
23     private function parseFragment($index)
24     {
25         // ...
26 
27         $this->parseAttributes($fragment);
28 
29         if (!$fragment->isClosingTag && !$fragment->isSelfClosing &&
30             str($fragment->tagName)->lower == 'script'
31         ) {
32             $this->isParsingScript = true;
33         }
34 
35         $this->fragments[] = $fragment;
36     }
37 }
```

The changes in **Figure 17.36** are relatively small. We have an internal instance of our `FragmentAttributeParser`, which we use in a new `parseAttributes` method. This method will receive an instance of `HtmlFragment` and check if it contains any inner content. If our fragment does contain inner content, we then use our attribute’s parser to extract all the information we can from the fragment. Using our updated parser on the following input:

Figure 17.37 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 <{{ $dynamic }} parameter="value" readonly />
 5 BLADE;
 6 
 7 preg_match_all('/{{.*?}}/i', $blade, $echos, PREG_OFFSET_CAPTURE);
 8 
 9 $ignore = [];
10 
11 foreach ($echos[0] as $match) {
12     $start = $match[1];
13     $end   = $start + str($match[0])->length() - 1;
14     $ignore[$start] = $end;
15 }
16 
17 $fragmentsParser = new FragmentsDocumentParser();
18 $fragmentsParser->setIgnoreRanges($ignore);
19 
20 $fragments = $fragmentsParser->parse($blade);
```

Would now produce the following list of HTML fragments:

Figure 17.38 

```
 1 array:1 [
 2   0 => HtmlFragment {
 3     startPosition: 0
 4     endPosition: 44
 5     content: "<               parameter="value" readonly />"
 6     isClosingTag: false
 7     isSelfClosing: true
 8     documentContent: "               parameter="value" readonly "
 9     innerContent: Fragment {
10       startPosition: 16
11       endPosition: 42
12       content: "parameter="value" readonly"
13     }
14     name: Fragment {
15       startPosition: 1
16       endPosition: 14
17       content: "{{ $dynamic }}"
18     }
19     tagName: "{{ $dynamic }}"
20     attributes: array:2 [
21       0 => FragmentAttribute {
22         startPosition: 16
23         endPosition: 32
24         content: "parameter="value""
25         name: "parameter"
26         value: ""value""
27         type: AttributeType {
28           name: "Parameter"
29         }
30       }
31       1 => FragmentAttribute {
32         startPosition: 34
33         endPosition: 41
34         content: "readonly"
35         name: "readonly"
36         value: ""
37         type: AttributeType {
38           name: "Attribute"
39         }
40       }
41     ]
42   }
43 ]
```

Our parser now returns a list of HTML fragments and their associated parameters and attributes. We can now use this information to develop a system for analyzing our input document.

### 17.5 Analyzing Fragmented HTML Documents

In **Figure 17.38**, we can see our fragments parser provides an immense amount of information about our source document. Importantly, our results have avoided potentially problematic areas of our input document by skipping over the results of other parsers. We can bring all this information together to begin asking interesting questions about *where* those skipped regions appear in our document.

For instance, if we wanted to write a code formatter that formatted our embedded languages and our HTML structure, we may want to know whether or not our embedded languages appear within an HTML parameter or as part of a dynamic HTML tag name. **Figure 17.39** contains the analyzer implementation that will be able to resolve the context for arbitrary positions within a source document:

Figure 17.39 FragmentsPositionAnalyzer Implementation 

```
 1 <?php
 2 
 3 enum FragmentPosition
 4 {
 5     case InsideFragment;
 6     case InsideAttribute;
 7     case InsideParameter;
 8     case InsideFragmentName;
 9     case StartOfFragment;
10     case EndOfFragment;
11     case Unknown;
12 }
13 
14 class FragmentsPositionAnalyzer
15 {
16     /**
17      * The fragments to be analyzed.
18      *
19      * @var HtmlFragment[]
20      */
21     protected $fragments = [];
22 
23     /**
24      * Sets the HTML fragments to be analyzed.
25      *
26      * @param HtmlFragment[] $fragments
27      * @return void
28      */
29     public function setFragments($fragments)
30     {
31         $this->fragments = $fragments;
32     }
33 
34     /**
35      * Retrieves the contextual location for the provided position.
36      *
37      * @param int $position
38      * @return FragmentPosition
39      */
40     public function getContext($position)
41     {
42         $loc = FragmentPosition::Unknown;
43 
44         foreach ($this->fragments as $fragment) {
45             if ($fragment->contains($position)) {
46                 $loc = FragmentPosition::InsideFragment;
47 
48                 // Check if the position is within the
49                 // characters making up the tag start.
50                 if ($position == $fragment->startPosition ||
51                     ($fragment->isClosingTag &&
52                         $position == $fragment->startPosition + 1)) {
53                     $loc = FragmentPosition::StartOfFragment;
54                     break;
55                 }
56 
57                 // Check if the position is within the
58                 // characters making up the tag end.
59                 if ($position == $fragment->endPosition ||
60                     ($fragment->isSelfClosing &&
61                         $position == $fragment->endPosition - 1)) {
62                     $loc = FragmentPosition::EndOfFragment;
63                     break;
64                 }
65 
66                 // Check if the position is within the tag name.
67                 if ($fragment->name != null &&
68                     $fragment->name->contains($position)) {
69                     $loc = FragmentPosition::InsideFragmentName;
70                     break;
71                 }
72 
73                 // Check if the position is inside an attribute.
74                 foreach ($fragment->attributes as $attr) {
75                     if ($attr->contains($position)) {
76                         $loc = FragmentPosition::InsideAttribute;
77 
78                         if ($attr->type == AttributeType::Parameter) {
79                             $loc = FragmentPosition::InsideParameter;
80                         }
81 
82                         break;
83                     }
84                 }
85 
86                 break;
87             }
88         }
89 
90         return $loc;
91     }
92 }
```

Between lines 3 and 12, we have defined an enumeration that contains all of the possible contextual locations our analyzer will be able to resolve. Each of these locations tells us something about where the feature appears within the original document:

*   **Inside Fragment**: This context corresponds to a position within an HTML fragment that is not the element’s name, nor does the location exist within a parameter or attribute.
*   **Inside Attribute**: The requested location appears within a fragment attribute.
*   **Inside Parameter**: This is similar to the `InsideAttribute` value but indicates the location that appears within an HTML parameter.
*   **Inside Fragment Name**: The requested location appears within the fragment’s name.
*   **Start of Fragment**: The requested location corresponds to the “<” character of the associated element or the “</” sequence for closing tags.
*   **End of Fragment**: The requested corresponds to the “>” character of the associated element or the “/>” sequence for self-closing tags.
*   **Unknown**: The requested location could not be located within any fragment, attribute, or parameter. This result helps determine if the requested location appears between HTML fragments.

Our implementation extensively uses the `contains` method defined on the base Fragment class. We iterate each of the fragments returned from our fragments parser. Once we have located a fragment that contains the requested position, we check to see if the position is contained within the fragment’s name. Suppose the location is not contained within the fragment’s name. In that case, we then iterate each fragment’s attributes, looking for one that contains the location we are interested in and adjusting our return value along the way.

We can now combine the parser and analyzer together to get a feel for how they interact:

Figure 17.40 

```
 1 <?php
 2 
 3 $blade = <<<'BLADE'
 4 <{{ $dynamic }} parameter="value" readonly>
 5     Content
 6 </{{ $dynamic }}>
 7 BLADE;
 8 
 9 preg_match_all('/{{.*?}}/i', $blade, $echos, PREG_OFFSET_CAPTURE);
10 
11 $ignore = [];
12 
13 foreach ($echos[0] as $match) {
14     $start = $match[1];
15     $end   = $start + str($match[0])->length() - 1;
16     $ignore[$start] = $end;
17 }
18 
19 $fragmentsParser = new FragmentsDocumentParser();
20 $fragmentsParser->setIgnoreRanges($ignore);
21 $fragments = $fragmentsParser->parse($blade);
22 
23 $analyzer = new FragmentsPositionAnalyzer();
24 $analyzer->setFragments($fragments);
25 
26 // Returns "StartOfFragment"
27 $analyzer->getContext(0);
28 
29 // Returns "InsideFragmentName"
30 $analyzer->getContext(2);
31 
32 // Returns "InsideParameter"
33 $analyzer->getContext(19);
34 
35 // Returns "InsideAttribute"
36 $analyzer->getContext(38);
37 
38 // Returns "Unknown"
39 $analyzer->getContext(50);
40 
41 // Returns "EndOfFragment"
42 $analyzer->getContext(72);
```

## 18\. Regular Expressions

Regular expressions are one of those topics that often feel obscure, intimidating, or too difficult to grasp; most of these descriptions can largely be attributed to the difficulty in reading non-trivial regular expressions. However, despite this, they are a straightforward yet powerful way to express search patterns that can be applied to text. Throughout this book, we have used several regular expressions to help us achieve our goals in one way or another. For example, we have used regular expressions often to quickly scan text input to locate all instances of a particular pattern and to remove substrings, amongst other things. However, we have not taken time to step back and explore regular expressions themselves.

To begin our discussion around regular expressions, let us consider the example in **Figure 18.1**:

Figure 18.1 

```
1 <?php
2 
3 $url = 'blog/2022-10-12/title';
4 
5 if (preg_match('/^blog\/.*\z/u', $url) === 1) {
6     // The URL starts with "blog/"
7 } else {
8     // The URL does not start with "blog/"
9 }
```

In **Figure 18.1**, we are using a simple regular expression to determine if the input string begins with “blog/.” The amount of boilerplate code we have used to perform this comparison can be reduced by using one of Laravel’s string helper methods: the `is` helper method.

Figure 18.2 is Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions Laravel 8, 9
 5  *
 6  * @return bool
 7  */
 8 public static function is(
 9     string|array $pattern,
10     string       $value
11 );
```

We can rewrite our sample from **Figure 18.1** using the `is` helper method like so:

Figure 18.3 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 if (Str::is('blog/*', $url)) {
6     // The URL starts with "blog/"
7 } else {
8     // The URL does not start with "blog/"
9 }
```

When we compare the logic between **Figure 18.1** and **Figure 18.3**, it is much easier to quickly scan **Figure 18.3** and understand the intention behind the condition. An important thing to note, however, is that Laravel’s `is` helper method will replace all instances of the asterisk character with the “.*” character sequence. If this behavior is inappropriate for your particular use case, you will need to revert to using PHP’s `preg_match` function directly.

An interesting thing to note from the `is` method’s signature is that the argument for the search pattern can be an array. We can use this to our advantage to check if a string matches multiple wildcard patterns like so:

Figure 18.4 

```
1 <?php
2 
3 use Illuminate\Support\Str;
4 
5 $url = 'article/2022-10-12/title';
6 
7 if (Str::is(['blog/*', 'article/2022-10-*/*'], $url)) {
8     // The URL matches one of the provided patterns.
9 }
```

The other two most commonly used Laravel helper methods related to regular expressions are the match and `matchAll` methods. The match method is equivalent to PHP’s `preg_match` function, and `matchAll` is a wrapper around PHP’s `preg_match_all` function. Neither helper method allows customization of the flags used by the underlying regular expression engine.

Figure 18.5 match Method Signature 

```
 1 <?php
 2 
 3 /**
 4  * Versions: Laravel 8, 9
 5  *
 6  * @return string
 7  */
 8 public static function match(
 9     string $pattern,
10     string $subject
11 );
```

As an example of the match method, we can use it to test if a string is composed of a certain number of digits. For example, **Figure 18.6** ensures that the input string contains exactly three digits:

Figure 18.6 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 // This would evaluate to true.
 6 if (Str::match('/^\d{3}$/', '333')) {
 7 
 8 }
 9 
10 // This would not evaluate to true.
11 if (Str::match('/^\d{3}$/', 'A333')) {
12     
13 }
```

The `matchAll` method is similar but can be used to return a Collection instance containing all matches. Unlike PHP’s `preg_match_all` function, we cannot specify any flags:

Figure 18.7 matchAll Method Signature 

```
 1 <?php
 2 
 3 use Illuminate\Support\Collection;
 4 
 5 /**
 6  * Versions: Laravel 8, 9
 7  *
 8  * @return Collection
 9  */
10 public static function matchAll(
11     string $pattern,
12     string $subject
13 );
```

As an example of the `matchAll` method, we can use it to retrieve all text that appears between a pair of double curly brackets within a document:

Figure 18.8 

```
 1 <?php
 2 
 3 use Illuminate\Support\Str;
 4 
 5 $text = <<<'TEXT'
 6 Hello, {{ $name }}
 7 
 8 Thank you for purchasing {{ $productName }}!
 9 TEXT;
10 
11 $matches = Str::matchAll('/{{.*}}/', $text);
```

After the code in **Figure 18.8** has been executed, we will receive a Collection instance containing the following items:

Figure 18.9 

```
1 array:2 [
2   0 => "{{ $name }}"
3   1 => "{{ $productName }}"
4 ]
```

### 18.1 Regular Expression Syntax Primer

One of the main criticisms of regular expressions is that they are difficult to understand, mainly due to the syntax’s information density. Throughout the remainder of this chapter, we will look at some of the various features provided by PHP’s regular expression engine and how we would express that using its syntax.

The first concept we will look at together is the pattern delimiter. When writing regular expressions in PHP, we must always start and end our patterns with a delimiter. A delimiter can be any non-alphanumeric character except for a backslash and whitespace. The most common delimiter we will encounter is the forward slash. In **Figure 18.10**, we can see a pattern that uses the forward slash as its delimiter.

Figure 18.10 

```
 1 <?php
 2 
 3 
 4 $text = 'Hello, world. Hello, there! Howdy, there!';
 5 
 6 
 7 // Returns ["Hello, world", "Hello, there"]
 8 str($text)->matchAll(
 9     '/Hello, [A-z]*\b/'
10 )->all();
```

If we want to use our delimiter character within the pattern itself, we need to escape it by using the backslash character:

Figure 18.11 

```
1 <?php
2 
3 $text = '/mnt/c/Windows/System32';
4 
5 // Returns ["Windows/System32"]
6 str($text)->matchAll(
7     '/mnt\/c\/([A-z0-9\/]*)/'
8 )->all();
```

If the delimiter character appears multiple times within the pattern, it is recommended to choose a different delimiter character to reduce the number of backslashes that appear to increase readability:

Figure 18.12 

```
1 <?php
2 
3 $text = '/mnt/c/Windows/System32';
4 
5 // Returns ["Windows/System32"]
6 str($text)->matchAll(
7     '#mnt/c/([A-z0-9/]*)#'
8 )->all();
```

#### Meta-Characters

Meta-characters have special meaning when defining our regular expression patterns. For example, we can use meta-characters to match word boundaries or to create character classes. **Table 18.1** contains the supported meta-characters:

Table 18.1 Regular Expression Meta-Characters

 
| Characters || Description ||   |
| --- | --- | --- |
| \\ || Escape Character ||   |
| --- | --- | --- |
| ^ || Matches the start of the input text (or line, when in multi-line mode) ||   |
| $ || Matches the end of the input text (or line, when in multi-line mode) ||   |
| . || Matches any character, except for the newline character. ||   |
| \[ \] || Defines a character class. ||   |
|   ||   || Start of an alternative branch. |
| ( ) || Defines a sub-pattern. ||   |
| ? || 0 or 1 quantifier; makes greedy quantifiers lazy ||   |
| \* || 0 or more quantifier. ||   |
| + || 1 or more quantifier. ||   |
| { } || Defines a quantity range. ||   |

**Table 18.2** contains the available meta-characters when inside a character class (square brackets):

Table 18.2 Character Class Meta-Characters

 
| Character || Description |
| --- | --- |
| \\ || General Escape Character |
| --- | --- |
| ^ || Negates the character class when it appears as the first character within the class. |
| \- || Indicates a range of characters. |

#### Anchors

Anchors are a particular type of meta-character that allows us to specify *where* in an input document matches may start or end. The most common anchors we have encountered in this book are the `^` and `$` anchors. The `^` anchor matches the start of the input text, and `$` anchors the match to the end of the input text.

These two anchors’ behavior depends on whether the regular expression has multi-line mode enabled. As an example, let us take a look at **Figure 18.13**, which uses these anchors to assert that our match starts at the beginning of the document and ends at the end of the input text:

Figure 18.13 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 one
 5 two
 6 TEXT;
 7 
 8 $pattern = '/^[a-z\s]*?$/';
 9 
10 preg_match_all($pattern, $text, $matches, PREG_OFFSET_CAPTURE);
```

After the code in **Figure 18.13** has executed, we would receive an array containing the following matches:

Figure 18.14 

```
 1 array:1 [
 2   0 => array:1 [
 3     0 => array:2 [
 4       0 => """
 5         one\n
 6         two
 7         """
 8       1 => 0
 9     ]
10   ]
11 ]
```

We can see in the example output in **Figure 18.14** that our pattern has matched the entirety of the input text. However, if we were to update our regular expression to use multi-line mode:

Figure 18.15 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 one
 5 two
 6 TEXT;
 7 
 8 $pattern = '/^[a-z\s]*?$/m';
 9 
10 preg_match_all($pattern, $text, $matches, PREG_OFFSET_CAPTURE);
```

Our pattern would now match the content of each line instead:

Figure 18.16 

```
 1 array:1 [
 2   0 => array:2 [
 3     0 => array:2 [
 4       0 => "one"
 5       1 => 0
 6     ]
 7     1 => array:2 [
 8       0 => "two"
 9       1 => 4
10     ]
11   ]
12 ]
```

When in multi-line mode, it may be desirable to match the start and end of the input text rather than the individual lines. This can be accomplished using the `\A` and `\z` escape sequences:

Figure 18.17 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 one
 5 two
 6 TEXT;
 7 
 8 $pattern = '/\A[a-z\s]*?\z/m';
 9 
10 preg_match_all($pattern, $text, $matches, PREG_OFFSET_CAPTURE)
```

Our updated regular expression in **Figure 18.17** would now produce the same output as the pattern in **Figure 18.13**, regardless of whether multi-line mode has been enabled.

#### Escape Sequences

Similar to how PHP strings support escape sequences, we may use different escape sequences within our regular expression patterns. We have seen a few escape sequence examples, such as those to assert a match is located at the start or end of an input document. **Table 18.3** lists the most commonly used escape sequences:

Table 18.3 Common Regular Expression Escape Sequences

 
| Sequence || Description |
| --- | --- |
| \\n || Matches the newline character. |
| --- | --- |
| \\r || Matches the carriage return character. |
| R || Matches line breaks (\\n, \\r, and \\r\\n). |
| \\t || Matches the tab character. |
| \\d || Matches any decimal digit. |
| D || Matches any character that is not a decimal digit. |
| \\s || Matches any whitespace character. |
| S || Matches any non-whitespace character. |
| \\w || Matches any “word” character (locale dependent). |
| W || Matches any “non-word” character (locale dependent). |
| \\b || Matches a word boundary. |
| B || Asserts the character is not a word boundary. |
| A || Anchors the match to the start of the input, regardless of multi-line mode. |
| Z || Anchors the match to the end of the input or final newline, regardless of multi-line mode. |
| \\z || Anchors the match to the end of the input document, regardless of multi-line mode. |

#### Character Classes

A character class allows us to specify which characters are acceptable for any given position. For example, if we had the pattern:

Figure 18.18 

```
1 /abc/
```

We can interpret it as a literal “a” followed by a literal “b” followed by a literal “c.” Suppose we wanted to match all substrings that contained those three characters in any order. We can achieve this using a character class. We define character classes by specifying what characters are allowed between square brackets:

Figure 18.19 

```
1 <?php
2 
3 $text = 'aaa abc acc cba';
4 
5 // Returns ["aaa", "abc", "acc", "cba"]
6 str($text)->matchAll(
7     '/[abc][abc][abc]/'
8 )->all();
```

We can also use negation to specify that we do *not* want characters to appear at a specific location. We do this by starting our class with the “^” character:

Figure 18.20 

```
1 <?php
2 
3 $text = 'aaa abc def cba';
4 
5 // Returns ["aaa"]
6 str($text)->matchAll(
7     '/[abc][^be][abc]/'
8 )->all();
```

In **Figure 18.20**, our regular expression can be interpreted as:

*   The character “a,” “b,” or “c” followed by
*   Any character that is *not* “b” or “e,” followed by
*   The character “a,” “b,” or “c.”.

If we wanted to include the “^” character itself in our character class, we need to add it to the *end* of the character class, so it is not interpreted as the negation operator:

Figure 18.21 

```
1 <?php
2 
3 $text = 'aaa abc a^b cba';
4 
5 // Returns ["a^b"]
6 str($text)->matchAll(
7     '/[abc][z^][abc]/'
8 )->all();
```

We can also specify ranges of characters when defining our character classes. This helps to avoid having to write every possible combination of characters. For example, we could rewrite our previous patterns using ranges like so:

Figure 18.22 

```
1 <?php
2 
3 $text = 'aaa abc acc cba';
4 
5 // Returns ["aaa", "abc", "acc", "cba"]
6 str($text)->matchAll(
7     '/[a-c][a-c][a-c]/'
8 )->all();
```

When defining alpha character ranges, the case of the character used within the range is important. For instance, our pattern in **Figure 18.23** would not result in any matches since it expects the final character to be uppercased:

Figure 18.23 

```
1 <?php
2 
3 $text = 'aaa abc acc cba';
4 
5 // Returns no matches.
6 str($text)->matchAll(
7     '/[a-c][a-c][A-C]/'
8 )->all();
```

Similar to using the negation operator within a character class, if we want to use the “-“ character as part of the list of acceptable characters, we need to specify it as the last character within the class:

Figure 18.24 

```
1 <?php
2 
3 $text = 'aaa abc a-c cba';
4 
5 // Returns ["aaa", "abc", "a-c", "cba"]
6 str($text)->matchAll(
7     '/[a-c][a-c-][a-c]/'
8 )->all();
```

#### Sub-Patterns, Capture Groups, and Non-Capturing Groups

Regular expression groups allow us to define sub-patterns, define multiple matching options, and “capture” different parts of a matched substring on its own. For example, the regular expression in **Figure 18.25** uses two groups to match the titles “Mr.” and “Mrs.” followed by a name:

Figure 18.25 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 Mr. Darcy
 5 Mrs. Bennet
 6 TEXT;
 7 
 8 $pattern = '/Mr(s)?\. ([A-z]*)\b/';
 9 
10 preg_match_all($pattern, $text, $matches);
```

And produces the following list of matches:

Figure 18.26 

```
 1 array:3 [
 2   0 => array:2 [
 3     0 => "Mr. Darcy"
 4     1 => "Mrs. Bennet"
 5   ]
 6   1 => array:2 [
 7     0 => ""
 8     1 => "s"
 9   ]
10   2 => array:2 [
11     0 => "Darcy"
12     1 => "Bennet"
13   ]
14 ]
```

Our results in **Figure 18.26** contain an array with three nested arrays. The first nested array contains the full text of each match, the second one contains the matching text of our optional “s” following “Mr,” and the final one includes the person’s name.

Our second array containing the following items is particularly interesting, however:

Figure 18.27 

```
1 1 => array:2 [
2   0 => ""
3   1 => "s"
4 ]
```

We can see that the first item contains an empty string, which corresponds to the “Mr.” title, and the second element is the letter “s,” which corresponds to “Mrs.”. Suppose we did want to include these two items in our results. We can do this by converting our group to a *non-capturing* group by starting the group with the `?:` sequence:

Figure 18.28 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 Mr. Darcy
 5 Mrs. Bennet
 6 TEXT;
 7 
 8 $pattern = '/Mr(?:s)*\. ([A-z]*)\b/';
 9 
10 preg_match_all($pattern, $text, $matches);
```

Our regular expression in **Figure 18.28** would now return the following results:

Figure 18.29 

```
 1 array:2 [
 2   0 => array:2 [
 3     0 => "Mr. Darcy"
 4     1 => "Mrs. Bennet"
 5   ]
 6   1 => array:2 [
 7     0 => "Darcy"
 8     1 => "Bennet"
 9   ]
10 ]
```

We can also use groups to effectively perform an “OR” match when defining our patterns. We can rewrite our regular expression like so to explicitly allow either “Mr” or “Mrs”:

Figure 18.30 

```
 1 <?php
 2 
 3 $text = <<<'TEXT'
 4 Mr. Darcy
 5 Mrs. Bennet
 6 TEXT;
 7 
 8 $pattern = '/(?:Mr|Mrs)\. ([A-z]*)\b/';
 9 
10 preg_match_all($pattern, $text, $matches);
```

#### Repeating Characters and Patterns

We can specify that characters, or entire sub-patterns, can be repeated zero or more times using quantifiers and ranges. By far, the most common is the `*` quantifier, which specifies that a character can be repeated zero or more times. We often see this combined with the `.` meta-character, which matches any character (except for newlines). We can combine these to match all text between sets of curly braces:

Figure 18.31 

```
1 <?php
2 
3 $text = <<<'TEXT'
4 {{ $one }} {{ $two }} {{ $three }}
5 TEXT;
6 
7 $pattern = '/{{.*}}/';
8 
9 preg_match_all($pattern, $text, $matches, PREG_OFFSET_CAPTURE);
```

Once executed, **Figure 18.31** would return the following matches:

Figure 18.32 

```
1 array:1 [
2   0 => array:1 [
3     0 => array:2 [
4       0 => "{{ $one }} {{ $two }} {{ $three }}"
5       1 => 0
6     ]
7   ]
8 ]
```

We can see in the output of **Figure 18.32** that our pattern is “lazy” and will continue matching until the very last set of closing curly braces. We can make our regular expression “greedy” and have it stop as soon as possible by adding the `?` quantifier to our pattern like so:

Figure 18.33 

```
1 <?php
2 
3 $text = <<<'TEXT'
4 {{ $one }} {{ $two }} {{ $three }}
5 TEXT;
6 
7 $pattern = '/{{.*?}}/';
8 
9 preg_match_all($pattern, $text, $matches, PREG_OFFSET_CAPTURE);
```

With our changes, **Figure 18.33** now returns the following matches:

Figure 18.34 

```
 1 array:1 [
 2   0 => array:3 [
 3     0 => array:2 [
 4       0 => "{{ $one }}"
 5       1 => 0
 6     ]
 7     1 => array:2 [
 8       0 => "{{ $two }}"
 9       1 => 11
10     ]
11     2 => array:2 [
12       0 => "{{ $three }}"
13       1 => 22
14     ]
15   ]
16 ]
```

The `+` quantifier can be used to match a character or pattern one or more times. For example, in **Figure 18.35**, we can test if the string contains at least one digit character:

Figure 18.35 

```
 1 <?php
 2 
 3 // Returns 1
 4 preg_match('/\d+/', '123');
 5 
 6 // Returns 1
 7 preg_match('/\d+/', 'abc123');
 8 
 9 // Returns 0
10 preg_match('/\d+/', 'abc');
```

We can combine our patterns with the anchors we saw previously to ensure that the string contains only one or more digit characters:

Figure 18.36 

```
1 <?php
2 
3 // Returns 1
4 preg_match('/^\d+$/', '123');
5 
6 // Returns 0
7 preg_match('/^\d+$/', 'abc123');
```

We can specify that a character or pattern can be repeated a specific number of times or between a minimum and maximum range by defining our range in a set of curly braces. **Figure 18.37** defines a pattern that matches between three and five digit characters:

Figure 18.37 

```
1 <?php
2 
3 // Returns 1
4 preg_match('/^\d{3,5}$/', '123');
5 
6 // Returns 0
7 preg_match('/^\d{3,5}$/', '123456');
```

Additionally, we can specify a fixed number of times the character or pattern can be repeated by eliminating the second value within our curly braces. **Figure 18.38** defines a pattern that will only match strings containing exactly three digits:

Figure 18.38 

```
1 <?php
2 
3 // Returns 1
4 preg_match('/^\d{3}$/', '123'); //?
5 
6 // Returns 0
7 preg_match('/^\d{3}$/', '1234'); //?
```

#### Ensuring Matches Do Not Start or End with a Specific Pattern

In Chapter 16, we developed a Blade directive validation system. To help find our Blade directives, we used the following regular expression:

Figure 18.39 

```
1 /(?<!@)@(?!@)(can|cannot|canany)/
```

The pattern in **Figure 18.39** contains two common regular expression techniques: the negative look behind and the negative look ahead.

We can define a negative look behind by starting our capture group with the `<?!` character sequence. When present, the regular expression engine will match everything that follows as long as it does not begin with the characters that appear within the negative look-behind group.

The negative look-behind in **Figure 18.39** is `(<?<!@)`, which can be interpreted as “is not preceded by the @ character.”

The negative look-ahead is the opposite of the negative look-behind and will ensure that our pattern is not followed by a specified pattern. In **Figure 18.39**, the negative look-ahead is `(?!@)`, and can be interpreted as “is not followed by the @ character.”

 begin backmatter  

## Appendix A: UTF-8 String Iterator Implementation

The following code example is the full implementation of the UTF-8 string iterator outlined in Chapter 1. The `setIteratorPosition` method was introduced in Chapter 15.

Figure 19.1 UTF-8 String Iterator Implementation 

```
  1 <?php
  2 
  3 use ArrayAccess;
  4 use Countable;
  5 use Iterator;
  6 
  7 class Utf8StringIterator implements ArrayAccess, Countable, Iterator
  8 {
  9     protected $string = '';
 10     protected $position = 0;
 11     protected $lastSize = 1;
 12     protected $length = 0;
 13     protected $stringIndex = null;
 14 
 15     public function __construct(string $string)
 16     {
 17         $this->string = $string;
 18         $this->length = mb_strlen($string, 'UTF-8');
 19     }
 20 
 21     public function setIteratorPosition(
 22         int $position,
 23         int $lastSize): void
 24     {
 25         $this->position = $position;
 26         $this->lastSize = $lastSize;
 27     }
 28 
 29     public function count(): int
 30     {
 31         return $this->length;
 32     }
 33 
 34     public function current(): mixed
 35     {
 36         $firstByte = ord($this->string[$this->position]);
 37 
 38         $this->lastSize = match(true) {
 39             $firstByte <= 127 => 1,
 40             $firstByte <= 223 => 2,
 41             $firstByte <= 239 => 3,
 42             default => 4
 43         };
 44 
 45         return substr(
 46             $this->string,
 47             $this->position,
 48             $this->lastSize
 49         );
 50     }
 51 
 52     public function next(): void
 53     {
 54         $this->position += $this->lastSize;
 55     }
 56 
 57     public function key(): mixed
 58     {
 59         return $this->position;
 60     }
 61 
 62     public function valid(): bool
 63     {
 64         return isset($this->string[$this->position]);
 65     }
 66 
 67     public function rewind(): void
 68     {
 69         $this->position = 0;
 70     }
 71 
 72     public function lastCharSize(): int
 73     {
 74         return $this->lastSize;
 75     }
 76 
 77     private function buildStringIndex(): void
 78     {
 79         if ($this->stringIndex !== null) {
 80             return;
 81         }
 82 
 83         $this->stringIndex = [];
 84         $string = new Utf8StringIterator($this->string);
 85 
 86         $charIndex = 0;
 87 
 88         foreach ($string as $char) {
 89             $this->stringIndex[$charIndex] = $string->lastCharSize();
 90             $charIndex += 1;
 91         }
 92 
 93         unset($string);
 94     }
 95 
 96     public function offsetExists(mixed $offset): bool
 97     {
 98         $this->buildStringIndex();
 99 
100         return array_key_exists(
101             $offset,
102             $this->stringIndex
103         );
104     }
105 
106     public function offsetGet(mixed $offset): mixed
107     {
108         $this->buildStringIndex();
109 
110         return substr(
111             $this->string,
112             $this->getPosition($offset),
113             $this->stringIndex[$offset]
114         );
115     }
116 
117     protected function getPosition($offset): int
118     {
119         $position = 0;
120 
121         for ($i = 0; $i < $offset; $i++) {
122             $position += $this->stringIndex[$i];
123         }
124 
125         return $position;
126     }
127 
128     public function getPositionFromCharIndex($charIndex): int
129     {
130         $this->buildStringIndex();
131 
132         return $this->getPosition($charIndex);
133     }
134 
135     public function offsetSet(mixed $offset, mixed $value): void
136     {
137         $this->buildStringIndex();
138 
139         $this->string = substr_replace(
140             $this->string,
141             $value,
142             $this->getPosition($offset),
143             $this->stringIndex[$offset]
144         );
145         $this->stringIndex = null;
146 
147         $this->buildStringIndex();
148         $this->updateStringMetaData();
149     }
150 
151     public function offsetUnset(mixed $offset): void
152     {
153         $this->buildStringIndex();
154 
155         $this->string = substr_replace(
156             $this->string,
157             '',
158             $this->getPosition($offset),
159             $this->stringIndex[$offset]
160         );
161         unset($this->stringIndex[$offset]);
162 
163         $this->updateStringMetaData();
164     }
165 
166     protected function updateStringMetaData(): void
167     {
168         $this->stringIndex = array_values($this->stringIndex);
169         $this->length = mb_strlen($this->string);
170     }
171 
172     public function __toString(): string
173     {
174         return $this->string;
175     }
176 }
```

## Appendix B: CharacterPositionLocator Implementation

The following code example is the full implementation of the character position locator developed in Chapter 10.

Figure 20.1 CharacterPositionLocator Implementation 

```
  1 <?php
  2 
  3 class Position
  4 {
  5     public $position = null;
  6     public $column = null;
  7     public $line = null;
  8 }
  9 
 10 class CharacterPositionLocator
 11 {
 12     protected $string = '';
 13     protected $length = 0;
 14     protected $newLineIndex = [];
 15 
 16     public function __construct(string $string)
 17     {
 18         $this->string = $string;
 19         $this->length = mb_strlen($string, 'UTF-8');
 20         $this->buildNewLineIndex();
 21     }
 22 
 23     protected function buildNewLineIndex(): void
 24     {
 25         preg_match_all(
 26             "/\r\n|\n|\r/u",
 27             $this->string,
 28             $matches,
 29             PREG_OFFSET_CAPTURE
 30         );
 31         
 32         $this->newLineIndex = collect($matches[0])
 33             ->map(function ($match) {
 34             // Return an array containing the start
 35             // and end position of the sequence.
 36             return [
 37                 $match[1],
 38                 $match[1] + strlen($match[0]) - 1
 39             ];
 40         })->all();
 41     }
 42 
 43     public function getLineNumber($position): ?int
 44     {
 45         return $this->getCharPosition($position)?->line;
 46     }
 47 
 48     public function getColumnNumber($position): ?int
 49     {
 50         return $this->getCharPosition($position)?->column;
 51     }
 52 
 53     public function isNewLine($position): bool
 54     {
 55         if ($position > $this->length || $position < 0) {
 56             return false;
 57         }
 58 
 59         for ($i = 0; $i < count($this->newLineIndex); $i++) {
 60             $nlStart = $this->newLineIndex[$i][0];
 61             $nlEnd = $this->newLineIndex[$i][1];
 62 
 63             if ($position >= $nlStart && $position <= $nlEnd) {
 64                 return true;
 65             }
 66         }
 67 
 68         return false;
 69     }
 70 
 71     public function getCharPositionFromLineColumn($line, $column): ?int
 72     {
 73         if ($line < 1 || $column < 1) {
 74             return null;
 75         }
 76         $position = null;
 77         for ($i = 0; $i < count($this->newLineIndex); $i++) {
 78             if ($i + 1 != $line) {
 79                 continue;
 80             }
 81 
 82             if ($i == 0) {
 83                 $position = $column - 1;
 84                 break;
 85             }
 86 
 87             $index = $this->newLineIndex[$i - 1];
 88             $position = $index[1] + $column;
 89 
 90             // Ensure the position is inside the current line.
 91             $nextLineStart = $this->newLineIndex[$i];
 92 
 93             if ($position >= $nextLineStart[0]) {
 94                 return null;
 95             }
 96 
 97             break;
 98         }
 99 
100         if ($position === null) {
101             $lastIndex =
102                 $this->newLineIndex[count($this->newLineIndex) - 1];
103 
104             $position = $lastIndex[1] + $column;
105         }
106 
107         if ($position >= $this->length || $position < 0) {
108             return null;
109         }
110 
111         return $position;
112     }
113 
114     public function getCharPosition($position): ?Position
115     {
116         if ($position > $this->length || $position < 0) {
117             return null;
118         }
119 
120         $lastOffset = null;
121         $column = null;
122         $line = null;
123 
124         for ($i = 0; $i < count($this->newLineIndex); $i++) {
125             $offset = $this->newLineIndex[$i][1];
126 
127             if ($i == 0 && $position < $offset) {
128                 $line = 1;
129                 $column = $position + 1;
130                 break;
131             }
132 
133             if ($offset > $position) {
134                 $line = $i + 1;
135                 $column = $position - $lastOffset;
136                 break;
137             }
138 
139             $lastOffset = $offset;
140         }
141 
142         if ($column == null) {
143             $line = $i + 1;
144             $column = $position - $lastOffset;
145         }
146 
147         $charPosition = new Position();
148         $charPosition->position = $position;
149         $charPosition->column = $column;
150         $charPosition->line = $line;
151 
152         return $charPosition;
153     }
154 }
```

## Appendix C: IndentationManager Implementation

The following code example is the full implementation of the indentation manager developed in Chapter 11. This implementation relies on numerous helper methods developed throughout Chapter 10 and Chapter 11.

Figure 21.1 IndentationManager Implementation 

```
  1 <?php
  2 
  3 class TextIndentation
  4 {
  5     public function __construct(
  6         public string $line,
  7         public int $lineNumber,
  8         public int $leadingWhitespace,
  9         public int $indentCount,
 10     ) {}
 11 
 12     /**
 13      * @var TextIndentation[]
 14      */
 15     public $nestedLines = [];
 16 
 17     /**
 18      * @var TextIndentation[]
 19      */
 20     public $allNestedLines = [];
 21 }
 22 
 23 class IndentationManager
 24 {
 25     /**
 26      * @var TextIndentation[]
 27      */
 28     protected $lines;
 29 
 30     /**
 31      * @var int
 32      */
 33     protected $numberOfLines;
 34 
 35     public function __construct(string $value, $tabSize = 4)
 36     {
 37         $this->lines = Str::indentation($value, $tabSize);
 38         $this->numberOfLines = count($this->lines);
 39     }
 40 
 41     public function getLines(): array
 42     {
 43         return $this->lines;
 44     }
 45 
 46     public function groupIndentation(): void
 47     {
 48         if ($this->numberOfLines == 0) {
 49             return;
 50         }
 51 
 52         for ($i = 0; $i < $this->numberOfLines; $i++) {
 53             if (str($this->lines[$i]->line)->trim->length == 0) {
 54                 continue;
 55             }
 56 
 57             $this->nestLines($i);
 58         }
 59     }
 60 
 61     protected function nestLines($start): void
 62     {
 63         $line = $this->lines[$start];
 64 
 65         if ($start + 1 >= $this->numberOfLines) {
 66             return;
 67         }
 68 
 69         $nestedLines = [];
 70 
 71         for ($i = $start + 1; $i < $this->numberOfLines; $i++) {
 72             $current = $this->lines[$i];
 73 
 74             if ($current->indentCount <= $line->indentCount &&
 75                 str($current->line)->trim->length > 0) {
 76                 break;
 77             }
 78 
 79             $nestedLines[] = $current;
 80         }
 81 
 82         if (count($nestedLines) == 0) {
 83             return;
 84         }
 85 
 86         $firstIndent = $nestedLines[0]->indentCount;
 87 
 88         // Find the first non-zero indentation, if any.
 89         if ($firstIndent == 0) {
 90             for ($i = 1; $i < count($nestedLines); $i++) {
 91                 if ($nestedLines[$i]->indentCount > 0) {
 92                     $firstIndent = $nestedLines[$i]->indentCount;
 93                     break;
 94                 }
 95             }
 96         }
 97 
 98         $line->allNestedLines = $nestedLines;
 99 
100         $line->nestedLines = collect($nestedLines)
101             ->filter(function ($line) use ($firstIndent) {
102             return $line->indentCount == $firstIndent;
103         })->values()->all();
104 
105     }
106 }
```

## Appendix D: Gherkin Parser Implementation

The following is the complete Gherkin parser implementation developed throughout Chapter 12.

Figure 22.1 Gherkin Parser Implementation 

```
   1 <?php
   2 
   3 class Block
   4 {
   5     /**
   6      * The start offset of the block.
   7      *
   8      * @var int
   9      */
  10     public int $start;
  11 
  12     /**
  13      * A list of all comments below the block.
  14      *
  15      * @var Comment[]
  16      */
  17     public array $comments = [];
  18 
  19     /**
  20      * The normalized Gherkin keyword of the block..
  21      *
  22      * @var string
  23      */
  24     public string $keyword = '';
  25 }
  26 
  27 /**
  28  * Represents a Gherkin Feature
  29  *
  30  * @see https://cucumber.io/docs/gherkin/reference/#feature
  31  */
  32 class Feature extends Block
  33 {
  34     /**
  35      * The name of the feature.
  36      *
  37      * @var string
  38      */
  39     public string $name;
  40 
  41     /**
  42      * The free-form description of the feature.
  43      *
  44      * @var string
  45      */
  46     public string $description;
  47 
  48     /**
  49      * An optional background for the feature.
  50      *
  51      * @var Background|null
  52      */
  53     public ?Background $background;
  54 
  55     /**
  56      * A list of all scenarios in the feature.
  57      *
  58      * @var Scenario[]
  59      */
  60     public array $scenarios = [];
  61 
  62     /**
  63      * A list of all rules in the feature.
  64      *
  65      * @var ScenarioOutline[]
  66      */
  67     public array $rules = [];
  68 }
  69 
  70 class DataBlock
  71 {
  72     /**
  73      * The start offset of the block.
  74      *
  75      * @var int
  76      */
  77     public int $start;
  78 
  79     /**
  80      * The end offset of the block.
  81      *
  82      * @var int
  83      */
  84     public int $end;
  85 }
  86 
  87 /**
  88  * Represents a Gherkin DocString
  89  *
  90  * Can start with """ or ```
  91  *
  92  * @see https://cucumber.io/docs/gherkin/reference/#doc-strings
  93  */
  94 class DocString extends DataBlock
  95 {
  96     public string $content = '';
  97     public string $delimiter = '';
  98 }
  99 
 100 /**
 101  * Represents a Gherkin DataTable
 102  *
 103  * Used to supplying a list of values a step definition.
 104  *
 105  * @see https://cucumber.io/docs/gherkin/reference/#data-tables
 106  */
 107 class DataTable extends DataBlock
 108 {
 109     /**
 110      * @var TableRow[]
 111      */
 112     public array $rows = [];
 113 }
 114 
 115 /**
 116  * Represents a single row in a DataTable.
 117  */
 118 class TableRow extends Block
 119 {
 120     /**
 121      * @var TableCell[]
 122      */
 123     public array $cells = [];
 124 }
 125 
 126 /**
 127  * Holds a single cell value in a TableRow.
 128  */
 129 class TableCell extends Block
 130 {
 131     public function __construct(public string $value)
 132     { }
 133 }
 134 
 135 /**
 136  * Represents a Gherkin Comment.
 137  *
 138  * @see https://cucumber.io/docs/gherkin/reference
 139  */
 140 class Comment extends Block
 141 {
 142     /**
 143      * The comment's text.
 144      *
 145      * @var string
 146      */
 147     public string $text;
 148 }
 149 
 150 /**
 151  * Represents a Gherkin Rule
 152  *
 153  * @see https://cucumber.io/docs/gherkin/reference/#rule
 154  */
 155 class Rule extends Scenario
 156 {
 157     public ?Background $background;
 158     public array $scenarios = [];
 159 }
 160 
 161 /**
 162  * Represents a Gherkin Background
 163  *
 164  * @see https://cucumber.io/docs/gherkin/reference/#background
 165  */
 166 class Background extends Scenario
 167 {
 168 
 169 }
 170 
 171 /**
 172  * Represents a Gherkin Scenario
 173  *
 174  * @see https://cucumber.io/docs/gherkin/reference/#example
 175  */
 176 class Scenario extends Block
 177 {
 178     /**
 179      * The free-form description of the scenario.
 180      *
 181      * @var string
 182      */
 183     public string $description;
 184 
 185     /**
 186      * The name of the scenario.
 187      *
 188      * @var string
 189      */
 190     public string $name;
 191 
 192     /**
 193      * The list of steps for the scenario.
 194      *
 195      * @var Step[]
 196      */
 197     public array $steps = [];
 198 
 199     /**
 200      * Any DataTable examples for the scenario.
 201      *
 202      * @var Examples[]
 203      */
 204     public array $examples = [];
 205 
 206     /**
 207      * The tags for the scenario.
 208      *
 209      * @var Tag[]
 210      */
 211     public array $tags = [];
 212 }
 213 
 214 /**
 215  * Represents a Gherkin Scenario Outline
 216  *
 217  * @see https://cucumber.io/docs/gherkin/reference/#scenario-outline
 218  */
 219 class ScenarioOutline extends Scenario
 220 {
 221 
 222 }
 223 
 224 /**
 225  * Represents a Scenario Outline's Examples.
 226  */
 227 class Examples extends Block
 228 {
 229     /**
 230      * The Example's DataTable.
 231      *
 232      * @var DataTable|null
 233      */
 234     public ?DataTable $table;
 235 }
 236 
 237 /**
 238  * Represents a Gherkin Scenario Step
 239  *
 240  * @see https://cucumber.io/docs/gherkin/reference/#steps
 241  */
 242 class Step extends Block
 243 {
 244     /**
 245      * The step's instructions, or text.
 246      *
 247      * @var string
 248      */
 249     public string $text;
 250 
 251     /**
 252      * The list of data blocks for the step.
 253      *
 254      * May include a DocString or DataTable.
 255      *
 256      * @var DataBlock[]
 257      */
 258     public array $data = [];
 259 
 260     /**
 261      * A list of parameters for the step.
 262      *
 263      * @var Parameter[]
 264      */
 265     public array $parameters = [];
 266 }
 267 
 268 /**
 269  * Represents a Gherkin Step Parameter.
 270  *
 271  * Step parameters a defined as <param> <param2>, etc.
 272  *
 273  * @see https://cucumber.io/docs/gherkin/reference/#step-parameters
 274  */
 275 class Parameter extends Block
 276 {
 277     /**
 278      * The name of the parameter.
 279      *
 280      * @var string
 281      */
 282     public string $name;
 283 }
 284 
 285 /**
 286  * Represents a Gherkin Scenario Tag
 287  *
 288  * Scenario tags are defined as @tag @tag2, etc.
 289  */
 290 class Tag extends Block
 291 {
 292     /**
 293      * The name of the tag.
 294      *
 295      * @var string
 296      */
 297     public string $name;
 298 }
 299 
 300 class GherkinParser
 301 {
 302 
 303     /**
 304      * @var CharacterPositionLocator
 305      */
 306     protected CharacterPositionLocator $locator;
 307 
 308     /**
 309      * The list of keywords that can be used to start a new block.
 310      *
 311      * @var string[]
 312      */
 313     protected array $gherkinKeywords = [
 314     ];
 315 
 316     /**
 317      * The list of keywords that can be used to start a new step.
 318      *
 319      * @var string[]
 320      */
 321     protected array $stepKeywords = [
 322     ];
 323 
 324     protected array $locales = [
 325         'en' => [
 326             'keywords' => [
 327                 'feature' => 'Feature:',
 328                 'rule' => 'Rule:',
 329                 'background' => 'Background:',
 330                 'scenario' => 'Scenario:',
 331                 'scenario_outline' => 'Scenario Outline:',
 332                 'scenario_template' => 'Scenario Template:',
 333                 'example' => 'Example:',
 334                 'examples' => 'Examples:',
 335                 'scenarios' => 'Scenarios:',
 336             ],
 337             'stepKeywords' => [
 338                 'given' => 'Given ',
 339                 'when' => 'When ',
 340                 'then' => 'Then ',
 341                 'and' => 'And ',
 342                 'but' => 'But ',
 343             ],
 344         ],
 345         'no' => [
 346             'keywords' => [
 347                 'feature' => 'Funksjonalitet:',
 348                 'rule' => 'Regel:',
 349                 'background' => 'Bakgrunn:',
 350                 'scenario' => 'Scenario:',
 351                 'scenario_outline' => 'Abstrakt Scenario:',
 352                 'scenario_template' => 'Scenariomal:',
 353                 'example' => 'Eksempel:',
 354                 'examples' => 'Eksempler:',
 355                 'scenarios' => 'Scenarier:',
 356             ],
 357             'stepKeywords' => [
 358                 'given' => 'Gitt ',
 359                 'when' => 'Når ',
 360                 'then' => 'Så ',
 361                 'and' => 'Og ',
 362             ],
 363         ],
 364     ];
 365 
 366     /**
 367      * Sets the parser locale.
 368      *
 369      * @param string $locale The locale.
 370      * @return void
 371      */
 372     public function setLocale(string $locale = 'en')
 373     {
 374         $this->gherkinKeywords = $this->locales[$locale]['keywords'];
 375         $this->stepKeywords = $this->locales[$locale]['stepKeywords'];
 376         $this->stepKeywords['*'] = '* ';
 377     }
 378 
 379     /**
 380      * Parses the provided Gherkin text.
 381      *
 382      * @param string $value The string to parse.
 383      * @param int $tabSize The tab size.
 384      * @param string $locale The locale.
 385      * @return Feature|null
 386      * @throws Exception
 387      */
 388     public function parse(string $value,
 389         int $tabSize = 2,
 390         string $locale = 'en'
 391     ): ?Feature
 392     {
 393         $this->setLocale($locale);
 394 
 395         $value = Str::normalizeEol($value);
 396         $this->locator = new CharacterPositionLocator($value);
 397 
 398         $indentationManager = new IndentationManager($value, $tabSize);
 399         $lines = $indentationManager->getLines();
 400 
 401         // Locate the start of the feature.
 402         for ($i = 0; $i < count($lines); $i++) {
 403             $cur = $lines[$i];
 404 
 405             $content = (string) str($cur->line)->ltrim;
 406 
 407             if ($i == 0 && $cur->indentCount == 0 &&
 408                 str($content)->startsWith('# language')
 409             ) {
 410                 $this->setLocale(str($content)->after(':')->trim);
 411                 continue;
 412             }
 413 
 414             if (str($content)->startsWith(
 415                 $this->gherkinKeywords['feature'])) {
 416                 return $this->parseFeature($cur, $cur->nestedLines);
 417             }
 418         }
 419 
 420         return null;
 421     }
 422 
 423     /**
 424      * Parses a feature.
 425      *
 426      * @param TextIndentation $featureLine The line to parse.
 427      * @param TextIndentation[] $lines The lines to parse.
 428      * @return Feature
 429      * @throws Exception
 430      */
 431     protected function parseFeature(
 432         TextIndentation $featureLine,
 433         array $lines): Feature
 434     {
 435         $feature = new Feature();
 436 
 437         $feature->comments = $this->parseComments($lines);
 438         $feature->start = $this->lineToPosition($featureLine);
 439         $feature->keyword = 'feature';
 440 
 441         $feature->name = $this->parseName(
 442             $featureLine,
 443             'feature'
 444         );
 445 
 446         $feature->description = $this->parseDescription(
 447             $featureLine->nestedLines
 448         );
 449 
 450         $feature->background = $this->parseBackground($lines);
 451         $feature->scenarios = $this->parseScenarios($lines);
 452         $feature->rules = $this->parseRules($lines);
 453 
 454         return $feature;
 455     }
 456 
 457     /**
 458      * Parses a Gherkin Background.
 459      *
 460      * @param TextIndentation[] $lines Then lines to parse.
 461      * @return Background|null
 462      * @throws Exception
 463      */
 464     protected function parseBackground(array $lines): ?Background
 465     {
 466         for ($i = 0; $i < count($lines); $i++) {
 467             $cur = $lines[$i];
 468 
 469             $content = (string) str($cur->line)->ltrim;
 470 
 471             // Test if the current line starts with the Background
 472             // keyword. For English, this checks for "Background:".
 473             if (str($content)->startsWith(
 474                 $this->gherkinKeywords['background'])) {
 475                 $scenario = $this->parseScenario($cur);
 476 
 477                 $background = new Background();
 478                 $background->steps = $scenario->steps;
 479                 $background->start = $scenario->start;
 480                 $background->keyword = 'background';
 481 
 482                 return $background;
 483             }
 484         }
 485 
 486         return null;
 487     }
 488 
 489     /**
 490      * Parses a list of Gherkin Scenarios.
 491      *
 492      * @param TextIndentation[] $lines The lines to parse.
 493      * @return array
 494      * @throws Exception
 495      */
 496     protected function parseScenarios(array $lines): array
 497     {
 498         $scenarios = [];
 499 
 500         for ($i = 0; $i < count($lines); $i++) {
 501             $cur = $lines[$i];
 502 
 503             $content = str($cur->line)->ltrim;
 504 
 505             // Test if the current line starts with the Scenario
 506             // keyword. For English, this checks for "Scenario:".
 507             // The Examples keyword will also be parsed as a
 508             // scenario. For English, this checks for "Examples:".
 509             if ($content->startsWith([
 510                 $this->gherkinKeywords['scenario'],
 511                 $this->gherkinKeywords['example']
 512             ])) {
 513                 $scenarios[] = $this->parseScenario(
 514                     $cur, $this->getTagsLine($lines, $i)
 515                 );
 516 
 517             } elseif ($content->startsWith(
 518                 $this->gherkinKeywords['scenario_outline'],
 519                 $this->gherkinKeywords['scenario_template']
 520             )) {
 521 
 522                 // Parses Scenario Outline if the current line
 523                 // begins with the scenario_outline or the
 524                 // scenario_template keyword. For English,
 525                 // this is "Scenario Outline:" or "Scenario Template:".
 526                 $scenarios[] = $this->parseScenarioOutline(
 527                     $cur, $this->getTagsLine($lines, $i)
 528                 );
 529             }
 530         }
 531 
 532         return $scenarios;
 533     }
 534 
 535     /**
 536      * Searches a list of lines in reverse for a
 537      * line that begins with the tag keyword (@).
 538      *
 539      * This method will stop searching if the
 540      * line immediately before the current
 541      * line is not a tag line.
 542      *
 543      * @param TextIndentation[] $lines The lines to search.
 544      * @param int $i The current line index.
 545      * @return TextIndentation|null
 546      */
 547     protected function getTagsLine(
 548         array $lines,
 549         int $i): ?TextIndentation
 550     {
 551         $tagLine = null;
 552 
 553         if ($i > 0) {
 554             $prev = $lines[$i - 1];
 555             $prevContent = str($prev->line)->ltrim;
 556 
 557             if ($prevContent->startsWith('@')) {
 558                 $tagLine =  $prev;
 559             }
 560         }
 561 
 562         return $tagLine;
 563     }
 564 
 565     /**
 566      * Parses a Gherkin Scenario Outline.
 567      *
 568      * @param TextIndentation $scenarioLine The line to parse.
 569      * @param TextIndentation|null $tagLine The tag line.
 570      * @return ScenarioOutline
 571      * @throws Exception
 572      */
 573     protected function parseScenarioOutline(
 574         TextIndentation $scenarioLine,
 575         TextIndentation $tagLine = null
 576     ): ScenarioOutline
 577     {
 578         $scenario = new ScenarioOutline();
 579 
 580         $scenario->comments = $this->parseComments(
 581             $scenarioLine->nestedLines
 582         );
 583 
 584         $scenario->start = $this->lineToPosition($scenarioLine);
 585 
 586         $scenario->keyword = 'scenario_outline';
 587 
 588         $scenario->name = $this->parseName(
 589             $scenarioLine,
 590             'scenario_outline'
 591         );
 592 
 593         $scenario->steps = $this->parseSteps(
 594             $scenarioLine->nestedLines
 595         );
 596 
 597         $scenario->examples = $this->parseExamples(
 598             $scenarioLine->nestedLines
 599         );
 600 
 601         if ($tagLine) {
 602             $scenario->tags = $this->parseTags($tagLine);
 603         }
 604 
 605         return $scenario;
 606     }
 607 
 608     /**
 609      * Parses a Gherkin Scenario.
 610      *
 611      * @param TextIndentation $scenarioLine The line to parse.
 612      * @param TextIndentation|null $tagLine The tag line.
 613      * @return Scenario
 614      * @throws Exception
 615      */
 616     protected function parseScenario(
 617         TextIndentation $scenarioLine,
 618         TextIndentation $tagLine = null): Scenario
 619     {
 620         $scenario = new Scenario();
 621 
 622         $scenario->comments = $this->parseComments(
 623             $scenarioLine->nestedLines
 624         );
 625 
 626         $scenario->description = $this->parseDescription(
 627             $scenarioLine->allNestedLines
 628         );
 629 
 630         $scenario->keyword = 'scenario';
 631 
 632         $scenario->name = (string) str($this->parseName(
 633             $scenarioLine,
 634             'scenario')
 635         )->ltrim;
 636 
 637         $scenario->steps = $this->parseSteps(
 638             $scenarioLine->nestedLines
 639         );
 640 
 641         $scenario->start = $this->lineToPosition(
 642             $scenarioLine
 643         );
 644 
 645         $scenario->examples = $this->parseExamples(
 646             $scenarioLine->nestedLines
 647         );
 648 
 649         if ($tagLine) {
 650             $scenario->tags = $this->parseTags($tagLine);
 651         }
 652 
 653         return $scenario;
 654     }
 655 
 656     /**
 657      * Parses Scenario Tags.
 658      *
 659      * @param TextIndentation $tagLine The tag line.
 660      * @return array
 661      */
 662     protected function parseTags(TextIndentation $tagLine): array
 663     {
 664         $tags = [];
 665 
 666         $tagLineContent = str($tagLine->line)->ltrim;
 667 
 668         // Splits the string into an array on the "@"
 669         // character. The string "@tag1 @tag2" will
 670         // become ["tag1", "tag2"].
 671         $tagNames = $tagLineContent->split('/@/');
 672 
 673         foreach ($tagNames as $tagName) {
 674             if (empty($tagName)) {
 675                 continue;
 676             }
 677 
 678             $tag = new Tag();
 679             $tag->name = (string) str($tagName)->trim;
 680             $tag->start = $this->lineToPosition($tagLine);
 681 
 682             $tags[] = $tag;
 683         }
 684 
 685         return $tags;
 686     }
 687 
 688     /**
 689      * Parses a list of Gherkin Rules.
 690      *
 691      * @param TextIndentation[] $lines The lines to parse.
 692      * @return array
 693      * @throws Exception
 694      */
 695     protected function parseRules(array $lines): array
 696     {
 697         $rules = [];
 698 
 699         for ($i = 0; $i < count($lines); $i++) {
 700             $cur = $lines[$i];
 701 
 702             $content = (string) str($cur->line)->ltrim;
 703 
 704             // Test if the current line starts with the Rule
 705             // keyword. For English, this checks for "Rule:".
 706             if (str($content)->startsWith(
 707                 $this->gherkinKeywords['rule'])) {
 708                 $rules[] = $this->parseRule($cur);
 709             }
 710         }
 711 
 712         return $rules;
 713     }
 714 
 715     /**
 716      * Parses a Gherkin Rule.
 717      *
 718      * @param TextIndentation $ruleLine The line to parse.
 719      * @return Rule
 720      * @throws Exception
 721      */
 722     protected function parseRule(TextIndentation $ruleLine): Rule
 723     {
 724         $rule = new Rule();
 725 
 726         $rule->comments = $this->parseComments($ruleLine->nestedLines);
 727         $rule->start = $this->lineToPosition($ruleLine);
 728         $rule->keyword = 'rule';
 729         $rule->name = $this->parseName($ruleLine, 'rule');
 730 
 731         $rule->description = $this->parseDescription(
 732             $ruleLine->allNestedLines
 733         );
 734 
 735         $rule->background = $this->parseBackground(
 736             $ruleLine->nestedLines
 737         );
 738 
 739         $rule->scenarios = $this->parseScenarios(
 740             $ruleLine->nestedLines
 741         );
 742 
 743         return $rule;
 744     }
 745 
 746     /**
 747      * Parses a list of Gherkin Steps.
 748      *
 749      * @param TextIndentation[] $lines The lines to parse.
 750      * @return Step[]
 751      * @throws Exception
 752      */
 753     protected function parseSteps(array $lines): array
 754     {
 755         $steps = [];
 756 
 757         for ($i = 0; $i < count($lines); $i++) {
 758             $cur = $lines[$i];
 759 
 760             $content = (string) str($cur->line)->ltrim;
 761 
 762             // Test if the current line starts with a Step
 763             // keyword. For English, this checks can be any
 764             // of "Given", "When", "Then", "And", or "But".
 765             if (str($content)
 766                 ->ltrim->startsWith($this->stepKeywords)) {
 767                 $steps[] = $this->parseStep($cur);
 768             }
 769         }
 770 
 771         return $steps;
 772     }
 773 
 774     /**
 775      * Parses an individual Gherkin Step.
 776      *
 777      * @param TextIndentation $stepLine The line to parse.
 778      * @return Step
 779      * @throws Exception
 780      */
 781     protected function parseStep(TextIndentation $stepLine): Step
 782     {
 783         $step = new Step();
 784 
 785         $step->comments = $this->parseComments($stepLine->nestedLines);
 786 
 787         // Extract the keyword from the line.
 788         // This returns an array containing a
 789         // normalized keyword as the first
 790         // element, and the localized keyword
 791         // as the second element. For example,
 792         // ["given", "Given"].
 793         $sourceKeyword = $this->parseStepKeyword($stepLine);
 794 
 795         $step->keyword = $sourceKeyword[0];
 796 
 797         $step->text = $this->parseStepText(
 798             $stepLine, str($sourceKeyword[1])->rtrim
 799         );
 800 
 801         $step->start = $this->lineToPosition($stepLine);
 802         $step->data = $this->parseStepData($stepLine);
 803         $step->parameters = $this->parseStepParameters($stepLine);
 804 
 805         return $step;
 806     }
 807 
 808     /**
 809      * Parses the line and returns an array containing
 810      * instances of either DataTable or DocString.
 811      *
 812      * @param TextIndentation $stepLine The line to parse.
 813      * @return DataTable[]|DocString[]
 814      */
 815     protected function parseStepData(TextIndentation $stepLine): array
 816     {
 817         $data = [];
 818 
 819         for ($i = 0; $i < count($stepLine->nestedLines); $i++) {
 820             $cur = $stepLine->nestedLines[$i];
 821 
 822             $content = (string) str($cur->line)->ltrim;
 823 
 824             // Doc strings can begin with either a
 825             // """ or ```. We will check for both.
 826             if (str($content)->startsWith(['"""', '```'])) {
 827                 $data[] = $this->parseDocString(
 828                     $cur,
 829                     $stepLine->allNestedLines
 830                 );
 831             } elseif (str($content)->startsWith('|')) {
 832                 // If the current line starts with a vertical
 833                 // pipe, we will ask the table parser to
 834                 // handle the contents.
 835                 $data[] = $this->parseTable(
 836                     $cur,
 837                     $stepLine->nestedLines
 838                 );
 839             }
 840         }
 841 
 842         return $data;
 843     }
 844 
 845     /**
 846      * Parses step parameters from a step line.
 847      *
 848      * @param TextIndentation $stepLine The line to parse.
 849      * @return array
 850      */
 851     protected function parseStepParameters(
 852         TextIndentation $stepLine
 853     ): array
 854     {
 855         // Matches all parameters in the step line.
 856         // For example, if the step line is:
 857         // Then I should have <left> cucumbers
 858         // This will match "<left>".
 859         preg_match_all(
 860             '/<([^>]+)>/u',
 861             $stepLine->line,
 862             $matches,
 863             PREG_OFFSET_CAPTURE)
 864         ;
 865 
 866         // Iterate all of our matches and
 867         // create new Parameter instances.
 868         return collect($matches[1])
 869             ->map(function ($match) use ($stepLine) {
 870                 $parameter = new Parameter();
 871 
 872                 // Add the relative position of our parameter.
 873                 $parameter->start =
 874                     $this->lineToPosition($stepLine) + $match[1];
 875 
 876                 $parameter->name = $match[0];
 877 
 878                 return $parameter;
 879             })->all();
 880     }
 881 
 882     /**
 883      * Parses a list of Gherkin Examples block.
 884      *
 885      * @param TextIndentation[] $lines The lines to parse.
 886      * @return array
 887      */
 888     protected function parseExamples(array $lines): array
 889     {
 890         $examples = [];
 891 
 892         for ($i = 0; $i < count($lines); $i++) {
 893             $cur = $lines[$i];
 894 
 895             $content = (string) str($cur->line)->ltrim;
 896 
 897             // Test if the current line starts with the Examples
 898             // or Scenarios keyword. For English, this checks
 899             // for "Examples:" or "Scenarios:".
 900             if (str($content)->startsWith(
 901                 $this->gherkinKeywords['examples'],
 902                 $this->gherkinKeywords['scenarios']
 903             )) {
 904                 $examples[] = $this->parseExample($cur);
 905             }
 906         }
 907 
 908         return $examples;
 909     }
 910 
 911     /**
 912      * Parses a Gherkin Example.
 913      *
 914      * @param TextIndentation $exampleLine The line to parse.
 915      * @return Examples
 916      */
 917     protected function parseExample(
 918         TextIndentation $exampleLine
 919     ): Examples
 920     {
 921         $example = new Examples();
 922 
 923         $example->comments = $this->parseComments(
 924             $exampleLine->nestedLines
 925         );
 926 
 927         $example->keyword = 'examples';
 928         $example->start = $this->lineToPosition($exampleLine);
 929 
 930         if (count($exampleLine->nestedLines) > 0) {
 931             $tableLine = $exampleLine->nestedLines[0];
 932 
 933             // Ask the table parser to handle the contents.
 934             $example->table = $this->parseTable(
 935                 $tableLine,
 936                 $exampleLine->nestedLines
 937             );
 938         }
 939 
 940         return $example;
 941     }
 942 
 943     /**
 944      * Parses a Gherkin DataTable.
 945      *
 946      * @param TextIndentation $tableLine The line to parse.
 947      * @param TextIndentation[] $lines All nested lines.
 948      * @return DataTable
 949      */
 950     protected function parseTable(
 951         TextIndentation $tableLine,
 952         array $lines
 953     ): DataTable
 954     {
 955         $table = new DataTable();
 956 
 957         $table->start = $this->lineToPosition($tableLine);
 958         $table->rows = $this->parseTableRows($lines);
 959 
 960         return $table;
 961     }
 962 
 963     /**
 964      * Parses the provided lines and returns a TableRow array.
 965      *
 966      * @param TextIndentation[] $lines The lines to parse.
 967      * @return TableRow[]
 968      */
 969     protected function parseTableRows(array $lines): array
 970     {
 971         $rows = [];
 972 
 973         for ($i = 0; $i < count($lines); $i++) {
 974             $cur = $lines[$i];
 975 
 976             $content = (string) str($cur->line)->ltrim;
 977 
 978             // If the current line begins with a vertical
 979             // pipe, we will parse it as a table row.
 980             if (str($content)->startsWith('|')) {
 981                 $rows[] = $this->parseTableRow($cur);
 982             }
 983         }
 984 
 985         return $rows;
 986     }
 987 
 988     /**
 989      * Parses a single line into a Gherkin DataRow.
 990      *
 991      * @param TextIndentation $tableRowLine The line to parse.
 992      * @return TableRow
 993      */
 994     protected function parseTableRow(
 995         TextIndentation $tableRowLine
 996     ): TableRow
 997     {
 998         $row = new TableRow();
 999 
1000         $row->start = $this->lineToPosition($tableRowLine);
1001         $row->cells = $this->parseTableCells($tableRowLine);
1002 
1003         return $row;
1004     }
1005 
1006     /**
1007      * Parses a single line into a Gherkin TableCell array.
1008      *
1009      * @param TextIndentation $tableRowLine The line to parse.
1010      * @return TableCell[]
1011      */
1012     protected function parseTableCells(
1013         TextIndentation $tableRowLine
1014     ): array
1015     {
1016         $cells = [];
1017 
1018         $content = (string) str($tableRowLine->line)->ltrim;
1019 
1020         // Splits our string into an array on the pipe character.
1021         // For example, if the line is: "| foo | bar |" this will
1022         // return ["", " foo ", " bar ", ""]. We also have a
1023         // negative lookbehind to ensure that we don't split
1024         // on escaped pipes. For example, if the line is:
1025         // "| foo \| bar |" this will return ["", " foo \| bar ", ""]
1026         $content = preg_split('/(?<!\\\)\|/u', $content);
1027 
1028         // Remove the spaces left over from the beginning and end.
1029         // We cannot remove all empty spaces,
1030         // since some cells can be empty.
1031         array_shift($content);
1032         array_pop($content);
1033 
1034         $content = collect($content)->map(function ($value) {
1035             return (string) str($value)
1036                 ->replace('\|', '|') // Replace escaped pipes
1037                 ->replace('\n', "\n") // Replace escaped newlines
1038                 ->replace('\\\\', '\\') // Replace escaped backslashes
1039                 ->trim;
1040         })->all();
1041 
1042         // Create a new TableCell for each cell value.
1043         foreach ($content as $cell) {
1044             $cells[] = new TableCell($cell);
1045         }
1046 
1047         return $cells;
1048     }
1049 
1050     /**
1051      * Parses a Ghrekin DocString.
1052      *
1053      * @param TextIndentation $docStringLine The line to parse.
1054      * @param TextIndentation[] $lines The lines to parse.
1055      * @return DocString
1056      */
1057     protected function parseDocString(
1058         TextIndentation $docStringLine,
1059         array $lines
1060     ): DocString
1061     {
1062         $docString = new DocString();
1063 
1064         $docString->start = $this->lineToPosition($docStringLine);
1065         $content = (string) str($docStringLine->line)->ltrim;
1066 
1067         if (str($content)->startsWith('"""')) {
1068             $docString->delimiter = '"""';
1069         } else {
1070             $docString->delimiter = '```';
1071         }
1072 
1073         $contentLines = [];
1074 
1075         foreach ($lines as $line) {
1076             if ($line->lineNumber <= $docStringLine->lineNumber) {
1077                 continue;
1078             }
1079 
1080             $trimmedLine = str($line->line)->ltrim;
1081 
1082             if ($trimmedLine->startsWith($docString->delimiter) &&
1083                 $line->leadingWhitespace ==
1084                 $docStringLine->leadingWhitespace) {
1085 
1086                 $docString->end = $this->lineToPosition($line);
1087                 break;
1088             }
1089 
1090             $contentLines[] = $line->line;
1091         }
1092 
1093         // Remove the leading whitespace from each line.
1094         $docString->content = collect($contentLines)
1095             ->map(function ($line) use ($docStringLine) {
1096 
1097                 return (string) str($line)->substr(
1098                     $docStringLine->leadingWhitespace
1099                 );
1100 
1101             })->implode("\n");
1102 
1103         return $docString;
1104     }
1105 
1106     /**
1107      * Returns the instruction text for a Gherkin Step.
1108      *
1109      * @param TextIndentation $stepLine The line to parse.
1110      * @param string $keyword The original keyword.
1111      * @return string
1112      */
1113     protected function parseStepText(
1114         TextIndentation $stepLine,
1115         string $keyword): string
1116     {
1117         $content = (string) str($stepLine->line)->ltrim;
1118 
1119         $stepText = str($content)->after($keyword);
1120 
1121         return (string) str($stepText)->trim;
1122     }
1123 
1124     /**
1125      * Returns the keyword for a Gherkin Step.
1126      *
1127      * @param TextIndentation $stepLine The line to parse.
1128      * @return array
1129      * @throws Exception
1130      */
1131     protected function parseStepKeyword(
1132         TextIndentation $stepLine
1133     ): array
1134     {
1135         $content = (string) str($stepLine->line)->ltrim;
1136 
1137         foreach ($this->stepKeywords as $name => $keyword) {
1138             if (str($content)->startsWith($keyword)) {
1139                 return [$name, $keyword];
1140             }
1141         }
1142 
1143         throw new \Exception('Invalid step keyword');
1144     }
1145 
1146     /**
1147      * Tests if the provided line begins with any Gherkin keyword.
1148      *
1149      * @param string $line The line to test.
1150      * @return bool
1151      */
1152     protected function startsWithKeyword(string $line): bool
1153     {
1154         $content = str($line)->ltrim;
1155 
1156         return $content->startsWith($this->stepKeywords) ||
1157             $content->startsWith($this->gherkinKeywords) ||
1158             $content->startsWith('@');
1159     }
1160 
1161     /**
1162      * Parses a free-form Gherkin description.
1163      *
1164      * @param TextIndentation[] $lines The lines to parse.
1165      * @return string
1166      */
1167     protected function parseDescription(array $lines): string
1168     {
1169         if (count($lines) == 0) { return ''; }
1170         $description = [];
1171 
1172         for ($i = 0; $i < count($lines); $i++) {
1173             $cur = $lines[$i];
1174 
1175             // We will stop looking for free-form
1176             // description text when we encounter
1177             // a line that starts with a keyword.
1178             if (str($cur->line)->trim->length == 0  ||
1179                 $this->startsWithKeyword($cur->line)) {
1180                 break;
1181             }
1182 
1183             if ($cur->indentCount > 0) {
1184                 $description[] = (string) str($cur->line)->ltrim;
1185                 continue;
1186             }
1187 
1188             break;
1189         }
1190 
1191         return (string) str(implode(' ', $description))
1192             ->squish();
1193     }
1194 
1195     /**
1196      * Parses a name for various blocks, such as the Feature name.
1197      *
1198      * @param TextIndentation $line The line to parse.
1199      * @param string $keyword The original keyword.
1200      * @return string
1201      */
1202     protected function parseName(
1203         TextIndentation $line,
1204         string $keyword
1205     ): string
1206     {
1207         return (string) str($line->line)
1208             ->trim->substr(strlen($this->gherkinKeywords[$keyword]))
1209             ->trim;
1210     }
1211 
1212     /**
1213      * Retrieves all Gherkin comments from the provided lines.
1214      *
1215      * @param TextIndentation[] $lines The lines to parse.
1216      * @return Comment[]
1217      */
1218     protected function parseComments(array $lines): array
1219     {
1220         $comments = [];
1221 
1222         foreach ($lines as $line) {
1223             if (str($line->line)->trim->startsWith('#')) {
1224                 $comments[] = $this->parseComment($line);
1225             }
1226         }
1227 
1228         return $comments;
1229     }
1230 
1231     /**
1232      * Parses an individual Gherkin comment.
1233      *
1234      * @param TextIndentation $line The line to parse.
1235      * @return Comment
1236      */
1237     protected function parseComment(TextIndentation $line): Comment
1238     {
1239         $comment = new Comment();
1240         $comment->start = $this->lineToPosition($line);
1241         $comment->text = (string) str($line->line)->substr(1)->trim;
1242 
1243         return $comment;
1244     }
1245 
1246     /**
1247      * Returns the position of the provided line.
1248      *
1249      * @param TextIndentation $line The line.
1250      * @return int
1251      */
1252     protected function lineToPosition(TextIndentation $line): int
1253     {
1254         return $this->locator->getCharPositionFromLineColumn(
1255             $line->lineNumber, $line->leadingWhitespace + 1
1256         );
1257     }
1258 }
```

## Appendix E: Markov Chain Implementation

The following is the complete Markov chain implementation developed throughout Chapter 13.

Figure 23.1 Markov Chain Implementation 

```
  1 <?php
  2 
  3 class MarkovGenerator
  4 {
  5     protected array $dictionary = [];
  6     protected array $totals = [];
  7     protected int $sequenceLength;
  8 
  9     public function __construct($sequenceLength = 1)
 10     {
 11         $this->sequenceLength = $sequenceLength;
 12 
 13         // Prevents negative, or zero, sequence lengths.
 14         if ($this->sequenceLength <= 0) {
 15             $this->sequenceLength = 1;
 16         }
 17     }
 18 
 19     /**
 20      * Trains the generator with the provided text.
 21      *
 22      * @param string $text The text to train the generator on.
 23      * @return void
 24      */
 25     public function loadText(string $text): void
 26     {
 27         $words = str($text)->lower->wordSplit->all();
 28 
 29         for ($i = 0; $i < count($words); $i++) {
 30             $word = implode(
 31                 ' ',
 32                 array_slice($words, $i, $this->sequenceLength)
 33             );
 34 
 35             $nextWord = $words[$i + $this->sequenceLength] ?? null;
 36 
 37             if (! isset($this->dictionary[$word][$nextWord])) {
 38                 $this->dictionary[$word][$nextWord] = 1;
 39             } else {
 40                 $this->dictionary[$word][$nextWord]++;
 41             }
 42         }
 43 
 44         foreach ($this->dictionary as $sequence => $values) {
 45             $this->totals[$sequence] = array_sum($values);
 46         }
 47     }
 48 
 49     /**
 50      * Returns a random word from the dictionary.
 51      *
 52      * @param string $seed The current word to use as a seed.
 53      * @return string|null
 54      */
 55     protected function getWord(string $seed): ?string
 56     {
 57         $rand = rand(1, $this->totals[$seed]);
 58 
 59         foreach ($this->dictionary[$seed] as $word => $count) {
 60             $rand -= $count;
 61 
 62             if ($rand <= 0) {
 63                 return $word;
 64             }
 65         }
 66 
 67         return null;
 68     }
 69 
 70     /**
 71      * Generates a random string based on the loaded text.
 72      *
 73      * @param string|null $seed The word to use as a seed.
 74      * @param int $length The number of words to generate.
 75      * @return string
 76      */
 77     public function generateText(
 78         string $seed = null,
 79         int $length = 100): string
 80     {
 81         if ($seed == null) {
 82             $seed = array_rand($this->dictionary);
 83         }
 84 
 85         // We need to break our seed into its
 86         // own list of words so that we can
 87         // retrieve the last word later
 88         // to help build up our seeds.
 89         $words = str($seed)->wordSplit->all();
 90 
 91         $output = $seed;
 92 
 93         for ($i = 0; $i < $length; $i++) {
 94             $nextWord = $this->getWord($seed);
 95 
 96             if ($nextWord == null) {
 97                 break;
 98             }
 99 
100             $output .= ' ' . $nextWord;
101 
102             // Remove the first word from our list of words.
103             $words = array_slice($words, 1);
104 
105             // Append the next word to the list.
106             $words[] = $nextWord;
107 
108             // Combine our words to create our next seed.
109             $seed = implode(' ', $words);
110         }
111 
112         return $output;
113     }
114 }
```

## Appendix F: Single-File Component Parser Implementation

The following code example is the full implementation of the single-file component parser developed in Chapter 15.

Figure 24.1 

```
 1 <?php
 2 
 3 class ParseResult
 4 {
 5     public string $content = '';
 6     public string $type = '';
 7     public int $startOffset = 0;
 8     public int $endOffset = 0;
 9 }
10 
11 class SingleFileComponentParser
12 {
13 
14     /**
15      * Parses the provided text into individual components.
16      *
17      * @param string $value The text to parse.
18      * @param array $parts The parts to parse.
19      * @return array
20      * @throws Exception
21      */
22     public function parse(
23         string $value,
24         array $parts = ['style', 'template', 'script']): array
25     {
26         $results = [];
27 
28         $positionLocator = new CharacterPositionLocator($value);
29 
30         $pattern = collect($parts)
31             ->map(fn($x) => preg_quote($x))->implode('|');
32 
33         preg_match_all(
34             '/^<[\/]?('.$pattern.').*>/m',
35             $value, $matches, PREG_OFFSET_CAPTURE
36         );
37 
38         $tagNames = $matches[1];
39         $sourceTags = $matches[0];
40 
41         for ($i = 0; $i < count($tagNames); $i++) {
42             $tag = $tagNames[$i];
43 
44             $next = $i + 1;
45 
46             if (! isset($sourceTags[$next])) {
47                 $location = $positionLocator
48                     ->getCharPosition($sourceTags[$i][1]);
49 
50                 throw new Exception("Missing closing tag for".
51                   " '{$tag[0]}' at line {$location->line} " .
52                   "column {$location->column}");
53             }
54 
55             $nextTag = $sourceTags[$next];
56             $expected = '</'.$tag[0].'>';
57 
58             if ($nextTag[0] != $expected) {
59                 $location = $positionLocator
60                     ->getCharPosition($sourceTags[$i][1]);
61 
62                 throw new Exception("Invalid closing tag " .
63                   "{$nextTag[0]}' for '{$tag[0]}' at ".
64                   "line {$location->line} column {$location->column}");
65             }
66 
67             $sourceTag = $sourceTags[$i][0];
68 
69             $start = $sourceTags[$i][1] + str($sourceTag)->length;
70             $end = $nextTag[1];
71 
72             $parseResult = new ParseResult();
73             $parseResult->type = $sourceTag;
74             $parseResult->startOffset = $start;
75             $parseResult->endOffset = $end;
76             $parseResult->content = str($value)
77                 ->substr($start, $end - $start)->toString();
78 
79             $results[] = $parseResult;
80 
81             $i += 1;
82         }
83 
84         return $results;
85     }
86 }
```

## Appendix G: String Cursor Implementation

The following code example is the full implementation of the string cursors concept introduced in Chapter 15.

Figure 25.1 Complete String Cursor Implementation 

```
  1 <?php
  2 
  3 class CursorResult
  4 {
  5     public int $startPosition = 0;
  6     public int $endPosition = 0;
  7     public int $length = 0;
  8     public string $value = '';
  9     public string $content = '';
 10 }
 11 
 12 abstract class AbstractStringCursor
 13 {
 14     /**
 15      * The string being iterated over.
 16      *
 17      * @var Utf8StringIterator
 18      */
 19     protected Utf8StringIterator $iterator;
 20 
 21     /**
 22      * Indicates if the cursor should reset the iterator back
 23      * to the location it was when traverse() was called.
 24      *
 25      * @var bool
 26      */
 27     private bool $shouldReset = false;
 28 
 29     /**
 30      * The number of characters to move the cursor forward.
 31      *
 32      * @var int|null
 33      */
 34     private ?int $advanceCount = null;
 35 
 36     /**
 37      * The character the iterator was
 38      * on when the cursor was created.
 39      *
 40      * @var string
 41      */
 42     protected string $initialCharacter;
 43 
 44     /**
 45      * The current string buffer contents.
 46      *
 47      * @var string
 48      */
 49     protected string $buffer = '';
 50 
 51     /**
 52      * The current position of the cursor.
 53      *
 54      * @var int
 55      */
 56     protected int $position = 0;
 57 
 58     /**
 59      * The cursor's relative index.
 60      *
 61      * @var int
 62      */
 63     protected int $index = 0;
 64 
 65     public function __construct(Utf8StringIterator $iterator)
 66     {
 67         $this->iterator = $iterator;
 68     }
 69 
 70     /**
 71      * Returns the internal Ut8StringIterator instance.
 72      *
 73      * @return Utf8StringIterator
 74      */
 75     public function iterator(): Utf8StringIterator
 76     {
 77         return $this->iterator;
 78     }
 79 
 80     /**
 81      * Sets the number of characters to move the cursor forward.
 82      *
 83      * @param int $count The number of characters to advance.
 84      * @return $this
 85      */
 86     public function advance(int $count): AbstractStringCursor
 87     {
 88         $this->advanceCount = $count;
 89 
 90         return $this;
 91     }
 92 
 93     /**
 94      * Skips the specified number of characters
 95      * without adding them to the string buffer.
 96      *
 97      * @param int $count The number of characters to skip.
 98      * @return $this
 99      */
100     public function skip(int $count): AbstractStringCursor
101     {
102         $this->position += $count;
103         $this->index += $count;
104 
105         for ($i = 0; $i < $count; $i++) {
106             $this->iterator->next();
107         }
108 
109         return $this;
110     }
111 
112     public function continue(): bool
113     {
114         return true;
115     }
116 
117     public function break(): bool
118     {
119         return false;
120     }
121 
122     /**
123      * Appends the content to the string buffer.
124      *
125      * @param string $content The content to append.
126      * @return $this
127      */
128     public function append(string $content): AbstractStringCursor
129     {
130         $this->buffer .= $content;
131 
132         return $this;
133     }
134 
135     /**
136      * Removes the last character from the string buffer.
137      *
138      * @return $this
139      */
140     public function popBuffer(): AbstractStringCursor
141     {
142         $this->buffer = str($this->buffer)->substr(0, -1);
143 
144         return $this;
145     }
146 
147     /**
148      * Resets the string buffer.
149      *
150      * @return $this
151      */
152     public function clearBuffer(): AbstractStringCursor
153     {
154         $this->buffer = '';
155 
156         return $this;
157     }
158 
159     /**
160      * Resets the string buffer and returns its contents.
161      *
162      * @return string
163      */
164     public function flushBuffer(): string
165     {
166         $contents = $this->buffer;
167         $this->buffer = '';
168 
169         return $contents;
170     }
171 
172     /**
173      * Indicates the cursor should reset the
174      * iterator and then returns false.
175      *
176      * @return bool
177      */
178     public function didNotProcess(): bool
179     {
180         $this->shouldReset = true;
181 
182         return false;
183     }
184 
185     /**
186      * Indicates if the cursor completed its traversal.
187      *
188      * @return bool
189      */
190     public function didProcess(): bool
191     {
192         return ! $this->shouldReset;
193     }
194 
195     abstract public function accept(
196         string $current,
197         ?string $prev = null,
198         ?string $next = null): ?bool;
199 
200     /**
201      * Adds the results of another cursor to the string buffer.
202      *
203      * @param AbstractStringCursor $cursor The cursor to traverse.
204      * @return string
205      */
206     public function bufferCursorResult(
207         AbstractStringCursor $cursor): string
208     {
209         $result = $cursor->traverse();
210         $this->popBuffer();
211         $this->append($result->value);
212 
213         $bufferContents = $this->flushBuffer();
214         $this->position += $result->length - 1;
215 
216         return $bufferContents;
217     }
218 
219     /**
220      * Traverses a string and returns the result.
221      *
222      * @return CursorResult
223      */
224     public function traverse(): CursorResult
225     {
226         $result = new CursorResult();
227 
228         // Store the current position of the iterator.
229         // We will use these if we need to rewind.
230         $lastSize = $this->iterator->lastCharSize();
231         $startPosition = $this->iterator->key();
232 
233         $this->shouldReset = false;
234         $this->advanceCount = null;
235         $this->buffer = '';
236         $this->index = 0;
237 
238         $this->position = $startPosition;
239 
240         $result->startPosition = $startPosition;
241 
242         $this->initialCharacter = $this->iterator->current();
243 
244         for ($this->position = $startPosition;
245              $this->position < count($this->iterator);
246              $this->position++) {
247             $current = $this->iterator[$this->position];
248             $next = null;
249             $prev = null;
250 
251             if ($this->position > 0) {
252                 $prev = $this->iterator[$this->position - 1];
253             }
254 
255             if ($this->position + 1 < count($this->iterator)) {
256                 $next = $this->iterator[$this->position + 1];
257             }
258 
259             $this->buffer .= $current;
260 
261             if ($this->accept($current, $prev, $next) === false) {
262                 // If needed, rewind the iterator back to its
263                 // position when traverse() was first called.
264                 if ($this->shouldReset) {
265                     $this->iterator->setIteratorPosition(
266                         $startPosition,
267                         $lastSize
268                     );
269                 }
270 
271                 $result->endPosition = $this->iterator->key();
272                 $result->value = $this->buffer;
273                 $result->length = str($this->buffer)->length();
274                 $result->content = str($this->buffer)->
275                     substr(1, -1)->toString();
276                 break;
277             }
278 
279             if ($this->advanceCount != null) {
280                 for ($j = 0; $j < $this->advanceCount; $j++) {
281                     $this->iterator->next();
282                     $cur = $this->iterator->current();
283                     $this->buffer .= $cur;
284                 }
285 
286                 $this->position  += $this->advanceCount;
287                 $this->index += $this->advanceCount;
288                 $this->advanceCount = null;
289 
290                 continue;
291             }
292 
293             // Move the iterator forward by the size of the
294             // current character. This is necessary because
295             // we want the iterator to be at the same
296             // location when a cursor completes so
297             // that iterations happening outside
298             // the cursor can resume after.
299             $this->iterator->next();
300 
301             $this->index += 1;
302         }
303 
304         return $result;
305     }
306 }
```

## Appendix H: String Cursors

This appendix contains numerous cursor implementations developed throughout this book. For more information on cursors, see Chapter 15.

The `ClosureStringCursor` accepts arbitrary functions, which will be invoked at each position of an input string:

Figure 26.1 ClosureStringCursor Implementation 

```
 1 <?php
 2 
 3 class ClosureStringCursor extends AbstractStringCursor
 4 {
 5     protected ?Closure $callback;
 6 
 7     public function traverseUsing(Closure $callback): CursorResult
 8     {
 9         $this->callback = $callback;
10 
11         return $this->traverse();
12     }
13 
14     public function accept(
15         string $current,
16         ?string $prev = null,
17         ?string $next = null): ?bool
18     {
19         if ($this->callback == null) {
20             return false;
21         }
22 
23         return $this->callback->call($this, $current, $prev, $next);
24     }
25 }
```

The `SqlStringsCursor` is capable of extracting SQL-style single-quote strings from input text:

Figure 26.2 SqlStringsCursor Implementation 

```
 1 <?php
 2 
 3 class SqlStringsCursor extends AbstractStringCursor
 4 {
 5     public function accept(
 6         string $current,
 7         ?string $prev = null,
 8         ?string $next = null): ?bool
 9     {
10         if ($this->index > 0 && $current == "'") {
11             if ($next == "'") {
12                 return $this->advance(1)->continue();
13             }
14 
15             return $this->skip(1)->break();
16         }
17 
18         return $this->continue();
19     }
20 }
```

The `StringsCursor` is capable of extracting PHP-style single or double-quoted strings from the input text while accounting for the backslash escape sequence:

Figure 26.3 StringsCursor Implementation 

```
 1 <?php
 2 
 3 class StringsCursor extends AbstractStringCursor
 4 {
 5     public function accept(
 6         string $current,
 7         ?string $prev = null,
 8         ?string $next = null): ?bool
 9     {
10         if ($this->index > 0 &&
11             $current == $this->initialCharacter && $prev != '\\') {
12             return false;
13         }
14 
15         return true;
16     }
17 }
```

The `NumberCursor` can be used to extract PHP-style numeric values from the input text:

Figure 26.4 NumberCursor Implementation 

```
 1 <?php
 2 
 3 class NumberCursor extends  AbstractStringCursor
 4 {
 5     protected function isValidChar($char): bool
 6     {
 7         if ($char == '.' || $char == '_') {
 8             return true;
 9         }
10         if (! ctype_digit($char) || ctype_punct($char)) {
11             return false;
12         }
13 
14         return true;
15     }
16 
17     public function accept(
18         string $current,
19         ?string $prev = null,
20         ?string $next = null): ?bool
21     {
22         return $this->isValidChar($next);
23     }
24 }
```

The `VariableCursor` can be used to extract PHP-style variable names from the input text:

Figure 26.5 VariableCursor Implementation 

```
 1 <?php
 2 
 3 class VariableCursor extends AbstractStringCursor
 4 {
 5     protected function isValidChar($char)
 6     {
 7         return ctype_alnum($char) || $char == '_';
 8     }
 9 
10     public function accept(
11         string $current,
12         ?string $prev = null,
13         ?string $next = null): ?bool
14     {
15         if (! $this->isValidChar($next)) {
16             return false;
17         }
18 
19         return true;
20     }
21 }
```

The `OpenTagCursor` can be used to extract the PHP opening tag from the input text:

Figure 26.6 OpenTagCursor Implementation 

```
 1 <?php
 2 
 3 class OpenTagCursor extends AbstractStringCursor
 4 {
 5     public function accept(
 6         string $current,
 7         ?string $prev = null,
 8         ?string $next = null): ?bool
 9     {
10         if (str($this->buffer)->startsWith('<?php')) {
11             if (! ctype_space($next)) {
12                 return false;
13             }
14         }
15 
16         return true;
17     }
18 }
```

The `PairedBracketCursor` can extract strings containing paired parentheses, angle brackets, square brackets, etc.:

Figure 26.7 PairedBracketCursor Implementation 

```
 1 <?php
 2 
 3 class PairedBracketCursor extends AbstractStringCursor
 4 {
 5     private string $closingBracket = '';
 6     private string $openingBracket = '';
 7     private int $pairCount = 0;
 8 
 9     public function __construct(
10         Utf8StringIterator $iterator,
11         string $openingBracket,
12         string $closingBracket)
13     {
14         parent::__construct($iterator);
15         $this->openingBracket = $openingBracket;
16         $this->closingBracket = $closingBracket;
17     }
18 
19     public function accept(
20         string $current,
21         ?string $prev = null,
22         ?string $next = null): ?bool
23     {
24         if ($current == '"' || $current == "'") {
25             $this->buffer = $this->bufferCursorResult(
26                 new StringsCursor($this->iterator)
27             );
28 
29             return $this->continue();
30         }
31 
32         if ($this->index == 0 || $current == $this->openingBracket) {
33             $this->pairCount += 1;
34 
35             return $this->continue();
36         }
37 
38         if ($current == $this->closingBracket) {
39             $this->pairCount -= 1;
40 
41             if ($this->pairCount == 0) {
42                 return $this->break();
43             }
44         }
45 
46         return $this->continue();
47     }
48 }
```

The `CommaStringSplitter` can be used to split complex string input on the comma character, accounting for paired brackets, and nested strings:

Figure 26.8 CommaStringSplitter Implementation 

```
 1 <?php
 2 
 3 class CommaStringSplitter extends AbstractStringCursor
 4 {
 5     protected string $current = '';
 6     protected ?string $prev = null;
 7     protected ?string $next = null;
 8     protected array $strings = [];
 9 
10     protected function nextIsNull(): bool
11     {
12         return $this->next == null ||
13             $this->iterator->key() == $this->iterator->count() - 1;
14     }
15 
16     public function continue(): bool
17     {
18         if ($this->nextIsNull()) {
19             $this->strings[] = $this->flushBuffer();
20             return false;
21         }
22 
23         return true;
24     }
25 
26     public function accept(
27         string $current,
28         ?string $prev = null,
29         ?string $next = null): ?bool
30     {
31         $this->current = $current;
32         $this->prev = $prev;
33         $this->next = $next;
34 
35         if ($current == '(') {
36             return $this->append($this->bufferCursorResult(
37                 new PairedBracketCursor(
38                     $this->iterator, '(', ')'
39                 )
40             ))->continue();
41         }
42 
43         if ($current == '"' || $current == "'") {
44             return $this->append($this->bufferCursorResult(
45                 new StringsCursor($this->iterator)
46             ))->continue();
47         }
48 
49         if ($current == ',') {
50             $this->strings[] = $this->popBuffer()->flushBuffer();
51         }
52 
53         return $this->continue();
54     }
55 
56     public function getStrings(): array
57     {
58         return $this->strings;
59     }
60 }
```

The `NonWhitespaceCursor` was developed in Chapter 16, and can be used to traverse a string to the next instance of a non-whitespace character:

Figure 26.9 NonWhitespaceCursor Implementation 

```
 1 <?php
 2 
 3 class NonWhitespaceCursor extends AbstractStringCursor
 4 {
 5     public function accept($current, $prev = null, $next = null)
 6     {
 7         if (! ctype_space($current)) {
 8             return $this->break();
 9         }
10 
11         return $this->continue();
12     }
13 }
```

The `BladeDirectiveCursor` was developed in Chapter 16, and may be used to traverse to the end of a Blade directive:

Figure 26.10 BladeDirectiveCursor Implementation 

```
 1 <?php
 2 
 3 class BladeDirectiveCursor extends AbstractStringCursor
 4 {
 5     public function accept($current, $prev = null, $next = null)
 6     {
 7         if ($next == null || ctype_space($next)) {
 8             return $this->break();
 9         }
10 
11         if (ctype_punct($next) && $next != '_' && $next != '-') {
12             return $this->break();
13         }
14 
15         return $this->continue();
16     }
17 }
```

## Appendix I: Blade Directive Validator Implementation

The following code example is the full implementation of the Blade Directive validator developed in Chapter 16:

Figure 27.1 BladeDirectiveValidator Implementation 

```
  1 <?php
  2 
  3 abstract class BladeStructure
  4 {
  5     public int $startPosition = 0;
  6     public int $endPosition = 0;
  7     public int $length = 0;
  8 
  9     public int $line = 0;
 10 
 11     public function getEndOffset()
 12     {
 13         return $this->endPosition;
 14     }
 15 }
 16 
 17 class ParsedDirective extends BladeStructure
 18 {
 19     public ?ParsedArguments $args = null;
 20     public string $directiveName = '';
 21 
 22     public function getEndOffset()
 23     {
 24         if ($this->args != null && $this->args->endPosition > 0) {
 25             return $this->args->endPosition;
 26         }
 27 
 28         return $this->endPosition;
 29     }
 30 }
 31 
 32 class ParsedArguments extends BladeStructure
 33 {
 34     public string $value = '';
 35     public string $content = '';
 36 }
 37 
 38 class NonWhitespaceCursor extends AbstractStringCursor
 39 {
 40     public function accept(string $current,
 41                            ?string $prev = null,
 42                            ?string $next = null): ?bool
 43     {
 44         if (! ctype_space($current)) {
 45             return $this->break();
 46         }
 47 
 48         return $this->continue();
 49     }
 50 }
 51 
 52 class BladeDirectiveCursor extends AbstractStringCursor
 53 {
 54     public function accept(string $current,
 55                            ?string $prev = null,
 56                            ?string $next = null): ?bool
 57     {
 58         if ($next == null || ctype_space($next)) {
 59             return $this->break();
 60         }
 61 
 62         if (ctype_punct($next) && $next != '_' && $next != '-') {
 63             return $this->break();
 64         }
 65 
 66         return $this->continue();
 67     }
 68 }
 69 
 70 class BladeDirectiveValidator
 71 {
 72     protected Utf8StringIterator $string;
 73     protected BladeDirectiveCursor $directiveCursor;
 74     protected NonWhitespaceCursor $nonWhitespaceCursor;
 75     protected PairedBracketCursor $pairedBracketCursor;
 76     protected bool $hasAdvancedIterator = false;
 77     protected CharacterPositionLocator $locator;
 78     protected array $structures = [];
 79     protected int $lineOffset = 0;
 80     protected array $validators = [];
 81     protected ?int $argGroupSpacing = null;
 82 
 83     /**
 84      * The core Blade directives.
 85      *
 86      * @var string[]
 87      */
 88     protected $coreDirectives = [
 89         'can', 'cannot', 'canany', 'elsecan', 'elsecannot',
 90         'elsecanany', 'endcan', 'endcannot', 'endcanany',
 91         'class', 'component', 'endComponent', 'slot', 'endSlot',
 92         'props', 'endComponentClass', 'componentClass',
 93         'componentFirst', 'endComponentFirst', 'push', 'endPush',
 94         'aware', 'auth', 'elseAuth', 'endAuth', 'env', 'endEnv',
 95         'production', 'endProduction', 'guest', 'elseGuest',
 96         'endGuest', 'hasSection', 'if', 'unless', 'elseIf',
 97         'else', 'endIf', 'endUnless', 'isset', 'endIsset',
 98         'switch', 'case', 'default', 'endSwitch', 'once',
 99         'endOnce', 'selected', 'checked', 'disabled', 'required',
100         'readonly', 'pushIf', 'endPushIf', 'error', 'enderror',
101         'csrf', 'dd', 'dump', 'method', 'vite', 'viteReactRefresh',
102         'each', 'include', 'includeIf', 'includeWhen',
103         'includeUnless', 'includeFirst', 'inject', 'js', 'json',
104         'extends', 'extendsFirst', 'section', 'parent', 'yield',
105         'show', 'append', 'overwrite', 'stop', 'endsection',
106         'foreelse', 'empty', 'endforelse', 'endempty', 'for',
107         'foreach', 'break', 'continue', 'endfor', 'endforeach',
108         'while', 'endwhile', 'php', 'unset', 'stack', 'push',
109         'pushOnce', 'endpush', 'endpushonce', 'prepend',
110         'prependOnce', 'endprepend', 'endprependOnce', 'lang',
111         'endlang', 'choice'
112     ];
113 
114     /**
115      * A list of custom Blade directives.
116      *
117      * @var string[]
118      */
119     protected $customDirectives = [];
120 
121     /**
122      * Sets the custom directives.
123      *
124      * @param string[] $directives
125      * @return void
126      */
127     public function setCustomDirectives(array $directives)
128     {
129         $this->customDirectives = $directives;
130     }
131 
132     /**
133      * Retrieves all Blade directive names.
134      *
135      * @return string[]
136      */
137     public function getDirectiveNames()
138     {
139         return array_merge(
140             $this->coreDirectives,
141             $this->customDirectives
142         );
143     }
144 
145     /**
146      * Advances the internal iterator to the target offset.
147      *
148      * @param int $targetOffset
149      * @return void
150      */
151     private function advance($targetOffset)
152     {
153         $targetOffset -= 1;
154 
155         if ($targetOffset <= 0) { $targetOffset = 0; }
156 
157         $byteSize = $this->string->index()[$targetOffset];
158 
159         if (!$this->hasAdvancedIterator &&
160             $this->string->key() != $targetOffset) {
161             $this->hasAdvancedIterator = true;
162             $this->string->setIteratorPosition(
163                 $targetOffset,
164                 $byteSize
165             );
166         } else {
167             $this->hasAdvancedIterator = true;
168         }
169     }
170 
171     /**
172      * Fills the Blade structure details from the CursorResult.
173      *
174      * @param CursorResult $result
175      * @param BladeStructure $structure
176      * @return BladeStructure
177      */
178     protected function fillStructureDetails(CursorResult $result,
179                                             BladeStructure $structure)
180     {
181         $structure->startPosition = $result->startPosition;
182         $structure->endPosition = $result->endPosition;
183         $structure->length = $result->length;
184 
185         $location = $this->locator->getCharPosition(
186             $result->startPosition
187         );
188 
189         if ($location) {
190             $structure->line = $location->line + $this->lineOffset;
191         }
192 
193         return $structure;
194     }
195 
196     /**
197      * Parses Blade directive arguments.
198      *
199      * @param int $offset
200      * @return ParsedArguments|null
201      */
202     protected function parseArgs($offset)
203     {
204         $args = null;
205         $this->hasAdvancedIterator = false;
206 
207         foreach ($this->string as $char) {
208             if (! $this->hasAdvancedIterator) {
209                 $this->advance($offset);
210                 continue;
211             }
212 
213             // Get the argument string.
214             $result = $this->pairedBracketCursor->traverse();
215             $args = new ParsedArguments();
216             $this->fillStructureDetails($result, $args);
217             $args->content = $result->content;
218             $args->value = $result->value;
219 
220             break;
221         }
222 
223         return $args;
224     }
225 
226     /**
227      * Parses a Blade directive.
228      *
229      * @param int $offset
230      * @return ParsedDirective|null
231      */
232     protected function parseDirective($offset)
233     {
234         $directive = null;
235 
236         $this->hasAdvancedIterator = false;
237 
238         // Because this method only ever gets called
239         // from our directive index combined with
240         // our advancing logic, our starting
241         // character will always be a "@".
242         foreach ($this->string as $char) {
243             if (!$this->hasAdvancedIterator) {
244                 $this->advance($offset);
245                 continue;
246             }
247 
248             $result = $this->directiveCursor->traverse();
249 
250             $directive = new ParsedDirective();
251             $this->fillStructureDetails($result, $directive);
252 
253             if (str($result->value)->startsWith('@')) {
254                 $directive->directiveName = str($result->value)
255                                                 ->substr(1)
256                                                 ->toString();
257             } else {
258                 $directive->directiveName = $result->value;
259             }
260 
261             // Look for the next non-whitespace character
262             if ($directive->endPosition + 1 < count($this->string)) {
263                 $this->string->setIteratorPosition(
264                     $directive->endPosition + 1,
265                     $this->string->index()[$directive->endPosition + 1]
266                 );
267 
268                 $nextNonWhitespace = $this->nonWhitespaceCursor
269                                         ->traverse();
270 
271                 if (str($nextNonWhitespace->value)->endsWith('(')) {
272                     $directive->args = $this->parseArgs(
273                         $nextNonWhitespace->endPosition
274                     );
275                 }
276             }
277 
278             break;
279         }
280 
281         return $directive;
282     }
283 
284     /**
285      * Returns a copy of the string containing
286      * only spaces and newline characters.
287      *
288      * @param string $value
289      * @return string
290      */
291     protected function fillSpaces($value)
292     {
293         $string = new Utf8StringIterator($value);
294         $newString = '';
295 
296         foreach ($string as $char) {
297             if ($char == "\n") {
298                 $newString .= $char;
299                 continue;
300             }
301 
302             $newString .= ' ';
303         }
304 
305         return $newString;
306     }
307 
308     /**
309      * Prepares the input value for the parser.
310      *
311      * @param string $value
312      * @return string
313      */
314     protected function prepareInput($value)
315     {
316         $value = Str::normalizeEol($value, "\n");
317 
318         // Remove the contents of any verbatim blocks.
319         $value = preg_replace_callback(
320             '/(?<!@)@verbatim(.*?)@endverbatim/s',
321             function ($matches) {
322                 return $this->fillSpaces($matches[0]);
323             }, $value
324         );
325 
326         // Remove the contents of any PHP blocks.
327         $value = preg_replace_callback(
328             '/(?<!@)@php(.*?)@endphp/s',
329             function ($matches) {
330                 return $this->fillSpaces($matches[0]);
331             }, $value
332         );
333 
334         // Remove the contents of any Blade comments.
335         return preg_replace_callback(
336             '/{{--(.*?)--}}/s',
337             function ($matches) {
338                 return $this->fillSpaces($matches[0]);
339             }, $value
340         );
341     }
342 
343     /**
344      * Parses the provided Blade template.
345      *
346      * @param $value
347      * @return array
348      */
349     public function parse($value)
350     {
351         $value = $this->prepareInput($value);
352 
353         $htmlRegions = collect(token_get_all($value))
354             ->filter(function ($token) {
355                 return is_array($token) && $token[0] == T_INLINE_HTML;
356             })->all();
357 
358         $this->structures = [];
359         $pattern = collect($this->getDirectiveNames())
360             ->map(function ($name) {
361                 return preg_quote($name);
362             })->implode('|');
363 
364         foreach ($htmlRegions as $region) {
365             $this->lineOffset = $region[2] - 1;
366             $this->string = new Utf8StringIterator($region[1]);
367             $this->locator = new CharacterPositionLocator($region[1]);
368             $this->directiveCursor = new BladeDirectiveCursor(
369                 $this->string
370             );
371 
372             $this->pairedBracketCursor = new PairedBracketCursor(
373                 $this->string,
374                 '(', ')'
375             );
376 
377             $this->nonWhitespaceCursor = new NonWhitespaceCursor(
378                 $this->string
379             );
380 
381             preg_match_all(
382                 '/(?<!@)@(?!@)('.$pattern.')/i',
383                 $region[1], $matches,
384                 PREG_OFFSET_CAPTURE
385             );
386 
387             $directiveIndex = $matches[0];
388 
389             for ($i = 0; $i < count($directiveIndex); $i++) {
390                 $directive = $this->parseDirective(
391                     $directiveIndex[$i][1]
392                 );
393 
394                 if ($directive != null) {
395                     $this->structures[] = $directive;
396                 }
397             }
398         }
399 
400         return $this->structures;
401     }
402 
403     /**
404      * @param $value
405      * @return void
406      * @throws Exception
407      */
408     public function validate($value)
409     {
410         $structures = $this->parse($value);
411 
412         foreach ($structures as $structure) {
413             if (! $structure instanceof ParsedDirective) {
414                 continue;
415             }
416 
417             $directive = str($structure->directiveName)
418                             ->lower->toString();
419 
420             if ($structure->args != null) {
421                 $this->validateArgumentOnSameLine($structure);
422 
423                 if ($this->argGroupSpacing != null) {
424                     $spacing = $structure->args->startPosition -
425                                $structure->endPosition - 1;
426 
427                     if ($spacing !=  $this->argGroupSpacing) {
428                         throw new Exception(
429                             'Improper spacing between @' .
430                             $structure->directiveName .
431                             ' and its arguments. Expected ' .
432                             $this->argGroupSpacing.' spaces, got ' .
433                             $spacing . ' on line ' . $structure->line
434                         );
435                     }
436                 }
437             }
438 
439             if (! array_key_exists($directive, $this->validators)) {
440                 continue;
441             }
442 
443             foreach ($this->validators[$directive] as $validator) {
444                 $result = $validator($structure);
445 
446                 if (is_string($result)) {
447                     throw new Exception($result . ' on line ' .
448                         $structure->line
449                     );
450                 }
451             }
452         }
453     }
454 
455     /**
456      * @param $directive
457      * @param $validator
458      * @return void
459      */
460     public function addValidator($directive, $validator)
461     {
462         $directive = str($directive)->lower->toString();
463 
464         if (! array_key_exists($directive, $this->validators)) {
465             $this->validators[$directive] = [];
466         }
467 
468         $this->validators[$directive][] = $validator;
469     }
470 
471     /**
472      * Adds case-sensitive directive name validation.
473      *
474      * @param string|string[] $directives
475      * @return $this
476      */
477     public function mustMatchCase($directives)
478     {
479         if (! is_array($directives)) {
480             $directives = [$directives];
481         }
482 
483         foreach ($directives as $directive) {
484             $this->addValidator($directive, function ($structure)
485                                                  use ($directive) {
486                 if ($structure->directiveName != $directive) {
487                     return 'Directive @'.$structure->directiveName .
488                            ' does not match case of @' . $directive;
489                 }
490 
491                 return true;
492             });
493         }
494 
495         return $this;
496     }
497 
498     /**
499      * Adds case-sensitive validation for all core directive names.
500      *
501      * @return $this
502      */
503     public function validateCoreDirectiveCasing()
504     {
505         $this->mustMatchCase($this->coreDirectives);
506 
507         return $this;
508     }
509 
510     /**
511      * Adds validation to ensure the provided
512      * directives have an argument group.
513      *
514      * @param string|string[] $directives
515      * @return $this
516      */
517     public function shouldHaveArgs($directives)
518     {
519         if (! is_array($directives)) {
520             $directives = [$directives];
521         }
522 
523         foreach ($directives as $directive) {
524             $this->addValidator($directive, function ($structure)
525                                                  use ($directive) {
526                 if ($structure->args == null ||
527                     $structure->args->content == '') {
528                     return '@' . $directive .
529                            ' is missing required argument group';
530                 }
531 
532                 return true;
533             });
534         }
535 
536         return $this;
537     }
538 
539     /**
540      * Adds validation to ensure the provided
541      * directives do not have arguments.
542      *
543      * @param string|string[] $directives
544      * @return $this
545      */
546     public function shouldNotHaveArgs($directives)
547     {
548         if (! is_array($directives)) {
549             $directives = [$directives];
550         }
551 
552         foreach ($directives as $directive) {
553             $this->addValidator($directive, function ($structure)
554             use ($directive) {
555                 if ($structure->args != null) {
556                     return 'Unexpected argument group for @' .
557                         $directive.' directive';
558                 }
559 
560                 return true;
561             });
562         }
563 
564         return $this;
565     }
566 
567     /**
568      * @param ParsedDirective $structure
569      * @return void
570      * @throws Exception
571      */
572     protected function validateArgumentOnSameLine(
573         ParsedDirective $structure
574     )
575     {
576         if ($structure->line != $structure->args->line) {
577             throw new Exception(
578                 'Start of argument group for @' .
579                 $structure->directiveName .
580                 ' directive must be on the same line on line ' .
581                 $structure->line
582             );
583         }
584     }
585 
586     /**
587      * Adds validation to ensure specific spacing between
588      * a directive name and its argument group.
589      *
590      * @param int|null $spacing
591      * @return $this
592      */
593     public function requireArgGroupSpacing(?int $spacing)
594     {
595         $this->argGroupSpacing = $spacing;
596 
597         return $this;
598     }
599 }
```

## Appendix J: HTML Fragments Parser and Analyzer Implementation

The following code samples contain the full implementation of the HTML fragments parser and context analyzer developed in Chapter 17.

Figure 28.1 HTML Fragments Parser and Analyzer Implementation 

```
  1 <?php
  2 
  3 enum AttributeType
  4 {
  5     case Attribute;
  6     case Parameter;
  7 }
  8 
  9 enum FragmentPosition
 10 {
 11     case InsideFragment;
 12     case InsideAttribute;
 13     case InsideParameter;
 14     case InsideFragmentName;
 15     case StartOfFragment;
 16     case EndOfFragment;
 17     case Unknown;
 18 }
 19 
 20 class Fragment
 21 {
 22     public int $startPosition = 0;
 23     public int $endPosition = 0;
 24     public string $content = '';
 25 
 26     /**
 27      * Tests if the fragment contains the provided position.
 28      *
 29      * @param int $position
 30      * @return bool
 31      */
 32     public function contains(int $position): bool
 33     {
 34         return $position >= $this->startPosition &&
 35                $position <= $this->endPosition;
 36     }
 37 }
 38 
 39 class FragmentAttribute extends Fragment
 40 {
 41     public string $name = '';
 42     public string $value = '';
 43     public AttributeType $type = AttributeType::Attribute;
 44 }
 45 
 46 class HtmlFragment extends Fragment
 47 {
 48     public bool $isClosingTag = false;
 49     public bool $isSelfClosing = false;
 50     public string $documentContent = '';
 51     public ?Fragment $innerContent = null;
 52     public ?Fragment $name = null;
 53     public string $tagName = '';
 54 
 55     /**
 56      * @var FragmentAttribute[]
 57      */
 58     public array $attributes = [];
 59 }
 60 
 61 abstract class BaseFragmentParser
 62 {
 63     protected Utf8StringIterator $string;
 64     protected string $buffer = '';
 65     protected int $position = 0;
 66     protected ?string $current = null;
 67     protected ?string $next = null;
 68     protected ?string $prev = null;
 69 
 70     /**
 71      * Sets the internal state variables for the provided offset.
 72      *
 73      * @param int $offset
 74      * @return void
 75      */
 76     protected function checkCurrentOffsets(int $offset): void
 77     {
 78         $this->position = $offset;
 79         $this->current = $this->string[$offset] ?? null;
 80         $this->next = $this->string[$offset + 1] ?? null;
 81         $this->prev = $this->string[$offset - 1] ?? null;
 82     }
 83 
 84     /**
 85      * Resets the internal state variables.
 86      *
 87      * @return void
 88      */
 89     protected function resetState(): void
 90     {
 91         $this->position = 0;
 92         $this->buffer = '';
 93         $this->next = null;
 94         $this->prev = null;
 95         $this->current = null;
 96     }
 97 
 98     /**
 99      * Tests if the current position is the start of a string.
100      *
101      * @return bool
102      */
103     protected function isStartOfString(): bool
104     {
105         return $this->current == '"' || $this->current == "'";
106     }
107 
108     /**
109      * Advances the parser over a string, and adds
110      * the string's content to the internal buffer.
111      *
112      * @param int $start The start position.
113      * @return int
114      */
115     protected function scanToEndOfString(int $start): int
116     {
117         $stringStyle = $this->current;
118         $this->buffer .= $this->current;
119         $returnedOn = $start;
120 
121         for ($i = $start + 1; $i < count($this->string); $i++) {
122             $this->checkCurrentOffsets($i);
123 
124             $this->buffer .= $this->current;
125             if ($this->current == $stringStyle) {
126                 $returnedOn = $i;
127                 break;
128             }
129         }
130 
131         return $returnedOn;
132     }
133 }
134 
135 class FragmentAttributeParser extends BaseFragmentParser
136 {
137     /**
138      * Parses the fragment's inner content for attributes.
139      *
140      * @param HtmlFragment $fragment
141      * @return array
142      */
143     public function parse(HtmlFragment $fragment): array
144     {
145         $this->resetState();
146         $this->string = new Utf8StringIterator(
147             $fragment->innerContent->content
148         );
149 
150         $tempAttributes = [];
151         $attributes = [];
152 
153         for ($i = 0; $i < count($this->string); $i++) {
154             $this->checkCurrentOffsets($i);
155 
156             if (ctype_space($this->current)) {
157                 $this->buffer = '';
158                 continue;
159             }
160 
161             if ($this->isStartOfString()) {
162                 $i = $this->scanToEndOfString($i);
163                 $this->checkCurrentOffsets($i);
164             } else {
165                 $this->buffer .= $this->current;
166             }
167 
168             if ($this->next == null || ctype_space($this->next)) {
169                 $tempAttributes[] = [
170                     $this->buffer, $i
171                 ];
172 
173                 $this->buffer = '';
174                 continue;
175             }
176         }
177 
178         foreach ($tempAttributes as $tempAttribute) {
179             $attribute = new FragmentAttribute();
180 
181             $attribute->content = $tempAttribute[0];
182 
183             // Calculate the attribute's start and end
184             // positions relative to the original doc.
185             $attribute->endPosition = $tempAttribute[1] +
186                 $fragment->innerContent->startPosition;
187             $attribute->startPosition = $attribute->endPosition -
188                 str($attribute->content)->length() + 1;
189 
190             // Extract name/values, if present.
191             $parts = str($attribute->content)->explode('=', 2);
192 
193             if ($parts->count() == 2) {
194                 $attribute->type = AttributeType::Parameter;
195                 $attribute->name = $parts->first();
196                 $attribute->value = $parts->last();
197             } else {
198                 $attribute->name = $attribute->content;
199                 $attribute->type = AttributeType::Attribute;
200             }
201 
202             $attributes[] = $attribute;
203         }
204 
205         return $attributes;
206     }
207 }
208 
209 class FragmentsDocumentParser extends BaseFragmentParser
210 {
211     private FragmentAttributeParser $attributeParser;
212 
213     /**
214      * The HTML fragments within the document.
215      *
216      * @var HtmlFragment[]
217      */
218     private array $fragments = [];
219 
220     /**
221      * A list of offsets to skip.
222      *
223      * @var array
224      */
225     protected array $ignoreRanges = [];
226 
227     /**
228      * Indicates if the parser is inside a <script> element.
229      *
230      * @var bool
231      */
232     private bool $isParsingScript = false;
233 
234     public function __construct()
235     {
236         $this->attributeParser = new FragmentAttributeParser();
237     }
238 
239     /**
240      * Sets the internal ranges to ignore while parsing.
241      *
242      * @param array $ignoreRanges The ranges to ignore.
243      * @return void
244      */
245     public function setIgnoreRanges(array $ignoreRanges): void
246     {
247         $this->ignoreRanges = $ignoreRanges;
248     }
249 
250     /**
251      * Parses an HTML fragment at the provided index.
252      *
253      * @param int $index The location to begin parsing.
254      * @return void
255      */
256     private function parseFragment(int $index): void
257     {
258         $this->buffer = '';
259         $brokeEarly = false;
260 
261         for ($i = $index; $i < count($this->string); $i++) {
262             if (array_key_exists($i, $this->ignoreRanges)) {
263                 $jumpIndex = $this->ignoreRanges[$i];
264 
265                 $this->buffer .= str(' ')->repeat($jumpIndex - $i + 1);
266 
267                 $i = $jumpIndex;
268                 continue;
269             }
270             $this->checkCurrentOffsets($i);
271 
272             if (($i != $index && $this->current == '<') ||
273                 ($this->current != '>' && $this->next == null)) {
274                 $brokeEarly = true;
275                 break;
276             }
277 
278             if ($this->isStartOfString()) {
279                 $i = $this->scanToEndOfString($i);
280                 continue;
281             }
282 
283             if ($this->current == '>') {
284                 $this->buffer .= $this->current;
285                 break;
286             }
287 
288             $this->buffer .= $this->current;
289         }
290 
291         if ($brokeEarly) {
292             $this->buffer = '';
293             return;
294         }
295 
296         $fragment = new HtmlFragment();
297         $fragment->startPosition = $index;
298         $fragment->endPosition = $this->position;
299         $fragment->content = $this->buffer;
300         $fragment->isSelfClosing = str($this->buffer)->endsWith('/>');
301         $fragment->isClosingTag = str($this->buffer)->startsWith('</');
302 
303         $documentContentStartOffset = 1;
304         $documentContentEndOffset = -1;
305 
306         if ($fragment->isClosingTag) {
307             $documentContentStartOffset = 2;
308         }
309 
310         if ($fragment->isSelfClosing) {
311             $documentContentEndOffset = -2;
312         }
313 
314         $fragment->documentContent =
315             str($this->buffer)->substr(
316                 $documentContentStartOffset,
317                 $documentContentEndOffset
318             );
319 
320         // Retrieve all content before the first space.
321         $tagName = str($fragment->documentContent)->before(' ');
322         $fragment->tagName = (string) $tagName->trim();
323 
324         // Check if the tag name was an ignored region.
325         // If so, we can grab that content substring.
326         if (array_key_exists(
327             $fragment->startPosition + $documentContentStartOffset
328             , $this->ignoreRanges
329         )) {
330             $tagNameStart =
331                 $fragment->startPosition + $documentContentStartOffset;
332 
333             $tagNameEnd = $this->ignoreRanges[$tagNameStart];
334             $nameLength = $tagNameEnd - $tagNameStart + 1;
335             $fragment->tagName = str($this->string)
336                 ->substr($tagNameStart, $nameLength)->value();
337         }
338 
339         // Create a Fragment representing the name.
340         if (str($fragment->tagName)->trim()->length > 0) {
341             $fragment->name = new Fragment();
342             $fragment->name->content = $fragment->tagName;
343             $fragment->name->startPosition =
344                 $fragment->startPosition + $documentContentStartOffset;
345 
346             $fragment->name->endPosition =
347                 $fragment->name->startPosition +
348                 str($fragment->tagName)->length() - 1;
349         }
350 
351         // Calculate the start of the inner content.
352         // This will be the first space after the tag name.
353         $innerContentStart = mb_strpos($fragment->documentContent,
354             ' ');
355 
356         if ($innerContentStart !== false) {
357             $innerContentFragment = new Fragment();
358             $innerContentFragment->content =
359                 str($fragment->documentContent)
360                     ->substr($innerContentStart)
361                     ->trim();
362 
363             // Calculate the start and end positions of the
364             // inner content relative to the document.
365             $innerContentFragment->startPosition = mb_strpos(
366                     $fragment->documentContent,
367                     $innerContentFragment->content
368                 ) + 1 + $fragment->startPosition;
369 
370             if ($fragment->isClosingTag) {
371                 $innerContentFragment->startPosition += 1;
372             }
373 
374             $innerContentFragment->endPosition =
375                 $innerContentFragment->startPosition +
376                 str($innerContentFragment->content)->length();
377 
378             $fragment->innerContent = $innerContentFragment;
379         }
380 
381         $this->parseAttributes($fragment);
382 
383         if (!$fragment->isClosingTag && !$fragment->isSelfClosing &&
384             str($fragment->tagName)->lower == 'script'
385         ) {
386             $this->isParsingScript = true;
387         }
388 
389         $this->fragments[] = $fragment;
390     }
391 
392     /**
393      * Parses attributes within the provided fragment.
394      *
395      * @param HtmlFragment $fragment
396      * @return void
397      */
398     private function parseAttributes(HtmlFragment $fragment): void
399     {
400         if ($fragment->innerContent == null ||
401             str($fragment->innerContent->content)->length() == 0) {
402             return;
403         }
404 
405         $fragment->attributes = $this->attributeParser
406                                     ->parse($fragment);
407     }
408 
409     /**
410      * @return array
411      */
412     private function buildFragmentIndex(): array
413     {
414         preg_match_all('/</', $this->string,
415             $matches, PREG_OFFSET_CAPTURE);
416 
417         $fragmentStarts = [];
418 
419         foreach ($matches[0] as $match) {
420             $index = $match[1];
421             $isValid = true;
422 
423             foreach ($this->ignoreRanges as $rangeStart => $rangeEnd) {
424                 if ($index >= $rangeStart && $index <= $rangeEnd) {
425                     $isValid = false;
426                     break;
427                 }
428             }
429 
430             if ($isValid) {
431                 $fragmentStarts[] = $index;
432             }
433         }
434 
435         return $fragmentStarts;
436     }
437 
438     /**
439      * Returns the parsed fragments.
440      *
441      * @return HtmlFragment[]
442      */
443     public function getFragments(): array
444     {
445         return $this->fragments;
446     }
447 
448     /**
449      * Parses the input value and returns a list of fragments.
450      *
451      * @param string $value The value to parse.
452      * @return HtmlFragment[]
453      */
454     public function parse(string $value): array
455     {
456         $this->isParsingScript = false;
457         $this->string = new Utf8StringIterator(
458             Str::normalizeEol($value, "\n")
459         );
460 
461         // Reduce the start positions by removing
462         // those that are contained within the
463         // list of offsets to be ignored.
464         $fragmentStartIndexes = $this->buildFragmentIndex();
465         $fragmentCount = count($fragmentStartIndexes);
466 
467         for ($i = 0; $i < $fragmentCount; $i++) {
468             $this->parseFragment($fragmentStartIndexes[$i]);
469             $this->resetState();
470 
471             if ($this->isParsingScript) {
472                 for ($j = $i + 1; $j < $fragmentCount; $j++) {
473                     $start = $fragmentStartIndexes[$j];
474                     $check = str($this->string)
475                                 ->substr($start, 8)
476                                 ->lower();
477 
478                     if ($check == '</script') {
479                         $this->isParsingScript = false;
480                         $i = $j - 1;
481                         break;
482                     }
483                 }
484             }
485         }
486 
487         return $this->fragments;
488     }
489 }
490 
491 class FragmentsPositionAnalyzer
492 {
493     /**
494      * The fragments to be analyzed.
495      *
496      * @var HtmlFragment[]
497      */
498     protected array $fragments = [];
499 
500     /**
501      * Sets the HTML fragments to be analyzed.
502      *
503      * @param HtmlFragment[] $fragments
504      * @return void
505      */
506     public function setFragments(array $fragments): void
507     {
508         $this->fragments = $fragments;
509     }
510 
511     /**
512      * Retrieves the contextual location for the provided position.
513      *
514      * @param int $position
515      * @return FragmentPosition
516      */
517     public function getContext(int $position): FragmentPosition
518     {
519         $loc = FragmentPosition::Unknown;
520 
521         foreach ($this->fragments as $fragment) {
522             if ($fragment->contains($position)) {
523                 $loc = FragmentPosition::InsideFragment;
524 
525                 // Check if the position is within the
526                 // characters making up the tag start.
527                 if ($position == $fragment->startPosition ||
528                     ($fragment->isClosingTag &&
529                      $position == $fragment->startPosition + 1)) {
530                     $loc = FragmentPosition::StartOfFragment;
531                     break;
532                 }
533 
534                 // Check if the position is within the
535                 // characters making up the tag end.
536                 if ($position == $fragment->endPosition ||
537                     ($fragment->isSelfClosing &&
538                      $position == $fragment->endPosition - 1)) {
539                     $loc = FragmentPosition::EndOfFragment;
540                     break;
541                 }
542 
543                 // Check if the position is within the tag name.
544                 if ($fragment->name != null &&
545                     $fragment->name->contains($position)) {
546                     $loc = FragmentPosition::InsideFragmentName;
547                     break;
548                 }
549 
550                 // Check if the position is inside an attribute.
551                 foreach ($fragment->attributes as $attr) {
552                     if ($attr->contains($position)) {
553                         $loc = FragmentPosition::InsideAttribute;
554 
555                         if ($attr->type == AttributeType::Parameter) {
556                             $loc = FragmentPosition::InsideParameter;
557                         }
558 
559                         break;
560                     }
561                 }
562 
563                 break;
564             }
565         }
566 
567         return $loc;
568     }
569 }
```

## 備註

## 

1For more information about PHP’s removed function overloading feature, you may consult the official documentation at: https://www.php.net/manual/en/mbstring.overload.php.[↩](#chap00.xhtml#fnref-funcoverload)

2It is important to note that UTF-8 includes only the first 128 ASCII characters (0-127) and does not contain the extended ASCII character set.[↩](#chap01.xhtml#fnref-utf8ascii)

3The source of this table can be found at the following URL: [https://unicode.org/faq/utf\_bom.html#bom5](https://unicode.org/faq/utf_bom.html#bom5)[↩](#chap01.xhtml#fnref-bomsource)

4Taken from https://stillat.com/blog/2021/12/12/creating-a-content-reaction-system-with-statamic-3-and-antlers#content-development-overview[↩](#chap05.xhtml#fnref-textsource)

5Laravel utilizes Doctrine’s Inflector package under the hood and provides additional features (such as working with studly-cased words) and a simple wrapper around its features. More information about the Doctrine Inflector can be found in its GitHub repository: https://github.com/doctrine/inflector.[↩](#chap08.xhtml#fnref-doctrine)

6To configure the pluralization language, we will need to instruct Laravel to use the language within the application’s service provider. Changing the language affects other features within the framework, such as the Eloquent ORM. The official documentation provides more information on how to change the language and coverage of which features this setting impacts: https://laravel.com/docs/9.x/localization#pluralization-language.[↩](#chap08.xhtml#fnref-pluralizerdocs)

7Marc Brysbaert, “How Many Words Do We Read per Minute? A Review and Meta-Analysis of Reading Rate,” Journal of Memory and Language 109 (2019): p. 104047, https://doi.org/10.1016/j.jml.2019.104047.[↩](#chap10.xhtml#fnref-citation_wpm)

8Steve McDougall, “Behavioural Driven Development in Laravel,” Laravel News (Laravel News, September 6, 2022), https://laravel-news.com/behavioral-driven-development.[↩](#chap12.xhtml#fnref-sourcelnews)

9“Gherkin Reference,” Gherkin Reference - Cucumber Documentation, accessed September 18, 2022, https://cucumber.io/docs/gherkin/reference/.[↩](#chap12.xhtml#fnref-citegherkin)

10A Gherkin file may technically start with a comment or language header instead. We will cover both of these scenarios later on in this chapter.[↩](#chap12.xhtml#fnref-gherkstart)

11The documentation used throughout the remainder of this chapter may be located at: [https://laravel.com/docs/9.x/artisan](https://laravel.com/docs/9.x/artisan). The exact contents used for the analysis can be found at: [https://github.com/laravel/docs/blob/5b0f8c34072aa374f11fa85e968087846920d1f9/artisan.md](https://github.com/laravel/docs/blob/5b0f8c34072aa374f11fa85e968087846920d1f9/artisan.md)[↩](#chap13.xhtml#fnref-artisandocs)