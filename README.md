## Architecture

The following diagram illustrates the end-to-end CI/CD workflow, from pushing code to GitHub through Jenkins automation, Docker image publishing, and Kubernetes deployment on Minikube.

<p align="center">
  <img src="https://github.com/user-attachments/assets/4df6b07f-6530-4d21-944b-6be08394a095" alt="Jenkins CI/CD Architecture" width="85%">
</p>

## Successful Pipeline Execution

The screenshot below shows a successful Jenkins pipeline execution, with all stages completed successfully.

<p align="center">
  <img width="1470" height="835" alt="Screenshot 2026-11-10 at 1 28 45 AM" src="https://github.com/user-attachments/assets/7663fd83-da70-4b0d-a965-f47b2d2a4c5d" />
</p>

## Credentials Management

- Jenkins Credentials Store is used to securely manage Docker Hub credentials and other required secrets.
- Credentials and access tokens are never hardcoded in the Jenkinsfile.
- Sensitive configuration files and credentials are excluded from the Git repository.
- Authentication is handled securely through Jenkins Credentials Binding.




