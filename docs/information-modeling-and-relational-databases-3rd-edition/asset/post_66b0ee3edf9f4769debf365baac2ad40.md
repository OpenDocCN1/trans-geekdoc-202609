
Variants include *exclusive-or* (the default if no icon is shown), *and*, *inclusive-or*, and *complex* (where the split or join conditions are determined by expressions).

Fig. 15.35 shows a typical BPMN process diagram. The process shown starts with the receipt of a loan application (identified as a message). After the loan assessment activity, the control flow passes to one of the three following activities. Each of these is a compound activity; the internal details are not shown here. The final exclusive-or gateway joins the split paths together and the process ends. In the referral case, there is a time event associated with the applicant review. If the review is not completed within the given period, it is escalated to be dealt with by a supervisor. The escalated review process also has branching in the flow, but rather than using gateways, the subprocess uses decisions on sequence flows and implicit joining of flows. The escalated review subprocess also shows the reuse of the definition of the compound activities for loan approval and loan rejection.

![](img/1344db3eba3d550e6edb009556fcd95c_834_0.png)

FIG. 15.35 A BPMN diagram.

## 15.8 Standard Process Patterns

A significant contribution to the establishment of a common foundation for business process modeling was made by the identification of 20 or so workflow patterns by van der Aalst, ter Hofstede, and others. The patterns have subsequently provided a valuable benchmark for describing the characteristics of alternative process modeling notations, methodologies, and tools. Table 15.4 provides a summary of the original workflow patterns using (mostly) BPMN notation. There is no particular significance to the numbering system used.

### Table 15.4 Standard process patterns.

| Nr | Pattern | Description |
|---|---|---|
| 1 | Sequence | \(\rightarrow\) Activity 1 \(\rightarrow\) Activity 2 \(\rightarrow\) Activity 3 \(\rightarrow\) etc.

Sequence is the simplest pattern. It expresses the notion that one activity follows another, so in the diagram, Activity 2 starts when Activity 1 finishes, Activity 3 starts when Activity 2 finishes, etc. |
| 2 | Parallel split | \(\rightarrow\) Activity 1 \(\rightarrow\) (+) \(\rightarrow\) Activity 2 \(\rightarrow\) etc.
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;\(\rightarrow\) Activity 3 \(\rightarrow\) etc.
(flow could split into more than two paths)

In the parallel split pattern, a token released by the completion of a preceding activity is split into multiple tokens, perhaps at an AND gateway, enabling several succeeding activities. In the diagram here, there is no defined ordering between Activity 2 and Activity 3. |
| 3 | Synchronization | \(\rightarrow\) Activity 1 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; (+) \(\rightarrow\) Activity 3 \(\rightarrow\) etc.
(flow could be combined
from more than two paths)
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; /
\(\rightarrow\) Activity 2

In synchronization, tokens from multiple branches merge, perhaps at a gateway, so that one token is emitted once a token has been received on all the preceding branches. Here, both Activity 1 and Activity 2 must complete before Activity 3 can be executed. |
| 4 | Exclusive choice | \(\rightarrow\) Activity 1 \(\rightarrow\) (X) \(\rightarrow\) Activity 2 \(\rightarrow\) etc.
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;\(\rightarrow\) Activity 3 \(\rightarrow\) etc.
(flow could split into more than two paths)

An exclusive choice is a decision point at which the thread of execution will take one of several alternative branches. The branching decision is typically defined by a business rule or rule set. One of the branches may be designated as the default. In the diagram here, Activity 1 can be followed by either Activity 2 or Activity 3, but only one of these will be executed. |
| 5 | Simple merge | (flow could be combined from more than two paths) Activity 1 -> X -> Activity 3 -> etc. Activity 2 -> X.

A simple merge is a point at which two or more alternative branches come together without synchronization. Only one of the preceding branches is assumed to be active (later patterns deal with merging multiple active branches). In the diagram here, either Activity 1 or Activity 2 must complete before Activity 3 can be executed. |
| 6 | Multiple choice | Activity 1 -> O -> Activity 2 -> etc.
                          -> Activity 3 -> etc.
                       (flow could split into more than two paths)

In multiple choice, the thread of control diverges into several parallel branches on a selective basis. The branching decision is typically defined by a business rule or rule set. One of the branches may be designated as the default. In the diagram here, Activity 1 can be followed by Activity 2, Activity 3, or both. |
| 7 | Synchronized merge | Activity 1 -> O -> Activity 3 -> etc.
                    Activity 2 -> O.
                 (flow could be combined from more than two paths)

Synchronized merge represents the completion of activities that have been started on parallel branches. One or more of the preceding branches can be active. All preceding active branches must complete before the succeeding Activity 3 can be executed. This assumes that the gateway has information about which preceding activities are expected to complete (sometimes called a “structured workflow” assumption). In the diagram here, Activity 1 or Activity 2 must complete (if they were started) before Activity 3 can begin. |
| 8 | Multiple merge | 
---
Activity 1 --> Activity 3 --> etc.
Activity 2 --> Activity 3
(flow could be combined from more than two paths)

Multiple merge is the unsynchronized convergence of several alternative branches. More than one of the branches can be active. The succeeding activity will be executed when any of the preceding activities completes. If multiple branches complete, the succeeding activity is executed multiple times. In the diagram here, either Activity 1 or Activity 2 must complete before Activity 3 can be executed, and a new instance of Activity 3 will be started for each preceding branch that completes. |
| 9 | Discriminator | 
---
Activity 1 --> X --> Activity 3 --> etc.
Activity 2 --> X
(flow could be combined from more than two paths)

The discriminator provides for synchronized convergence after one out of m alternative branches completes. One or more preceding branches will be active. Completion of any preceding active branch will forward a token to the succeeding activity. The completion of subsequent branches is ignored. A Complex gateway in place of the XOR gateway shown here would allow n-out-of-m merges: an expression would determine which path(s) must join. Here, either Activity 1 or Activity 2 (or both) must complete before Activity 3 can be executed. |
| 10 | Arbitrary cycles | 
---
Activity 1 --> X --> Activity 2 --p1--> Activity 6
                  |            |
                  v            v
                  Activity 3   Activity 4 --> Activity 5 --> X --> etc.
                                        ^            |
                                        |____________|
                                        p2

Arbitrary cycles of activity have more than one entry or exit point in a repetitive cycle of activities. This pattern supports unstructured repetition in a process without requiring special looping constructs. This is not possible in "block structured" modeling languages. Here, Activities 4, 5, and 6 form a loop that can be entered at either points p1 or p2. |
| 11 | Implicit termination | ![Diagram: Activity n, Activity m, Activity r leading to end events or gateways] Implicit termination specifies that when a process is terminated, any subprocesses should also be terminated. The intention is that on termination there are no active activities, there is no activity that can be made active, and the process is not deadlocked. In BPMN this is specified by ensuring that every thread of control in a process ends with an end event (as shown in the diagram here). |
| 12 | Multiple instances, without synchronization | ![Diagram: Activity x splitting into Activity y.1, y.2, y.3] Multiple instances of the same activity are initiated in parallel without requiring that they resynchronize on completion. Each instance of the activity runs independently of the other instances. This is not the same as a parallel split because all instances are of the same activity. Here, Activities y.1, y.2, and y.3 are all separate instances of Activity y. This diagram (and the other multiple instance diagrams) departs from the BPMN notation to make the patterns more distinct. |
| 13 | Multiple instances with a priori design-time knowledge | ![Diagram: Activity x splitting into y.1, y.2, y.3 and joining into Activity z] Several instances of the same activity are initiated in parallel with intended resynchronization on completion. The number of instances is known when the process is defined. Each instance of the activity (such as Activities y.1, y.2, and y.3 shown here) runs independently of the other instances but succeeding activities (such as Activity z above) cannot be triggered until every instance has completed. Note: this is not the same as a parallel split/join because these are all instances of the same activity. |
