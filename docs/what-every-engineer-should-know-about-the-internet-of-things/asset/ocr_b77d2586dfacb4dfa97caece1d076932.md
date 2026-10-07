# Networks of 'Things'

+   1. Aggregators may be virtual the benefit of changing implementations quickly and increased malleability. A situation may exist where aggregators are physically manufactured, e.g., a field-programmable gate array (FPGA) or hard-coded aggregator that is not programmable. Aggregators may also act in a similar way as n-version voters.

+   2. Aggregators require computing powersower; however, this assumption can be relaxed by changing the definition and assumption of virtual to physical, e.g. firmware, microcontroller, or microprocessor. For example, aggregators could execute on faster hardware such as a smartphone. Aggregators will likely use weights (see Section 2.2) to compute intermediate, aggregated data.

+   3. Aggregators have two actors for consolidating large volumes of data into lesser amounts: clusters (see Section 2.1) and weights (see Section 2.2). Aggregators process big data concerns within NoTs, and to satisfy this role, computational “performance enhancing” technologies will be needed. This is the only primitive with actors.

+   4. Sensors may communicate directly with others, and thus act in situations similar to aggregators.

+   5. Intermediate, aggregated data may suffer from some level of information loss. Proper care in the aggregation process should be given to significant digits, rounding, averaging, and other arithmetic operations to avoid unnecessary loss of process.

+   6. For each cluster (see Section 2.1), there should be an aggregator or set of potential aggregators.

+   7. Aggregators are (1) executed at a specific time and for a fixed time interval or (2) event-driven.

+   8. Aggregators may be acquired off the shelf. Note that aggregators may be nonexistent and will need to be grown. This may create a problem for huge volumes of data within a Not

+   9. Some NoTs may not have an aggregator, e.g., a single light sensor will send a signal directly to a smart light bulb to turn it off or.

+   10. Security is a concern for aggregators (malware or general defects) and for the sensitivity of their aggregated data. Further, aggregators could be attacked, e.g., by denying them ability to operate/execute or by feeding them bogus data.

+   11. Reliability is a concern for aggregators (general defects).

# 2.3.2.1 Actor #1: Cluster (or “Sensor Cluster”)

A cluster is an abstract grouping of sensors that can appear and disappear instantaneously. Basic properties, assumptions, recommendations, and general statements about cluster include the following:

+   1. Clusters are abstractions of a set of sensors along with the data they output — clusters may be created in an ad hoc manner or organized according to fixed rules.

+   2. Clusters are not inherently physical.