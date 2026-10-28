![](bbox=[0.269, 0.082, 0.763, 0.256])

excerpt contains the RML-star rule that generates the triple with the reified property dct:subject (Lines 1 to 16) and the rule to generate one annotation (Lines 18 to 33). Lines 2 to 6 indicate an iteration over every ER in the JSON file. Lines 7 to 9 define the id of the ER as a subject for the triple. Lines 10 to 16 define the predicate for this subject (dct:subject) and multiple objects. These multiple objects are the set of concepts obtained from the JSON data. They are DBpedia resources treated as IRIs. Lines 19 to 23 again iterate over every ER in the JSON file. This time to generate the annotation. Lines 24 to 26 show that :ER_concept_link, that is the name of the first rule, is now the subject. Lines 27 to 33 define the annotation of the pageRank score, taken from the JSON under the attribute “norm_pageRank”. In a similar way, the annotation for cosineSimilarity is generated.

We use Morph-KGC [11] as mapper to generate the RDF triples. Morph-KGC was able to generate the four versions of our KG through the four mappings including the RML-star mapping.

```
```text
1  :ER_concept_link a rr:TriplesMap;
2      rml:logicalSource [
3          rml:source "json/ER/normal.json";
4          rml:referenceFormulation ql:JSONPath;
5          rml:iterator "$.resources[*]";
6      ];
7      rr:subjectMap [
8          rr:template "https://unknown.com/resource/{id}";
9      ];
10     rr:predicateObjectMap [
11         rr:predicate dct:subject;
12         rr:objectMap [
13             rml:reference "concepts.dbPediaIri";
14             rr:termType rr:IRI;
15         ]
16     ].
17
18 :ER_concept_context a rr:TriplesMap;
19     rml:logicalSource [
20         rml:source "json/ER/ER_0.json";
21         rml:referenceFormulation ql:JSONPath;
22         rml:iterator "$.resources[*]";
23     ];
24     rml:subjectMap [
25         rml:quotedTriplesMap :ER_concept_link;
26     ];
27     rr:predicateObjectMap [
```
```