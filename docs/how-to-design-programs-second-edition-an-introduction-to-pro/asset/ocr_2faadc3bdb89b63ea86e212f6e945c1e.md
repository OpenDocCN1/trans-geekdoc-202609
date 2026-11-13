Programming with enumerations is mostly straightforward. When a function’s input is a class of data whose description spells out its elements on a case-by-case basis, the function should distinguish just those cases and compute the result on a percease basis. For example, if you wanted to define a function that computes the next state of a traffic light, given the current state as an element of TrafficLight, you would come up with a definition like this one:

```
```lisp
; TrafficLight -> TrafficLight
; yields the next state given current state s
(check-expect (traffic-light-next "red") "green")
(define (traffic-light-next s)
 (cond
  [(string=? "red" s) "green"]
  [(string=? "green" s) "yellow"]
  [(string=? "yellow" s) "red"]]))
```
```

Because the data definition for TrafficLight consists of three distinct elements, the traffic-light-next function naturally distinguishes between three different cases. For each case, the result expression is just another string, the one that corresponds to the next case.

**Exercise 50.** If you copy and paste the above function definition into the definitions area of DrRacket and click RUN, DrRacket highlights two of the three cond lines. This coloring tells you that your test cases do not cover the full conditional. Add enough tests to make DrRacket happy.

**Exercise 51.** Design a big-bang program that simulates a traffic light for a given duration. The program renders the state of a traffic light as a solid circle of the appropriate color, and it changes state on every clock tick. What is the most appropriate initial state? Ask your engineering friends.

The main idea of an enumeration is that it defines a collection of data as a finite number of pieces of data. Each item explicitly spells out which piece of data belongs to the class of data that we are defining. Usually, the piece of data is just shown as is; on some occasions, the item of an enumeration is an English sentence that describes a finite number of elements of pieces of data with a