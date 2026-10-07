# DEEP-Q Learning-Based Intelligent IoT Edge Solutions 133

These locations denoted by L1, L2, .... L12 are autonomous locations in which we have different categories of goods placed. Let us consider a business process where an autonomous agent must collect these products from these locations. These locations turn have a priority ranking. That the warehouse system ranks the locations in terms of priority of items stored. This priority may be decided as per item demand, easy of availability, price, popularity, etc. The ranking is as follows:

At a time, this priority ranking influences the autonomous robot movement in the warehouse. Let us consider the problem of making the autonomous agent learn the shortest route from any location-to-location L7 as this is the location with the highest priority. We will train the AI agent to go to L7 via the second priority location that is L11. After training the AI agent we will deploy it in an edge cloud based IoT architecture so that it can be used by any other devices for agent training.

Let us first define the environment in which the AI agent would work. An environment would fundamentally consist of three elements (Table 6.1):

+   * State definition
* Action definition
* Reward definition

Table 6.1 Priority business process schematic representation.

| Priority | Location |
|---||
| 1 | L7 |
| 2 | L11 |
| 3 | L12 |
| 4 | L10 |
| 5 | L1 |
| 6 | L9 |
| 7 | L8 |
| 8 | L3 |
| 9 | L2 |
| 10 | L4 |
| 11 | L6 |
| 12 | L5 |