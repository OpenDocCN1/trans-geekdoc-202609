
# Blockchain Programming Fundamentals

## Smart Contract Example: Product Management

```solidity
mapping(uint256 => Product) public products;

function addProduct(uint256 id, string memory name, uint256 price) public {
    products[id] = Product(name, price, msg.sender);
}

function transferOwnership(uint256 id, address newOwner) public {
    require(products[id].owner == msg.sender, "Not the owner");
    products[id].owner = newOwner;
}
```

The contract above exemplifies a basic application of blockchain for supply chain management, where products can be registered and transferred between owners.

## Testing and Validation

Before full implementation, it is essential to test the system in a controlled environment. Tests must include:

1. **Functionality**: Verify that smart contracts perform tasks as planned.
2. **Security**: Ensure the system is resistant to attacks and breaches.
3. **Scalability**: Evaluate whether the solution can handle the expected volume of transactions.

## Deployment and Monitoring

After validation, the system can be deployed into production. Continuous monitoring is necessary to identify issues, optimize performance, and ensure regulatory compliance.

## Case Studies

### Logistics: Supply Chain

**Enterprise**: Walmart  
**Aim**: Increase traceability and food safety.  
**Solution**:  
Walmart has implemented blockchain to track food products throughout the supply chain. Using `Hyperledger Fabric`, the company reduced the time needed to track the origin of products from weeks to seconds.

**Benefits**:
1. **Transparency**: All participants in the chain, including farmers and distributors, have access to up-to-date information.
2. **Risk Reduction**: The ability to quickly identify the origin of contaminated food minimizes financial and health impacts.

### Finance: International Payments

**Enterprise**: Santander  
**Aim**: Reduce costs and processing times in international payments.  
**Solution**:  
Santander used `Ripple` to create a cross-border payments platform that allows near-instant transfers between countries.

**Benefits**:
1. **Speed**: Transactions that previously took days are now processed in minutes.
2. **Cost**: Significant reduction in transaction fees.

### Healthcare: Patient Data Management

**Institution**: Estonia  
**Aim**: Protect medical data and improve access for patients and healthcare professionals.  
**Solution**:  
Estonia has integrated blockchain into its healthcare system, allowing patients to control access to their medical data and ensuring records are immutable and secure.

**Benefits**:
1. **Privacy**: Only authorized patients can access their data.
2. **Efficiency**: Facilitates secure information sharing between hospitals and clinics.

### Energy: P2P Energy Trading

**Platform**: Power Ledger  
**Aim**: Allow solar energy consumers to trade surpluses directly with other users.  
**Solution**:  
Power Ledger uses blockchain to manage energy contracts between peers, recording all transactions on a decentralized network.

**Benefits**:
1. **Autonomy**: Users can trade directly without relying on large energy companies.
2. **Sustainability**: Encourages the use of renewable energy sources.

Implementing blockchain in business requires a strategic approach, from problem identification to validation and ongoing monitoring. Real case studies demonstrate that, when well applied, technology can transform industries, improving efficiency, transparency and security.

When planning blockchain projects, it is critical to involve all stakeholders, conduct rigorous testing, and be prepared for adjustments over time. With the right tools and a clear vision, companies can harness the potential of blockchain to gain lasting competitive advantages.

# CHAPTER 21. BASIC BLOCKCHAIN PROGRAMMING

---

Blockchain programming is one of the pillars for building decentralized solutions, and `Solidity` is one of the most popular languages for this purpose. `Solidity` is designed to create smart contracts that run on the `Ethereum Virtual Machine (EVM)` and other supported platforms. In this chapter, the first steps with `Solidity` will be covered, from setting up the environment to creating simple smart contracts.

## Getting Started with Solidity

### Environment Configuration

Before you start programming in `Solidity`, you need to set up a suitable development environment.

**Installing an IDE**:
- **Remix IDE**: A web-based tool that simplifies the development, testing, and deployment of smart contracts. Access Remix at `remix.ethereum.org` and start programming directly in your browser.

**Node.js and Truffle**:
- Install `Node.js` to manage packages and dependencies.
- Use the `Truffle Framework` to develop, test, and deploy contracts.

```bash
npm install -g truffle
```

**Ganache**:  
A local blockchain for testing smart contracts. Install Ganache via the official website or as an npm package.

```bash
npm install -g ganache-cli
```

**Metamask**:  
A browser extension that allows you to interact with Ethereum blockchains. Set up a wallet to test transactions on test networks.

### Understanding the Structure of a Solidity Contract

A smart contract is a collection of code (functions) and data (state) stored at a specific address on the blockchain.

```solidity
pragma solidity ^0.8.0;

contract HelloWorld {
    string public message;

    constructor(string memory initialMessage) {
        message = initialMessage;
    }

    function updateMessage(string memory newMessage) public {
        message = newMessage;
    }
}
```

1. **Pragma**: Defines the version of `Solidity` that the contract uses.
2. **Contract**: The basic unit of a `Solidity` program.
3. **State**: Variables such as `message` are stored on the blockchain.
4. **Functions**: They perform actions and modify the state. In the example, `updateMessage` allows you to change the message.

### Data Types

`Solidity` supports multiple data types, including:

1. **Primitives**:
   - `uint`: Unsigned integers.
   - `bool`: Boolean values (true or false).
   - `address`: Represents an Ethereum address.

2. **Complexes**:
   - `struct`: To create custom types.
   - `mapping`: Data structures that map keys to values.

```solidity
pragma solidity ^0.8.0;

contract DataTypes {
    struct Product {
        string name;
        uint price;
    }

    mapping(uint => Product) public products;

    function addProduct(uint id, string memory name, uint price) public {
        products[id] = Product(name, price);
    }
}
```

In this contract, the `mapping` stores products using IDs as keys.

## Creating Simple Smart Contracts

### Simple Storage Contract

The storage contract demonstrates how to create, update, and retrieve information from the blockchain.

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint public storedData;

    function set(uint data) public {
        storedData = data;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

1. **Function `set`**: Updates the stored value.
2. **Function `get`**: Retrieves the stored value.

### Voting Contract

This contract allows users to vote on different options.

```solidity
pragma solidity ^0.8.0;

contract Voting {
    mapping(string => uint) public votes;

    function vote(string memory candidate) public {
        votes[candidate]++;
    }

    function getVotes(string memory candidate) public view returns (uint) {
        return votes[candidate];
    }
}
```

1. **Function `vote`**: Increases votes for a candidate.
2. **Function `getVotes`**: Returns the number of votes for a specific candidate.

### Payment Contract

This contract demonstrates how to send and receive Ether.

```solidity
pragma solidity ^0.8.0;

contract Payment {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function sendPayment() public payable {
        require(msg.value > 0, "Payment must be greater than 0");
    }

    function withdraw() public {
        require(msg.sender == owner, "Only owner can withdraw");
        payable(owner).transfer(address(this).balance);
    }

    function getBalance() public view returns (uint) {
        return address(this).balance;
    }
}
```

1. **Function `sendPayment`**: Allows users to send Ether to the contract.
