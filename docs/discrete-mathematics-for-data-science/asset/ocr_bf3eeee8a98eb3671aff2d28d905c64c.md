provided that, if \( (a, b) \) is in the relation, then \( (b, a) \) is not in the relation, unless \( a = b \).

For example, the relation \( \le \) on real numbers is antisymmetric because for two numbers \( a \) and \( b \), \( a \) must equal \( b \) for \( a \le b \) and \( b \le a \).

# 7.5.5 Transitive Relations

A relation \( R \) is transitive *if and only if* for all elements of sets \( A \), \( B \), and \( C \), if \( (a, b) \) and \( (b, c) \) are in \( R \), then \( (a, c) \) is also in \( R \).

Symbolically stated, \( R \) is transitive iff:

\( aRb \land bRc \rightarrow aRc, \forall a \in A, b \in B, c \in C \)

For a single set \( A = \{ a_1 a_2 a_3 \} \), a relation \( R \) is transitive iff \( a_1 \) is related to \( a_2 \) and \( a_2 \) is related to \( a_3 \) in the same way that \( a_1 \) is related to \( a_3 \).

For example, Boston is further away than Chicago. Chicago is further away than Seattle. Therefore, Boston is further away than Seattle.

A relation \( R \) is *intransitive*, or *non-transitive*, *iff* there is at least one combination of ordered pairs, \( (a, b) \) and \( (b, c) \), in \( R \) where \( (a, c) \notin R \). So, \( a \) is related to \( b \) and \( b \) is related to similarly to \( c \), but \( a \) is definitely not related to \( c \) in the same way.\(^4\)

For example, consider that an airline has a direct route from Boston to Chicago, and from Chicago to Seattle, but not from Boston to Seattle.

For a relation \( R \) on a larger single set \( S \), suppose \( x \), \( y \), and \( z \) are any three elements of \( S \). \( R \) is a transitive relation *if and only if*