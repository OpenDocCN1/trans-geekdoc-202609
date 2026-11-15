expression s and the argument s. A self-application function may also be part of an application, such as (λx.x λs.(s s)). In this application, the function expression is λx.x and the argument expression is λs.(s s). To evaluate this application the bound variable in the function expression body x is replaced by the argument expression giving λs.(s s).

# 12.3 APPLICABLE ORDER

In *normal order*, left-to-right, the value of a parameter is not evaluated until it is passed. The problem with this is that a concrete parameter may not exist until a function on the right is first evaluated. So, sometimes we need to first evaluate the right side. The term for this is *applicative order*.

Applicative order applies a normal order to the inner-most expression as it is needed. This is a strategy of *lazy evaluation* in which function execution is done only when needed and not earlier (aka, *call-by-need*).

With lazy evaluation there is no ongoing interim computation or need to *memoize* (cache) intermittent (iterative) results. As typical of recursive functions, laziness allows the operations of a recursive expression to accumulate as a series in memory, before being processed. While desirable for the benefits of immutable variables that are limited to a one-time assignment, this comes at a cost of higher memory usage.