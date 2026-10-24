# Algorithm: Apriori. Find frequent itemsets using an iterative level-wise approach based on candidate generation.

# Input:

+   - D, a database of transactions;
+   - min_sup, the minimum support count threshold.

# Output:

L, frequent itemsets in D.

# Method:

+   (1) L1 = find_frequent_1-itemsets(D);
+   (2) for (k = 2; Lk-1 != empty; k++) {
+   (3) Ck = apriori_gen(Lk-1);
+   (4) for each transaction t in D { // scan D for counts
+   (5) Ct = subset(Ck, t); // get the subsets of t that are candidates
+   (6) for each candidate c in Ct
+   (7) c.count++;
+   (8) }
+   (9) Lk = {c in Ck | c.count >= min_sup}
+   (10) }
+   (11) return L = Uk Lk;

# procedure apriori_gen(L_{k-1}: frequent (k-1)-itemsets)

+   (1) for each itemset l1 in L_{k-1}
+   (2) for each itemset l2 in L_{k-1}
+   (3) if (l1[1] = l2[1]) ^ (l1[2] = l2[2]) ^ ... ^ (l1[k-2] = l2[k-2]) ^ (l1[k-1] < l2[k-1]) then {
+   (4) c = l1 join l2; // join step: generate candidates
+   (5) if has_infrequent_subset(c, L_{k-1}) then
+   (6) delete c; // prune step: remove unfruitful candidate
+   (7) else add c to Ck;
+   (8) }
+   (9) return Ck;

# procedure has_infrequent_subset(c: candidate k-itemset; L_{k-1}: frequent (k-1)-itemsets); // use prior knowledge

+   (1) for each (k-1)-subset s of c
+   (2) if s not in L_{k-1} then
+   (3) return TRUE;
+   (4) return FALSE;

# FIGURE 4.4

Apriori algorithm for discovering frequent itemsets for mining Boolean association rules.

Because the rules are generated from frequent itemsets, each one automatically satisfies the minimum support. Frequent itemsets can be stored ahead of time in hash tables along with their counts so that they can be accessed quickly.

# Example 4.4. Generating association rules.

Let's try an example based on the transactional data shown before in Table 4.1. The data contain frequent itemset X = {I1, I2, I5}. What are the association rules that can be generated from X? The nonempty subsets of X are {I1, I2}, {I1, I5}, {I2, I5}, {I1}, {I2}, and {I5}. The resulting association rules are as shown below, each listed with its confidence: