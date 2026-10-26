# 13.6.2  **CONTRACT CAMPAIGN**

Each contract created will represent a project on the front-end. This contract manages all the details and transferring of ether related to a project. This contract will be created by the CampaignFactory contract with two input arguments, minimum contribution value of type int and address of the manager of type address. The contract will store all the ether that is raised through the funding. In this, the participants will contribute some ether greater than the minimum value and become as contributors. The contributors have a right to vote for or against a request made by the manager. If the voting result is greater than 50%, then the request will be accepted and finally executed by the manager.

The Campaign contract has a struct of type Request which is shown in Figure 13.6. It contains the information about the requests that are made by the manager. The values for the variable’s manager of type address and minimumContribution of type uint will be assigned through the constructor. The variable approvers is of type mapping between address and a Boolean value. It indicates whether an address is a contributor or not. The variable requests is an array of type Request struct which stores the list of requests created by the manager.

# 13.6.3  **METHODS IN CAMPAIGN**

**Campaign ():** This is a constructor function that will be invoked while creating the contract, and it has two arguments: minimum and creator. These two will be assigned to the variables minimumContribution and manager, refer Figure 13.7.

**Modifier restricted ():** Some functions like creating a request and finalizing request should only be done by the manager. So, these kinds of functions will have a similar code of checking whether the function is invoked by the manager or not. This verification can be kept in a modifier restricted function as shown in Figure 13.8. The restricted should be attached to the functions which will use this modifier.

![](bbox=[0.133, 0.632, 0.866, 0.884])

**FIGURE 13.6**  Structure of Campaign contract.