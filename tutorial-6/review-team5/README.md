### Introduction

AWS Elastic Beanstalk is a managed service by Amazon Web Services (AWS) that streamlines the deployment and management of applications in the cloud. It enables developers to quickly deploy and manage applications without the need to handle the underlying infrastructure.

### Tutorial

#### Step 1: Create a Spotify Account and App

1. **Create a Spotify Account**:
   - Sign up for a Spotify account [here](https://www.spotify.com/es/signup) if you don't have one already.

2. **Create a Spotify Developer App**:
   - Go to the Spotify Developer website [here](https://developer.spotify.com/).
   - Log in with your Spotify account.
   - Create a new app by filling in the required details:
     - **App Name**: ccbda_research
     - **App Description**: Research topic for CCBDA
     - **Redirect URIs**: http://localhost:3000 
   - Create the app and save the Client ID and Client Secret from the app settings.

   ![Creating Spotify App](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/b30d9273-923d-4546-9c77-653277ca4f0d)
   ![App Created](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/eed3e277-ca40-4e48-aa59-c5f99e1e6ed2)

#### Step 2: Clone the Repository and Set Up the App

3. **Clone the Repository**:
   - Clone the repository from GitHub and add the Client ID and Client Secret to the `spotify_script.py` file.

4. **Set Up the Python Environment**:
   - Create a virtual environment and install the necessary dependencies:
     ```bash
     (venv) _$ pip install -r requirements.txt
     ```
   
5. **Run the Flask App Locally**:
   - Execute the Flask application locally:
     ```bash
     (venv) _$ python3 application.py
     ```
   - Open the application at `http://127.0.0.1:8000` to see the Spotify code for the song and have the option to get a new random song.
   
   ![Local Web App](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/142ae5de-877d-4a2f-9cb7-1ceb6f3eb50f)

#### Step 3: Deploy the App with AWS Elastic Beanstalk

6. **Prepare the Application for Deployment**:
   - Zip the application folder, excluding the virtual environment:
     ```bash
     zip -r application.zip ./ -x "/venv/*"
     ```
   
7. **Deploy to AWS Elastic Beanstalk**:
   - Open the AWS Elastic Beanstalk console and create a new application:
     - **Application Name**: research-ccbda
   
   ![Create Application](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/8b10fe24-c52e-407c-943d-507134f2dbf4)

8. **Create an Environment**:
   - Name the environment "research" and choose Python 3.11 as the platform.
   
   ![Create Environment](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/327d882d-72c3-4747-8250-63b20a39ea69)
   ![Choose Platform](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/0194db12-d0eb-4638-b5c0-3a2addc5adb9)
   
   - Upload the zipped application code and configure the service roles:
     - **Service Role**: LabRole
     - **EC2 Key Pair**: vockey
     - **EC2 Instance Profile**: LabInstanceProfile
   - Skip the remaining configurations and submit.

9. **Access the Deployed Application**:
   - Once the environment is launched, click on the provided domain to access your website.
   
   ![Deployment Dashboard](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/94b440ca-1936-45fb-a087-8d967e5edfc0)
   ![Deployed Web App](https://github.com/AlexCioca/Hungry-Angular/assets/95017313/9695ad63-26df-49ba-af65-c51fa10229a6)
### Summary 
This tutorial on integrating a Spotify app with AWS Elastic Beanstalk is well-structured and comprehensive. It guides users through creating a Spotify developer app with ease, setting up a local development environment with Flask, and deploying the application on AWS Elastic Beanstalk.

