
After downloading is complete, open VS Code; you will see a welcome screen. Here, you can create a new file or open a new folder. Let us create a new file.

VS Code supports hundreds of programming languages, extensions of which can be found in the VS Code marketplace. However, the default language support for a file is based on the filename extension. To add a new file extension to an existing language, go to files.associations setting, for example, if you want to add .myphp file extension to the PHP language:

```json
"files.associations": {
    "*.myphp": "php"
}
```

Let us now understand the interface of VS Code:

- At the bottom, you will see a status bar; it contains helpful information such as current line number, programming language, and errors and warnings.
- On the left-hand side, you have an Activity bar; starting from the top, you will see:
  - File Explorer that contains your current files and folders.
  - Search, which can be used to search your files.
  - Source control that helps you to track the changes you made in different versions of your files.
  - Run view, which enables you to run and debug your code.
  - Extension views where you can manage and download extensions for almost anything.
- In the center of the screen, you have the command palette. It is the control center for all the actions performed in the VS Code. Any action you perform in VS Code is mapped to command in the command palette.

To make VS Code a better editor for you, you need to install the correct extensions for the programming language you want to use. VS Code provides built-in support for some languages, but to have the best experience, install the extensions for the language you want to use.

You then need to go to keymaps to install keyboard shortcuts from other editors.

Another thing that can be customized here is your color theme. It enables you to choose any colors available in VS Code. Select the color theme option on the welcome screen to see the list of color themes. When you select a specific color, it shows the preview of the chosen color theme.

To learn about VS Code editing features, choose interactive playground. Here you will find examples of the code editor features such as multi-cursor editing. To see multiple cursors in action, you can click into the interactive panel.

There is literally nothing a VS Code cannot do. Any functionality that you need will either be supported by the editor or by someone who has created an extension for it.

## Customer Churn Prediction

Customer churn, also known by the term customer attrition, is simply a tendency of customers to stop being a paying client to your business and abandon it. Businesses must take a proactive approach by recognizing the contributing factors responsible for customer attrition and enhancing customer retention by doing something about it. Customer attrition is not so good for businesses as it costs more to attract new loyal customers than preserving existing ones. Proactively predicting the customers who can leave your business is a critical insight that can help you minimize losses.

Azure Machine Learning can enable you to build models, even with relatively little or no experience in this area. To predict customer attrition, you can use historical customer data to train and develop churn prediction models in Azure Machine Learning. It will help if you have datasets that incorporate a true/false column for customer status. Models built based on these datasets can be used to identify which customer attributes are most prominent for retaining your customers.

To test different algorithms and choose the best one, you can use Automated Machine Learning (Automated ML). It automates the process for quicker deployment of a machine learning model with less manual work, while still producing the accurate results.

## Customer Lifetime Value

Customer Lifetime Value is a metric that helps you to understand:

- How well are you resonating with your audience?
- How content are your customers with your products and services?
- What is it that you are doing right to fulfill their needs and what else can you do to make their experience impeccable?

Every business owner wants to know the answers to these questions. Sure, calculating customer lifetime value sounds tough and does not come under everyone's strong suit, but fortunately, learning how to calculate it is not that big of a deal. It does not require high-level arithmetic; in fact, you can calculate this metric repeatedly to establish map points as your business grows.

If you are successfully increasing the customer lifetime value, you are on the right track, and your customers love your product/services. Let us understand what customer lifetime value means.

Customer lifetime value (CLV), also referred to as lifetime value (LTV), is the average amount of expenditure your customers have made on your business over time. To calculate CLV, you need several data points:

- The average monthly transactions of your customer.
- The average amount spent per transaction by your customer.
- The average number of months your customers remain loyal.
- And then calculate the average gross margin.

Multiply all these numbers, and you will get the predictive CLV.

## Product Recommendation System

Today, many e-commerce businesses are giving product recommendations to customers on their websites. It has become a standard feature for e-commerce websites. All businesses are adopting this feature rapidly because relevant product recommendations drive higher sales.

Microsoft has introduced a Microsoft Product recommendation system that does not cost anything more than the underlying Azure resources. You must train it first with some historical transaction data to get recommendations. It analyzes the data and discovers relationships between the products by comparing the interests of different users. For example, it looks for the products that have been purchased together by different users. Once your model is trained, you can add code to your website that requests recommendations by calling an application programming interface (API). You will be able to get two types of recommendations:

- 1. **Item-to-Item.** In this type of recommendation, you send an item number with the API, which then returns with the list of possible items that a customer might be looking for, for example on websites where they mention customers who bought Product A and also bought Product B.
- 2. **Personalized.** For this, you choose a particular user and send the recent transactions with the API, returning with product recommendations for that user.

The algorithm that is mostly used for such type of recommendations is the collaborative filtering approach. It combines the preferences of multiple users and comes up with a recommendation for a given user.

For item-to-item recommendation, the algorithm identifies the frequency of two items bought together by creating a matrix. Now the tricky part starts; the way it comes up with personalized recommendations requires matrix multiplication. Now let us investigate the architecture of the system:

- The Product recommendation system deploys a web app. The same web app hosts the API that you call while training your model and which provides recommendations. It creates Azure Storage accounts for Blobs, Queues, and Tables and to perform training operations, it creates a Web Job Instance.
- When you put in a request for training of your model, it gets the transaction data from blob storage and adds an entry for that model in the Model Registry Table. It also adds a message to the model queue.
- When the Web Job Instance observes the new entry in the model queue, it trains the model. It puts the trained model in Blob storage and updates the entry in Model Registry to complete when it is finished.
- When you send a request against recommendations, the process is much easier. It takes the model from Blob storage, loads it, runs the requests through it, and returns the recommendations. The only time-consuming task in this whole process is to get your transaction data into the format expected by a training job.

Before making the recommendations, the algorithm considers the interest of the user on products, which is why you need to define weights for every event type. For example, some default events are:

- If a user just clicked on a product – weight = 1.
- If a user clicked on a recommendation link – weight = 2.
- If a user adds the product into the cart – weight = 3.
- If a user removes a product from the cart – weight = -1.
- If a user makes a purchase – weight = 4.

Indeed, if users make a purchase, they are more interested in the product than those who just clicked the product. That is why the weight of the purchase event is more than the weight of the clicking event.

This is how Microsoft's Product Recommendation System works.
