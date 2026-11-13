# Union

A union joins two sets to create one that contains all the elements from both, without any duplicates.

```
```python
# Union
union_set = A | B # or A.union(B)
print("Union:", union_set)
# Output
# Union: {1, 2, 3, 4, 5, 6}
```
```

```
```java
// Union
Set<Integer> unionSet = new HashSet<>(A); // Creates a new
// set containing all elements from A
unionSet.addAll(B); // Performs a union join with B
System.out.println("Union: " + unionSet); // Output set contents
// Output
// Union: [1, 2, 3, 4, 5, 6]
```
```

# Intersection

An intersection of two sets creates a new set that contains only the elements that are present in both.

```
```python
# Intersection
intersection_set = A & B # or A.intersection(B)
print("Intersection:", intersection_set)
# Output
# Intersection: [3, 4]
```
```

```
```java
// Intersection
Set<Integer> intersectionSet = new HashSet<>(A);
intersectionSet.retainAll(B);
System.out.println("Intersection: " + intersectionSet);
// Output
// Intersection: [3, 4]
```
```