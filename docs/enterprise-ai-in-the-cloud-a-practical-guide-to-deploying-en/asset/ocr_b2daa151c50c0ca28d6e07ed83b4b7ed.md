![](bbox=[0.129, 0.091, 0.873, 0.385])

FIGURE 15.3: Data collection process

**NOTE** Data can be collected from various sources such as sensors, time-series data, event data, IoT data, and social media using API or SQL query, web scraping, or direct downloads.

Data that's collected must be ingested into various storage facilities using real-time or batch processing. The following table compares the pros and cons of the two methods:

| DATA INGESTION METHOD | DESCRIPTION | EXAMPLE USE CASE | PROS | CONS |
|---|---|---|---|---|
| Real-time data ingestion | For real-time data ingestion, you must use a real-time processing system such as Apache Kafka or AWS Kinesis. | Customer reviews can be smaller in volume but high in velocity as new reviews keep coming in. For this scenario, a real-time ingestion method is appropriate. | Handles high velocity data; ensures data is current | Requires specific tools and systems and is not suitable for large volume data. |