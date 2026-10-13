
## Definition 3: Provenance Path

Given a provenance graph, a provenance path `(s p o)` is a path $s\overset{p}{\rightarrow}o$ that is defined over the provenance vocabulary `V` using regular expressions.

## Definition 4: Regular Expressions

Let $\Sigma$ be an alphabet of terms in `V`, then the set `RE(\Sigma)` of regular expressions is inductively defined by:

*   $\forall x \in \Sigma, x \in RE(\Sigma)$;
*   $\Sigma \in RE(\Sigma)$;
*   $\varepsilon \in RE(\Sigma)$;
*   If $A \in RE(\Sigma)$ and $B \in RE(\Sigma)$ then:
    `A|B`, `A/B*`, `A+`, `A?` $\in RE(\Sigma)$.

The symbols `|` and `/` are interpreted as logical OR and composition, respectively.

Our intention is to define paths between two nodes by edges equipped with `*` for paths of arbitrary length, including length 0 or `+` for paths that have at least length 1. Therefore, for two nodes `x`, `y`, and predicate name `p`, $x{(\overset{p}{\rightarrow})}^{*}y$ and $x{(\overset{p}{\rightarrow})}^{+}y$ are paths in `G`.

A SPARQL query extended with regular expressions [[HARR2010]](#ch16.xhtml#ref16_31) can define a resource (or subgraph) of the provenance graph in Figure 16.18 as follows:

### Example 16.1: Provenance Path Query

```
Select ?x
{ex:PubRpt1 arq:OnPath("([opm:WasGeneratedBy]/[opm:WasTriggeredBy]/[ex:location])" ?x). }
```

This query would return the location as a binding to the variable `x` and could be used to pinpoint the origin of a compromise (and leakage) of the original report. This could also serve to alert policy designers to add appropriate policies for reports and servers in their respective agencies.

*   **Policy sequence**: The execution of the policies over an agency's resource results in a policy sequence. In particular, a protected resource could employ the services of multiple policy engines and policy types. Each policy type produces a new subgraph of its input RDF graph. It is important to note that the effect of a policy is directly dependent on the RDF graph it receives as input, and furthermore, the effect may be different from the original effect the policy was intended to achieve. A sequence takes the original input graph through a series of transformations until a final RDF graph is returned to the user. Note that the success of a policy rule (which is implemented as a SPARQL query) returning a particular set of RDF triples is dependent on the transformation step at which the rule was applied in a policy sequence. We illustrate this using the following SPARQL query:

```
CONSTRUCT G WHERE P
```

`G` is a newly constructed graph, which contains a set of triples that satisfy condition `P` in the input graph. A policy protecting the following RDF triples,

```
<http://cs.utdallas.edu/semanticweb/Prov-AC/agency#agent_1>
foaf:name "John brown";
foaf:projectHomepage <http://www.agency1.gov/>
```

will fail if either the name or project home page triple was earlier removed or altered by a previous policy rule.

A policy precedence feature in the framework helps an agency determine the ordering of its policies. In the user interface layer, an agency configures the ordering of its policies. The policy sequence is then stored in an RDF sequence file (using the `rdf:seq` feature of the RDF specification). When a query is evaluated, the policy framework will in turn invoke each policy in the intended order.

*   **Rule sequence**: In a similar way, a policy may be implemented using a set of rules. For example, to fully redact a shared resource, an agency may need a separate rule to redact each sensitive triple in an RDF graph. Each rule is triggered when a triple (or set of triples) meet some specified criteria in the input graph. Note that each rule transforms the current state of a shared resource. Therefore, each sequencing of the rules will impact the final graph (also called the redacted graph).

### 16.3.3.1.3 Data layer

At the Data Layer is a connection factory which acts as a facade for creating connection objects. These connection objects expose the same properties (functionally) as public methods to the policy designer. This makes it easier for the policy designer to concentrate on the policy engine design. The policy designer makes a call to an `RDF Policy Factory` which returns an `RDF model object`. This `RDF model object` is backed by a connection store which can be a local connection, a relational database connection or a cloud connection. During the registration process, an agency is given an opportunity to decide where it wants to store its resources and configuration documents. It is recommended that the smaller configuration documents be stored locally on disk (or in a local database) to enable quick access to them. Local connections also consume lower bandwidth, offers real-time access and enable development before deployment. However, an agency may decide to store them in a private cloud (or on a remote database server) to take advantage of the added protection there.

The connection factory also enables agencies to store their resources in any cloud infrastructure. For example, an agency's resources could reside on a private cloud, a community cloud or a public cloud. A private cloud deployment provides more control in that agencies could house their own cloud. A community cloud is provisioned for exclusive access by a specific community thus serving the common interest of cooperating agencies. A public cloud is open to the public and thus susceptible to more vulnerabilities due to the loss of control over the data uploaded onto the public cloud. Agencies may choose to use a mixture of connections and also employ more than one deployment simultaneously (e.g., a hybrid cloud model).

## 16.3.3.2 Features of Our Policy Engine Framework

In the following subsections below, we present some novel features of our policy engine framework.

### 16.3.3.2.1 Policy reciprocity

Policy reciprocity enables agencies to specify policies when knowledge of the other agencies, their resources or policy specification are available. This is made possible via the registration process, where agencies make metadata available about themselves, their recourses and associated policies. The following discussion provides scenarios for policy reciprocity.

`Agency1` wishes to share its resources if `Agency2` also shares its resources with it. Current access control and redaction policies do not provide for this reciprocity. Our framework provides information sharing policies which allow agents to define policies based on reciprocity and mutual interest amongst cooperating agencies.

We present the following two sample information sharing policies:

1.  $\forall r_1 \in Agency1, \forall r_2 \in Agency2, \text{use } r_1 \cup r_2$.

    This policy states that `Agency1` shares all its resources with any resource of `Agency2` as a union of the resources (i.e., $\odot \in \{\cup\}$).

2.  let $r_1[1], r_1[2], \dots, r_1[n] \in Agency1$. `Agency1` can use $r_1[1] \cup r_2, r_1[1] \cap r_2, \forall r_2 \in Agency2$.

    This policy offers a finer level of control and defines the combined operator, $\odot \in \{\cap, \cup\}$.

*   **Conditional policies**: A consequence of policy reciprocity is allowing the use of conditional sharing policies. For example, `Agency1` shares its resources with `Agency2` if `Agency2` does not share `Agency1`'s resources with `Agency3`. We present the following sample information sharing policy:

1.  $\forall r_1 \in Agency1, \forall r_2 \in Agency2, Agency1 \text{ defines } r_1 \cap r_2$. If $\forall r_3 \in Agency3$, then
    *   `Agency2` does not define any sharing policy of the form $r_1 \cap r_3$,
    *   or `Agency2` does not define any sharing policy of the form $r_1 \subseteq r_2 \odot r_3$, where $\odot \in \{\cup, \cap\}$.

*   **Policy symmetry**: Another consequence of policy reciprocity is to have symmetry in the sharing of policies. For example, `Agency1` shares its resources with `Agency2` with a combined operator, $\odot$, if `Agency2` also shares its resources with `Agency1` using the same combined operator, $\odot$. We present the following sample information sharing policy:
