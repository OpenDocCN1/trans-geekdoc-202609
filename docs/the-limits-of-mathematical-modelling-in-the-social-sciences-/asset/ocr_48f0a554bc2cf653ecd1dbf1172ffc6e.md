# Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit 35

axiomatizable systems in classical analysis. In the case of our axiomatic system $T$, we can represent its proofs by a Turing machine $M_T$ that halts whenever one of its theorems $\xi$ (or a decidable sentence) is input; if we input an undecidable sentence $\zeta$, $M_T(\zeta)$ will never halt over it.

If $M_T$ halts over $\xi$, then we can explicitly obtain a Diophantine equation $p(m_\xi, x_1, \dots) = 0$, which has solutions ($m_\xi$ is a Gödel number for $\xi$); if $M_T$ doesn't halt over $\zeta$, then $p(m_\zeta, \dots) = 0$ has no integer solutions. Therefore, with the help of Richardson's maps, we can code within the language of classical analysis the whole deductive machinery of an axiomatizable formal system.

The thing turns out to be wide-ranging. Out of a suggestion by Suppes we proved a general undecidability and incomplete theorem — a Rice-like theorem within classical analysis (see Proposition 15.1). Let $P$ be an arbitrary nontrivial property in the language of analysis. The blueprint for our undecidable sentences out of those constructions is informally:

# Proposition 11.1. *There is a term-expression $\zeta$ in the language of analysis such that neither $T \vdash P\zeta$ nor $T \vdash 
eg P\zeta$.*

There is a corresponding result, and the associated decision problems can be made as high as one wishes in the arithmetic hierarchy, and even beyond (da Costa and Doria, 1994a). See below.

# 12. Generalized incompleteness

This is a technical section. Notation is standard. We follow here da Costa and Doria (2007) and some previous papers where these questions have been introduced and discussed such as da Costa and Doria (1991a, 2005). We deal (among other objects) with algorithmic functions here. These are given by their programs coded in Gödel numbers $e$ (see Rogers, 1967). We will sometimes use Turing machines (noted

12A property that isn't satisfied by either all or none of the objects in its domain.