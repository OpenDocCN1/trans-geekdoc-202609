Secret splitting can increase security by requiring multiple people to perform a specific function. Requiring too many people can increase issues associated with availability, while requiring too few increases the risk of a small number of people compromising a secret.

![](bbox=[0.168, 0.178, 0.247, 0.224])

> **EXAM TIP** Secret splitting using *m* of *n* authentication schemes can improve security by requiring that multiple people perform critical functions, preventing a single party from compromising a secret.

All key recovery procedures should be highly audited. The audit logs should capture at least what keys were recovered, who was involved in the process, and the time and date. Keys are an integral piece of any encryption cryptosystem and are critical to a PKI environment, so you need to track who does what with them.

# Key Escrow

*Key recovery* and *key escrow* are terms that are often used interchangeably, but they actually describe two different things. You should not use them interchangeably after you have read this section.

Key recovery is a process that allows for lost keys to be recovered. Key escrow is a process of giving keys to a third party so that they can decrypt and read sensitive information when this need arises. Key escrow almost always pertains to handing over encryption keys to the government, or to another higher authority, so that the keys can be used to collect evidence during investigations.

A key pair used in a person’s place of work may be required to be escrowed by the employer for obvious reasons. First, the keys are the property of the enterprise, issued to the employee for use. Second, the firm may have need for them after an employee leaves the firm. Key escrow by businesses can make total sense, provided that the escrowed keys are stored in a manner to prevent their unauthorized use.

![](bbox=[0.168, 0.641, 0.247, 0.688])

> **EXAM TIP** Key escrow, allowing another trusted party to hold a copy of a key, has long been a controversial topic. This essential business process provides continuity should the authorized key-holding party leave an organization without disclosing keys. The security of the escrowed key is a concern, and it needs to be managed at the same security level as the original key.

# Public Certificate Authorities

An individual or company may decide to rely on a CA that is already established and being used by many other individuals and companies—this would be a *public* CA. A company, on the other hand, may decide that it needs its own CA for internal use, which gives the company more control over the certificate registration and generation process and allows it to configure items specifically for its own needs. This second type of CA is referred to as a *private* CA (or *in-house* CA).