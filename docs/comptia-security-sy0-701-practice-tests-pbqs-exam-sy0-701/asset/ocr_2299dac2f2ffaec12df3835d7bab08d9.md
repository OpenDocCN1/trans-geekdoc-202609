Option A is incorrect. Fail-open is the opposite of what the organization wants. In a fail-open scenario, if the system fails, it would allow all requests by default.

Option C is incorrect. While “fail-secure” is another term for “fail-closed”, the use of both terms in the options can confuse the test-taker. In this context, option B is the more appropriate choice.

Option D is incorrect. Fail-passive isn’t a standard term in the context of authentication failure modes. Fail-open and fail-closed (or fail-secure) are the primary recognized terms.

**Question 530.** Jane, a security analyst, receives a report about network slowdowns happening at specific times of the day. After investigating, she discovers that a device is flooding the network with traffic, causing legitimate requests to be dropped. Which type of attack is this device likely performing?

+   (A) Distributed Denial of Service (DDoS)
(B) ARP poisoning
(C) MAC flooding
(D) DNS amplification

**Explanation 530.** **Correct Answer: C. MAC flooding.** MAC flooding is an attack that aims to flood the switch’s MAC table with fake MAC addresses until the table overflows. Once it overflows, the switch acts as a hub broadcasting packets to all machines in the network. This can cause significant slowdowns and disruptions.