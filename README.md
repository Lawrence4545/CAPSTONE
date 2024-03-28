# CAPSTONE PROJECT QUESTION

#Project Overview:
#Objective: We aim to deploy a microservices-based application, specifically the Socks Shop, #using a modern approach that emphasizes automation and efficiency. The goal is to use #Infrastructure as Code (IaaC) for rapid and reliable deployment on Kubernetes.
#Setup Details Explained:
#What You'll Do: Your main task is to set up the Socks Shop application, a demonstration of a #microservices architecture, available on GitHub. You'll be using tools and technologies that #automate the setup process, ensuring that the application can be deployed quickly and #consistently.
#Resources:
#- Socks Shop Microservices Demo:https://github.com/microservices-demo/microservices-demo.github.#io
#- Detailed Implementation Guide:https://github.com/microservices-demo/microservices-demo/tree/#master
#Task Instructions:
#1. Use Infrastructure as Code: Automate the deployment process. This means all the steps to get #the application running on Kubernetes should be scripted and easily executable.
#2. Focus on Clarity and Maintenance: Your deployment scripts and configurations should be easy #to understand and maintain. Think of someone else (or yourself in the future) needing to update #or replicate your setup.
#3. Key Evaluation Criteria:

# - Deployment Pipeline: How the application moves from code to a running environment.

# - Monitoring and Alerts: Implement Prometheus for monitoring and set up Alertmanager for #alerts.

# - Logging: Ensure the application's operations can be tracked and analyzed through logs.

# - Tools for Setup: Use either Ansible or Terraform for managing configurations. Choose an #Infrastructure as a Service (IaaS) provider where your Kubernetes cluster will live.

#4. Security and HTTPS: Make sure the application is accessible over HTTPS by using Let’s #Encrypt for certificates. Consider implementing network security measures and use Ansible Vault #for handling sensitive information securely.
#Extra Project Requirements for Bonus Points:
#- HTTPS Requirement: The application must be securely accessible over HTTPS.
#- Infrastructure Security: Enhance security by setting up network perimeter security rules.
#- Sensitive Information: Use Ansible Vault to encrypt sensitive data, adding an extra layer of #security.
#Project Goals Summarized:
#This project is about deploying a microservices-based application using automated tools to #ensure quick, reliable, and secure deployment on Kubernetes. By focusing on Infrastructure as #Code, you'll create a reproducible and maintainable deployment process that leverages modern #DevOps practices and tools.

###################### SOLUTION #########################################################

#Deploying the Socks Shop Application

Welcome to the readme file for deploying the Socks Shop application, a demonstration of a microservices architecture, using Infrastructure as Code (IaC) principles.

In this document, I will outline how to automate the deployment process using Terraform, ensuring clarity, maintainability, and security throughout the setup.

####### DevOps ##########

DevOps, short for "Development and Operations," originally aimed to unite development and operations teams. Over time, it has evolved into a broader concept focused on making software development faster, more reliable, and more efficient. This includes leveraging cloud computing, automation, machine learning, AI, and other technologies.

######## Process ########

After building the code with Terraform using the modern technology of Infrastructure as Code to automate every deployment process, follow these steps:

Create an EC2 Instance on AWS with a VPC:

Inbound Rule:

- All Traffic - IPv4
- SSH Port - 22
- HTTPS Port - 443
- HTTP Port - 80

Outbound Rule:

- All Traffic - IPv4
- All Traffic - IPv6

###### Create an Administrative User:

Create a user with administrative access privileges in the same region for the deployment and save both the access key and secret access key.

#### Instance Connect:

Connect to the instance on AWS and clone the repository to AWS.
Make the installer.sh file executable using the command: chmod +x installer.sh
Install Jenkins by running: ./installer.sh

###### Access Jenkins:

Copy the public IP address of the EC2 instance to a browser (IP:8080) to access the Jenkins default page.

###### Customize Jenkins:

Customize Jenkins, install its plugins, and sign up into Jenkins creating a username and password.

##### Link Jenkins with GitHub:############

On the dashboard, select manage Jenkins => Security => Enable CSRF Protection.
Select credentials => Global => Add credentials for GitHub, AWS access key, and secret access key.

########### Setting File Path on Jenkins: ######################

Click on "New Item" on the Jenkins dashboard, select "Pipeline," name the pipeline, and provide SCM details (Git repository URL, GitHub credentials, branch name, and script path).

######### Jenkins Pipeline Deployment: ############

On the Jenkins dashboard, select "Build Now" to start the deployment process on AWS.
Ensure that the Elastic Kubernetes Service (EKS) pipeline finishes booting before deploying the Kubernetes cluster pipeline to avoid conflicts or errors.

######## Ingress Rule and Domain Name: ###########

Use the Nginx-ingress rule to create an internal load balancer for routing traffic.
Use the ingress rule to route traffic to a specific sub-domain for accessing Grafana and Socks Shop.

####### AWS Configuration:###################

Use aws configure on the instance terminal to add the user credentials (access key ID, secret access key, default region name, and default output format).

####### Route53: #########################################
Copy the name servers from Route53 on AWS to the provided domain name and save the name servers.

############## View Grafana and Socks Shop on the Browser: ################3

Copy the Grafana and Socks Shop URLs with the personal domain name to the browser to see the default pages secured by AWS Certificate Manager (ACM).
Overview of Socks Shop Application

The Socks Shop is a sample microservices-based e-commerce application available on GitHub. It consists of multiple microservices, each serving a specific function such as product catalog, shopping cart, and payment processing. The application showcases best practices for building and deploying microservices architectures.

###### Infrastructure as Code Approach

l utilize Terraform to automate the provisioning and management of infrastructure on Kubernetes. My deployment scripts and configurations are designed to be clear, concise, and easily maintainable.

######## Deployment Pipeline

My deployment pipeline orchestrates the movement of the application from code to a running environment on Kubernetes. l leverage Terraform to provision Kubernetes resources and deploy the Socks Shop microservices.

######### Monitoring and Alerts

Prometheus is implemented for monitoring the health and performance of the Socks Shop application. Alertmanager is configured to send alerts based on predefined thresholds or conditions.

####### Logging

Logging is crucial for tracking and analyzing the application's operations. l ensure comprehensive logging by integrating logging solutions such as Fluentd and Elasticsearch with Kubernetes.

##### Tools for Setup

l utilize Terraform for managing infrastructure configurations, making it easy to scale and manage Kubernetes clusters. AWS is chosen as the Infrastructure as a Service (IaaS) provider for hosting our Kubernetes cluster.

####### Security and HTTPS

The Socks Shop application is accessible securely over HTTPS using Let's Encrypt for certificates. l implement network security measures to enhance infrastructure security and utilize Ansible Vault for securely handling sensitive information.

Conclusion

In conclusion, this project demonstrates the successful deployment of the Socks Shop application on Kubernetes using Infrastructure as Code principles. Through clear and maintainable deployment scripts, robust monitoring and logging, and stringent security measures, l ensure the reliability and security of the application.

Please make sure to verify the commands and steps mentioned in this document before executing them in your environment.
