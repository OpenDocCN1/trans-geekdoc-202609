The zoom_start keyword argument specifies the map's initial zoom level, lower values show more of the world and higher values show less. On our system, 5 displays the entire continental United States. The detect_retina keyword argument enables folium to detect high-resolution screens. When it does, it requests higher-resolution maps from OpenStreetMap.org and changes the zoom level accordingly.

# # Creating Popup Markers for the Tweet Locations

Next, let's iterate through the DataFrame and add to the Map folium Popup objects containing each tweet's text. In this case, we'll use method itertuples to create tuples from each row of the DataFrame. Each tuple will contain a property for each DataFrame column:

lick here to view code image

```
In [22]: for t in df.itertuples():
    ....:     text = ': '.join([t.screen_name, t.text])
    ....:     popup = folium.Popup(text, parse_html=True)
    ....:     marker = folium.Marker((t.latitude, t.longitude),
    ....:                          popup=popup)
    ....:     marker.add_to(usmap)
    ....: 
```

First, we create a string (text) containing the user's screen_name and tweet text separated by a colon. This will be displayed on the map if you click the corresponding marker. The second statement creates a folium Popup to display the text. The third statement creates a folium Marker object using a tuple to specify the Marker's latitude and longitude. The popup keyword argument associates the tweet's Popup object with the new Marker. Finally, the last statement calls the Marker's add_to method to specify the Map that will display the Marker.

# # Saving the Map

The last step is to call the Map's save method to store the map in an HTML file, which you can then double click to open in your web browser:

lick here to view code image

```
In [23]: usmap.save('tweet_map.html')
```

The resulting map follows. The Markers on your map will differ: