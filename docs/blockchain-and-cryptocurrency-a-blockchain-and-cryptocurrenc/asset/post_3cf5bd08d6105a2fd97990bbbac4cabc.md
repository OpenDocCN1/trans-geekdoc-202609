
blockchain technology. BitTicket provides users with one wallet QR code that holds all their BitTickets securely, no matter which ticketing provider they bought them from. They simply present it along with proof of ID to gain entry. Due to the security of BitTicket identity, ticket transfer to friends and family can be done easily and with assurance. BitTickets are immutable, transferable, and verifiable.

BitTicket guarantees the following:

- Your purchased ticket is genuine
- Inherent protection against industrial-scale ticket touts and ticket purchasing bots
- Transfer your tickets securely and with ease between friends & family
- Provides one wallet for all your tickets – no more individual tickets

## 18.2.2 GUTS

GUTS uses blockchain technology to create a transparent ticketing ecosystem where inflated secondary market prices and ticket fraud are eliminated. Their motto is simple, transparent, and secure.

GUTS brings numerous benefits for different stakeholders:

- Artist and Managers
  - A fair chance for all the fans to attend the show
  - Expand the fan base with exact data
  - Direct communication with your fans - send them a message right before the show starts
- The Venue, Festival and Theatre Operators
  - No ticket fraud: fewer complaints and a stronger image
  - You know exactly who is present at any time (and is not)
- Automatic refund procedure at the time of cancelation or resale
- Identification via mobile phones means shorter queues
- Ticket Providers
  - Complete control of the tickets in both the primary and secondary market
  - Easy to integrate with existing ticketing solutions

## 18.2.3 LAVA

LAVA is a blockchain-based ticketing system that guarantees fair and secure smart tickets for music lovers. The system prevents ticket touting and fraud ruining festivals for music lovers.

The LAVA ecosystem has the following features:

- 100% Safe
  - Using latest blockchain technology to eliminate ticket fraud
- Smart Tickets
  - Smart tickets to stop the exploitation of festival tickets using a unique digital footprint
- Lava Wallet - Eliminate printing completely by generating the ticket digitally and sending the digital ticket to the Lava wallet directly
- No booking fees

## 18.2.4 PouchNATION

PouchNATION is an event management software system that uses the blockchain technology to good effect. PouchNATION is the first platform to implement blockchain and new digital currency across all verticals in event management. Its components comprise guest registration, cashless payment, access control, activity tracking, social engagement and detailed analytics reporting.

This innovative platform could overcome issues that the ticket industry is currently facing with managing events, attendance tracking apps, eliminating duplicate tickets, and validating registration at the door.

They have executed over 100 events including cashless events in Indonesia, Philippines, Vietnam, Malaysia, Thailand, and Myanmar.

## 18.2.5 EventChain

EventChain is a global Smart Ticketing blockchain project that will allow events worldwide to sell SmartTickets through a peer-to-peer network, solving the issues of the centralized event ticketing industry.

It implements the EventChain token network for event management to ensure faster transactions, indisputable ticket vouchers, transparency from event hosts and fully flexible and programmable SmartTickets. With the use of the EVC token, smart contract code, and the Ethereum blockchain, EventChain’s transaction network brings increased accountability, transparency, and security to event ticketing.

To fix excessive ticket fees, EventChain is distributing EVC tokens, a digital ERC20 token created for buying, selling, and programming SmartTickets on the Ethereum distributed network. EventChain claims that their transaction fees are much lower, and the transaction confirmation speed is near seconds.

## 18.2.6 Event Management and Ticketing Platform - A Conceptual Model

After examining the above use cases, I propose a conceptual model that utilizes a similar concept to develop a blockchain-based event management and ticketing platform. Below is a simple conceptual model of the Event Management and Ticketing Platform:

## Blockchain Event Management Platform

![](img/f2f9952d33ef3f083419e55bc6a6e2e1_185_0.png)

Figure 18.1

The platform allows an event organizer to create an event and broadcast it to the website as well as a mobile wallet. The event should comprise details such as event title, date, time, venue, and a ticketing ordering button. The participant can then order tickets by paying Token X. Once the organizer receives Token X, the e-ticket shall be automatically delivered.

## 18.3 Developing a DApp - KittyChain Shop

In this project, we shall use Ganache (https://truffleframework.com/ganache) to develop the KittyChain DApp.

Ganache is a personal blockchain for Ethereum development you can use to deploy contracts, develop applications, and run tests. It is available as both a desktop application as well as a command-line tool (formerly known as TestRPC).

Truffle is a world-class development environment, testing framework and asset pipeline for blockchains using the Ethereum Virtual Machine (EVM), aiming to make life as a developer easier.

The KittyChain DApp is an adoption tracking system for a pet shop.

### 18.3.1 Steps to Build the Dapp

1. Setting up the development environment
2. Creating a Truffle project using a Truffle Box
3. Writing the smart contract
4. Compiling and migrating the smart contract
5. Testing the smart contract
6. Creating a user interface to interact with the smart contract
7. Interacting with the DApp in a browser

### Step 1 Setting Up the Development Environment

Install the following:

1. Node.js
2. Git
3. Truffle

Having installed the aforementioned packages, we shall proceed to install Ganache. You can download Ganache by navigating to http://truffleframework.com/ganache and clicking the "Download" button.

### Step 2 Creating the Project Using a Truffle Box

Truffle initializes in the current directory, so first create a directory in your development folder of choice and then move inside it.

```
mkdir pet-shop-tutorial
cd pet-shop-tutorial
```

Now you have created a Truffle Box called pet-shop, which includes the basic project structure as well as code for the user interface.

Next, use the truffle unbox command to unpack this Truffle Box.
```
truffle unbox pet-shop
```

# The Output

![](img/f2f9952d33ef3f083419e55bc6a6e2e1_188_0.png)

Figure 18.2
