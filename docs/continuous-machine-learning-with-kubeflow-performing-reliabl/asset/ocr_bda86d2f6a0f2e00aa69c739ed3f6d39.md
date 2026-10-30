class will be fulfilled by creating persistent volumes backed by directories under the /volumes directory on the Filestore instance's managed storage.

```
```bash
helm install stable/nfs-client-provisioner --name nfs-cp --set nfs.server=${FSADDR} --set nfs.path=/volumes
watch kubectl get po -l app=nfs-client-provisioner
```
```

![](bbox=[0.12, 0.35, 0.88, 0.44])

Figure 1.45: FileStore

# Step Make a Persistent Volume Claim.

Create a Kubernetes Persistent Volume Claim specification. This is a .yaml file that allows a Kubernetes pod to access the storage resources of a Persistent Volume. The specification looks similar to the following example:

![](bbox=[0.12, 0.75, 0.88, 0.93])