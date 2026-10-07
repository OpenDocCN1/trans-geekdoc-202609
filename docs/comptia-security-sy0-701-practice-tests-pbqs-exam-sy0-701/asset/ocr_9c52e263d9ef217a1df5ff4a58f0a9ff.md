Option A is incorrect. An Active IDS can detect potential security breaches and take action, which may introduce latency or alter the traffic flow.

Option B is incorrect. While the term “passive firewall” is not standard, traditional firewalls can actively block or allow traffic, which can introduce changes to the network flow.

Option C is incorrect. An Active firewall actively filters network traffic based on configured policies, potentially affecting the network flow.

Question 254. A developer at your company is excited about the scalability benefits of serverless architecture and has deployed a new service using it. However, you notice an increased bill due to the service even when it’s not in use. Which of the following could be a contributing factor?

+   (A) The serverless functions are continuously triggered by unintended events

+   (B) The server hardware is outdated

+   (C) The load balancer is misconfigured

+   (D) The organization lacks a Content Delivery Network (CDN)

Explanation 254. Correct Answer: A. The serverless functions are continuously triggered by unintended events.

Serverless architectures charge based on the number of function invocations and the execution time. If there are unintended events, such as rogue requests or misconfigured triggers, continuously invoking the serverless functions, it could lead to unexpected costs.