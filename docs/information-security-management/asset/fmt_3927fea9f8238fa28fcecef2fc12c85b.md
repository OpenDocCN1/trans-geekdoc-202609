
# 6.1.5 Programming Languages and Resource Files

High-level languages are usually divided between interpreted and compiled languages. Compiled languages include COBOL, Pascal, “C,” and C++. Interpreted languages include Python and JavaScript (and variations such as Angular.js), and there are hybrid languages such Java and Visual Basic.NET. All of these are considered “high-level” languages because their program instructions are in the human-constructed form of source code. Source code must be transformed into an executable that the computer OS can understand. For compiled languages, the compiler does this transformation, along with its linker/loader to pull in libraries of other code functions or objects. This is translated yet again by an assembler at the lowest layer of programming logic, which consists of groupings of 0s and 1s called machine language. This becomes the executable. The executable machine code can be loaded into memory and run when called upon by the CPU on behalf of another program or as initiated by a user.

As you might imagine then, there are differences between compiled and interpreted programs in how this transformation is done. Interpreted code is parsed line-by-line and executed at the same time by an “interpreter” program. Scripts, such as JavaScript and all its variations, are interpreted by a browser, for example. Hybrids like Java use both a compiler and interpreter. The main goal here is that the compiler transforms the source code into intermediate (byte) code, which is then interpreted as it runs. This construction allows for language portability across different OSs, and it executes faster than purely interpreted code. Resource files include JavaScript Object Notation (JSON) and Yet Another Markup Language (YAML). JSON is a text file with a defined syntax that is used for defining, storing, and transporting data among applications and automation tools. YAML is also a text file that has a defined syntax and is commonly used for defining configurations for applications and automation tools and is a superset of JSON. There are many others, but the common attribute is that they allow people to define and declare resources in human-readable text files that can be operated upon by some other application.

# 6.1.6 RDF and Ontology Markup

The W3C standards body embarked on a revolutionary way to reorganize information in the web and coined the “Semantic Web.” Semantics is a name given to a group of technologies that evolved from XML to provide enriched and better-contextualized information, thus enhancing the human ability to make meaning out of the information. As such, a type of markup called Resource Description Framework (RDF) was developed to provide more relational intelligence (semantics) in web systems. In other words, RDF is based on hierarchical XML, but it is an attempt to make better use of metadata (data about data) by extending the markup to form relationships among documents. It is, if you will, a relational form of XML of sorts.

For example, using the technology of search engines, if we were going to write a research paper, we might first do a search using keywords on the topic. A typical search engine would sift through metadata looking for keywords or combinations of keywords, cross linkages, and other cues that might help match, and then we would receive back from the search engine lists of links, many of which might not be relevant. RDF, on the other hand, establishes internally defined relationships among documents by embedded Uniform Resource Identifiers (URIs), and the relationships among documents are expressed in triples: subject, predicate, and object. With RDF statements, I might make assertions in three separate but interconnected or linked RDF documents such that:

1.  Michael is a university professor.

    1.  A university professor conducts research and teaches.

    2.  A university professor provides academic services to the community.

2.  Michael researches and teaches information security for managers.

    1.  Teaching occurs both on campus and online.

    2.  Teaching includes cybersecurity training, laboratories, and simulations.

        1.  Training is the process of inculcating important knowledge.

        2.  Laboratories are activities to practice with learned applications.

        3.  Simulations are types of online games that have a learning objective.

3.  Michael has an office in the Harrington Building.

    1.  The Harrington Building is on the campus of Texas A&M University.

    2.  Texas A&M University is located in College Station, Texas.

Beyond the relational aspects of RDF markup, ontologies have evolved to organize bodies of related information and provide semantic rules with context, as illustrated in the differences between these two sentences: Wave to the crowd versus Let’s catch the next wave. While ontologies and ontology markup are beyond the scope of this text because they require an extensive understanding of programming concepts, we will briefly mention them here because they are important for technology managers to consider in terms of security as this technology evolves. An ontology in the context of our text is a controlled vocabulary in a specific knowledge domain that provides structure for representing concepts, properties, and allowable values for the concepts. As indicated, ontologies are created using a markup language, and documents are linked together with URIs. URIs resemble URLs in that they are used by browsers to find webpages, but they differ in some subtle ways—in particular, URIs extend beyond webpages to include other media.
