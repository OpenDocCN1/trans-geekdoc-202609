Now that we have eliminated this fine point of `list-pick`, let’s look at the actual problem, the choice of inputs. The goal of the example step is to cover the input space as much as possible. We do so by picking one input per clause in the description of complex forms of data. Here this procedure suggests we pick at least two elements from each class because each data definition has two clauses. We choose ’()) and (cons ’a ’()) for the first argument, and 0 and 3 for the latter. Two choices per argument means four examples total; after all, there is no immediately obvious connection between the two arguments and no restriction in the signature.

As it turns out, only one of these pairings produces a proper result; the remaining ones choose a position that does not exist because the list doesn’t contain enough symbols:

```
(check-error (list-pick '() 0) "list too short")
(check-expect (list-pick (cons 'a '()) 0) 'a
(check-error (list-pick '() 3) "list too short")
```

The function is expected to signal an error, and we pick our favorite message here.

Stop! Put these fragments into DrRacket’s definitions area and run the partial program.

The discussion on examples indicates that there are indeed four independent cases that we must inspect for the design of the function. One way to discover these cases is to arrange the conditions for each of the clauses into a two-dimensional table:

| | (empty? 1) | (cons? 1) |
|---|---|---|
| (= n 0) | | |
| (> n 0) | | |

The horizontal dimension of the table lists those questions that `list-pick` must ask about lists; the vertical dimension lists the questions about natural numbers. By this arrangement, we naturally get four squares, where each represents the case when both the conditions on the horizontal and the vertical axis are true.

Our table suggests that the `cond` for the function template has four clauses. We can figure out the appropriate condition for each of these clauses by and-ing