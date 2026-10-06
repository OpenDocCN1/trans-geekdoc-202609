
# CHAPTER 1 WORKING WITH NUMBERS: WHAT IS DATA, REALLY?

Although interactions are often recorded as new columns in the original dataset, aggregations create a totally new dataset. The columns are usually different from those in the original tabular data, and the rows almost always are. For instance, in the aggregated values of height by gender in Table 1-10, the only columns are Gender and Height, as opposed to Name, Height, Age, Gender, T-shirt Size, and Plays Sports of the original table. These datasets store two different things—one is a representation of individual patients and the other is a representation of attributes of groupings of patients.

## Metadata

I've already mentioned metadata, data that describes other data. It can be quite important in the data world.

### METADATA

The word “meta” is casually thrown around a lot, generally to indicate a higher layer of awareness to an experience or facts. It has the same meaning with data—data about data, or data about the information being represented in the data.

In a lot of ways, it doesn't matter if something is metadata or plain data. Both can be used in data science. For instance, imagine you collect all the tweets that mention a particular movie in the week of release because you're interested to see what people are saying. There will be a lot of data associated with the tweets that would largely be considered metadata, like the hashtags, timestamp of the tweet, the username posted, and the location of the IP address, and if you ran some automatic semantic analysis, a score representing sentiment (how positive or negative the post is). Most people will consider the text of the tweet data and all the other things metadata. But if you're studying hashtags and the sentiment they're associated with, that may be what you focus on, without even looking at the tweets directly.

Data about media is some of the most common metadata. Table 1-12 shows common metadata stored for different types of media (definitely not a comprehensive list).

## Table 1-12. Metadata fields associated with different types of media

| Movie | Video Game | Song | Book | Art |
| --- | --- | --- | --- | --- |
| Title | Title | Title | Title | Title |
| Release date | Release date | Album name | Author | Artist |
| Director | Studio | Artist name | Illustrator | Series |
| Producer | Genre | Release date | Editor | Creation date |
| Editor | Platform | Studio | Series | Medium |
| Actors | Score composer | Album release date | Series # | Style |
| Score composer | Artists | Running time | Publisher | Dimensions |
| Running time | Writers | Track number | Genre | Monetary value |
| Studio | Target age | Producer | Target age | |
| Rating | | | ISBN | | |

We can even have more metadata about some of this metadata. For instance, we would likely store information about all the people on these lists—directors, artists, authors, etc.—such as their names, gender, and agents.

Note that metadata can be stored in the same table—data and metadata can exist together, as long as it makes sense in terms of reality. Some other common metadata you see in databases includes timestamps for when record was created, a timestamp for when it was modified, and the creator of the record. Note that not all timestamps are metadata. If we record the time of a sales transaction on a cash register, that timestamp would not be metadata it represents a thing that happened in the real world—the sale itself. a “last updated” timestamp on the row for that transaction in a table indicating when row was last modified in some way would be metadata. For instance, imagine that the row contains a link to a generated PDF invoice, and a process is run nightly that adds the file size to the row modifies the last updated column with the time it does it. This is data about that row in the table and has nothing directly to do with the real-world transaction.

## Data Collection and Storage

How data is collected and stored is hugely important in data science and the data world in modern times, data is usually collected automatically from some types of computer systems and stored in different types of database systems. This is a result of evolution from manual processes and storage (like spreadsheets). Data collection and storage will both be covered in a later chapter.

## The Use of Data in Organizations

We hear a lot about big data, which is an amorphous term basically used to indicate large quantities of data. Data is usually considered big when processing it stretches computer resources, but that varies over time. What would have been considered a lot of data on a computer in 1995 would be considered minuscule today. Many organizations are collecting so much data that they are starting to stretch their resources, which definitely qualifies as big data.

One aspect of big data that it shares with “normal data” is that all of it exists for a purpose—to increase our understanding of the world. As previously discussed, data is an abstraction of reality. Once we’ve abstracted the world, we can use the data to better understand that world in some way, through data science or data analysis. To put this in this context, people have defined different levels of data. A famous diagram called the DIKW Pyramid in Figure 1-5 shows the progression of data from bottom to top as it becomes increasingly useful.

![](img/df37a23523ff92247f9125691b1edea2_66_0.png)

Figure 1-5. DIKW Pyramid

If the purpose of data is to help us become wiser about the world, then data analysis and data science are the main methods used to achieve that. Although the word information (or info) is often used synonymously with data, there is an important distinction in this diagram: in this view, information is data that has meaning. Beyond that, meaning is clearly useful, but it takes a collection of information to become knowledge. And finally, knowledge doesn’t instantly become wisdom. It has to build up over time.
