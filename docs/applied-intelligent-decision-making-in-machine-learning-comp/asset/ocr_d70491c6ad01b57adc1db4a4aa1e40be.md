# Domain-Specific Journal Recommendation Using a Feed Forward

# 5.3.1.3 Access Limitations

# 5.3.1.3.1 Masked URL Parameters

Typically, web repositories employ non-sequential URL parameters to obstruct content mining, for example, page identifiers with randomly selected characters. Usually, web repositories use consisting of 12 characters with lower and upper case letters, a dash, and an underscore, which would result in 39* 1020 pages. In the case of scientific web archives, a considerable amount of these identifiers may not reflect to specific pages. Hence, crawling pages in the above conditions in case of web repositories require other ways to acquire the subsequent pages in a paginated environment. An alternative method that the web archives follow to obstruct the subsequent pages is by creating relation among URL of the succeeding page and to the content of the current page. Scientific web archives use an “after item” factor that typically represents the identifier of a data element in the current page and has to be specific to access the succeeding pages. In this case, the efficiency of the scraper significantly decreased as each page must be parsed to analyze the subsequent page. Directly accessing the arbitrary sub-lists using one request becomes hard in these cases.

# 5.3.1.3.2 Robot Recognition and Reverse Turing Tests

Numerous web archives devise various techniques to identify and block robots. Much research has been devoted to incorporate such identification techniques, which usually depend on machine learning algorithms. Balla et al. propose a decision based on ID3 (Balla, Stassopoulos, and Dikaikos 2011). Bomhardt et al. recommend non-sequential networks (Bomhardt, Gaul, and Schmidt-Thieme 2005), and Lu and Yu Employ Markov Models for this purpose (Lu and Yu 2006).

If the identification approaches such an automated effort, they may activate opposing Turing tests to the web resource, for example, static text CAPTCHAs, audio or video CAPTCHAs, image classification, and Google’s “reCAPTCHA.” To prevent being categorized as a robot and to avoid denial of access, a scraper can devise the below-listed approaches.

# 5.3.1.3.3 Changing the Content of Request Headers

A scraper could change user agents by simulating a user agent’s identity for different requests.

# 5.3.1.3.4 Selecting Appropriate Cookie Settings

Depending on the scraping condition, the choice of whether to support or restrict cookies essentially needs a thorough study of the aimed-policy, because enabling cookies can help a scraper to see more human.

# 5.3.1.3.5 Requests and Different Time Intervals

The interval between a series of requested URLs can be varied by choosing random intervals or by varying statistical data of user interactions. However, a trade-off among delaying requests and a scraper’s efficiency has to be matched by developers.