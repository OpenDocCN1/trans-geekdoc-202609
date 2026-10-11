
# Acceptance Testing

Acceptance testing tests whether software meets various end-state requirements, from a user or customer, contract or compliance perspective. The ISTQB (International Software Testing Qualifications Board) defines acceptance testing as: “a formal testing with respect to user needs, requirements, and business processes conducted to determine whether or not a system satisfies the acceptance criteria and to enable the user, customers or other authorized entity to determine whether or not to accept the system” [\[34\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0175).

The ISTQB also lists four levels of acceptance testing:

*   **User Acceptance Test**: focuses mainly on the functionality thereby validating the fitness-for-use of the system by the business user. The user acceptance test is performed by the users and application managers.
*   **Operational Acceptance Test**: also known as Production acceptance test validates whether the system meets the requirements for operation. In most of the organization the operational acceptance test is performed by the system administration before the system is released. The operational acceptance test may include testing of backup/restore, disaster recovery, maintenance tasks and periodic check of security vulnerabilities.
*   **Contract Acceptance Testing**: It is performed against the contract’s acceptance criteria for producing custom developed software. Acceptance should be formally defined when the contract is agreed.
*   **Compliance Acceptance Testing**: It is also known as regulation acceptance testing is performed against the regulations which must be adhered to, such as governmental, legal or safety regulations” [\[35\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0180).

## Assessing the Security Impact of Acquired Software

We would like to believe that we can trust vendor claims regarding a product’s capabilities. Vendor claims should be taken as marketing until proven to be true. Don’t rely simply on vendor’s claims even regarding basic capabilities.

An important point is to gather requirements before reviewing products. If requirements are defined after products are reviewed, vendors might be able to convince the organization that it has specific needs that only their product can fill. Don’t let products or marketing determine what the organization “needs” in a product.

### Commercial Off-the-Shelf (COTS) Software

Vendor claims are more readily verifiable for Commercial Off-the-Shelf (COTS) Software. With COTS, perform a bake-off to compare products that already meet requirements. Don’t rely on product roadmaps to become reality. A particularly important security requirement is to look for integration with existing infrastructure and security products. While best-of-breed point products might be the organization’s general preference, recognize that an additional administrative console, with additional user provisioning, will add to the operational costs of the product. Consider the TCO of the product not just the capital expense and annual maintenance costs.

Vendors’ claims are more readily verifiable with COTS software as the product can be evaluated to determine whether it provides the stated capabilities.

Third-party research and analysis organizations provide assessments of various players in a space, which can provide basic (albeit potentially biased) comparisons of products without requiring extensive in-house testing.

Customers of the vendor can often be contacted. Of course, if those contacts are provided by the vendor themselves, then be cautious with accepting claims. A better approach would be to find someone on your own that is using the product and query them concerning Pros/Cons and Likes/Dislikes.

Some questions/concerns for COTS: What happens if the vendor goes out of business? What happens if a critical feature is missing? How easy is it to find in-house or third-party support for the vendor’s products?

### Custom-Developed Third-Party Products

An alternative to COTS is to employ custom-developed applications. These custom-developed third-party applications provide both additional risks and potential benefits beyond COTS. Contractual language and Service Level Agreements (SLAs) are vital when dealing with third-party development shops. Never assume that security will be a consideration in the development of the product unless they are contractually obligated to provide security capabilities.

Basic security requirements should be discussed in advance of signing the contracts and crafting the SLAs to ensure that the vendor expects to be able to deliver those capabilities. Much like COTS, key questions include: What happens if the vendor goes out of business? What happens if a critical feature is missing? How easy is it to find in-house or third-party support for the vendor’s products?

# Artificial Intelligence

Computers compute: they do exactly what they are told. The term “computer” was first used in 1613 to describe a person who added numbers. Artificial Intelligence is the science of programming electronic computers to “think” more intelligently, sometimes mimicking the ability of mammal brains.

## Expert Systems

*Expert systems* consist of two main components. The first is a *knowledge base* that consists of “if/then” statements. These statements contain rules that the expert system uses to make decisions. The second component is an *inference engine* that follows the tree formed by the knowledge base, and fires a rule when there is a match.

Here is a sample “the Internet is down” Expert System, which may be used by a help desk when a user calls to complain that they cannot reach the Internet:

1.  **If your computer is turned on**
    *   Else: turn your computer on
2.  **Then if your monitor is turned on**
    *   Else: turn your monitor on
3.  **Then if your OS is booted and you can open a `cmd.exe` prompt**
    *   Else: repair OS
4.  **Then if you can ping `127.0.0.1`**
    *   Else: check network interface configuration
5.  **Then if you can ping the local gateway**
    *   Else: check local network connection
6.  **Then if you can ping Internet address `192.0.2.187`**
    *   Else: check gateway connectivity
7.  **Then if you can ping `syngress.com`**
    *   Else: check DNS

Forward chaining begins with no premise (“Is the computer turned on” in our previous example), and works forward to determine a solution. Backward chaining begins with a premise (“Maybe DNS is broken”), and works backwards.

The integrity of the knowledge base is critical. The entire knowledge base should form a logical tree, beginning with a trunk (“Is the computer turned on” in our previous example). The knowledge base should then branch out. The inference engine follows the tree, branching or firing as if/then statements are answered.

There should be no circular rules; an example of a circular rule using our previous example: “If your computer is turned on, then if your monitor is turned on, then if your OS is booted and you can open a `cmd.exe` prompt, then if your computer is turned on … .” There should also be no unreferenced rules (branches that do not connect to the knowledge base tree).

## Artificial Neural Networks

Artificial Neural Networks (ANNs) simulate neural networks found in humans and animals. The human brain’s neural network has 100 billion neurons, interconnected by thousands or more synapses each. Each neuron may fire based on synaptic input. This multilayer neural network is capable of making a single decision based on thousands or more inputs.

### Real Neural Networks
