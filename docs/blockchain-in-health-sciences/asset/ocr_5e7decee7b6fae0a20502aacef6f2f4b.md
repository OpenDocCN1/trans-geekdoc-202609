# BLOCKCHAIN EMPOWERED PHARMACEUTICALS 223

![](bbox=[0.12935, 0.11935, 0.94135, 0.46335000000000004])

**Figure 10.11** A message sequence diagram is presented illustrating two scenarios: Case 1, depicting a failed consumer authentication, and Case 2, demonstrating a breach in shipment specifications [6].

container’s improper route. The smart contract receives these events from sensors inside the smart containers. According to the contract, the customer has 72 hours to provide the correct secret code. If this is not done, the customer will receive a 50% freight refund, and the delivery will be permanently canceled. Furthermore, Figure 10.11 describes circumstances in which the smart contract provides reimbursement, such as an accidental container breakage during shipment.

Improving the security protocols in the suggested approach involves applying a cryptographic hashing method to confirm the hash provided by the contract. After the customer deposits payment for the goods, a secret hash is supplied to them for digital authentication of their identity. When the medication package is delivered, the customer can present this hash. The smart contract then verifies that the hash corresponds to the one entered during the deposit phase. If they match, it confirms that the customer has rightful custody of the pharmaceutical package. For the container to unlock, the customer must supply the correct code. If the correct code is not provided, the container waits three days, giving the customer time to submit it. An event is triggered to cancel the shipment if