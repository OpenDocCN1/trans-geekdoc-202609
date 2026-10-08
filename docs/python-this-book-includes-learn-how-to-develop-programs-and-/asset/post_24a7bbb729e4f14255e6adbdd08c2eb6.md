
assist render these labels. You can rotate them along the x-axis using the parameter displayed in the following code:

```python
# -*- coding: utf-8 -*-
import pygal
from datetime import datetime, timedelta
Date_Y = pygal(x_Label_rotation=25)
Date_Y.title = "Flights and amount of passengers arriving from St. Louis."
Date_Y.add("Arrival", [
  (datetime(2014, 1, 5), 42),
  (datetime(2014, 1, 14), 123),
  (datetime(2014, 2, 2), 97),
  (datetime(2014, 3, 22), 164)
])
Date_Y.render_to_file('datey_chart.svg')
```

Next, re-render the chart, like in the following screenshot. You can notice that the labels are formatted in a way that supports readability.

![](img/43582740ac1227a817786ef73e0f3772_234_0.png)

Let's include an additional chart before we complete the following chapter. In the following case, you'll capture two points in time known by your code; one is going to be delayed using a sleep delay similar to the time delta example, you're going to have two flights come in at two different points in time.

Here, you'll set a delay between two arrivals and the time for every data point. You will apply for time.sleep() to delay the script. Execute this script. Remember that the chart has a delay in its code, the SVG file will require 277 seconds to process:

```python
# -*- coding: utf-8
import pygal, time
from datetime import datetime
# Set pre-defined arrival dates for compare.
arrival1 = datetime.now()
time.sleep(277)
arrival2 = datetime.now()
delta = arrival2 - arrival1
result = str(delta.seconds)
Date_Y = pygal.Date(x_label_rotation=25)
Date_Y.title = "Flights and amount of passengers arriving from St. Louis."
Date_Y.add("Arrival", [
  (datetime(2014, 1, 5), 42),
  (datetime(2014, 1, 14), 123),
  (datetime(2014, 2, 2), 97),
  (datetime(2014, 3, 22), 164)
])
Date_Y.add("Arrivals today (time between flights %s)" % result, [
  (arrival1, 44),
  (arrival2, 47)
])
Date_Y.render_to_file('datey_chart.svg')
```

Now, let's consider the results. Since the times aren't too far apart, you may want to hover over for a granular appearance at how much time has elapsed. Our label shows that 277 seconds have elapsed.

# Flights and amount of passengers arriving from St. Louis.

![](img/43582740ac1227a817786ef73e0f3772_236_0.png)

# Chapter 6: Data Analysis

Analyzing a dataset to identify patterns is an art. There can be different metrics related to a dataset, and you would like to identify the needle in the following haystack. For your case, the needle is the insight you are searching for in the data that you aren't aware of. In this case, insight may refer to relevant information about people who purchase milk of a certain brand and also purchase cereals of another company. The retail store can arrange the products close to each other.

Whenever you choose to analyze a dataset, you need to have a deep knowledge of it and also of the domain that is related with. If it's a simple dataset that can be understood easily, then the analysis should be done directly, but if the dataset has some similarities to the sensor data of a turbine, then the field of knowledge of how turbines operate and what is important to their operation will increase richness to your analysis.

The mastery of a domain allows you to navigate your analysis.

# What is Data Mining?

Data mining refers to the process of exploring data and discovering patterns in the application of machine learning, database systems, and statistics. The end result of data mining is to extract important information from data, which can be optimized to boost revenue, limit costs, or even save lives through some of its applications.

When you have a dataset that you need to mine, it's not feasible to apply all the data-mining techniques that are available on each column field of the data to extract insights. This will be a difficult task, and it will take a long time to extract any important insights.

To increase the process of data mining, understanding of domains is critical. With the following knowledge, one can understand what the data represents and how to analyze it for gain insights.

The perfect way to begin data mining is to extract themes on which the data requires to be mined. If you have sales data of a Fast Moving Consumer Goods company, then the themes could be as follows:

- Brand behavior
- Outlet behavior
- Growth of products
- Seasonal effect on products

The themes are useful in giving direction to explore data and discover patterns in it.

Once you have the themes, you need to set questions for each to polish the analysis.

For example:

- Brand behavior: Here are questions used to enhance the analysis:
  - Which are the best brands?
  - Which brands have the largest coverage?
  - Which companies are cannibalizing the sales of other brands?

- Outlet behavior: The following are questions that polish the analysis.
  - What is the percentage of outlets that consume 80% of revenue?
  - What type of outlets has the highest number of sales?
  - What type of outlets sells major premium products?

- Growth of products: Here are the questions used to streamline the following theme.
  - How many brands are seasonal?
  - What is the difference based on sales during seasonal and no seasonal times?
  - Which holiday generates the highest amount of sales for a specific brand?

The previous questions below these themes offer pinpointed directions to identify patterns and conduct analysis that generates quality results.

The process of data exploration can be summarized by the flow chart below:

![](img/43582740ac1227a817786ef73e0f3772_239_0.png)

# Present an Analysis

After analysis, you will want to present the results. The most popular medium for doing is PowerPoint. The results of your analysis can be a chart or table.

![](img/43582740ac1227a817786ef73e0f3772_239_1.png)

Below are the different parts:

- Question: The topmost section of the
- Observation: In the following case, observations are highlighted
- Key takeaway: At the bottom of the image, you can explain

# Exploring the Titanic

To conduct the data analysis, you'll use the dataset from Kaggle. This is easy to understand and doesn't need any domain understanding. This dataset holds the details of every passenger and whether they survive or not.

| Field | Descriptions |
|---|---|
| survival | 0= No, 1= Yes |
| pclass | Passenger class (1st, 2nd, 3rd) |
| name | Name of the passenger |
| sex | Gender of the passenger |
| age | Age of the passenger |
| sibsp | Number of siblings/spouses |
| parch | Number of parents/children |
| ticket | Ticket number |
| fare | Passenger fare |
| cabin | Cabin |
| embarked | C = Cherbourg, Q = Southampton |

Because the data is simple to understand, you'll maintain the survival analysis as the major theme that can be used. Here are some of the questions that you will:

- Which class of passengers has the highest number of survivors?
- What is the distribution of the non-vivors among classes?
- What is the distribution, depending on the gender of the survivors among various classes?
- What is the percentage of survival among various age groups?

# Which class of passengers has the highest number of survivors?

To respond to this question, you will create a simple bar plot of the number of survivors and the percentage of survivors in every class, respectively.

![](img/43582740ac1227a817786ef73e0f3772_241_0.png)

In your code, you need to perform a preliminary check for null values on the fields that are utilized. Next, compute the number of survivors and the percentage of survivors in every class. Then, you can plot two bar charts to get the overall number of survivors and the percentage of survivors.

Here are your observations:

- The highest number of survivors are found in the first and third class, respectively.
- With regard to the overall number of passengers in every class, the first class has the highest survivors at around 66%.
- With regard to the overall number of passengers in every class, the third class has the highest number of survivors at around 25%.

Now, your key takeaway:

- There was obviously a preference toward saving those from the first class as the ship was drowning. Also, it featured the highest percentage
