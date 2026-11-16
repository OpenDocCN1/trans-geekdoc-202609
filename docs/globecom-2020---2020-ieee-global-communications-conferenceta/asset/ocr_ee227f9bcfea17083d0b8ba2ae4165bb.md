These instances are divided into two sets, which we call the tracker set and the non-tracker set (§ III-B).

2) Extract features for sites and requests (§ III-C).

3) Check the F1 score of 10 classification algorithms using 10-fold stratified cross-validation. After evaluating performance, we select some effective classification algorithms for hyper-parameter tuning phase, and combine conceptually different machine learning classification algorithms to build a model (§ III-D).

4) Evaluate the models with the testing data (§ IV).

# B. Data collection

1) Finding CNAME cloaking-based tracking with blacklists: We present our method to label CNAME cloaking-based tracking. Firstly, we perform DNS queries for CNAME answer set on all subdomains of each site. Then, we apply wildcard matching based on well-known tracking filter lists to each resolved CNAME in order to detect CNAME cloaking base tracking. More specifically, we select third-party tracking domains and international third-party tracking domains from Easy privacy list [19] and tracking servers list from AdGuard tracking protection filter [14] as of April 26, 2020. This approach was used in the previous work [18].

2) Datasets: We use OpenWPM [20] with vanilla Firefox in April 2020 to crawl 1,762 sites from Alexa Top 300k where CNAME cloaking-based tracking was previously detected [18]. We also crawl 1,762 sites that were randomly picked from all sites without CNAME cloaking-based tracking [18]. The stored data is all HTTP/HTTPS requests and their responses for each site. Then, applying the method (§ III-B1) to the stored crawled data, we find that 4,047 HTTP requests in 1,532 sites used CNAME cloaking-based tracking¹.

We also rely on another dataset crawled on Alexa Top 100K sites using OpenWPM [20] in April 2018. We check the historical forward DNS (FDNS) datasets provided by Rapid7 [21], and apply the methodology in § III-B1 to detect CNAME cloaking-based tracking in this historical data. We find that 2,546 HTTP requests in 1,005 sites are related to CNAME cloaking-based tracking. We also use 1,005 additional randomly picked sites without CNAME cloaking from this dataset to analyze concept drift in § IV-C. The details of the 2020 dataset and the 2018 dataset are listed in Table I.

TABLE I

SUMMARY OF DATA: 2,010 SITES IN 2018 AND 3,524 SITES IN 2020.

| Metrics | 2018 | 2020 |
|---|---|---|
| 3rd party requests | 185,896 (62.2%) | 276,686 (63.8%) |
| 1st party requests domain | 60,278 (20.2%) | 120,689 (27.8%) |
| subdomain | 52,476 (17.6%) | 36,399 (8.4%) |
| Total requests | 298,649 (100%) | 433,774 (100%) |
| Total sites | 2,010 | 3,524 |

C. Feature extraction We experimentally extract the following features related to sites and requests.

¹The dataset is available at https://github.com/fukuda-lab/cname-cloaking

# 1) Site with CNAME cloaking-related tracking occurring:

+   - num_url: The total number of HTTP requests in a site.
+   - num_1st: The total number of first-party requests in a site.
+   - num_3rd: The total number of third-party requests in a site.
+   - pct_script_call: The proportion of fingerprinting-related method calls in a site.
+   - pct_xhr: The proportion of XMLHttpRequest in a site, which is a built-in browser object that can be used to make HTTP requests in JavaScript to exchange data between the web browser and the server.
+   - pct_3rd_window: The proportion of requests originating from a third-party DOM window in the window hierarchy [22].
+   - ranking: The site ranking according to the Alexa ranking [23].
+   - country: The site country based on Free IP Geolocation API [24].
+   - category: The site category according to the FortiGuard Web Filtering [25] dataset in April 2020.

# 2) Request linked to CNAME cloaking-related tracking:

+   - method: The desired action to be performed for given request.
+   - is_xhr: The request uses an API that provides scripted client functionality for transferring data between a client and a server.
+   - content_type: The HTML tag that resulted in a request, such as image, javascript or document, which are defined in this IDL [22].
+   - len_url: The length of request URL.
+   - len_sub: The subdomain length of request.
+   - len_prefix_sub: The subdomain prefix length of request.
+   - num_prefix_sub: The number of subdomain prefixes.
+   - prefix_sub_blacklist: The subdomain prefix is among subdomain prefixes in tracking filter lists [14] [19].
+   - is_sub_dic: The prefix of subdomain is a word in English dictionary.
+   - entropy_url: The randomness of request URL by calculating the metric entropy from request URL.
+   - entropy_sub: The randomness of subdomain by calculating the metric entropy from subdomain.
+   - entropy_prefix_sub: The randomness of subdomain prefix by calculating the metric entropy from subdomain prefix.

D. Modeling and preliminary results First of all, we split the 2020 dataset (Table I) into testing data and training data. The percentage of the data held over for testing is 20%. It is used in § IV-A to evaluate our model. Next, we describe how it is built to a classification model to detect CNAME cloaking-based tracking using testing data (80% of the 2020 dataset).

1) Model cross-validation: We randomly split the training dataset into 10 smaller sets (folds) without replacement, where nine folds are used for the model training and the remaining