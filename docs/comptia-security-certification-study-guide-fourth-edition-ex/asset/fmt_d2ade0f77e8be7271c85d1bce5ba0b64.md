
# The first step is to create a scale for the probability of a threat occurring

[Table 17-1](#ch17.xhtml#ch17tab1) displays an example of a table of probability values. Other terms for probability are *likelihood* and *likelihood of occurrence,* which is the term used by the Security+ certification objectives.

## TABLE 17-1

### A Sample Probability Scale

![Image](t0682-01.jpg)

The table reflects that you have decided on five values for probability. With each of the threats listed with the assets, you will assign a probability value to indicate how likely it is that the threat will occur. For example, the web server hosting a public e-mail site has a threat of a denial of service attack, and you assign the threat a probability of "Likely," which has a value of 3.

Once you have determined the probability, you will identify the *impact* associated with each of the threats. Like the probability, the loss is based on a scale—you may want to use a "low/medium/high" scale, or come up with your own scale, such as the one found in [Table 17-2](#ch17.xhtml#ch17tab2).

## TABLE 17-2

### A Sample Impact (Loss) Scale

![Image](t0682-02.jpg)

Looking at the table, you can see I have gone with another scale that has five values. This gives you some flexibility when assigning an impact to each of the different threats. For example, you may decide that denial of service attacks to your e-commerce web site have a "Medium Impact" level because they will crash the server and make it unavailable for business.

Once you have identified the probability and the impact (loss) for each of the risks, calculate the risk of each threat based on our formula of *risk = probability × loss.* [Table 17-3](#ch17.xhtml#ch17tab3) displays an example of how you should plot the threats against an asset and then calculate the risk associated with each threat by using qualitative analysis. You measure the risk associated with each of the threats by using the probability and the loss (known as impact). This allows you to prioritize the threats and to deal with the highest-priority threats first by investing in security solutions to protect the asset from those high-priority threats. In this example, your high-risk threats are the SQL injection attack and the buffer overflow attack, so you would invest in controls to prevent those threats from occurring.

## TABLE 17-3

### Qualitative Risk Analysis Example for an E-commerce Site

![Image](t0683-01.jpg)

![Image](exam.jpg)

**Qualitative risk analysis has the benefit of being a very quick assessment type because you are not bogged down with figuring out financial figures—you are simply applying values based on a scale you create.**

## EXERCISE 17-1

### Performing a Qualitative Risk Analysis

In this exercise, you will identify a few assets within your organization and perform a risk assessment by identifying sample threats against the assets and then calculating the risk based on a qualitative approach.

1. On a piece of paper, or using your favorite word processor, identify three different assets within your organization.
2. Identify three or four threats against each asset.
3. Using the scale for probability displayed in [Table 17-1](#ch17.xhtml#ch17tab1), record the probability value for each threat.
4. Using the scale of impact displayed in [Table 17-2](#ch17.xhtml#ch17tab2), record the impact each threat will have.
5. Calculate the risk based on the formula of `risk = probability × loss (impact)`, and then prioritize the threats based on the highest risk being the highest priority.

![Image](exam.jpg)

**With quantitative analysis, the resulting cost of the threat helps determine how much you should invest in a security solution to protect the asset.**

## Quantitative

The other type of risk analysis is quantitative. The drawback of qualitative analysis is that you are using a scale someone created to judge the seriousness of the threat, and the seriousness is subject to the viewpoint of the person doing the assessment.

With quantitative analysis, you calculate dollar amounts for each of the risks and what the impact of the threat is. This is a critical type of assessment because upper-level management wants to see dollar figures to justify the cost of purchasing a security control to protect the asset. For example, with quantitative analysis, if you say, "The threat is going to cost us $1,400 a year, so we should purchase a firewall solution that will cost us $6,500 a year over three years," management may well tell you to find a cheaper solution.

The first step to quantitative analysis is to assess the value of the asset. For example, you may determine that your e-commerce web site brings in thousands of dollars a day of revenue—this will help you calculate the value of the asset.

Once you know the value of the asset, you then must determine the impact that each threat to the asset would have. With quantitative analysis, the impact is specified as an *exposure factor (EF),* which is the percentage of the asset's value that is lost if the threat occurs.

Once you know the value of the asset and have an exposure factor associated with each threat, you can then calculate what is called the *single loss expectancy (SLE),* which is a dollar figure representing how much money the company will lose each time the threat occurs. The following is the formula for single loss expectancy:

```
SLE = value ($) × EF (%)
```

For example, let's say you decide the e-commerce web site has a value of $200,000, and each time the web server has a hard drive failure, you lose 8 percent of the *asset value.* This means that your single loss expectancy is $200,000 × .08, which is $16,000. Therefore, every time the hard drive fails in the server, your business loses $16,000!

![Image](exam.jpg)

**For the Security+ exam, remember how to calculate single loss expectancy: `SLE = value of asset × exposure factor`.**

Once you have calculated the single loss expectancy, you can work on calculating the *annualized loss expectancy (ALE),* which is a calculation of how much money you will lose per year with each of the threats. The formula to calculate the annual loss expectancy is to take the single loss expectancy and multiply it by the *annualized rate of occurrence (ARO).* The annual rate of occurrence is how many times a year you expect the threat to occur.

```
ALE = SLE × ARO
```

For example, you may expect a threat to occur three times a year or to occur once every five years. The following example calculates the ALE for our hard drive failure threat if it were to occur three times a year:

```
ALE = $16,000 × 3
```

This means that the ALE based on the hard drive failing three times a year would cost the company $48,000. You need to make sure that the solution you implement to protect from hard drive failure does not cost more than $48,000 a year.

![Image](exam.jpg)

**For the certification exam, remember that annual loss expectancy is calculated by the `SLE × annual rate of occurrence`.**

Let's look at a different ARO. If the failed hard drive threat was expected to occur once every five years, then your ARO would be 1/5, or .20. This means that your formula to calculate the annual loss expectancy would be

```
ALE = $16,000 × .20
```

This results in an ALE of $3,200. Therefore, you need to find a security solution to protect the asset that costs no more than $3,200 a year.

The benefit of quantitative analysis is that you are calculating exact dollar figures, which is what management likes because it is easy to see if implementing a solution makes sense financially. The drawback of quantitative analysis is the time it takes to calculate these numbers; for example, it is difficult to place a value on an asset because so many variables are involved.

![Image](exam.jpg)

**Quantitative risk analysis has the benefit of you being able to make informed decisions based on whether a security control is financially worthwhile.**

## EXERCISE 17-2
