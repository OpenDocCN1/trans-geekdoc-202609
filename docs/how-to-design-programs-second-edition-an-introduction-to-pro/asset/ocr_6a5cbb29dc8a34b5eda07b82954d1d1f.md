Although this idea is functionally correct, it makes the assumption that the cost of *SL-provided operations is a fixed constant. If `length` is more like how-many, however, `searchS` is going to be slower than `searchL`. Using our new terminology, `searchL` is using O(n) recursive steps while `searchS` needs O(n^2) steps for a list of n items. In short, using arbitrary *SL operations to formulate conditions may shift performance from one class of functions to one that is much worse.

Let’s wrap up this intermezzo with an experiment that checks whether `length` is a constant-time function or whether it consumes time proportionally to the length of the given list. The easiest way is to define a program that creates a long list and determines how much time each version of the search program takes:

```
```
; N -> [List Number Number]
; how long do searchS and searchL take
; to look for n in (list 0 ... (- n 1))
(define (timing n)
  (local ((define long-list
            (build-list n (lambda (x) x))))
    (list
     (time (searchS n long-list))
     (time (searchL n long-list)))))
```
```

Now run this program on 10000 and 20000. If `length` is like `empty?`, the times for the second run will be roughly twice those of the first one; otherwise, the time for `searchS` will increase dramatically.

Stop! Conduct the experiment.

Assuming you have completed the experiment, you now know that `length` takes time proportionally to the size of the given list. The “S” in `searchS` stands for “squared” because its running time is O(n^2). But don’t jump to the conclusion that this kind of reasoning holds for every programming language you will encounter. Many deal with containers differently than *SL. Understanding how this is done requires one more design concept, accumulators, the concern of the final part of this book.