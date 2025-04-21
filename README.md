# java-artifact-ci
# 🚀 CI/CD Pipeline: Jenkins + GitHub + EC2

This project demonstrates a complete CI/CD pipeline using **Jenkins**, **GitHub**, and **AWS EC2** to automate the build, test, and deployment of a simple Java application.

---

## 🔧 Tech Stack

- **Java 17**
- **Maven**
- **Jenkins (Freestyle & Pipeline)**
- **GitHub (SSH Auth)**
- **AWS EC2 (Ubuntu)**
- **SCP / SSH for deployment**

---

## 📂 Project Structure
ci-cd-jenkins-github-ec2/ ├── Jenkinsfile
# Jenkins pipeline configuration ├── pom.xml 
# Maven build file ├── src/ 
# Java source code │ └── main/java/App.java ├── test/ 
# Unit tests │ └── AppTest.java ├──

---

## 📋 Jenkins Pipeline Stages

1. **Clone** the GitHub repo using SSH credentials
2. **Build** the code using `mvn clean compile`
3. **Test** the code using `mvn test`
4. **Package** the application using `mvn package` and archive the JAR
5. **Deploy** the `.jar` to an AWS EC2 instance using `scp` and restart the app with `ssh`

---

## 🚀 Deployment Details

- The EC2 instance must allow SSH access (port 22) and be reachable from Jenkins.
- You must have a `.pem` key file (private key) configured in Jenkins or securely placed on your Jenkins machine.
- The deployment script uses:
  ```bash
  ssh -i /home/ubuntu/Jenkins1.pem ubuntu@54.226.55.23:/home/ubuntu/app/
  ssh -i /home/ubuntu/Jenkins1.pem ubuntu@54.226.55.23 "java -jar /home/ubuntu/app/yourapp.jar &"
