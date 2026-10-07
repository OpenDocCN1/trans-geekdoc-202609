# Listing 6

| | |
|---||
| 21 | inc++ |
| 22 | println("inc:\tValue Of[", inc, "]\tAddr Of[",", &inc, ")") |

The output of line 22 on the playground should look something like this:

# Listing 7

| inc; Value Of[ 11 ] Addr Of[ 0x10429f98 ]

This is what the stack looks like after the execution of those same lines of code:

# Figure 3

![](bbox=[0.119, 0.303, 0.905, 0.735])

After lines 21 and 22 are executed, the increment function returns and control goes back to the main function. Then the main function displays the "value of" and "address of" the local count variable again on line 14.

# Listing 8

| 14 | println("count:\tValue Of[", count, "]\tAddr Of[",", &count, \") |"

The full output of the program on the playground should look something like this.