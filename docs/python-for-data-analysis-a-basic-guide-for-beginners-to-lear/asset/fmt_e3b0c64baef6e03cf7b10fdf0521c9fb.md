
# Customer analytics has evolved as the backbone of the marketing industry

This is a direct result of the advent of "smart consumer" who is more aware and connected to one another than ever before and willing to take their business elsewhere at a moment's notice. The smart customer has seamless access to a variety of information including the best products and services available in the market and where can they find the best deals to make the most of their money. Therefore, companies are required to be proactive and be able to predict consumer behavior when interacting with their products and to be in a position to take the required action to convert the prospective customer into a paying client. To generate more accurate forecasts and predictions of customer behavior, companies must have a solid understanding of their customers' buying habits and lifestyle choices. These near accurate predictions will provide the company with an edge over the competition and help achieve higher conversion rates in their sales and marketing funnel.

## One of the best customer analytics solution in the market today

One of the best customer analytics solution in the market today is “SAS Customer Intelligence,” which claims to have the following applications:

* Achieve higher customer loyalty and response rates.
* Generate personalized customer offers and messages to reach the right customer at the right time.
* Identify prospective customers with similar attributes and a high likelihood of conversion so the company can reduce costs on their targeted marketing strategies and campaigns.
* Reduce customer attrition by generating accurate predictions on customers that are more likely to take their business somewhere else and developing proactive marketing campaigns to retain them.

“The insights derived from our new analytics capabilities are allowing us to find the sweet spots that will continue to drive loyalty, profitability, and sustainable growth.”

\- Carrie Gray, Executive Director for Medium Business Marketing, Verizon

## Predictive Analytics Marketing

According to SAS, predictive analytics is the “use of data, statistical algorithms, and machine learning techniques to identify the likelihood of future outcomes based on historical data. The goal is to go beyond knowing what has happened to provide the best assessment of what will happen in the future". Today, companies are digging through their past with an eye on the future, and this is where artificial intelligence for marketing comes into play, with the application of predictive analytics technology. The success of predictive analytics is directly proportional to the quality of big data collected by the company.

Here are some of the widely used predictive analytics applications for marketing:

### Predictive Analysis for Customer Behavior

For the industrial giants like "Amazon," "Apple," and "Netflix," analyzing customer activities and behavior is fundamental to their day-to-day operations. Smaller businesses are increasingly following in their footsteps to implement predictive analysis in their business model. The development of a customized suite of predictive models for a company is not only capital-intensive but also requires extensive manpower and time. Marketing companies like "AgilOne” offer relatively simple predictive model types with wide applicability across industrial domains. They have identified three main types of predictive models to analyze customer behavior, which are:

“`Propensity models`” – These models are used to generate “true or accurate” predictions for customer behavior. Some of the most common propensity models include: “predictive lifetime value,” “propensity to buy,” “propensity to turn,” “propensity to convert,” “likelihood of engagement,” and “propensity to unsubscribe.”

“`Cluster models`” – These models are used to separate and group customers based on shared attributes such as gender, age, purchase history, and demographics. Some of the most common cluster models include "product-based or category base clustering," "behavioral customs clustering," and "brand based clustering."

“`Collaborative filtering`” – These models are used to generate products and services and recommendations as well as to recommended advertisements based on prior customer activities and behaviors. Some of the most common collaborative filtering models include "upsell," "cross-sell," and "next sell" recommendations.

The most significant tool used by companies to execute predictive analytics on customer behavior is "`regression analysis`," which allows the company to establish correlations between the sale of a particular product and the specific attributes displayed by the purchasing customer. This is achieved by employing "`regression coefficients`," which are numeric values depicting the degree to which the customer behavior is affected by different variables and developing a "`likelihood score`" for the future sale of the product.

### Predictive Data Analysis using Scikit-Learn library

To understand how `Scikit-Learn` library is used in the development of the “Predictive Data Analysis” or machine learning model, let us use the “`Sales_Win_Loss` data set from IBM’s Watson repository” containing data obtained from sales campaign of a wholesale supplier of automotive parts. We will build a machine learning model to predict which sales campaign will be a winner and which will incur a loss.

The data set can be imported using `Pandas` and explored using `Pandas` techniques such as “`head()`”, “`tail()`”, and “`dtypes()`.” The plotting techniques from “`Seaborn`” will be used to visualize the data. To process the data `Scikit-Learn`’s “`preprocessing.LabelEncoder()`” will be used and “`train_test_split()`” to divide the data set into a training subset and testing subset.

To generate predictions from our data set, three different algorithms will be used, namely, “`Linear Support Vector Classification` and `K-nearest neighbor classifier`.” To compare the performances of these algorithms, `Scikit-Learn` library technique, “`accuracy_score`,” will be used. The performance score of the models can be visualized using “`Yellowbrick`” visualization and `Scikit-Learn`.

#### Installing Scikit-Learn

The latest version of `Scikit-Learn` can be found on “`Scikit-Learn.org`” and requires “`Python` (version >= 3.5); `NumPy` (version >= 1.11.0); `SciPy` (version >= 0.17.0); `joblib` (version >= 0.11)”. The plotting capabilities or functions of Scikit-learn start with “`plot_`” and require “`Matplotlib` (version >= 1.5.1)”. Certain `Scikit-Learn` examples may need additional applications: “`Scikit-Image` (version >= 0.12.3), `Pandas` (version >= 0.18.0)”.

With the prior installation of "`NumPy`" and "`SciPy`,” the best method of installing `Scikit-Learn` is using “`pip`: `pip install -U scikit-learn`” or “`conda`: `conda install scikit-learn`.”

One must make sure that “`binary wheels`” are utilized when using `pip` and that “`NumPy`” and “`SciPy`” have not been recompiled from source, which may occur with the use of specific OS and hardware settings (for example, “`Linux on a Raspberry Pi`”). Developing “`NumPy`” and “`SciPy`” from source tends to be complicated (particularly on Windows); therefore, they need to be set up carefully, making sure the optimized execution of linear algebra routines is achievable.

#### Importing the Data Set

To import the “`Sales_Win_Loss` data set from IBM’s Watson repository," the first step is importing the "`Pandas`" module using "`import pandas as pd`.”

Then, we leverage a variable `URL` as “`https://community.watsonanalytics.com/wp content/uploads/2015/04/WA_Fn-UseC_-Sales-Win-Loss.csv`” so that the data set can be stored and downloaded on the URL.

Now, “`read_csv()` as `sales_data = pd.read_csv(url)`” technique will be used to read the above "`CSV or comma-separated values`" file, which is supplied by the `Pandas` module. The CSV file will then be converted into a `Pandas` data framework with the return variable as "`sales_data`,” where the framework will be stored.
