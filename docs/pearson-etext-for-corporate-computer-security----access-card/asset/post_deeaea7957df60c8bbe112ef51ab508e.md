
## Policies

### WHAT ARE POLICIES?
Policies are statements of *what should be done* under specific circumstances. For example, a policy may require a thorough background check for every new employee.

### WHAT, NOT HOW
Note that policies are statements of *what* should be done, not *how* it should be done. Figure 2-18 shows that policies are separate from implementation. Over time, various jobs in the firm will change in sensitivity. What constitutes a thorough background check will change as well. Policies set goals and vision, but they do not inadvertently constrain future implementation changes as conditions change.

> Policies are statements of what should be done, not how it should be done.

### CLARITY
Focusing on what must be done instead of how it should be done does not mean that policies are irrelevant to implementers. On the contrary, when making design decisions, implementers constantly turn to policies for guidance. To continue our example, if there are two alternatives for doing background checks, implementers ask themselves if the alternatives fit the intent of the policy. By focusing on policy goals and sometimes on rationales for these goals, policies bring clarity about what should be done. Implementers do not get lost in the details.

![](img/073342643701cc54eb7875c41ab92ef2_99_0.png)

**Figure 2-18** Policies (Study Figure)

## Test Your Understanding

- 28.
- a. What are policies?
- b. Distinguish between policies and implementation.
- c. Why should policies not specify implementation in detail?

## Categories of Security Policies

### CORPORATE SECURITY POLICY
A company needs several categories of security policies. At the top is the **corporate security policy**. As we have just noted, its goal is to emphasize a firm’s commitment to strong security. It is brief and to the point.

> A corporate security policy’s goal is to emphasize a firm’s commitment to strong security.

### MAJOR POLICIES
Under the umbrella of the brief corporate security policy, companies need specific policies about major concerns. These major policies are much more detailed than the corporate security policy.

- ***E-mail policies*** exist in almost all firms. E-mail policies specify what the IT staff should do about security-related e-mail concerns. They should also specify what e-mail users should do or not do with e-mail.
- ***Hiring and termination policies*** are needed because hiring and termination are dangerous periods of time. The company needs strong policies for background checks and other matters at the time of hiring as well as termination policies for different types of terminations (voluntary, layoffs, termination for cause, etc.).
- ***Personally identifiable information (PII)*** policies specify protections for sensitive personal information. These policies must specify access controls, encryption, and other matters that can reduce the threat of revealing sensitive personal information.

**Figure 2-19** Policies, Implementation, and Oversight

![](img/073342643701cc54eb7875c41ab92ef2_100_0.png)

## ACCEPTABLE USE POLICY

Users cannot be expected to read many detailed policies. For users, corporations create an acceptable use policy (AUP) that summarizes key points of special importance to users. For example, an AUP will note that (1) the resources are company property and are not for personal use, (2) there should be no presumed right to privacy in e-mail or other uses, and (3) specific types of behavior will not be tolerated.

Typically, companies require users to read and sign the AUP. This provides legal protection so that the user cannot say that he or she never knew company policies. Of equal importance, signing creates a sense of ceremony that is memorable. Required signing also emphasizes the company’s commitment to IT security.

## POLICIES FOR SPECIFIC COUNTERMEASURES OR RESOURCES

At the most detailed level, major policies are not sufficiently detailed for specific countermeasures, such as a single firewall, or for specific resources, such as the payroll database. Countermeasure and resource policies provide this additional specificity. Again, the goal is to separate security goals from implementation.

## Test Your Understanding

- 29. a. Distinguish between the corporate security policy and major security policies.
- b. Distinguish between major security policies and the acceptable use policies.
- c. What are the purposes of requiring users to sign the AUP?
- d. Why are policies for individual countermeasures and resources needed?

## Policy-Writing Teams

Broad policies cannot be developed by the IT security staff in isolation. For each policy, the company should form a team to create the policy. While IT security will be an important member of the team, it may not even chair the team.

For example, consider a policy for terminating employees for committing fraud or theft of intellectual property. Obviously, human resources and the legal department should be on the team—so should any department that would have to implement the policy.

Team-written policies carry much more weight with employees than policies written exclusively by IT security. They are also more likely to be effective because they are not based on IT security’s limited viewpoint.

## Test Your Understanding

- 30. Why is it important to have corporate teams write policies?

## Implementation Guidance

Although policies are and should be broad statements of vision and goals, Figure 2-20 shows that companies often develop implementation guidance for policies. Implementation guidance limits the discretion of implementers, in order to simplify implementation decisions, to avoid bad choices in interpreting policies, and to give consistency in implementation.

> Implementation guidance limits the discretion of implementers in order to simplify implementation decisions and to avoid bad choices in interpreting policies.

Implementation guidance is distinct from the policy it addresses. Policies state security goals and vision to drive implementation. Implementation guidance constrains implementation choice to an appropriate degree. Policies rarely change. Implementation guidance, while generally stable, is likely to change faster than policies.

We now have three levels in Figure 2-20. Policies govern the what, and implementation determines the how. In between, implementation guidance forms an optional intermediate step of control.

## NO GUIDANCE

If a company can trust implementers to act wisely, then it should not create implementation guidance. Providing no implementation guidance frees implementers to develop what they see as the best possible policy implementation. It also avoids a lock-down feeling. This often is a good trade-off with the increased risk that not providing implementation guidance creates.

- **Implementation Guidance**
- Limits the discretion of implementers, in order to simplify implementation decisions and to avoid bad choices in interpreting policies
- **No Guidance**
- Implementer is only guided by the policy itself
- **Standards versus Guidelines**
- Standards are mandatory directives
- Guidelines are not mandatory but must be considered
- **Types of Implementation Guidance**
- Can be either standards or guidelines
- Procedures: detailed specification of how something should be done
- Segregation of duties: two people are required to complete sensitive tasks
- In movie theaters, one sells tickets and the other takes tickets
- No individual can do damage, although
- Request/authorization control
- Limit the number of people who may make requests on sensitive matters
- Allow even fewer to be able to authorize requests
- Authorizer must never be the requester
- Mandatory vacations to uncover schemes that require constant maintenance
- Job rotation to uncover schemes that require constant maintenance
- Processes: less detailed specifications of what actions should be taken
- Necessary in managerial and professional business function
- Baselines: checklists of what should be done
- Best practices: most appropriate actions in other companies
- Recommended practices: normative guidance
- Accountability
- Owner of resource is accountable
- Implementing the policy can be delegated to a trustee, but accountability cannot be delegated
- Codes of ethics

Figure 2-20 Implementation Guidance (Study Figure)
