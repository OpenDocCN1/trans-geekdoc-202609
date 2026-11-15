![](bbox=[0.27, 0.09, 0.75, 0.24])

FIG. 9.49 Changeability of attributes and association roles.

As a simple if unrealistic example, see Fig. 9.49. Here employee number, birthdate, and country of birth are readOnly for Employee, so they cannot be changed from their original value. For instance, if we assign an employee the employee number 007, and enter his/her birthdate as 02/15/1946 and birth country as “Australia”, then we can never make any changes or additions to that.

For each employee, the set of languages and the set of countries visited are addOnly. Suppose that for employee 007, we initially set his/her languages to {Latin, Japanese} and countries visited to {Japan}. As long as employee 007 is referenced in the database, these facts can’t be deleted. However, we may add to these (e.g., later we might add the facts that employee 007 speaks German and visited India).

By default, the other properties are changeable. For example, employee 007 might legally change his name from “Terry Hagar” to “Hari Seldon”, and the countries he wants to visit might change from {Ireland, USA} to {Greece, Ireland}.

Some traditional data modeling approaches also note some restrictions on changeability. The Barker ER notation includes a diamond to mark a relationship as nontransferable (once an instance of an entity type plays a role with an object, it cannot play this role with another object). Although changeability restrictions can be useful, in practice their application in database settings is limited.

One reason for this is that facts entered into a database might need to be changed. With snapshot data, this is the norm, but even with historical data changes can occur. The most common occurrence is to allow for corrections of mistakes, which might be because we were told the wrong information originally or because we carelessly made a misspelling or typo when entering the data.

In exceptional cases, we might require that mistakes of a certain kind be retained in the database (e.g., for auditing purposes) but be corrected by entering later facts to compensate for the error. This kind of approach makes sense for bank transactions (see Fig. 9.50). For example, if a deposit transaction for $100 was mistakenly entered as $1000, the record of this error is kept, but once the error is detected it can be compensated for by a bank withdrawal of $900. The balance is both derived and stored, and its readOnly status is typically implied by the readOnly settings on the base attributes, together with a derivation rule.