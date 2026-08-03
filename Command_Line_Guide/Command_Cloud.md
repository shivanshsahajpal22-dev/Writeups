# Most used Cloud CLI commands
(AWS CLI, Azure CLI, and gcloud — the ones you'll actually reach for day to day)

**Authentication & Setup**
```
1. Configure credentials (AWS) -> aws configure
2. Login (Azure) -> az login
3. Login (GCP) -> gcloud auth login
4. Check current identity (AWS) -> aws sts get-caller-identity
5. Check current account (Azure) -> az account show
6. Check current account (GCP) -> gcloud auth list
7. List configured profiles (AWS) -> aws configure list-profiles
8. Set active project (GCP) -> gcloud config set project <project-id>
9. Set active subscription (Azure) -> az account set --subscription <name>
```

**Identity & Access Management**
```
1. List IAM users (AWS) -> aws iam list-users
2. List IAM roles (AWS) -> aws iam list-roles
3. List policies attached to a user (AWS) -> aws iam list-attached-user-policies --user-name <name>
4. List role assignments (Azure) -> az role assignment list
5. Show effective permissions (Azure) -> az role assignment list --assignee <user>
6. List IAM policies (GCP) -> gcloud projects get-iam-policy <project-id>
7. Add IAM policy binding (GCP) -> gcloud projects add-iam-policy-binding <project-id> --member=user:x --role=roles/y
8. Check what an identity can do (AWS) -> aws iam simulate-principal-policy --policy-source-arn <arn> --action-names <action>
```

**Compute instances**
```
1. List EC2 instances (AWS) -> aws ec2 describe-instances
2. Start an EC2 instance (AWS) -> aws ec2 start-instances --instance-ids <id>
3. Stop an EC2 instance (AWS) -> aws ec2 stop-instances --instance-ids <id>
4. Terminate an EC2 instance (AWS) -> aws ec2 terminate-instances --instance-ids <id>
5. List VMs (Azure) -> az vm list
6. Start a VM (Azure) -> az vm start --name <name> --resource-group <rg>
7. Stop a VM (Azure) -> az vm stop --name <name> --resource-group <rg>
8. List instances (GCP) -> gcloud compute instances list
9. Start an instance (GCP) -> gcloud compute instances start <name>
10. Stop an instance (GCP) -> gcloud compute instances stop <name>
```

**Storage**
```
1. List S3 buckets (AWS) -> aws s3 ls
2. List objects in a bucket (AWS) -> aws s3 ls s3://bucket-name
3. Copy a file to S3 (AWS) -> aws s3 cp file s3://bucket-name/
4. Sync a folder to S3 (AWS) -> aws s3 sync ./dir s3://bucket-name/
5. Check bucket public access (AWS) -> aws s3api get-bucket-acl --bucket bucket-name
6. List storage accounts (Azure) -> az storage account list
7. List blobs in a container (Azure) -> az storage blob list --container-name <name>
8. List buckets (GCP) -> gcloud storage buckets list
9. Copy a file to a bucket (GCP) -> gcloud storage cp file gs://bucket-name/
```

**Networking**
```
1. List VPCs (AWS) -> aws ec2 describe-vpcs
2. List security groups (AWS) -> aws ec2 describe-security-groups
3. List security group rules (AWS) -> aws ec2 describe-security-groups --group-ids <id>
4. List VNets (Azure) -> az network vnet list
5. List network security groups (Azure) -> az network nsg list
6. List firewall rules (Azure) -> az network nsg rule list --nsg-name <name> --resource-group <rg>
7. List VPC networks (GCP) -> gcloud compute networks list
8. List firewall rules (GCP) -> gcloud compute firewall-rules list
```

**Serverless / Functions**
```
1. List Lambda functions (AWS) -> aws lambda list-functions
2. Invoke a Lambda function (AWS) -> aws lambda invoke --function-name <name> out.json
3. Get Lambda function config (AWS) -> aws lambda get-function --function-name <name>
4. List function apps (Azure) -> az functionapp list
5. List Cloud Functions (GCP) -> gcloud functions list
6. Deploy a Cloud Function (GCP) -> gcloud functions deploy <name> --runtime python39 --trigger-http
```

**Databases**
```
1. List RDS instances (AWS) -> aws rds describe-db-instances
2. List DynamoDB tables (AWS) -> aws dynamodb list-tables
3. List SQL servers (Azure) -> az sql server list
4. List SQL databases (Azure) -> az sql db list --server <server> --resource-group <rg>
5. List Cloud SQL instances (GCP) -> gcloud sql instances list
```

**Logging & Monitoring**
```
1. View CloudTrail events (AWS) -> aws cloudtrail lookup-events
2. Get CloudWatch logs (AWS) -> aws logs tail /log/group/name --follow
3. List log groups (AWS) -> aws logs describe-log-groups
4. View activity log (Azure) -> az monitor activity-log list
5. Read logs (GCP) -> gcloud logging read "resource.type=gce_instance"
6. List log sinks (GCP) -> gcloud logging sinks list
```

**Resource management & Cost**
```
1. List all resources (AWS) -> aws resourcegroupstaggingapi get-resources
2. List all resource groups (Azure) -> az group list
3. List all resources in a group (Azure) -> az resource list --resource-group <rg>
4. List all resources (GCP) -> gcloud asset search-all-resources
5. Get cost/usage (AWS) -> aws ce get-cost-and-usage --time-period Start=2026-07-01,End=2026-08-01 --granularity MONTHLY --metrics BlendedCost
6. Show cost analysis (Azure) -> az consumption usage list
7. List billing accounts (GCP) -> gcloud billing accounts list
```

**Kubernetes-managed clusters**
```
1. List EKS clusters (AWS) -> aws eks list-clusters
2. Update kubeconfig for EKS (AWS) -> aws eks update-kubeconfig --name <cluster>
3. List AKS clusters (Azure) -> az aks list
4. Get AKS credentials (Azure) -> az aks get-credentials --name <cluster> --resource-group <rg>
5. List GKE clusters (GCP) -> gcloud container clusters list
6. Get GKE credentials (GCP) -> gcloud container clusters get-credentials <cluster>
```

**Infrastructure as Code (Terraform — cloud-agnostic)**
```
1. Initialize a working directory -> terraform init
2. Preview changes -> terraform plan
3. Apply changes -> terraform apply
4. Destroy infrastructure -> terraform destroy
5. Show current state -> terraform show
6. List resources in state -> terraform state list
7. Validate configuration -> terraform validate
```

---

### The 80/20 shortlist
If you only remember a handful, make it these:

**AWS:** `aws sts get-caller-identity`, `aws s3 ls`, `aws ec2 describe-instances`, `aws iam list-users`, `aws logs tail --follow`

**Azure:** `az login`, `az account show`, `az vm list`, `az role assignment list`, `az resource list`

**GCP:** `gcloud auth list`, `gcloud config set project`, `gcloud compute instances list`, `gcloud projects get-iam-policy`

**Terraform:** `terraform init`, `terraform plan`, `terraform apply`, `terraform destroy`
