# Jenkins CI Sample Pipeline

This project contains medium level Jenkins Pipeline (Declarative) as to demonstrate the core stages of a CI pipeline.

## 📌 Pipeline Overview
The pipeline performs the following steps:
1. **Checkout** → Clones this GitHub repository into the Jenkins workspace.
2. **Build** → Creates a simple build output file (`output.txt`).
3. **Test** → Runs a basic test command to verify the build.
4. **Archive Artifacts** → Archives the build output so it can be accessed later in Jenkins.

## 🛠 Pipeline Script (Jenkinsfile)
The `Jenkinsfile` in this repo defines the pipeline stages:
- **agent any** → Runs on any available Jenkins agent.
- **stage('Checkout')** → Clones this repo.
- **stage('Build')** → Runs shell commands and creates `build/output.txt`.
- **stage('Test')** → Executes basic verification commands.
- **stage('Archive Artifacts')** → Archives the build artifacts (`output.txt`).
