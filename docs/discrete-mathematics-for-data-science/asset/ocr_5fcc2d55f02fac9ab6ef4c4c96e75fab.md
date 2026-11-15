Because of their lack of restrictions, bags may serve as a foundational data structure for more restrictive and abstract structures. Closer to machine level instructions, bags may be constructed using the native facilities for arrays or lists. Used this way, processing a bag is similar to randomly selecting elements from a random access list, which is a topic in the Linear Structures chapter.

Because of the randomness inherent in processing unconnected data, the algorithm efficiency for processing a bag is relatively poor. We never know exactly when, or in what sequence, an element will be drawn from a bag.

A set can be represented by a list such as { a b c d }. Because order does not matter, the same set can be represented as { c b d a }.

Similarly, a bag can be represented by a list, such as { a b c d b } or { b c b d a }. Note the duplicates in these lists.

We can designate elements for a bag b<sub>0</sub> or set s<sub>0</sub> as follows:

```
{ a r g u } s<sub>0</sub> LIST
{ y t b b } b<sub>0</sub> LIST
```

No particular ordering in these list representations of bags and sets is intended here.

The values contained in bags and sets can be numbers, characters, or objects that represent some categorical classification, such as animals, automobiles, financial instruments, etc.

By definition, the data type of the values of a bag are to be the same. However, it may be argued that type consistency in bags does not matter, as bag data is unconnected and there is no comparison of the data inside the bag, such as would be the case if