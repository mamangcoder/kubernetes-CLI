# kubernetes-CLI
## Task 1. Create a GKE cluster
gcloud container clusters create <dynamic cluster name> \--release-channel regular \--cluster-version 1.27.8 \--num-nodes 3 \--min-nodes 2 \--max-nodes 6 \--enable-autoscaling

## Task 2. Enable Managed Prometheus on the GKE cluster 
- autentication for clusters <br>
$ gcloud container clusters get-credentials clustersName --zone asia-southeast-a
- check namespace <br>
  $ kubectl get ns
1.  Enable Managed Prometheus <br>
$ ​​gcloud container clusters update hello-world-q2a7 --zone=us-central1-b --enable-managed-prometheus  <br>

2.  Create namespace <br>
   $ kubectl create namespace nsName
3. Download a sample Prometheus app
4. Update the <todo sections (lines 35-38) with the following configuration.
- containers.image: nilebox/prometheus-example-app:latest
- containers.name: prometheus-test
- ports.name: metrics
5. Deploy the application onto the  namespace on your GKE cluster.
  - CLI Deploy app on namespace: <br>
  $ kubectl apply -n nsName -f prometheus-app.yaml
- Check resource on namespace <br>
  $ kubctl get all -n nsName
  <br>
6. Download the pod-monitoring.yaml file
7. Update the <todo> sections (lines 18-24) with the following configuration
- metadata.name: prometheus-test
- labels.app.kubernetes.io/name: prometheus-test
- matchLabels.app: prometheus-test
- endpoints.interval: interval period
8. Apply the pod monitoring resource onto the namespace name namespace on your GKE cluster.
   - CLI Deploy app on namespace: <br>
  $ kubectl apply -n nsName -f  pod-monitoring.yaml
- check resource podmonitoring
  $ kubectl get podmonitoring -n nsName 

## Task 3. Deploy an application onto the GKE cluster
1. Download the demo deployment manifest files:
   - nothing to config
3. Create a deployment onto the namespace name
   - change dir
     $ cd hello-app
  - apply deployment
    $ kubectl apply -n nsName -f  manifests/helloweb-deployment.yaml
5. Verify you have created the deployment on console

## Task 4. Create a logs-based metric and alerting policy
-
- resource.type="k8s_pod"  severity=WARNING

## Task 5. Update and re-deploy your app
- update helloweb-deployment.yaml
- delete deployment errors sebelumnya
- apply/deploy ulang <br>
  $ kubectl apply -n nsName -f  manifests/helloweb-deployment.yaml

<br>

## Task 6. Containerize your code and deploy it onto the cluster
1. In the hello-app directory, update the main.go file to use Version: 2.0.0 on line 49.
2. Use the hello-app/Dockerfile to create a Docker image with the v2 tag.
