
```
In [18]: for senator in senators_df.TwitterHandle:
    ...:     tweet_counts.append(db.tweets.count_documents(
    ...:         {"$text": {"$search": senator}}))
    ...:
```

The JSON object passed to count_documents in this case indicates that we're using the index named text to search for the value of senator.

## Show Tweet Counts for Each Senator

Let's create a copy of the DataFrame senators_df that contains the tweet_counts as a new column, then display the top-10 senators by tweet count:

Click here to view code image

```python
In [19]: tweet_counts_df = senators_df.assign(Tweets=tweet_counts)
In [20]: tweet_counts_df.sort_values(by='Tweets',
    ...:     ascending=False).head(10)
    ...:
Out[20]:
```

| Index | State | Name | Party | TwitterHandle | TwitterID | Tweets |
|---|---|---|---|---|---|---|
| 78 | SC | Lindsey Graham | R | LindseyGrahamSC | 432895323 | 1405 |
| 41 | MA | Elizabeth Warren | D | SenWarren | 970207298 | 1249 |
| 8 | CA | Dianne Feinstein | D | SenFeinstein | 476256944 | 1079 |
| 20 | HI | Brian Schatz | D | brianschatz | 477470704 | 934 |
| 62 | NY | Chuck Schumer | D | SenSchumer | 17494010 | 811 |
| 24 | IL | Tammy Duckworth | D | SenDuckworth | 1058520120 | 656 |
| 13 | CT | Richard Blumenthal | D | SenBlumenthal | 278124059 | 646 |
| 21 | HI | Mazie Hirono | D | maziehirono | 92186819 | 628 |
| 86 | UT | Orrin Hatch | R | SenOrrinHatch | 262756641 | 506 |
| 77 | RI | Sheldon Whitehouse | D | SenWhitehouse | 242555999 | 350 |

## Get the State Locations for Plotting Markers

Next, we'll use the techniques you learned in the “Data Mining Twitter” chapter to get each state’s latitude and longitude coordinates. We’ll soon use these to place on a Folium map popup markers that contain the names and numbers of tweets mentioning each state’s senators.

The file state_codes.py contains a state_codes dictionary that maps two-letter state codes to their full state names. We’ll use the full state names with geopy’s OpenMapQuest geocode function to look up the location of each state. 7 First, let’s import the libraries we need and the state_codes dictionary:

7We use full state names because, during our testing, the two-letter state codes did not always return correct locations.

Click here to view code image

```python
In [21]: from geopy import OpenMapQuest

In [22]: import time

In [23]: from state_codes import state_codes
```

Next, let's get the geocoder object to translate location names into Location objects:

Click here to view code image

```python
In [24]: geo = OpenMapQuest(api_key=keys.mapquest_key)
```

There are two senators from each state, so we can look up each state's location once and use the Location object for both senators from that state. Let's get the unique state names, then sort them into ascending order:

Click here to view code image

```python
In [25]: states = tweet_counts_df.State.unique()
In [26]: states.sort()
```

The next two snippets use code from the "Data Mining Twitter" chapter to look up each state's location. In snippet [28], we call the geocode function with the state name followed by ', USA' to ensure that we get United States locations, 8 since there are places outside the United States with the same names as U.S. states. To show progress, we display each new Location object's string:

8When we initially performed the geocoding for Washington state, OpenMapQuest returned Washington, D.C.'s location. So we modified state_codes.py to use Washington State instead.

Click here to view code image

```python
In [27]: locations = []
In [28]: for state in states:
    ...:     processed = False
    ...:     delay = .1
    ...:     while not processed:
    ...:         try:
    ...:             locations.append(
    ...:                 geo.geocode(state_codes[state] + ', USA'))
    ...:         print (locations[-1])
    ...:             processed = True
    ...:         except: # timed out, so wait before trying again
    ...:             print('OpenMapQuest service timed out. Waiting.')
    ...:             time.sleep(delay)
    ...:             delay += .1
    ...: 
Alaska, United States of America
Alabama, United States of America
Arkansas, United States of America
...
```

## Grouping the Tweet Counts by State

We'll use the total number of tweets for the two senators in a state to color that state on the map. Darker colors will represent the states with higher tweet counts. To prepare the data for mapping, let's use the pandas DataFrame method groupby to group the senators by state and calculate the total tweets by state:

Click here to view code image

```python
In [29]: tweets_counts_by_state = tweet_counts_df.groupby(
 ...:     'State', as_index=False).sum()
 ...:
In [30]: tweets_counts_by_state.head()
Out[30]:
```

| Index | State | Tweets |
|---|---|---|
| 0 | AK | 27 |
| 1 | AL | 2 |
| 2 | AR | 47 |
| 3 | AZ | 47 |
| 4 | CA | 1135 |

The as_index=False keyword argument in snippet [29] indicates that the state codes should be values in a column of the resulting GroupBy object, rather than the indices for the rows. The GroupBy object’s sum method totals the numeric data (the tweets by state). Snippet [30] displays several rows of the GroupBy object so you can see some of the results.

## Creating the Map

Next, let's create the map. You may want to adjust the zoom. On our system, the following snippet creates a map in which we initially can see only the continental United States. Remember that Folium maps are interactive, so once the map is displayed, you can scroll to zoom in and out or drag to see different areas, such as Alaska or Hawaii:

Click here to view code image

```python
In [31]: import folium
In [32]: usmap = folium.Map(location=[39.8283, -98.5795],
 ...:                  zoom_start=4, detect_retina=True,
 ...:                  tiles='Stamen Toner')
 ...:
```

## Creating a Choropleth to Color the Map

A choropleth shades areas in a map using the values you specify to determine color. Let’s create a choropleth that colors the states by the number of tweets containing their senators’ Twitter handles. First, save Folium’s us-states.json file at

https://raw.githubusercontent.com/python-visualization/folium/master/examples/data

to the folder containing this example. This file contains a JSON dialect called GeoJSON (Geographic JSON) that describes the boundaries of shapes—in this case, the boundaries of every U.S. state. The choropleth uses this information to shade each state. For more about GeoJSON, see http://geojson.org/. 9The following snippets create the choropleth, then add it to the map:

9Folium provides several other GeoJSON files in its examples folder at https://github.com/python-visualization/folium/tree/master/examples/data. You also can create your own at http://geojson.io.

Click here to view code image

```python
In [33]: choropleth = folium.Choropleth(
    ...:     geo_data='us-states.json',
    ...:     name='choropleth',
    ...:     data=tweets_counts_by_state,
    ...:     columns=['State', 'Tweets'],
    ...:     key_on='feature.id',
    ...:     fill_color='YlOrRd',
    ...:     fill_opacity=0.7,
    ...:     line_opacity=0.2,
    ...:     legend_name='Tweets by State'
    ...: ).add_to(usmap)
In [34]: layer = folium.LayerControl().add_to(usmap)
```

In this case, we used the following arguments:

- geo_data='us-states.json'—This is the file containing the GeoJSON that specifies the shapes to color.

- name='choropleth'—Folium displays the Choropleth as a layer over the map. This is the name for that layer that will appear in the map's layer controls, which enable you to hide and show the layers. These controls appear when you click the layers icon () on the map.

- data=tweets_counts_by_state—This is a pandas DataFrame (or Series) containing the values that determine the Choropleth colors.

- columns=['State', 'Tweets']—When the data is a DataFrame, this is a list of two columns representing the keys and the corresponding values used to color the Choropleth.

- key_on='feature.id'—This is a variable in the GeoJSON file to which the Choropleth binds the values in the columns argument.

- fill_color='YlOrRd'—This is a color map specifying the colors to use to fill in the states. Folium provides 12 colormaps: 'BuGn', 'BuPu', 'GnBu', 'OrRd', 'PuBu', 'PuBuGn', 'PuRd', 'RdPu', 'YlGn', 'YlGnBu', 'YlOrBr' and 'YlOrRd'. You should experiment with these to find the most effective and eye-pleasing ones for your application(s).

- fill_opacity=0.7—A value from 0.0 (transparent) to 1.0 (opaque) specifying the transparency of the fill colors displayed in the states.

- line_opacity=0.2—A value from 0.0 (transparent) to 1.0 (opaque) specifying the transparency of lines used to delineate the states.

- legend_name='Tweets by State'—At the top of the map, the Choropleth displays a color bar (the legend) indicating the value range represented by the colors. This legend_name text appears below the color bar to indicate what the colors represent.
