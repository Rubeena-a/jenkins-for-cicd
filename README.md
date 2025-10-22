# jenkins-for-cicd
Jenkins Pipeline for Automated Build and Deployment

## Project Overview

This project demonstrates a CI/CD pipeline using Jenkins and Docker. It includes a sample application and the necessary configurations to build and deploy it using Jenkins.

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

## Usage
- Access the application at `http://localhost:3000`
- Access Jenkins at `http://localhost:8080`


