# 1 Lie group machine learning model

This chapter is divided into eight sections. The first section is the introduction. The second section presents the concepts of Lie group machine learning. The third and fourth sections describe the algebraic and geometric models of Lie group machine learning, respectively. The fifth section discusses the axiom hypothesis of Lie group machine learning. The sixth and seventh sections deal with the geometric learning algorithm and linear classifier design of Dynkin graphs, respectively. Finally, the eighth section summarises the chapter.

# 1.1 Introduction

In this chapter, the theory of Lie group is introduced into the field of machine learning, and the related concepts and model of Lie group machine learning are presented. Understanding this chapter requires relevant knowledge of topological and differential geometries, which is included in Appendix 17.1 and 17.2.

# 1.2 Concepts of Lie group machine learning

Before establishing the Lie group machine learning model, we first introduce some basic concepts of Lie group [1].

**Definition 1.1**. Semigroup: A non-empty set S satisfies the operation of the combined law. In general, this operation of semigroups is called multiplication and denoted by ·. Therefore, semigroups are denoted by (S, ·).

The generalised combined law of semigroup S means that the operation results of the arbitrary sequence $a_{1}$, $a_{2}, \dots, a_{n}$ in S and any reasonable brackets are the same. In other words, the result of the operation depends only on order of the elements instead of the brackets.

According to the definition of semigroups, the operation does not necessarily satisfy the law of commutation for the elements a and b (i.e., $ab \neq ba$). Semigroups satisfying the commutative law are called exchange semigroups. The product of n elements $a_{1}$, $a_{2}, \dots, a_{n}$ in an exchange semigroup is independent of the factor order.

**Definition 1.2**. Unitary group: Let (M, ·) be a semigroup. If $e \in M$ satisfies $ea = ae = a$ for any $a \in M$, then M is a unitary group.

**Definition 1.3**. Consider a non-empty set G that satisfies the operation of the law of association(generally termed multiplication). If an element e satisfies $ea = a$ for all $a \in G$, and if for any $a \in G, a^{\prime} \in G$ satisfies $a^{\prime}a = e$, then G is called a group.