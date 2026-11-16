
Frame and on a Folium map. Other popular document databases include Amazon DynamoDB (also a key-value database), Microsoft Azure Cosmos DB and Apache CouchDB.

https://db-engines.com/en/ranking.

## 16.3.3 NoSQL Columnar Databases

In a relational database, a common query operation is to get a specific column's value for every row. Because data is organized into rows, a query that selects a specific column can perform poorly. The database system must get every matching row, locate the required column and discard the rest of the row's information. A columnar database 7, 8, also called a column-oriented database, is similar to a relational database, but it stores structured data in columns rather than rows. Because all of a column's elements are stored together, selecting all the data for a given column is more efficient.

https://en.wikipedia.org/wiki/Columnar_database.

https://www.predictiveanalyticstoday.com/top-wide-columnar-store-databases/.

Consider our authors table in the books database:

Click here to view code image

| id | first | last |
|---|---|---|
| 1 | Paul | Deitel |
| 2 | Harvey | Deitel |
| 3 | Abbey | Deitel |
| 4 | Dan | Quirk |
| 5 | Alexander | Wald |

In a relational database, all the data for a row is stored together. If we consider each row as a Python tuple, the rows would be represented as (1, 'Paul', 'Deitel'), (2, 'Harvey', 'Deitel'), etc. In a columnar database, all the values for a given column would be stored together, as in (1, 2, 3, 4, 5), ('Paul', 'Harvey', 'Abbey', 'Dan', 'Alexander') and ('Deitel', 'Deitel', 'Deitel', 'Quirk', 'Wald'). The elements in each column are maintained in row order, so the value at a given index in each column belongs to the same row. Popular columnar databases include MariaDB ColumnStore and HBase.

## 16.3.4 NoSQL Graph Databases

A graph models relationships between objects. 9 The objects are called nodes (or vertices) and the relationships are called edges. Edges are directional. For example, an edge representing an airline flight points from the origin city to the destination city, but not the reverse. A graph database 0 stores nodes, edges and their attributes.

https://en.wikipedia.org/wiki/Graph_theory.

https://en.wikipedia.org/wiki/Graph_database.

If you use social networks, like Instagram, Snapchat, Twitter and Facebook, consider your social graph, which consists of the people you know (nodes) and the relationships between them (edges). Every person has their own social graph, and these are interconnected. The famous “six degrees of separation” problem says that any two people in the world are connected to one another by following a maximum of six edges in the worldwide social graph.¹ Facebook’s algorithms use the social graphs of their billions of monthly active users ² to determine which stories should appear in each user’s news feed. By looking at your interests, your friends, their interests and more, Facebook predicts the stories they believe are most relevant to you. ³

https://en.wikipedia.org/wiki/Six_degrees_of_separation.

https://zephoria.com/top-15-valuable-facebook-statistics/.

https://newsroom.fb.com/news/2018/05/inside-feed-news-feed-ranking/.

Many companies use similar techniques to create recommendation engines. When you browse a product on Amazon, they use a graph of users and products to show you comparable products people browsed before making a purchase. When you browse movies on Netflix, they use a graph of users and movies they liked to suggest movies that might be of interest to you.

One of the most popular graph databases is Neo4j. Many real-world use-cases for graph databases are provided at:

```
https://neo4j.com/graphists/
```

With most of the use-cases, sample graph diagrams produced by Neo4j are shown. These visualize the relationships between the graph nodes. Check out Neo4j’s free PDF book, Graph Databases. ⁴

https://neo4j.com/graph-databases-book-sx2.

## 16.3.5 NewSQL Databases

Key advantages of relational databases include their security and transaction support. In particular, relational databases typically use ACID (Atomicity, Consistency, Isolation, Durability) ⁵ transactions:

https://en.wikipedia.org/wiki/ACID_(computer_science).

- Atomicity ensures that the database is modified only if all of a transaction’s steps are successful. If you go to an ATM to withdraw $100, that money is not removed from your account unless you have enough money to cover the withdrawal and there is enough money in the ATM to satisfy your request.
- Consistency ensures that the database state is always valid. In the withdrawal example above, your new account balance after the transaction will reflect precisely what you withdrew from your account (and possibly ATM fees).
- Isolation ensures that concurrent transactions occur as if they were performed sequentially. For example, if two people share a joint bank account and both attempt to withdraw money at the same time from two separate ATMs, one transaction must wait until the other completes.
- *Durability* ensures that changes to the database survive even hardware failures.

If you research benefits and disadvantages of NoSQL databases, you'll see that NoSQL databases generally do not provide ACID support. The types of applications that use NoSQL databases typically do not require the guarantees that ACID-compliant databases provide. Many NoSQL databases typically adhere to the **BASE (Basic Availability, Soft-state, Eventual consistency)** model, which focuses more on the database's availability. Whereas, ACID databases guarantee consistency when you write to the database, BASE databases provide consistency at some later point in time.

NewSQL databases blend the benefits of both relational and NoSQL databases for big-data processing tasks. Some popular NewSQL databases include VoltDB, MemSQL, Apache Ignite and Google Spanner.

## 16.4 CASE STUDY: A MONGODB JSON DOCUMENT DATABASE

MongoDB is a document database capable of storing and retrieving JSON documents. Twitter's APIs return tweets to you as JSON objects, which you can write directly into a MongoDB database. In this section, you'll:

- use Tweepy to stream tweets about the 100 U.S. senators and store them into a MongoDB database,
- use pandas to summarize the top 10 senators by tweet activity and
- display an interactive Folium map of the United States with one popup marker per state that shows the state name and both senators' names, their political parties and tweet counts.

You'll use a free cloud-based MongoDB Atlas cluster, which requires no installation and currently allows you to store up to 512MB of data. To store more, you can download the MongoDB Community Server from:

Click here to view code image

```
`https://www.mongodb.com/download-center/community`
```

and run it locally or you can sign up for MongoDB's *paid* Atlas service.

### Installing the Python Libraries Required for Interacting with MongoDB

You'll use the *pymongo* library to interact with MongoDB databases from your Python code. You'll also need the *dnspython* library to connect to a MongoDB Atlas Cluster. To install these libraries, use the following commands:

Click here to view code image

```
conda install -c conda-forge pymongo
conda install -c conda-forge dnspython
```

## keys.py

The ch16 examples folder's TwitterMongoDB subfolder contains this example's code and keys.py file. Edit this file to include your Twitter credentials and your OpenMapQuest key from the “Data Mining Twitter” chapter. After we discuss creating a MongoDB Atlas cluster, you'll also need to add your MongoDB connection string to this file.

### 16.4.1 Creating the MongoDB Atlas Cluster

To sign up for a free account go to

```
https://mongodb.com
```

then enter your email address and click **Get started free**. On the next page, enter your name and create a password, then read their terms of service. If you agree, click **Get started free** on this page and you'll be taken to the screen for setting up your cluster. Click **Build my first cluster** to get started.

They walk you through the getting started steps with popup bubbles that describe and point you to each task you need to complete. They provide default settings for their free Atlas cluster (**Mo** as they refer to it), so just give your cluster a name in the **Cluster Name** section, then click **Create Cluster**. At this point, they'll take you to the **Clusters** page and begin creating your new cluster, which takes several minutes.

Next, a **Connect to Atlas** popup tutorial will appear, showing a checklist of additional steps required to get you up and running:

- **Create your first database user**—This enables you to log into your cluster.
- **Whitelist your IP address**—This is a security measure which ensures that only IP addresses you verify are allowed to interact with your cluster. To connect to this cluster from multiple locations (school, home, work, etc.), you'll need to whitelist each IP address from which you intend to connect.
- **Connect to your cluster**—In this step, you'll locate your cluster's connection string, which will enable your Python code to connect to the server.

### Creating Your First Database User

In the popup tutorial window, click **Create your first database user** to continue the tutorial, then follow the on-screen prompts to view the cluster's **Security** tab and click + **ADD NEW USER**. In the **Add New User** dialog, create a username and password. Write these down—you'll need them momentarily. Click **Add User** to return to the **Connect to Atlas** popup tutorial.

### Whitelist Your IP Address

In the popup tutorial window, click **Whitelist your IP address** to continue the tutorial, then follow the on-screen prompts to view the cluster's **IP Whitelist** and click + **ADD IP**
