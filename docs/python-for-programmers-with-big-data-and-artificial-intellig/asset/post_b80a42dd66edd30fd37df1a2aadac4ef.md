
procedural programming and object-oriented programming.

- We use best practices, emphasizing current idiom.
- **Functional-style programming** is used throughout the book as appropriate. A chart in Chapter 4 lists most of Python's key functional-style programming capabilities and the chapters in which we initially cover most of them.

## 538 Code Examples

- You'll get an engaging, challenging and entertaining introduction to Python with **538 real-world examples** ranging from individual snippets to substantial computer science, data science, artificial intelligence and big data case studies.
- You'll attack significant tasks with AI, **big data and cloud** technologies like **natural language processing**, **data mining Twitter**, **machine learning**, **deep learning**, Hadoop, MapReduce, Spark, IBM Watson, key data science libraries (**NumPy**, **pandas**, **SciPy**, **NLTK**, **TextBlob**, **spaCy**, **Textastic**, **Tweepy**, **Scikit-learn**, **Keras**), key visualization libraries (**Matplotlib**, **Seaborn**, **Folium**) and more.

## Avoid Heavy Math in Favor of English Explanations

- We capture the conceptual essence of the mathematics and put it to work in our examples. We do this by using libraries such as **statistics**, **NumPy**, **SciPy**, **pandas** and many others, which hide the mathematical complexity. So, it's straightforward for you to get many of the benefits of mathematical techniques like **linear regression** without having to know the mathematics behind them. In the **machine-learning** and **deep-learning** examples, we focus on creating objects that do the math for you “behind the scenes.”

## Visualizations

- **67 static, dynamic, animated and interactive visualizations** (charts, graphs, pictures, animations etc.) help you understand concepts.
- Rather than including a treatment of low-level graphics programming, we focus on high-level visualizations produced by **Matplotlib**, **Seaborn**, **pandas** and **Folium** (for **interactive maps**).
- We use visualizations as a pedagogical tool. For example, we make the **law of large numbers** “come alive” in a dynamic **die-rolling simulation** and bar chart. As the number of rolls increases, you’ll see each face’s percentage of the total rolls gradually approach 16.667% (1/6th) and the sizes of the bars representing the percentages equalize.
- Visualizations are crucial in big data for **data exploration** and **communicating reproducible research results**, where the data items can number in the millions, billions or more. A common saying is that a picture is worth a thousand words 5 —in **big data**, a visualization could be worth billions, trillions or even more items in a database. Visualizations enable you to “fly 40,000 feet above the data” to see it “in the large” and to get to know your data. **Descriptive statistics** help but can be misleading. For example, Anscombe’s quartet 6 **demonstrates through visualizations that _significantly different_ datasets can have _nearly identical_ descriptive statistics.**
- We show the visualization and animation code so you can implement your own. We also provide the animations in source-code files and as **Jupyter Notebooks**, so you can conveniently customize the code and animation parameters, re-execute the animations and see the effects of the changes.

5 https://en.wikipedia.org/wiki/A_picture_is_worth_a_thousand_words.
6 https://en.wikipedia.org/wiki/Anscombe%27s_quartet.

## Data Experiences

- Our **Intro to Data Science sections** and case studies in Chapters 11–16 provide rich data experiences.
- You'll work with many **real-world datasets and data sources**. There’s an enormous variety of **free open datasets** available online for you to experiment with. Some of the sites we reference list hundreds or thousands of datasets.
- Many libraries you'll use come bundled with popular datasets for experimentation.
- You'll learn the steps required to obtain data and prepare it for analysis, analyze that data using many techniques, tune your models and communicate your results effectively, especially through visualization.

## GitHub

- **GitHub** is an excellent venue for finding open-source code to incorporate into your projects (and to contribute your code to the open-source community). It’s also a crucial element of the software developer’s arsenal with version control tools that help teams of developers manage open-source (and private) projects.
- You'll use an extraordinary range of free and open-source Python and data science **libraries**, and **free, free-trial** and **freemium** offerings of software and cloud services. Many of the libraries are hosted on GitHub.

## Hands-On Cloud Computing

- Much of big data analytics occurs in the cloud, where it's easy to scale **dynamically** the amount of hardware and software your applications need. You’ll work with various cloud-based services (some directly and some indirectly), including **Twitter**, **Google Translate**, **IBM Watson**, **Microsoft Azure**, **OpenMapQuest**, **geopy**, **Dweet.io** and **PubNub**.
- We encourage you to use free, free trial or freemium cloud services. We prefer those that don’t require a credit card because you don’t want to risk accidentally running up big bills. **If you decide to use a service that requires a credit card, ensure that the tier you’re using for free will not automatically jump to a paid tier.**

## Database, Big Data and Big Data Infrastructure

- According to IBM (Nov. 2016), 90% of the world’s data was created in the last two years. 7 Evidence indicates that the speed of data creation is rapidly accelerating.
7 https://public.dhe.ibm.com/common/ssi/ecm/wr/en/wrl12345usen/watson-customer-engagement--watson-marketing-wr-other-papers-and-reports-rl12345usen-20170719.pdf.
- According to a March 2016 AnalyticsWeek article, within five years there will be over 50 billion devices connected to the Internet and by 2020 we'll be producing 1.7 megabytes of new data every second *for every person on the planet!* 8
8 https://analyticsweek.com/content/big-data-facts/.
- We include a treatment of **relational databases** and **SQL** with **SQLite**.
- Databases are critical **big data infrastructure** for storing and manipulating the massive amounts of data you'll process. Relational databases process **structured data**—they’re not geared to the **unstructured** and **semi-structured data** in big data applications. So, as big data evolved, **NoSQL** and **NewSQL databases** were created to handle such data efficiently. We include a NoSQL and NewSQL overview and a hands-on case study with a **MongoDB JSON document database**. MongoDB is the most popular NoSQL database.
- We discuss **big data hardware and software infrastructure** in Chapter 16, “Big Data: Hadoop, Spark, NoSQL and IoT (Internet of Things).”

## Artificial Intelligence Case Studies

- In case study chapters 11–15, we present artificial intelligence topics, including natural language processing, data mining Twitter to perform sentiment analysis, cognitive computing with IBM Watson, supervised machine learning, unsupervised machine learning and deep learning. Chapter 16 presents the big data hardware and software infrastructure that enables computer scientists and data scientists to implement leading-edge AI-based solutions.

## Built-In Collections: Lists, Tuples, Sets, Dictionaries

- There's little reason today for most application developers to build custom data structures. The book features a rich two-chapter treatment of Python's built-in data structures—lists, tuples, dictionaries and sets—with which most data-structuring tasks can be accomplished.

## Array-Oriented Programming with NumPy Arrays and Pandas Series/DataFrames

- We also focus on three key data structures from open-source libraries—NumPy arrays, pandas Series and pandas DataFrames. These are used extensively in data science, computer science, artificial intelligence and big data. NumPy offers as much as two orders of magnitude higher performance than built-in Python lists.
- We include in Chapter 7 a rich treatment of NumPy arrays. Many libraries, such as pandas, are built on NumPy. The Intro to Data Science sections in Chapters 7–9 introduce pandas Series and DataFrames, which along with NumPy arrays are then used throughout the remaining chapters.

## File Processing and Serialization

- Chapter 9 presents text-file processing, then demonstrates how to serialize objects using the popular JSON (JavaScript Object Notation) format. JSON is used frequently in the data science chapters.
- Many data science libraries provide built-in file-processing capabilities for loading datasets into your Python programs. In addition to plain text files, we process files in the popular CSV (comma-separated values) format using the Python Standard Library's csv module and capabilities of the pandas data science library.

## Object-Based Programming

- We emphasize using the huge number of valuable classes that the Python open-source community has packaged into industry standard class libraries. You'll focus on knowing what libraries are out there, choosing the ones you'll need for your apps, creating objects from existing classes (usually in one or two lines of code) and making them "jump, dance and sing." This object-based programming enables you to build impressive applications quickly and concisely, which is a significant part of Python's appeal.
- With this approach, you'll be able to use machine learning, deep learning and other AI technologies to quickly solve a wide range of intriguing problems, including cognitive computing challenges like speech recognition and computer vision.

## Object-Oriented Programming

- Developing custom classes is a crucial object-oriented-programming skill, along with inheritance, polymorphism and duck typing. We discuss these in Chapter 10.
- Chapter 10 includes a discussion of unit testing with doctest and a fun card-shuffling-and-dealing simulation.
