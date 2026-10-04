# 314

# Blockchain for Cybersecurity and Privacy

![](bbox=[0.121, 0.091, 0.878, 0.513])

FIGURE 13.5 Second of RETPAY.

```
function getIDsAmount(bytes32 _IDs) public view returns (uint) {
  for(int j = 0; j < PaidIds.length; j++) {
    if(PaidIds[j] == _ID) {
      return (j);
    }
}
```

FIGURE 13.6 Prevention of double payment in the smart contract.

The DApp requires the client's approval to complete the partial completion and retention process for the reporting period. The client will have to log in MetaMask by using his wallet specified in the smart contract to start the approval process. The client logs in with the specified wallet, the DApp will display the requested payment amount of the client's screen, as shown in Figure 13.5. If the client does not approve the list of completed works and the retention payment amount, the DApp will notify the contractor and will provide the reasons for rejection of the client. If the client approves the completed works, the agreed retention amount for the report period is transferred from the client's wallet to contractor's wallet, and the list of completed activities that are stored in the blockchain is updated, with their completion dates. The client, however, has to make sure that there are sufficient funds in her wallet before approval. Once the contractor receives the amount in Ethereum, he can convert it into any fiat currency in the local cryptocurrency exchanges.