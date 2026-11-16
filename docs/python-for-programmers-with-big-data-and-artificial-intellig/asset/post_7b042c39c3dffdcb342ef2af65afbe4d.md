

## Methods That Return String Representations of a Card

Class Card provides three special methods that return string representations. As in class Time, method `__repr__` returns a string representation that looks like a constructor expression for creating and initializing a Card object:

click here to view code image

```python
def __repr__(self):
    """Return string representation for repr()."""
    return f"Card(face='{self.face}', suit='{self.suit}')"
```

Method `__str__` returns a string of the format 'face of suit', such as 'Ace of Hearts':

click here to view code image

```python
def __str__(self):
    """Return string representation for str()."""
    return f'{self.face} of {self.suit}'
```

When the preceding section's IPython session printed the entire deck, you saw that the Cards were displayed in four left-aligned columns. As you'll see in the `__str__` method of class DeckOfCards, we use f-strings to format the Cards in fields of 19 characters each. Class Card's special method `__format__` is called when a Card object is formatted as a string, such as in an f-string:

click here to view code image

```python
def __format__(self, format):
    """Return formatted string representation for str()."""
```

This method's second argument is the format string used to format the object. To use the `format` parameter's value as the format specifier, enclose the parameter name in braces to the `right` of the colon. In this case, we're formatting the `Card` object's string representation returned by `str(self)`. We'll discuss `__format__` again when we present the `__str__` method in class `DeckOfCards`.

## 10.6.3 Class DeckOfCards

Class `DeckOfCards` has a class attribute `NUMBER_OF_CARDS`, representing the number of `Cards` in a deck, and creates two data attributes:

- `_current_card` keeps track of which `Card` will be dealt next (0–51) and
- `_deck` (line 12) is a list of 52 `Card` objects.

### Method __init__

`DeckOfCards` method `__init__` initializes a `_deck` of `Cards`. The `for` statement fills the list `_deck` by appending new `Card` objects, each initialized with two strings—one from the list `Card.FACES` and one from `Card.SUITS`. The calculation `count % 13` always results in a value from 0 to 12 (the 13 indices of `Card.FACES`), and the calculation `count // 13` always results in a value from 0 to 3 (the four indices of `Card.SUITS`). When the `_deck` list is initialized, it contains the `Cards` with faces `'Ace'` through `'King'` in order for all the `Hearts`, then the `Diamonds`, then the `Clubs`, then the `Spades`.

click here to view code image

```python
# deck.py
"""Deck class represents a deck of Cards."""
import random
from card import Card

class DeckOfCards:
    NUMBER_OF_CARDS = 52 # constant number of Cards

    def __init__(self):
        """Initialize the deck."""
        self._current_card = 0
        self._deck = []

        for count in range(DeckOfCards.NUMBER_OF_CARDS):
            self._deck.append(Card(Card.FACES[count % 13],
                Card.SUITS[count // 13]))
```

### Method shuffle

Method `shuffle` resets `_current_card` to 0, then shuffles the `Cards` in `_deck` using the random module's shuffle function:

click here to view code image

```python
def shuffle(self):
    """Shuffle deck."""
    self._current_card = 0
    random.shuffle(self._deck)
```

### Method deal_card

Method deal_card deals one Card from _deck. Recall that _current_card indicates the index (0–51) of the next Card to be dealt (that is, the Card at the top of the deck). Line 26 tries to get the _deck element at index _current_card. If successful, the method increments _current_card by 1, then returns the Card being dealt; otherwise, the method returns None to indicate there are no more Cards to deal.

click here to view code image

```python
def deal_card(self):
    """Return one Card."""
    try:
        card = self._deck[self._current_card]
        self._current_card += 1
        return card
    except:
        return None
```

### Method __str__

Class DeckOfCards also defines special method __str__ to get a string representation of the deck in four columns with each Card left aligned in a field of 19 characters. When line 37 formats a given Card, its __format__ special method is called with format specifier '<19' as the method's format argument. Method __format__ then uses '<19' to create the Card's formatted string representation.

click here to view code image

```python
def __str__(self):
    """Return a string representation of the current _deck."""
    s = ''
    for index, card in enumerate(self._deck):
        s += f'{self._deck[index]:<19}'
        if (index + 1) % 4 == 0:
            s += '\n'
    return s
```

## 10.6.4 Displaying Card Images with Matplotlib

So far, we've displayed Cards as text. Now, let's display Card images. For this demonstration, we downloaded public-domain 5 card images from Wikimedia Commons:

5 https://creativecommons.org/publicdomain/zero/1.0/deed.en.

https://commons.wikimedia.org/wiki/-Category:SVG_English_pattern_playing_cards

These are located in the ch10 examples folder's card_images subfolder. First, let's create a DeckOfCards:

click here to view code image

```python
In [1]: from deck import DeckOfCards

In [2]: deck_of_cards = DeckOfCards()
```

### Enable Matplotlib in IPython

Next, enable Matplotlib support in IPython by using the %matplotlib magic:

click here to view code image

```python
In [3]: %matplotlib
Using matplotlib backend: Qt5Agg
```

### Create the Base Path for Each Image

Before displaying each image, we must load it from the card_images folder. We'll use the pathlib module's Path class to construct the full path to each image on our system. Snippet [5] creates a Path object for the current folder (the ch10 examples folder), which is represented by '.', then uses Path method joinpath to append the subfolder containing the card images:

click here to view code image

```python
In [4]: from pathlib import Path

In [5]: path = Path('.').joinpath('card_images')
```

### Import the Matplotlib Features

Next, let's import the Matplotlib modules we'll need to display the images. We'll use a function from matplotlib.image to load the images:

click here to view code image

```python
In [6]: import matplotlib.pyplot as plt
In [7]: import matplotlib.image as mpimg
```

### Create the Figure and Axes Objects

The following snippet uses Matplotlib function subplots to create a Figure object in which we'll display the images as 52 subplots with four rows (nrows) and 13 columns (ncols). The function returns a tuple containing the Figure and an array of the subplots' Axes objects. We unpack these into variables figure and axes_list:

click here to view code image

```python
In [8]: figure, axes_list = plt.subplots(nrows=4, ncols=13)
```

When you execute this statement in IPython, the Matplotlib window appears immediately with 52 empty subplots.

### Configure the Axes Objects and Display the Images

Next, we iterate through all the Axes objects in axes_list. Recall that ravel provides a one-dimensional view of a multidimensional array. For each Axes object, we perform the following tasks:

- We're not plotting data, so we do not need axis lines and labels for each image. The first two statements in the loop hide the x- and y-axes.
- The third statement deals a Card and gets its image_name.
- The fourth statement uses Path method joinpath to append the image_name to the Path, then calls Path method resolve to determine the full path to the image on our system. We pass the resulting Path object to the built-in str function to get the string representation of the image's location. Then, we pass that string to the matplotlib.image module's imread function, which loads the image.
- The last statement calls Axes method imshow to display the current image in the current subplot.

click here to view code image

```python
In [9]: for axes in axes_list.ravel():
    ...:     axes.get_xaxis().set_visible(False)
    ...:     axes.get_yaxis().set_visible(False)
    ...:     image_name = deck_of_cards.deal_card().image_name
    ...:     img = mpimg.imread(str(path.joinpath(image_name).resolve()))
```

