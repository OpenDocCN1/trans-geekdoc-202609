+   1. The BFDS learning set is acquired (stolen) by attackers.
+   2. Access to accounts is gained, enabling transactions.²
+   3. Create an IFDS to emulate BFDS.
+   4. Create a model, generator, based on the GANs approach.
+   5. Use the generator from step 4 to generate a dataset imitating a specific distribution.
+   6. Test the data from step 5 on the classifier created in step 3 (IFDS).
+   7. With satisfactory results of step 6, use the generated data in actual banking transactions, i.e., attack BFDS.

The purpose of generating data that appears to be legitimate transactions is to produce a set of transactions that does not raise an alert by BFDS. This means:

+   - Forcing a false-negative classification for an attacker to carry out a fraudulent transaction
+   - Generating transactions that appear to be legal in significant numbers.

Assuming that the computational cost of processing each transaction is > 0, and the banking infrastructure is scaled to a limited extent, it is theoretically possible to carry out a DDoS attack on the BFDS infrastructure in this way. It is also possible to generate transactions that look like financial frauds (false-positive errors). Raising many false-positives, carried out at high intensity in the short term, can paralyze the functioning of the antifraud team. In the extreme case, multiple false-positive alerts can strongly create a lack of confidence in the BFDS.

The practical use of those scenarios is highly complicated and requires significant resources and coordination of transactions from multiple mule accounts.

# 17.3  GENERATOR AND DISCRIMINATION MODEL

# 17.3.1  Model Construction

# 17.3.1.1  *Imitation Fraud Detection System Model*