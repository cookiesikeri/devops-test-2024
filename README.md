Tools i used for this project:

1. Jenkins: Automated CI/CD pipelines
2. ArgoCD: Continuous deployment to Kubernetes
3. Kubernetes: Orchestration for containerized applications
4. Trivy: Container vulnerability scanner
5. Trivy FS: scanning the file system of the project
6. OWASP Dependency-Check: Ensuring secure dependencies
7. Docker: Containerized application deployment
8. Terraform: Infrastructure as Code for AWS EKS
9. Docker: Used in handling the images.

This is a full end to end k8s (Kubernetes) tasks for a test environment.

Pipeline step:

1. when a code is pushed to the man branch
2. Jenkins is triggered via its webhook and handles the build, test and updates the github manifest (image of the app to a new tag)
3. argo Cd listens to the repo and pulls latest app sand replaces with the old pods and services in the cluster.
4. the app can be access via a load balancer service  via  http://k8s-default-devtests-3a49bb816d-3ecd0200ffd623c8.elb.us-east-1.amazonaws.com/
5. the app runs on 3 pods and can be scaled manually from the deployment file in the repo.
6. the app db credentials were handled using kubernetes secrets (for security best practice), rather than hard coding it.
7. RBAC was created for service account for load balancer, prometheus and grafana.

NOte: i created the cluster on aws using private network for security reasons.

ArgoCD can be accessed here https://ab53794af9d7248d381b6052a9fd4ab7-150846727.us-east-1.elb.amazonaws.com/applications?showFavorites=false&proj=&sync=&health=&namespace=&cluster=&labels=

Jenkins for this project can be accessed here http://34.195.57.238:8080/

to access the Jump server kindly reach out to for the pem file.

the link to the cluster https://github.com/cookiesikeri/eks-github-action-terraform



