programmer’s productivity. Hence, this part introduces design recipes for creating and using abstractions.

+   • Intermezzo 3 plays two roles. On the one hand, it injects the concept of lexical scope, the idea that a programming language ties every occurrence of a name to a definition that a programmer can find with an inspection of the code. On the other hand, it explains a library with additional mechanisms for abstraction, including so-called for loops.

+   • Part IV generalizes part II and explicitly introduces the idea of iterative refinement into the catalog of design concepts.

+   • Intermezzo 4 explains and illustrates why decimal numbers work in such strange ways in all programming languages. Every budding programmer ought to know these basic facts.

+   • Part V adds a new design principle. While structural design and abstraction suffice for most problems that programmers encounter, they occasionally lead to insufficiently “performant” programs. That is, structurally designed programs might need too much time or energy to compute the desired answers. Computer scientists therefore replace structurally designed programs with programs that benefit from ad hoc insights into the problem domain. This part of the book shows how to design a large class of just such programs.

+   • Intermezzo 5 uses examples from part V to illustrate how computer scientists think about performance.

+   • Part VI adds one final trick to the toolbox of designers: accumulators. Roughly speaking, an accumulator adds “memory” to a function. The addition of memory greatly improves the performance of structurally designed functions from the first four parts of the book. For the ad hoc programs from part V, accumulators can make the difference between finding an answer and never finding one.

The Epilogue is both an assessment and a look ahead to what’s next.

Independent readers ought to work through the entire book, from the first