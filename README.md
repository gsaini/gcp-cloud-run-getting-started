# gcp-cloud-run-getting-started

Cloud Run(beta)

## Build and Deploy

## Quickstart: Deploy to Cloud Run on GKE

================================================================================

### Steps -

    1. Submit the project build - `gcloud builds submit --tag gcr.io/[PROJECT-ID]/helloworld`
    2. Deploy using this command - `gcloud beta run deploy --image gcr.io/[PROJECT-ID]/helloworld`

** NOTE - where [PROJECT-ID] is your GCP project ID. You can get it by running gcloud config get-value project.

### => Deploy on GKE -

### Step - Creating a GKE cluster with Cloud Run enabled

`gcloud beta container clusters create cloud-run-gke-cluster \
  --addons=HorizontalPodAutoscaling,HttpLoadBalancing,Istio,CloudRun \
  --machine-type=n1-standard-1 \
  --cluster-version=1.12 --zone=us-central1-a \
  --enable-stackdriver-kubernetes --enable-ip-alias \
  --scopes cloud-platform`

`gcloud config set run/cluster cloud-run-gke-cluster`

`gcloud config set run/cluster_location us-central1-a`

### Step - Deploying a sample container

To deploy a container to the cluster you just created:

Click Create service to display the Create service form. In the form,

Use the sample `gcr.io/[PROJECT-ID]/helloworld` as the container image.

In the Location dropdown, select the cluster you just created in the previous steps.

Click Create and wait for the deployment to finish. This creates the service and deploys it to Cloud Run on GKE.

### Step - Accessing your deployed service

After you deploy your service, you can use CURL to send a request and verify the service is working, using the cluster's IP address:

Go to the Google Kubernetes Engine page in the GCP Console:

Click Services in the left navigation panel to display a list of services.

Scroll down to the istio-ingressgateway service and copy the IP address shown next to the load balancer. Ignore the other values under that IP address.

Invoke CURL:

`curl -v -H "Host: helloworld.default.example.com" http://[YOUR-IP]`

Replace [YOUR-IP] with the IP address you obtained in the previous step, and if you used a service name other than helloworld you'll need to replace that as well.

=================================================================================
