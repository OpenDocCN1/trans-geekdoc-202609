thresholds on the number of requests or the amount of data processed, rate limiting can effectively prevent the system from being overwhelmed by excessive demands, whether they are part of a deliberate attack or a surge in legitimate usage. Sophisticated rate limiting can also involve dynamic adjustments based on ongoing system performance and user behavior monitoring, allowing for more flexible and responsive control.

# # Resource Use Capping

Capping resource use per query or processing step is a direct way to control the computational burden placed on an LLM. This can involve setting limits on the number of tokens processed per request, the complexity of the computation allowed, or the time allowed for processing a single input. By imposing these caps, it becomes more difficult for an attacker to induce the LLM to perform highly resource-intensive tasks. This strategy can also help maintain predictable and stable system performance, even under high load conditions.

# # Monitoring and Alerts

Continuous monitoring of the LLM's resource utilization is vital for early detection of potential attacks. This monitoring involves tracking various metrics, such as CPU usage, memory consumption, response times, and the number of concurrent requests. Establishing baseline patterns of regular operation makes detecting anomalies that may indicate an attack easier. Implementing a robust alerting system ensures that any unusual activity is promptly brought to the attention of relevant personnel, allowing for quick investigation and response. This proactive approach is critical in minimizing the impact of attacks and maintaining the reliability of the LLM service.

# # Financial Thresholds and Alerts

Setting financial thresholds and alerts for cloud-based LLMs can drastically reduce the damage from DoW attacks. You should establish budget limits for LLM usage and configure alerts to notify administrators when these thresholds are approached or exceeded. Such measures are essential in pay-per-use models, where the cost implications of high usage can be significant. By closely monitoring usage costs and setting predefined limits, organizations can avoid unexpected financial burdens due to malicious exploitation of their LLM resources.

Model DoS and DoW represent significant threats. As these models become more integral to various applications, understanding and mitigating these threats is essential for maintaining LLM-based services’ operational integrity and financial viability.