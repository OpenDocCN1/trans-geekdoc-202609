
# Risk Control and Analysis

## Risk Control

Risk control is a set of actions to reduce or manage risk.

---

We usually want to weigh the pros and cons of different actions we can take to address each risk. To that end, we can quantify the effects of a risk by multiplying the risk impact by the risk probability, yielding the **risk exposure**. For example, if the likelihood of virus attack is 0.3 and the cost to clean up the affected files is $10,000, then the risk exposure is $3,000. So we can use a calculation like this one to decide that a virus checker is worth an investment of $100, since it will prevent a much larger expected potential loss. Clearly, risk probabilities can change over time, so a risk analysis activity should track them and plan for events accordingly.

Risk is inevitable in life: Crossing the street is risky but that does not keep us from doing it. We can identify, limit, avoid, or transfer risk but we can seldom eliminate it. In general, we have three strategies for dealing with risk:

- **avoid** the risk by changing requirements for security or other system characteristics
- **transfer** the risk by allocating the risk to other systems, people, organizations, or assets; or by buying insurance to cover any financial loss should the risk become a reality
- **assume** the risk by accepting it, controlling it with available resources and preparing to deal with the loss if it occurs

Thus, costs are associated not only with the risk's potential impact but also with reducing it. **Risk leverage** is the difference in risk exposure divided by the cost of reducing the risk. In other words, risk leverage is

![Image](graphics/669equ01.jpg)

The leverage measures value for money spent: A risk reduction of $100 for a cost of $10, a 10:1 reduction, is quite a favorable result. If the leverage value of a proposed action is not high enough, then we look for alternative but less costly actions or more effective reduction techniques.

---

**Risk leverage is the amount of benefit per unit spent.**

---

**Risk analysis** is the process of examining a system and its operational context to determine possible exposures and the potential harm they can cause. Thus, the first step in a risk analysis is to identify and list all exposures in the computing system of interest. Then, for each exposure, we identify possible controls and their costs. The last step is a cost–benefit analysis: Does it cost less to implement a control or to accept the expected cost of the loss? In the remainder of this section, we describe risk analysis, present examples of risk analysis methods, and discuss some of the drawbacks to performing risk analysis.

## The Nature of Risk

In our everyday lives, we take risks. In riding a bike, eating oysters, or playing the lottery, we take the chance that our actions may result in some negative result—such as being injured, getting sick, or losing money. Consciously or unconsciously, we weigh the benefits of taking the action with the possible losses that might result. Just because a certain act carries a risk, we do not necessarily avoid it; we may look both ways before crossing the street, but we do cross it. In building and using computing systems, we must take a more organized and careful approach to assessing our risks. Many of the systems we build and use can have a dramatic impact on life and health if they fail. For this reason, risk analysis is an essential part of security planning.

We cannot guarantee that our systems will be risk free; that is why our security plans must address actions needed should an unexpected risk become a problem. And some risks are simply part of doing business; for example, as we have seen, we must plan for disaster recovery, even though we take many steps to avoid disasters in the first place.

When we acknowledge that a significant problem cannot be prevented, we can use controls to reduce the seriousness of a threat. For example, you can back up files on your computer as a defense against the possible failure of a file storage device. But as our computing systems become more complex and more distributed, complete risk analysis becomes more difficult and time consuming—and more essential.

## Steps of a Risk Analysis

Risk analysis is performed in many different contexts; for example, environmental and health risks are analyzed for activities such as building dams, disposing of nuclear waste, or changing a manufacturing process. Risk analysis for security is adapted from more general management practices, placing special emphasis on the kinds of problems likely to arise from security issues. By following well-defined steps, we can analyze the security risks in a computing system.

The basic steps of risk analysis are listed below.

1.  Identify assets.
2.  Determine vulnerabilities.
3.  Estimate likelihood of exploitation.
4.  Compute expected annual loss.
5.  Survey applicable controls and their costs.
6.  Project annual savings of control.

[Sidebar 10-4](#ch10.html#ch10sb04) illustrates how different organizations take slightly different approaches, but the basic activities are still the same. These steps are described in detail in the following sections.

---

### Sidebar 10-4: Alternative Steps in Risk Analysis

There are many formal approaches to performing risk analysis. For example, the U.S. Army used its Operations Security (OPSEC) guidelines during the Vietnam War [[SEC99]](#bib01.html#bib_557). The guidelines involve five steps:

1.  Identify the critical information to be protected.
2.  Analyze the threats.
3.  Analyze the vulnerabilities.
4.  Assess the risks.
5.  Apply countermeasures.

Similarly, the U.S. Air Force uses an Operational Risk Management procedure to support its decision making [[AIR00]](#bib01.html#bib_06). The steps are:

1.  Identify hazards.
2.  Assess hazards.
3.  Make risk decisions.
4.  Implement controls.
5.  Supervise.

As you can see, the steps are similar, but their details are always tailored to the particular situation at hand. For this reason, you may use someone else's risk analysis process as a framework, but then change it to match your own situation.

---

### Step 1: Identify Assets

Before we can identify vulnerabilities, we must first decide what we need to protect. Thus, the first step of a risk analysis is to identify the assets of the computing system. The assets can be considered in categories, as listed below. The first three categories are the assets identified in [Chapter 1](#ch01.html#ch01) and described throughout this book. The remaining items are not strictly a part of a computing system but are important to its proper functioning.

- **hardware:** processors, boards, keyboards, monitors, terminals, microcomputers, workstations, tape drives, printers, disks, disk drives, cables, connections, communications controllers, and communications media
- **software:** source programs, object programs, purchased programs, in-house programs, utility programs, operating systems, systems programs (such as compilers), and maintenance diagnostic programs
- **data:** data used during execution, stored data on various media, printed data, archival data, update logs, and audit records
- **people:** skilled staff needed to run the computing system or specific programs, as well as support personnel such as guards
- **documentation:** on programs, hardware, systems, administrative procedures, and the entire system
- **supplies:** paper, forms, laser cartridges, recordable media, and printer ink, as well as power, heating and cooling, and necessary buildings or shelter
- **reputation:** company image
- **availability:** ability to do business, ability to resume business rapidly and efficiently after an incident
