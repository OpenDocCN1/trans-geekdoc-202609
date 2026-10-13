
The data structure for a particular universe of discourse (UoD) can be defined by a schema. The XML Schema standard provides a means of defining the structure, content, and semantics of XML documents. It replaces the earlier document type definitions (DTDs) used to define structure. An XML document can be validated against a schema to ensure that its structure is consistent. Like SQL, XML defines a variety of data types, although these do not correspond exactly. The SQL specification (part 14) defines a mapping between XML Schema and SQL datatypes, but XML Schema is a complex topic, and we will not examine it in detail in this chapter.

## XML Structure

The crucial distinction between relational and XML data is that XML structure is inherently hierarchical. This is a consequence of the expression of the structure as items embedded within other items. [Fig. 16.1](#Ch016_831-873_B9780443237904000207.xhtml#f0010) illustrates this with a simple list of items. XML has a more complex syntax, but the principle is the same. As the figure shows, a natural interpretation of embedding one item within another is that a contained item becomes a child of the containing item.

![Fig. 16.1 Hierarchies: (a) List with embedded items. (b) Interpretation as a hierarchy.](images/B9780443237904000207/f16-01-9780443237904.jpg)

[Fig. 16.1](#Ch016_831-873_B9780443237904000207.xhtml#B-f0010) Hierarchies: (a) List with embedded items. (b) Interpretation as a hierarchy.

Interestingly, early hierarchical database systems were commercially successful—with IBM’s IMS being a prominent example—before they became overtaken by later developments. The rigidity of these earlier hierarchical systems proved to be uncompetitive against alternatives (especially the relational model) and so they became obsolete. XML does not set out to imitate these earlier systems, but there seems to be something compelling about the hierarchical notion that just won’t go away. Some differences in structure between relational and XML structure are summarized in [Table 16.1](#Ch016_831-873_B9780443237904000207.xhtml#t0010).

[Table 16.1](#Ch016_831-873_B9780443237904000207.xhtml#B-t0010)

Some differences between relational and XML structured data.

| ![t16-01-9780443237904](images/B9780443237904000207/t16-01-9780443237904.jpg) |

| --- |

The directory structure of most operating systems provides a familiar example of a hierarchy. Even in a graphical interface, we have become used to a system of “folders” that can contain a combination of other “folders” and leaf nodes called “files”. The file system analogy is particularly relevant here because the XPath/XQuery expressions used to navigate the XML structures resemble the textual commands used to navigate directory structures in environments that aren’t based on a graphical user interface (GUI). The basic hierarchy concepts are shown in [Fig. 16.2](#Ch016_831-873_B9780443237904000207.xhtml#f0015).

![Fig. 16.2 A node in a hierarchy.](images/B9780443237904000207/f16-02-9780443237904.jpg)

[Fig. 16.2](#Ch016_831-873_B9780443237904000207.xhtml#B-f0015) A node in a hierarchy.

We’re going to be navigating from node Q, which provides the “context” for our path expression. Node Q might be at the top of the hierarchy we’re considering, in which case it can be taken to represent the whole of our XML document. Apart from that special case, we can always go up one level from Q to the node P, the `parent` of Q. If Q has `siblings` (nodes that also have the parent P), we can navigate sideways. If Q has `children`, then we can navigate down. Some combination of up/sideways/down movements can take us to a new node. Once we get there, the newly selected node can become the context for some other navigation.

Most of the time, we’re going to be concerned with relationships between XML elements, so, for example, we might want to know about all elements that are “contained in” element Q (i.e., they are descendent nodes of the node Q). But we might also want to know about all elements that have some specific attribute, all elements related to some specific namespace, and so on. All these possible dimensions are known in XPath/XQuery as `axes`, and the languages provide a sophisticated notation for the precise definition of navigation along various combinations of axes. Unfortunately, the full notation is a little cumbersome. Fortunately, there are short-form notations that cover the main possibilities, and we’ll concentrate on those.

Nodes or “Elements” are identified in XML with a pair of named tags (opening and closing). Nodes can have zero or more attributes, which are listed in the opening tag. Each opened tag must ultimately be closed after all the content of the tag has been listed. The following XML expression shows an example:

```
<movie movieNr=“1”> <title> Cosmology </title> </movie>
```

Here, we have a tag named “movie” with one attribute, `movieNr`, that contains data. It contains another tag named `title`, which itself contains some data. The closing tag repeats the tag name preceded by a *solidus* or *slash* character. Optionally, elements that contain no other elements can be closed with just a single solidus character following any attributes, as in the following.

```
<movie movieNr=“1” />
```

The guidelines for choosing between attribute or element content as the location for data are a little vague. Broadly speaking, attributes are supposed to be for intrinsic properties of the node, but this is open to interpretation. It's certainly true that the following representation is just as valid, syntactically, as the first.

```
<movie title=“Cosmology”> <movieNr> 1 </movieNr> </movie>
```

In many cases, finding a path to the relevant node or nodes is all that's necessary to extract relevant data from XML. The required path can be specified using an XPath expression. To provide some concrete examples, we’ll return to the *Movies* example from [Chapter 1](#Ch001_1-25_B9780443237904000062.xhtml). There, we saw how the content of a report could be captured as relational tables. [Listing 16.1](#Ch016_831-873_B9780443237904000207.xhtml#f0035) shows similar information (with slightly different data from the example in [Chapter 1](#Ch001_1-25_B9780443237904000062.xhtml)). The initial tag simply identifies this as an XML document. This listing is a lot more verbose than an equivalent rendering in, say, a CSV file, but that's the price that must be paid to achieve the expressiveness necessary to represent complex data structures.

![Listing 16.1 Movie information in XML.](images/B9780443237904000207/f16-06-9780443237904.jpg)

[Listing 16.1](#Ch016_831-873_B9780443237904000207.xhtml#B-f0035) Movie information in XML.

Navigation is relative to a given node in an XPath sequence. The basic navigational notation resembles that of a conventional file system. A *period* or *full stop* “ . ” means “the current node”, “ .. ” means “the parent of the current node”. A *slash* or *solidus* character “ / ” without further qualification means “go down one level”; “ // ” means go down any number of levels. Names are taken to refer to elements unless prefixed with “@”, in which case they refer to attributes. At any step in the path, a predicate can be introduced in square brackets. This will filter the resulting nodes, so only those for which the predicate is “True” will be included. [Table 16.2](#Ch016_831-873_B9780443237904000207.xhtml#t0015) shows some typical expressions that use these concepts.

[Table 16.2](#Ch016_831-873_B9780443237904000207.xhtml#B-t0015)

Example path expressions.

| ![t16-02-9780443237904](images/B9780443237904000207/t16-02-9780443237904.jpg) |

| --- |
