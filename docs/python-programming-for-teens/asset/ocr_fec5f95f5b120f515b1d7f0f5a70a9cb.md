```
```python
forward(70)
    left(angle)
    left(36)    # Rotate them evenly
end_fill()
return "Done!"
if __name__ == "__main__":
    msg = main()
    print(msg)
    mainloop()
```
```

# EXERCISE SOLUTIONS FOR CHAPTER 5

# Exercise 1

```
```python
"""
pythagoras.py
Compute the hypotenuse of a right triangle.
"""

from math import sqrt

def hypo(side1, side2):
    """Arguments: the two smaller sides of a right triangle.
    Returns: the hypotenuse."""
    sumOfSquares = side1 ** 2 + side2 ** 2
    return sqrt(sumOfSquares)

def main():
    sides = ((2, 3), (3, 4), (5, 6))
    for (side1, side2) in sides:
        hypotenuse = hypo(side1, side2)
        print("Side1:   ", side1)
        print("Side2:   ", side2)
        print("Hypotenuse:", hypotenuse)

if __name__ == "__main__":
    main()
```
```

# Exercise 2

```
```python
"""
testcircle.py
Draws a circle using the regularPolygon function.
"""
```
```