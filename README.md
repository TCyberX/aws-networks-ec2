

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** Albert  
**Email:** tapcyberx@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is AWS’s foundational networking service. It allowed me to create and manage my own virtual network in this project, where I could control IP addressing, subnetting, routing, and connectivity to and from the internet.

It also gave me the tools to define security and traffic rules using components like security groups and network ACLs, making it essential for securely launching AWS resources.



### How I used Amazon VPC in this project

In this project, I used Amazon VPC to create my own custom virtual network along with a range of essential components. This included setting up security groups, network ACLs, and subnets both public and private.

I also launched EC2 instances in each subnet to simulate a realistic environment where public-facing and private resources are securely separated, following best practices in cloud network architecture.



### One thing I didn't expect in this project was...

I didn’t expect the VPC resource map to be so intuitive and helpful. It gave me a clear visual overview of all my VPC components and how they’re connected making it much easier to understand and manage the network architecture during setup.

### This project took me...

This project took me around 3h to completed and make notes that help to understand in future projects.

---

## Setting Up Direct VM Access

Directly accessing a virtual machine like an EC2 instance means "logging into" the instance itself, rather than managing it through the AWS Management Console.

This allows you to perform hands-on operations, such as installing software, updating packages, configuring system settings, or troubleshooting issues from the command line giving you full control over the machine’s environment.


### SSH is a key method for directly accessing a VM

SSH stands for Secure Shell, and it refers to both a protocol and a type of encrypted traffic used to securely access and manage remote systems.

SSH is the protocol that enables key pair authentication, allowing users to connect to virtual machines (like EC2 instances). Once the connection is established, SSH also ensures that all communication is encrypted, protecting data as it’s transferred between your local machine and the remote server.



### To enable direct access, I set up key pairs

A key pair is a set of cryptographic keys a public key and a private key used to securely authenticate access to virtual machines, such as EC2 instances in AWS.

The public key is stored on the instance, while the private key remains with the user. When connecting (e.g., via SSH), AWS uses the key pair to verify identity without the need for a password, making it a secure and commonly used method for remote access authentication.

A private key's file format refers to the type of file used to store the key. This format determines how the key can be read and used by authentication tools.

In my case, the private key was stored in .pem format (Privacy Enhanced Mail), which is a widely accepted format supported by most servers and SSH clients making it ideal for securely connecting to services like AWS EC2.



---

## Launching a public server

To update my EC2 instance’s networking settings, I changed the VPC and subnet it would be launched in. I selected my custom Nextwork VPC and assigned the instance to a Public Subnet to ensure internet accessibility.

Additionally, I attached my existing security group to manage traffic rules ensuring the instance remained protected while being accessible for the project.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because the Nextwork public security group allows in ALL HTTP traffic - which would leave my private server much more vulnerable to security attacks or risk.

My private server's security group's source is my Nextwork Public Security Group, which means only SSH traffic coming from resources associated with that security group would be allowed.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

This time, I used the “VPC and more” setup option in the AWS Console to create my Amazon VPC. This method provides a resource map that simplifies the process of launching a VPC along with all its key components such as subnets, route tables, internet gateways, and security groups.

It’s a more visual and guided approach that ensures everything is properly connected and configured from the start.

A VPC resource map is a visual diagram that displays all the components of your VPC such as subnets, route tables, internet gateways, and security groups along with the connections between them.

The map is interactive, allowing you to hover over or select a specific resource to highlight its related components. This makes it easier to understand the structure and flow of your network, and helps with troubleshooting or verifying configurations at a glance.



My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC Nextwork because are already isolated from each other. Still, this is not the best practice if I need VPC peering.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When setting up my VPC, I could create either none or one public subnet per Availability Zone. I chose to create one public subnet in each zone, following AWS best practices.

This approach helps improve redundancy and high availability by distributing resources across multiple zones ensuring that if one zone goes down, the others can still operate effectively.




NAT gateways (Network Address Translation gateways) are connectors that allow resources in a private subnet to access the internet, while still preventing inbound traffic from reaching them directly.

When setting up my VPC, I was given the option to create NAT gateways to support use cases like downloading updates or sending logs from instances in private subnets without exposing them to public internet threats.


![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-ec2_8ee57662)

---

---
