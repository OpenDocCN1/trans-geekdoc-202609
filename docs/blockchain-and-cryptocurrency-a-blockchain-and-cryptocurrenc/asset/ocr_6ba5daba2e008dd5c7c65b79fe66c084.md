```
require(pet >= 0 && petId <= 15);
adopters[petId] = msg.sender;
return petId;
}
// Retrieving the adopters
function getAdopters() public view returns
(address[16]) {
  return adopters;
}
```

# Step 4 Compiling and Migrating the Smart Contract

Now that we have the smart contract, we shall proceed to compile and migrate it.

Truffle has a built-in developer console known as Truffle Develop, which generates a development blockchain that we can use to test and deploy the smart contract. It can also run Truffle commands directly from the console.

We need to compile the smart contract written in Solidity bytecode for the Ethereum Virtual Machine (EVM) to execute. Think of it as translating our human-readable Solidity into something the EVM understands. In a terminal, make sure you are in the root of the directory that contains the DApp and type:

truffle compile

The Output

Compiling ./contracts/Migrations.sol...

Compiling ./contracts/Adoption.sol...

Writing artifacts to ./build/contracts