
It analyses log records and the created ontology to apply aggregation to user accesses to domain-specific websites. By employing Web usage mining approaches \[[17](#ch24.xhtml#ref24_17), [18](#ch24.xhtml#ref24_18)\], we may first create visit or navigation profiles, and then promote the formation of new ideas. Extracting relevant information from a database often begins with a well-applied clustering method. In reality, grouping results in classification, or the separation of data into similar but separate groupings \[[19](#ch24.xhtml#ref24_19), [20](#ch24.xhtml#ref24_20) and [21](#ch24.xhtml#ref24_21)\].

## D. Extracting Information and Relations from Domain Specific Ontology
Use analysis yields categories of visited pages and total visits. Syntactic labeling of pages is accomplished in relation to the directories that map to the sites’ structures, visit classes are determined by groups of pages that have been visited, and clusters of pages are used for clustering. Extracting object and occurrence attributes based on these categories of syntax and the ontology’s semantic concepts is necessary for gauging the effect ontology.

## E. Pruning the Ontology
By filtering out unrelated results and qualities, it is able to capture a deep understanding of the target domain.
The steps presented in [Figure 24.1](#ch24.xhtml#fig24_1) have already been explained above.

## Result and Implementation
The first phase begins with web search results produced by user queries in context of domain. Here, the user entered query for knowing current weather report in Delhi. The web search results are produced in [Figure 24.2](#ch24.xhtml#fig24_2).
![Figure 24.2 Web search results produced](images/fig24_2_C.jpg)
[Figure 24.2 Web search results produced](#ch24.xhtml#R_fig24_2)
The search results are produced in context of user query ‘current weather report’. Now, it becomes difficult for users to access each and every web page and extract relevant information from it. To make it easier, the next step is pre-processing of search results to get information about web logs and sessions.
[Figure 24.3](#ch24.xhtml#fig24_3) displays the user log data having 193 requests for viewing pages. Each log file consists of requests by users who visited page related to weather current report. The log files contain Status, timestamp, size of transferred document and page addresses.
![Figure 24.3 Pre-processing of web logs](images/fig24_3_C.jpg)
[Figure 24.3 Pre-processing of web logs](#ch24.xhtml#R_fig24_3)
[Figure 24.4](#ch24.xhtml#fig24_4) shows the classes and instance browser of ontology designed in context of weather phenomenon. The classes include wind gusts, temperature, humidity, pressure, cloud cover, visibility, dew point and cloud ceiling. It is seen that humidity is in percentage so its instance is made as percent.
![Figure 24.4 Creation of ontology using PROTEGE](images/fig24_4_C.jpg)
[Figure 24.4 Creation of ontology using PROTEGE](#ch24.xhtml#R_fig24_4)
[Figure 24.5](#ch24.xhtml#fig24_5) shows clustering algorithm applied to the designed ontology for generating clusters and instance values. The values are such that wind gusts are at 19 k/h, humidity is 88%, and temperature is 27 degrees and so on.
![Figure 24.5 Applying clustering to generate instance values and clusters](images/fig24_5_B.jpg)
[Figure 24.5 Applying clustering to generate instance values and clusters](#ch24.xhtml#R_fig24_5)
After application of clustering algorithm, we will find relations between the pages visited by users.[Table 24.1](#ch24.xhtml#tab24_1) illustrates the pages of all web sites visited by users. The user may be student who wants to perform research on weather report, may be meteorologist, and may be some others.
[Table 24.1 Clustered results between page visits and type of users.](#ch24.xhtml#R_tab24_1)
| Type of users || Pages visited |
| --- | --- |
| Students || 100 |
| --- | --- |
| Researcher || 250 |
| IMD Dept || 30 |
| Meteorologist || 50 |
| Scientist || 120 |
| Total number || 550 |
[Figure 24.6](#ch24.xhtml#fig24_6) shows successful execution of proposed approach by creating only relevant sub-classes and axi-oms of ontology. It is termed as pruning of ontology.
![Figure 24.6 Wizard to extract relations successfully completed](images/fig24_6_C.jpg)
[Figure 24.6 Wizard to extract relations successfully completed](#ch24.xhtml#R_fig24_6)
[Figure 24.7](#ch24.xhtml#fig24_7) represents clustered results between type of users and number of page visits.
![Figure 24.7 Graphical representation of clustered results between type of users and number of page visits](images/fig24_7_C.jpg)
[Figure 24.7 Graphical representation of clustered results between type of users and number of page visits](#ch24.xhtml#R_fig24_7)

## Conclusion and Future Work
The given paper proposed a refined framework based on ontology for analyzing web search results. It leads to various steps like pre-processing of search results given by traditional search engine followed by development of ontology with the help of editor named PROTÉGÉ. The ontology is designed in context of weather report which consists of classes, sub-classes and instances. It is followed by applying web usage mining methods like clustering to generate clusters and number of pages visited by users. It is done to perform mining of web logged files and extract relevant information from them. Lastly, the pruned or refined ontology is generated based on knowledge gathering process.
In future, the work can be extended to apply semantic web rule language (SWRL) in the designed ontology for generating recommendations and results.

## References
1. [Malik, S. K., Prakash, N., and Rizvi, S. A. M.](#ch24.xhtml#R_ref24_1) (2010). Ontology and web usage mining towards an intelligent web focusing web logs. In International Conference on Computational Intelligence and Communication Networks, Bhopal, India, (pp. 443–448), doi: [10.1109/CICN.2010.90.](http://dx.doi.org/10.1109/CICN.2010.90)
2. [Ramesh, C., Rao, K. V. C., and Govardhan, A.](#ch24.xhtml#R_ref24_2) (2017). Ontology based web usage mining model. In International Conference on Inventive Communication and Computational Technologies (ICICCT), Coimbatore India, (pp. 356–362), doi: [10.1109/ICICCT.2017.7975219.](http://dx.doi.org/10.1109/ICICCT.2017.7975219)
3. [Singh, S. P., and Meenu](#ch24.xhtml#R_ref24_3), (2017). Analysis of web site using web log expert tool based on web data mining. In International Conference on Innovations in Information, Embedded and Communication Systems (ICIIECS), Coimbatore India, (pp. 1–5), doi: [10.1109/ICIIECS.2017.8275961.](http://dx.doi.org/10.1109/ICIIECS.2017.8275961)
4. [Bharti, P. M., and Raval, T. J.](#ch24.xhtml#R_ref24_4) (2019). Improving web page access prediction using web usage mining and web content mining. In 3rd International conference on Electronics, Communication and Aerospace Technology (ICECA), Coimbatore India, (pp. 1268–1273), doi: [10.1109/ICECA.2019.8821950.](http://dx.doi.org/10.1109/ICECA.2019.8821950)
5. [Anitha, V., and Isakki, P.](#ch24.xhtml#R_ref24_5) (2016). A survey on predicting user behavior based on web server log files in a web usage mining. In International Conference on Computing Technologies and Intelligent Data Engineering (ICCTIDE’16), Kovilpatti India, (pp. 1–4), doi: [10.1109/ICCTIDE.2016.7725340.](http://dx.doi.org/10.1109/ICCTIDE.2016.7725340)
6. [Yadao, S., Babu, A. V., Janarthanan, M., and Bhaumik, A.](#ch24.xhtml#R_ref24_6) (2021). Web usage mining: a comparison of WUM category web mining algorithms. In Third International Conference on Intelligent Communication Technologies and Virtual Mobile Networks (ICICV), Tirunelveli India, (pp. 1020–1024), doi: [10.1109/ICICV50876.2021.9388539.](http://dx.doi.org/10.1109/ICICV50876.2021.9388539)
