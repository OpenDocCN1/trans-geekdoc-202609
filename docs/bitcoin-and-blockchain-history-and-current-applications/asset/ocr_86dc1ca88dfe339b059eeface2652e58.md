```
```javascript
20.   const wallet = new FileSystemWallet(walletPath);
21.   console.log(`Wallet path: ${ walletPath }`);
22.
23.   const userExists = await wallet.exists(userName);
24.   if (!userExists) {
25.     console.log(
26.       'An identity for the user ' + userName + ' does not
       exist in the wallet'
27.     );
28.     console.log('Run the registerUser.js application before
       retrying');
29.     throw new Error('An identity for the user ' + userName + '
       does not exist in the wallet');
30.   }
31.
32.   gateway = new Gateway();
33.   await gateway.connect(ccp, {
34.     wallet,
35.     identity: userName,
36.     discovery: { enabled: false }
37.   });
38.   const network = await gateway.getNetwork(channelName);
39.
40.   const contract = network.getContract(contractName);
41.   args = JSON.stringify(args);
42.   let result = await contract.evaluateTransaction(function
     Name, args);
43.
44.   console.log(
45.     `Transaction has been evaluated, result is: ${ result.
     toString() }`
46.   );
47.   result = result.toString();
48.   return result;
49. } catch (error) {
50.   console.error(`Failed to evaluate transaction: ${ error
     }`);
51.   return error;
52. } finally {
53.   if (gateway) {
54.     await gateway.disconnect();
55.   }
56. }
57. }
58.
59. module.exports = query;
```
```

We can query the blockchain ledger using the above function. This function uses several API’s from Fabric SDK and gives the result of the query