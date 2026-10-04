# Preparing and exploring your data 247

+   * license—The license number or information related to the listing. It is the object data type, which typically represents a string or text.

We can safely ignore features as host_id

As for the other features, whereas most of them are numeric, the name feature is a string containing various pieces of information to be extracted based on how the data has been organized. By visualizing a single example from it, we can gain an idea of its organization:

```
summary_listings['name'].iloc[0]
```

The string is arranged into five distinct parts separated by conventional signs with some kind of partially sheared and repeated content:

+   'Rental unit in Sumida · 4.78 · 1 bedroom · 2 beds · 1 bath'

The first portion of the string is the unit type and location. The second portion is the average score received from guests. The third portion is the number of bedrooms, the fourth portion is the number of beds, and the last is the number of bathrooms.
Apart from the numeric values, we can also extract some specific information related to the accommodation or services offered—for instance, if the apartment is a studio, if it is shared, and if it is a half-bath (a room with a toilet and washbasin but no bath or shower). We can deal with this by creating string correspondence and obtaining a binary feature pointing out the presence or absence of the characteristic using regex commands.. (short for regular expressions) commands are a sequence of characters constituting a search pattern. They are used for pattern matching within strings. Table 7.1 shows the transformations we apply to the description field and highlights what strings we strive to match, what regex command

Table 7.1 Regex commands for feature engineering

| Matched description | Regex | Resulting feature |
|---|---|---|
 Text that starts with "in," followed by a space, then captures any characters until another space, and ends with a dot | r'in\s(.*?)\s*' | Area of Tokyo of the listing |
| Text that starts with the character "★" (a star), followed by one or more digits, a dot, and one or more additional digits (e.g.,★4.5) | r'★(\d+\.\d+)' | Star ratings |