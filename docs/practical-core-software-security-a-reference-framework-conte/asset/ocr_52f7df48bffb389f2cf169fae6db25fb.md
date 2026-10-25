all of the identified threats, they are ranked from the highest to lowest risk. Some threats may also be ignored because of the very limited likelihood that they will occur, in addition to the limited harm the vulnerabilities would cause if they were exploited. A prioritized list of threats by risk will significantly help the priority and importance of mitigation. At a high level, these risks will typically be ranked as high, medium, and low. A typical risk probability formula used in industry shows the risk and consequence of a particular vulnerability as equal to the probability of the threat occurring multiplied by the damage potential. That is,

# Risk = Probability × Damage Potential

A 10-scale measurement is typically used in risk probability calculations, with the number 1 representing a threat or component of a threat that is least likely to occur and the number 10 representing that which is most likely to occur. The same 1-to-10 ranking system is used for assigning damage potential, with 1 indicating the least damage potential and 10 the most.

As an example of the mechanics involved, a threat that is moderately likely to occur, with a probability risk score of 5, and a high damage potential of 10 has a risk equal to that of a threat having a probability risk score of 10 and a medium damage risk potential of 5. Mathematically,

```
If Probability = 5 and Damage Potential = 10, then Risk = 5 × 10 = 50%
If Probability = 10 and Damage Potential = 5, then Risk = 10 × 5 = 50%
```

As you can see from this example, 100 can be divided into three ranges of numbers to indicate a high, medium, or low risk rating. Obviously, your level of priority to fix the vulnerabilities will start with the highest priority of risk, which likely means that immediate mitigation is required. Then you would tackle vulnerabilities of medium risk, which should be done shortly thereafter but with less priority. The priority of low risks, as noted previously, will depend on the level of effort, exposure, and financial or legal risk also associated with the risk.

# 4.3.3.4 DREAD

Although many different risk models can be used when assessing vulnerabilities during the software development process, the DREAD model used by Microsoft is one the most popular. The acronym DREAD stands for Damage potential, Reproducibility, Exploitability, Affected users, and Discoverability. Answers to questions used to establish a risk rating for each of these elements produces a number from 0 to 10; the higher the number, the more serious is the risk. These numbers are used as a classification scheme for quantifying, comparing, and prioritizing the amount of risk presented by each evaluated threat and calculating the overall risk in numeric form so that threats can be ranked and sorted with any other risks found in the software application.

The DREAD algorithm, shown below, is used to compute a risk value, which is an average of all five categories:

```
Risk_DREAD = (DAMAGE + REPRODUCIBILITY + EXPLOITABILITY + AFFECTED USERS + DISCOVERABILITY)/5^10
```