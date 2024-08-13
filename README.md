Tools i used for this project:

Jenkins: Automated CI/CD pipelines
ArgoCD: Continuous deployment to Kubernetes
Kubernetes: Orchestration for containerized applications
Trivy: Container vulnerability scanner
OWASP Dependency-Check: Ensuring secure dependencies
Docker: Containerized application deployment
Terraform: Infrastructure as Code for AWS EKS
Docker: Used in handling the images.

This is a full end to end k8s (Kubernetes) tasks for a test environment.

Pipeline step:

1. when a code is pushed to the man branch
2. Jenkins is triggered via its webhook and handles the build, test and updates the github manifest (image of the app to a new tag)
3. argo Cd syncs and replaces the old pods and services in the cluster to a new one.
4. the app can be access via a load balancer service  via  http://k8s-default-devtests-3a49bb816d-3ecd0200ffd623c8.elb.us-east-1.amazonaws.com/
5. the app runs on 3 pods and can be scaled manually from the deployment file in the repo.
6. the app db credentials were handled using kubernetes secrets (for security best practice), rather than hard coding it.
7. RBAC was created for service account for load balancer, prometheus and grafana.

NOte: i created the cluster on aws using private network for security reasons.


