
# Clinical Research Data Protection Requirements

## Required Plans and Statements

- A plan that includes alternate measures to safeguard protected health information
- A plan to destroy patient information when no longer needed (to include any bona fide need to keep the information for research or legal reasons)
- Written statements to prohibit reuse or disclosure of patient information unless permitted by law or the IRB or privacy board
- No research without a waiver
- No research without access to and use of the patient information

---

# Clinical Research Data Handling Steps

For clinical research, several of the alternative steps that are taken to remove patient information from the data or at least limit it to the least amount required are important to know. You may even use these concepts outside of a formal clinical research setting in terms of simply storing and transferring data without unauthorized disclosure.

## De-identification of Patient Information

This consists of removing any individually identifying information from the data set so that you can be reasonably certain no one can identify someone based on the remaining information. There are two ways to do this. The first way is to use a person trained in rendering the information anonymous through algorithms and changes to the standard categories of identifiable data. The second way is to simply remove completely these same categories of identifiable data. The following are sources of data that may be individually identifiable information (from the `NIST 800-122`[^14]):

- Name, such as full name, maiden name, mother’s maiden name, or alias
- Personal identification number, such as `SSN`, passport number, driver’s license number, taxpayer identification number, patient identification number, and financial account or credit card number
- Address information, such as street address or e-mail address
- Asset information, such as `IP` or `MAC` address or other host-specific persistent static identifier that consistently links to a particular person or small, well-defined group of people
- Telephone numbers, including mobile, business, and personal numbers
- Personal characteristics, including photographic image (especially of face or other distinguishing characteristic), X-rays, fingerprints, or other biometric image or template data (for example, retina scan, voice signature, and facial geometry)
- Information identifying personally owned property, such as vehicle registration number or title number and related information
- Information about an individual that is linked or linkable to one of the previous (for example, date of birth, place of birth, race, religion, weight, activities, geographical indicators, employment information, medical information, education information, and financial information)

---

![image](note.jpg) **NOTE** When anonymizing data, a situation can occur where results that are considered outliers are so unique that they actually can be used to identify an individual. An example: take a sample size of a small 12th-grade class at the local high school (150 students). Anonymize any of the 18 individual identifiers as found in `NIST 800-122`, `Sec 2.2`, that are present in the data set. Then you may be left with data elements such as height, weight, eye color, hair color, and immunizations received. Most likely, those individuals with red hair and blue eyes would be unique enough to be identifiable with just those aggregate (albeit anonymized) data elements. These elements would still require confidentiality protection.

## Limited Data Sets

This establishes that some of the patient information can be excluded and what remains is the minimum number and types of identifiers needed, if any. You would usually have a data use agreement in place for using a limited data set that would also determine who has a need to know the information and for what purposes.

## Accounting for Disclosures

Researchers must keep and be able to provide a record of all information disclosed, by whom, and to whom outside of the research organization (for example, another research organization doing similar trials) during the life of the research.

---

![image](tip.jpg) **TIP** Increased disclosure of patient information is authorized for the purposes of clinical research under `HIPAA`. When the information is used for clinical research, controls that would be required under `HIPAA` may be absent. Be aware of the impact of clinical research on any data use scenario.

---

![image](note.jpg) **NOTE** In countries outside of the United States, other types of data may be considered uniquely identifying or protected, such as trade union membership.

# Contract Research Organizations (CRO)

Noteworthy clinical research done by a third party is through a contract research organization (`CRO`). This organization provides support to healthcare organizations conducting specialized types of biopharmaceutical development, preclinical research, clinical trials management, and drug safety. For the most part, these advanced research types are done by leading pharmaceutical, biotechnology, and medical device industries. `CRO`s also support academic medical centers, the government, and international organizations. The ability to partner with `CRO`s allows the development and evaluation of all the various trials of safety and efficacy, but they do not need to have internal staff from the healthcare organization dedicated to the research. For medical devices, the `CRO` gathers clinical data to support a regulatory before-market submission, drive product adoption, support product reimbursement, or monitor after-market product use. They bring expertise and streamlined processes at a much more cost-effective level than what the healthcare organization could if the healthcare organization had to do the same processes itself.

# Health Records Management

Finally, you will encounter health records management organizations that are business partners to physician offices, smaller health clinics, and some other healthcare providers. Because they store and manage patient information as well as valuable business-related data, they introduce information risk that the healthcare provider must still mitigate. You will hear this many times: You cannot outsource responsibility for protecting information.

The health records management organization will typically handle the designated record set for the healthcare provider. This might be because the provider does not have adequate space or expertise. In the case of electronic information, the provider may not be able to invest in the hardware or software (such as a data center) to manage the information. Also, the healthcare organization may not be able to employ adequate privacy and security methods to maintain compliance or properly manage the information from collection to disposition. For any or all of these reasons, it is more cost-effective to outsource to a third party.

The designated records set is more than the legal medical record (discussed previously). It is defined as all the various types of patient medical and billing records used in whole or in part to make decisions on treatment, payment, and operations. The record consists of paper records, film images, electronic data, and any other medium used to store healthcare data. You might think of the difference between a legal health record and the designated record set like this: Direct patient care is recorded in the legal medical record. The designated record set has that information plus all the business information unrelated (but important) to patient care.

[^14]: National Institute of Standards and Technology (NIST) Special Publication 800-122
