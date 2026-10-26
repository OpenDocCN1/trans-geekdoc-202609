in the request variable, the data at the index of requests array will also be changed. In the next statement, we are verifying whether the function is invoked by one of the people (addresses) in the approvers mapping using require function. And also we are checking whether that person has already voted to the campaign by querying variable approvals in the Request struct that has the mapping between address and a Boolean type. If the person has already voted, the result will be true which will be false in the require condition and the function will not execute. Else, the approvals variable at the index will be assigned the value of true and approvalCount variable is incremented whenever a vote is accepted (Figure 13.11).

**finalizeRequest ():** The requests which got more than 50% approvals from the contributor can be executed by this function. This function will be executed, only when it is invoked by the manager of the project. The function is marked with the restricted modifier since only the manger should call the function. The function has an argument index of type uint which represents the request number. Again, a storage variable request of type Request struct is created and is assigned with the Request struct data at the index of the array requests, as shown in Figure 13.12. In the require statement, we are verifying whether the approvalCount is greater than 50%. We are also checking whether the request has already been completed to eliminate double spending. Finally, the amount in ether mentioned in the request will be transferred to the recipient address that is given while creating the request. Then the request will

```
```solidity
function approveRequest(uint index) public {
    Request storage request = requests[index];
    require(approvers[msg.sender]);
    require(!request.approvals[msg.sender]);
    request.approvals[msg.sender] = true;
    request.approvalCount++;
}
```
```

**FIGURE 13.11**  approveRequest method.

```
```solidity
function finalizeRequest(uint index) public restricted {
    Request storage request = requests[index];
    require(request.approvalCount>(approversCount/2));
    require(!request.complete);
    request.recipient.transfer(request.value);
    request.complete = true;
}
```
```

**FIGURE 13.12**  finalizeRequest method.