# aviGcp

## Goals
Spin up a full Gcp/Avi environment (through Terraform and Ansible)

## Prerequisites:
1. Make sure terraform in installed in the orchestrator VM
2. Make sure GCP credential/details are configured as environment variable:
```
GOOGLE_CLOUD_KEYFILE_JSON=**************
```

## Environment:

Terraform tf and Playbook(s) has/have been tested against:

### terraform

```
avi@ansible:~$ terraform -v
Terraform v0.12.21

Your version of Terraform is out of date! The latest version
is 0.12.26. You can update by downloading from https://www.terraform.io/downloads.html
avi@ansible:~$
```

### Avi version

```
18.2.9
```

### GCP Region:

europe-north1

## Input/Parameters:

1. All the paramaters/variables are stored in variables.tf

## Use the the terraform script to:
1. Create the VPC and subnets
2. Spin up 3 backend servers (second subnet) across the 3 zones - no NAT public IP
3. Spin up a jump server with ansible in the mgt subnet (first subnet) - NAT Public IP
4. Transfer GCP ansible files to the jump server
5. Create a GCP storage bucket
5. Download the Avi image to the jump server (via Ansible)
6. Upload the Avi image to the bucket (via Ansible)
7. Create an GCP image (via Ansible)
8. Remove avi controller object from the GCP bucket (does not work)
9. Spin up an Avi controller (in the first subnet)
10. Transfer Avi ansible files to the jump server including Ansible hosts
11. Wait for Avi controller to be ready
12. Bootstrap Avi Controller (password update)
13. Configure System config
14. Create IPAM/DNS profile (Avi based)
15. Create a new GCP cloud (with Avi IPAM/DNS create before)
16. Create/Update SE Group (a new one ffor GSLB)
17. Create health monitor, create pool, create VS

## Run the terraform:
```
terraform apply -auto-approve
# the terraform will output the command to destroy the environment.
```

### future devlopment:
- Handle a controller cluster use case (multi AZ)
