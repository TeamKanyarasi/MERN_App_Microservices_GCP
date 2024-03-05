# MERN_App_Microservices_GCP

## Objective :
Deploying a MERN Microservice Application using Kubernetes in GCP.

## Prerequisites
1: Launch a GCP VM.

2: Install gcloud CLI in it
   - Follow the link https://cloud.google.com/sdk/docs/install#deb to install gcloud cli for your desired OS.

3: Install Jenkins in it

4: Install docker in it

5: Install Kubectl in it

## Set Up the gcloud CLI
1: To initialize the gcloud CLI, run
```
gcloud init
```
2: Create or select a configuration if prompted.
   - If you are initializing a new gcloud CLI installation, gcloud init creates a configuration named default for you and sets it as the active configuration. If you have existing configurations, gcloud init prompts you to choose between three options — re-initialize the active one, switch to another one and re-initialize it, or create a new one.

3: Choose a current Google Cloud project if prompted.
```
This account has a lot of projects! Listing them all can take a while.
 [1] Enter a project ID
 [2] Create a new project
 [3] List projects
Please enter your numeric choice:
```
4: Run gcloud auth login
```
gcloud auth login
```

## Prepare the MERN Application

1. Containerize the MERN Application:

   - Ensure the MERN application is containerized using Docker. Create a Dockerfile for each component (frontend and backend).

2. Docker Images:

   - Build Docker images for the frontend and backend.

PS : We're using existing public images from Amazon ECR.
