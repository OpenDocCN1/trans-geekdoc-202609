you're relying heavily on value-centric analogies. If you're watching a movie and you start subconsciously categorizing the different characters into “types,” that's value-centric abstraction.

# PROGRAM-CENTRIC ANALOGY

Crucially, there's more to cognition than the kind of immediate, approximative, intuitive categorization that value-centric analogy enables. There's another type of abstraction-generation mechanism that's slower, exact, deliberate: program-centric (or structure-centric) analogy.

In software engineering, you often write different functions or classes that seem to have a lot in common. When you notice these redundancies, you start asking, “could there be a more abstract function that performs the same job, that could be reused twice? Could there be an abstract base class that both of my classes could inherit from?” The definition of abstraction you're using here corresponds to program-centric analogy. You're not trying to compare your classes and functions by how similar they look, the way you'd compare two human faces, via an implicit distance function. Rather, you're interested in whether there are parts of them that have exactly the same structure. You're looking for what is called a subgraph isomorphism (see figure 14.10): programs can be represented as graphs of operators, and you're trying to find subgraphs (program subsets) that are exactly shared across your different programs.

![](bbox=[0.15, 0.48, 0.9, 0.76])

Figure 14.10 Program-centric analogy identifies and isolates isomorphic substructures across different instances

This kind of analogy-making via exact structural match within different discrete structures isn't at all exclusive to specialized fields like computer science or mathematics—you're constantly using it without noticing. It underlies reasoning, planning, and the