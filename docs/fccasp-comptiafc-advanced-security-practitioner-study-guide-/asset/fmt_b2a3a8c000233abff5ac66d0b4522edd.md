
Some products can have a long useful life. As an example, Windows XP was released in 2005 and was updated and maintained until 2014. Regardless of the product, at some point you will have to consider asset object reuse. Asset object reuse is important because of the remaining information that may reside on a hard disk or any other type of media. Even when data has been sanitized, there may be some remaining information. This is known as data remanence. `Data remanence` is the residual data that remains after data has been erased. Any asset object that may be reused will have some remaining amount of information left on media after it has been erased. Best practice is to wipe the drive with a minimum of seven passes or random ones and zeros. For situations where that is not sufficient, physical destruction of the media may be used.

When such information is deemed too sensitive, the decision may be made not to reuse the objects but to dispose of the assets instead. Asset disposal must be handled in an approved manner. As an example, media that has been used to store sensitive or secret information should be physically destroyed. Before decommissioning or disposing of any systems or data, you must understand any existing legal requirements pertaining to records retention. When archiving information, take into account the method for retrieving the information.

## General Change Management

Change management is a formalized process that is implemented to control modifications made to systems and programs. Change management provides a controlled process for change and is typically handled by a change review board. It also provides stakeholders with an opportunity to voice their concerns before changes are implemented. Before changes are made, the change management request should list specific items about the requested change. Items to record include change number, change type and description, change requestor name and time/date, change source, problem or reason for the change, and dates of the proposed change. A change management program, such as ITIL (`www.itil-officialsite.com`), might include these procedures:

*   Define change management process and practices.
*   Receive change requests.
*   Plan and document the implementation of changes.
*   Implement and monitor the changes. Develop a means of backing out proposed changes if necessary.
*   Evaluate and report on implemented change.
*   Train users on all changes.

## Systems Development Life Cycle

One good source of information on systems development life cycle (SDLC) is NIST 800-64. Although there are many models for SDLC, NIST 800-64, Security Considerations in the Information System Development Life Cycle, breaks the model into five phases. These include the following and are shown in [Figure 10.6](#c10.xhtml#c10-fig-0006), which is from NIST 800-64:

1.  **Phase 1: Initiation** The purpose of the initiation phase is to express the need and purpose of the system. System planning and feasibility studies are performed.
2.  **Phase 2: Development/Acquisition** During this phase, the system is designed, purchased, programmed, developed, or otherwise created. This phase often consists of other defined steps such as the systems development cycle or the acquisition cycle.
3.  **Phase 3: Implementation** After validation and acceptance testing, the system is installed or released.
4.  **Phase 4: Operation/Maintenance** During this phase, the system performs its stated and designed work. The system is almost always modified by the addition of hardware and software and by numerous other events such as patching.
5.  **Phase 5: Disposal** The computer system is disposed of or decommissioned once the transition to a new system is completed.

![FIGURE 10.6 SDLC processes ¶ Source: http://programa.gobiernoenlinea.gov.co/apc-aa-files/5854534aee4eee4102f0bd5ca294791f/nist_sp800_64_1.pdf](images/c10f006.jpg)

[**FIGURE 10.6**](#c10.xhtml#c10-fig-anc-0006) SDLC processes ¶ Source: `http://programa.gobiernoenlinea.gov.co/apc-aa-files/5854534aee4eee4102f0bd5ca294791f/nist_sp800_64_1.pdf`

### Security System Development Life Cycle/Security Development Life Cycle

Although the purpose of NIST 800-64 is to assist in integrating essential information technology security steps into their established SDLC process ([Figure 10.6](#c10.xhtml#c10-fig-0006)), the security systems development life cycle (SSDLC) is designed to identify security requirements early in the development process and incorporate them throughout the process. The idea is to build security into all SDLC activities and have them incorporated into each step of the SDLC. One good example of this process is the security development life cycle.

In 2002, Microsoft developed the security development life cycle (SDL) to increase the security of software and to reduce the impact severity of problems in software and code. The SDL is designed to minimize the security-related design and coding bugs in software. An organization that employs the Microsoft SDL is expected to have a central security entity or team that performs security functions. Some objectives are:

*   The team must create security best practices.
*   The team must consist of security experts and be able to act as a source of security expertise to the organization.
*   The team is responsible for completing a final review of the software before its release.
*   The team must interact with developers and others as needed throughout the development process.

### Security Requirements Traceability Matrix

The security requirements traceability matrix (SRTM) is a grid that allows easy viewing of requirements and documentation supporting specific activities. An example of an SRTM is shown in [Figure 10.7](#c10.xhtml#c10-fig-0007). The SRTM is a spreadsheet document that typically contains items such as the following:

*   Requirement number
*   Description
*   Source
*   Objective
*   Verification

![FIGURE 10.7 Security requirements traceability matrix ¶ Source: https://en.wikipedia.org/wiki/Traceability_matrix](images/c10f007.jpg)

[**FIGURE 10.7**](#c10.xhtml#c10-fig-anc-0007) Security requirements traceability matrix ¶ Source: `https://en.wikipedia.org/wiki/Traceability_matrix`

### Validation and Acceptance Testing

Before products are released, they must typically go through some type of validation and acceptance testing. The idea is to conduct tests to verify that the product or application meets the requirements laid out in the specification documents. Acceptance testing might be black box or white box. Black-box testing works under the assumption that the inner logic is not accessible so you must examine inputs and outputs. White-box testing is used when the code or inner workings of the application are known.

For some entities, validation is also performed. The U.S. federal government specifies this process as certification and accreditation. Federal agencies are required by law to have their IT systems and infrastructures certified and accredited. Certification is the process of validating that implemented systems are configured and operating as expected. If management agrees with the findings of the certification, the report is formally approved. When comparing products, all products must be validated with identical tests. The formal approval of the certification is the accreditation process and authorization to operate in a given environment.

## Adapt Solutions to Address Emerging Threats and Security Trends
