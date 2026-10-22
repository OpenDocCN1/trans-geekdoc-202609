
Next, the authors compared the metadata schemas and application domains to determine their relevance and usefulness in different cases. The authors create a decision table that shows the compatibility of each metadata schema with the various application domains. They find that MPEG-7 scores well for all domains but note some interoperability issues. FreeDB and MusicBrainz are best suited for music retrieval, while MusicXML is highly relevant for musical notation. The paper concludes by emphasizing that no single metadata standard covers all the requirements for music metadata. The choice of metadata schema depends on the specific application and its functionality. The proposed framework and decision table can assist users in selecting the most suitable metadata schema for their needs.

Overall, the paper highlights the importance of metadata in music applications and provides a framework for comparing different metadata schemas. It offers insights into the strengths and limitations of various metadata standards and their compatibility with different application domains.

## AIM AND OBJECTIVE OF PROPOSED SOFTWARE

To utilize Data Mining and Machine Learning principles to develop a piece of software that can Achieve the following tasks with regards to songs without metadata:

- Extract Title from Current File name, along with Artist name (If possible), save it to a database.
- Data Scraper for each Title of Song – Find the following metadata parameters and save to database using principles of Data Mining of various sources like Wikipedia, Spotify, shazam, etc. And aggregating the following results (using a classification algorithm) to find the best fit for the following parameters: file name, path, Tag, Title, Artist, Album, Year, Track, Genre, Comment, Album Artist, Composer, Disc number, album art jpg file.
- Automate process for all songs metadata addition. Make it user friendly via a GUI based python application/API.

## METHODOLOGY

The implementation plan is fairly straightforward. We are to deploy an automation software that can data mine (data scrape) the required metadata from various sources like google searches, Wikipedia, Spotify Databases, etc. This metadata is then applied to the required songs along with appropriate cover art. Figure 3 depicts the Process Flow Diagram employed for the project at hand. Thus, this software under complete implementation can be used to successfully perform its required actions, under optimal conditions.

As shown in the diagram above, the overall process flow is demonstrated. The Application begins by loading songs into the database from any given directory. The file name and file path columns within the Database are populated accordingly. Next the title generator module takes over Process Flow. The Title Generator employs a regex function to get ‘cues’ from file names. Cues are basically clues that enable the Data Scraper to better scrape data for a given Music file. If no cues are found, the Data Scraper will utilise the mp3 file’s sound signature to identify a song. This search avenue is handled by means of the Shazam API. The two main cues are the Artist Name and the Title. If found, they are placed in the database for further processing. Process then moves forward into the Data Scraper section. This section

Figure 2. Process flow diagram

![](img/4a898a1f1442f24bfffba36e7ac62ad8_238_0.png)

employs the use of multiple ‘search avenues’ to obtain various sets of metadata from various sources. These currently include ordinary Google searches, Wikipedia API searches, Google Images (For Album Art), Shazam API, Spotify API. Etc. The possibilities for scraping are endless, with only a need for interfacing within the given system This is further discussed in Sections 5.1 and 5.2.

Each search avenue returns a set of metadata depending on the cues obtained from the regex function. The metadata is then pushed into the classification unit, which decides the best fit data for each field based on majority. Currently, a Naïve Bayes Classifier is utilised for the same, with equal weightage given to all search avenues. Alternatives are further explored in Sections 8 and 9.

## HOW DATA MINING IS UTILIZED IN GIVEN APPLICATION

Data Mining is simply the process of sorting and searching through a large pool of data (here obtained via Data Scraping) to gain inferences and find patterns within a given dataset. Data Scraping is just the means for obtaining the data required. The given application employs multiple search avenues to handle this process, however, to improve performances, it is necessary to employ as many search avenues as possible. These include sites that do not have standard API’s, or those that just display XML/HTML files on request. To extract the data that we need, we need to employ the use of specialised functions, like BeautifulSoup from Python.

As seen in the above case scenario, data is available everywhere, even within the first site page present on providing a search query. As seen in figure, searching for the cues ‘runaway’ and ‘Aurora’, we are able to gather multiple data points, like the Album Name, Artist, Release Date, List of Genres, etc. This enables us to better equip the classifier with as much data as possible to handle anomalies and misinterpretations. Thus, these are the ways Data Scraping and Mining is employed in the given Application.

Figure 3. Google search: Avenue led data

![](img/4a898a1f1442f24bfffba36e7ac62ad8_239_0.png)

### The Need for Classification

The metadata is then pushed into the classification unit, which decides the best fit data for each field based on the majority specified. For the given application, we are using a Naïve Bayes Classifier. It is a supervised Machine Learning Algorithm, which is used for classification tasks, specifically text classification. It uses Bayesian Probability to determine how likely a given data point is accurate for a given song. For example, if a search avenue were to return data that is incorrect or corrupted, the most probable data point is added into the database. Naïve Bayes gives equal weightage to all the search avenues within the application. This is an important need overall to get the best fit data from the overall dataset for a given song. At its current stage, Classification is at its simplest, and can be greatly improved and optimized. This is further discussed in Section 8.

### Choice of Process Model for Given Implementation: V Model

As this is a relatively small project, which aims to encompass the technology of data mining into a meta tag editor, it seemed appropriate to go for the V-Model, which aims to give a working model at the end of the Project Cycle. As seen in the advantages section, it is a highly disciplined model which is completed one stage at a time. As mapped out in the Gantt chart, this would coincide with the objective of a V-Model type Project Model. The Project requirements are clear and well established, and since it only encompasses the three to four sub-models to fully implement, the project “Automated Mp3 tag Editor using Data Mining” can proceed under the V-Model Software Project Model type.

Figure 4. V model

![](img/4a898a1f1442f24bfffba36e7ac62ad8_240_0.png)

## IMPLEMENTATION: SOFTWARE DESIGN SPECIFICATIONS (SDS)

### Design Considerations

**System Environment:** As this is predominantly a data mining project, the language used is python for the entire app. Depending on live performances, a shift to java for the GUI components can be made. The database used is the python sqlite3 database, which is inbuilt into python 3. In case of Java, SQL (either Oracle or any other substitute) can be used.

**Design Methodology:** The major processes that will be used for the given project are in line with the Software Design Schema discussed in the course CSE3001 - Software Engineering. It is predominantly an Object-Oriented System Design (in terms of code design and implementation) Other design considerations included the methodology involved in designing use case scenarios and Classes present within OOP based design. These were specified via creation and usage of UML diagrams (See Figure 5) and UML diagrams (See Figure 4), as shown in this chapter.

**Risks and Volatile Areas:** Only major issue that can be discussed would be the possibility for a Python based exe file not being able to perform its tasks as required, in a stable and continuous form. Other than that, no other problems/volatile areas have been identified.

### Architecture

As mentioned before, the architecture used for the given project is Object Oriented. The components of the given system are to be encapsulated and the operations within the project must be applied accordingly to manipulate the given data. The subsequent communication between various components in the project scope is therefore established to be of the Object-Oriented type. Subsystem Components of given software are discussed below:
