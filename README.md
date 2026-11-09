## Architecture

The following diagram illustrates the end-to-end CI/CD workflow, from pushing code to GitHub through Jenkins automation, Docker image publishing, and Kubernetes deployment on Minikube.

<p align="center">
  <img src="https://github.com/user-attachments/assets/4df6b07f-6530-4d21-944b-6be08394a095" alt="Jenkins CI/CD Architecture" width="85%">
</p>

## Successful Pipeline Execution

The screenshot below shows a successful Jenkins pipeline execution, with all stages completed successfully.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fbfd769a-f790-4df2-8cd3-1f05cbc193cf" alt="Successful Jenkins Pipeline Execution" width="75%">
</p>

## Credentials Management

- Jenkins Credentials Store is used to securely manage Docker Hub credentials and other required secrets.
- Credentials and access tokens are never hardcoded in the Jenkinsfile.
- Sensitive configuration files and credentials are excluded from the Git repository.
- Authentication is handled securely through Jenkins Credentials Binding.




