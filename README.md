# Project VPC Setup Guide

## Table of Contents
1. [VPC Setup](#1-vpc-setup)
2. [Internet Gateway](#2-internet-gateway)
3. [Subnet Configuration](#3-subnet-configuration)
4. [Public Route Table](#4-public-route-table)
5. [Subnet Association](#5-subnet-association)
6. [NAT Gateway Setup](#6-nat-gateway-setup)
7. [Private Route Table](#7-private-route-table)
8. [Security Groups](#8-security-groups)
9. [Web Server Security Group](#9-web-server-security-group)
10. [EC2 Instances Launch](#10-ec2-instances-launch)
11. [Automation Scripting](#11-automation-scripting)
12. [Target Group Creation](#12-target-group-creation)
13. [Website Accessibility](#13-website-accessibility)
14. [AWS Route 53 Integration](#14-aws-route-53-integration)


## 1. VPC Setup:
- **Resource Isolation:** 
  "Project VPC" was created to isolate resources, ensuring they operate in a secure and controlled environment separate from other AWS accounts.
- **Customizable Networking:** 
  Users have control over IP addressing, subnets, routing tables, and network gateways within the VPC, allowing tailored network configurations to meet specific requirements.
- **Scalable Infrastructure:** 
  VPC facilitates the provisioning of various AWS resources like EC2 instances, RDS databases, and Elastic Load Balancers, enabling the building of scalable and secure infrastructures.

## 2. Internet Gateway:
- **Internet Connectivity:** 
  "Project Internet Gateway" enables instances within the VPC to establish outbound connections to the internet and receive inbound traffic initiated from the internet.
- **Bidirectional Traffic:** 
  Acting as a gateway for both outbound (egress) and inbound (ingress) traffic, it facilitates communication between VPC resources and the wider internet.
- **High Availability:** 
  Internet Gateways are highly available and scalable components, automatically scaled to handle varying levels of demand, ensuring continuous connectivity to the internet.

## 3. Subnet Configuration:
- **Multi-AZ Deployment:** 
  Subnets were created across multiple availability zones (AZs) to distribute resources geographically, reducing the risk of downtime and improving fault tolerance.
- **Public Subnets:** 
  Public subnets (Public Subnet AZ1, Public Subnet AZ2) were established for resources that require direct internet access, such as web servers, allowing them to communicate with the internet while maintaining security.
- **Private Subnets:** 
  Private subnets (Private Subnet AZ1, Private Subnet AZ2) were designated for resources that do not need direct internet access, such as databases or application servers, providing an additional layer of security by keeping them isolated from the internet.

## 4. Public Route Table:
- **Traffic Routing:** 
  Configured a public route table to direct traffic with public access, ensuring that internet-bound traffic is routed to the Internet Gateway for onward transmission to the internet.
- **Network Segmentation:** 
  Public route tables facilitate the segregation of public-facing resources from private resources within the VPC, enhancing security and network management.
- **Route Prioritization:** 
  By associating public subnets with the public route table, the project ensures that traffic originating from those subnets follows the specified routing rules for internet connectivity.

## 5. Subnet Association:
- **Efficient Traffic Management:** 
  Associated subnets with respective route tables to manage traffic efficiently, ensuring that traffic is directed according to its intended destinations.
- **Routing Flexibility:** 
  Subnet associations allow for flexible routing configurations within the VPC, enabling administrators to adapt to changing network requirements.
- **Traffic Isolation:** 
  By correctly associating subnets with their respective route tables, the project ensures that traffic remains isolated within the designated network segments, enhancing security and network segmentation.

## 6. NAT Gateway Setup:
- **Private Subnet Internet Access:** 
  Deployed NAT gateways in each availability zone (NAT Gateway AZ1, NAT Gateway AZ2) to facilitate outbound internet access for resources deployed in private subnets.
- **Outbound Traffic Control:** 
  NAT gateways allow outbound traffic from private subnets to access the internet while preventing inbound traffic initiation from external sources, enhancing security.
- **Scalability and Redundancy:** 
  NAT gateways are highly available and scalable, automatically scaled to accommodate varying levels of outbound traffic demand and providing redundancy for continuous connectivity.

## 7. Private Route Table:
- **Internal Traffic Control:** 
  Created private route tables for each availability zone (Private route table AZ1, Private route table AZ2) to control internal traffic flow between resources deployed in private subnets.
- **Network Isolation:** 
  Private route tables specify routes for communication within private subnets, ensuring that internal traffic remains internal to the VPC and does not traverse the internet.
- **Enhanced Security:** 
  By keeping internal traffic isolated within private subnets, the project enhances security by minimizing exposure to external threats and unauthorized access attempts.

## 8. Security Groups:
- **Network Access Control:** 
  Defined security groups with inbound rules to control network traffic to EC2 instances, acting as virtual firewalls to filter incoming and outgoing traffic based on specified rules.
- **Granular Security Policies:** 
  Security groups allow for granular control over traffic flow, enabling administrators to define precise rules for permitting or denying specific types of network traffic.
- **Dynamic Security Updates:** 
  Security groups can be updated dynamically to adapt to changing security requirements, providing flexibility and responsiveness in managing network security.

## 9. Web Server Security Group:
- **Focused Traffic Control:** 
  Established a specific security group for web servers with tailored rules to allow only necessary incoming traffic, such as HTTP (port 80) and HTTPS (port 443) requests, while blocking unauthorized access attempts.
- **Security Compliance:** 
  Web server security groups enforce security best practices by restricting access to essential ports and protocols, reducing the attack surface and mitigating the risk of security breaches.
- **Isolation of Web Resources:** 
  By segregating web server resources within dedicated security groups, the project enhances security by limiting access to sensitive web assets and preventing unauthorized access to web applications and data.

## 10. EC2 Instances Launch:
- **Redundant Hosting:** 
  Launched 2 EC2 instances across availability zones (WebServer1 and WebServer2) to host the website, ensuring redundancy and fault tolerance in case of instance failure or maintenance.
- **Scalability:** 
  EC2 instances can be scaled vertically or horizontally to accommodate changes in website traffic or workload demands, ensuring optimal performance and user experience.
- **Cost Optimization:** 
  By leveraging EC2 instances, the project can benefit from pay-as-you-go pricing models, optimizing costs by scaling resources based on actual usage patterns.

## 11. Automation Scripting:
- **Efficient Deployment:** 
  Developed a bash script for automated web application deployment on EC2 instances, streamlining the deployment process and reducing manual intervention.
- **Consistency:** 
  Automation scripting ensures consistency in deployment procedures, minimizing the risk of human error and ensuring that deployments follow standardized processes.
- **Time Savings:** 
  By automating deployment tasks, the project saves time and resources, allowing team members to focus on higher-value activities such as development and innovation.

## 12. Target Group Creation:
- **Load Balancing:** 
  Created target groups to route traffic to specific EC2 instances, enabling load balancing and ensuring high availability and fault tolerance for the website.
- **Traffic Distribution:** 
  Target groups distribute incoming traffic across multiple EC2 instances based on predefined criteria, such as round-robin or least connections, optimizing resource utilization and improving performance.
- **Scalability:** 
  By using target groups in conjunction with load balancers, the project can scale resources dynamically to handle fluctuations in website traffic, ensuring a seamless user experience during peak demand periods.

## 13. Website Accessibility:
- **DNS Resolution:** 
  Accessed the DNS of the target group to view and interact with the website, allowing users to access the website using a domain name.

## 14. AWS Route 53 Integration:
- **Domain Management:** 
  Utilized AWS Route 53 for DNS management throughout the project, enabling the registration and management of domain names for the deployed website.
- **Dynamic DNS Updates:**
  Route 53 supports dynamic DNS updates, allowing for automatic changes to DNS records based on changes in the infrastructure, such as IP address updates or resource additions/removals. This ensures that the DNS configuration remains up-to-date without manual intervention, improving overall system reliability and reducing administrative overhead.
