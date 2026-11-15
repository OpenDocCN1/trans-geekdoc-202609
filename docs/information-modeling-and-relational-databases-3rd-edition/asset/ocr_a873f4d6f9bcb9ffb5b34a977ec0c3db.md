![](bbox=[0.303, 0.097, 0.678, 0.206])

For each Folder and FileName,
at most one File is in that Folder and has that FileName.

FIG. 5.18 File has a compound reference scheme.

![](bbox=[0.283, 0.306, 0.747, 0.563])

FIG. 5.19 The previous schema populated with references and elementary facts.

Using icons for entities, the reference types File is in Folder and File has FileName are populated as shown. In the fact table for File has Size, the file entries appear as value pairs. Although not apparent in the diagram, these are ordered (Folder, FileName) in the same order as the reference types were added to the schema—an ORM tool can display this order on request.

If the reference predicates are included in the definite descriptions for the files, any order can be used. For example, “the File that is in Folder ‘MyDocs’ and has FileName ‘flag.vsd’” is equivalent to “the File that has FileName ‘flag.vsd’ and is in Folder ‘MyDocs.’” In general, compound reference schemes involve a mandatory 1:1 map of objects to a tuple of two or more values.

Textually, a compound reference scheme for an object type A may be declared by listing the reference types, with the leading A removed, in parentheses after A. The relevant uniqueness and mandatory constraints on reference predicates are assumed, and if the reference schemes are declared first, the facts may be stated in shortened form. For example, the sample model may be specified textually as follows: