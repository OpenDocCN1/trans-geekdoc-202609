The role-based notation of ORM facilitates validation with sample populations because each role corresponds to a column in the associated fact table. The UC on the first role means that its entries must be unique. The absence of a UC on the second role indicates that its entries may be duplicated.

Although this notation is easy to understand, and schema diagrams reveal how things are connected, the domain expert assisting you in the modeling task should not be required to master the diagram notation. To validate a constraint, it is more important to use verbalization and sample populations.

For a binary fact type, three rows are enough for a *significant population*, so long as you pick the data carefully. If a column can have duplicates, give it two values that are the same and one different. If a column is unique, make each value different.

![](bbox=[0.295, 0.335, 0.67, 0.38])

FIG. 4.8 Each person was born in at most one country.

Looking back at Fig. 4.6, note that its population is significant. Using an ORM tool, you can enter sample populations like this and have them printed out along with automatic verbalizations of the constraints for the domain expert to validate.

Now consider the example shown in Fig. 4.9, which concerns heads of government (e.g., Presidents or Prime Ministers). At any point in time, a politician can head the government of at most one country, and each country has at most one head of government. Hence, the entries in the politician column must be unique, and the entries in the country column must be unique also. So, UCs are added above each of these columns. These constraints may be verbalized as shown. The conceptual schema for this fact type can be obtained by removing the fact table.

Note the use of the *hyphen* in the inverse predicate. This binds the word with the hyphen to the object type when the constraint is verbalized. So, the right-hand UC is verbalized as “Each Country has at most one head Politician”, not “Each Country has head *at most one* Politician”. Some ORM tools interpret hyphens this way when automatically generating the constraint verbalization.

If you don't include an inverse reading, the right-hand UC verbalizes as “At most one Politician governs *each* Country”. Usually, a constraint on a role verbalizes better if you include a predicate reading that starts at that role. We generally recommend that you include both predicate readings for binaries, but this is especially advisable if each role has a constraint that applies to it only.

For any state of the database, any one politician can be recorded as the government head of only one country, and vice versa. Hence, each population of this fact type is said to be a *one-to-one* (or *1:1*) relation. The instance diagram of Fig. 4.10 best illustrates the idea, abbreviating the surnames to their first letter.