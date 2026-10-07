# Summary

![](bbox=[0.135, 0.105, 0.864, 0.35])

Figure 8.22 - Cloud Armor named IP list

In Figure 8.22, you can see how named IP lists work. CDN provides a list of IP addresses, such as 23.235.32/20, 43.249.72/20, and so on. Only communication coming from these IP addresses is permitted by this security rule. This means that the traffic of 2 CDN providers can be accessed (the access points are 23.235 32 10 and 43.249 72 10), while unapproved traffic from 198.51.100.1 is banned.

# Summary

In this chapter, we looked at some advanced network security concepts. We covered the usage and configuration of Private Google Access, IAP and its use cases, and Cloud NAT. Finally, we looked at Cloud Armor and how it protects against DDoSs and web-application-based attacks. We also covered additional details related to Cloud Armor, such as security policies, WAF rules, and named IP lists.

In the next chapter, we will cover data security, which is an important topic for the exam. We will look at the Google Cloud Key Management system and then cover data loss prevention and Secret Manager in the subsequent chapters.