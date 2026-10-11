
# Data Exploration with HVPlot and Bokeh

This makes much more sense. Here we can infer that around 1970, something happened which brought down the rate of measles to almost nil. This is true since measles vaccines were introduced in the US around the year 1963.

The plots above convey the right information but provide no interactivity. This is because they are static plots without the functionalities of the pan, hover or zoom in a web browser. However, we can achieve this interactive functionality by a mere import of the `hvplot` package.

## Import hvplot.pandas

```python
diseases_by_year.hvplot()
```

![Description: https://cdn-images-1.medium.com/max/800/1*rwEJnxATIJDnI1OkCOTGqQ.gif](Images/image00275.gif)

The outcome that is displayed by the call is known as a [HoloViews](http://holoviews.org/) object (HoloViews [curve](http://holoviews.org/reference/elements/bokeh/Curve.html)) which is displayed as a Bokeh curve or plot. HoloViews curves or plots are richer and easy to capture your comprehension while exploring the information.

Let us view what more can be done using HoloViews:

### Capturing important points on the Plot itself

1963 was important concerning measles and how about we record this point on the graph itself. This will also help us to compare the number of measles cases before and after the vaccine introduction.

![](Images/image00276.gif)

![Description: https://cdn-images-1.medium.com/max/800/1*NebOYPn7QpWXVlT9UxEhKQ.png](Images/image00277.gif)

Holoviews objects preserve the original data as opposed to other plotting libraries. For instance, it is possible to access the original data in a tabular format.

```python
print(vaccination_introduced)

vaccination_introduced.Curve.I.data.head()
```

![Description: https://cdn-images-1.medium.com/max/800/1*_MDbOOEuPqY4yzm6F1CJXQ.png](Images/image00278.gif)

Here we were able to use the data that was used for making the plot. Also, it is now very easy to break data in many different ways as shown in the code snippet below.

![](Images/image00279.gif)

![Description: https://cdn-images-1.medium.com/max/800/1*e06bgLCzgyKmhXb1BD2bow.gif](Images/image00280.gif)

Instead of a dropdown, we can place charts side by side for better comparison.

```python
by_state["Alabama"].relabel('Alabama') + by_state["Florida"].relabel('Florida')
```

![Description: https://cdn-images-1.medium.com/max/800/1*cmvpwPEKLS7AFEuTJBWwlQ.png](Images/image00281.jpeg)

We can also change the type of plots, say to a bar chart. Let us compare the measles pattern from 1980 to 1985 across four states.

![](Images/image00282.gif)

It is quite evident from the examples above that by choosing HoloViews+Bokeh plots; we get the ability to explore data in our browser itself, with full interactivity and minimal code.

## Visualizing large datasets with PyViz

PyViz also enables working on very large datasets with ease. For such datasets, other members of PyViz suite come into the picture.

*   [GeoViews](http://geoviews.org/)
*   [Datashader](http://datashader.org/)
*   [Panel](https://panel.pyviz.org/)
*   [Param](https://param.pyviz.org/)
*   [Colorcet](https://colorcet.pyviz.org/) for perceptually uniform colormaps for big data

To show you the capabilities of these libraries when handling the voluminous amount of data, let’s work with the NYC taxi dataset which consists of data about a whopping 10 million taxi trips. Again this data is already provided in this book.

We can also add widgets to control the selections. This can be either done in the notebook or a standalone server by marking the servable objects with `.servable()` then running the `.ipynb` file through Bokeh Server or extracting the code to a separate `.py` file and typing the following code snippet:

![](Images/image00283.gif)

### Taxi explorer

The interactiveness does not render on GitHub, but you can still access the notebook and run locally.

## Conclusion

The PyViz tools help us to create beautiful visualizations even with a small amount of code. The PyViz tools bundle up together to create deployable, flexible, scalable, and high-performance dashboards, applications, and visualizations, without using web technologies such as JavaScript. This book is just a mere introduction to the multi useful PyViz ecosystem. Go through the entire book to understand the intricacies and its usage for different types of data.

# Chapter 6: Case Studies

The major shift that has transformed application development has begun remolding Information Technology operations. To keep pace with digital transformation, Information Technology Operations is changing how it manages its ecosystem, turning to artificial intelligence, analytics, and Machine Learning.

Cloud, agile, and DevOps are making new demands that Information Technology can meet only through the use of Artificial Intelligence and its ilk. Professionals who wish to advance their Information Technology Operations career in the future will need to get a handle on [Artificial Intelligence Operations](https://techbeacon.com/enterprise-it/essential-guide-aiops-top-tools-implementation-tips), the term used to describe what it takes for Information Technology Operations to handle the digital transformation.

One way to get the knowledge needed to advance in the coming brave new world of Information Technology Operations is to attend conferences where experts are discussing Artificial Intelligence, analytics, and machine-learning developments and trends, and where you can consult with your peers about their experience with Artificial Intelligence Operations.

This year people will not only witness big advancements in ML but also unimaginable steps and new applications that will force people to go back to square one and re-consider whether ML is a bane or a boon. I like to imagine that it may be just like any other advancement in technology – it is about how you use it. That being said let us dive into the upcoming applications of Artificial Intelligence and ML this year. These applications are mostly in R&D stages and about to be out to the public, or are out to the public but in beta stages, and again to get an official flag off.

### AI chips

Remember when you used to play those arcade PC games before you moved on to consoles like PS4 and Xbox? When playing low-end games, the CPU (usually Intel or AMD) was enough, but when playing the latest high-end games like Tomb Raider and Assasin’s Creed Odyssey, you would need a dedicated GPU (or graphics card in layman’s term). These are dedicated chips that boost only your graphics experience. Why am I talking about this? Well, a new dedicated chip is about to hit the market.

AI enabled chips have already debuted in a few cell-phones like iPhone XR, Huawei Honor Play, and the Galaxy Note 8. In these cell-phones, a dedicated AI chip does the heavy lifting during functionalities like ML-based voice assistant, AI-powered smart camera and more. This way, the AI chip decreases the workload of the primary processor and keeps the phone from lagging. But AI enabled chips in cell-phones are just the tip of the iceberg.

Google, Microsoft, Amazon, Intel, and Facebook are all investing heavily in dedicated infrastructure that will boost AI-based functionalities, be it a chip that you can buy and plugin or a cloud-based CPU that can be used for ML and neural networks. The latest in the news among these are the [Intel Nervana](https://www.intel.ai/nervana-nnp/#gs.C5HAvM5Q) (developed by Intel, where Facebook is a significant development partner), [Google Cloud TPU](https://cloud.google.com/tpu/), [Microsoft’s project Brainwave](https://www.microsoft.com/en-us/research/project/project-brainwave/), and [Amazon’s AWS Inferentia](https://aws.amazon.com/machine-learning/inferentia/).
