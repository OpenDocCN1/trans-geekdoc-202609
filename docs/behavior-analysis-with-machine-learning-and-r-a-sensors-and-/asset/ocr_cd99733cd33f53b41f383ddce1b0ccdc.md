# # Chapter 7

# ## Encoding Behavioral Data

Sensor data comes in many different flavors and shapes. Data stored in databases also have different structures (relational, graph, plain text, etc.). As mentioned in chapter 1, before training a predictive model, data goes through a series of steps, from data collection to preprocessing (Figure 1.6). During these steps, data is transformed and shaped with the aim of easing the operations in the subsequent tasks. Finally, the data needs to be encoded in a very specific format as expected by the predictive model. For example, decision trees and many other classifier methods expect their input data to be formatted as **feature vectors** when Dynamic Time Warping expects the data to be represented as **timeseries**. When working with images, one usually encodes them as $n$-dimensional matrices and when it comes to social network analysis, a **graph** is the preferred representation.

So, I have been mentioning two key terms: **encode** and **representation**. The Cambridge Dictionary¹ defines the verb *encode as:

> > To put information into a form in which it can be stored, and which can only be read using special technology or knowledge...

while TechTerms.com² defines it as:

> > Encoding is the process of converting data from one form to another.

Both definitions are similar but for case, the second one will make more sense. The Cambridge Dictionary³ defines representation as:

+   ¹https://dictionary.cambridge.org/dictionary/english/encode
²https://techterms.com/definition/encoding
³https://dictionary.cambridge.org/dictionary/english/representation