# Storing Sensitive Information for IoT Access Control

First, we will check the code used to register a user:

```
function register(string memory name,string memory passwd_biometric) public {
  users.push(User(nextid,name,passwd_biometric));
nextid++;
}
```

Here in this function, we are using username and biometric details as passwords. And we are pushing them and generating a serial number. It will create a user. Here, we are storing the hashes at which location data will be stored in the form of blobs. We could use IPFS or Inter-Planetary File System, which is used for storing and sharing data in a distributed file system. We could store the file in a peer-to-peer server and return a hash where the image has been stored and then we will store the hash for future use or be in D-apps. Then we have defined a function where the admin can read the details of the user by providing its serial number:

```
function getUserByById(uint id) view public returns(uint, string memory,string memory) {
  uint i = checkUserxists(id);
  return(users[i].id,users[i].name,users[i].passwd_biometric);
```

Here we are passing ID as parameter to get all the details about the user. Then we are going to define a function to update user details like biometric.

```
function updateById(uint id, string memory name,string memory passwd_biometric) {
  uint i = checkUserxists(id);
  users[i].name = name;
  users[i].passwd_biometric = passwd_biometric;
}
```

After passing, the field which needs to be updated are passed and then it will be updated accordingly. Then there is a function for deleting or removing users.

```
function destroyById(uint id) public {
  uint i = checkUserxists(id);
  delete users[i];
}
```

This administrator panel of our proposed architecture is summarized in Figure 12.5. The final workflow diagram of the proposed architecture is depicted in Figure 12.6. The code is tested on the Ethereum virtual environment and gives the desired result. Though yet to be tested on an actual environment comprising the data makes more secure than other techniques. The smart contract is kept as simple as possible and tested using dummy data, which can differ from biometric data. Proper algorithms can be used to convert the biometric data to desired store values. The motivation of the model came from the fact that data in blockchain cannot be tampered by malicious users. There are very few endpoints that are