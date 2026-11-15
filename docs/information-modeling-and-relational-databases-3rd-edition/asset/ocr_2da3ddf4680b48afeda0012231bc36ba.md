operators, such as +, -, * (multiply), and / (divide); set operators such as U (union); and functions for counting, summing, and computing averages, maxima, and minima.

In addition to such generic derivation facilities, specific *derived fact types* known to be required may be defined in the schema by means of derivation rules. Some mathematically computed fact types and almost all logically inferred fact types fit into this category. Fact types derived by use of logical inference typically involve rules that make use of logical operators such as **and** or **if**.

Although derivable facts could be stored in the database, it is usually better to avoid this. Apart from saving storage space, the practice of omitting derived facts from the stored data usually makes it much easier to deal with updates. For instance, suppose we want to regularly obtain individual ages (in years) of students in a class and, on occasion, the average age for the class. If we stored the average age in the database, we would have to arrange for this to be recomputed every time a student was added to or deleted from the class as well as every time the age of any individual in the class increased.

As an improvement, we might store the number of students as well as their individual ages, and have the average age derived only upon request. But this is still clumsy. Can you think of a better design?

As you probably realized, there is no need to store the number of students in a class because this can be derived using a count function. This avoids having to update the class size every time someone joins or leaves the class. Moreover, there is no need to store even the individual ages of students. Computer systems have a built-in clock that enables the current date to be accessed. If we store the birth date of the students, then we can have the system derive the age of any student upon request by using an appropriate date subtraction algorithm. This way, we don't have to worry about updating ages of students as they become a year older.

Sometimes, what is required is not the current age but the age on a certain date (e.g., entrance to a school, age grouping for a future sports competition). In such cases where a single, stable age is required for each person, it may be appropriate to store it.

Before considering a derivation example using logical inference, note the difference between *propositions* and *sentences*. Propositions are asserted by declarative sentences and are always true or false (but not both). The same proposition may be asserted by different sentences, for example, "Paris is the capital of France" and "The French capital is Paris".

While humans can deal with underlying meanings in a very sophisticated way, computers are completely literally minded: they deal in sentences rather than their meanings. If we want the computer to make connections that may be obvious to us, we have to explicitly provide it with the background or rules for making such connections.

Suppose that facts about brotherhood and parenthood are stored in the database. For simplicity, assume that the only objects we want to talk about are people identified by their first names. We might now set out facts as follows:

+   - Alan is a brother of Betty.
+   - Charles is a brother of Betty.
+   - Betty is a parent of Fred.