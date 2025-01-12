Automated CI/CD Pipeline with Infrastructure Provisioning and Monitoring
This project automates the end-to-end process of Continuous Integration and Continuous Deployment (CI/CD), infrastructure provisioning, automated testing, and continuous monitoring. The goal is to enable seamless deployment of code with just a single push to the GitHub repository. This README will guide you through the architecture, tools, and steps involved in setting up this system.

Tools Used
Git: Version control system for tracking changes in the code.
Maven: Used for Continuous Build and packaging of the application.
Jenkins: Automates Continuous Integration (CI) and Continuous Deployment (CD) processes.
Docker: Containerizes the application for easy deployment across environments.
Ansible: Configuration management tool to automate software installation and server configuration.
Terraform: Infrastructure as Code (IaC) tool to provision servers for different environments (test, prod).
Prometheus: For automated monitoring of servers.
Grafana: Visualizes the metrics collected by Prometheus, providing a dashboard for system health.
Project Flow
Push to GitHub:

Developer pushes code to the master branch of the GitHub repository.
Jenkins Integration:

Jenkins listens for changes to the master branch on GitHub.
It then pulls the latest code, compiles it, runs tests, and packages the application.
Infrastructure Provisioning:

Terraform is used to automatically provision a new test server.
The test server is then configured using Ansible with all necessary software (e.g., Java, Maven, Docker).
Deployment to Test Server:

Once the server is provisioned, the latest packaged code is deployed to the test server automatically.
Automated Testing:

A test automation tool is used to run integration tests on the deployed application on the test server.
Deployment to Production:

If the build and test stages are successful, the application is deployed to the production server.
Continuous Monitoring:

Prometheus is used to collect system metrics like CPU utilization, disk space usage, and memory utilization.
Grafana is configured to visualize these metrics on a dashboard.
Metrics Displayed in Grafana Dashboard
CPU Utilization: Percentage of CPU usage on the servers.
Disk Space Utilization: Percentage of used disk space.
Total Available Memory: Amount of available memory on the servers.

+---------------------------------------+
|            GitHub Repository         |
|   (Code Push to Master Branch)       |
+---------------------------------------+
                |
                V
         +-----------------+
         |     Jenkins     |
         |  (CI/CD Server) |
         +-----------------+
                |
                V
  +---------------------------+
  |    Terraform Provisioning  |
  |    (Test Server Setup)     |
  +---------------------------+
                |
                V
       +-----------------+
       |    Ansible      |
       | (Configuration) |
       +-----------------+
                |
                V
       +--------------------------+
       |    Docker (Containerized) |
       |    Application Deployment |
       +--------------------------+
                |
                V
    +----------------------------+
    |  Test Automation & Results |
    +----------------------------+
                |
                V
  +----------------------------+
  |   Terraform (Prod Server)  |
  +----------------------------+
                |
                V
   +----------------------------+
   |    Prometheus + Grafana    |
   | (Monitoring & Dashboard)   |
   +----------------------------+
