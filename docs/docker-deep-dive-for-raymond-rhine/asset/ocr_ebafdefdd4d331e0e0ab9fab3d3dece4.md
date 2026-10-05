![](bbox=[0.17, 0.09, 0.75, 0.3])

Figure 13.10

If you add more containers to the **localnet** network, they'll all be able to communicate using names. This is because Docker automatically registers container names with an internal DNS service and allows containers on the same network to find each other by name. The exception to this rule is the built-in **bridge** network that does not support DNS resolution.

Let's test name resolution by creating a new container called **c2** on the same **localnet** network and seeing if it can ping the **c1** container.

Run the following command to create the **c2** container on the **localnet** network. You'll need to type **exit** if you're still logged in to the **c1** container.