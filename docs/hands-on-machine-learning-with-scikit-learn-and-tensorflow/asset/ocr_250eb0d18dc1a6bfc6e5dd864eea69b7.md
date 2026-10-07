![](bbox=[0.1475, 0.0815, 0.8525, 0.3315])

Figure 2-12. A better visualization highlighting high-density areas

Now that's much better: you can clearly see the high-density areas, namely the Bay Area around Los Angeles and San Diego, plus a long line of fairly high density in the Central Valley, particularly around Sacramento and Fresno.

More generally, our brains are very good at spotting patterns on pictures, but you may need to play around with visualization parameters to make the patterns stand out.

Now let's look at the housing prices [Figure 2-13]. The radius of each circle represents the district's population (option s), and the color represents the price (option c). We will use a predefined color map (option cmap) called jet, which ranges from blue (low values) to red (high prices).

```
housing.plot(kind="scatter", x="longitude", y="latitude", alpha=0.4,
 s=housing["population"]100, label="population", figsize=(10,7),
 c="median_house_value", cmap=plt.get_cmap("jet"), colorbar=True)

plt.legend()
```

16 If you are reading this in grayscale, grab a red pen and scribble over most of the coastline from the Bay Area down to San Diego (as you might expect). You can add a patch of yellow around Sacramento as well.

60 | Chapter 2: End-to-End Machine Learning Project

# WOW! eBook
www.wowebook.com