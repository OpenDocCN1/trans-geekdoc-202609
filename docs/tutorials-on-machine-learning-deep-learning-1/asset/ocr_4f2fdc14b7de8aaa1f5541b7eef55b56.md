SOMAs take a multi-dimensional data set (with lots of columns which are the dimensions of the data set, and lots of rows) and they reduce the dimensionality of these data sets

+   - Basically, instead of using 20, 30 or a hundred or more columns (20, 30 or 100 dimension), we end up with a map.
- That's why they called Self-Organizing Maps (SOMs) we end up with a two-dimensional representation of your data set.
- The purpose of the SOM is to reduce the amount of columns. And represent the data in 2D-map.

Example: Here is an actual SOM, which was produced, from the data of the different states of prosperity and poverty in different countries.

![](bbox=[0.11, 0.227, 0.9, 0.483])

Image Source: cis.hut.fi

+   - Those names actually represents countries of the world and this SOM has put them into clusters based on lots of different indicators.

+   - In this example, 39 indicators were used. And indicators are parameters describing such things as quality of life, the state of health in a country, nutrition, educational, services, and so on.

+   - We can see in the top left corner, we have countries with the best or the least alarming state of poverty. Those countries are Belgium, Sweden, Japan, Spain.

+   - We also notice that it is slowly going towards the other end of spectrum where we have countries with the most alarming state of poverty, like Ethiopia or Zimbabwe.

+   - If we have a huge data set containing 200 plus countries as rows, and 39 different columns (dimensions). Indicators in SOM. It's impossible to visualize.

+   - But using a SOM, we can reduce the dimensionality and present it as a map like above.

+   - Remember that, SOMs are unsupervised techniques: It has training data but it doesn't have any labels in the training data. So its learning is on its.
- Just using given data, and it learns to group these data (countries). It is much more like clustering in ML.

+   - What else can we do with this map: We take the color-codes for the different countries and color them in the world map. In this world map we can determine first world countries and third world countries, where countries are developed, where countries are developing.