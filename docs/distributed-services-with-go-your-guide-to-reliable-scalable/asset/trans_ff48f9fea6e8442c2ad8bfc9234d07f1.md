
To install Helm, run this command:

| || $ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 *\\*| |

| --- | --- |

| || bash |

Before we write our own Helm chart, let’s take Helm for a spin and install an existing chart. Bitnami^([\[61\]](#f_0083.xhtml#FOOTNOTE-61)) maintains a repository of charts for popular applications. Let’s add a Bitnami repository and install the Nginx chart, which is a web and proxy server:

| || $ helm repo add bitnami https://charts.bitnami.com/bitnami |

| --- | --- |

| || $ helm install my-nginx bitnami/nginx |

We can see the releases by running $ helm list:

| || $ helm list |

| --- | --- |

| || NAME NAMESPACE REVISION UPDATED STATUS... |

| || my-nginx default 1 2020... deployed... |

Let’s request Nginx to confirm that it’s really running:

| || $ POD_NAME=$(kubectl get pod \\ |

| --- | --- |

| || --selector=app.kubernetes.io/name=nginx \\ |

| || --template '{{index .items 0 "metadata" "name" }}') |

| || $ SERVICE_IP=$(kubectl get svc \\ |

| --- | --- |

| || --namespace default my-nginx --template "{{ .spec.clusterIP }}") |

| || $ kubectl exec $POD_NAME curl $SERVICE_IP |

| || % Total % Received % Xferd Average Speed Time Time Time Current |

| || Dload Upload Total Spent Left Speed |

| || 100 612 100 612 0 0 597k 0 --:--:-- --:--:-- --:--:-- 597k |

| || <!DOCTYPE html> |

| || <html> |

| || <head> |

| || <title>Welcome to nginx!</title> |

| || <style> |

| || body { |

| || width: 35em; |

| || margin: 0 auto; |

| || font-family: Tahoma, Verdana, Arial, sans-serif; |

| || } |

| || </style> |

| || </head> |

| || <body> |

| || <h1>Welcome to nginx!</h1> |

| || <p>If you see this page, the nginx web server is successfully installed and |

| || working. Further configuration is required.</p> |

| ||  |

| || <p>For online documentation and support please refer to |

| || <a href="http://nginx.org/">nginx.org</a>.<br/> |

| || Commercial support is available at |

| || <a href="http://nginx.com/">nginx.com</a>.</p> |

| ||  |

| || <p><em>Thank you for using nginx.</em></p> |

| || </body> |

| || </html> |

We could use the same technique for deploying Nginx in a production environment, aside from setting some configuration parameters to fit our use case. Helm made it easy to install and configure an Nginx cluster, and we can manage other services the same way.

Uninstall the Nginx release by running the following:

| || $ helm uninstall my-nginx |

| --- | --- |

| || release "my-nginx" uninstalled |

Now, let’s build our own chart.

### Build Your Own Helm Chart

In this section, we’ll build a Helm chart for our service and use it to install a cluster in our Kind cluster.

Create your Helm chart by running these commands:

| || $ mkdir deploy && cd deploy |

| --- | --- |

| || $ helm create proglog |

Helm created a new chart in a new proglog directory that’s bootstrapped with an example that shows you what a Helm chart looks like—to write your own or to tweak for your own services. The proglog directory contains these directories and files:

| || . |

| --- | --- |

| || └── proglog |

| || ├── charts |

| || ├── Chart.yaml |

| || ├── templates |

| || │   ├── deployment.yaml |

| || │   ├── _helpers.tpl |

| || │   ├── ingress.yaml |

| || │   ├── NOTES.txt |

| || │   ├── serviceaccount.yaml |

| || │   ├── service.yaml |

| || │   └── tests |

| || │   └── test-connection.yaml |

| || └── values.yaml |

| ||  |

| || 4 directories, 9 files |

The Chart.yaml file describes your chart. You can access the data in this file in your templates. The charts directory may contain subcharts, though I’ve never needed subcharts.

The values.yaml contains your chart’s default values. Users can override these values when they install or upgrade your chart (for example, the port your service listens on, your service’s resource requirements, log level, and so on).

The templates directory contains template files that you render with your values to generate valid Kubernetes manifest files. Kubernetes applies the rendered manifest files to install the resources needed for your service. You write your Helm templates using the Go template language.

You can render the templates locally without applying the resources in your Kubernetes cluster by running $ helm template. This is useful when you’re developing your templates or if you want to apply your changes in a two-step plan-then-apply process because you can see the rendered resources that Kubernetes will apply.

To check out the resources Helm would create with the example chart, run this command:

| || $ helm template proglog |

| --- | --- |

You’ll see the following:

| --- | --- |

| || \--- |

| --- | --- |

| || \# Source: proglog/templates/serviceaccount.yaml |

| || apiVersion: v1 |

| || kind: ServiceAccount |

| || metadata: |

| || name: RELEASE-NAME-proglog |

| || labels: |

| ||  |

| || helm.sh/chart: proglog-0.1.0 |

| || app.kubernetes.io/name: proglog |

| || app.kubernetes.io/instance: RELEASE-NAME |

| || app.kubernetes.io/version: "1.16.0" |

| || app.kubernetes.io/managed-by: Helm |

| || \--- |

| || \# Source: proglog/templates/service.yaml |

| || rest |

We don’t need the example templates, so remove them by running this command:

| || $ rm proglog/templates/\*\*/\*.yaml proglog/templates/NOTES.txt |

| --- | --- |

Generally, Helm charts include a template file for each resource type. Our service will require two resource types: a StatefulSet and a Service, so we’ll have a statefulset.yaml file and a service.yaml file. Let’s begin with the StatefulSet.

#### StatefulSets in Kubernetes

You use StatefulSets to manage stateful applications in Kubernetes, like our service that persists a log. You need a StatefulSet for any service that requires one or more of the following:

*   Stable, unique network identifiers—each node in our service requires unique node names as identifiers.

*   Stable, persistent storage—our service expects the data its written to persist across restarts.

*   Ordered, graceful deployment and scaling—our service needs initial node to bootstrap the cluster and join subsequent nodes to its cluster.

*   Ordered, automated rolling updates—we always want our cluster to have a leader, and when we roll the leader we want to give the cluster enough time to elect a new leader before rolling the next node.

And by “stable,” I mean persisted across scheduling changes like restarts and scaling.

If your service isn’t stateful and doesn’t require these features, then you should use a Deployment instead of a StatefulSet. One example is an API service that persists to a relational database, like Postgres. You’d run the API service with a Deployment because it’s stateless, and you’d run Postgres with a StatefulSet.

Create a deploy/proglog/templates/statefulset.yaml file with this code:

[DeployLocally/deploy/proglog/templates/statefulset.yaml](http://media.pragprog.com/titles/tjgo/code/DeployLocally/deploy/proglog/templates/statefulset.yaml) 

| || apiVersion: ​*apps/v1*​ |

| --- | --- |

| || kind: ​*StatefulSet*​ |

| || metadata: |

| || name: {{ include "proglog.fullname" . }} |

| || namespace: {{ .Release.Namespace }} |

| || labels: {{ include "proglog.labels" . | nindent 4 }} |

| || spec: |

| || selector: |

| || matchLabels: {{ include "proglog.selectorLabels" . | nindent 6 }} |

| || serviceName: {{ include "proglog.fullname" . }} |

| || replicas: {{ .Values.replicas }} |

| || template: |

| || metadata: |

| || name: {{ include "proglog.fullname" . }} |

| || labels: {{ include "proglog.labels" . | nindent 8 }} |

| || spec: |

| || ​*\# initContainers...*​ |

| || ​*\# containers...*​ |

