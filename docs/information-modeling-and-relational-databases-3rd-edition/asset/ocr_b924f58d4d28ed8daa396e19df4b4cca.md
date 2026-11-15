An invoice includes a table of one or more rows, called “line items” or “invoice lines”. Each invoice line lists details about the order of one or more units (copies) of a software item. For simplicity, assume that on a given invoice the same item can appear on only one invoice line. For each invoice line, the item code, title, quantity of units ordered, and unit price are listed. The total charge for the invoice line is displayed as a subtotal. The total charge for the whole invoice is displayed as the amount due.

Schematize this UoD, including uniqueness, mandatory role, and value constraints. Identify a LineItem or invoice line by using the invoice number and the item code. If a fact type is derived, omit it from the diagram but include a derivation rule for it.

+   4. Consider the previous question, but suppose that the same item may appear on more than one line of the same invoice. Devise an alternative identification scheme to deal with this situation. (_Hint:_ Compare this with the compact disc example. Sometimes you need to identify things in terms of their position.)

+   5. Now suppose that a cumulative record of purchases from suppliers is also to be recorded, an extract of which is shown in the following table. Only a cumulative record is kept (individual deliveries from suppliers are not recorded in the information system). No supplier can be a customer.

| ItemCode | Supplier | Quantity |
|---|---|---|
| B123 | MacSoft | 7 |
| | TechAtlantic | 3 |
| DL | Microsoft | 11 |
| DB3 | PacificTech | 5 |
| etc. | | |

+   (a) Draw a conceptual schema for this table.

+   (b) Assume that this subschema is integrated with your solution to Question 3, and that your fact type for stock quantity is now declared to be derivable.

+   (i) Specify a derivation rule for this approach.

+   (ii) In a real business, how practical would it be to use such a rule to avoid storing stock quantity? Discuss.

# 6.4 Subset, Equality, and Exclusion Constraints

Set-comparison constraints restrict the way the population of one role, or role sequence, relates to the population of another. In an earlier section, we considered six ways in which two sets might be related: subset, equality, exclusion, proper subset, overlap, and proper overlap. The last three of these require some objects to exist in at least one of the sets being compared. However, static constraints must apply to every state of the database, including the empty state. So, the only set-comparison constraints of interest are subset, equality, and exclusion. These three kinds of constraint are examined in this section.