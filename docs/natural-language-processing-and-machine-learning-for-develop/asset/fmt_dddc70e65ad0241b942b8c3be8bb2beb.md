
There are three major types of algorithms that are used for recommendation systems, as shown in the following list:

*   collaborative filtering (similar users)

*   content-based approaches (item features)

*   a hybrid of the first two

In highly simplified terms, collaborative filtering makes recommendations to a user based on another user who has similar preferences. This technique obviously requires some users, and the initial absence of users is called the “cold start” problem. By contrast, a content-based approach recommends a new item to a user based on the similarity of the features of that item to an existing (and similar) item. A hybrid approach can start with a content-based approach (which does not suffer from the cold start problem), and then use a collaborative filtering approach.

These three approaches are discussed in greater detail in a subsequent section, after we explore some of the aspects of a movie recommender system, which is the topic of the next section.

### **Movie Recommender Systems**

A movie recommender system is familiar to most people, and in simple terms, the goal of such a system is to create an accurate list of recommendations to its users. A recommendation list takes into account the movies that a user has seen, the ratings assigned to movies by each user, along with a mix of other factors.

Suppose that we have a matrix R with m rows (users) and n columns (movies), and each entry in matrix R is a movie rating, which can be a number between 1 and 5 inclusive or a floating point number between 0 and 1. Matrix R can have millions of rows and tens of thousands of movies. In addition, matrix R probably has some relationships that can provide useful information. For example, it’s possible to have the following:

*   two equal rows (two users have the same movie ratings)

*   two equal columns (two movies have the same ratings by multiple users)

*   a third row is the sum of two other rows (can you guess how?)

Here is an example of a matrix R that consists of four users and four movies, with movie ratings expressed as a floating point number between 0 and 1:

       M1  M2   M2   M4 Alice  1   -    0.2  - Edward -   0.5  -    0.3 Steve  1   -    1    - David  1   -    -    0.4 

As you can see, there are some missing entries in the preceding matrix: the goal of a recommender system is to infer values for the missing entries.

Now consider the following rating matrix R in which all numeric ratings are equal to 2, along with one missing value:

       M1  M2  M2  M4 Alice  2   2   2   2 Edward 2   2   2   2 Steve  2   2   2   ? David  2   2   2   2 

The obvious choice for the missing value in the preceding matrix R is 3. Now try to infer the missing value in the following matrix R:

       M1  M2  M2  M4 Alice  3   1   1   2 Edward 1   2   4   3 Steve  3   1   1   ? David  4   3   5   4 

What is the missing value in the preceding matrix? If you guessed 2, you are correct: this value is inferred from the fact that Alice and Steve have three identical ratings, and since Alice rated M4 with the value 2, we can infer that Steve would also rate this movie with a value of 2.

### **Factoring the Rating Matrix R**

As you learned in a previous section, the rating matrix R can be massive, which will degrade performance when processing this matrix for information. Fortunately, we can avail ourselves of a technique called *matrix factorization*, which is discussed here (other online articles might be easier to read):

*[https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems))*

Let’s suppose that each row of R is a movie and there are 1,000 movies. In addition, suppose that each column of R is a user, and there are 2,000 users. Then the array R has 2,000,000 entries (and is also sparse).

However, we can decompose the matrix R into the product of two matrices M and U. Specifically, M is a 1000×100 matrix of consisting of movies and features for its rows and columns, respectively. In addition, matrix U is a 100×2000 matrix consisting of features and users for its rows and columns respectively. The matrices M and U are compatible, because their product is (1000×100) × (100×2000), which is a matrix of dimensionality 1000×2000: this is also the dimensionality of matrix R. Moreover, the content of the rows and columns of M\*U matches the content of the rows and columns of matrix R.

The following section describes a new type of recommendation system, followed by the two main types of recommendation systems that were mentioned earlier in this chapter.

## **Content-Based Recommendation Systems**

The premise of content-based recommendation systems is simple: if you like an item, you will probably like a “similar” item. In situations where it’s easy to determine the context or properties of each item, a recommendation that’s based on the similarity of the items generally works well. For example, recommending the same kind of item such as a movie, book, song, or restaurant recommendation.

Content-based recommendation systems are classified in two broad categories: (1) a technique that analyzes only the description of the content and (2) a technique that involves building user profiles and item profiles. Both techniques are discussed in the following subsections.

### **Analyzing only the Description of the Content**

This technique is similar to item-based collaborative filtering: this means that the system recommends anything similar to previously items that are marked as “liked.” The advantages of this technique are listed below:

*   avoids the “new item problem” if descriptions are meaningful

*   semantic information and inferences can be used

*   easier to create more transparent systems

This technique also has the following disadvantages:

*   content-based recommendation systems tend to overspecialize

*   they will recommend items similar to those already consumed

*   the preceding also has a tendency of creating a “filter bubble”

### **Building User Profiles and Item Profiles**

One technique for creating use profiles utilizes a description or attributes from items the user has previously interacted with in order to recommend similar items. This technique depends only on the user previous choices. This technique is robust to avoid the cold-start problem,” and it’s also simple to use for textual items (such as articles, news, and books).

## **Collaborative Filtering Algorithm**

The premise of collaborative algorithm can be illustrated with the following simple example. Suppose that person A likes items 1, 2, and 3, whereas person B likes items 2, 3, and 4. As you can see, A and B have similar interests, and so we infer that A would like item 4 (because B likes it) and that B would like item A (because A likes it).

As a concrete example, suppose you go to a restaurant and then you ask the wait staff (or someone in your group) for a recommendation: this is an example of collaborative filtering.

A few points to keep in mind regarding the collaborative filtering algorithm:

*   The algorithm is entirely based on past behavior.

*   It is not based on the context.

*   It is independent of any other information.

*   This is a commonly used algorithm.

### **User–User Collaborative Filtering**

This technique involve searching for customers similar to a given customer, finding products that they like, and then suggesting those products to the given customer. This is a very effective algorithm that also requires a lot of time and resources because information about *every* customer pair must be determined. In case of very large platforms, this algorithm is difficult to implement without a very strong parallelizable system.

### **Item–Item Collaborative Filtering**

This technique is similar to user–user collaborative filtering, with the following points:

find item lookalike instead of customer look alike
