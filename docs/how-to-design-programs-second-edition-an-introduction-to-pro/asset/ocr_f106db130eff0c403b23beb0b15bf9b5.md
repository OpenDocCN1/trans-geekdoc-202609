+   • Finally, here is one where the missile is about to collide with the UFO:

```
(make-fired (make-posn 20 100)
(make-tank 100 3)
(make-posn 22 103))
```

This example assumes that the canvas is more than 100 pixels tall.

Notice that the first instance of SIGS is generated according to the first clause of the data definition, and the second and third follow the second clause. Naturally the numbers in each field depend on your choices for global game constants.

**Exercise 95.** Explain why the three instances are generated according to the first or second clause of the data definition.

**Exercise 96.** Sketch how each of the three game states could be rendered assuming a 200 × 200 canvas.

**The Design Recipe** With a new way of formulating data definitions comes an inspection of the design recipe. This chapter introduces a way to combine two or more means of describing data, and the revised design recipe reflects this, especially the first step:

+   1. When do you need this new way of defining data? You already know that the need for itemizations is due to distinctions among different classes of information in the problem statement. Similarly, the need for structure-based data definitions is due to the demand to group several different pieces of information.
+   
+   An itemization of different forms of data—including collections of structures—is required when your problem statement distinguishes different kinds of information and when at least some of these pieces of information consist of several different pieces.
+   
+   One thing to keep in mind is that data definitions may refer to other data definitions. Hence, if a particular clause in a data definition looks overly complex, it is acceptable to write down a separate data definition for this clause and refer to this auxiliary definition.
+   
+   And, as always, formulate data examples using the data definitions.