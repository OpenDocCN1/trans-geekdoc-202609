
# Knowledge Representation Overview

## Approaches to Mental Objects

The second approach is a first-order theory in which mental objects are fluents. Davis (2005) and Davis and Morgenstern (2005) describe this approach. It relies on the possible-worlds formalism, and builds on work by Robert Moore (1980, 1985).

The third approach is a syntactic theory, in which mental objects are represented by character strings. A string is just a complex term denoting a list of symbols, so `CanFly(Clark)` can be represented by the list of symbols `\[C, a,n, F, l,y,(, C, l, a, r, k,)\]`. The syntactic theory of mental objects was first studied in depth by Kaplan and Montague (1960), who showed that it led to paradoxes if not handled carefully. Ernie Davis (1990) provides an excellent comparison of the syntactic and modal theories of knowledge. Pnueli (1977) describes a temporal logic used to reason about programs, work that won him the Turing Award and which was expanded upon by Vardi (1996). Littman et al. (2017) show that a temporal logic can be a good language for specifying goals to a reinforcement learning robot in a way that is easy for a human to specify, and generalizes well to different environments.

## Semantic Networks and Frames

The Greek philosopher Porphyry (c. 234–305 CE), commenting on Aristotle’s Categories, drew what might qualify as the first semantic network. Charles S. Peirce (1909) developed existential graphs as the first semantic network formalism using modern logic. Ross Quillian (1961), driven by an interest in human memory and language processing, initiated work on semantic networks within AI. An influential paper by Marvin Minsky (1975) presented a version of semantic networks called frames; a frame was a representation of an object or category, with attributes and relations to other objects or categories.

## Semantics in Knowledge Representation

The question of semantics arose quite acutely with respect to Quillian’s semantic networks (and those of others who followed his approach), with their ubiquitous and very vague “`IS-A` links.” Bill Woods’s (1975) famous article “What’s In a Link?” drew the attention of AI researchers to the need for precise semantics in knowledge representation formalisms. Ron Brachman (1979) elaborated on this point and proposed solutions. Patrick Hayes’s (1979) “The Logic of Frames” cut even deeper, claiming that “Most of ‘frames’ is just a new syntax for parts of first-order logic.” Drew McDermott’s (1978b) “Tarskian Semantics, or, No Notation without Denotation!” argued that the model-theoretic approach to semantics used in first-order logic should be applied to all knowledge representation formalisms. This remains a controversial idea; notably, McDermott himself has reversed his position in “A Critique of Pure Reason” (McDermott, 1987). Selman and Levesque (1993) discuss the complexity of inheritance with exceptions, showing that in most formulations it is NP-complete.

## Description Logics

Description logics were developed as a useful subset of first-order logic for which inference is computationally tractable. Hector Levesque and Ron Brachman (1987) showed that certain uses of disjunction and negation were primarily responsible for the intractability of logical inference. This led to a better understanding of the interaction between complexity and expressiveness in reasoning systems. Calvanese et al. (1999) summarize the state of the art, and Baader et al. (2007) present a comprehensive handbook of description logic.

## Nonmonotonic Inference

The three main formalisms for dealing with nonmonotonic inference—circumscription (McCarthy, 1980), default logic (Reiter, 1980), and modal nonmonotonic logic (McDermott and Doyle, 1980)—were all introduced in one special issue of the AI Journal. Delgrande and Schaub (2003) discuss the merits of the variants, given 25 years of hindsight. Answer set programming can be seen as an extension of negation as failure or as a refinement of circumscription; the underlying theory of stable model semantics was introduced by Gelfond and Lifschitz (1988), and the leading answer set programming systems are `DLV` (Eiter et al.,1998) and `S MODELS` (Niemela et al., 2000). Brewka et al. (1997) give a good overview of the various approaches to nonmonotonic logic. Clark (1978) covers the negation-as-failure approach to logic programming and Clark completion. Lifschitz (2001) discusses the application of answer set programming to planning. A variety of nonmonotonic reasoning systems based on logic programming are documented in the proceedings of the conferences on Logic Programming and Nonmonotonic Reasoning (`LPNMR`).

## Truth Maintenance Systems

The study of truth maintenance systems began with the `TMS` (Doyle, 1979) and `RUP` (McAllester, 1980) systems, both of which were essentially `JTMSs`. Forbus and de Kleer (1993) explain in depth how `TMSs` can be used in AI applications. Nayak and Williams (1997) show how an efficient incremental `TMS` called an `ITMS` makes it feasible to plan the operations of a NASA spacecraft in real time.

## Omitted Topics

This chapter could not cover every area of knowledge representation in depth. The three principal topics omitted are the following:

### Qualitative Physics

Qualitative physics is a subfield of knowledge representation concerned specifically with constructing a logical, nonnumeric theory of physical objects and processes. The term was coined by Johan de Kleer (1975), although the enterprise could be said to have started in Fahlman’s (1974) `BUILD`, a sophisticated planner for constructing complex towers of blocks. Fahlman discovered in the process of designing it that most of the effort (80%, by his estimate) went into modeling the physics of the blocks world to calculate the stability of various subassemblies of blocks, rather than into planning per se. He sketches a hypothetical naive-physics-like process to explain why young children can solve `BUILD-like` problems without access to the high-speed floating-point arithmetic used in `BUILD`’s physical modeling. Hayes (1985a) uses “histories”—four-dimensional slices of space-time similar to Davidson’s events—to construct a fairly complex naive physics of liquids. Davis (2008) gives an update to the ontology of liquids that describes the pouring of liquids into containers.

*Qualitative physics*

De Kleer and Brown (1985), Ken Forbus (1985), and Benjamin Kuipers (1985) independently and almost simultaneously developed systems that can reason about a physical system based on qualitative abstractions of the underlying equations. Qualitative physics soon developed to the point where it became possible to analyze an impressive variety of complex physical systems (Yip, 1991). Qualitative techniques have been used to construct novel designs for clocks, windshield wipers, and six-legged walkers (Subramanian and Wang, 1994). The collection Readings in Qualitative Reasoning about Physical Systems (Weld and de Kleer, 1990), an encyclopedia article by Kuipers (2001), and a handbook article by Davis (2007) provide good introductions to the field.

### Spatial Reasoning

The reasoning necessary to navigate in the wumpus world is trivial in comparison to the rich spatial structure of the real world. The earliest serious attempt to capture commonsense reasoning about space appears in the work of Ernest Davis (1986, 1990). The region connection calculus of Cohn et al. (1997) supports a form of qualitative spatial reasoning and has led to new kinds of geographical information systems; see also (Davis, 2006). As with qualitative physics, an agent can go a long way, so to speak, without resorting to a full metric representation.

*Spatial reasoning*
