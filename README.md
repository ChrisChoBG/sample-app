# Sample App

This repository demonstrates the implementation of a DevOps workflow using Google Cloud Platform (GCP). It showcases the deployment of a simple Go application on Google Kubernetes Engine (GKE) with automated CI/CD pipelines facilitated by Cloud Build.

## Overview

The project encompasses the following components:

- **Go Application**: A basic Go-based web application.
- **Dockerfile**: Defines the containerization process for the Go application.
- **Cloud Build Configurations**:
  - `cloudbuild-dev.yaml`: Configuration for the development environment.
  - `cloudbuild.yaml`: Configuration for the production environment.
- **GKE Deployment**: Scripts and configurations to deploy the application on GKE clusters.

## Getting Started

### Prerequisites

- A Google Cloud Platform account.
- Google Cloud SDK installed and configured.
- Access to create and manage GKE clusters.
- Permissions to set up Cloud Build triggers.

### Setup Instructions

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/ChrisChoBG/sample-app.git
   cd sample-app
   ```

2. **Create a GKE Cluster**:

   ```bash
   gcloud container clusters create sample-app-cluster \
     --num-nodes=3 \
     --zone=us-central1-a
   ```

3. **Configure Docker Authentication**:

   ```bash
   gcloud auth configure-docker
   ```

4. **Build and Push Docker Image**:

   ```bash
   docker build -t gcr.io/[PROJECT-ID]/sample-app .
   docker push gcr.io/[PROJECT-ID]/sample-app
   ```

   Replace `[PROJECT-ID]` with your actual GCP project ID.

5. **Deploy to GKE**:

   Apply your Kubernetes deployment and service configurations to deploy the application.

6. **Set Up Cloud Build Triggers**:

   - Navigate to the Cloud Build section in the GCP Console.
   - Create triggers for both development and production builds using the provided YAML configurations.

7. **Continuous Deployment**:

   - Make changes to the application code.
   - Push updates to the repository.
   - Cloud Build will automatically build and deploy the application based on the configured triggers.

## Rollback Procedure

In case of issues with the production deployment:

1. Identify the previous successful build from the Cloud Build history.
2. Redeploy the application using the artifacts from the selected build.

## Project Structure

```
sample-app/
├── Dockerfile
├── README.md
├── cloudbuild-dev.yaml
├── cloudbuild.yaml
├── main.go
```

## Technologies Used

- **Go**: Programming language for the application.
- **Docker**: Containerization of the application.
- **Google Kubernetes Engine (GKE)**: Hosting the containerized application.
- **Cloud Build**: CI/CD pipeline for automated builds and deployments.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
