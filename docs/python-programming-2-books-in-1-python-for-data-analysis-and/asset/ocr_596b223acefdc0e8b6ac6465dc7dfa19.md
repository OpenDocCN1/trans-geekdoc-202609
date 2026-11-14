```
X = ("corn", "cilantro," "carrot," "potato," "onion")
print (X [-3 : -1])
```

OUTPUT – ("carrot," "potato")

# **EXERCISE** – Create a Tuple “X” with string data values as “corn, cilantro, carrot, potato, onion” and change its item from “potato” to “pepper” using List function.

***USE YOUR DISCRETION HERE AND WRITE YOUR CODE FIRST***

Now, check your code against the correct code below:

```
X = ("corn", "cilantro", "carrot", "potato", "onion")
Y = list (X)
Y [4] = "pepper"
X = tuple (Y)
print (X)
```

OUTPUT – ("corn", "cilantro", "carrot", "potato", "pepper")

# **EXERCISE** – Create a Tuple “X” with string data values as “corn, cilantro, carrot” and another Tuple “Y” with numeric data values as (2, 12, 22), then join them together.