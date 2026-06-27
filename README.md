
# End to End CICD Pipeline Project

## This Project Can be Used to Build an End to End CICD Pipeline.

## CICD Pipeline Stages

- Checkout Code from GitHub.
- Build Project.
- Build Docker Image.
- Push Docker Image to AWS ECR Registry.
- Update Docker Image Tag in Kubernetes Manifest.
- Deploy Application into Elastic Kubernetes Cluster.

### Tools and Technologies Used are Java, Git, GitHub, Maven, SonarQube, Sonatype Nexus, Jenkins, Docker, DockerHub, Kubernetes and Amazon Web Services.

# Project Execution
## Git Checkout
```bash
  git branch: 'main', url: 'https://github.com/PavanKumarKJ347/JavaMavenApplication_GitHubActions.git'
```

## Build Project

Build Automation Tool Maven Can be Used to Build This Project as This Project is Developed Using Java Programming Language.

```bash
  mvn clean package
```
Note:
Java and Maven Should be Installed as a Prerequisite to Build Project Code.

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
**Application Can be Deployed to Kubernetes Cluster Using Kubernetes Manifest Files as well as Helm Chart.**