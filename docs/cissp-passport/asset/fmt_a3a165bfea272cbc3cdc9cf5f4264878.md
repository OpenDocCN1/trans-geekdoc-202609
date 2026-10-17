
### [3](#ch01.xhtml#ch1ques13-3)

As part of governance requirements, a specific population of users within your company must be trained on risk management techniques and compliance on an annual basis. Which of the following groups is the likely target of this training?

**A.** Senior executives

**B.** Routine users

**C.** Help desk technicians

**D.** Junior security analysts

### [4](#ch01.xhtml#ch1ques13-4)

For a company-sponsored, off-duty employee development program, you would like to teach a more advanced class on security theory. Which of the following would be the appropriate level of this type of instruction?

**A.** Awareness

**B.** Training

**C.** Education

**D.** Briefing

#### 1.13 ANSWERS

### [1](#ch01.xhtml#r_ch1ques13-1)

A Since all the users are co-located, distance learning may not be necessary. The topic is very basic so the training only needs to increase awareness about the new social engineering technique.

### [2](#ch01.xhtml#r_ch1ques13-2)

C Because some of the students you must train are geographically separated and work different shifts, classroom training likely won’t be feasible. You should consider distance-learning, in combination with self-study, because of the advanced nature of the topic, and include interactive exercises to help the students learn how to configure the firewall better. Self-study alone likely would not enable them to learn these skills sufficiently.

### [3](#ch01.xhtml#r_ch1ques13-3)

A Since the topics involve risk management and compliance, senior executives likely benefit most from this type of training, as it is more suited to their roles and responsibilities.

### [4](#ch01.xhtml#r_ch1ques13-4)

C Advanced topics, such as security theory, would most likely be considered at the level of education within the training program, as this level of learning represents more advanced topics that cover the “why” of the subject.

![Images](f0085-01.jpg)

## Asset Security

Domain Objectives

• 2.1 Identify and classify information and assets.

• 2.2 Establish information and asset handling requirements.

• 2.3 Provision resources securely.

• 2.4 Manage data lifecycle.

• 2.5 Ensure appropriate asset retention (e.g., End-of-Life (EOL), End-of-Support (EOS)).

• 2.6 Determine data security controls and compliance requirements.

Domain 2, “Asset Security,” discusses one of the most important things an organization can do in terms of securing itself: protect its assets. As you will see in this domain, anything of value can be categorized as an asset, and an organization must manage its assets effectively by identifying them and protecting them according to how valuable they are to the organization. In this domain we will discuss how to identify and classify assets and how to handle their secure use, storage, and transportation. We will also talk about how to provision assets and resources securely to authorized users. As an asset, information has a defined life cycle, and we will examine this life cycle so that you understand everything involved with protecting critical or sensitive information. We’ll also discuss asset retention, as well as the security controls and compliance requirements that are levied as a part of protecting assets.

### Identify and classify information and assets

As discussed in Objective 1.10, an asset is anything of value to the organization. Examples of assets include servers, workstations, network equipment, facilities, information, and people. The value placed on an asset depends on how much the organization needs it to fulfill its mission. How an organization places value on an asset depends on many factors, including the original cost of the asset, its depreciation, its replacement value, what it costs to repair, how much revenue it generates for the organization, and how critical it is to the organization’s mission.

We also discussed tangible and intangible assets in Objective 1.10. As a refresher, a tangible asset is an item that we can easily see, touch, interact with, and measure; examples are systems, equipment, facilities, people, and even information. Intangible assets are those that are difficult to interact with, and sometimes difficult to place a value on, but are still critical to the organization’s success. Examples of intangible assets include customer satisfaction, reputation, and standing in the marketplace. In this objective we will discuss how assets and data are identified and classified.

![Images](exam.jpg)

**EXAM TIP** Although the CISSP objectives sometimes seem to refer to *information* and *assets* as two different things, understand that in reality information is in fact one of the organization’s critical assets, and in this book, we will treat it as such and make reference to it as an asset, along with facilities, equipment, systems, and even people.

#### Asset Classification

Classifying assets means to categorize them in some fashion so that they can be managed better. Assets are generally classified in terms of criticality and sensitivity, both of which are discussed in the next section. Assets aren’t purchased or acquired for their own sake; they exist to support the mission of the organization, including its business processes. The organization can classify an asset according to criticality by determining how critical the business process is that the asset supports.

A common way to perform this criticality assessment is to perform a business impact analysis (BIA), introduced in Objective 1.8. A BIA is also one of the first steps in business continuity planning, which we will discuss later in the book. A BIA inventories the organization’s business processes to determine those that are critical to its mission and cannot be allowed to stop functioning. It also identifies the information assets used to support those processes, which are considered the critical assets in an organization.

**Cross-Reference**

We will discuss business impact analysis, as part of business continuity planning, in Objective 7.13.

Even before determining criticality, however, the organization must discover all of its assets. Normally, tangible IT/cyberassets fall into one of two categories: hardware or software. Hardware is normally inventoried and identified by its serial number, model number, cost, and other data elements. Software is tracked by its license number or key, business or process it supports, and specific function.

#### Data Classification

Like other assets, data can be classified in terms of criticality, or in terms of sensitivity. While often used interchangeably, data criticality and data sensitivity mean two different things. Data criticality refers to how important the data is to a mission or business process, and data sensitivity relates to the level of confidentiality of the data. For example, privacy data in an organization may not be critical to its core business processes and only collected incidentally to the human resource process of managing employees. However, it is still very sensitive data that cannot be allowed to be accessed by unauthorized entities.

**Cross-Reference**

Remember from Objective 1.2 that data and information are terms that are often used interchangeably, but they have distinct definitions. Data are raw, singular pieces of fact or knowledge that have no immediate context or meaning. An example would be an IP address, or domain name, or even an audit log entry. Information is data organized into context and given meaning. When given context, many pieces of data become information. Giving data context means correlating data—determining how it relates to other pieces of data and a particular event or circumstance. While individual pieces of data should be considered critical or sensitive, we normally classify information rather than pieces of data.
