# 1.6.6 Connect to cluster and Deploy Grafana

# #### Setup knative-monitoring

```
```bash
##RUN THE COMMAND IN GOOGLE SHELL
# Connect to cluster
gcloud container clusters get-credentials <$ClusterName> --zone
<$ZONE> --project <$PROJECTID>
#create namespace
kubectl create namespace knative-monitoring
#setup monitoring components
kubectl apply --filename
https://github.com/knative/serving/releases/download/v0.17.2/monitoring-metrics-prometheus.yaml
```
```