
# End to End CICD Pipeline Project

## This Project can be used to Build an End to End CICD Pipeline.

## CICD Pipeline Stages

- Checkout Code from GitHub.
- Build Project.
- Build Docker Image.
- Push Docker Image to AWS ECR Registry.
- Update Docker Image Tag in Kubernetes Manifest.
- Deploy Application into Elastic Kubernetes Cluster.

### Tools and Technologies used are Java, Git, GitHub, Maven, SonarQube, Sonatype Nexus, Jenkins, Docker, DockerHub, Kubernetes and Amazon Web Services.

![CICD](https://github.com/DevOpsCloudAutomation/Java_Docker/assets/123757746/085ef572-bd9d-4d05-b710-4fc2a0646d39)
  
# Project Execution
## Git Checkout
```bash
  git branch: 'main', url: 'https://github.com/PavanKumarKJ347/JavaMavenApplication_GitHubActions.git'
```

## Build Project

Build Automation Tool Maven can be used to build this project as this project is developed using Java Programming Language.

```bash
  mvn clean package
```
Note:
Java and Maven should be installed as a prerequisite to Build Project Code.

## Build Docker Image
```bash
  docker build -t 149536451818.dkr.ecr.ap-south-1.amazonaws.com/login:${{ github.run_number }} .
```

## Push Docker Image to Docker Hub Registry
```bash
  docker push 149536451818.dkr.ecr.ap-south-1.amazonaws.com/login:${{ github.run_number }}
```

## Update Docker Image Tag in Kubernetes Manifest
```bash
  sed -i "s/Build_Tag/${{ github.run_number }}/g" Deployment.yaml
```

## Deploy Application to Kubernetes Cluster
```bash
  kubectl apply -f Deployment.yaml

  helm install helmwebapplication helmwebapplication -n production
```
**Note**<br>
**Application can be deployed to Kubernetes Cluster using Kubernetes Manifest Files as well as Helm Chart.**