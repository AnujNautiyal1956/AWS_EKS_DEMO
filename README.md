# AWS_EKS_MSTAKX_DEMO
K8's cluster on AWS EKS using IAAC tool Terraform

## Componenets
Infrastructure Provisioning- Terraform

Ingress controller - Nginx

Kubernetes CLI - Kubectl

## Steps to provision K8's cluster Infrastructure
The complete process of infrastructure provisioning has been automated through Terraform.
# Infra provision
cd ClusterConfig Directory 

terraform init

terraform plan

terraform apply

# Nginx Ingress controller installation
cd Nginx-Ingress-controller

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/aws/service-l7.yaml

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/aws/patch-configmap-l7.yaml

# Namespace creation and Guestbook-Application installation
cd Guestbook-php-Application

The process of namespace creation and Installtion of the Guestbook applciation has been automated through gitlab-ci.yaml CI/CD Devops.
All the commands for installation of the application on respective namespaces is done through the automated Integration and deployment process.

After this the exposure of both staging and applications  on respective domain names is also done through the gitlab-ci.yaml

The autoscaling of the pods on the basis of CPU-Utilization is the last stage in the yaml file .

## Important Note
The runner has not been registered as of now to carry out the process of CI/CD 
Also the Docker image has not been explicitly defined in the imagename block of gilab-ci.yaml
Both these things are WIP

## References 
Cluster Configuration Terraform reference - https://github.com/christopherhein/terraform-eks.git

Nginx Ingress controller - https://kubernetes.github.io/ingress-nginx/deploy/#aws

Guestbook-application installation on namespaces - https://kubernetes.io/docs/tutorials/stateless-application/guestbook/


