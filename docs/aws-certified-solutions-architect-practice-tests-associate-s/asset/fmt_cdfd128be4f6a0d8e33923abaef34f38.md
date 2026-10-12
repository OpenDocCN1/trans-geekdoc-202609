
## 132.  You have a number of large PDF files stored in an RDS instance. These PDFs are accessed infrequently, but when they are accessed, they need to respond quickly to requests. As the user base increases, the load is beginning to overwhelm the database. What suggestions would you make to improve performance? (Choose two.)

1.  Move the PDFs to S3.
2.  Install ElastiCache in front of the database.
3.  Create read replicas of the primary database.
4.  Consider increasing the available memory for the database instance.

## 133.  You have a number of large PDF files stored in an RDS instance used by a company’s internal staff, of which 80% are on-site. These PDFs are accessed infrequently, but when they are accessed, they need to respond quickly to requests. As the company’s support staff has increased, the load is beginning to overwhelm the database. What suggestions would you make to improve performance? (Choose two.)

1.  Set up a CloudFront distribution.
2.  Upgrade the instance running the RDS database.
3.  Consider installing a storage gateway with stored volumes at the customer’s on-premises site.
4.  Install ElastiCache in front of the database.

## 134.  You have a number of large PDF files stored in an RDS instance used by a company’s geographically distributed user base. These PDFs are accessed infrequently, but when they are accessed, they need to respond quickly to requests. As the company’s user base has increased, the load is beginning to overwhelm the database. What is the best option for improving database performance?

1.  Set up a CloudFront distribution.
2.  Create read replicas across the regions in which the user base accesses the application.
3.  Consider installing a storage gateway with stored volumes at the customer’s on-premises site.
4.  Install ElastiCache in front of the database.

## 135.  You have a number of large images stored in an RDS instance used by a company’s geographically distributed user base. Each of these images is accessed several thousand times a day and needs to respond quickly to requests. As the company’s user base has increased, the load is beginning to overwhelm the database. What is the best option for improving database performance?

1.  Upgrade the instance running the RDS database.
2.  Create read replicas across the regions in which the user base accesses the application.
3.  Consider installing a storage gateway with stored volumes at the customer’s on-premises site.
4.  Install ElastiCache in front of the database.

## 136.  Which of the following are valid routing policies for Route 53? (Choose two.)

1.  Simple routing
2.  Fault recovery routing
3.  Latency-based routing
4.  Cached routing

## 137.  Which of the following are valid routing policies for Route 53? (Choose two.)

1.  Geolocation routing
2.  Weighted routing
3.  Round-robin routing
4.  Distributed routing

## 138.  Which of the following are valid routing policies for Route 53? (Choose two.)

1.  FIFO routing
2.  Multivalue answer routing
3.  Geoproximity routing
4.  Distributed routing

## 139.  Which of the following routing policies sends traffic to a single resource, such as a web server?

1.  Geolocation routing
2.  Weighted routing
3.  Simple routing
4.  Latency-based routing

## 140.  Which of the following routing policies sends traffic to a single resource, unless that resource is unhealthy, and then routes to a backup resource?

1.  Health-based routing
2.  Failover routing
3.  Simple routing
4.  Latency-based routing

## 141.  Which of the following routing policies chooses a route for a user based on the user’s geographic location?

1.  Health-based routing
2.  Failover routing
3.  Geolocation routing
4.  Region-based routing

## 142.  Which of the following routing policies chooses a route for a user based on the latency of the available region to which traffic can be directed?

1.  Health-based routing
2.  Latency-based routing
3.  Geolocation routing
4.  Region-based routing

## 143.  Which of the following routing policies can direct traffic to multiple resources as long as those resources are healthy?

1.  Health-based routing
2.  Latency-based routing
3.  Multivalue answer routing
4.  Region-based routing

## 144.  Which of the following routing policies uses assigned weights to shape traffic to different resources?

1.  Health-based routing
2.  Latency-based routing
3.  Multivalue answer routing
4.  Weighted routing

## 145.  Which of the following routing policies is ideal for routing traffic to a single web server?

1.  Simple routing
2.  Latency-based routing
3.  Multivalue answer routing
4.  Weighted routing

## 146.  Which of the following Route 53 routing policies are ideal for a geographically distributed user base? (Choose two.)

1.  Geolocation routing
2.  Geographical routing
3.  Geoproximity routing
4.  Weighted routing

## 147.  Which of the following values is an invalid weight for a weighted routing policy?

1.  1
2.  255
3.  125
4.  These weights are all valid.

## 148.  How does a weight of 0 affect routing on Route 53 when using a weighted routing policy?

1.  0 is an invalid weight.
2.  All traffic is directed to the resource with a weight of 0, as long as that resource is healthy.
3.  No traffic is directed to the resource with a weight of 0.
4.  Traffic is routed to the resource, but health checks are not performed.

## 149.  You have three resources in a weighted routing policy. Resource A has a weight of 100, resource B has a weight of 100, and resource C has a weight of 200. How will traffic be routed in this scenario?

1.  25% of traffic to resource A, 25% of traffic to resource B, and 50% of traffic to resource C
2.  10% of traffic to resource A, 10% of traffic to resource B, and 20% of traffic to resource C
3.  33% of traffic to resource A, 33% of traffic to resource B, and 33% of traffic to resource C
4.  There is not enough information to know how routing will occur in this scenario.

## 150.  Which of the following statements concerning Route 53 routing policies are true? (Choose two.)

1.  You can have multiple primary resources in a simple routing policy.
2.  A weighted routing policy uses weights for routing, but not health checks.
3.  You can have multiple secondary resources in a simple routing policy.
4.  Health checks are ignored if a resource has a weight of over 100 in a routing policy.

## 151.  You are responsible for a media-serving website backed by a database that has a global user base. The fleet of EC2 instances serving the website is responding well to requests from the US, but requests from the EU are taking nearly five times as long to receive a response. Database CPU utilization stays between 70% and 90% throughout the day. What suggestions would you make to attempt to improve performance of this website? (Choose two.)

1.  Install ElastiCache in front of the RDS instance to cache common queries and reduce database reads and therefore overall load.
2.  Set up CloudFront to enable caching of data at edge locations closer to the EU user base.
3.  Set up an Auto Scaling group with low CPU thresholds to scale up the EC2 instances.
4.  Create additional EC2 instances that will serve the website, and locate them in a South Asia region.

## 152.  Which of the following are not valid instance types? (Choose two.)

1.  T3
2.  E1
3.  M5
4.  Q2

## 153.  What is the primary purpose of IAM?

1.  Deployment of applications
2.  Management of permissions in AWS
