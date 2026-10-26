
Security, we tend to refer to the measurements we make of things and situations as metrics. We tend to give lip service to metrics, saying that they are important (like auditors), but in reality we often try to avoid them whenever we can. We often measure the wrong things. One of the common examples of incorrect metrics is that almost all of us will measure the number of computer viruses that a scanning platform catches. However, the more important number is how many viruses it fails to detect.

One of the most helpful books in the metrics literature is *PRAGMATIC Security Metrics: Applying Metametrics to Information Security* (Auerbach Publications, 2016) by W. Krag Brotby and Gary Hinson. As you might suspect, PRAGMATIC is an acronym, reminding us that metrics should be Predictive, Relevant, Actionable, Genuine, Meaningful, Accurate, Timely, Independent, and Cheap. Dr. Hinson has done further work on the idea since then, and I’m very much looking forward to his next book on the topic.

The COVID-19 pandemic has lessons to teach us about metrics. In British Columbia we get regular briefings and updates from Dr. Bonnie Henry, the provincial health officer, and Adrian Dix, the Minister of Health. Every statement starts with a standard list of metrics, and it is instructive to see what the different metrics actually mean.

The first numbers in every statement are the number of new cases, and the total number since the pandemic began. While these metrics are obviously important, right away we realize that possibly more important than the number of new cases is the trend: is the number of new cases more or less than it was the previous day, and for some days past. In other words, is the situation getting better, or worse? A recent addition to the statements is the number of the new cases that have not been confirmed through actual testing, but are, in the words of the reports, ‘epi-linked’: people who have been found by contact tracing and epidemiological study to be infected.

One metric missing at this point is the total number of tests that have been done over the past day. In relation to the number of new cases, this gives us the positivity rate for the testing. The positivity rate can indicate a number of interesting things, although you have to be careful to examine the situation carefully. If the positivity rate is too low, it may mean that you are testing the wrong people, and wasting resources. However, if the positivity rate gets too high (and this generally means more than single digits) it likely means that you are not doing enough testing, and you are probably missing people who, especially with a disease like COVID-19 which may generate a number of those infected who don’t show any symptoms, can be out spreading the virus.

The total number of cases is interesting, but equally important, and the next set of numbers to be given, are the numbers of cases who have completely recovered, and, therefore, the total number of people who are still considered to be ‘active’ cases. This is followed by the number of people in hospital, and in intensive care, which provides some idea of the drain and demands placed on the healthcare system.

The next set of numbers in the briefings is the total numbers in the five different health regions in the province. This reminds us, in security, that total numbers are all very well, but that some parts of our enterprise may be unequally affected, and we need to keep track of that fact. In addition, recently a separate category has been added to this part of the statement, noting people who are not from the province, and arrived here already sick.

The next metric is the number of deaths that have occurred in the past day. At this point, I should note that my use of the word ‘case’, when I am actually talking about people, is simply following standard medical reporting terminology, and not an attempt to hide the fact that each case is a sick person, and each death is a death. As Adrian Dix points out, every day when the report has a death to list, every single death means loss and grief for friends, relatives, and society as a whole. It is important to remember the actual implications of the metrics.

The final metric that is included with every statement reports outbreaks in care facilities, hospitals, and in the general community. In security terms, this is alerting us to vulnerabilities in the system. Seniors, in care facilities, are not necessarily more likely to contract the disease, but the impact and outcome tends to be much more serious. Outbreaks in hospitals are, of course, obviously serious in a number of ways, including the greater risk to the health professionals who work there, and on whom we all rely. Outbreaks in the community are important, relevant to the situation: a large house party means somebody (actually a large number of somebodies) has been foolish and we can’t do anything about that, but contact tracing needs to follow up on it. An outbreak in a workplace may mean that health and safety needs to look at the environment and processes in order to issue orders to ensure that businesses and industries may continue to operate safely.

## COST/BENEFIT

Many jurisdictions around the world have experienced some form or duration of lockdown. This ‘bent the curve’. Isolation from basically everyone reduced the rate of transmission. It reduced the spread of the disease, reduced the suffering, and reduced the number of deaths.

It has come at a cost. Quite a number of costs, actually. Some jobs can be done from home, but many cannot. That has meant unemployment for some, financial losses for others, and an enormous cost to the economy as a whole.

The financial hits ripple throughout our society. Wage earners lose their jobs. They can’t pay rent. Landlords lose out on income. Cities don’t get paid property taxes. That means budgets have to be slashed and more workers lose their jobs. Landlords also have trouble paying mortgages. Banks face a minor dip in their profits and so get bailed out by the government. (Wait, what?)

Some of the costs are not financial. Isolation prevents the spread of the disease and so keeps us medically or physically safe. But social isolation also has psychological effects and those in turn can have a bearing on physical and medical conditions. (Finance can also come back into play here. Poverty has a known and well-documented negative effect on physical health.)

As I’m writing this, many jurisdictions have ‘reopened’ and more are considering it. Most of the reopening is being done on a gradual or graduated basis. There is much discussion of a ‘new normal’ (which undoubtedly differs from place to place).

The disease has come at a cost. The preventive measures have come at a cost but have benefited in terms of lives not lost as well as grief unsuffered. The reopening will have benefits but it will also have its own costs in terms of suffering and lives. The reopening will allow business to resume, businesses to make money, and the economy to improve.

In security, we are constantly assessing costs and benefits in very tangled and interconnected situations. Security, as a profession, exists to support businesses, so one might assume that we would universally be on the side of reopening. But ‘life safety’ is always the highest priority in any security calculation if you want to pass the CISSP (Certified Information Systems Security Professional) exam.

There are no easy answers.

## Access Control

### 3

### DEFENCE IN DEPTH/LAYERED DEFENCE

One of the foundational principles of access control is the realization that you might fail. In fact, any kind of protection you set up will fail at some point. No defence is ever going to withstand every attack mounted against it.

Therefore, we rely on a fundamental concept referred to as defence in depth (or layered defence). The idea is that whatever safeguard you put in place has some kind of weakness. You want to set up a compensating control that will, well, compensate for that weakness. You want to know what and where your existing weaknesses are and choose other countermeasures and controls that will provide support and backstops for those holes. Since your compensating controls may (will) themselves have vulnerabilities, we build multiple layers of defence.

So it is with the response to COVID-19. A first step, when a new disease appears, is to try to prevent geographic spread. So we may try to restrict travel. We will ask travellers if they have been to an affected area, and we may not admit them if they have been. But there are holes in that policy. People may lie about where they have been or may have been infected in a different location because of transmissions we may not know about. So we do not rely on screening questions only. We do symptom checks. We may check temperatures since we know that fever is one of the symptoms of COVID-19.

But temperature and symptom checks have weaknesses as well since people can be asymptomatic or presymptomatic. So relying solely on travel restrictions is foolish. We must prepare another layer of defence since we have to assume that the travel limitations will not be a perfect protection. We have to prepare our medical system to be alert for signs of the disease in our population, and we need diagnostic tests to confirm whether people in our area have become infected. But the tests, as we know, have error rates and detect only once people
