+   - Unlike relational databases, there is no standard for the structure of key-value stores. There is little opportunity for the transfer of expertise from one key-value product to another because each uses its own proprietary functions and methodologies.
+   - Key-value stores are generally not well equipped to provide the kind of support for the ACID properties that are usually associated with relational systems. Transactions are generally limited to operations on a single data unit.
+   - There is limited scope for the validation of data or the application of constraints within the data store. Again, such operations must be carried out by the application code before the data is stored or after it is retrieved as a unit.

Identifying the right key-value store, or even deciding if a key-value store is appropriate, will depend heavily on the requirements of each individual case. Key-value stores are very well suited to applications that require rapid access to an individual unit of complex data from a very large pool of similar units. Some typical use cases include the following:

*Caching.* Data that is frequently accessed can be stored in a key-value data store for faster retrieval. This can help to improve application performance and reduce latency. For example, an e-commerce website may use a key-value data store to cache the product information for popular products so that the website can be served quickly without querying the traditional database every time.

*Session management.* A key-value data store can be useful in applications where a user's session needs to be maintained across multiple requests or across multiple servers. Values such as log-in information and shopping cart contents can be held for quick retrieval of the information when needed.

*Storing user preferences.* User preferences can be stored as key-value pairs, allowing for easy retrieval and updating of user preferences. This can be useful in applications where users need to be able to customize their experience or where user preferences need to be shared across multiple devices.

*Content management.* Digital content is now commonplace. This includes text, images, videos, documents, and other multimedia assets. An application may need to collect diverse kinds of media into a collection that can be stored and retrieved as a single unit, which is ideally suited to a key-value store.

# # 17.3 Column-Oriented Databases

The main difference between column-oriented databases and relational databases is how data is organized and stored rather than the logical structure of the data. A relational database stores information in tables, organized into rows and columns. A table can be thought of as information about a particular type of entity, with each row representing an individual entity of that type and the columns containing values that are relevant to that entity type. A row is often described as a record, and the related column values as fields of that record. The main focus is on managing records, so it is legitimate to describe this type of database as row-oriented.