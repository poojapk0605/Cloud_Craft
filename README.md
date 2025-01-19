# Cloud_Craft :( ### link : https://github.com/orgs/cloud-craft-project-fullstack/repositories )
# Web Application Deployment with Git Actions, Packer, and Terraform

This repository contains the source code and deployment configurations for deploying a web application on Google Cloud Platform (GCP) using Git Actions, Packer, and Terraform.

## Assignments Overview

### Assignment_01: Health Check Endpoint
- Created a web application with an endpoint at http://localhost:8080/healthz to check the health status of the database server.

### Assignment_02: Additional Endpoints and Methods
- Enhanced the web application to include a second endpoint at http://localhost:8080/v1 supporting methods such as POST, GET, and PUT.

### Assignment_03: Integration Testing with Git Actions
- Integrated Git Actions for automated integration testing of the web application.

### Assignment_04: Custom Image Creation with Packer and Terraform
- Developed a custom image using Packer with all dependencies required for the web application.
- Utilized Terraform to create VM instances on GCP and configured a systemd service file named `application.service` to start the web application. The service hits both endpoints defined in Assignment_02.

### Assignment_05: Cloud SQL Integration
- Updated the Packer custom image to include connections to a Cloud SQL instance for the web application.
- Leveraged Terraform to create VM instances on GCP, integrating a startup script to launch the web application.

### Assignment_06 : DNS Setup details

This assignment involved the setup of a DNS system, which included the creation of a public zone and configuration of Nameservers through the DNS registrar. Additionally, Terraform was utilized to create an A record, and endpoints were established for `/healthz` and `/v1`, accessible via [http://poojacloud24.pw:8080](http://poojacloud24.pw:8080).

Moreover, modifications were made to a Packer configuration. Specifically, the `google-agent-ops` was installed, and logging was configured to direct logs from `/var/logs/app.log` to the Google Cloud Platform (GCP) console log explorer.

### Assignment_07 : Serverless and cloud functions
In Assignment #07, the focus was on setting up a Pub/Sub system and Cloud Function using Terraform. This involved creating the necessary infrastructure to establish communication between Pub/Sub, Cloud Function, MySQL instances, and the web application.

The primary functionality implemented was related to user registration. Upon registration via a POST method, an email verification link is dispatched to the user utilizing Pub/Sub and Cloud Function. If the user fails to verify their email, they are restricted from updating or accessing their user details within the application.

## Assignment_08
There is no changes on web application

## Assignment_09
Enhanced Integration Test Workflow:

Updated integration test workflow to support CI/CD testing.
Ensured thorough testing of application changes before deployment.
Manual Creation of VM Instance Templates:

Created VM instance templates manually via the GCP console.
Templates serve as predefined configurations for launching virtual machine instances.
Introduction of New Endpoint:

Added a new endpoint to the application for testing updates.
Facilitates validation of changes and integration with existing functionality.
Purpose of Updates:

Establishment of a robust CI/CD pipeline for the application.
Optimization of development and deployment processes for efficiency and reliability.
## Directory Structure

- `/app`: Contains the source code of the web application.
- `/packer`: Includes Packer configuration files for building custom images.
- `/terraform`: Contains Terraform configurations for provisioning VM instances on GCP and associated resources.(seperate repo)
- `/tests`: Includes integration tests for the web application.



Terraform VPC Creation
This repository contains Terraform configuration files designed for creating and managing a Virtual Private Cloud (VPC) along with its associated subnets and routing on Google Cloud Platform (GCP).

Configuration Files
The project includes the following Terraform configuration files:

main.tf: This file contains the provider information, specifically for GCP, and configurations for VM instances.
variables.tf: Defines the variables utilized within the configuration, enabling customization and reusability of the code.
network.tf: Contains networking settings required for VM instances using VPC and VPC peering.
database.tf: Consists of database settings for VM instances utilizing Cloud SQL.
script.sh: Used to execute the web application during VM instance creation.
Prerequisites
Before getting started, ensure you have the following:

Terraform installed on your machine.
A Google Cloud Platform (GCP) account and gcloud CLI configured.
Necessary permissions to create and manage VPC resources within your GCP account.
The Google Compute Engine API (google_compute_API) enabled in your GCP project.
Ensure VPC peering is configured, allowing Cloud SQL instances to only connect with the web application and not other networks.
Usage
To create your VPC, subnets, and routing, follow these steps using Terraform. Replace the variable placeholders with your desired values:

Run the following command to initialize Terraform:
sh
Copy code
terraform init
Execute the Terraform apply command with the necessary variables replaced:
sh
Copy code
terraform apply \
  -var="vpc_name=your_vpc_name" \
  -var="subnet_name=your_subnet_name" \
  -var="subnet_ip_cidr_range=your_subnet_cidr" \
  -var="subnet_region=your_subnet_region" \
  -var="route_name=your_route_name" \
  -var="route_dest_range=your_route_destination" \
  -var="route_next_hop_gateway=your_next_hop_gateway"



Cloud Function Implementation Guide
Prerequisites
Before implementing the cloud function, ensure the following prerequisites are met:

Google Cloud Platform Account: You need to have access to Google Cloud Platform (GCP) services.
Publisher and Subscriber Setup: Set up a Publisher and Subscriber for your Pub/Sub topic to trigger the cloud function.
Google Cloud Storage Bucket: Create a Google Cloud Storage bucket to store the cloud function code as a zip file.
Entry Point and Permissions: Define the entry point for your cloud function and ensure appropriate permissions are configured.
Implementation Steps
Trigger Setup:
When the VM starts and hits the POST method at http://poojacloud24.pw:8080/v1/user for user registration, it triggers the cloud function.
Cloud Function Configuration:
Write the cloud function using Node.js.
Utilize Pub/Sub to trigger the function.
Use Mailgun as the email provider to send an email to the user's email address.
User Verification:
Upon receiving the email, the user must verify their email address.
If verified, the user can perform update or display operations.
If not verified, the user is restricted from performing any methods.
Resending Verification Link:
Implement a mechanism to prevent users from sending repeated API calls to resend the verification link after initial registration.
Integration with MySQL Cloud Instances:
Utilize MySQL Cloud Instances with private IP addresses.
Use a VPC connector created on the cloud function to securely access the MySQL instances.
Conclusion
By following these steps, you can implement a cloud function on Google Cloud Platform to handle user registration, email verification, and integration with MySQL Cloud Instances efficiently. Ensure proper testing and monitoring of the cloud function for optimal performance and reliability.

Updates :
The post method URL changes from http to https : https://poojacloud24.pw/v1/user
