CI/CD Pipeline Demo with GitHub Actions
This repository demonstrates how to set up a CI/CD pipeline for a simple Python application using GitHub Actions. The application is built using the Flask framework and is containerized using Docker. The CI/CD pipeline automates the building, testing, and deployment of the application to Docker Hub.

Overview
In this demo, we will:

Build a Docker container for a Python Flask application.
Run automated tests using pytest.
Push the Docker image to Docker Hub.
Deploy the application locally to verify the deployment.
Application Details
The Python application is created using the Flask module and shows a "Hello World" message on a web page. The repository contains the following files:

app.py: The main application file.
Dockerfile: The Dockerfile used to build the Docker image.
requirements.txt: Contains the Python dependencies.
test.py: Contains the automated tests for the application.
CI/CD Pipeline with GitHub Actions
The CI/CD pipeline is defined in .github/workflows/cicd-pipeline.yml and is triggered on every push to the main branch. The pipeline contains two jobs:

Build Job:

Checks out the repository.
Logs in to Docker Hub using credentials stored in GitHub Secrets.
Builds the Docker image and pushes it to Docker Hub.
Test Job:

Checks out the repository.
Installs dependencies from requirements.txt.
Runs tests using pytest.
Prerequisites
To run this CI/CD pipeline, you need:

A Docker Hub account.
GitHub repository secrets configured for Docker Hub credentials:
DOCKERHUB_USERNAME: Your Docker Hub username.
DOCKERHUB_PASSWORD: Your Docker Hub password.
Getting Started
Clone the Repository:

git clone https://github.com/your-username/your-repo.git
cd your-repo

Configure GitHub Secrets:

Go to your GitHub repository's settings.
Add the following secrets under Settings > Secrets > Actions:
DOCKERHUB_USERNAME
DOCKERHUB_PASSWORD
Build and Test the Pipeline:

Make a change in the app.py file to trigger the pipeline.
For example, change "Hello World" to "Hello CI/CD World" in the application.
Check the Pipeline Status:

Navigate to the Actions tab in your GitHub repository.
You will see the pipeline running. Once completed, it should build the Docker image and run tests.
Pull and Run the Docker Image Locally:


docker pull <your-dockerhub-username>/<your-repo>:latest
docker run -p 5000:5000 <your-dockerhub-username>/<your-repo>:latest

Visit the Application:

Open a web browser and go to http://localhost:8080.
You should see the message "Hello CI/CD World" if everything worked correctly.
Troubleshooting
If the test job fails, it may be due to a mismatch in the expected output. Ensure that the app.py file returns the expected "Hello World" message.
