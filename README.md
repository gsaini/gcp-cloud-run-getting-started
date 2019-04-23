# gcp-cloud-run-getting-started
Cloud Run(beta)


## Steps - 
    1. Submit the project build - `gcloud builds submit --tag gcr.io/[PROJECT-ID]/helloworld`
    2. Deploy using this command - `gcloud beta run deploy --image gcr.io/[PROJECT-ID]/helloworld`

** NOTE - where [PROJECT-ID] is your GCP project ID. You can get it by running gcloud config get-value project.
