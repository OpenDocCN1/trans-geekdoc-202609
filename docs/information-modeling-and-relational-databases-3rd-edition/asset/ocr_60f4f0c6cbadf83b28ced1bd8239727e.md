Perhaps you verbalized this as in (23). For completeness, the inverse is included.

+   23. The Person with firstname “Terry” is married to / is married to the Person with firstname “Norma”.

Notice that the forward predicate is the same as the inverse. This is an example of a symmetric relationship. Such relationships create special problems (as discussed in a later chapter). To help avoid such problems, at the conceptual level no asserted predicate should be the same as its inverse.

You can always rephrase the fact to ensure this. For example, (24) does this by highlighting the different roles played by each partner.

+   24. The Person with firstname “Terry” is husband of / is wife of the Person with firstname “Norma”.

As another example, consider Table 3.3. This is like Table 3.1 that was considered earlier, but it has a third column added. Try to express the information on the first row of the table in terms of elementary facts before reading the discussion about the table.

# Table 3.3 Origin details about some programming languages.

| Designer | Language | Year |
|---|---|---|
| Wirth | Pascal | 1970 |
| Kay | Smalltalk | 1972 |
| Wirth | Modula-2 | 1979 |

We might at first consider expressing this information as sentence (25), using the ternary predicate “... designed ... in ...”. Do you see any problems with this?

+   25. The Person with surname “Wirth” designed the Language named “Pascal” in the Year 1970 CE.

Recall that an elementary fact must be simple or irreducible. It cannot be split into two or more simpler facts in the context of the UoD. The appearance of the word “and” in a sentence usually indicates that the sentence may be split into simpler facts. Here there is no “and”, but “common sense” tells us that the fact can be split into the following two elementary facts with no information loss:

+   26. The Person with surname “Wirth” designed the Language named “Pascal”.

+   27. The Language named “Pascal” was designed in the Year 1970 CE.

Here, “no information loss” means that if we know (26) and (27), then we also know (25). The phrase “common sense” hides some formal ideas. A sufficient reason for splitting (25) into (26) and (27) would be an implicit understanding that each language was designed in only one year. This constraint holds if we interpret “was designed in” to mean “had its design completed in”. Let us agree with this interpretation.