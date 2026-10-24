| Constraint | Antimonotonic | Monotonic | Succinct |
| :--- | :--- | :--- | :--- |
| \( v \in S \) | no | yes | yes |
| \( S \subseteq V \) | no | yes | yes |
| \( S \supseteq V \) | yes | no | yes |
| \( min(S) \le v \) | no | yes | yes |
| \( min(S) \ge v \) | yes | no | yes |
| \( max(S) \le v \) | yes | no | yes |
| \( max(S) \ge v \) | no | yes | yes |
| \( count(S) \le v \) | yes | no | no |
| \( count(S) \ge v \) | no | yes | no |
| \( sum(S) \le v (\forall a \in S, a \ge 0) \) | yes | no | no |
| \( sum(S) \ge v (\forall a \in S, a \ge 0) \) | no | yes | no |
| \( range(S) \le v \) | yes | no | no |
| \( range(S) \ge v \) | no | yes | no |
| \( avg(S) \theta v, \theta \in \{>, \ge\} \) | convertible | convertible | no |
| \( support(S) \ge \xi \) | yes | no | no |
| \( support(S) \le \xi \) | no | yes | no |
| \( all\_confidence(S) \ge \xi \) | yes | no | no |
| \( all\_confidence(S) \le \xi \) | no | yes | no |

# Convertible constraints: ordering data in transactions

There are constraints that are neither pattern antimonotonic nor pattern monotonic. For example, it is hard to directly push the constraint “C3 : avg(I.price) ≤ $10” deeply into an iterative mining process because the next item to be added to the current itemset can be more expensive or less expensive than the average price of the itemset computed so far. At the first glance, it seems to be hard to explore constraint pushing for such kind of constraints in pattern mining. However, observing that the items in a transaction can be treated as a set, and thus it is possible to arrange items in a transaction in any specific ordering. Interestingly, when the items in the itemset are arranged in a price ascending or descending order, it is possible to explore efficient pruning in frequent itemset mining as we did before. In this context, it is possible to convert such kind of constraints into monotonic or antimonotonic constraints. Hence we call such constraints as convertible constraints.

Let's re-examine the constraint C3. If the items in all the transactions are sorted in the price-ascending order (or items in any transaction are added in this order) in the pattern-growth mining process, the constraint C3 becomes antimonotonic, because if an itemset I violates the constraint (i.e., with an average price greater than $10), then further addition of more expensive items into the itemset will never make it satisfy the constraint. Similarly, if items in all the transaction are sorted (or being added to the itemset being mined) in the price-descending order, it becomes monotonic, because if the itemset satisfies the constraint (i.e., with an average price no greater than $10), then adding cheaper items into the current itemset will still make the average price no greater than $10.

Will the Apriori-like algorithm make good use of the convertible constraint to prune its search space? Unfortunately, such a constraint satisfaction checking cannot be done easily with an Apriori-like