# Difference

The difference between two sets is a set containing elements that are in the first set but not in the second.

```
Python
# Difference
difference_set = A - B # or A.difference(B)
print("Difference:", difference_set)
# Output
# Difference: [1, 2]
```

```
Java
// Difference
Set<Integer> differenceSet = new HashSet<>(A);
differenceSet.removeAll(B);
System.out.println("Difference: " + differenceSet);
// Output
// Difference: [1, 2]
```

# REVIEW QUESTIONS

+   Set A: {4, 8, 15, 16, 23}
+   Set B: {42, 8, 16, 60, 7}
+   1 Show the output if a union operation is performed.
+   2 Show the output if an intersection operation is performed.
+   3 Show the output if a difference operation is performed.

# ACTIVITY

# Social Skills: Collaborative group work

# Social-media friend recommendation

With a partner, working in your chosen language, create two sets consisting of the following names:

+   A: Carlos Gomez, Yuna Kim, Dmitri Ivanov
+   B: Yuna Kim, Dmitri Ivanov, Leila Al-Farsi, Sean O'Brien

A and B represent two users on a social-media network. A and B are friends with each other.

+   1 Using set operations, identify the users' common friends.
+   2 Using set operations, identify friends of B that are not friends with A, so the platform can recommend new connections.