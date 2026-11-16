# 10.6.4 Displaying Card Images with Matplotlib

So far, we've displayed Cards as text. Now, let's display Card images. For this demonstration, we downloaded public-domain 5 card images from Wikimedia Commons:

5 https://creativecommons.org/publicdomain/zero/1.0/deed.en.

https://commons.wikimedia.org/wiki/-Category:SVG_English_pattern_playing_cards

These are located in the ch10 examples folder's card_images subfolder. First, let's create a DeckOfCards:

lick here to view code image

```
In [1]: from deck import DeckOfCards

In [2]: deck_of_cards = DeckOfCards()
```

# Enable Matplotlib in IPython

Next, enable Matplotlib support in IPython by using the %matplotlib magic:

lick here to view code image

```
In [3]: %matplotlib
Using matplotlib backend: Qt5Agg
```

# Create the Base Path for Each Image

Before displaying each image, we must load it from the card_images folder. We'll use the pathlib module's Path class to construct the full path to each image on our system. Snippet [5] creates a Path object for the current folder (the ch10 examples folder), which is represented by '.', then uses Path method joinpath to append the subfolder containing the card images:

lick here to view code image

```
In [4]: from pathlib import Path

In [5]: path = Path('.').joinpath('card_images')
```

# Import the Matplotlib Features

Next, let's import the Matplotlib modules we'll need to display the images. We'll use a function from matplotlib.image to load the images: