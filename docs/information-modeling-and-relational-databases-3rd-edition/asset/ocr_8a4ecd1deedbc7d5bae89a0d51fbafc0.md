![](bbox=[0.26, 0.1, 0.73, 0.295])

# FIG. 15.5 An activity hierarchy.

to happen inside the top and intermediate nodes; in others, these nodes exist only as a mechanism for grouping the leaf nodes, which are assumed to contain all the actual work, into convenient clusters.

Clearly, we could have both a model of business activity and a model of information structure relating to the same area of a business, and therefore it should be possible to establish some kind of relationship between them. Most process modeling approaches focus mainly on flow-of-control issues and have surprisingly little to say about the information used by, produced by, or modified by the process. We look at some examples later in this chapter.

To establish a connection between process activities and the information they use, produce, or consume, we need to examine process structure in a little more detail. Specifically, we need to establish how the “activity” level of a process structure can be aligned with identifiable elements in an information model. We will return to the detailed sequencing and control of the activities later, but our focus for now will be on the *structure* of a process.

![](bbox=[0.28, 0.66, 0.75, 0.785])

# FIG. 15.6 Main process-definition structure.

A model fragment containing the main structure of a process definition is shown in Fig. 15.6. Processes can contain subprocesses to any number of levels, but loops are not allowed. We use the special term “activity” for the lowest level of the hierarchy and assume that a process definition (at any level) will contain subprocesses, activities, or