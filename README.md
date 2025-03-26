
# CI/CD Pipeline with Jenkins, SonarQube, Docker, and AWS

This project demonstrates how to build an automated CI/CD pipeline for a web application using Jenkins, SonarQube, Docker, and AWS. Each push to the GitHub repository automatically triggers the pipeline, which builds, tests, analyzes, and deploys the application to an AWS EC2 instance.

![Project illustration](https://github.com/user-attachments/assets/442613de-5ffc-4649-ae1d-787c929827c0)
---
![jenkins](https://github.com/user-attachments/assets/3cc4e279-9ac7-4fce-8c8a-d8bfa43bd1cc)
---
![SonarQube](https://github.com/user-attachments/assets/0ec5c3e2-39f0-419b-a3c2-4f53b30694e7)
---
![Myweb](https://github.com/user-attachments/assets/f343dd84-b133-4c15-9f26-31283adf7ae2)




---

## Table of Contents
- [Project Overview](#project-overview)
- [Pipeline Workflow](#pipeline-workflow)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
  - [1. Launch EC2 Instances](#1-launch-ec2-instances)
  - [2. Install Jenkins, SonarQube, and Docker](#2-install-jenkins-sonarqube-and-docker)
  - [3. Configure SSH Connections](#3-configure-ssh-connections)
  - [4. Configure Jenkins Plugins and Jobs](#4-configure-jenkins-plugins-and-jobs)
- [Pipeline Steps](#pipeline-steps)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

---

## Project Overview

This project automates the process of building, testing, analyzing, and deploying a web application every time code is pushed to the specified GitHub branch. The pipeline performs the following:

- **Static Code Analysis** with SonarQube to catch bugs and vulnerabilities early.
- **Deployment** using Docker on AWS EC2, making the latest application version accessible to end users.

## Pipeline Workflow

1. **GitHub**: Pushes code changes to a specified branch.
2. **Jenkins**: Pulls the latest code and initiates the build and test stages.
3. **SonarQube**: Scans code for quality issues.
4. **Docker**: Deploys the application for user access.

---

## Prerequisites

- **AWS Account** with permissions to create and manage EC2 instances.
- **GitHub Repository** with the web application code.
- **Basic Knowledge** of Jenkins, SonarQube, Docker, and AWS.

---

## Setup Instructions

### 1. Launch EC2 Instances

Create three EC2 instances on AWS with a security group that allows all traffic (for demonstration purposes).

- **Jenkins Instance**
- **SonarQube Instance**
- **Docker Instance**

### 2. Install Jenkins, SonarQube, and Docker

Install the necessary software on each EC2 instance:

- **Jenkins** on the first EC2 instance.
- **SonarQube** on the second EC2 instance.
- **Docker** on the third EC2 instance.

### 3. Configure SSH Connections

1. Generate SSH keys on the Jenkins server:
   ```bash
   ssh-keygen -t rsa
   ```
2. Add the public SSH keys to the **authorized_keys** files on the SonarQube and Docker instances for password-less authentication.

### 4. Configure Jenkins Plugins and Jobs

1. Install the **SSH2 Easy** plugin in Jenkins to manage secure SSH connections.
2. Set up server groups and sites for Jenkins, SonarQube, and Docker.
3. Create a Jenkins job:
   - Add the GitHub repository link.
   - Set the branch to build and deploy.
   - Add build steps to copy code from Jenkins to SonarQube and Docker instances.

---

## Pipeline Steps

1. **Code Checkout**: Jenkins pulls the latest code from GitHub.
2. **Static Code Analysis**: Jenkins sends the code to SonarQube for bug and vulnerability scanning.
3. **Build and Test**: Jenkins prepares the application for deployment.
4. **Deployment**: If the code passes SonarQube checks, Jenkins deploys it to the Docker container, making it available online.

---

## Usage

1. Push code to the specified branch in your GitHub repository.
2. Jenkins automatically starts the pipeline.
3. SonarQube performs a static code analysis.
4. If all tests pass, the code is deployed to Docker on AWS EC2.

---

## Contributing

Feel free to submit issues or pull requests for enhancements or bug fixes.

---

## License

This project is licensed under the MIT License.
