# 70 Chapter 3: Data Conditioning

(e.g., Snowflake and Databricks). At present, both Snowflake and Databricks are dominant in their specialties, with a market capitalization of tens of billions of dollars, which gives an indication of how significant data management and storage are to modern data processing and AI.

Databricks uses something that it calls the "datahouse," a platform meant to combine the best of data warehouses and data lakes [23]. Data warehouses primarily store data in structured format, where data lakes predominantly store data in unstructured format [24–26].

There is an ongoing trend to use AI in business intelligence, well as integrating structure, semructured, and unstructured data into the decision support workflow for a modern AI organization. This trend is very healthy for the AI community to looking at databases and types as uniquely distinct environments. The digital transformation platform, discussed earlier, should incorporate these databases and data types into an integrated data environment.

An organization that has implemented a digital transformation, owning a modern platform infrastructure, can create value by either performing the process of Extract-Transform-Load (ETL) or Extract-Load-Transform (ELT), across data environments (e.g., data warehouses, data lakes, or data houses). In the data-conditioning stage, ETL is employed in the data manipulation flow using the data and database-management tools described earlier. ELT, in addition to reversing the operation of load and transform, is becoming the accepted data manipulation flow for a large volume of unstructured data, with data processing occurring close to where the data is stored (minimizing latency). An excellent resource to stay abreast of changes in the data and AI ecosystem is by Matt Turk (a venture capitalist at FirstMark), who regularly writes a comprehensive post with relevant updates [28].

So far, we have articulated the need for an AI organization to undergo a digital transformation in order to achieve a modern platform infrastructure. This platform utilizes the best of database management tools and techniques necessary to implement the data-conditioning stage. The next steps, after these foundational pieces are in place, are to perform data quality assessment, cleaning, and preparation prior to the ML stage. The next section elaborates on these data-processing functions in more detail.

# 3.4 Data Quality, Cleaning, and Preparation

The third-tier component of our earlier discussion of the transitioning and scaling of AI products and services is to focus on data-centric AI instead of putting the majority of the emphasis on model-centric AI. "Data-centric AI" simply refers to between the