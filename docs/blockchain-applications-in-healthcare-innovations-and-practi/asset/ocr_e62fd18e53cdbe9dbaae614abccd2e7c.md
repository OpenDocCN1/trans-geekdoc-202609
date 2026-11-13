```
function getDataPatient() public returns (bytes32) {
    GetNamePatient(msg.sender);
    return patient.name;
}
function setPatientName(bytes32 name) public onlyOwner {
    patient.name = name;
}
}
```

# Smart Contract 2.3.

Part 1 discusses an enum that is used to declare the patient’s gender and Part 2 describes a struct. Part 3 discusses the state variables. A state variable merely indicates the status of a certain record for a patient. In the above program, there are three state variables: a unique id, the patient for the data and the state variable for the smart contract address that owns this patient history. Function RecordPatientData() gives the address of the generating smart contract to dataOwner, a state variable that can be used later. Part 4 describes events and Part 5 describes modifiers. Part 6 discusses functions, which are nothing more than constructors, getters and setters.

# 2.6. Challenges related to smart contracts

Smart contracts, being an emerging technology in its early stages, are now afflicted by a plethora of difficulties and roadblocks. This section will describe the issues with smart contracts, as well as current research developments.

# 2.6.1. Contract vulnerabilities

+   - Transaction-ordering dependence (TOD): each block includes numerous activities, and the miner determines the order that they are completed in. TOD occurs when a large number of reliant actions execute the same contract in a manner