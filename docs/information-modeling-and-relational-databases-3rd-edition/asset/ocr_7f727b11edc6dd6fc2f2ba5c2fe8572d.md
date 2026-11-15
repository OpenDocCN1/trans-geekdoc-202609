3. In Megasoft corporation, at the start of each year, each salesperson is assigned at most three different software products to sell during that year (not necessarily the same each year). At the end of each year, each salesperson reports how many of each product he / she sold in each month of that year. Historical data is kept on who is assigned what to sell in each year and the monthly sales figures for that person (if the figures are available). No month may be omitted in these annual sales figures. The system retains information from previous years. Schematize this, including value and frequency constraints. Use nesting.

4. (Acknowledgment: This question is based on an exercise devised by Dr. E. Falkenberg and is used with permission.)

The following tables are sample reports from a system that maintains information about communities and roads. A “–” mark means “inapplicable because of other data” (see the asterisked notes). Mayors are identified by the combination of their first name and surname. A person can be mayor of only one city, and each city has exactly one mayor. Each road connects exactly two communities. Schematize this UoD, including uniqueness, mandatory role, value, subtype, and frequency constraints.

| Community | Population | Longitude * | Latitude * | Size ** (km²) | Mayor Firstname | Mayor Surname |
|---|---|---|---|---|---|---|
| Astraluna | 900,000 | – | – | 145 | Fred | Bloggs |
| Bradman | 90,000 | +120°50' | +48°45' | 12 | – | – |
| Cupidville | 9,000 | +120°50' | +48°40' | – | – | – |

* Recorded only for villages and towns (at most 100,000 inhabitants).
** Recorded only for towns and cities (more than 10,000 inhabitants).
*** Recorded only for cities (more than 100,000 inhabitants).

| Road Nr | Road kind* | Connection Community 1 | Connection Community 2 | Length (km) | Avg. travel time*** | Max. slope (%)**** |
|---|---|---|---|---|---|---|
| 11,000 | f | Astraluna | Bradman | 25 | 0 h 20 m | – |
| 11,500 | h | Astraluna | Bradman | 22 | 0 h 25 m | 2 |
| 11,561 | p | Bradman | Cupidville | 17 | 0 h 20 m | 2 |
| 11,562 | d | Bradman | Cupidville | 15 | – | 15 |

* f = freeway; h = highway; p = paved minor road; d = dirt road.
** All connections are two-way (so the order of the connection is irrelevant).
*** Recorded only for freeways, highways and paved minor roads.
**** Recorded only for dirt roads, paved minor roads and highways.

5. An award-granting institute has a rule that any given person (identified by a PersonNr) may apply for the same award (identified by an awardNr) at most three times. For each award application (identified by an ApplicationNr), its status is recorded.

(a) Model this using an external frequency constraint.
(b) Try to model this without using an application number, instead objectifying “Person applied for Award” as “Application”. Explain why this approach fails.