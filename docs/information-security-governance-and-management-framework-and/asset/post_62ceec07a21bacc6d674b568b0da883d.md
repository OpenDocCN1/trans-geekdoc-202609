
![](img/90693339cd50db9a18259ad447383b45_201_0.png)

## Figure 9.1 Expected trends of ALE and TCO

Cost analysis). TCO answers the question “How much does security cost?” TCO is well understood by senior officials, who are accustomed to comparing benefits and the evolution of expenses, including those related to security.

The gain from security investments alone—economic value added (EVA)—is difficult to calculate for the reasons mentioned previously, but it can be calculated indirectly by observing changes in ALE and TCO. Both trends are presented in Figure 9.1. The added value of security investments could then be expressed as:

EVA = ΔALE / ΔTCO

EVA should always be <1 for security investments to be cost-effective. Indeed, if EVA > 1 according to this formula, then security investments (TCO) are not enough to compensate for potential losses. If EVA = 1, then security costs just barely compensate for the evolution of potential losses.

EVA as expressed here can be considered the same as return on security investments (ROSI). Several tools or methods exist to calculate ROSI based on loss and investment analyses for specific security processes or controls.

The main difficulty with these methods is that the estimate of a loss must be associated with its probability of occurrence for all the business units and all the controls deployed, which may be very inaccurate. An accurate calculation method requires statistics over several years with precise figures on incidents, their typology, and estimates of losses incurred. And this is for estimates of direct losses. Indirect losses (such as loss of customers or reputation) are even more difficult to estimate. It clearly becomes impossible for businesses to effectively manage such a large amount of data in a constantly changing production environment while keeping pace with new technologies.

Trying to calculate return on security investment (ROSI) for all the security investments is very difficult, if not impossible, for the reasons just mentioned. On the other hand, this is relatively easy to calculate for elements or isolated technical protection devices such as firewalls, intrusion detection systems, antiviruses, etc. Delineating the scope and identifying the purpose of the measurements are key in this process.

Before discussing the delineation of measurement domains and the evaluation of the ROSI, it is essential to understand the benefit provided by security controls. To make an analogy, the benefit of the braking system on a vehicle is obvious. We can then quantify the cost of a failure and estimate the ROSI, which will probably be very high. Without answers to these questions on the added value, we cannot design the metrics and calculate the ROSI.

### EXAMPLE

To calculate the profit or added value of strong authentication, we can take the increase in the system’s added value compared with authentication based on simple user ID and password. This added value can then be calculated by the reduction of the risk of fraud or the reduction of negative economic impact. Metrics to assess threats or vulnerabilities, for example, include the increase in the number of people who can easily access applications or the number of exposed applications. For financial impact, we can use cost of data breach surveys from specialized institutes and make an estimate or extrapolation in the particular context of the company.

But is it really necessary to calculate ROSI accurately? It is more important to be able to assess its magnitude on the basis of a risk analysis. We will now focus on calculating ROSI based on the probability of incident occurrences and an estimation of their impact. To estimate the total cost of an incident, it is obviously necessary to know its impact and estimate the total cost of rectifying the damage. To estimate the impact, we can use publications on losses or arbitrarily set a cost. The same can be done to estimate probability based on different reports or specialized studies.

## 9.2.1 Calculation of ROSI Based on Risk Analyses

The benefit obtained from countermeasures is the difference between the inherent risk (without security controls) and the residual risk (after setting up countermeasures). If we consider that countermeasures modify the probability (P) of occurrences (e.g., the probability of the occurrence of an attack decreases because of measures such as antivirus or intrusion detection), risk impacts (or ALE) can then be calculated as follows:

Impact of the inherent risk = Cost of incident × P(inherent risk)

Impact of the residual risk = Cost of incident × P(residual risk)

The benefit can then be expressed as:

Benefit (EVA) = Impact of inherent risk − Impact of residual risk

and the ROSI as:

ROSI = Benefit − Cost of countermeasures

Discussions with management will thus be about calculating the probabilities of occurrence; in other words, how risks are analyzed. It should be possible to show how the security measures taken modify the probabilities of occurrence and/or the level of impact.

## 9.2.2 Protection Capacity Index

If we know the impact of inherent risk (*IR*) weighted by its probability of occurrence and the impact of residual risk (*RR*) weighted by its probability, then we can use an index called *protection capacity* (*PC*), expressed as:

PC = (IR − RR) / IR

Protection capacity is ideal if the index tends to 1. This will happen if the impact of the residual risk is very small (or tends to 0) or if the difference between the inherent risk and the residual risk is very large. The idea behind this indicator is to attach a value to the means of protection in place or the degree of risk mitigation. If we know the operational costs or the cost of controls to reduce the risk, we will be able to follow the evolution of our protection capacity with the evolution of investments. The *IR − RR* difference presents the risk reduction capacity.

This leads to several reflections. First of all, only the operational costs directly related to the impacts of the analyzed risks should be taken into consideration. In other words, we need to look only at controls that reduce the analyzed risk. Ideally, the *PC* will be calculated by risk. Subsequently, it may be possible to aggregate the indices of several risks into one that has an average protection capacity.

By combining the indicators on the operational costs of controls and the indices of protection capacity by risk, we will be able to present a risk map highlighting the relationship: operational costs − protective capacity (Figure 9.2). This will also point out risks having high operational costs for which our protection capacity is low (bottom right field).

![](img/90693339cd50db9a18259ad447383b45_204_0.png)

**Figure 9.2** Risk distribution according to their protection capacity and operational costs.

### EXAMPLE

A Distributed Denial of Service (DDoS) cybersecurity risk or an attack aimed at making a web server unavailable by saturating it with queries will be mitigated by relatively expensive controls, which will probably be justified as long as the probability of occurrence or the impact is drastically reduced. In this case, protection capacity will be close to 1 despite the high operational costs. The risk will be located in the upper right corner in Figure 9.2.

The impact of the inherent risk of computer data loss is very high, but backups have reduced this likelihood, so the residual risk is very small. Therefore, protection capacity is close to 1 (very high), and operational costs are relatively low. The risk will therefore be located in the upper left corner in Figure 9.2.

*Can we use some modeling to estimate ROSI or better assess the impact of change?*

## 9.3 Modeling

Many disciplines use models to represent reality so as to simulate or observe the behavior of a system, make “what if” analyses, or extrapolate the effects of decisions.

All change projects involving new investments are characterized by a setup phase that increases costs, followed by an operational phase in which real costs (as operational costs per unit of value produced) decrease. Cost evolution modeling makes it possible to visualize not only the ROI of the envisaged solution but also the timeframe until the breakeven (BE) point, taking into account the initial investments (Figure 9.3). During the start-up of a new solution, setup costs are added to operational costs. Since the costs of the new solution will decrease once it is in operation, after amortizing the costs of carrying out the project, a BE point will be reached after a certain period of time. We will talk here about the *timeframe* of the ROI.

This approach makes it possible to plan expenses in relation to expected benefits. For such modeling to be possible, it is important to project the evolution of the operational costs of the current solution (status quo), the project costs, and the
