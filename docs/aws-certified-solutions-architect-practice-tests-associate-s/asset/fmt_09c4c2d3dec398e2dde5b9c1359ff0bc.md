
## 2. You need an IPv6 address for a specific instance.

## 3. You want to mask the failure of an instance to network clients.

## 4. You want to avoid making changes to your security groups.

## 183. Which of the following can you not do with an elastic IP address?

1. Change the IP address associated with it while it is in use.
2. Move it from one instance to another.
3. Move it across VPCs.
4. Associate it with a single instance in a VPC.

## 184. Which of the following are advantages of an elastic IP? (Choose two.)

1. Reduces the number of IP addresses your VPC uses
2. Provides protection in case of an instance failure
3. Allows all attributes of a network interface to be moved at one time
4. Provides multiple IP addresses for a single instance

## 185. Which of the following would you need to do to create an elastic IP address? (Choose two.)

1. Allocate an elastic IP address for use in a VPC.
2. Allocate an IP address in Route 53.
3. Detach the primary network interface on an instance.
4. Associate the elastic IP to an instance in your VPC.

## 186. Which of these is not a valid means of working with an Amazon EBS snapshot?

1. The AWS API
2. The AWS CLI
3. The AWS console
4. The AWS EBS management tool

## 187. Where are individual instances provisioned?

1. In a VPC
2. In a region
3. In an availability zone
4. In an Auto Scaling group

## 188. How are EBS snapshots backed up to S3?

1. Incrementally
2. In full, every time they are changed
3. EBS snapshots are backed up to RDS.
4. Sequentially

## 189. You have an existing IAM role in use by several instances in your VPC. You make a change in the role, removing permissions to access S3. When does this change take effect on the instances already attached to the role?

1. Immediately
2. Within 60 seconds
3. The next time the instances are restarted
4. The instances preserve the pre-change permissions indefinitely.

## 190. How many IAM roles can you attach to a single instance?

1. One
2. One or two
3. As many as you want
4. None, roles are not assigned to instances.

## 191. How can you attach multiple IAM roles to a single instance? (Choose two.)

1. You can attach as many roles as you want to an instance.
2. You cannot, but you can combine the policies each role uses into a single new role and assign that.
3. You can assign two IAM roles to an instance, but no more than that.
4. You cannot; only one role can be assigned to an instance.

## 192. You need to make a change to a role attached to a running instance. What do you need to do to ensure the least amount of downtime? (Choose two.)

1. Update the IAM role via the console or AWS API or CLI.
2. Re-attach the updated role to the instance.
3. Restart the instance.
4. Other than updating the role, no additional changes are needed.

## 193. You have a new set of permissions that you want to attach to a running instance. What do you need to do to ensure the least amount of downtime? (Choose two.)

1. Remove the instance’s IAM role via the console or AWS API or CLI.
2. Create a new IAM role with the desired permissions.
3. Stop the instance, assign the role, and restart the instance.
4. Attach the new role to the running instance.

## 194. How can you delete a snapshot of an EBS volume when it’s used as the root device of a registered AMI?

1. You can’t.
2. You can, but only using the AWS API or CLI.
3. Delete the snapshot using the AWS console.
4. Ensure that you have correct IAM privileges and delete the AMI.

## 195. Which of the following is the best option for encrypting data at rest on an EBS volume?

1. Configure the volume’s encryption at creation time.
2. Configure AES 256 encryption on the volume once it’s been started.
3. Configure encryption using the OS tools on the attached EC2 instance.
4. Back up the data in the volume to an encrypted S3 bucket.

## 196. How can you ensure that an EBS root volume persists beyond the life of an EC2 instance, in the event that the instance is terminated?

1. The volume will persist automatically.
2. Configure the EC2 instance to not terminate its root volume and the EBS volume to persist.
3. You cannot; root volumes always are deleted when the attached EC2 instance is terminated.
4. Ensure that encryption is enabled on the volume and it will automatically persist.

## 197. Which of the following is not part of the well-architected framework?

1. Apply security at all layers.
2. Enable traceability.
3. Use defaults whenever possible.
4. Automate responses to security events.

## 198. Which of the following should you attempt to automate, according to the AWS well-architected framework? (Choose two.)

1. Security best practices
2. Scaling instances
3. Responses to security events
4. IAM policy creation

## 199. Which of the following statements are true? (Choose two.)

1. You are responsible for security in the cloud.
2. AWS is responsible for security of the cloud.
3. AWS is responsible for security in the cloud.
4. You are responsible for security of the cloud.

## 200. For which of the following is AWS responsible for security? (Choose two.)

1. Edge locations
2. Firewall configuration
3. Network traffic
4. Availability zones

## 201. For which of the following is AWS not responsible for security?

1. Networking infrastructure
2. RDS database installations
3. S3 buckets
4. Networking traffic

## 202. For which of the following are you not responsible for security?

1. DynamoDB
2. Operating system configuration
3. Server-side encryption
4. Application keys

## 203. Which of the following is not included in the well-architected framework’s definition of security?

1. Data protection
2. Infrastructure protection
3. Reduction of privileges
4. Defective controls

## 204. Which of the following is a principle of the well-architected framework’s security section?

1. Encrypt the least amount of data possible.
2. Always encrypt the most important data.
3. Encrypt everything where possible.
4. Encrypt data at rest.

## 205. Which of the following are principles of the well-architected framework’s security section? (Choose two.)

1. Encrypt data at rest.
2. Encrypt data in transit.
3. Encrypt data in groups rather than individually.
4. Encrypt data at the destination.

## 206. Who is responsible for encrypting data in the cloud?

1. You
2. AWS
3. AWS provides mechanisms such as key rotation for which they are responsible, but you are responsible for appropriate usage of those mechanisms.
4. AWS provides an API, but you are responsible for security when using that API.

## 207. What is the term used to represent the resiliency of data stored in S3?

1. 9 9s
2. 11 9s
3. 7 9s
4. 99th percentile

## 208. Which of these statements is not true?

1. AWS recommends encrypting data at rest and in transit.
2. AWS will never move data between regions unless initiated by the customer.
3. AWS will initiate moving data between regions if needed.
4. Customers move data between regions rather than AWS.

## 209. Which of the following can be part of a strategy to avoid accidental data overwriting of S3 data?

1. IAM roles
2. MFA Delete
3. Versioning
4. All of these
