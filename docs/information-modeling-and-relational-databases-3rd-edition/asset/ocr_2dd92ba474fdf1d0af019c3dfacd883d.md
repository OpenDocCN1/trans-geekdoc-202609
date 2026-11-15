+   * The cutely named *Markdown* is a lightweight language that is used to add formatting indicators to textual documents. The marked document can be used in various applications to generate publishing formats such as PDF and convert to other formats such as a complete static website. However, it is obviously limited in its capability to express data structures.

+   * *AsciiDoc* is a plain text equivalent to the XML-based DocBook format used for structured documents. Documents can be created simply using a text editor and then rendered to a desired final format, such as PDF, HTML, and many others.

+   * *MediaWiki* is another lightweight language designed for ease of use. As the name suggests, it was developed for the creation of Wiki pages and is the basis for Wikipedia. As with other languages of this type, its documents can be re-processed into many other formats, including HTML.

The main purpose of most of these languages is to define the structure of documents, not the structure of data. Although there is a certain amount of overlap, there is no pressing need to use these languages for data description when better alternatives are available. We will therefore not explore them any further in this chapter.

# # 16.5 XML, JSON, and ORM

A question worth considering is whether object-role modeling (ORM) can be used to design an XML schema or a JSON schema, in much the same way that it can be used to design a relational schema. The answer is certainly “Yes”, but there are some additional considerations that are not relevant in the relational case.

As already mentioned, an ORM model can be represented in XML, and this indeed is the default file format used by the NORMA tool. The general structure can be outlined as follows:

```
```
<ORMModel>
  <Objects>
    <Object id = 123 ...> </ObjectType>
    <Object id = 456 ...> </ObjectType>
      ...
  </Objects>
  <Facts>
    <Fact id = 321 ...>
      <FactRole id = 789 ...> </FactRole>
      <FactRole id = 987 ...> </FactRole>
    </Fact>
      ...
  </Facts>
  <Constraints> ... </Constraints>
    ...
  <ORMDiagram> ... </ORMDiagram>
</ORMModel>
```
```