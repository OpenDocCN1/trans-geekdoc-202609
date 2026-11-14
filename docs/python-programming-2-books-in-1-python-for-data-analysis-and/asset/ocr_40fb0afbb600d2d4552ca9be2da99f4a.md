| popitem () | Will remove the key value pair that was most recently added. |
| :--- | :--- |
| setdefault () | Will result in the values of the indicated key. In case the key is not found, a new key will be added with the indicated values. |
| update () | Will update the dictionary with the indicated key value pairs. |
| values () | Will result in a list of all the values in the dictionary. |

EXERCISE – Create a Dictionary “CoffeeShop” with items containing keys as “type”, “size” and “price” with corresponding values as “cappuccino”, “large” and “5.99”. Then add a new item with key as “syrup” and value as “caramel”.

***USE YOUR DISCRETION HERE AND WRITE YOUR CODE FIRST***

Now, check your code against the correct code below:

```
```python
CoffeeShop = {
"type" : "cappuccino",
"size" : "large",
"price" : 5.99
}
CoffeeShop ["syrup"] = "caramel"
print (CoffeeShop)
```
```

OUTPUT – {"type" : "cappuccino", "size" : "large", "price" : 5.99, "syrup" : "caramel"}