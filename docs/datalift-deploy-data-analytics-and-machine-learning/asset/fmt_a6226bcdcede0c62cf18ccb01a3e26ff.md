
![Siemens Mobility use cases](Image00002.jpg) “Deployment must inform all the steps taken before. For instance, if you're doing detection and were to use the most massive, most powerful detector out there, but you find you don't have the hardware to run it, then you need to go back to the whiteboard and choose something else.” Irina Vidal Migallón, Technical Lead AI & Computer Vision

I'm just going to show you a couple of use cases that, at their core, have the same machine learning concept. But you'll see how they look nothing like each other precisely because of how they're deployed.

## Use case 1: Inspection of rail track joints

The first use case is about the inspection of rail track joints. We gather data by specially equipped rail vehicles that run around collecting images. At its core, the machine learning task is to locate the joints and determine whether the joints are damaged (or not) and what type the damage is.

For the first use case, our customer is a rail maintainer. Rail maintainers make sure that the railway is safe, for example, by checking the joints of kilometers and kilometers of rails across countries and identifying any damage happening to those joints. In the past, either someone needed to survey the rail track or manually go through many images. Most of the footage has nothing relevant because there isn’t a joint every millimeter. In effect, you have terabytes of data, and only a small part of that will be applicable.

Siemens Mobility has a cloud application that enables rail maintainers to survey the joints through a user interface. The workflow is as follows: there is a bucket with terabytes of images, and we have a couple of containers that first detect the joints, and next classify whether it's damaged or not, and what type of damage it is. Data on damages, amongst other data, is stored in a database. The user can go through a map, click on the joints flagged as damaged, and look at the specific information.

A critical part of this process is the feedback loop with the user. Our users have a wealth of domain knowledge but perhaps are not familiar with the data requirements in Machine Learning. Before you go into development, you need to find the right way to get their input and how they wish to interact with the system. After you've deployed, you keep checking how the user interacts with your application.

## Use case 2: Signal recognition for autonomous rail

The second use case is signal recognition. Regardless of whether we're talking about city trams or mainline trains, the signals are scattered along the route. At its core, this is a location and classification problem. However, the devil is in the details.

In this use case, we know that we cannot rely on a data link to the train. We need a computer on the train. Moreover, the prediction needs to be in real-time, and it has to work at all times, whether the temperature is +40 C or -40 C. The use case requires incredibly robust hardware on the train.

### Considering differences

Let’s consider some of the resulting differences in using machine learning for these two use cases. In the case of rail track inspection, we rolled out on a cloud platform, ran on CPUs, and used the Python stack. We use S3 buckets, and because the latency requirements aren't strict, we can work in batches. If it takes a little longer, that's quite all right. Also, there's no competition for resources with other processes.

With signal recognition, the biggest concern is safety. The solution must be stable. The hardware needs to remain steady at all times under all temperatures, which already conditions the kind of GPU you can use – or even if you can use a GPU at all. There is special legislation, the development of which for autonomous driving is in the early stages only. And there is the real-time requirement.

What from a pre-production perspective looked like two very similar machine learning problems – both are ‘detect & classify’ – changes very much from the customer’s perspective and the solution’s deployment.

In sum, how you deploy shapes the whole product and also affects the original machine learning algorithms.

### From the Q&A

“Were there any surprises after going into production?”

“Well, yes. For instance, the rail track maintainers got back and said they had all false positives. We discovered that the images were not being uploaded as expected.”

“Do you collect feedback from multiple users, and how do you validate a difference in feedback?”

“Feedback is something delicate. Getting annotations right may be complicated, and there is usually variability within the same person. Indeed we measured differences within the same customer.”

“How do you deal with model drift?”

“You can and should put metrics in place to monitor how the behavior changes. It nevertheless is a challenging issue, especially within different campaigns.”

“Models decay with time; how do you trigger the retraining?”

“You can start small and fairly simple, possibly even manually. Once you are sure you can validate all the user feedback coming and trust all your monitoring metrics, then you can automate retraining to correct any kind of data or model drift and re-deploying.”

For open positions at Siemens Mobility, see [www.mobility.siemens.com/global/en/company/jobs.html](https://www.mobility.siemens.com/global/en/company/jobs.html)

---

## Automated decision making for supplier management

### Invoice classification

**Dr. Nicholas Hoff**  
Founder, New Approach Technologies  
Moderated by Evan Simpson

Can you automatically and accurately decide whether to pay an invoice? How to automate decision making at the 99.5% confidence level.

[New Approach Technologies](http://newapproachtechnologies.com/) is my freelancing firm. I consult, build quick prototypes, and deploy production systems. Consulting often is exploratory and driven by questions clients have, for example, about the feasibility and value of Data Science for their company. Prototypes are a low-risk way for people to see what’s possible with their data.

“I have built many production systems over the past years, especially in the banking sector. The deployment of machine learning has now become common in this area, partly because of the plentiful data available.” Nick Hoff, Machine Learning expert

I will show you the invoice classification problem that Société Générale presented to me. We will survey some of the machine learning techniques that I considered using, why they worked, and when they didn't work. Finally, I will discuss the solution that went into production and elaborate on some of the more interesting points about productionizing machine learning.

### Classifying invoices to automate payment

One branch of Société Générale runs a corporate car leasing operation. Since the cars are leased, Société Générale is responsible for the maintenance. Whenever a car goes to a maintenance shop, the maintenance or repair generates an invoice. The invoice goes to Société Générale, and an expert decides whether or not to pay it. The goal of this project was to automate that decision partially.
