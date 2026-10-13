
1. ∀`r1`∈ `Agency1`, ∀`r2`∈ `Agency2`, `Agency1` uses `r1`∪ `r2` if `Agency2` also uses `r2` ∪ `r1`.

### 16.3.3.2.2 Develop and scale policies

To enable freedom of maneuverability across the information environment and to deliver the power of information to ensure mission success, an agency should be able to rapidly develop policies and deploy them as needed. We next discuss the features that are available to an agency during and after development of its policies.

*   **Policy development:** `Agency1` wishes to simulate a live environment and create test scenarios to visualize the results of each policy configuration. Our policy framework provides three configurations: (i) a stand-alone version for development and testing; (ii) a version backed by a relational database; and (iii) a cloud-based version that achieves high availability and scalability while maintaining low set-up and operation costs.

*   **Sequencing effects:** `Agency1` wishes to vary the result set to a user's query based on the user's credentials. The policy sequence feature can be used to configure different outcomes by permuting the policies and their respective rules.

*   **Rapid elasticity:** `Agency1` identifies recent security vulnerabilities in its existing policy configurations and wishes to extend (or grow) its existing policy set with support for policies at a finer granularity. Our policy engine provides a policy interface that should be implemented by all policies; therefore, we can add newer types of policies as needed. In addition, our policy engine gives an agency rapid elasticity, whereby the capabilities available by our policy framework appear unlimited.

*   **Location independence:** `Agency1` wishes to store its resources closer to where it is consumed, but with little or no change at the policy layer. Our policy engine provides location independence whereby the policy engine has no control or knowledge over the exact location of the resources, but may be able access the resources through a specified location using the connection manager. Note that an agency's resources can be in any cloud, geographically. The ability to locate any resource by a dereferenceable URE provides much flexibility.

*   **Deployment models:** `Agency1` can take advantage of different deployment models. For example, a private cloud, a hybrid cloud, a community or a public cloud. The connection manager allows an agency to choose among a list of connection types based on different risk factors and objectives to protect data confidentiality.

### 16.3.3.2.3 Justification of resources

Provenance makes available an explanation about why information was manipulated and a trace to the source of the information manipulation. This establishes trust among agencies, thus facilitating partnerships for common goals.

`Agency1` asks `Agency2` for a justification of resource `R2`. The current commercial access control policies are mainly designed to protect single data items, while current redaction policies are designed for redacting text and images. Our policy engine allows agents to define policies over provenance; therefore, `Agency2` can provide the provenance to `Agency1`, but protect it by using access control or redaction policies.

### 16.3.3.2.4 Policy specification and enforcement

Our architectural design supports a high-level specification of policies, thus separating the business layer from a specific policy implementation.

`Agency1` wishes to express its policies in a high-level language (e.g., `XACML`), and would prefer not learning `RDF` or any of its variations. The framework exposes a web interface layer between the users and the policy engine layer, whereby the users can specify their policies independent of the actual implementation of the policy. A suitable adapter, also known as a data translator, will translate each high-level policy specification into the appropriate `RDF` representation used by the appropriate policy which protects an agency's resources.

Policies may be specified using more expressive languages than `RDF` by extending `RDF` with a formal vocabulary, in particular a sublanguage of `OWL`. `OWL` has a formal semantics that is based on description logics, a decidable fragment of first order logic. Thus, by supporting this adapter pattern, our framework is extended to handle semantic policies specified in `OWL` and high-level policies can be translated into a suitable sublanguage of `OWL` using existing or custom-built translators.

## 16.4 Related Work

### 16.4.1 Research Efforts

While there are some related efforts, none of the efforts have provided a solution to `AIS` in the cloud, or have they conducted such a formal policy analysis.

#### 16.4.1.1 Secure Data Storage and Retrieval in the Cloud

Security for cloud has received recent attention [TALB09]. Some efforts on implementing at the infrastructure level have been reported [OMAL09]. Such development efforts are an important step toward securing cloud infrastructures but are only in their inception stages. The goal of our system is to add another layer of security above the security offered by `Hadoop` [UTD1]. Once the security offered by `Hadoop` becomes robust, it will only strengthen the effectiveness of our system. Similar efforts have been undertaken by Amazon and Microsoft for their cloud computing offerings [[AMAZ2016](#ch16.xhtml#ref16_3), [MARS2010](#ch16.xhtml#ref16_43)]. However, this work falls in the public domain whereas our system is designed for a private cloud infrastructure. This distinguishing factor makes our infrastructure "trusted" over public infrastructures where the data must be stored in an encrypted format.

#### 16.4.1.2 SPARQL Query Processor

Only a handful of efforts have been reported on `SPARQL` query processing. These include `BioMANTA` [[BIOM](#ch16.xhtml#ref16_6)] and `SHARD` [SHAR2011]. `BioMANTA` proposes extensions to `RDF` Molecules [DING05] and implements a `MapReduce`-based Molecule store [[NEWM2008](#ch16.xhtml#ref16_45)]. They use `MapReduce` to answer the queries. They have queried a maximum of 4 million triples. Our work differs in the following ways: first, we have queried 1 billion triples. Second, we have devised a storage schema which is tailored to improve query execution performance for `RDF` data. To our knowledge, we are the first to come up with a storage schema for `RDF` data using flat files in `HDFS`, and a `MapReduce` job determination algorithm to answer a `SPARQL` query. `SHARD` (Scalable, High-Performance, Robust and Distributed) is an `RDF` triple store using the `Hadoop` Cloudera distribution. This project shows initial results demonstrating `Hadoop`'s ability to improve scalability for `RDF` datasets. However, `SHARD` stores its data only in a triple store schema. It does no query planning or reordering, and its query processor will not minimize the number of `Hadoop` jobs. None of the efforts have incorporated security policies.

#### 16.4.1.3 RDF-based Policy Engine
