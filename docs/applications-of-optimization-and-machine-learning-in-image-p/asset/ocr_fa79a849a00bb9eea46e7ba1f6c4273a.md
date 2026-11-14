+   * Notifying Scheme: In this scheme, if an authenticated scheme finds that the key is not new, it is understood that the node is malicious, and false data is sent to the node, the loss of which carries no weight and effect.

# Pseudo Code of the VKS Model

```
Key ()
{
X=RNG();
Function(f) = Aproxy(value of node, adjustment, X)
{
int apr, node;
node=X+ node
New key(nk) = node + adjustment;
check the authenticated list
if nk is already in the authenticated list, then
adjustment++;
calculate the nk value;
return nk;
}
}
New_generate_key(nk, sizeof network)
{
y=nk % size of network;
return 1;
}
Enter the value of l in authenticated list of nodes
l is now a distinguished value for all the nodes
participating.
At each device:
verification(1)
{
 Verify the l with the log table given by
 admin.
 If l matches the value in the authenticated
 nodes list, then
 Send a success message to the participating
 node
 else {
 Discard the device
 }
}
```