
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_305_0.png)

Figure 10.2 Journal article shows the emergency (from Tiempo, 2018).

2016 to 2020. The average minimum and maximum river-level values were found to be 200.40 and 493.82 cm, respectively. This information was obtained from the IDEAM (Colombia’s Institute of Hydrology, Meteorology and Environmental Studies) database.

Likewise, ERA5 data on the precipitation and the temperature at monthly intervals, with a resolution of 0.25° x 0.25° for the analysis period, were used to compare the results. The information was obtained through Google Earth Engine. The average mean precipitation in the course of the Magdalena River Basin was 233.59 mm for the period, and the average maximum precipitation was 1,805.38 mm. For the same period, the average mean, maximum, and minimum temperatures in the course of the Magdalena River Basin were 23.65 °C, 30.83 °C, and 9.68 °C, respectively.

Among the multiple sources of digital citizens’ information (e.g., Facebook, Twitter, news, text messages), only digital newspapers were selected for this research. According to Prensa (2015, Dec 17):

> The penetration of the press in Colombia is 78% and regional newspapers and the popular press play an important role. Although there appear to be no studies on the time Colombians spend reading the newspaper, recent research revealed that the number of newspaper readers in Colombia reached 6.3 million in 2013 versus 6.1 million in 2012. As of 2015, there are only 4 newspapers with national circulation. There are about 90 different regional newspapers between paid, popular and free press.

Additionally, Perdomo (2022) found:

> Colombian media has historically been dominated by publishers and broadcasters with strong ties to the political and business elites. That influence seems to be transferring to the digital world, but new players and social media are clearly changing consumption trends. “El Tiempo” newspaper website is by far the most used news site (40%), followed by the online versions of “El Espectador” and “Caracol TV” (27%). But some digital native media are growing in importance. (5 Jan, p. 121)

## 10.3. Methodology

Figure 10.3 shows the main tasks performed to apply, evaluate, and validate the use of NLP in the mapping between water resource problems and digital news. These steps allowed us to extract, detect, and analyze qualitative and quantitative information from newspaper articles related to water bodies.

### 10.3.1. Step 1 (Digital Citizens’ Search for Information Sources)

In this study, digital newspapers were selected as the sources of digital citizens’ information. In this sense, the digital news information provided text records of water-related events (environmental, extreme climatic events, supply). First, all available open sources of information (digital newspapers) were identified. No journalist blogs, newsletters, or non-water-related newspapers were considered for the analysis. The digital newspaper sources were selected under the following criteria: spatial coverage (regional or national), digital information availability, Web access permission, and number of articles. Nevertheless, because of the exploratory nature of this research, the newspaper selection was limited, and not all available newspapers were used. Only departments in close proximity to the Magdalena River Basin were selected. Two regional newspapers were picked for each department, and four national newspapers were used.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_306_0.png)

**Figure 10.3** Methodology process.

Once the newspaper sources were identified, the uniform resource locator (URL) of each newspaper was obtained. For all selected digital newspapers’ websites, the types of available information (articles, photos, videos, and documentaries) were studied. Thus, the news text section was identified for the purpose of obtaining information only from each article’s author. No photos or videos were analyzed.

Although the most representative and oldest newspaper in the country has provided digital information since 1990 and even earlier, most of this information is poor and mainly related to sociopolitical problems, not to water resources. In contrast, the objective of our research was to test the hypothesis that it would be possible to relate water resource events and associated problems to news information. Therefore, the time range was reduced; the digital news search included only news articles from 1 January 2016 to 31 May 2020.

### 10.3.2. Step 2 (Water Bodies and Keywords)

Next, the most important water bodies in the basin were identified (rivers, reservoirs, lakes, and swamps). An analysis of the water bodies in the Magdalena River Basin was then carried out. The analyzed characteristics are (1) size (area or length); (2) importance for the region (environmental, economic, and social); and (3) information availability from digital citizens’ sources. This analysis allowed us to identify and prioritize the elements. Consequently, this information allowed us to select local sources of digital information.

Understanding that the basin is a fundamental and transversal element in the development of many communities, a filtering process to omit irrelevant or unrelated news was carried out. Then, a set of keywords to be used in the news search process and filtering related to the main events and

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_309_0.png)

Figure 10.4 Data-mining process.

The keyword filtered information regarding the water resource main events and problems. In this sense, our search excluded any irrelevant or unrelated news, for example, “Soccer match on the banks of the Medellin River.” In this case, while the news might mention the water body, the focus of the main article was related to other social topics. The time period selection allowed us to filter information regarding its digital publishing date for further analysis.

Figure 10.4 summarizes the data mining and analysis process developed in Steps 4 to 7.

### 10.3.4. Step 4 (Data Extraction and Preprocessing)

As a result of Step 3, for every newspaper article related to each water body, the URL was obtained through the Web-crawling process. The consequent step was to perform Web scraping, based on the parameters of each newspaper website obtained in Step 1. In this process, the information was filtered, downloaded, and processed from an HTML format to a comma-separated values (CSV) file as unstructured data. Python scripts with Googleapiclient, BeautifulSoup, and Pandas libraries were used to download, extract, and transform the digital news. These scripts are available in a GitHub repository at https://github.com/sduarte09/buscandoelmagdalena.

Next, the unstructured data were transformed into a structured data format, so the text of each article, the title, the date, and the ID of the news websites were extracted. This information was then used to filter the news articles in order to remove duplicates, empty website pages, music/video links, or image galleries, as illustrated in Figure 10.5.

Once the structured data were filtered, the data were cleaned, checking the accent marks, changing uppercase into lowercase letters, and removing advertising in the middle of the text. Likewise, for the implementation of NLP techniques, a stop word filter was needed. In the NLP context,

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_310_0.png)

Unique newspaper articles

Figure 10.5 News-filtering process.

### 10.3.5. Step 5 (Text Vectorization–Tokenization)

Subsequently, the feature text identification or tokenization started with the word embedding, applying the Word2Vec function, which provides concepts for the word embedding (Goldberg & Levy, 2014). The Word2Vec method identifies text mapping and then creates a model for reproducing such mappings to generate “word embedding” (given a text corpus), which is the process of mapping words to a vector space to realize statistical and probabilistic operations. The most important objective of this method is to preserve the relation between words, this is minimizing the distance between vectors within a similar context. For example, while through a tokenization, it is possible to represent the word flood in a text corpus X as [0,0,0,0,0,0,1,0,0,0,0,0] and the word drought as [0,0,1,0,0,0,0,0,0,0,0,0], where the vector size is equal to the vocabulary in the text corpus, these vectors do not show any relation between the meaning of the words flood and drought, both extreme event opposites within the hydrological cycle.
