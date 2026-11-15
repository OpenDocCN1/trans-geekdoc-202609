Since this list contains no elements its cardinality is zero:

```
L' LEN 0 EQ ( → 1,true)
```

Conversely, suppose that we create a nonempty list:

```
{l₀ l₁ ... lₙ} L LIST
```

This list has cardinality greater than zero:

```
L \not LEN 0 > ( → 1,true)
```

By an element count of 0 we can determine that a list is empty. Any greater count signifies that the list is not empty.

Suppose we wish to prove that two lists, L₀ and L₁, have the same cardinality. We want to show that:

```
(L₀) = (L₁)
```

This Boolean operation has an outcome of either true or false.

Programmatically, given the following two lists Ia and Ix, we can check if they have the same cardinality.

```
{ a b c } Ia LIST
{ x y z } Ix LIST
Ia' LEN Ix' LEN EQ ( → 1, or true)
```

# Theorem:

```
For all lists L₀, L₁, ..., Lₙ :
|L₀ L₁ ... Lₙ| = |L₀| + |L₁| + ... + |Lₙ|
```