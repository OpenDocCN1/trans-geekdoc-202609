A language L that is oriented to a particular machine M may be denoted L(M).

Consider the set of words { w x z I } consisting of four subwords: w, x, z, and the identity word I. Because the identity word has no effect,

{ w x z I } = { w x z }

We may also define an abstract word based on the w and x words that were previously defined using ab cd mn and pq rs respectively.

```
{ w x } y WORD
```

The word y is the set of symbols of the word w followed by the symbols of the word x.

y → ab cd mn pq rs

To append an element to the word set y, we can either redefine the word, such as:

```
{ w x z } y WORD
```

Or, use the following approach, which is less tedious with larger sets:

```
{ y z } y WORD
```

The concatenation operation is used to join two strings of characters.<sup>10</sup>