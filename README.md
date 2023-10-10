# Jenkins Pipeline for Java Project with SonarQube and Nginx

This repository contains a Jenkins Pipeline script for building and deploying a Java project using Git, JDK 17, Maven, Docker for SonarQube, and Nginx.

## Prerequisites

Before running the Jenkins Pipeline, ensure you have the following prerequisites installed:

- Jenkins CI Server
- JDK 17
- Maven
- Docker
- SonarQube Docker image
- Nginx

## Jenkins Pipeline Overview

The Jenkins Pipeline script automates the following steps:

1. **Git Checkout:** The script checks out the Java project source code from your Git repository.

2. **Build with Maven:** It builds the Java project using Maven, ensuring that all dependencies are resolved.

3. **Static Code Analysis with SonarQube:** The Docker container for SonarQube is pulled and started, and the project's code is analyzed for quality issues using the SonarQube scanner.

4. **Artifact Packaging:** The script packages the project artifacts

5. **Deploy with Nginx:** A Docker container running Nginx serves as a reverse proxy to the application, allowing you to access it.

## Usage

1. Configure Jenkins to use this repository and set up a Pipeline job.

2. Customize the Jenkinsfile if necessary, e.g., by modifying the project name or build steps.

3. Run the Jenkins Pipeline job, which will execute the defined stages.

4. Access your deployed Java application via Nginx at http://your_server_ip.

## Additional Configuration

- Adjust SonarQube analysis parameters in the Jenkinsfile to match your SonarQube server configuration.

## Contributing

Contributions to improve this Jenkins Pipeline script are welcome. Feel free to submit pull requests or raise issues.

## License

This project is licensed under the [MIT License](LICENSE).

