# Terraform AWS Infrastructure with Jenkins Automation

This repository contains Terraform configurations to set up a basic AWS infrastructure with an EC2 instance.
Additionally, it includes a Jenkinsfile for automating the deployment and destruction of the infrastructure using Jenkins.

## Prerequisites

Before you begin, ensure you have the following:

- [Terraform](https://www.terraform.io/) installed locally.
- AWS credentials configured on your machine with appropriate permissions.
- [Jenkins](https://www.jenkins.io/) installed and configured with the necessary plugins.

## Getting Started

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/terraform-aws-infrastructure.git
    cd terraform-aws-infrastructure
    ```

2. **Customize Configuration:**
    Review and customize the `main.tf` file to match your specific requirements.

3. **Configure Jenkins:**
    - Create a Jenkins pipeline job linked to this repository.
    - Configure AWS credentials in Jenkins with the IDs 'AWS_ACCESS_KEY_ID' and 'AWS_SECRET_ACCESS_KEY'.

4. **Run Jenkins Pipeline:**
    - Trigger the Jenkins job to execute the pipeline.
    - Jenkins will prompt for approval before applying changes.

## Terraform Files

- **main.tf:** Contains the main Terraform configuration for EC2 instance, security group, and S3 bucket.
- **output.tf:** Defines the output variable for the public IP address of the EC2 instance.

## Jenkinsfile

- **Jenkinsfile:** Defines a Jenkins pipeline with stages for Terraform initialization, application, and output retrieval.

## Outputs

- **instance_ip:** The public IP address of the created EC2 instance.

## Important Notes:

- AWS credentials must be properly configured on your machine and in Jenkins.
- The security group allows SSH traffic from any IP address (0.0.0.0/0); tighten security settings for production environments.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Feel free to explore and adapt this project for your AWS infrastructure needs, and automate deployments with Jenkins!
