
Her Tip for Prospective Data and Visualization Professionals: Learning is never over. You have to always be learning new things in the field—new tools, new ways of doing things. You may find the need to transition from tool to tool based on what is trending in the market. It's also important to try to seek partners on the business side to learn more about the domain you're working in. Trading knowledge is a great way to build relationships.

Meghan is an experienced analytics and visualization professional with a strong background in retail.

## CHAPTER 19
## This Ain’t Our First Rodeo: ML Applications

### Introduction

Both data science and machine learning in general have been around decades now, and it's steadily increasing in popularity. With a lot of publicly available ML-based tools like ChatGPT, many companies are easily generating marketing copy, and coders are speeding up their coding. With the ever-growing popularity of analytics and ML in general, we're seeing many uses crop up in so many fields. Some companies are using third-party tools to generate their models on their own data, like we saw with Salesforce's ML tool in Chapter 16, but plenty are also diving into creating their own data science solutions and ML tools from scratch.

Data science has helped companies improve their marketing efforts greatly, with approaches like A/B testing commonplace now. It's made easier for companies to cater to specific groups of customers with clustering techniques, allowing hyper-personalization. It can improve sales with things well like well-targeted product and service recommendation. A lot of companies are able to automate a variety of tasks that can save time and labor.

NLP and speech processing are making automating parts of customer support easier, cutting down the number of customer support agents needed with easy-to-build chatbots.

One trend that is making it easier for companies to adopt ML is businesses shifting to the cloud for data storage and tools as they move away from hosting everything on site. Cloud providers offer a variety of services on top of the core ones that attracts companies, and it's easy for them to throw in some ML so companies can try things out with minimal effort. If they like the results, they're already on their way. We'll be talking about the cloud in the next chapter.

One thing that's important to mention here is that you already know a lot of uses of ML—and technology in general—come with ethical quandaries. Many of the applications I'll mention have hard-to-ignore issues even though we don't realize how things are done, so they don't know that there are ethical questions. This can include both the companies using the ML and customers using their products.

Although there are so exciting things we can do with ML, we need to not forget the bigger picture. It's always our responsibility to think about the ethics involved, even if other people aren't.

Below, we'll look at how several industries are using data science and machine learning right now. We'll start with insurance, banking, and finance and then look into retail. Then we'll go into both healthcare and bioinformatics before jumping to the gaming industry. Finally, we'll take a look at criminal justice and education.

## Insurance

Statistics has been a part of the insurance industry almost since its modern inception with rich Englishmen underwriting shipping and colonist transport to the American colonies in the 1600s (underwriting means taking on financial risk for a fee, with the possibility of having to make a large payout). Once Pascal and Fermat solved the problem of points, their techniques for calculating risk were picked up by underwriters, and soon insurance was an entire industry.

So statistics and statistical modeling like linear regression and generalized linear models have been the traditional techniques used in insurance. These have helped them balance risk and profit during underwriting (like determining premium prices), but the industry hasn't yet embraced modern machine learning in their core business. However, there are many possible applications, especially in enhancing current methods. One possibility is to use ML to do feature engineering to create features to use in the traditional models of the field. For instance, they could prepare nonlinear features, bin existing features more effectively, or use clustering to identify entirely new features. Additionally, some ML methods like trees and regularization handle sparse data better than traditional models, so some are starting to look at those. Using ML in this way can open up ethical risks, especially because many Western countries have significant regulations based on protected classes, which can't be included in modeling. In instance, race can't be included in determining what is offered, so data scientists have to be careful that none of the new features act as proxies for race, even if race is not included.

Other areas of the industry have already embraced ML more. For instance, ML can be used to speed up claims processing by looking at characteristics of the claims and routing them to analysts more effectively based on fraud risk or other aspects that require certain specialization. This speeds up processing time. ML can also be used to predict claim frequency and severity. Fraud detection and prevention are more sophisticated with ML, relying on anomaly detection approaches, catching more truly fraudulent claims and minimizing the number of non-fraudulent claims that get sent for further analysis. There are also possibilities in compliance monitoring around regulatory requirements by watching transactions, claims, or communications. Even property damage assessment in claims can be partially automated with image processing techniques. For the most part, these don't have great risk in terms of ethics, but as always, they need to be cautious to treat customers fairly, especially in light of protected classes.

Customer management and sales can also be improved with better monitoring and product recommendations. ML can inform interactions with current customers and identify methods for gaining new ones by grouping customers so different actions can be taken. Another area they're starting to apply ML is in customer churn prediction (predicting customers that leave), and it's very effective. Chatbots and other tools can assist customer service. These are also fairly low risk in terms of ethics, but there be privacy risks with chatbots, so they need to be secure.

## Banking and Finance

ML in banking and finance has a lot in common with insurance, as they're both legacy fields that have benefited greatly from statistics and mathematics. Like in insurance, one of the most powerful and embraced areas that machine learning has revolutionized fraud detection. Similarly, they're starting to use ML in the underwriting phase and in credit scoring, especially in assessing credit risk and determining interest rates on loans. ML makes it easier to include more information in all these decisions, leading to more loans that are also lower risk. Like insurance, they also have to be cautious around regulations on protected classes to make sure info isn't being included in models.

Efforts are also being poured into predicting market trends like interest rates and the stock market behavior because there is so much more data than ever been included before. NLP makes it easier for companies to utilize more data from unstructured sources like news and other documents for use in stock forecasting, as well as any other area that could use that data. A final area that's growing in popularity is fully automated stock trading, called algorithmic trading. The ethical risks aren't significant here, especially if the data used is publicly available. However, what is done with these forecasts can lead to ethical questions in terms of how it's presented to customers.

Money laundering has always been something banking and finance had to watch for, and for ML has made that easier, making it easier to stay in compliance with regulations with anomaly detection. Regulations in general can be especially difficult because they change periodically, but there are methods for automating compliance in the face of change.

There are also many areas related to customers where ML is being used in banking and finance. They use NLP and chatbots to automate or semi-automate customer service, especially on simpler tasks. Customer churn prediction is also done here because it's very useful to try to convince customers to stay if they're planning to leave. Personalization is invaluable for improving the customer experience on website usage, and product recommendations can both make customers happy and increase sales. Some of these come with privacy risks that need to be properly handled.

## Retail

Like other sectors, retail uses data science for improving the customer experience and sales through customer segmentation, targeted marketing, and personalized product recommendations. This is hugely important in retail as repeated selling is their main goal. Loyal customers are invaluable in retail.
