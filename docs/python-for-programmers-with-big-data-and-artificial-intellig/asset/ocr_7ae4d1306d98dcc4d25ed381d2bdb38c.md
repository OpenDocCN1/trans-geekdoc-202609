+   - Most apps created today use at least some open-source software. You’ll take advantage of many open-source libraries and tools throughout this book.
+   
+   - Waze communicates information over the Internet between their servers and their users’ mobile devices. Today, such data often is transmitted in JSON (JavaScript Object Notation) format, which we’ll introduce in hapter 9 and use in subsequent chapters. The JSON data is typically hidden from you by the libraries you use.
+   
+   - Waze uses speech synthesis to speak driving directions and alerts to you, and speech recognition to understand your spoken commands. We use IBM Watson’s speech-synthesis and speech-recognition capabilities in hapter 13.
+   
+   - Once Waze converts a spoken natural-language command to text, it must determine the correct action to perform, which requires natural language processing (NLP). We present NLP in hapter 11 and use it in several subsequent chapters.
+   
+   - Waze displays dynamically updated visualizations such as alerts and maps. Waze also enables you to interact with the maps by moving them or zooming in and out. We create dynamic visualizations with Matplotlib and Seaborn throughout the book, and we display interactive maps with Folium in hapters 12 and 6.
+   
+   - Waze uses your phone as a streaming Internet of Things (IoT) device. Each phone is a GPS sensor that continuously streams data over the Internet to Waze. In hapter 16, we introduce IoT and work with simulated IoT streaming sensors.
+   
+   - Waze receives IoT streams from millions of phones at once. It must process, store and analyze that data immediately to update your device’s maps, to display and speak relevant alerts and possibly to update your driving directions. This requires massively parallel processing capabilities implemented with clusters of computers in the cloud. In hapter 6, we’ll introduce various big-data infrastructure technologies for receiving streaming data, storing that big data in appropriate databases and processing the data with software and hardware that provide massively parallel processing capabilities.
+   
+   - Waze uses artificial-intelligence capabilities to perform the data-analysis tasks that enable it to predict the best routes based on the information it receives. In hapters 14 and 5 we use machine learning and deep learning, respectively, to analyze massive amounts of data and make predictions based on that data.
+   
+   - Waze probably stores its routing information in a graph database. Such databases can efficiently calculate shortest routes. We introduce graph databases, such as Neo4J, in hapter 16.
+   
+   - Many cars are now equipped with devices that enable them to “see” cars and obstacles around them. These are used, for example, to help implement automated braking systems and are a key part of self-driving car technology. Rather than relying on users to report