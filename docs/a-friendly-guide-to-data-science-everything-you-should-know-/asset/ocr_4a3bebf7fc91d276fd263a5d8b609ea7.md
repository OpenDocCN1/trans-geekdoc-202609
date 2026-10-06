# If-Else Blocks

If-else constructions allow you to say if this, do one thing and if not, do something else. You can also nest these, so you could say, if this, do one thing; if this other thing, do a different thing; and if this last thing, do an even different thing; otherwise, do something else. What this looks like if we spell out the logic is as seen in Table 11-5. This way of writing things out is called pseudocode (although normally you would have actual values like the block on the right), which is a code-like way of writing it's not specific to any particular language, but makes what's happening fairly clear.

# Table 11-5. Framework for a three-condition if–else block

| Flow Concept | Pseudocode |
|---|---|
| if condition 1 | if var1 > 0 |
| then do thing A | then print "positive" |
| else if condition 2 | else var1 == 0 |
| then do thing B | then print "zero" |
| else if condition 3 | else if var1 < 0 |
| then do thing C | then print "negative" |
| else do thing D | else print "something's wonky" |

The code on the left in Table 11-5 checks condition 1 and will do thing A if condition 1 is true. Otherwise, it will check if condition 2 is true, and so down. Note that the way these blocks work is that they “escape” at the first condition they meet. If condition 1 is satisfied, the block will do thing A and then go to the next thing after the entire block, not to condition 2. The only time it would do thing D would be if none of the conditions (1, 2, or 3) are true. The code on the right shows the flow if we're wanting to print the direction (positive or negative) of a numeric variable called var1.