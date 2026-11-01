
- `Transition model`: Maps a state and action to a resulting state; for example, if we apply `Left` to the start state in [Figure 3.3](#Chapter03-02.xhtml#fig3-3), the resulting state has the 5 and the blank switched.
- `Goal state`: Although any state could be the goal, we typically specify a state with the numbers in order, as in [Figure 3.3](#Chapter03-02.xhtml#fig3-3).
- `Action cost`: Each action costs 1.

Note that every problem formulation involves abstractions. The `8-puzzle` actions are abstracted to their beginning and final states, ignoring the intermediate locations where the tile is sliding. We have abstracted away actions such as shaking the board when tiles get stuck and ruled out extracting the tiles with a knife and putting them back again. We are left with a description of the rules, avoiding all the details of physical manipulations.

Our final standardized problem was devised by Donald Knuth (1964) and illustrates how infinite state spaces can arise. Knuth conjectured that starting with the number 4, a sequence of `square root`, `floor`, and `factorial` operations can reach any desired positive integer. For example, we can reach 5 from 4 as follows:

$\\left\\lfloor \\sqrt{\\sqrt{\\sqrt{\\sqrt{\\sqrt{(4!)!}}}}} \\right\\rfloor = 5.$

The problem definition is simple:
- `States`: Positive real numbers.
- `Initial state`: 4.
- `Actions`: Apply `square root`, `floor`, or `factorial` operation (factorial for integers only).
- `Transition model`: As given by the mathematical definitions of the operations.
- `Goal state`: The desired positive integer.
- `Action cost`: Each action costs 1.

The state space for this problem is infinite: for any integer greater than 2 the `factorial` operator will always yield a larger integer. The problem is interesting because it explores very large numbers: the shortest path to 5 goes through `(4!)! = 620,448,401,733,239,439,360,000`. Infinite state spaces arise frequently in tasks involving the generation of mathematical expressions, circuits, proofs, programs, and other recursively defined objects.

## 3.2.2 Real-world problems

We have already seen how the route-finding problem is defined in terms of specified locations and transitions along edges between them. Route-finding algorithms are used in a variety of applications. Some, such as Web sites and in-car systems that provide driving directions, are relatively straightforward extensions of the Romania example. (The main complications are varying costs due to traffic-dependent delays, and rerouting due to road closures.) Others, such as routing video streams in computer networks, military operations planning, and airline travel-planning systems, involve much more complex specifications. Consider the airline travel problems that must be solved by a travel-planning Web site:
- `States`: Each state obviously includes a location (e.g., an airport) and the current time. Furthermore, because the cost of an action (a flight segment) may depend on previous segments, their fare bases, and their status as domestic or international, the state must record extra information about these “historical” aspects.
- `Initial state`: The user’s home airport.
- `Actions`: Take any flight from the current location, in any seat class, leaving after the current time, leaving enough time for within-airport transfer if needed.
- `Transition model`: The state resulting from taking a flight will have the flight’s destination as the new location and the flight’s arrival time as the new time.
- `Goal state`: A destination city. Sometimes the goal can be more complex, such as “arrive at the destination on a nonstop flight.”
- `Action cost`: A combination of monetary cost, waiting time, flight time, customs and immigration procedures, seat quality, time of day, type of airplane, frequent-flyer reward points, and so on.

Commercial travel advice systems use a problem formulation of this kind, with many additional complications to handle the airlines’ byzantine fare structures. Any seasoned traveler knows, however, that not all air travel goes according to plan. A really good system should include contingency plans—what happens if this flight is delayed and the connection is missed?

Touring problems describe a set of locations that must be visited, rather than a single goal destination. The traveling salesperson problem (`TSP`) is a touring problem in which every city on a map must be visited. The aim is to find a tour with cost < C (or in the optimization version, to find a tour with the lowest cost possible). An enormous amount of effort has been expended to improve the capabilities of `TSP` algorithms. The algorithms can also be extended to handle fleets of vehicles. For example, a search and optimization algorithm for routing school buses in Boston saved $5 million, cut traffic and air pollution, and saved time for drivers and students (Bertsimas et al., 2019). In addition to planning trips, search algorithms have been used for tasks such as planning the movements of automatic circuit-board drills and of stocking machines on shop floors.

Touring problem
Traveling salesperson problem (`TSP`)

A `VLSI` layout problem requires positioning millions of components and connections on a chip to minimize area, minimize circuit delays, minimize stray capacitances, and maximize manufacturing yield. The layout problem comes after the logical design phase and is usually split into two parts: cell layout and channel routing. In cell layout, the primitive components of the circuit are grouped into cells, each of which performs some recognized function. Each cell has a fixed footprint (size and shape) and requires a certain number of connections to each of the other cells. The aim is to place the cells on the chip so that they do not overlap and so that there is room for the connecting wires to be placed between the cells. Channel routing finds a specific route for each wire through the gaps between the cells. These search problems are extremely complex, but definitely worth solving.

`VLSI layout`

Robot navigation is a generalization of the route-finding problem described earlier. Rather than following distinct paths (such as the roads in Romania), a robot can roam around, in effect making its own paths. For a circular robot moving on a flat surface, the space is essentially two-dimensional. When the robot has arms and legs that must also be controlled, the search space becomes many-dimensional—one dimension for each joint angle. Advanced techniques are required just to make the essentially continuous search space finite (see [Chapter 26](#Chapter26-00.xhtml)). In addition to the complexity of the problem, real robots must also deal with errors in their sensor readings and motor controls, with partial observability, and with other agents that might alter the environment.

Robot navigation

Automatic assembly sequencing of complex objects (such as electric motors) by a robot has been standard industry practice since the 1970s. Algorithms first find a feasible assembly sequence and then work to optimize the process. Minimizing the amount of manual human labor on the assembly line can produce significant savings in time and cost. In assembly problems, the aim is to find an order in which to assemble the parts of some object. If the wrong order is chosen, there will be no way to add some part later in the sequence without undoing some of the work already done. Checking an action in the sequence for feasibility is a difficult geometrical search problem closely related to robot navigation. Thus, the generation of legal actions is the expensive part of assembly sequencing. Any practical algorithm must avoid exploring all but a tiny fraction of the state space. One important assembly problem is protein design, in which the goal is to find a sequence of amino acids that will fold into a three-dimensional protein with the right properties to cure some disease.
