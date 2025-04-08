 🚀 task2-app

A simple Node.js app with CI/CD pipeline using Jenkins and Docker, deployed on an AWS EC2 instance.



## 📌 Project Setup Summary

1. 🔧 Virtual Machine Setup (AWS EC2)
- Launched an EC2 instance on AWS using Ubuntu as the OS.
- Configured security groups to allow SSH (port 22), HTTP (port 80), and Jenkins (port 8080).

2. ☕ Installed Java
 Installed **OpenJDK 17 (required for Jenkins):
  
  sudo apt update
  sudo apt install openjdk-17-jdk -y

3. 🔨 Installed Jenkins

Added Jenkins repository and installed Jenkins:


wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y

Started and enabled Jenkins:


sudo systemctl start jenkins
sudo systemctl enable jenkins
Accessed Jenkins at http://<your-ec2-ip>:8080

4. 🐳 Installed Docker

Installed Docker to build and run containerized applications:


sudo apt install docker.io -y
sudo usermod -aG docker jenkins
sudo systemctl restart docker

5. 🔁 GitHub Integration

Used GitHub Webhooks to automatically trigger the Jenkins pipeline on every push.
Enabled "GitHub hook trigger for GITScm polling" in Jenkins job configuration.

6. 🛠️ Configured Jenkins Pipeline

Selected Pipeline script from SCM option in the Jenkins project.
Linked it to the GitHub repository containing this project.
Jenkins automatically fetched the Jenkinsfile and executed the pipeline on code commits.

📂 Project Structure

bash
Copy
Edit
task2-app/
├── index.js         # Simple Node.js app
├── package.json     # Node.js project config
├── Dockerfile       # Docker instructions to containerize the app
└── Jenkinsfile      # Jenkins pipeline definition
