## Prerequisites

Before setting up the pipeline, ensure you have the following:
# A simple Docker flask App
- This app is written in in python
1. **Google Cloud Project**: Create or use an existing Google Cloud Project.
2. **Source Repository**: Ensure you have a repository on **Google Cloud Source Repositories**, **GitHub**, or **Bitbucket**.
3. **Google Cloud SDK**: [Install Google Cloud SDK](https://cloud.google.com/sdk/docs/install).
4. **Permissions**: Ensure you have the appropriate IAM roles:
   - `Cloud Build Editor`
   - `Viewer` on the project for logging and monitoring
   - `Storage Admin` for managing artifacts

## Steps to Set Up CI/CD Pipeline with Cloud Build

### 1. Enable Required APIs

Run the following commands to enable APIs required for Cloud Build:

```bash
gcloud services enable cloudbuild.googleapis.com
gcloud services enable sourcerepo.googleapis.com
gcloud services enable containerregistry.googleapis.com
2. Create a Cloud Build YAML File
In the root of your repository, create a cloudbuild.yaml file that defines the steps for your CI/CD pipeline. Here’s an example configuration file:

This configuration includes the following stages:

Cloning the repository
Running tests
Building a Docker image
Pushing the image to Google Container Registry
Deploying to Google Cloud Run or GKE (Google Kubernetes Engine)
3. Set Up Triggers for Automatic Build and Deployment
Go to the Google Cloud Console and navigate to Cloud Build > Triggers.
Click Create Trigger.
Configure the trigger:
Select the repository and branch/tag that should trigger the build.
Use the cloudbuild.yaml file as the configuration file.
Save the trigger.
4. Set Up Service Accounts and Permissions
Ensure the Cloud Build service account has the necessary permissions to deploy to your selected service.
For example, to deploy to Cloud Run, add the following IAM role:
Cloud Run Admin
5. Test the Pipeline
Push a commit to the configured branch in your repository to test the pipeline. Cloud Build should:

Clone the code.
Run tests.
Build and push the Docker image.
Deploy the service.
You can monitor the build progress in the Google Cloud Console under Cloud Build > History.
