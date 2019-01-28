# gke-test
Exploring Google Kubernetes Engine. Includes
- a simple test app dockerized and running on Google Kubernetes Engine
- Postgres instance on Cloud SQL
- infrastructure defined with Terraform
- multiple environments
- CI pipeline on CircleCI

## Dependencies
- [terraform](https://learn.hashicorp.com/terraform/getting-started/install.html)
- [gcloud](https://cloud.google.com/sdk/#Quick_Start) for local testing

## Setup

The following steps need to be completed manually to set up the project before automation kicks in:

1. Create a new Google Cloud project per each environment
2. For each Google Cloud project,
  - set up a Cloud Storage bucket for [remote Terraform state](https://www.terraform.io/docs/backends/types/gcs.html)
  - set up a service IAM account to be used by Terraform. Attach the `Editor` role to the created user
  - run `terraform init` to initialize Terraform providers

## Manual deployment

1. Update infra: `terraform apply`
2. Follow [instructions](https://cloud.google.com/kubernetes-engine/docs/tutorials/hello-app) on building and pushing a Docker image to GKE

## TODO

- networking
- (load balancing)[https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer]
- secrets
- tune down Terraform IAM user role, least privilege
