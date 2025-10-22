# jenkins-for-cicd
Jenkins Pipeline for Automated Build and Deployment

## Project Overview

This project demonstrates a CI/CD pipeline using Jenkins and Docker. It includes a sample application and the necessary configurations to build and deploy it using Jenkins.
- A sample Node.js app with basic HTTP server and test
- Dockerization of the app
- Jenkins pipeline for build, test, push, and deploy
- Jenkins running in Docker with Docker CLI support


## Project Structure

- **app/**: Contains the application code.
  - `package.json`: Lists the dependencies for the application.
  - `server.js`: The main server file for the application.
  - `test.js`: Contains tests for the application.
- **jenkins-docker/**: Contains Docker configurations for Jenkins.
  - `Dockerfile`: The Dockerfile for building the Jenkins image.
  - `docker-compose.yml`: Defines the services for Jenkins and the application.

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/<name>/cicd-using-jenkins.git
   cd cicd-using-jenkins
   ```
2. Build the Docker images:
   ```bash
   docker-compose build
   ```
3. Start the services:
   ```bash
   docker-compose up
   ```


### Node.js App
- Located in the app directory
- Simple HTTP server on port 3000 responding with Hello
- Includes a basic test script (npm test) to verify server response

### Dockerization
- Dockerfile in root builds the Node.js app image
- Exposes port 3000
- Uses node:18-alpine for lightweight builds

### Jenkins Setup
- Jenkins runs in Docker using Dockerfile (extends official Jenkins image, adds Docker CLI)
- docker-compose.yml sets up Jenkins with persistent volume and Docker socket access
- Jenkins UI available at http://localhost:8080 when running locally

### Jenkins Pipeline (Jenkinsfile)
- Checkout: Retrieves source code
- Build Docker image: Builds app image with tag ${BUILD_NUMBER}
- Test inside container: Runs npm test inside the built image
- Push to registry: (optional) Pushes image to Docker Hub if PUSH_TO_REGISTRY is true
- Deploy (local): Runs the app container locally, mapping port 8080 (host) to 3000 (container)
- Credentials for Docker Hub are managed via Jenkins (dockerhub-creds)

### How to Run Locally
1. Build and Run Jenkins
   ```
   cd jenkins-docker
docker-compose up --build```

- Access Jenkins at http://localhost:8080
- Initial admin password can be found in Jenkins container logs
2. Build and Test Node.js App Manually
  
### Build app image
```docker build -t simple-app:latest .```
### Run tests
```docker run --rm simple-app:latest npm test```
### Run app
```docker run -d -p 8080:3000 --name simple-app simple-app:latest```


3. Jenkins Pipeline
- Configure a Jenkins job using the included Jenkinsfile
- Set up Docker Hub credentials in Jenkins (dockerhub-creds)
- Trigger builds manually or via SCM webhook
 ### Notes
- The pipeline supports parameterized builds (push to registry optional)
- Jenkins container has Docker CLI for building and running containers
- App container exposes port 3000; mapped to 8080 on host during deploy


## Usage
- Access the application at `http://localhost:3000`
- Access Jenkins at `http://localhost:8080`

### Author
Rubeena Shaik
