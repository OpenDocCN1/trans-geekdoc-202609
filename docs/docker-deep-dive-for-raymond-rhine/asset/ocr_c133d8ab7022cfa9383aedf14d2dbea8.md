```
$ kubectl get pod jump-pod -o yaml
apiVersion: v1
kind: Pod
metadata:
  name: jump-pod
  namespace: default
spec:
  containers:
    - image: nigel-poulton/curl:1.0
      imagePullPolicy: IfNotPresent
      name: jump-ctr
      stdin: true
      tty: true
  volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-2g29h
      readOnly: true
dnsPolicy: ClusterFirst
```

# # THE
KUBNETES
BOOK

Nigel Poulton\ & Pushkar Joglekar