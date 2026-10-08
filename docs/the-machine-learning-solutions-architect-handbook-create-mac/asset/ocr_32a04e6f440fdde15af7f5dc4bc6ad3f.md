To understand Kendra works, let's review some of the key technical Amazon Kendra concepts:

+   **Index**: An index provides search results for the documents and FAQ lists that it has indexed. Kendra generates indexes and FAQ lists that allow them to be searched.

+   **Documents**: Documents can be structured (FAQs) and unstructured (HTML, PDFs) and can be indexed by the Kendra index engine.

+   **Data sources**: Data sources are locations where the documents are located. These can be S3 locations, Amazon RDS databases, and Google Workspaces drives, among others. Kendra has a list of built-in connectors for connecting to different data sources.

+   **Queries**: Queries are used for getting results from indexes. Queries can be natural language containing criteria and filters.

+   **Tags**: Tags are metadata that can be assigned to indexes, data sources, and FAQs.

There are two main steps in setting up Kendra to perform an intelligent search against your documents:

+   1. **Generate index**: The first step is to set up an index for your documents.

+   2. **Add documents to index**: Once the index has been created, you can add document sources to the index to be indexed.

Once the index has been created, you use the Kendra query() API to get responses for your index with queries. The following code snippet shows the Python syntax for querying index:

```
kendra = boto3.client('kendra')
query = '${searchString}'
index id = '${indexID}'
response=kendra.query(
QueryText = query, IndexError = index_id)
```

Kendra has built-in connectors for a range of data sources, so you don't have to build custom code to extract data from those sources. It also has native application integration with Amazon Lex, which allows Lex to send user queries directly to a Kendra index for fulfillment.