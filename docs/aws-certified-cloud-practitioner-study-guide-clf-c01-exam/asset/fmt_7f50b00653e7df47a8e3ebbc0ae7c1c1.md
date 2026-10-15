
The AWS documentation team does a pretty good job keeping their content organized and updated. One important trick—especially if you’ve landed on a page based on the results of an internet search engine—is to look for the word `latest` in the web page’s URL. This tells you that you’re on the page that accurately reflects the most recent version of the software. Here’s an example of a page that includes the `latest` identifier:

`[https://docs.aws.amazon.com/AmazonS3/latest/user-guide/what-is-s3.html](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/what-is-s3.html)`

AWS documentation comes in some other forms, as you’ll discover in the next sections.

### Knowledge Center

The AWS Knowledge Center (`[https://aws.amazon.com/premiumsupport/knowledge-center](https://aws.amazon.com/premiumsupport/knowledge-center)`) is basically a frequently asked questions (FAQ) page that accidentally swallowed a family pack–sized box of steroids and then walked through the radioactive core of a nuclear power plant wearing wet pajamas. Or, in simpler terms, there’s a lot of information collected here.

The Knowledge Center page contains links to nearly 1,000 questions arranged by service, each representing a fairly common problem encountered by real AWS customers. You’ll find questions like, “How can I install the AWS CloudFormation helper scripts on Ubuntu or Red Hat Enterprise Linux?” and “What happens when my reserved instance expires?”

Choosing a question will take you to a page with a proposed resolution and more links to related information. If you’re ever stuck, it’s probably worth taking a quick look to see whether there’s a solution in the Knowledge Center.

### Security Resources

AWS makes it perfectly clear that it wants your deployments to be as secure as possible. One way it makes this easier to accomplish is by maintaining a dedicated documentation page with links to useful and practical security-related resources. The page, found at `[https://aws.amazon.com/security/security-resources](https://aws.amazon.com/security/security-resources)`, points to AWS blogs, white papers, articles, and tutorials covering topics such as security best practices and encrypting your data in transit and at rest.

AWS often adds new content to the collection, and the links to blogs will always lead to fresh content.

### Discussion Forums

When things don’t work the way you expected, it’s generally safe to assume you’re not the first person to hit this particular brick wall. Even if this is something only a couple dozen people have experienced, there’s a good chance that at least one of them asked about it on some online forum. While many of those questions were probably asked on Stack Overflow or another public site, the AWS discussion forums have also addressed their share of problems.

The site—found at `[https://forums.aws.amazon.com](https://forums.aws.amazon.com)`—is divided into categories including Amazon Web Services (which is further divided into individual services), AWS Startups (focused on newcomers to the platform), AWS Web Site and Resources (topics like Java Development and High Performance Computing), and a number of areas serving non- English speakers using languages like Japanese and German. You can search the entire site or individual forums to see whether your question might already have been answered.

To post on the forum, you’ll need to be signed into your AWS account *and* have a forum nickname and email.

## Trusted Advisor

You use Trusted Advisor to visually confirm whether your account resource configurations are sound and are compliant with best practices. Trusted Advisor organizes its compliance alerts across five categories, which are described in [Table 3.3](#c03.xhtml#table3-3).

[**TABLE 3.3**](#c03.xhtml#tableanchor3-3) The Five Trusted Advisor Alert Categories

| Category || Purpose || Examples |
| --- | --- | --- |
| Cost Optimization || Identifies any resources that are running and costing you money but are either underutilized or inactive || EC2 instances or Redshift clusters that, over time, are mostly idle |
| Performance || Identifies configuration settings that might be blocking performance improvements || Inappropriate reliance on slower magnetic or low-throughput Elastic Block Store (EBS) volumes |
| Security || Identifies any failures to use security best-practice configurations || Simple Storage Service (S3) buckets with publicly accessible permissions or security groups permitting unrestricted access |
| Fault Tolerance || Identifies any running resources that, through poor configuration, are unnecessarily vulnerable to service disruptions || Data volumes that aren’t properly backed up or instances that aren’t replicated |
| Service Limits || Identifies resource usage that’s approaching AWS Region or service limits (as described in Chapter 2, “Understanding your AWS Account”) || Your account is currently using close to the 100 Simple Storage Service (S3) buckets limit |

The status of an advisor *check* is illustrated by the icon next to a particular item. [Figure 3.1](#c03.xhtml#figure3-1) shows what a healthy service limit status might look like. However, if, for instance, you haven’t configured multifactor authentication for your root account, you’ll get a red alert icon suggesting that you should seriously consider attending to the problem. Each item can be expanded to provide contextual information.

![FIGURE 3.1 The green “healthy” icon indicating that these services are not approaching their service limits](images/c03f001.jpg)

[**FIGURE 3.1**](#c03.xhtml#figureanchor3-1) The green “healthy” icon indicating that these services are not approaching their service limits

As you’ve already seen, the full range of Trusted Advisor alerts is only available for users signed on to either the Business or Enterprise Support service tier. For everyone else—including those on the free Basic Support plan—access is limited to service limits and some of the security alerts. All users are able to browse through inactive versions of the entire range of alerts to at least see what they’re missing.

This is an automated service, so, as you may see for yourself as you work through Exercise 3.2, you should expect to encounter some false positives. For instance, Trusted Advisor will flag any S3 bucket that permits public access. A lot of the time, that’s a signal of a serious problem, but sometimes—as when you’re using the bucket to host a static website—that’s exactly what you want. So, don’t think you have to blindly follow all the suggestions you’re shown. This is an *advisor*, after all, not your mother.

## Summary

AWS requires you to select one of four support plans. The Basic plan is free, Developer starts at $29, Business starts at $100, and Enterprise starts at $15,000. Nonfree plans (beyond the minimum charge) are billed as a percentage of total monthly resource usage. The higher the support level, the more responsive and personalized the technical troubleshooting and planning support you get.

The Developer Support plan is aimed at organizations still testing and planning deployments. The Business Support plan is for smaller operations running relatively light production infrastructure. The Enterprise Support plan is ideal for large production deployments with a global footprint that cannot tolerate downtime.

AWS provides exhaustive and regularly updated documentation using multiple styles across a number of web platforms. Those include user guide documentation pages, the Knowledge Center, resources specific to security, and discussion forums.

The AWS Trusted Advisor alerts users to the best-practice compliance of their running account resources. Basic Support and Developer Support plan users get service limit and some security information, while Business and Enterprise customers get access to all alerts.

## Exam Essentials
