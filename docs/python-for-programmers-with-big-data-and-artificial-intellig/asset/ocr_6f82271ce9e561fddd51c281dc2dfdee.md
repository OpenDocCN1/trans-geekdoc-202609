lick here to view code image

```
In [7]: wordcloud = wordcloud.generate(text)
```

Before creating the word cloud, generate first removes stop words from the text argument using the wordcloud module’s built-in stop-words list. Then generate calculates the word frequencies for the remaining words. The method uses a maximum of 200 words in the word cloud by default, but you can customize this with the max_words keyword argument.

# Saving the Word Cloud as an Image File

Finally, we use WordCloud’s to_file method to save the word cloud image into the specified file:

lick here to view code image

```
In [8]: wordcloud = wordcloud.to_file('RomeoAndJulietHeart.png')
```

You can now go to the ch11 examples folder and double-click the RomeoAndJuliet.png image file on your system to view it—your version might have the words in different positions and different colors:

![](bbox=[0.18, 0.43, 0.62, 0.7])

# Generating a Word Cloud from a Dictionary

If you already have a dictionary of key–value pairs representing word counts, you can pass it to WordCloud’s fit_words method. This method assumes you’ve already removed the stop words.

# Displaying the Image with Matplotlib

If you’d like to display the image on the screen, you can use the IPython magic

```
%matplotlib
```

to enable interactive Matplotlib support in IPython, then execute the following statements: