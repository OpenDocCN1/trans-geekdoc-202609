
# 18.7.2.1 Patient Generator

The Patient Generator extracts the attributes of a person from a set of web pages. [Algorithm 18.1](#ch18.xhtml#alg18_1) details the job of the patient generator.

```
http://www.yellowpages.com/findaperson?fap_terms%5Bfirst%5D="fname"
&fap_terms%5Blast%5D=" Lname "
&fap_terms%5Bstate%5D=" State "
&page=1"
```

[Figure 18.10](#ch18.xhtml#fig18_10a) shows the result when `fname`=`John`, `lname`=`Smith` and `State`=`CA`. We then extract the address and telephone number from the result page. [Figure 18.11](#ch18.xhtml#fig18_11a) shows the result of executing Algorithm 18.1 when the base uri is `www.whitepatges.com` and the parameters are `fname`=`John`, `lname`=`Smith` and `State`=`CA`. We then extract the address and age from the result page. [Figure 18.12](#ch18.xhtml#fig18_12a) is a list of attributes we collect for each patient in our provenance knowledge base.

![Figure 18.10 Partial page – Yellowpage.com.](images/fig18_10.jpg)

[Figure 18.10 Partial page –](#ch18.xhtml#Ffig18_10) [Yellowpage.com](http://Yellowpage.com).

![Figure 18.11 Partial page – Whitepage.com.](images/fig18_11.jpg)

[Figure 18.11 Partial page –](#ch18.xhtml#Ffig18_11) [Whitepage.com](http://Whitepage.com).

![Figure 18.12 Patient attributes.](images/fig18_12.jpg)

[Figure 18.12 Patient attributes.](#ch18.xhtml#Ffig18_12)

# 18.7.2.2 Physician Generator

The Physician Generator extracts information as attribute values for a doctor. We modify the line 1 of Algorithm 18.1 by replacing the value of the base URI to base `rateMd.com`. [Figures 18.13](#ch18.xhtml#fig18_13a), [18.14](#ch18.xhtml#fig18_14a), and [18.15](#ch18.xhtml#fig18_15a) display the user interface for searching a doctor and the results, respectively.

![Figure 18.13 Partial page – ratemd.com.](images/fig18_13.jpg)

[Figure 18.13 Partial page –](#ch18.xhtml#Ffig18_13) [ratemd.com](http://ratemd.com).

![Figure 18.14 Single Result page (obtained from ratemd.com).](images/fig18_14.jpg)

[Figure 18.14 Single Result page (obtained from](#ch18.xhtml#Ffig18_14) [ratemd.com](http://ratemd.com)[).](#ch18.xhtml#Ffig18_14)

![Figure 18.15 Multi-result page – ratemd.com.](images/fig18_15.jpg)

[Figure 18.15 Multi-result page –](#ch18.xhtml#Ffig18_15) [ratemd.com](http://ratemd.com).

# 18.7.2.3 Hospital Generator

We also generate hospital information from `yellowpages.com` website. [Figure 18.16](#ch18.xhtml#fig18_16a) shows the results returned from searching for a hospital. [Figure 18.17](#ch18.xhtml#fig18_17a) is a list of attributes we extracted for each physician in our provenance knowledge base.

![Figure 18.16 Partial page (Hospital) – yellowpages.com.](images/fig18_16.jpg)

[Figure 18.16 Partial page (Hospital) –](#ch18.xhtml#Ffig18_16) [yellowpages.com](http://yellowpages.com).

![Figure 18.17 Physician attributes.](images/fig18_17.jpg)

[Figure 18.17 Physician attributes.](#ch18.xhtml#Ffig18_17)

# 18.7.3 Miscellaneous generators

This module uses `www.webMD.com` to determine the relationships between a disease, a medication, a test, and a treatment. Therefore, this allows us to add semantic association among these entities to our knowledge base. Since the relationships are background information that is also available to any user, we build rules that takes these semantic relationships into consideration when disclosing provenance information.

# 18.7.4 Workflow generator

We build a set of standard workflows, which are taken from existing procedures (e.g., `mercyhealthcom`). As these procedures are freely available, we build rules to protect some sensitive components in the generated workflows. Furthermore, the relationships among the entities in these workflows can be explicit or implicit. Therefore, our inference controller utilizes a mixture of policies and inference rules to protect the information in these workflows.

# 18.7.5 Annotating the Workflow

We annotate our workflow using the data produced by the background generator. Therefore, the associations between the attributes of a patient are the ones gathered from `www.yellowpages.com` and `www.whitepages.com`. Similarly, the hospital and physician attributes are in fact the ones gathered from `www.yellowpages.com` and `www.ratemd.com`.

# 18.7.6 Generating workflows

As stated earlier, for each patient in our toy hospital example, we initiate workflows that update the record for the patient. The recorded provenance is the only confidential data we assumed in our system. The intent is to give the querying user an opportunity to guess the patient's disease, medications or tests associated with the record. Provenance poses more challenges than that of traditional data. The controller not only anticipates inferences involving a user's prior knowledge, but also considers the inferences associated with the causal relationships among the data items as well as the provenance entities ([Algorithms 18.2](#ch18.xhtml#alg18_2)).

# 18.7.7 Incomplete information in the databases

We generated our data from various web pages, each contributing a part to the knowledge base. This represent a classic case of our knowledge base containing partial or incomplete information.

An incomplete database is defined by a set of constraints and a partial database instance. Answering conjunctive queries over incomplete databases is an important computational task that lies at the core of many problems such as information integration, data exchange, and data warehousing. A common example of partial information over a relational database is a view. A view can be defined so as to hide important data in the underlying database and thus restrict access to a user. This is usually done to satisfy some constraints; for example, employees in the accounts department can view the accounting records but not the human resources records. Given a query and an incomplete database, the task is to compute the set of certain answers. The certain answers are tuples that satisfy the query in every database instance that conforms to the partial instances and satisfies the constraints. Answering queries under general constraints is undecidable. Therefore, the expressivity of the constraint language considered is typically restricted in order to achieve decidability. An analogy to incomplete information in databases is an OWL ontology. In an OWL ontology, the TBox can be seen as a conceptual schema containing the set of constraints, and the ABox as some partial instances of the schema.

An incomplete database has an important property that an inference controller can use when answering queries over the RDF database. When a query returns a negative response, the user must decide whether the query was attempting to access confidential information or whether the query was not entailed in the RDF database.

# 18.8 Use Case: Medical Example

In this section, we provide examples of provenance queries. These queries can be used to identify resources for a policy or identify the answer for a user query.
