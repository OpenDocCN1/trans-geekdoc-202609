
![](img/1344db3eba3d550e6edb009556fcd95c_821_0.png)

### FIG. 15.26 An activity diagram for a simple sales process.

The diagram is self-explanatory, but not unique, in the sense that the same process could have been depicted in several slightly different ways. For example, the join and the fork that immediately follow it could have been combined into a join/fork construct that would have appeared as a thick bar with two edges entering and two edges leaving. Combining a join and a fork in this way can make diagrams slightly tidier but does not affect the semantics.

The execution of the process can be simulated by tracing the flow of a token in a particular instance of the process represented by the diagram. The token originates at the initial node. A customer places an order, which is received by the company's sales department. The first decision is to either accept or reject the order. The two guard conditions, [rejected] and [accepted], are mutually exclusive. If the token takes the [rejected] branch, it immediately reaches the merge and appears on its output edge. After the order is closed, the token reaches the activity final node, which immediately ends the process instance. If the token takes the [accepted] branch, the order is filled. When the token reaches the fork, two tokens are generated. The upper token causes the order to be shipped, and the lower token stimulates a series of actions to invoice the customer and eventually receive payment.

The upper and lower branches have no implied timing constraints, so either could be the first to complete. The following join waits for a token to arrive on both branches before emitting its own single token. This immediately forks into two other branches. The token on the upper branch reaches the merge that we have already discussed and causes the order to be closed. The token on the lower branch reaches a decision. If the customer is new, then they are added to the customer database, but for an existing customer, the token is immediately consumed by the flow final node.

The second fork in the diagram is not balanced (there is no corresponding join), but we eliminate the token in the lower branch because it eventually reaches a flow final node. This ensures that adding the customer to the database does not interfere with the closing of the order. However, the design is unsound because the lower branch is in a race with the upper branch. Once the order is closed, a token will reach the activity final node and immediately terminate the process, regardless of the status of the token in the other branch. This could result in a new customer not being added to the database, contradicting the process designer's original intentions.

One other feature of activity diagrams is support for swimlanes. These are optional but can be used to indicate features such as separation of responsibilities, usage of resources, geographical distribution, and so on. As with other features, the precise meaning of a swimlane is not defined in UML; the interpretation is left up to the user of the activity diagram. Fig. 15.27 shows the process model of Fig. 15.26 with swimlanes added. In Fig. 15.27, the swimlanes are drawn to indicate who carries out the actions (customer or sales clerk). The invoice object is used by both, and so is shown on a swimlane boundary. Multiple orthogonal swimlanes can be defined. For example, one axis could represent organization units and the other could represent resource types. The result resembles a kind of Venn diagram with the actions placed in whichever swimlane intersection is appropriate. However, this quickly gets difficult to draw and can be confusing to read.

![](img/1344db3eba3d550e6edb009556fcd95c_822_0.png)

### FIG. 15.27 An activity diagram with swimlanes.

Activity diagrams also provide for the hierarchical composition/decomposition of actions. A structured activity of this kind can be treated at one level as a single action but can be expanded as required to show the breakdown into its subordinate activities. Activities can be nested in this way to any level that's useful.

When considering the relationship between an activity diagram and the data that the activities may produce or consume, we need to bear in mind that the primary purpose of the diagram is to illustrate activity sequences. There is only a limited ability to show data in the form of objects being transferred between activities, as with the Invoice object in Fig. 15.27. These objects are transient and disappear when the sequence of activities terminates.

![](img/1344db3eba3d550e6edb009556fcd95c_823_0.png)

There is no direct way of showing how activities relate to any kind of persistent data. UML does provide a promising-sounding element with the stereotype «datastore», but this is used to indicate a specific type of internal buffer, as shown in Fig. 15.28, and still represents only transient data.

Fig. 15.28 shows an object transferred between activities, using the alternative “pin” notation to indicate the object. The transfer is indirect, with the object being buffered in the datastore ready for use by the succeeding activity. UML also provides another type of buffer with the stereotype «commonBuffer», the difference being that a «datastore» transfers a copy of the object so that the same object can be retrieved multiple times.

Activity diagrams have several other features that we haven’t space to discuss here. Examples include signaling between system elements, events used to trigger activities, the definition of interrupts and interruptible regions of activity, and so on. Many of these features can be useful in the definition of software but are less relevant for conceptual modeling.

## State Machine Diagrams

In UML version 1, state machine diagrams were known as statecharts and were closely aligned with activity diagrams, to the extent that an activity diagram could be considered as a special type of statechart. In UML version 2, state machine diagrams and activity diagrams occupy positions that are rather more distinct.

UML state machine diagrams have many of the same main constituents as other state diagramming conventions. States are normally shown as rectangles with rounded corners. The name of the state can be shown free form inside the rectangle, in a separate compartment in the rectangle, or as a name tag attached to the rectangle, as shown in Fig. 15.29.

States are interconnected by transitions, shown as directed lines. The lines typically begin on the border of one state and end on the border of another state; we discuss some special cases later. A transition can begin and end at the same state, and there can be more than one transition between a particular pair of states.

![](img/1344db3eba3d550e6edb009556fcd95c_823_1.png)

![](img/1344db3eba3d550e6edb009556fcd95c_824_0.png)

### FIG. 15.30 (a) Simple composite state. (b) Orthogonal state.

A state can be simple or composite. Composite states contain other substates within them. If a state has an active substate, then the containing state is also active. A composite state that is subdivided into multiple regions is known as an orthogonal state. Fig. 15.30 shows examples of a simple composite state (containing exactly one region) and an orthogonal state (in this case, with two regions).

The small black nodes in Fig. 15.30 are special pseudostates that represent the initial conditions for their respective states. Within a region, only one substate can be active at any one time, so the state shown in Fig. 15.30(a) can be in state S1, S2, S3, or S4. In contrast, the state shown in Fig. 15.30(b) can be in state S1 or S2 and simultaneously in state S3 or S4. A state can also contain nested state machines—called submachine state machines—that are semantically equivalent to composite states. Submachines are a convenient way of encapsulating common behaviors for reuse.

Actions can be carried out in a state at one of three times:

- (a) on entry to the state, denoted as entry / action
- (b) during the state (perhaps continuously in a loop), denoted as do / action
- (c) on exit from the state, denoted as exit / action.

All these are optional. The “during” actions do not begin until any entry actions are completed and will be completed or aborted before any exit actions begin. This ensures that entry actions are always carried out before anything else and that exit actions are always carried out after anything else. Actions carried out within a state correspond to the Moore machine semantics discussed earlier. If required, the actions can be shown on a state machine diagram by listing them in a compartment of the state symbol just below the compartment with the state name, as shown in Fig. 15.31.

![](img/1344db3eba3d550e6edb009556fcd95c_824_1.png)

### FIG. 15.31 Showing state actions.
