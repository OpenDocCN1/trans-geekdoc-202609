
require periodic testing as to their effectiveness and coverage. Systems change over time, as do threats. Ensuring appropriate mitigation of risk through security controls requires regular reevaluation of their employment and efficacy. This is done through scheduled testing of controls in both singular and all-hazard environments.

## Chapter Review

In this chapter, you became acquainted with the principal security control attributes of confidentiality, integrity, and availability. The chapter also covered usage of specific types of controls for safety purposes and emphasized the need for testing security control structures.

### Questions

To help you prepare further for the CompTIA Security+ exam, and to test your level of preparedness, answer the following questions and then check your answers against the correct answers at the end of the chapter.

1. What is a key advantage of palisade steel fencing?
   - A. It cannot be knocked over.
   - B. Its gates are tightly integrated.
   - C. It is easily constructed.
   - D. It is nearly impossible to climb.

2. How do many types of high-security locks accomplish bump resistance?
   - A. They use higher-strength pins.
   - B. They use patented keyways and control blank distribution.
   - C. They have more tightly controlled mechanical tolerances.
   - D. They don’t; no lock can effectively resist bumping techniques.

3. What is the primary benefit of steganography over encryption?
   - A. Can hold more data securely
   - B. Harder to brute force the key
   - C. Difficulty in detecting it
   - D. Ease of implementation

4. What redundancy scheme could provide instantaneous failover?
   - A. Hot standby
   - B. Cold standby
   - C. Active-active
   - D. Warm-standby

5. A message digest provides integrity by:
   - A. Providing encryption that cannot be unlocked
   - B. Providing a value that can be independently verified to show if the message changed
   - C. Providing message confidentiality so other users cannot see the message
   - D. Applying a signature to the message

6. A lockdown drill dictates:
   - A. All occupants should follow the evacuation route to the designated safe area.
   - B. All occupants are to line up against an interior wall and cover their heads.
   - C. All occupants are to move silently to their designated station.
   - D. All occupants are to stay inside and lock all doors and windows.

7. What does *fail-safe* mean when it is used to describe electronic access control systems?
   - A. All door strikes lock securely to ensure the people are safely inside.
   - B. All door strikes open so people may safely exit.
   - C. All door strikes assume their default locked/unlocked status.
   - D. None of the above.

8. Advances in technology allow a CCTV system to be paired with ________ for tracking individuals.
   - A. facial recognition
   - B. GPS sensors
   - C. cellular triangulation
   - D. computerized body movement analysis

9. Which is an example of fault tolerance in a computer system?
   - A. Dual power supplies
   - B. RAID 5 configured disks
   - C. Multiple network interface controllers
   - D. All of the above

10. A building escape route is usually required by:
    - A. The building's architecture
    - B. Building owners
    - C. Local building codes
    - D. Tenants

For questions 11-15, assume the following scenario: After a break-in at your company, the board decides to transition your role from Director of Information Security to Chief Security Officer. They have asked you to assume all physical security responsibilities and bolster security so that another incident does not happen.

11. To improve physical security against intrusions, what security controls should you immediately review for effectiveness? (Choose all that apply.)
    - A. Fencing
    - B. Control testing
    - C. Non-repudiation
    - D. Lighting
    - E. Escape plans
    - F. Certificates

12. What software controls should you review to make sure no data was compromised during the break-in? (Choose all that apply.)
    - A. Access controls
    - B. CCTV
    - C. Encryption
    - D. Hashing
    - E. Locks
    - F. Fault tolerance

13. Your newly instated control testing policy has identified a problem with escape routes, as shown by confused personnel during a drill. What is the best remediation?
    - A. Clearer signage and a modified escape plan
    - B. Better fencing
    - C. Office redesign to funnel people only to the larger stairs at the south end
    - D. Better emergency lighting

14. Regular evacuation drills have shown that employees are taking too much time getting out of the building because they are bringing their laptops with them. When questioned, they state that critical data only exists on their machines. What is the security control to correct the issue?
    - A. More drills
    - B. Better escape plans
    - C. More data redundancy
    - D. Faster escape routes

15. The company has used the same locks for several years. What are the justifications you would use to request a card-based access control system?
    - A. It provides time-based access controls.
    - B. It makes it easier to remove access to parties that are no longer authorized.
    - C. It is fail-safe in an emergency situation, improving evacuation.
    - D. All of the above.

## Answers

1. D. A steel palisade fence consisting of multiple vertical bars offers excellent climb resistance and is often referred to as an anti-climb fence.

2. B. Many high-security lock manufacturers will patent and tightly control keyways. This will make blanks unavailable to unauthorized persons, and if blanks are found, they will only work on locks in a small physical area.

3. C. Steganography has a key advantage of being difficult to detect, as its encoding can resemble visual noise present in images or video frames.

4. C. An active-active system processes data on both the primary and backup systems, which allows instant failover but has the drawback of needing bidirectional replication—capable software.

5. B. A message digest produced by a hashing function provides a value that can be independently computed to verify that the message has not been changed.

6. D. A lockdown drill is a response to a criminal threat, so the proper action is to stay inside and lock all doors and windows tightly to resist access by the potential threat.

7. B. *Fail-safe* means the doors will unlock to safely allow users to exit the building in the case of a fire or other emergency.

8. A. CCTV can be combined with facial recognition technology with the potential to track individuals as they pass cameras connected to the system.

9. D. All are examples of fault-tolerant designs; one for a power cord or supply failing, one for the loss of a single hard drive, and one for the loss of network connectivity.

10. C. Local building codes will specify the need for building emergency escape routes, almost always with one at either side of the building and clearly marked with lighted signs.

11. A, B, and D. The best answers are fencing, control testing, and lighting. Fencing and lighting are self-explanatory; regularly testing security controls is vital to ensuring their effectiveness.

12. A, C, and D. Access controls, encryption, and hashing are the best answers. Access control permissions should be checked for any change and to determine if they are configured too loosely. Encryption is a primary protection for data confidentiality, and you must ensure that access to the keys was not compromised. Finally, you must check hashes for message integrity to make sure files have not been altered to change the existing data or that critical system files have not been altered to include malware.

13. A. Clearer signage allows employees at a glance to know the escape path from anywhere in the building. A modified escape plan to better control traffic flows and to make sure everyone is familiar with their escape route and plan will better avoid confusion.

14. C. While A, B, and D are all good things to do, this issue is best resolved through data redundancy. Critical data should always be stored in multiple, redundant locations.

15. D. All are correct answers.
