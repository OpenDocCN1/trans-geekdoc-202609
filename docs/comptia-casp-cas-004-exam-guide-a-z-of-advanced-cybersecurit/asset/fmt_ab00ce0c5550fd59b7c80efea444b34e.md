
# Software Development Life Cycle

The software development life cycle is a subset of the systems development life cycle, in that any system in development may (but is not required to) contain software development to support the solution. The software development life cycle’s purpose is to create a predictable framework of methods for identifying and ensuring that all criteria for functionality, cost, dependability, and delivery schedule are satisfied in the final product. As shown in [Figure 19.3](#c19.xhtml#fig19_3), this section breaks down the processes in the software development life cycle and explains how each one contributes to the end objective; remember that the processes in the software development life cycle vary depending on the provider, and this is just one example:

![](images/Image31335.jpg)

**Figure 19.3:** Software development lifecycle

## Summary of Steps

The following sections flesh out the software development life cycle steps in detail:

1.  **Step 1**: Plan/initiate project
2.  **Step 2**: Gather requirements
3.  **Step 3**: Design
4.  **Step 4**: Develop
5.  **Step 5**: Test/validate
6.  **Step 6**: Release/maintain
7.  **Step 7**: Certify/accredit
8.  **Step 8**: Change management and configuration management/replacement

## Detailed Phases

### Plan/Initiate Project

The organization chooses to start a new software development project and formally plans it at the plan/initiate step of the software development life cycle. Security experts should be consulted in this phase to assess if the project’s data needs to be protected and whether the application itself needs to be protected independently from the data it processes. Security specialists must examine the predicted outcomes of the new application to evaluate whether the resulting data is more valuable to the company and, as a result, requires more security. Any data processed by the program requires a value provided by its owner, as well as documentation of any unique regulatory or compliance requirements. Healthcare information, for example, is governed by various federal regulations and must be safeguarded. The classification of all input and output data for the application, as well as the required application controls to guarantee that the input and output data are safeguarded, should be documented. The sorts of networks utilized in data transmission must also be determined. All data sources must be scrutinized. Finally, the application’s impact on organizational operations and culture must be evaluated.

### Gather Requirements

The functionality and security needs of the solution are identified during the gather requirements phase of the software development life cycle. These criteria might come from a variety of places, such as a competitive product evaluation for a commercial product or a user survey for an internal solution. These needs might originate from a direct request from a present customer in some situations. Organizations must assess possible weaknesses and threats from a security standpoint. When performing this assessment, keep in mind the software’s intended function as well as the expected environment. Furthermore, the sensitivity of the data that the solution will create or manage must be evaluated. It could be beneficial to assign a privacy effect rating to the data in order to advise efforts to prevent the data from exposure.

### Design

An organization produces a clear description of how the software will fulfil all functional and security goals throughout the design phase of the software development life cycle. It entails mapping the software’s internal behavior and operations to specified criteria in order to detect those that have not been satisfied prior to installation and testing. Throughout this procedure, the application’s state is determined at each stage of its operations. During each operation, the state of the application refers to its functional and security posture. As a result, all conceivable activities must be identified in order to guarantee that the program never becomes vulnerable or behaves in an unpredictable manner. This study also includes determining the attack surface. An attacker’s attack surface defines what resources are available to them. At different stages of the application, the quantity of attack surface offered may fluctuate, but at no point should the attack surface provided contradict the security needs defined in the gather requirements stage.

### Develop

The code or instructions that make the software work are written during the development phase. This phase is focused on ensuring that secure coding techniques are followed to the letter. Insecure coding techniques, such as the lack of `input validation` or `data type checks`, cause many software security concerns. These flaws must be identified via a code review that aims to anticipate all conceivable attack scenarios and their consequences for the code. `Buffer overflows`, `injection`, and other incorrect circumstances can occur if these problems are not identified.

### Test/Validate

Several sorts of testing should take place throughout the test/validate phase, including finding both functional and security concerns. The test data method is an auditing approach that determines the amount of system testing and identifies specific program logic that has not been tested. This approach assesses the behavior of the program in both cases by testing not only the anticipated or legitimate input, but also incorrect and unexpected data. An aggressive attempt at hacking the program should be performed, including `Buffer overflows` and `denial-of-service` (`DoS`) attacks. Some types of testing performed at this time are as follows:

*   **Verification testing**: Determines whether the original design specifications have been met
*   **Validation testing**: Takes a higher-level view and determines whether the original purpose of the software has been achieved

### Release/Maintain

The introduction of the program into the live environment, as well as ongoing monitoring of its operation, are part of the release/maintenance phase. It’s fairly uncommon to discover additional functional and security issues as the program begins to communicate with other network parts at this stage. In many circumstances, vulnerabilities in live settings are uncovered for which there is no current fix or patch. A `zero-day vulnerability` is what it’s called. Supporting development employees should, ideally, find such flaws before those seeking to exploit them do.

### Certify/Accredit

The process of reviewing software for its security efficiency in relation to the customer’s demands is known as certification. Ratings can obviously help, but they aren’t the only factor to consider. Management’s official acknowledgment of the suitability of a system’s overall security is known as accreditation. Provisional accreditation is granted for a certain period of time and it includes a list of needed adjustments to applications, systems, or accreditation paperwork. Full certification means that there are no adjustments that must be made. Once all of the revisions have been performed, assessed, and authorized by the certifying authority, provisional certification becomes full accreditation. While certification and accreditation are connected, they are not thought to be two separate phases in the same process.

### Change and Configuration Management
