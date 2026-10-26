```
```javascript
};
const walletPath = path.join(__dirname, 'wallet',
  orgName);
const wallet = new FileSystemWallet(walletPath);
console.log(`Wallet path: ${ walletPath }`);
const userExists = await wallet.exists(userName);
if (userExists) {
  console.logimport(
    `An identity for the user ${ userName } already exists
    in the wallet`
  );
  return 'User already registered';
}
const adminExists = await wallet.exists(appAdmin);
if (!adminExists) {
  console.log(
    `An identity for the admin user ${ appAdmin } does not
    exist in the wallet`
  );
  console.log('Registering the admin');
  regAdmin(orgName);
}
const gateway = new Gateway();
await gateway.connect(ccp, {
  wallet,
  identity: appAdmin,
  discovery: gatewayDiscovery
});
const ca = gateway.getClient().getCertificateAuthority();
const adminIdentity = gateway.getCurrentIdentity();
const secret = await ca.register(
{
  affiliation: 'org1',
  enrollmentID: userName,
  role: 'client'
},
  adminIdentity
);

console.log('secret:');
console.log(secret);
const enrollment = await ca.enroll({
  enrollmentID: userName,
  enrollmentSecret: secret
});
const userIdentity = X509WalletMixin.createIdentity(
  orgMSPID,
  enrollment.certificate,
  enrollment.key.toBytes()
);
```
```