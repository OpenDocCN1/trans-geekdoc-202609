lick here to view code image

```
```python
# card.py
"""Card class that represents a playing card   and its image file name."""

class Card:
    FACES = ['Ace', '2', '3', '4', '5', '6',
             '7', '8', '9', '10', 'Jack', 'Queen', 'King']
    SUITS = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
```
```

You define a class attribute by assigning a value to it inside the class’s definition, but not
inside any of the class’s methods or properties (in which case, they’d be local variables).
FACES and SUITS are constants that are not meant to be modified. Recall that the Style
Guide for Python Code recommends naming your constants with all capital letters. 4

4 Recall that Python does not have true constants, so FACES and SUITS are still modifiable.

We’ll use elements of these lists to initialize each Card we create. However, we do not need a
separate copy of each list in every Card object. Class attributes can be accessed through any
object of the class, but are typically accessed through the class’s name (as in, Card.FACES or
Card.SUITS). Class attributes exist as soon as you import their class’s definition.

# Card Method __init__

When you create a Card object, method __init__ defines the object’s _face and _suit
data attributes:

lick here to view code image

```
```python
def __init__(self, face, suit):
    """Initialize a Card with a face and   suit."""
    self._face = face
    self._suit = suit
```
```

# Read-Only Properties face, suit and image__name

Once a Card is created, its face, suit and image_name do not change, so we implement
these as read-only properties (lines 14–17, 19–22 and 24–27). Properties face and suit
return the corresponding data attributes _face and _suit. A property is not required to
have a corresponding data attribute. To demonstrate this, the Card property image_name’s
value is created dynamically by getting the Card object’s string representation with
str(self), replacing any spaces with underscores and appending the ‘ .png ’ filename
extension. So, ‘Ace of Spades’ becomes ‘Ace_of_Spades.png’. We’ll use this file
name to load a PNG-format image representing the Card. PNG (Portable Network Graphics)
is a popular image format for web-based images.