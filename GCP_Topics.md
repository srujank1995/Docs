# Google Cloud Platform (GCP) Commands and Key Topics for a GCP Engineer/Consultant

This repository contains essential commands and concepts for working with Google Cloud Platform (GCP) as a GCP Engineer/Consultant. 
The guide includes common operations for Compute Engine, Kubernetes Engine (GKE), Networking, IAM, and more. 
This documentation can be useful for both beginners and experienced engineers.

---

## Table of Contents
1. [Compute Engine](#1-compute-engine)
2. [Kubernetes Engine (GKE)](#2-kubernetes-engine-gke)
3. [Networking](#3-networking)
4. [Cloud Storage](#4-cloud-storage)
5. [Identity and Access Management (IAM)](#5-identity-and-access-management-iam)
6. [Cloud Functions](#6-cloud-functions)
7. [Cloud SQL](#7-cloud-sql)
8. [Monitoring and Logging](#8-monitoring-and-logging)
9. [Cloud Build](#9-cloud-build)
10. [BigQuery](#10-bigquery)
11. [Infrastructure as Code (IaC)](#11-infrastructure-as-code-iac)
12. [Miscellaneous](#12-miscellaneous)
13. [Key Concepts](#key-concepts)

---

## 1. Compute Engine

### Create a VM Instance
```bash
gcloud compute instances create INSTANCE_NAME --zone ZONE --machine-type MACHINE_TYPE --image-family IMAGE_FAMILY --image-project IMAGE_PROJECT
```

### Start/Stop a VM Instance
```bash
gcloud compute instances start INSTANCE_NAME --zone ZONE
gcloud compute instances stop INSTANCE_NAME --zone ZONE
```

### SSH into a VM Instance
```bash
gcloud compute ssh INSTANCE_NAME --zone ZONE
```

---

## 2. Kubernetes Engine (GKE)

### Create a GKE Cluster
```bash
gcloud container clusters create CLUSTER_NAME --zone ZONE --num-nodes NUM_NODES
```

### Get Credentials for a Cluster
```bash
gcloud container clusters get-credentials CLUSTER_NAME --zone ZONE
```

### Deploy an Application
```bash
kubectl apply -f DEPLOYMENT_FILE.yaml
```

### Scaling a Deployment
```bash
kubectl scale deployment DEPLOYMENT_NAME --replicas=NUM_REPLICAS
```

---

## 3. Networking

### Create a VPC
```bash
gcloud compute networks create VPC_NAME --subnet-mode custom
```

### Create a Subnet
```bash
gcloud compute networks subnets create SUBNET_NAME --network=VPC_NAME --range=IP_RANGE --region=REGION
```

### Set Up Firewall Rules
```bash
gcloud compute firewall-rules create RULE_NAME --network=VPC_NAME --allow tcp:PORT --source-ranges IP_RANGE
```

---

## 4. Cloud Storage

### Create a Bucket
```bash
gsutil mb -l LOCATION gs://BUCKET_NAME/
```

### Upload/Download Files
```bash
gsutil cp FILE_PATH gs://BUCKET_NAME/
gsutil cp gs://BUCKET_NAME/FILE_PATH LOCAL_PATH
```

---

## 5. Identity and Access Management (IAM)

### Add IAM Policy Binding
```bash
gcloud projects add-iam-policy-binding PROJECT_ID --member=USER_OR_SERVICE_ACCOUNT --role=ROLE
```

### List IAM Roles
```bash
gcloud iam roles list
```

---

## 6. Cloud Functions

### Deploy a Cloud Function
```bash
gcloud functions deploy FUNCTION_NAME --runtime RUNTIME --trigger-http --entry-point ENTRY_POINT
```

### Invoke a Cloud Function
```bash
gcloud functions call FUNCTION_NAME --data '{"key":"value"}'
```

---

## 7. Cloud SQL

### Create a Cloud SQL Instance
```bash
gcloud sql instances create INSTANCE_NAME --database-version=VERSION --tier=MACHINE_TYPE --region=REGION
```

### Connect to a Cloud SQL Instance
```bash
gcloud sql connect INSTANCE_NAME --user=USERNAME
```

---

## 8. Monitoring and Logging

### View Logs in Cloud Logging
```bash
gcloud logging read "resource.type=gce_instance AND logName=projects/PROJECT_ID/logs/LOG_NAME" --limit=10
```

### Create an Alert Policy
```bash
gcloud monitoring policies create --config-from-file=ALERT_POLICY.yaml
```

---

## 9. Cloud Build

### Trigger a Build
```bash
gcloud builds submit --tag gcr.io/PROJECT_ID/IMAGE_NAME
```

---

## 10. BigQuery

### Run a Query
```bash
bq query --use_legacy_sql=false 'SELECT * FROM dataset.table LIMIT 10'
```

---

## 11. Infrastructure as Code (IaC)

### Deploy Resources Using Deployment Manager
```bash
gcloud deployment-manager deployments create DEPLOYMENT_NAME --config CONFIG_FILE.yaml
```

---

## 12. Miscellaneous

### Set Default Project and Zone
```bash
gcloud config set project PROJECT_ID
gcloud config set compute/zone ZONE
```

### List All Resources
```bash
gcloud compute instances list
gcloud container clusters list
gcloud sql instances list
```

---

## Key Concepts

- **IAM Roles and Permissions**: Understand how IAM roles work, how to assign them, and best practices for securing resources.
- **VPC Networking, Subnets, and Firewall Rules**: Know how to set up and manage VPCs, subnets, and firewall rules to control traffic.
- **Resource Monitoring and Logging**: Be familiar with Cloud Monitoring and Logging for tracking resource performance and identifying issues.
- **Service Accounts and OAuth 2.0**: Understand how to use service accounts for authentication and authorization in GCP.
- **Cost Management and Billing Alerts**: Learn how to monitor costs, set up billing alerts, and optimize spending.
- **Best Practices for Security and Compliance**: Follow best practices for data protection, encryption, and access control in GCP.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
