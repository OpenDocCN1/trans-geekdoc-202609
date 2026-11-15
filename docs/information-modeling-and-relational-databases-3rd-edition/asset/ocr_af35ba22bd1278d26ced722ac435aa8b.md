In step 6, subtypes are mapped to subclasses, adding relevant subclassing constraints. Subtype definitions are handled with discriminators and/or textual constraints. For example, the ORM schema considered earlier in Fig. 9.38 maps to the UML schema in Fig. 9.37.

In step 7, we map derived and semiderived fact types. The schemas in Fig. 9.53 and Fig. 9.54 provide simple examples.

With these hints, and the examples discussed earlier, you should now have enough background to do the mapping manually for yourself. The following short exercise will give you some practice at this.

If you are keen on using UML for data modeling, you may wish to use UML to model some of the many modeling exercises in other chapters.

# Exercise 9.8

+   1. Model the following application in UML. We suggest that you do an ORM model first, but that's up to you.

The universe of discourse (UoD) is based on a simplified fragment of a database application used by an electrical utility to help manage the delivery of electricity to consumers in Australia. A line link is a section of an electrical feeder or mains power line that connects two adjacent nodes (e.g., power poles, pilllar boxes).

The figure shown illustrates a tiny part of the electrical power network. Here, three power poles (also called telephone poles) carry power lines to supply electricity. The house is one of many receiving electricity from the power company.

![](bbox=[0.175, 0.529, 0.852, 0.724])

The following output report provides an extract of sample data about line links. The link types listed are not exhaustive.

| Line link | Link type | Linktype description | Voltage (V) | Current (A) | Power (kW) | Length (m) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 33 | OW | Open wire | 11,000 | 400 | 4400 | 200 |
| 40 | UGC | Underground cable | 11,000 | 400 | 4400 | 150 |
| 55 | ABC | Aerial bundled conductor | 415 | 300 | 124.5 | 170 |
| 56 | ABC | Aerial bundled conductor | 240 | 200 | 48 | 180 |