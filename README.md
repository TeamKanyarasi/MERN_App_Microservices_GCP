# MERN_App_Microservices_GCP

## Objective:
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

   - Establish a connect between Docker and GCP using the following command.
      ```
      gcloud auth configure-docker YOUR-REGION-docker.pkg.dev
      ```

![Screenshot (163)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/7d33f895-3c9f-409e-a41d-2118dbadc39c)

![Screenshot (164)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/e4e35210-bdea-4692-9822-a002fe694f61)

   - Build Docker images for the frontend and backend.
   - In this task, we utilized the existing Docker images and pushed them to GCP Artifact Registry.
   - Hello Service:

![Screenshot (165)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/d0a6803a-127a-4e1d-9409-627e4b946395)

![Screenshot (177)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/dd64b43c-7e64-4f28-b998-d117732ccd65)

![Screenshot (181)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/0a5e7f40-298f-4ce6-94f2-e61c9a003778)

   - Profile Service:

![Screenshot (166)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/a146a857-a920-42af-bf75-c96f938a3d5b)

![Screenshot (178)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/7dad0ae4-5876-4db3-a3e7-5f0c0f186014)

![Screenshot (182)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/b9ef396f-0db1-4943-b291-c2decede0bab)

   - Frontend Service:

![Screenshot (167)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/068329c1-68b4-424c-a88c-6965e30785b0)

![Screenshot (179)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/c4010f99-1a4b-4892-a69b-623cc77135b5)

![Screenshot (180)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/b66ce749-1fb6-446e-b514-6c3aaec4a480)

## Kubernetes (GKE) Deployment

1. Create GKE Cluster:
   ```
   gcloud container clusters create mern-app --min-nodes=1 --num-nodes=2 --max-nodes=3 --zone=asia-south1-a --machine-type e2-small
   ```
2. Install kubectl to access the cluster [https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html]
3. Pass the env variables into the deployment.yaml file using the below command
   ```
   kubectl create secret generic mongo-secret --from-literal=MONGO_URL=" your mongo db url"
   ```
   
![Screenshot (169)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/58a539b8-b1fc-427c-bdb9-a35f0530cbc9)

4. Apply all the deployment.yaml files from the following link using the below command

   https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/tree/main/deployment
    ```
    kubectl apply -f <deployment-file-name.yml>
    ```
![Screenshot (174)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/fa5a5b77-3064-4bc9-aae7-df0c08825719)

![Screenshot (170)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/77efada9-0694-463d-b0f3-c54b87e2bd89)

![Screenshot (172)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/11a332b0-c732-4122-a497-0cf5de9f85b5)

![Screenshot (175)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/bf497883-9c98-4dff-9d47-869b6ee5b51d)

![Screenshot (176)](https://github.com/TeamKanyarasi/MERN_App_Microservices_GCP/assets/139607786/ca942845-14bd-4d7f-8d69-557507aced81)



