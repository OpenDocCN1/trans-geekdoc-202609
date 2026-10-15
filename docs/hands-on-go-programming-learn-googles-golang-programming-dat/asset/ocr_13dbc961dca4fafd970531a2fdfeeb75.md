```
c2 := c1 // A copy of the struct 'c1' is assigned to 'c2'
fmt.Println("city list c1 =", c1)
fmt.Println("city list c2 =", c2)

c2.city2 = "Bengaluru"
c2.city3 = "Mumbai"
fmt.Println("\nAfter modifying c2:")
fmt.Println("city list c1 =", c1)
fmt.Println("city list c2 =", c2)
}
```

The following will be the output for the above code:

**city list c1 = {Pune Delhi Lucknow}**
**city list c2 = {Pune Delhi Lucknow}**

**After modifying c2:**
**city list c1 = {Pune Delhi Lucknow}**
**city list c2 = {Pune Bengaluru Mumbai}**