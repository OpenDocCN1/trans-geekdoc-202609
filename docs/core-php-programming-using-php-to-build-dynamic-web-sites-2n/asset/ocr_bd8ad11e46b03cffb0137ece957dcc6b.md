# Core PHP Programming

proposed a solution in his white paper "The Design of a Robust Persistence Layer for Relational Databases" <http://www.ambysoft.com/persistenceLayer.html>. A careful analysis of the problems is explored as well as a detailed design, neither of which I can do justice to in the context of this chapter.

An abstraction layer trades some performance in favor of robustness. Certain unique, high-performance features of each database must must be abandoned. The abstraction layer will provide the common set of functionality. But what you gain is independence from any particular database.