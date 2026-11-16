![](bbox=[0.252, 0.094, 0.766, 0.619])

The XML web publishing framework separates web content generation into three different steps:

+   - **XML Creation**
+   Content owners create and develop the XML file(s). The content owners do not need to know anything about how their content is processed or presented. In our applications, the business logic layer will be responsible for generating the XML content. Some database vendors are enabling their databases to produce XML data directly out of `SELECT` statements.

+   - **XML Processing**
+   The XML file is processed. Any intermediate logic is applied here. This step may be eliminated depending on how step 1 was performed. See Chapter 21 for an example of XML processing.

+   - **XSL Rendering**
+   Applying an XSL style sheet renders the document generated in step 2. Specific formatting is applied, resulting in a document applicable to the requesting client. Possible outputs are HTML, PDF, WML, XML, and others.