# Deployment guideline
# 1. Create EKS Cluster and Worker Nodes
First, create your Amazon EKS cluster and worker nodes by following the AWS guidelines:
- https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

# 2. Deploy PostgreSQL Database
## 2.1 Update Database Configuration
Before deploying PostgreSQL, update the environment variables for the database configuration in postgresql-deployment.yaml, specifically the user name and password.

## 2.2 Deploy PostgreSQL Database
Run the following commands to deploy the PostgreSQL database:
```
kubectl apply -f pvc.yaml          # Apply PersistentVolumeClaim
kubectl apply -f pv.yaml           # Apply PersistentVolume
kubectl apply -f postgresql-deployment.yaml  # Apply PostgreSQL Deployment
```

## 2.3 Deploy PostgreSQL Service
Deploy the PostgreSQL service using the command:
```
kubectl apply -f postgresql-service.yaml
```
# 3. Setup AWS CodeBuild Pipeline
Follow the AWS guidelines to set up your AWS CodeBuild pipeline. This process will help automate your build and deployment workflows.

# 4. Deploy Coworking Application
## 4.1 Update Configuration
Before deployment, ensure the following configuration files are updated:
- Update deployment/configmap.yaml with necessary configuration settings.
- Update deployment/configmap-secret.yaml to handle secret configurations.
- Update the image value in deployment/coworking.yaml to point to the correct container image.
## 4.2 Deploy Coworking Application
Run these commands to deploy the coworking application:
```
kubectl apply -f deployment/configmap.yaml
kubectl apply -f deployment/configmap-secret.yaml
kubectl apply -f deployment/coworking.yaml
```

# 5. Verify Deployment
To ensure that all pods are running successfully, execute the following command:
```
kubectl get pods
```
This command will display the status of all the pods in your Kubernetes cluster