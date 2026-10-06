# CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

There are other ways to reshape data, including basically just reverses the process of pivoting. If we took Table 14-15 and did a quick pivot on it, we'd end up with six rows per day, each one with a column with the values "Qty-Personal, Qty-Medium,” and a second column with the corresponding quantity or sales total (4, 3, etc.), etc., like you can see in Table 14-16.

# Table 14-16. An unpivoted version of Table 14-15

| Date | Type | Quantity |
|---|---|--|
| 2024-03-01 | Qty-Personal | 4 |
| 2024-03-01 | Qty-Medium | 3 |
| 2024-03-01 | Qty-Large | 4 |
| 2024-03-02 | Sales-Personal | 50.00 |
| 2024-03-02 | Sales-Medium | 52.00 |
| 2024-03-02 | Sales-Large | 93.50 |
| 2024-03-02 | Qty-Personal | 4 |
| 2024-03-02 | Qty-Medium | 1 |
| 2024-03-02 | Qty-Large | 4 |
| 2024-03-02 | Sales-Personal | 44.00 |
| 2024-03-02 | Sales-Medium | 16.50 |
| 2024-03-02 | Sales-Large | 80.00 |

Realistically, this is pretty ugly, and more work could be done to make it better, like having separate columns for Quantity and Sales. Sometimes transforming data takes several steps.