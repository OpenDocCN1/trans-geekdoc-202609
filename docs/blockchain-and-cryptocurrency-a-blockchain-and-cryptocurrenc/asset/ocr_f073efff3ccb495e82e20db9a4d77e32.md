simple conceptual model of the Event Management and Ticketing Platform:

# Blockchain Event Management Platform

![](bbox=[0.148, 0.29, 0.803, 0.4])

Figure 18.1

The platform allows an event organizer to create an event and broadcast it to the website as well as a mobile wallet. The event should comprise details such as event title, date, time, venue, and a ticketing ordering button. The participant can then order tickets by paying Token X. Once the organizer receives Token X, the e-ticket shall be automatically delivered to the participant's mobile wallet. To enter the event venue, the organizer just needs to scan the e-ticket of the participant.

To build the platform, we need to build a smart contract layer on top of the blockchain network to automate the buying and selling of event tickets. We shall use Solidity to write the contracts. There shall be at least three smart contracts - the ERC220 token contract (to generate Token X), the event contract, and the ERC721 ticket contract. The event contract will need to link to the ticket contract as it needs to use the data in the ticket contract. The keyword to access the data in another contract is import. For example, we can create an event contract event.sol that imports the ticket contract ticket.sol, using the syntax as:

```
Pragma Solidity ^0.5.0
```