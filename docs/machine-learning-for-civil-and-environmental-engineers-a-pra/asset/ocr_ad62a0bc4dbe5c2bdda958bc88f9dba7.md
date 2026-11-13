accommodate addition and subtraction operations. Unlike interval data, ratio data can have zero values. Overall, numerical data can be statistically and arithmetically calculated (i.e., averaged) and/or arranged in an ascending or descending order.

I would like you to try a mental exercise and read the following numbers: 33, 35, 48, 86, 88, 91, and 97 out loud. Now, I would like you to answer the following two questions, what are these numbers? What do they convey?

Go back to this chapter’s quote. As you can see, “data have no meaning in themselves”! Now, let us assign units to these numbers, say, MPa. These numbers now refer to pressure or stress.14 In the context of construction materials, the compressive strength of concrete is given in terms of MPa.15 If we use different units, then these numbers would represent the air quality in a certain region (in μg/m3), the length of highways (in km), depth of footing for a structure (in feet).

Knowing the context allows us to build a story. Our story is that we have seven concrete cylinders that we have tested and recorded their compressive strength. Knowing the context also allows us to effectively name all these values under one title. Now, these are no longer random values. These are data points that describe the measured compressive strength of concrete of each tested cylinder. In Chapter 2, we discussed how most supervised ML revolves around building regression and classification models. Thus, these data points can be readily used in a regression model. If this model is to predict the compressive strength of concrete, then these values are now our target (or response).

What if we would like to run a classification model on this data? To do so, we will have to use categorical data. Let us then discuss categorical data.

# 3.2.2 Categorical Data

Categorical data are non-numerical and are sorted by their labels or characteristics such as construction type (low-rise, high-rise, etc.), failure mode (flexures, shear, etc.), etc. Given their labels, such data cannot be added or averaged. Categorical data can be further divided into nominal16 data and ordinal data.

Nominal data contain names or titles (such as color or title). This type of data can be collected from surveys or questionnaires. On the other hand, ordinal data comes with a preconceived order/rating scale. While this type of data can be ranked, it cannot be measured (i.e., minor damage, major damage, collapse). A simple way to remember numerical and categorical data is coded in Figure 3.1.

Let us now revisit our aforementioned question. By definition, a classification model classifies categorical data. However, the data we collected from testing the concrete cylinders is numerical. To convert numerical data into categorical data, we will have to create categories that our numerical data can be fitted into. One such example is to create two classes, namely, normal strength concrete and high strength concrete.

![](bbox=[0.585, 0.54, 0.903, 0.78])

The cylinders with a compressive strength of concrete under 55 MPa can fall into the normal strength concrete category,17 and those of higher strength must then fall under the high strength concrete category. Thus, our target now is no longer a numerical value but rather a class.

From this context, we can now build regression-based or classification-based ML models to predict our target based on some input. This input could be numerical, categorical, or a mixture of the two.18 I would like to emphasize this point. The target in a tabular format is more likely to be homogeneous than the inputs. As in, the target will be numerical values (in case of regression) or classes (in case of classification) – see Table 3.1 for an example that lists the results from a series of tests conducted on structural elements.

# Figure 3.1 Data types.

+   - 14 Pa is pascal (named after Blaise Pascal). A pascal describes a force over an area (such as N/mm²). Force over an area is pressure or stress.
+   - 15 Equivalently, ksi.
+   - 16 From the Latin nomenclature Nomen (meaning name).
+   - 17 I am following the recommendation of the American Concrete Institute (ACI).
+   - 18 We will get to these in a few sections from now. Look under the manipulation section.