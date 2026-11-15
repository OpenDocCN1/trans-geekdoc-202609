# Data Modeling in UML

# Chapter Outline

+   9.1 Introduction
+   9.2 Object-Orientation
+   9.3 Attributes
+   9.4 Associations
+   9.5 Set-Comparison Constraints
+   9.6 Subtyping
+   9.7 Other Constraints and Derivation Rules
+   9.8 Mapping from ORM to UML
+   9.9 Summary

# 9.1 Introduction

Although semantic approaches to information modeling appeared in the early seventies, no single approach has yet achieved universal adoption. By and large, the history of information systems modeling has been characterized by a plethora of techniques and notations, with occasional religious wars between proponents of different approaches. Each year, many new approaches would be proposed, leading to groans from academics who were charged with teaching the state of the art. This is referred to as the “YAMA” (yet another modeling approach!) or “NAMA” (not another modeling approach!) syndrome. Fig. 9.1 pictures this as a mountain of modeling methods, piled on top of one another, which nicely ties in with the Japanese meaning of “yama” (mountain), depicted as a kanji that is high in the middle and low on the ends.

While diversity is often useful, the modeling industry would benefit if practitioners used just a few standard modeling approaches, individually suited for their modeling scope, and collectively covering the tasks needed to model a wide variety of applications. This would improve communication between modelers and reduce training costs.

The rapid rise of the unified modeling language (UML) has been accompanied by claims that UML by itself is an adequate approach for modeling any software application. Some UML proponents have even been so bold as to claim that “the modeling wars are over–UML has won”. This claim has been strongly rejected by several experienced data modelers, including Dave Hay, who argues that “there is no such thing as ‘object-oriented analysis’” (Hay, 1999a), only object-oriented design, and that “UML is ... not suitable for analyzing business requirements in cooperation with business people” (Hay, 1999b).