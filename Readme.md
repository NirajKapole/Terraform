# Terraform AWS Infrastructure Setup

This Terraform configuration sets up an AWS infrastructure that includes a VPC, an internet gateway, a custom route table, a subnet, a security group, a network interface, an Elastic IP, and an Ubuntu web server with Apache2.

## Prerequisites

Before you begin, ensure you have the following:

1. [Terraform](https://www.terraform.io/) installed on your local machine.
2. AWS credentials configured with the necessary permissions.
3. An SSH key pair for SSH access to the created instances (in this example, "main-key").

## Configuration Details

### Provider

The Terraform configuration uses AWS as the provider with the specified access and secret keys in the provider block.

### VPC

A Virtual Private Cloud (VPC) is created with the CIDR block "10.0.0.0/16."

### Internet Gateway

An internet gateway is attached to the VPC.

### Custom Route Table

A custom route table is created with a default route to the internet gateway.

### Subnet

A subnet is created within the VVC with the CIDR block "10.0.1.0/24."

### Security Group

A security group named "allow_web_traffic" is created to allow inbound traffic on ports 22 (SSH), 80 (HTTP), and 443 (HTTPS).

### Network Interface

A network interface is created with a private IP address within the previously defined subnet, and it's associated with the "allow_web_traffic" security group.

### Elastic IP

An Elastic IP is assigned to the network interface to provide a public IP address.

### Ubuntu Web Server

An Ubuntu web server instance is launched in the subnet, and Apache2 is installed and enabled on it.

## How to Use

1. Clone this repository to your local machine.

2. Set up your AWS credentials using the [AWS CLI](https://aws.amazon.com/cli/).

3. Modify the variables and configurations in the Terraform script as needed.

4. Initialize the working directory with Terraform:

   ```bash
   terraform init
Plan the infrastructure changes:
terraform plan

Apply the infrastructure changes:
terraform apply

Access the web server using the public IP address provided in the Terraform output.

Outputs
server_public_ip: The public IP address of the web server.
server_private_ip: The private IP address of the web server.
server_id: The ID of the web server instance.

Cleanup
To destroy the created resources and clean up the infrastructure:
terraform destroy
Be cautious when running this command, as it will remove all created AWS resources.

License
This Terraform configuration is provided under the MIT License. See the LICENSE file for more details.

