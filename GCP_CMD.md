
# GCP Commands for a 2-Year Experienced Consultant

## 1. Compute Engine
### Create a VM Instance
```bash
gcloud compute instances create INSTANCE_NAME --zone ZONE --machine-type MACHINE_TYPE --image-family IMAGE_FAMILY --image-project IMAGE_PROJECT
```
- `INSTANCE_NAME`: Name of your virtual machine.
- `ZONE`: The zone where the VM will be created, e.g., `us-central1-a`.
- `MACHINE_TYPE`: The machine type, e.g., `n1-standard-1`.
- `IMAGE_FAMILY`: The image family, e.g., `debian-11`.
- `IMAGE_PROJECT`: The project that hosts the image, e.g., `debian-cloud`.

### Start/Stop an Instance
```bash
gcloud compute instances start INSTANCE_NAME --zone ZONE
gcloud compute instances stop INSTANCE_NAME --zone ZONE
```
- These commands start or stop a specified VM instance.

### SSH into an Instance
```bash
gcloud compute ssh INSTANCE_NAME --zone ZONE
```
- SSH into the VM instance for remote management.

## 2. Kubernetes Engine (GKE)
### Create a GKE Cluster
```bash
gcloud container clusters create CLUSTER_NAME --zone ZONE --num-nodes NUM_NODES
```
- `CLUSTER_NAME`: Name of your Kubernetes cluster.
- `NUM_NODES`: Number of nodes in the cluster.

### Get Credentials for a Cluster
```bash
gcloud container clusters get-credentials CLUSTER_NAME --zone ZONE
```
- Fetches credentials to interact with the Kubernetes cluster using `kubectl`.

### Deploy an Application
```bash
kubectl apply -f DEPLOYMENT_FILE.yaml
```
- Deploys an application using the provided Kubernetes YAML file.

### Scaling a Deployment
```bash
kubectl scale deployment DEPLOYMENT_NAME --replicas=NUM_REPLICAS
```
- Scales the number of replicas for a Kubernetes deployment.

## 3. Networking
### Create a VPC
```bash
gcloud compute networks create VPC_NAME --subnet-mode custom
```
- Creates a VPC network with a custom subnet mode.

### Create a Subnet
```bash
gcloud compute networks subnets create SUBNET_NAME --network=VPC_NAME --range=IP_RANGE --region=REGION
```
- Creates a subnet within a specified VPC.
- `IP_RANGE`: CIDR range for the subnet, e.g., `10.0.0.0/24`.

### Set Up Firewall Rules
```bash
gcloud compute firewall-rules create RULE_NAME --network=VPC_NAME --allow tcp:PORT --source-ranges IP_RANGE
```
- Creates a firewall rule to allow specific traffic.

## 4. Cloud Storage
### Create a Bucket
```bash
gsutil mb -l LOCATION gs://BUCKET_NAME/
```
- Creates a new Cloud Storage bucket.

### Upload/Download Files
```bash
gsutil cp FILE_PATH gs://BUCKET_NAME/
gsutil cp gs://BUCKET_NAME/FILE_PATH LOCAL_PATH
```
- Uploads or downloads files from the storage bucket.

### List Buckets and Objects
```bash
gsutil ls
gsutil ls gs://BUCKET_NAME/
```
- Lists all buckets or objects within a specific bucket.

## 5. IAM (Identity and Access Management)
### Add IAM Policy Binding
```bash
gcloud projects add-iam-policy-binding PROJECT_ID --member=USER_OR_SERVICE_ACCOUNT --role=ROLE
```
- Grants a role to a user or service account on a project.

### List IAM Roles
```bash
gcloud iam roles list
```
- Lists all IAM roles available in the project.

## 6. Cloud Functions
### Deploy a Cloud Function
```bash
gcloud functions deploy FUNCTION_NAME --runtime RUNTIME --trigger-http --entry-point ENTRY_POINT
```
- Deploys a new cloud function triggered by HTTP.

### Invoke a Cloud Function
```bash
gcloud functions call FUNCTION_NAME --data '{"key":"value"}'
```
- Invokes a cloud function with specified data.

## 7. Cloud SQL
### Create a Cloud SQL Instance
```bash
gcloud sql instances create INSTANCE_NAME --database-version=VERSION --tier=MACHINE_TYPE --region=REGION
```
- Creates a Cloud SQL instance.

### Connect to a Cloud SQL Instance
```bash
gcloud sql connect INSTANCE_NAME --user=USERNAME
```
- Connects to the Cloud SQL instance via the command line.

## 8. Monitoring and Logging
### View Logs in Cloud Logging
```bash
gcloud logging read "resource.type=gce_instance AND logName=projects/PROJECT_ID/logs/LOG_NAME" --limit=10
```
- Reads logs from a specific resource type.

### Create an Alert Policy
```bash
gcloud monitoring policies create --config-from-file=ALERT_POLICY.yaml
```
- Creates an alert policy using a configuration file.

## 9. Cloud Build
### Trigger a Build
```bash
gcloud builds submit --tag gcr.io/PROJECT_ID/IMAGE_NAME
```
- Submits a build to Cloud Build and tags it with a Docker image.

## 10. BigQuery
### Run a Query
```bash
bq query --use_legacy_sql=false 'SELECT * FROM dataset.table LIMIT 10'
```
- Runs a SQL query on a BigQuery dataset.

## 11. Infrastructure as Code (IaC)
### Deploy Resources Using Deployment Manager
```bash
gcloud deployment-manager deployments create DEPLOYMENT_NAME --config CONFIG_FILE.yaml
```
- Deploys infrastructure resources using Google Cloud Deployment Manager.

## 12. Miscellaneous
### Set Default Project and Zone
```bash
gcloud config set project PROJECT_ID
gcloud config set compute/zone ZONE
```
- Sets default project and compute zone for the `gcloud` CLI.

### List All Resources
```bash
gcloud compute instances list
gcloud container clusters list
gcloud sql instances list
```
- Lists all instances, clusters, or SQL instances in the current project.

# Key Concepts to Understand
- **IAM Roles and Permissions**
- **VPC Networking, Subnets, and Firewall Rules**
- **Resource Monitoring and Logging**
- **Service Accounts and OAuth 2.0**
- **Cost Management and Billing Alerts**
- **Best Practices for Security and Compliance**
