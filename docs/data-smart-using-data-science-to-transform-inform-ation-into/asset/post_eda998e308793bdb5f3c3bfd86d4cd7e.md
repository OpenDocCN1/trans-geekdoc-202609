
Cluster 5 is the pinot noir cluster once again (see Figure 4.49).

| Offer # | Offer date | Product | Minimum t... | Discount | Origin | Past Peak | 5 |
|---|---|---|---|---|---|---|---|
| 24 | September | Pinot Noir | 6 | 34 | Italy | FALSE | 12 |
| 26 | October | Pinot Noir | 144 | 83 | Australia | FALSE | 11 |
| 2 | January | Pinot Noir | 72 | 17 | France | FALSE | 8 |
| 17 | July | Pinot Noir | 12 | 47 | Germany | FALSE | 7 |
| 1 | January | Malbec | 72 | 56 | France | FALSE | 2 |
| 11 | May | Champagne | 72 | 85 | France | FALSE | 1 |
| 28 | November | Cabernet Sau | 12 | 56 | France | TRUE | 1 |
| 23 | September | Chardonnay | 144 | 39 | South Africa | FALSE | 1 |
| 27 | October | Champagne | 72 | 88 | New Zealand | FALSE | 1 |
| 10 | April | Prosecco | 72 | 52 | California | FALSE | 1 |
| 20 | August | Cabernet Sau | 72 | 82 | Italy | FALSE | 0 |
| 22 | August | Champagne | 72 | 63 | France | FALSE | 0 |
| 31 | December | Champagne | 72 | 89 | France | FALSE | 0 |
| 9 | April | Chardonnay | 144 | 57 | Chile | FALSE | 0 |

**Figure 4.49:** Sorting on cluster 5—mainly pinot noir

That feels a lot cleaner, doesn’t it? That’s because in the K-medians case, using an asymmetric distance measure like cosine distance, you can cluster customers based on their interests more than their disinterests. That’s really what you care about.

If you made it through the chapter, you should feel confident not only about how to cluster data but also which questions can be answered in business through clustering and how to prepare your data to make it ready to cluster.

K-means clustering has been around for decades, but it’s not the most “current” clustering technique. In Chapter 5, “Cluster Analysis Part II: Network Graphs and Community Detection,” you’ll explore using network graphs to find communities of customers within this same dataset. You’ll even take a field trip outside of Excel, very briefly, to visualize the data.

See you there!

## 5 Cluster Analysis Part II: Network Graphs and Community Detection

Consider your customers. They buy similar things, and in that way, they’re related to each other. We can say that some customers are “friendlier” than others, they’re interested in the same stuff, and thus they have a stronger relationship between one another. Others are not related at all, because they don’t like the same things and rarely if ever buy the same stuff.

By thinking about how related or not related each customer is to the others, you can identify communities of customers without needing to plant a set number of flags in the data that get moved around until people feel at home, like we did in Chapter 4, “Cluster Analysis Part I: Using K-means to Segment Your Customer Base.”

One way to achieve this is through a *network graph*. In fact, network graphs are used across many fields to connect people, stuff, and concepts. Indeed, the same graph could even model multiple entity types: cities, phone numbers, and equipment. The connections can also represent different relationship types and strengths.

A network graph, as you’ll see in the next section, is a simple way to store and visualize entities that are connected. When doing cluster analysis on a network, people often use the term *community detection* instead, which makes sense because many network graphs are social in nature and their clusters do indeed make up communities. This chapter focuses on a particular community detection algorithm called *modularity maximization*.

At a high level, modularity maximization rewards you every time you place two good friends in a cluster together and penalizes you every time you shove some strangers together. By grabbing all the rewards you can and avoiding as many penalties as possible, the technique leads to a natural clustering of customers. And here’s the cool part, which you’ll see later—unlike the K-means clustering approach, you don’t need to choose K. The algorithm does it for you! In this way, the clustering technique used here takes *unsupervised* machine learning to a whole new level of knowledge discovery.

> See the section “Supervised vs. Unsupervised Machine Learning” in Chapter 4 for a refresher on the differences.

### What Is a Network Graph?

> The Excel workbook FriendsGraph.xlsx is available for download at the book's website at www.wiley.com/go/datasmart2e.

A network graph is simple. It’s made up of *nodes* connected by relationships. Those relationships are called *edges*.

For instance, you could have nodes that are Facebook users and other nodes that are product pages they like. Those “likes” comprise the edges of the graph. Similarly, you could create a network graph of all the stops on your city’s transportation system, or all the destinations and routes on a flight map (in fact, if you look at the route map on any airline’s website, you’ll see it’s a canonical network graph). These graphs allow analysts to discover all sorts of insights both visually and algorithmically, such as clusters, outliers, local influencers, and bridges between different groups.

In the next section, we’ll go through visualizing a simple networking graph in Excel just so you can get a feel for how everything works.

### Visualizing a Simple Graph

You remember *Friends*, right? It was a popular millennial sitcom (you know, the kind I grew up with). The show centered around six friends: Ross, Rachel, Joey, Chandler, Monica, and Phoebe.

These characters become involved in a lot of interesting relationships: real romances, fantasy romances that never amount to anything, play romances based on some dare or competition, and so on.

Think of these characters as six nodes or vertices on the graph. The relationships between them are edges. Off the top of my head, I can think of these edges:

- Ross and Rachel, obviously.
- Monica and Chandler end up married.
- Joey and Rachel have a little romance going but ultimately decide it's too weird (that's real).
- Chandler and Rachel meet each other in a flashback episode.
- Chandler and Phoebe play at a relationship and end up having to kiss.

These six characters and their five edges can be visualized as shown in Figure 5.1.

![](img/9c4b3d77873bec9e7da149a75c568d36_136_0.png)

Figure 5.1: A diagram of relationships on Friends

Pretty simple, right? Nodes and edges.

Figure 5.1 is what's called an undirected network graph. By undirected, we are implying the relationship between each node is mutual. Or, at the very least, we are keeping the direction of the relationship ambiguous. For this moment, we care more that these people are connected rather than the direction of their connection.

On the other hand, in a directed network, the connections have arrows and the direction of the arrows is important. Thus, the easiest way to remember the difference is that a directed network has arrows and an undirected network does not.

Excel has a very simple add-in called GiGraph that allows you to create and visualize a network graph using an Excel table very quickly. (GiGraph requires an Internet connection to use.) Unfortunately, GiGraph can make only directed graphs. In Excel, we'll re-create the Friends graph in Figure 5.1 as a directed network graph to show you one way to store this data mathematically and to demonstrate the differences between each type.

To implement this type of chart in Excel, we'll need some type of table structure to represent each relationship. The easiest representation of these relationships is an adjacency list. An adjacency list stacks each edge as a row and records the connecting nodes. Table 5.1 shows an adjacency list for the Friends graph in Figure 5.1.

Table 5.1: Simple network graph representation of Friends

| From | To | Value |
| :--- | :--- | :--- |
| Ross | Rachel | 1 |
| Rachel | Chandler | 1 |
| Rachel | Joey | 1 |
| Chandler | Monica | 1 |
| Chandler | Phoebe | 1 |

Go ahead and open the file FriendsGraph.xlsx. We'll take a look at a simple graph network in Microsoft Excel.

Once open, start on the Friends Graph worksheet tab. Notice that I've already placed the data in Excel as an adjacency list. Also take note that the data is in an Excel table, which is what GiGraph will need to read the data. To create a graph network from this data, we'll have to insert a content add-in. To that, go to the Insert tab and select Get Add-ins (see Figure 5.2).

![](img/9c4b3d77873bec9e7da149a75c568d36_137_0.png)

Figure 5.2: Get Add-ins on the Insert tab

From within the Office Add-Ins store, search for giGraph. When you find it, click the Add button (see Figure 5.3).
